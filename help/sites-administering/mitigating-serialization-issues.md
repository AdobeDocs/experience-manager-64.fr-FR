---
title: Réduire les problèmes de sérialisation dans AEM
seo-title: Mitigating serialization issues in AEM
description: Découvrez comment atténuer les problèmes de sérialisation dans AEM.
seo-description: Learn how to mitigate serialization issues in AEM.
uuid: c3989dc6-c728-40fd-bc47-f8427ed71a49
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: Security
content-type: reference
discoiquuid: f3781d9a-421a-446e-8b49-40744b9ef58e
exl-id: 779e1e4c-9a6e-4446-9c12-5b2499afbf6a
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '992'
ht-degree: 69%

---

# Réduire les problèmes de sérialisation dans AEM{#mitigating-serialization-issues-in-aem}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

## Présentation {#overview}

L’équipe d’AEM chez Adobe travaille en étroite collaboration avec le projet [NotSoSerial](https://github.com/kantega/notsoserial) open source pour limiter les vulnérabilités décrites dans **CVE-2015-7501**. NotSoSerial est accordé sous [licence Apache 2](https://www.apache.org/licenses/LICENSE-2.0) et comprend du code ASM accordé sous sa propre [licence de type BSD](https://asm.ow2.org/license.html).

Le fichier JAR d’agent inclus dans ce package est la distribution de NotSoSerial modifiée par Adobe.

NotSoSerial est une solution de niveau Java à un problème de niveau Java, et il n’est pas spécifique à AEM. Il ajoute un contrôle en amont à une tentative de désérialisation d’un objet. Ce contrôle teste un nom de classe par rapport à une liste autorisée ou une liste bloquée de style pare-feu. En raison du nombre limité de classes dans la liste bloquée par défaut, il est peu probable que cela ait un impact sur vos systèmes ou votre code.

Par défaut, l’agent effectue un contrôle de liste bloquée en vérifiant les classes vulnérables actuellement connues. Cette liste bloquée est destinée à vous protéger contre la liste actuelle des attaques qui utilisent ce type de vulnérabilité.

La liste bloquée et comme la liste autorisée peuvent être configurées en suivant les instructions de la section [Configuration de l’agent](/help/sites-administering/mitigating-serialization-issues.md#configuring-the-agent) de cet article.

L’agent est conçu pour vous aider à limiter les dernières classes vulnérables connues. Si votre projet désérialise des données non approuvées, il peut toujours être vulnérable aux attaques par déni de service, aux attaques par saturation de mémoire et aux futures attaques inconnues de désérialisation.

Adobe prend officiellement en charge Java 6, 7 et 8, toutefois, il semble que NotSoSerial prend également en charge Java 5.

## Installation de l’agent {#installing-the-agent}

>[!NOTE]
>
>Si vous avez déjà installé le correctif de sérialisation pour AEM 6.1, supprimez les commandes de démarrage de l’agent de la ligne d’exécution Java.

1. Installez le lot **com.adobe.cq.cq-serialization-tester**.

1. Accédez à la console Lots web à l’adresse `https://server:port/system/console/bundles`.
1. Recherchez le lot de sérialisation et démarrez-le. Cela devrait charger automatiquement l’agent NotSoSerial de manière dynamique.

## Installation de l’agent sur les serveurs d’applications {#installing-the-agent-on-application-servers}

L’agent NotSoSerial n’est pas inclus dans la distribution standard des AEM pour les serveurs d’applications. Cependant, vous pouvez l’extraire de la distribution jar d’AEM et l’utiliser avec la configuration de votre serveur d’applications :

1. Tout d’abord, téléchargez AEM fichier quickstart et extrayez-le :

   ```shell
   java -jar aem-quickstart-6.2.0.jar -unpack
   ```

1. Accédez à l’emplacement du QuickStart AEM que vous venez de décompresser et copiez le dossier `crx-quickstart/opt/notsoserial/` dans le dossier `crx-quickstart` de l’installation du serveur d’applications AEM.

1. Modifiez le propriétaire de `/opt` sur l’utilisateur exécutant le serveur :

   ```shell
   chown -R opt <user running the server>
   ```

1. Configurez et vérifiez que l’agent a été correctement activé, comme indiqué dans les sections suivantes de cet article.

## Configuration de l’agent {#configuring-the-agent}

La configuration par défaut est appropriée pour la plupart des installations. Cela inclut une liste bloquée des classes vulnérables connues pour l’exécution distante et une liste autorisée de packages où la désérialisation des données de confiance doit être relativement sécurisée.

La configuration de pare-feu est dynamique et peut être changée à tout moment en :

1. accédant à la console web à l’adresse `https://server:port/system/console/configMgr` ;
1. Recherche et clic **Configuration du pare-feu de désérialisation.**

   >[!NOTE]
   >
   >Vous pouvez également accéder directement à la page de configuration en accédant à l’URL :
   >
   >* `https://server:port/system/console/configMgr/com.adobe.cq.deserfw.impl.DeserializationFirewallImpl`


Cette configuration contient la journalisation de la liste autorisée, de la liste bloquée et de la désérialisation.

**Listes autorisées**

Dans la section Liste autorisée se trouvent les classes ou les préfixes de package pour lesquels la désérialisation est autorisée. Il est important de noter que si vous désérialisez vos propres classes, vous devez ajouter les classes ou les packages à cette liste autorisée.

**Liste bloquée**

La section Liste bloquée comprend les classes pour lesquelles la désérialisation n’est jamais autorisée. L’ensemble initial de ces classes est limité à celles qui sont considérées comme vulnérables aux attaques d’exécution à distance. La liste bloquée est appliquée avant toute entrée de liste autorisée.

**Journalisation des diagnostics**

Dans la section de journalisation des diagnostics, vous pouvez choisir plusieurs options afin de consigner les moments où la désérialisation a lieu. Les désérialisations sont uniquement consignées lors de la première utilisation, elles ne le sont pas pour les utilisations suivantes.

La valeur par défaut **class-name-only** vous notifie les classes qui sont désérialisées.

Vous pouvez également définir l’option **full-stack** qui consigne une pile Java de la première tentative de désérialisation afin de vous informer lorsque votre désérialisation a lieu. Cela peut être utile pour rechercher et supprimer la désérialisation de votre utilisation.

## Vérification de l’activation de l’agent {#verifying-the-agent-s-activation}

Vous pouvez vérifier la configuration de l’agent de désérialisation en accédant à l’URL à l’adresse :

* `https://server:port/system/console/healthcheck?tags=deserialization`

Lorsque vous accédez à l’URL, la liste des contrôles de l’intégrité associés à l’agent s’affiche. Vous pouvez déterminer si l’agent est correctement activé en vérifiant la réussite des contrôles de l’intégrité. S’ils échouent, vous devrez peut-être charger l’agent manuellement.

Pour plus d’informations sur la résolution des problèmes avec l’agent, voir [Gestion Des Erreurs Avec Le Chargement Dynamique De L’Agent](#handling-errors-with-dynamic-agent-loading) ci-dessous.

>[!NOTE]
>
>Si vous ajoutez `org.apache.commons.collections.functors` à la liste autorisée, le contrôle de l’intégrité échoue systématiquement.

## Gestion des erreurs avec le chargement de l’agent dynamique {#handling-errors-with-dynamic-agent-loading}

Si des erreurs sont exposées dans le journal, ou si les étapes de vérification détectent un problème lors du chargement de l’agent, vous devrez peut-être charger l’agent manuellement. Cette méthode est également recommandée si vous utilisez un environnement d’exécution JRE (Java Runtime Environment) au lieu d’un kit JDK (Java Development Toolkit), car les outils de chargement dynamique ne sont pas disponibles.

Pour charger l’agent manuellement, suivez les instructions ci-dessous :

1. Modifiez les paramètres de démarrage de la JVM du jar CQ, en ajoutant l’option suivante :

   ```shell
   -javaagent:<aem-installation-folder>/crx-quickstart/opt/notsoserial/notsoserial.jar
   ```

   >[!NOTE]
   >
   >Cela nécessite également l’utilisation de l’option -nofork CQ/AEM, ainsi que les paramètres de mémoire JVM appropriés, car l’agent ne sera pas activé sur une JVM dupliquée.

   >[!NOTE]
   >
   >La distribution Adobe du fichier JAR de l’agent NotSoSerial réside dans le dossier `crx-quickstart/opt/notsoserial/` pour votre installation AEM.

1. Arrêtez et redémarrez la JVM.

1. Vérifiez à nouveau l’activation de l’agent en suivant les étapes décrites ci-dessus dans la section [Vérification de l’activation de l’agent](/help/sites-administering/mitigating-serialization-issues.md#verifying-the-agent-s-activation).

## Autres considérations {#other-considerations}

Si vous exécutez sur une JVM IBM, consultez la documentation sur la prise en charge de l’API Attach Java à cet [emplacement](https://www.ibm.com/support/knowledgecenter/SSSTCZ_2.0.0/com.ibm.rt.doc.20/user/attachapi.html).
