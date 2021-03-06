---
title: Réduction des problèmes de sérialisation dans AEM
seo-title: Mitigating serialization issues in AEM
description: Apprenez à réduire les problèmes de sérialisation dans AEM.
seo-description: Learn how to mitigate serialization issues in AEM.
uuid: c3989dc6-c728-40fd-bc47-f8427ed71a49
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: Security
content-type: reference
discoiquuid: f3781d9a-421a-446e-8b49-40744b9ef58e
exl-id: 779e1e4c-9a6e-4446-9c12-5b2499afbf6a
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '956'
ht-degree: 67%

---

# Réduction des problèmes de sérialisation dans AEM{#mitigating-serialization-issues-in-aem}

## Présentation {#overview}

 L’équipe d’AEM chez Adobe travaille en étroite collaboration avec le projet [NotSoSerial](https://github.com/kantega/notsoserial) open source pour limiter les vulnérabilités décrites dans **CVE-2015-7501**. NotSoSerial est accordé sous [licence Apache 2](https://www.apache.org/licenses/LICENSE-2.0) et comprend du code ASM accordé sous sa propre [licence de type BSD](https://asm.ow2.org/license.html).

Le fichier JAR d’agent inclus dans ce module est la distribution de NotSoSerial modifiée par Adobe.

  NotSoSerial est une solution de niveau Java à un problème de niveau Java, et il n’est pas spécifique à AEM. Il ajoute un contrôle en amont à une tentative de désérialisation d’un objet. Cette vérification teste un nom de classe par rapport à une liste autorisée et/ou une liste bloquée de type pare-feu. En raison du nombre limité de classes dans la liste bloquée par défaut, il est peu probable que cela ait un impact sur vos systèmes ou votre code.

Par défaut, l’agent effectue un contrôle de liste bloquée sur les classes vulnérables connues actuelles. Cette liste bloquée a pour but de vous protéger de la liste actuelle des exploits qui utilisent ce type de vulnérabilité.

La liste bloquée et la liste autorisée peuvent être configurées en suivant les instructions de la section [Configuration de l’agent](/help/sites-administering/mitigating-serialization-issues.md#configuring-the-agent) de cet article.

L’agent est conçu pour vous aider à limiter les dernières classes vulnérables connues. Si votre projet désérialise des données non approuvées, il peut être vulnérable aux attaques par déni de service, aux attaques de mémoire insuffisante et aux futures attaques inconnues de désérialisation.

Adobe prend officiellement en charge Java 6, 7 et 8, toutefois, il semble que NotSoSerial prend également en charge Java 5.

## Installation de l’agent {#installing-the-agent}

>[!NOTE]
>
>Si vous avez déjà installé le correctif de sérialisation pour AEM 6.1, supprimez les commandes de démarrage de l’agent de la ligne d’exécution Java.

1. Installez le lot **com.adobe.cq.cq-serialization-tester**.

1. Accédez à la console web du bundle à l’adresse `https://server:port/system/console/bundles`
1. Recherchez le lot de sérialisation et démarrez-le. Cela devrait charger automatiquement et dynamiquement l’agent NotSoSerial.

## Installation de l’agent sur les serveurs d’applications {#installing-the-agent-on-application-servers}

L’agent NotSoSerial n’est pas inclus dans la distribution standard d’AEM pour les serveurs d’applications. Cependant, vous pouvez l’extraire du fichier de distribution JAR d’AEM et l’utiliser avec la configuration de votre serveur d’applications :

1. Tout d’abord, téléchargez le fichier QuickStart AEM et extrayez-le :

   ```shell
   java -jar aem-quickstart-6.2.0.jar -unpack
   ```

1. Accédez à l’emplacement de l’AEM de démarrage rapide que vous venez de décompresser, puis copiez la variable `crx-quickstart/opt/notsoserial/` vers le dossier `crx-quickstart` du dossier d’installation du serveur d’applications AEM.

1. Modifier la propriété de `/opt` à l’utilisateur exécutant le serveur :

   ```shell
   chown -R opt <user running the server>
   ```

1. Configurez l’agent et vérifiez qu’il a été correctement activé, comme indiqué dans les sections suivantes de cet article.

## Configuration de l’agent {#configuring-the-agent}

La configuration par défaut est appropriée pour la plupart des installations. Cela inclut une liste bloquée de classes vulnérables connues d’exécution distante et une liste autorisée de packages où la désérialisation de données approuvées doit être relativement sûre.

   La configuration de pare-feu est dynamique et peut être changée à tout moment en :

1. Accédez à la console web à l’adresse `https://server:port/system/console/configMgr`
1. recherchant **Configuration du pare-feu de désérialisation** et en cliquant dessus.

   >[!NOTE]
   >
   >Vous pouvez également atteindre la page de configuration directement en accédant à l’URL :
   >
   >* `https://server:port/system/console/configMgr/com.adobe.cq.deserfw.impl.DeserializationFirewallImpl`


Cette configuration contient la journalisation de la liste autorisée, de la liste bloquée et de la désérialisation.

**Listes autorisées**

Dans la section Liste autorisée, il s’agit de classes ou de préfixes de package qui seront autorisés pour la désérialisation. Il est important de savoir que si vous désérialisez des classes, vous devrez ajouter les classes ou les modules à cette liste autorisée.

**Liste bloquée**

Dans la section de liste bloquée se trouvent des classes qui ne sont jamais autorisées pour la désérialisation. L’ensemble initial de ces classes est limité à celles qui sont considérées comme vulnérables aux attaques d’exécution à distance. La liste bloquée est appliquée avant toute entrée de liste autorisée.

**Journalisation des diagnostics**

Dans la section relative à la journalisation des diagnostics, vous pouvez choisir plusieurs options de journalisation lorsque la désérialisation a lieu. Les désérialisations sont uniquement consignées lors de la première utilisation, elles ne le sont pas pour les utilisations suivantes.

La valeur par défaut **class-name-only** vous notifie les classes qui sont désérialisées.

Vous pouvez également définir l’option **full-stack** qui consigne une pile Java de la première tentative de désérialisation afin de vous informer lorsque votre désérialisation a lieu. Cela peut être utile pour rechercher et supprimer la désérialisation de votre utilisation.

## Vérification de l’activation de l’agent {#verifying-the-agent-s-activation}

Vous pouvez vérifier la configuration de l’agent de désérialisation en accédant à l’URL :

* `https://server:port/system/console/healthcheck?tags=deserialization`

Lorsque vous accédez à l’URL, la liste des contrôles de l’intégrité associés à l’agent s’affiche. Vous pouvez déterminer si l’agent est correctement activé en vérifiant la réussite des contrôles de l’intégrité. S’ils échouent, vous pouvez être amené à charger l’agent manuellement.

Pour plus d’informations sur la résolution des incidents avec l’agent, voir [Gestion des erreurs lors du chargement dynamique de l’agent](#handling-errors-with-dynamic-agent-loading) ci-dessous.

>[!NOTE]
>
>Si vous ajoutez `org.apache.commons.collections.functors` à la liste autorisée , le contrôle de l’intégrité échouera toujours.

## Gestion des erreurs lors du chargement dynamique de l’agent {#handling-errors-with-dynamic-agent-loading}

Si des erreurs sont exposées dans le journal, ou si les étapes de vérification détectent un problème lors du chargement de l’agent, vous devrez peut-être charger l’agent manuellement. Cela est également recommandé au cas où vous utilisez un JRE (Java Runtime Environment) plutôt qu’un JDK (Java Development Toolkit), dans la mesure où les outils pour le chargement dynamique ne sont pas disponibles.

Pour charger l’agent manuellement, suivez les instructions ci-dessous :

1. Modifiez les paramètres de démarrage de la JVM du fichier JAR de CQ, en ajoutant l’option suivante :

   ```shell
   -javaagent:<aem-installation-folder>/crx-quickstart/opt/notsoserial/notsoserial.jar
   ```

   >[!NOTE]
   >
   >Pour cela, utilisez également l’option -nofork de CQ/d’AEM, avec les paramètres appropriés de mémoire JVM, car l’agent ne sera pas activé sur une JVM divisée.

   >[!NOTE]
   >
   >La distribution par Adobe du fichier jar de l’agent NotSoSerial se trouve dans la variable `crx-quickstart/opt/notsoserial/` de votre installation AEM.

1. Arrêtez et redémarrez la JVM.

1. Vérifiez à nouveau l’activation de l’agent en suivant les étapes décrites ci-dessus dans [Vérification de l’activation de l’agent](/help/sites-administering/mitigating-serialization-issues.md#verifying-the-agent-s-activation).

## Autres considérations {#other-considerations}

Si vous exécutez sur une JVM IBM, voir la documentation sur la prise en charge de l’API Attach Java à cet [emplacement](https://www.ibm.com/support/knowledgecenter/SSSTCZ_2.0.0/com.ibm.rt.doc.20/user/attachapi.html).
