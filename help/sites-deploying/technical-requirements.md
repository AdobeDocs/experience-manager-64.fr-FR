---
title: Exigences techniques
seo-title: Technical Requirements
description: Liste des plateformes clientes et serveur prises en charge pour AEM.
seo-description: A list of the supported client and server platforms for AEM.
uuid: d5bdcd41-3585-41f7-860d-8068a2931a72
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: platform
discoiquuid: 4d3c4650-3e2a-43b1-ad2d-8d0ae2254ca9
exl-id: 21c10b39-ca37-4085-86f8-063c30a180ed
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '3295'
ht-degree: 69%

---

# Exigences techniques {#technical-requirements}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Adobe prend en charge Adobe Experience Manager (AEM) sur les plateformes, comme décrit ci-après dans ce document.

Pour tout problème spécifique à la plateforme elle-même, contactez directement le fournisseur de la plateforme.

>[!NOTE]
>
>Selon la plateforme sur laquelle vous installez AEM, il peut y avoir différents ensembles d’exigences pour la gestion des utilisateurs et des utilisatrices.

## Prérequis {#prerequisites}

Configuration minimale requise pour installer Adobe Experience Manager :

* Installation de la plateforme Java, du JDK standard ou d’autres [machines virtuelles Java](#java-virtual-machines) prises en charge
* Fichier de démarrage rapide Experience Manager (JAR autonome ou WAR de déploiement de l’application web)

### Configuration minimale requise en matière d’espace disque et de mémoire {#minimum-sizing-requirements}

Configuration minimale requise pour exécuter Adobe Experience Manager :

* 5 Go d’espace disque disponible dans le répertoire d’installation
* Mémoire de 2 Go

>[!NOTE]
>
>* Les cas d’utilisation des ressources numériques nécessitent davantage de mémoire de base. Voir [Déploiement et maintenance](/help/sites-deploying/deploy.md#default-local-install) pour plus d’informations.
>* [Le package complémentaire AEM Forms](/help/forms/using/installing-configuring-aem-forms-osgi.md) nécessite 15 Go d’espace temporaire.
>


Veuillez consulter la [Instructions de dimensionnement du matériel](/help/managing/hardware-sizing-guidelines.md) pour plus d’informations.

### Niveaux de prise en charge {#support-levels}

Ce document répertorie les plateformes clientes et serveur prises en charge pour Adobe Experience Manager. Adobe fournit plusieurs niveaux de prise en charge, tant pour les configurations recommandées que pour les autres.

### Configurations prises en charge {#supported-configurations}

Adobe recommande ces configurations et fournit une prise en charge complète dans le cadre du contrat de maintenance logicielle standard.

<table> 
 <tbody> 
  <tr> 
   <td>Niveau de prise en charge</td> 
   <td>Description<br /> </td> 
  </tr> 
  <tr> 
   <td><strong>A : pris en charge</strong></td> 
   <td>Adobe fournit une prise en charge et une maintenance complètes de cette configuration. Cette configuration est couverte par le processus d’assurance qualité d’Adobe.</td> 
  </tr> 
  <tr> 
   <td><strong>R : Prise en charge limitée </strong></td> 
   <td>Pour garantir la réussite des projets de nos clients et de nos clientes, Adobe fournit une prise en charge complète dans le cadre d’un programme d’assistance restreint, qui nécessite que des conditions spécifiques soient remplies. La prise en charge au niveau R nécessite une requête formelle de la part du client ou de la cliente et une confirmation par Adobe. Pour plus d’informations, veuillez contacter l’assistance clientèle d’Adobe.</td> 
  </tr> 
 </tbody> 
</table>

### Configurations non prises en charge {#unsupported-configurations}

| Niveau de prise en charge | Description |
|---|---|
| **Z : non pris en charge** | La configuration n’est pas prise en charge. Adobe ne fait aucune déclaration indiquant si la configuration fonctionne et ne la prend pas en charge. |

## Plateformes prises en charge {#supported-platforms}

### Machines virtuelles Java {#java-virtual-machines}

L’application nécessite l’exécution d’une machine virtuelle Java, fournie par la distribution Java Development Kit (JDK).

Adobe Experience Manager fonctionne avec les versions suivantes des machines virtuelles Java :

>[!CAUTION]
>
>Il est conseillé de consulter les bulletins de sécurité publiés par l’éditeur Java afin de garantir la sécurité des environnements de production et d’installer les mises à jour Java les plus récentes.

<table> 
 <tbody> 
  <tr> 
   <td>Plateforme</td> 
   <td>Niveau de prise en charge<br /> </td> 
  </tr> 
  <tr> 
   <td>Oracle Java SE 11 JDK [1]</td> 
   <td>Z : non pris en charge </td> 
  </tr> 
  <tr> 
   <td>Oracle Java SE 10 JDK [1]</td> 
   <td>Z : non pris en charge </td> 
  </tr> 
  <tr> 
   <td>Oracle Java SE 9 JDK [1]</td> 
   <td>Z : non pris en charge</td> 
  </tr> 
  <tr> 
   <td><strong>Oracle Java SE 8 JDK – 64 bits</strong></td> 
   <td>A : pris en charge [3]<br /> </td> 
  </tr> 
  <tr> 
   <td>IBM J9 VM - build 2.9, JRE 1.8.0 [2]</td> 
   <td>A : pris en charge</td> 
  </tr> 
  <tr> 
   <td>IBM J9 VM - build 2.8, JRE 1.8.0 [2]</td> 
   <td>A : pris en charge</td> 
  </tr> 
 </tbody> 
</table>

1. Oracle est passé à un modèle de support à long terme (LTS) pour les produits Oracle Java SE. Java 9 et 10 sont des versions non-LTS par Oracle (voir [Feuille de route du support Oracle Java SE](https://www.oracle.com/technetwork/java/eol-135779.html)). Adobe ne prendra en charge que les versions LTS de Java pour exécuter AEM en production.

1. IBM JRE est uniquement pris en charge conjointement avec WebSphere Application Server.
1. La prise en charge et la distribution du JDK Oracle Java SE, y compris toutes les mises à jour de maintenance des versions LTS après la fin des mises à niveau publiques, seront directement prises en charge par Adobe pour tous les clients AEM utilisant la technologie Oracle Java SE. Voir [Prise en charge Java Oracle pour Adobe Experience Manager Q&amp;A](assets/adobe-oracle-java-license-agreement.pdf) pour plus d’informations.

### Stockage et persistance {#storage-persistence}

Il existe différentes options pour déployer le référentiel d’Adobe Experience Manager. Consultez la liste suivante pour connaître les technologies et les options de stockage prises en charge.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Plateforme</strong></td> 
   <td><strong>Description</strong></td> 
   <td><strong>Niveau de prise en charge</strong></td> 
  </tr> 
  <tr> 
   <td><strong>Système de fichiers avec fichiers TAR [1]</strong></td> 
   <td>Référentiel</td> 
   <td>A : pris en charge</td> 
  </tr> 
  <tr> 
   <td><strong>Système de fichiers avec banque de données [1]</strong></td> 
   <td>Binaires</td> 
   <td>A : pris en charge</td> 
  </tr> 
  <tr> 
   <td>Stocker les fichiers binaires dans les fichiers TAR sur le système de fichiers [1]</td> 
   <td>Binaires</td> 
   <td>Z : Non pris en charge pour la production</td> 
  </tr> 
  <tr> 
   <td>Amazon S3</td> 
   <td>Binaires</td> 
   <td>A : pris en charge</td> 
  </tr> 
  <tr> 
   <td>Microsoft Azure Blob Storage</td> 
   <td>Binaires</td> 
   <td>A : pris en charge</td> 
  </tr> 
  <tr> 
   <td>MongoDB Enterprise 3.6 [5, 6]</td> 
   <td>Référentiel</td> 
   <td>A : pris en charge avec des limites</td> 
  </tr> 
  <tr> 
   <td>MongoDB Enterprise 3.4 [2, 3, 6]</td> 
   <td>Référentiel</td> 
   <td>A : pris en charge avec des limites</td> 
  </tr> 
  <tr> 
   <td>MySQL 5.7</td> 
   <td>Base de données Forms</td> 
   <td>A : pris en charge</td> 
  </tr> 
  <tr> 
   <td>IBM DB2 11.1<br /> </td> 
   <td>Base de données Forms</td> 
   <td>A : pris en charge</td> 
  </tr> 
  <tr> 
   <td>IBM DB2 10.5</td> 
   <td>Référentiel et base de données Forms</td> 
   <td>R : prise en charge limitée  (4)</td> 
  </tr> 
  <tr> 
   <td>Oracle Database 12c (12.1.x)</td> 
   <td>Référentiel et base de données Forms</td> 
   <td>R : prise en charge limitée </td> 
  </tr> 
  <tr> 
   <td>Microsoft SQL Server 2017</td> 
   <td>Base de données Forms</td> 
   <td>Z : Non pris en charge (4)</td> 
  </tr> 
  <tr> 
   <td>Microsoft SQL Server 2016</td> 
   <td>Base de données Forms</td> 
   <td>A : pris en charge</td> 
  </tr> 
  <tr> 
   <td>Microsoft SQL Server 2014</td> 
   <td>Base de données Forms</td> 
   <td>R : Prise en charge limitée (4)</td> 
  </tr> 
  <tr> 
   <td><strong>Apache Lucene (démarrage rapide intégré)</strong></td> 
   <td>Service de recherche</td> 
   <td>A : pris en charge</td> 
  </tr> 
  <tr> 
   <td>Apache Solr</td> 
   <td>Service de recherche</td> 
   <td>A : pris en charge</td> 
  </tr> 
 </tbody> 
</table>

1. Le système de fichiers comprend le stockage de bloc compatible avec POSIX. Cela inclut la technologie de stockage réseau. Gardez à l’esprit que les performances du système de fichiers peuvent varier et avoir une incidence sur les performances globales. Il est recommandé de charger l’AEM de test en combinaison avec le système de fichiers réseau/distant.
1. La fragmentation MongoDB n’est pas prise en charge dans AEM.
1. Seul le moteur de stockage WiredTiger de MongoDB est pris en charge.
1. Non pris en charge pour AEM Forms.
1. MongoDB Enterprise 3.6 est pris en charge à partir de AEM version 6.4.2.0.
1. La prise en charge de MongoDB 3.4 a atteint la fin de vie (EOL), tandis que MongoDB 3.6 devrait atteindre la fin de vie le 30 avril 2021. Veuillez noter que Adobe ne fournira une assistance que pour AEM problèmes liés aux produits à l’avenir.

>[!NOTE]
>
>Consultez la section [Déploiement de Communities](/help/communities/deploy-communities.md) pour plus d’informations sur les fonctionnalités d’AEM Communities.

>[!NOTE]
>
>MongoDB est un logiciel tiers non inclus dans le package de licence d’AEM. Pour plus d’informations, consultez la page [Politique de licence de MongoDB](https://www.mongodb.org/about/licensing/).
>
>Pour tirer le meilleur parti de votre déploiement AEM avec MongoDB, Adobe recommande d’obtenir une licence de la version MongoDB Enterprise afin de bénéficier d’une assistance professionnelle. Consultez la section [Déploiements recommandées](/help/sites-deploying/recommended-deploys.md#prerequisites-and-recommendations-when-deploying-aem-with-mongomk) pour plus d’informations.
>
>La licence comprend un ensemble standard de répliques, composé d’une instance principale et de deux instances secondaires qui peuvent être utilisées pour les déploiements de création ou de publication.
>
>Si vous souhaitez exécuter les instances de création et de publication sur MongoDB, deux licences distinctes doivent être achetées.
>
>Vous obtiendrez auprès de l’assistance clientèle d’Adobe une aide adaptée aux problèmes admissibles relatifs à l’utilisation de MongoDB avec AEM.
>
>Pour plus d’informations, consultez la page [MongoDB pour Adobe Experience Manager](https://www.mongodb.com/lp/contact/mongodb-adobe-experience-manager).

>[!NOTE]
>
>Les bases de données relationnelles prises en charge, telles que répertoriées ci-dessus, sont des logiciels tiers qui ne sont pas inclus dans le package de licence d’AEM.
>
>Pour exécuter AEM 6.4 avec une base de données relationnelle prise en charge, un contrat d’assistance distinct avec un fournisseur de base de données est requis. L’assistance clientèle Adobe propose son assistance pour les problèmes de qualification liés à l’utilisation de bases de données relationnelles avec AEM 6.4.
>
>**Notez que la plupart des bases de données relationnelles sont actuellement prises en charge au niveau R sur AEM 6.4, qui comprend des critères de prise en charge et un programme de prise en charge, comme indiqué dans la description du niveau R ci-dessus.**

### Moteurs de servlet/serveurs d’applications {#servlet-engines-application-servers}

Adobe Experience Manager peut s’exécuter en tant que serveur autonome (fichier JAR de démarrage rapide) ou en tant qu’application web au sein d’un serveur d’applications tiers (fichier WAR).

La version minimale requise de l’API de servlet est 3.1, mais sous Servlet 4.0.

| Plateforme | Niveau de prise en charge |
|---|---|
| **Moteur de servlet intégré à démarrage rapide (Jetty 9.3)** | A : pris en charge |
| Oracle WebLogic Server 12.2 (12cR2) | A : pris en charge |
| Serveur d’applications IBM WebSphere en livraison continue (LibertyProfile) avec Web Profile 7.0 et IBM JRE 1.8 | A : pris en charge |
| IBM WebSphere Application Server 9.0 | A : pris en charge |
| Apache Tomcat 8.5.x | A : pris en charge |
| JBoss EAP 7.1.0 avec le serveur d’applications JBoss | A : Pris en charge (1) |
| JBoss EAP 7.0.0 avec le serveur d’applications JBoss | A : pris en charge |

1. Non pris en charge pour AEM Forms.

### Systèmes d’exploitation de serveur {#server-operating-systems}

Adobe Experience Manager fonctionne avec les plateformes de serveur suivantes :

<table> 
 <tbody> 
  <tr> 
   <td><strong>Plateforme</strong></td> 
   <td><strong>Niveau de prise en charge</strong></td> 
  </tr> 
  <tr> 
   <td><strong>Linux, basé sur la distribution Red Hat</strong></td> 
   <td>A : Pris en charge (1)</td> 
  </tr> 
  <tr> 
   <td>Linux, en fonction de la distribution Debian, y compris Ubuntu </td> 
   <td>A : Pris en charge (4)</td> 
  </tr> 
  <tr> 
   <td>Linux, en fonction de la distribution SUSE</td> 
   <td>A : pris en charge</td> 
  </tr> 
  <tr> 
   <td>Microsoft Windows Server 2016</td> 
   <td>A : pris en charge</td> 
  </tr> 
  <tr> 
   <td>Microsoft Windows Server 2012 R2</td> 
   <td>A : pris en charge</td> 
  </tr> 
  <tr> 
   <td>Oracle Solaris 11</td> 
   <td>A : Pris en charge avec des restrictions (3,5,7)<br /> R : Prise en charge limitée des nouveaux contrats</td> 
  </tr> 
  <tr> 
   <td>IBM AIX 7.2</td> 
   <td>A : Pris en charge avec des restrictions (2,5,7)<br /> R : Prise en charge limitée des nouveaux contrats</td> 
  </tr> 
 </tbody> 
</table>

1. Les Linux Kernel 2.6. 3.x et 4.x contiennent des dérivés de la distribution Red Hat, y compris Red Hat Enterprise Linux, CentOS, Oracle Linux et Amazon Linux. Les fonctions de module complémentaire AEM Forms sont uniquement prises en charge sur CentOS 7 et Red Hat Enterprise Linux 7.
1. AEM Assets : Consultez la section [Prise en charge de l’écriture différée des métadonnées XMP](#requirements-for-aem-assets-xmp-metadata-write-back)
1. AEM Assets : Pas de prise en charge de l’imagerie Dynamic Media. La vidéo Dynamic Media est prise en charge.
1. AEM Forms est pris en charge uniquement sur Ubuntu 16.04 LTS.
1. AEM Assets : Pas de prise en charge pour [Transformation de fichier brut](/help/assets/camera-raw.md)
1. AEM Forms : Pas de prise en charge de l’environnement de production
1. AEM Assets : Pas de prise en charge pour [PDF Rasterizer amélioré](/help/assets/aem-pdf-rasterizer.md)
1. AEM Forms : Non pris en charge

### Environnements virtuels et de cloud computing {#virtual-cloud-computing-environments}

Adobe Experience Manager est pris en charge lorsqu’il s’exécute sur une machine virtuelle dans des environnements de cloud computing, tels que Microsoft Azure et Amazon Web Services (AWS), conformément aux exigences techniques répertoriées sur cette page et aux conditions de prise en charge standard d’Adobe.

Adobe recommande d’utiliser Adobe Managed Services pour déployer AEM sur Azure ou AWS. Adobe Managed Services fournit aux experts les compétences nécessaires pour déployer et utiliser AEM dans ces environnements de cloud computing. Consultez notre [Documentation supplémentaire sur Adobe Managed Services](https://www.adobe.com/marketing-cloud/enterprise-content-management/managed-services-cloud-platform.html?aemClk=t).

Dans tous les autres cas de déploiement d’AEM sur Azure ou AWS, ou tout autre environnement de cloud computing, la prise en charge d’Adobe sera limitée à l’environnement informatique virtuel, conformément aux spécifications techniques répertoriées sur cette page. Tout problème signalé relatif à AEM s’exécutant dans l’un de ces environnements cloud devra être reproductible indépendamment de tout service cloud spécifique à l’environnement cloud computing, sauf si le service cloud est spécifiquement pris en charge dans le cadre des exigences techniques répertoriées sur cette page, par exemple le stockage Azure Blob ou AWS S3.

Pour obtenir des recommandations sur le déploiement d’AEM sur Azure ou AWS, en dehors d’Adobe Managed Services, nous vous recommandons vivement de travailler directement avec le fournisseur cloud ou les partenaires d’Adobe qui prennent en charge le déploiement d’AEM dans l’environnement cloud de votre choix. Le fournisseur ou partenaire cloud sélectionné sera responsable du dimensionnement, de la conception et de l’implémentation de l’architecture, afin de répondre à vos besoins spécifiques en termes de performances, de charge, d’évolutivité et de sécurité.

### Plateformes de Dispatcher (serveurs web) {#dispatcher-platforms-web-servers}

Le Dispatcher est le composant de mise en cache et d’équilibrage de charge. [Téléchargez la dernière version de Dispatcher](https://helpx.adobe.com/experience-manager/dispatcher/release-notes.html). Experience Manager 6.4 nécessite la version 4.3.1 ou une version ultérieure du Dispatcher.

Les serveurs web suivants sont pris en charge pour une utilisation avec Dispatcher version 4.3.1 :

| Plateforme | Niveau de prise en charge |
|---|---|
| **Apache httpd 2.4.x** (voir également 1,2 ci-dessous) | A : pris en charge |
| Microsoft IIS 10 (Internet Information Server) | A : pris en charge |
| Microsoft IIS 8.5 (Internet Information Server) | A : pris en charge |

1. Les serveurs web développés sur la base du code source Apache httpd bénéficieront du même niveau de prise en charge que la version de httpd sur laquelle ils sont basés : En cas de doute, demandez à l’Adobe de confirmer le niveau de prise en charge associé au produit serveur correspondant. Différents cas de figure :

   1. Le serveur HTTP a été créé en utilisant uniquement les distributions source Apache officielles, ou
   1. Le serveur HTTP a été livré dans le cadre du système d’exploitation sur lequel il est exécuté. Exemples : Serveur IBM HTTP, Serveur Oracle HTTP 

1. Dispatcher n’est pas disponible pour Apache 2.4.x pour les systèmes d’exploitation Windows.

## Plateformes clientes prises en charge {#supported-client-platforms}

### Navigateurs pris en charge pour l’interface utilisateur de création {#supported-browsers-for-authoring-user-interface}

L’interface utilisateur d’Adobe Experience Manager fonctionne avec les plates-formes clientes suivantes : Tous les navigateurs sont testés avec l’ensemble par défaut de plug-ins et de modules complémentaires.

L’interface utilisateur d’AEM est optimisée pour les grands écrans (généralement les notebooks et les ordinateurs de bureau) et le format de tablette (comme Apple iPad ou Microsoft Surface). Le format de téléphone n’est pas pris en charge.

>[!NOTE]
>
>**Prise en charge des navigateurs avec des cycles de version rapides :**
>
>Mozilla Firefox, Google Chrome and Microsoft Edge publient des mises à jour tous les quelques mois. Adobe s’engage à fournir des mises à jour pour qu’Adobe Experience Manager conserve le niveau de prise en charge, comme indiqué ci-dessous avec les versions à venir de ces navigateurs.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Navigateur</strong></td> 
   <td><strong>Prise en charge de l’interface utilisateur<br /> </strong></td> 
   <td><strong>Prise en charge de l’interface utilisateur classique</strong></td> 
  </tr> 
  <tr> 
   <td><strong>Google Chrome (Evergreen)</strong></td> 
   <td>A : pris en charge</td> 
   <td>A : pris en charge</td> 
  </tr> 
  <tr> 
   <td>Microsoft Edge (Evergreen)</td> 
   <td>A : pris en charge</td> 
   <td>A : pris en charge</td> 
  </tr> 
  <tr> 
   <td>Microsoft Internet Explorer 11</td> 
   <td>A : pris en charge</td> 
   <td>A : pris en charge</td> 
  </tr> 
  <tr> 
   <td>Mozilla Firefox (Evergreen)</td> 
   <td>A : pris en charge</td> 
   <td>A : pris en charge</td> 
  </tr> 
  <tr> 
   <td>Mozilla Firefox, dernier ESR [1]</td> 
   <td>A : pris en charge</td> 
   <td>A : pris en charge</td> 
  </tr> 
  <tr> 
   <td>Apple Safari 12.x sous macOS</td> 
   <td>A : pris en charge</td> 
   <td>A : pris en charge</td> 
  </tr> 
  <tr> 
   <td>Apple Safari 11.x sous macOS</td> 
   <td>A : pris en charge</td> 
   <td>A : pris en charge</td> 
  </tr> 
  <tr> 
   <td>Apple Safari 10.x sous macOS</td> 
   <td>A : pris en charge</td> 
   <td>A : pris en charge</td> 
  </tr> 
  <tr> 
   <td>Apple Safari sur iOS 12.x</td> 
   <td>A : pris en charge [2]</td> 
   <td>Z : non pris en charge</td> 
  </tr> 
  <tr> 
   <td>Apple Safari sur iOS 11.x</td> 
   <td>A : pris en charge [2]</td> 
   <td>Z : non pris en charge</td> 
  </tr> 
  <tr> 
   <td>Apple Safari sur iOS 10.3</td> 
   <td>A : pris en charge [2]</td> 
   <td>Z : non pris en charge</td> 
  </tr> 
 </tbody> 
</table>

1. Version de prise en charge étendue de Firefox [En savoir plus à ce sujet sur mozilla.org](https://www.mozilla.org/fr-FR/firefox/organizations/faq/)
1. Prise en charge d’Apple iPad

### Navigateurs pris en charge pour les sites web {#supported-browsers-for-websites}

En règle générale, la prise en charge des navigateurs pour les sites web rendus par AEM Sites dépend de l’implémentation des modèles de page d’AEM, de la conception et de la sortie des composants, et relève donc de celui ou celle qui met en œuvre ces parties.

### Clients et clientes WebDAV {#webdav-clients}

**Microsoft Windows 7+**

Pour vous connecter avec Microsoft Windows 7 et les versions ultérieures à une instance AEM non sécurisée avec SSL, l’authentification de base sur un réseau non sécurisé doit être activée sous Windows. Cela nécessite une modification du registre Windows du WebClient :

1. Recherchez la sous-clé de registre :

   * HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\WebClient\Parameters

1. Ajoutez l’entrée de registre BasicAuthLevel à cette sous-clé à l’aide d’une valeur de 2 ou plus.

Voir [Microsoft Support KB 841215](https://support.microsoft.com/default.aspx/kb/841215).

Pour améliorer la réactivité du client WebDav sous Windows, voir [Microsoft Support KB 2445570](https://support.microsoft.com/kb/2445570)

## Remarques supplémentaires sur Platform {#additional-platform-notes}

Cette section contient des notes spéciales et des informations plus détaillées sur l’exécution d’Adobe Experience Manager et de ses modules complémentaires.

### IPv4 et IPv6 {#ipv-and-ipv}

Vous pouvez installer tous les éléments d’Adobe Experience Manager (instance, Dispatcher) sur des réseaux IPv4 et IPv6.

Tout fonctionne sans problème, dans la mesure où aucune configuration particulière n’est requise. Vous pouvez simplement spécifier une adresse IP au format approprié à votre type de réseau, le cas échéant.

Cela signifie que lorsqu’une adresse IP doit être indiquée, vous avez le choix entre les éléments suivants (suivant les besoins) :

* une adresse IPv6 ;

   par exemple `https://[ab12::34c5:6d7:8e90:1234]:4502`

* une adresse IPv4 ;

   par exemple `https://123.1.1.4:4502`

* un nom de serveur ;

   par exemple, `https://www.yourserver.com:4502`

* Le scénario par défaut de `localhost` sera interprété à la fois pour les installations réseau IPv4 et IPv6.

   par exemple, `http://localhost:4502`

### Exigences requises pour le module complémentaire AEM Dynamic Media {#requirements-for-aem-dynamic-media-add-on}

Par défaut, AEM Dynamic Media est désactivé. Voir [Activation de Dynamic Media](/help/assets/config-dynamic.md#enabling-dynamic-media).

Lorsque Dynamic Media est activé, la configuration système requise supplémentaire suivante s’applique :
>[!NOTE]
>
>La configuration requise suivante s’applique : **_only_** si vous utilisez le mode hybride de Dynamic Media ; Dynamic Media - Le mode hybride comporte un serveur d’images intégré, qui est certifié uniquement sur certains systèmes d’exploitation.
>
>Pour les clients Dynamic Media qui exécutent Dynamic Media en mode Scene7 (mode d’exécution **dynamicmedia_scene7**), il n’existe aucune exigence système supplémentaire spécifique ; la configuration requise est donc la même que pour AEM. Dynamic Media - L’architecture du mode Scene7 utilise le service d’images basé sur le cloud, et non le service incorporé dans AEM.

#### Matériel {#hardware}

Les exigences matérielles suivantes s’appliquent aux systèmes d’exploitation Linux et Windows :

* Processeur Intel Xeon ou AMD Opteron avec au moins 4 cœurs
* 16 Go de RAM au minimum

#### Linux {#linux}

L’utilisation de Dynamic Media sous Linux requiert les prérequis suivants :

* Red Hat Enterprise 7 ou CentOS 7 et versions ultérieures avec les derniers correctifs
* Système d’exploitation 64 bits
* Permutation désactivée (recommandé)
* SELinux désactivé (voir la note ci-dessous)

>[!NOTE]
>
>Si le paramètre régional est défini de telle sorte que LC_CTYPE n’est pas égal à en_US.UTF-8, cela empêchera le fonctionnement de Dynamic Media. Pour voir quelle est sa valeur, saisissez « locale » à l’invite de commande. Si elle n’est pas définie, définissez la variable d’environnement LC_CTYPE sur la chaîne vide en saisissant « export LC_CTYPE= » avant d’exécuter AEM.

>[!NOTE]
>
>**Désactivation de SELinux :** la diffusion d’images ne fonctionne pas lorsque SELinux est activé. Cette option est activée par défaut. Pour résoudre ce problème, modifiez le fichier **/etc/selinux/config** et modifiez la valeur SELinux à partir de :
>
>`SELINUX=enforcing` vers  `SELINUX=disabled`

>[!NOTE]
>
>**Architecture NUMA :** les systèmes dotés de processeurs AMD64 et Intel EM64T sont généralement configurés en tant que plateformes NUMA (Non Uniform Memory Architecture), ce qui signifie que le noyau construit plusieurs nœuds de mémoire au moment du démarrage plutôt que de construire un seul nœud de mémoire.
>
>La construction de plusieurs nœuds peut entraîner un épuisement de la mémoire sur un ou plusieurs nœuds avant que d’autres nœuds ne s’épuisent. Lorsque l’épuisement de la mémoire se produit, le noyau peut décider d’interrompre les processus (par exemple, la diffusion d’images ou le serveur de plateformes) même s’il existe de la mémoire disponible.
>
>Par conséquent, si vous exécutez un tel système, Adobe recommande de désactiver NUMA à l’aide de l’option de démarrage **numa=off** pour éviter que le noyau n’arrête ces processus.

>[!NOTE]
>
>**Le nom d’hôte du serveur doit pouvoir être résolu :** Assurez-vous que le nom d’hôte du serveur peut être résolu sur une adresse IP. Si cela n’est pas possible, ajoutez le nom d’hôte complet et l’adresse IP à la variable **/etc/hosts**:
>
>`<ip address> <fully qualified hostname>`

#### Windows {#windows}

* Microsoft Windows Server 2016
* Espace de permutation égal à au moins deux fois la quantité de mémoire physique (RAM)

Pour utiliser Dynamic Media sous Windows, les redistribuables Microsoft Visual Studio 2010, 2013 et 2015 pour x64 et x86 doivent être installés.

x64

* Le redistribuable Microsoft Visual Studio 2010 se trouve à l’adresse [https://www.microsoft.com/en-us/download/details.aspx?id=13523](https://www.microsoft.com/fr-fr/download/details.aspx?id=13523)
* Le redistribuable Microsoft Visual Studio 2013 est disponible à l’adresse [https://www.microsoft.com/en-us/download/details.aspx?id=40784](https://www.microsoft.com/fr-fr/download/details.aspx?id=40784)
* Le redistribuable Microsoft Visual Studio 2015 se trouve à l’adresse [https://www.microsoft.com/en-us/download/details.aspx?id=48145](https://www.microsoft.com/fr-fr/download/details.aspx?id=48145)

x86

* Le redistribuable Microsoft Visual Studio 2010 se trouve à l’adresse [https://www.microsoft.com/en-in/download/details.aspx?id=5555](https://www.microsoft.com/en-in/download/details.aspx?id=5555)
* Le redistribuable Microsoft Visual Studio 2013 est disponible à l’adresse [https://www.microsoft.com/en-in/download/details.aspx?id=40769](https://www.microsoft.com/en-in/download/details.aspx?id=40769)
* Le redistribuable Microsoft Visual Studio 2015 se trouve à l’adresse [https://www.microsoft.com/en-us/download/details.aspx?id=52685](https://www.microsoft.com/fr-fr/download/details.aspx?id=52685)

#### MacOS {#macos}

* 10.9.x et versions ultérieures
* Pris en charge uniquement à des fins d’évaluation et de démonstration

### Conditions requises pour AEM Forms PDF Generator {#requirements-for-aem-forms-pdf-generator}

<table> 
 <tbody> 
  <tr> 
   <th><p><strong>Produit</strong></p> </th> 
   <th><p><strong>Formats pris en charge pour la conversion en PDF</strong></p> </th> 
  </tr> 
  <tr> 
   <td><p><a href="https://helpx.adobe.com/fr/acrobat/release-note/release-notes-acrobat-reader.html">Suivi classique Acrobat 2017</a></p> </td> 
   <td><p>XPS, formats d’image (BMP, GIF, JPEG, JPG, TIF, TIFF, PNG, JPF, JPX, JP2, J2K, J2C, JPC), HTML, HTM, DWG, DXF et DWF</p> </td> 
  </tr> 
  <tr> 
   <td>Microsoft® Project 2016</td> 
   <td>MPP</td> 
  </tr> 
  <tr> 
   <td>Microsoft® Publisher 2016</td> 
   <td>PUB</td> 
  </tr> 
  <tr> 
   <td>Microsoft® Office Visio 2016</td> 
   <td>VSD</td> 
  </tr> 
  <tr> 
   <td>Microsoft® Office 2016</td> 
   <td>DOC, DOCX, XLS, XLSX, PPT, PPTX, RTF et TXT</td> 
  </tr> 
  <tr> 
   <td>Microsoft® Office 2013</td> 
   <td>DOC, DOCX, XLS, XLSX, PPT, PPTX, RTF et TXT</td> 
  </tr> 
  <tr> 
   <td>Corel WordPerfect X7</td> 
   <td>WP, WPD<br /> </td> 
  </tr> 
  <tr> 
   <td>OpenOffice 4.1.2</td> 
   <td>ODT, ODP, ODS, ODG, ODF, SXW, SXI, SXC, SXD, XLS, XLSX, DOC, DOCX, PPT, PPTX, formats d’image (BMP, GIF, JPEG, JPG, TIF, TIFF, PNG, JPF, JPX, JP2, J2K, J2C, JPC), HTML, HTM, RTF et TXT</td> 
  </tr> 
  <tr> 
   <td><p>OpenOffice 3.4</p> </td> 
   <td><p>ODT, ODP, ODS, ODG, ODF, SXW, SXI, SXC, SXD, XLS, XLSX, DOC, DOCX, PPT, PPTX, formats d’image (BMP, GIF, JPEG, JPG, TIF, TIFF, PNG, JPF, JPX, JP2, J2K, J2C, JPC), HTML, HTM, RTF et TXT</p> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>PDF Generator ne prend en charge que les versions allemande, anglaise, française et japonaise des systèmes d’exploitation et des applications pris en charge.
>
>En outre :
>
>* PDF Generator nécessite [Acrobat 2017 Classic track version 17.011.30078 ou ultérieure](https://helpx.adobe.com/fr/acrobat/release-note/release-notes-acrobat-reader.html) pour effectuer la conversion.
>* AEM Forms ne prend en charge que les versions 32 bits des logiciels pris en charge.
>* Les fonctionnalités de PDF OCR (PDF indexable), de Optimize PDF et d’Export PDF ne sont prises en charge que sous Microsoft Windows.
>* Le service HTML2PDF est obsolète sous AIX.
>* Les conversions de PDF Generator pour OpenOffice sont prises en charge uniquement sous Windows, Linux et Solaris.
>* Les fonctionnalités OCR PDF, Optimize PDF et Export PDF sont uniquement prises en charge sous Windows.
>* Une version d’Acrobat est fournie avec AEM Forms pour activer la fonctionnalité PDF Generator. La version groupée ne doit être accessible par programmation qu’avec AEM Forms, pendant la durée de la licence AEM Forms, pour une utilisation avec AEM Forms PDF Generator. Pour plus d’informations, voir la description du produit AEM Forms en fonction de votre déploiement ([On-Premise](https://helpx.adobe.com/fr/legal/product-descriptions/adobe-experience-manager-on-premise.html) ou [Managed Services](https://helpx.adobe.com/fr/legal/product-descriptions/adobe-experience-manager-managed-services.html)).
>


### Conditions requises pour AEM Forms Designer {#requirements-for-aem-forms-designer}

* Microsoft® Windows® 2012 Server R2, Microsoft® Windows® 2016 Server, Microsoft® Windows® 2019 Server, Microsoft® Windows® 10
* Processeur de 1 GHz ou plus avec prise en charge de PAE, NX et SSE2.
* Systèmes d’exploitation 32 bits : 1 Go de RAM ; systèmes d’exploitation 64 bits : 2 Go de RAM.
* Systèmes d’exploitation 32 bits : 16 Go d’espace disque ; systèmes d’exploitation 64 bits : 20 Go d’espace disque.
* Mémoire graphique – 128 Mo de GPU (256 Mo recommandé)
* 2,35 Go d’espace disponible sur le disque dur
* Résolution d’écran de 1 024 x 768 pixels ou plus
* Accélération matérielle de la vidéo (facultatif)
* Acrobat Pro DC, Acrobat Standard DC ou Adobe Acrobat Reader DC
* Droits d’administrateur pour l’installation de Designer

### Conditions requises pour l’écriture différée des métadonnées AEM Assets XMP {#requirements-for-aem-assets-xmp-metadata-write-back}

L’écriture différée XMP est prise en charge et activée pour les plateformes et formats de fichier suivants :

**Systèmes d’exploitation**

* Linux (32 bits, prise en charge des applications 32 bits requise sur les systèmes 64 bits). Pour les étapes d’installation des bibliothèques clientes 32 bits, consultez la section [Activation de l’écriture différée et de l’extraction XMP sous RedHat Linux 64 bits](https://helpx.adobe.com/fr/experience-manager/kb/enable-xmp-write-back-64-bit-redhat.html).

* Windows Server
* Oracle Solaris 
* Mac OS X (64 bits)

**Formats de fichier**

* JPEG
* PNG
* TIFF
* PDF
* INDD
* AI
* EPS

### Conditions requises pour le lecteur AEM Screens {#requirements-for-aem-screens-player}

La version 3.3.x du lecteur AEM Screens prend en charge les systèmes d’exploitation suivants :

* Microsoft Windows 10 Enterprise LTSB
* Google Chrome OS 62+
* Google Android 5.1.1 avec Android System WebView Version 52+ mise à jour
* Apple iOS 10.3+
* Apple macOS 10.12+
