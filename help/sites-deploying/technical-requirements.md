---
title: Exigences techniques
seo-title: Exigences techniques
description: Une liste de plateformes serveur et client prises en charge pour AEM.
seo-description: Une liste de plateformes serveur et client prises en charge pour AEM.
uuid: d5bdcd41-3585-41f7-860d-8068a2931a72
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: platform
discoiquuid: 4d3c4650-3e2a-43b1-ad2d-8d0ae2254ca9
translation-type: tm+mt
source-git-commit: 5e418ea537e00dc3b23174a7b1bb01dba0fc6b3a
workflow-type: tm+mt
source-wordcount: '3182'
ht-degree: 83%

---


# Exigences techniques{#technical-requirements}

Adobe prend en charge Adobe Experience Manager (AEM) sur les plateformes indiquées dans les informations suivantes de ce document.

Pour tout problème relatif à la plateforme proprement dite, contactez directement le fournisseur de la plateforme.

>[!NOTE]
>
>Selon le plateforme sur lequel vous avez installé AEM, il peut exister différents ensembles de critères d’exigences pour la gestion des utilisateurs. 

## Conditions préalables {#prerequisites}

Configuration minimale requise pour installer Adobe Experience Manager :

* Installation de la plateforme Java, du JDK Standard Edition ou d’autres [machines virtuelles Java ](#java-virtual-machines) prises en charge
* Fichier de démarrage rapide Experience Manager (JAR autonome ou WAR de déploiement de l’application web)

### Configuration minimale requise en matière d’espace disque et de mémoire {#minimum-sizing-requirements}

Configuration minimale requise pour l’exécution de Adobe Experience Manager :

* 5 Go d’espace disque disponible dans le répertoire d’installation
* Mémoire de 2 Go

>[!NOTE]
>
>* Les cas d’utilisation des ressources numériques nécessitent plus de mémoire de base. Voir [Deploiement et maintenance](/help/sites-deploying/deploy.md#default-local-install) pour plus de détails.
>* [Le module complémentaire AEM Forms](/help/forms/using/installing-configuring-aem-forms-osgi.md) nécessite 15 Go d’espace temporaire.

>



Pour plus d&#39;informations, consultez les [directives de dimensionnement du matériel](/help/managing/hardware-sizing-guidelines.md).

### Niveaux de prise en charge {#support-levels}

Ce document répertorie les plateformes client et serveur compatibles avec Adobe Experience Manager. Adobe fournit plusieurs niveaux de prise en charge, tant pour les configurations recommandées que pour les autres.

### Configurations prises en charge {#supported-configurations}

Adobe recommande ces configurations et assure un support complet dans le cadre du contrat de maintenance logicielle standard.

<table> 
 <tbody> 
  <tr> 
   <td>Niveau de prise en charge</td> 
   <td>Description<br /> </td> 
  </tr> 
  <tr> 
   <td><strong>A : Pris en charge</strong></td> 
   <td>Adobe fournit une prise en charge et une maintenance complètes pour cette configuration. Cette configuration est couverte par le processus d’assurance qualité d’Adobe.</td> 
  </tr> 
  <tr> 
   <td><strong>R : Prise en charge limitée </strong></td> 
   <td>Pour garantir la réussite des projets de ses clients, Adobe fournit une prise en charge complète dans le cadre d’un programme de prise en charge limitée, ce qui exige le respect de conditions spécifiques. Une prise en charge de niveau R exige une demande formelle de la part du client et la confirmation d’Adobe. Pour plus d’informations, contactez l’assistance clientèle d’Adobe.</td> 
  </tr> 
 </tbody> 
</table>

### Configurations non prises en charge {#unsupported-configurations}

| Niveau de prise en charge | Description |
|---|---|
| **Z : Non pris en charge** | La configuration n’est pas prise en charge. Adobe ne fait aucune déclaration quant au fonctionnement de la configuration et n’en assure pas la prise en charge. |

## Plateformes prises en charge {#supported-platforms}

### Machines virtuelles Java (JVM){#java-virtual-machines}

L’application nécessite l’exécution d’une machine virtuelle Java, laquelle est fournie par la distribution JDK (Java Development Kit).

Adobe Experience Manager fonctionne avec les versions suivantes des machines virtuelles Java :

>[!CAUTION]
>
>Il est conseillé de consulter les bulletins de sécurité publiés par l’éditeur Java afin de garantir la sécurité des environnements de production et d’installer les mises à jour Java les plus récentes.

<table> 
 <tbody> 
  <tr> 
   <td>Plate-forme</td> 
   <td>Niveau de prise en charge<br /> </td> 
  </tr> 
  <tr> 
   <td>Oracle Java SE 11 JDK [1]</td> 
   <td>Z : Non pris en charge </td> 
  </tr> 
  <tr> 
   <td>Oracle Java SE 10 JDK [1]</td> 
   <td>Z : Non pris en charge </td> 
  </tr> 
  <tr> 
   <td>Oracle Java SE 9 JDK [1]</td> 
   <td>Z : Non pris en charge</td> 
  </tr> 
  <tr> 
   <td><strong>Oracle Java SE 8 JDK – 64 bits</strong></td> 
   <td>A : Pris en charge [3]<br /> </td> 
  </tr> 
  <tr> 
   <td>Machine virtuelle IBM J9 – Version 2.9, JRE 1.8.0 [2]</td> 
   <td>A : Pris en charge</td> 
  </tr> 
  <tr> 
   <td>Machine virtuelle IBM J9 – Version 2.8, JRE 1.8.0 [2]</td> 
   <td>A : Pris en charge</td> 
  </tr> 
 </tbody> 
</table>

1. Oracle est passé à un modèle de support à long terme (LTS) pour les produits Oracle Java SE. Java 9 et 10 ne sont pas des versions de LTS par Oracle (voir [Oracle Java SE support roadmap](https://www.oracle.com/technetwork/java/eol-135779.html)). Adobe assure uniquement la prise en charge des versions LTS de Java pour exécuter AEM en production.

1. IBM JRE est pris en charge uniquement avec WebSphere Application Server.
1. La prise en charge et la distribution du JDK Oracle Java SE, y compris toutes les mises à jour de maintenance des versions LTS après la fin des mises à niveau publiques, seront directement prises en charge par Adobe pour tous les clients AEM utilisant la technologie Oracle Java SE. Pour plus d’informations, voir la [prise en charge Java Oracle pour Adobe Experience Manager Q&amp;A](assets/adobe-oracle-java-license-agreement.pdf).

### Stockage et persistance {#storage-persistence}

Plusieurs options sont disponibles pour déployer le référentiel d’Adobe Experience Manager. Consultez la liste suivante pour connaître les options de stockage et les technologies prises en charge.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Plate-forme</strong></td> 
   <td><strong>Description</strong></td> 
   <td><strong>Niveau de prise en charge</strong></td> 
  </tr> 
  <tr> 
   <td><strong>Système de fichiers avec fichiers TAR [1]</strong></td> 
   <td>Référentiel</td> 
   <td>A : Pris en charge </td> 
  </tr> 
  <tr> 
   <td><strong>Système de fichiers avec banque de données [1]</strong></td> 
   <td>Binaires</td> 
   <td>A : Pris en charge</td> 
  </tr> 
  <tr> 
   <td>Stockage de binaires dans des fichiers TAR sur le système de fichiers [1]</td> 
   <td>Binaires</td> 
   <td>Z : Non pris en charge pour la production</td> 
  </tr> 
  <tr> 
   <td>Amazon S3</td> 
   <td>Binaires</td> 
   <td>A : Pris en charge</td> 
  </tr> 
  <tr> 
   <td>Stockage Microsoft Azure Blob</td> 
   <td>Binaires</td> 
   <td>A : Pris en charge</td> 
  </tr> 
  <tr> 
   <td>MongoDB Enterprise 3.6  [5, 6]</td> 
   <td>Référentiel</td> 
   <td>A : Pris en charge  avec limites</td> 
  </tr> 
  <tr> 
   <td>MongoDB Enterprise 3.4 [2, 3, 6]</td> 
   <td>Référentiel</td> 
   <td>A : Pris en charge  avec limites</td> 
  </tr> 
  <tr> 
   <td>MySQL 5.7</td> 
   <td>Base de données de formulaires</td> 
   <td>A : Pris en charge</td> 
  </tr> 
  <tr> 
   <td>IBM DB2 11.1<br /> </td> 
   <td>Base de données de formulaires</td> 
   <td>A : Pris en charge</td> 
  </tr> 
  <tr> 
   <td>IBM DB2 10.5</td> 
   <td>Base de données de formulaires et de référentiels</td> 
   <td>R : Prise en charge limitée (4)</td> 
  </tr> 
  <tr> 
   <td>Base de données Oracle 12c (12.1.x)</td> 
   <td>Base de données de formulaires et de référentiels</td> 
   <td>R : Prise en charge limitée</td> 
  </tr> 
  <tr> 
   <td>Microsoft SQL Server 2017</td> 
   <td>Base de données de formulaires</td> 
   <td>Z : Non pris en charge (4)</td> 
  </tr> 
  <tr> 
   <td>Microsoft SQL Server 2016</td> 
   <td>Base de données de formulaires</td> 
   <td>A : Pris en charge</td> 
  </tr> 
  <tr> 
   <td>Microsoft SQL Server 2014</td> 
   <td>Base de données de formulaires</td> 
   <td>R : Prise en charge limitée (4)</td> 
  </tr> 
  <tr> 
   <td><strong>Apache Lucene (démarrage rapide intégré)</strong></td> 
   <td>Service de recherche</td> 
   <td>A : Pris en charge</td> 
  </tr> 
  <tr> 
   <td>Apache Solr</td> 
   <td>Service de recherche</td> 
   <td>A : Pris en charge</td> 
  </tr> 
 </tbody> 
</table>

1. Le système de fichiers comprend le stockage de bloc compatible avec POSIX. Cela inclut la technologie de stockage réseau. Notez que les performances du système de fichiers sont variables et ont une incidence sur les performances globales. Il est conseillé d’effectuer un test de charge d’AEM avec le système de fichiers distant/réseau.
1. La fragmentation MongoDB n’est pas pris en charge dans AEM. 
1. Seule le moteur de stockage MongoDB WiredTiger est prise en charge. 
1. AEM Forms n’est pas pris en charge.
1. MongoDB Enterprise 3.6 est pris en charge à partir d’AEM version 6.4.2.0.
1. La prise en charge de MongoDB 3.4 a atteint la fin de vie (EOL), tandis que MongoDB 3.6 devrait atteindre EOL le 30 avril 2021. Veuillez noter que l&#39;Adobe ne fournira qu&#39;un soutien pour AEM problèmes liés aux produits.

>[!NOTE]
>
>Voir [Déploiement de Communities](/help/communities/deploy-communities.md) pour plus d’informations sur les fonctionnalités d’AEM Communities.

>[!NOTE]
>
>MongoDB est un logiciel tiers qui n’est pas inclus dans le pack de licences AEM. Pour plus d’informations, consultez la page relative à la stratégie de gestion des licences MongoDB ([MongoDB licensing policy](https://www.mongodb.org/about/licensing/)).
>
>Pour tirer pleinement parti de votre déploiement AEM avec MongoDB, Adobe conseille d’utiliser la version MongoDB Enterprise sous licence afin de bénéficier d’une assistance professionnelle. Voir [Déploiements recommandés](/help/sites-deploying/recommended-deploys.md#prerequisites-and-recommendations-when-deploying-aem-with-mongomk) pour plus d&#39;informations.
>
>La licence comprend un ensemble de répliques, composé d’une instance principale et de deux instances secondaires qui peuvent être utilisées pour les déploiements de création ou de publication.
>
>Si vous souhaitez créer des déploiements de création et de publication sur MongoDB, vous devez acheter deux licences distinctes.
>
>Vous obtiendrez auprès de l’assistance clientèle d’Adobe une aide adaptée aux problèmes admissibles relatifs à l’utilisation de MongoDB avec AEM.
>
>Pour plus d’informations, consultez la page [MongoDB pour Adobe Experience Manager](https://www.mongodb.com/lp/contact/mongodb-adobe-experience-manager).

>[!NOTE]
>
>Les bases de données relationnelles prises en charge, telles qu’elles sont répertoriées ci-dessus, sont des logiciels tiers qui ne sont pas inclus dans le pack de licences AEM.
>
>Pour pouvoir exécuter AEM 6.4 avec une base de données relationnelle prise en charge, un contrat d’assistance distinct auprès d’un fournisseur de base de données est requis. Vous obtiendrez auprès de l’assistance clientèle d’Adobe une aide adaptée aux problèmes admissibles relatifs à l’utilisation des bases de données relationnelles avec AEM 6.4.
>
>**Notez que, pour l’heure, la plupart des bases de données relationnelles bénéficient du niveau de prise en charge R sur AEM 6.4. Cette version s’accompagne des critères et d’un programme de prise en charge, comme indiqué dans la description du niveau R ci-dessus.**

### Moteurs de servlet / Serveurs d’applications  {#servlet-engines-application-servers}

Adobe Experience Manager peut s’exécuter comme serveur autonome (fichier JAR de démarrage rapide) ou comme application web avec un serveur d’applications tiers (fichier WAR).

La version d’API de servlet minimum requise est 3.1, mais elle doit être au-dessous de 4.0.

| Plate-forme | Niveau de prise en charge |
|---|---|
| **Moteur de servlet intégré au fichier de démarrage rapide (Jetty 9.3)** | A : Pris en charge |
| Oracle WebLogic Server 12.2 (12cR2) | A : Pris en charge |
| IBM WebSphere Application Server en livraison continue (LibertyProfile) avec Web Profile 7.0 et IBM JRE 1.8 | A : Pris en charge |
| IBM WebSphere Application Server 9.0 | A : Pris en charge |
| Apache Tomcat 8.5.x | A : Pris en charge |
| JBoss EAP 7.1.0 avec JBoss Application Server  | A : Pris en charge (1) |
| JBoss EAP 7.0.0 avec JBoss Application Server  | A : Pris en charge |

1. AEM Forms n’est pas pris en charge.

### Systèmes d’exploitation serveur {#server-operating-systems}

Adobe Experience Manager fonctionne avec les plates-formes serveur suivantes :

<table> 
 <tbody> 
  <tr> 
   <td><strong>Plate-forme</strong></td> 
   <td><strong>Niveau de prise en charge</strong></td> 
  </tr> 
  <tr> 
   <td><strong>Linux, en fonction de la distribution Red Hat </strong></td> 
   <td>A : Pris en charge (1)</td> 
  </tr> 
  <tr> 
   <td>Linux, en fonction de la distribution Debian, y compris Ubuntu</td> 
   <td>A : Pris en charge (4)</td> 
  </tr> 
  <tr> 
   <td>Linux, en fonction de la distribution SUSE</td> 
   <td>A : Pris en charge</td> 
  </tr> 
  <tr> 
   <td>Microsoft Windows Server 2016</td> 
   <td>A : Pris en charge</td> 
  </tr> 
  <tr> 
   <td>Microsoft Windows Server 2012 R2</td> 
   <td>A : Pris en charge</td> 
  </tr> 
  <tr> 
   <td>Oracle Solaris 11</td> 
   <td>A : Pris en charge avec des restrictions (3,5,7)<br /> R : Prise en charge limitée pour les nouveaux contrats</td> 
  </tr> 
  <tr> 
   <td>IBM AIX 7.2</td> 
   <td>A : Pris en charge avec des restrictions (2,5,7)<br /> R : Prise en charge limitée pour les nouveaux contrats</td> 
  </tr> 
 </tbody> 
</table>

1. Linux Kernel 2.6, 3.x et 4.x inclut des dérivés de la distribution Red Hat, y compris Red Hat Enterprise Linux, CentOS, Oracle Linux et Amazon Linux. Les fonctions de module complémentaire AEM Forms sont uniquement prises en charge sur CentOS 7 et Red Hat Enterprise Linux 7.
1. AEM Assets : Veuillez consulter la section [Prise en charge pour l’écriture différée des métadonnées XMP](#requirements-for-aem-assets-xmp-metadata-write-back)
1. AEM Assets : Pas de prise en charge pour l’imagerie Dynamic Media. Le service vidéo de média dynamique est pris en charge.
1. AEM Forms est pris en charge uniquement sur Ubuntu 16.04 LTS.
1. AEM Assets : Pas de prise en charge pour [ la transformation de fichiers bruts](/help/assets/camera-raw.md)
1. AEM Forms : Pas de prise en charge pour l’environnement de production
1. AEM Assets : Pas de prise en charge pour [ PDF Rasterizer amélioré](/help/assets/aem-pdf-rasterizer.md)
1. AEM Forms : Non pris en charge

### Environnements virtuels et de cloud computing {#virtual-cloud-computing-environments}

Adobe Experience Manager exécuté sur une machine virtuelle sur des environnements de cloud computing, tels que Microsoft Azure et Amazon Web Services (AWS), est pris en charge conformément aux exigences techniques répertoriées sur cette page, et d’après les conditions de prise en charge standard d’Adobe.

Adobe recommande l’utilisation d’Adobe Managed Services pour déployer AEM sur Azure ou AWS. Adobe Managed Services fournit aux experts les compétences nécessaires pour déployer et utiliser AEM dans ces environnements de cloud computing. Veuillez consulter nos [documents complémentaires sur Adobe Managed Services](https://www.adobe.com/marketing-cloud/enterprise-content-management/managed-services-cloud-platform.html?aemClk=t).

Dans tous les autres cas, lorsqu’AEM est déployé sur Azure ou AWS, ou tout autre environnement de cloud computing, la prise en charge d’Adobe sera limitée à l’environnement informatique virtuel, conformément aux caractéristiques techniques répertoriées sur cette page. Tout problème signalé lié à l’exécution d’AEM dans ces environnements cloud devra être reproductible indépendamment de tout service cloud spécifique à l’environnement de cloud computing, à moins que le service cloud ne soit spécifiquement pris en charge dans le cadre des exigences techniques répertoriées sur cette page, par exemple le stockage Azure Blob ou AWS S3.

Pour des recommandations sur le déploiement d’AEM sur Azure ou AWS, en dehors d’Adobe Managed Services, nous vous recommandons vivement de travailler directement avec votre fournisseur cloud ou avec l’un des partenaires Adobe prenant en charge le déploiement d’AEM dans l’environnement de cloud de votre choix. Le partenaire ou fournisseur cloud que vous choisissez est responsable du dimensionnement, de la conception et de l’implémentation de l’architecture, et ce, pour répondre à vos besoins spécifiques en matière de performance, de chargement, d’évolutivité et de sécurité.

### Plateformes Dispatcher (serveurs web)  {#dispatcher-platforms-web-servers}

Dispatcher est le composant de mise en cache et d’équilibrage de charge. [Téléchargez la dernière version de Dispatcher](https://helpx.adobe.com/experience-manager/dispatcher/release-notes.html). Experience Manager 6.4 nécessite Dispatcher version 4.3.1 ou ultérieure.

L’utilisation des serveurs web ci-dessous est prise en charge avec Dispatcher version 4.3.1 :

| Plate-forme | Niveau de prise en charge |
|---|---|
| **Apache httpd 2.4.x**  (voir aussi 1,2 ci-dessous) | A : Pris en charge |
| Microsoft IIS 10 (Internet Information Server) | A : Pris en charge |
| Microsoft IIS 8.5 (Internet Information Server) | A : Pris en charge |

1. Les serveurs web développés sur la base du code source Apache httpd bénéficieront du même niveau de prise en charge que la version de httpd sur laquelle ils sont basés : En cas de doute, demandez à Adobe de confirmer le niveau de prise en charge relatif au produit serveur correspondant. Cas suivants :

   1. le serveur HTTP a été développé en utilisant uniquement les distributions source Apache officielles; ou
   1. le serveur HTTP a été distribué comme composant du système d’exploitation sur lequel il est exécuté. Exemples : Serveur IBM HTTP, Serveur Oracle HTTP 

1. Dispatcher n’est pas disponible pour Apache 2.4.x sur les systèmes d’exploitation Windows.

## Plateformes clientes prises en charge {#supported-client-platforms}

### Navigateurs pris en charge pour l’interface utilisateur de création {#supported-browsers-for-authoring-user-interface}

L’interface utilisateur d’Adobe Experience Manager fonctionne avec les plates-formes clientes suivantes : Tous les navigateurs sont testés avec l’ensemble par défaut de modules complémentaires et externes.

L’interface utilisateur d’AEM est optimisée en vue d’une utilisation sur des grands écrans (ordinateurs portables et de bureau) et sur des tablettes (du type Apple iPad ou Microsoft Surface). Le format « téléphone » n’est pas pris en charge.

>[!NOTE]
>
>**Prise en charge des navigateurs mis à jour fréquemment :**
>
>Mozilla Firefox, Google Chrome and Microsoft Edge publient des mises à jour tous les quelques mois. Adobe s’engage à fournir des mises à jour pour Adobe Experience Manager afin de conserver le niveau de prise en charge indiqué ci-dessous avec les versions à venir de ces navigateurs.

<table> 
 <tbody> 
  <tr> 
   <td><strong>Navigateur</strong></td> 
   <td><strong>Prise en charge de l’interface utilisateur<br /> </strong></td> 
   <td><strong>Prise en charge de l’interface utilisateur classique</strong></td> 
  </tr> 
  <tr> 
   <td><strong>Google Chrome (Evergreen)</strong></td> 
   <td>A : Pris en charge</td> 
   <td>A : Pris en charge</td> 
  </tr> 
  <tr> 
   <td>Microsoft Edge (Evergreen)</td> 
   <td>A : Pris en charge</td> 
   <td>A : Pris en charge</td> 
  </tr> 
  <tr> 
   <td>Microsoft Internet Explorer 11</td> 
   <td>A : Pris en charge</td> 
   <td>A : Pris en charge</td> 
  </tr> 
  <tr> 
   <td>Mozilla Firefox (Evergreen)</td> 
   <td>A : Pris en charge</td> 
   <td>A : Pris en charge</td> 
  </tr> 
  <tr> 
   <td>Mozilla Firefox, dernière version Extended Support Release (ESR) [1]</td> 
   <td>A : Pris en charge</td> 
   <td>A : Pris en charge</td> 
  </tr> 
  <tr> 
   <td>Apple Safari 12.x sur macOS</td> 
   <td>A : Pris en charge</td> 
   <td>A : Pris en charge</td> 
  </tr> 
  <tr> 
   <td>Apple Safari 11.x sur macOS</td> 
   <td>A : Pris en charge</td> 
   <td>A : Pris en charge</td> 
  </tr> 
  <tr> 
   <td>Apple Safari 10.x sur macOS</td> 
   <td>A : Pris en charge</td> 
   <td>A : Pris en charge</td> 
  </tr> 
  <tr> 
   <td>Apple Safari sur iOS 12.x</td> 
   <td>A : Pris en charge [2]</td> 
   <td>Z : Non pris en charge</td> 
  </tr> 
  <tr> 
   <td>Apple Safari sur iOS 11.x</td> 
   <td>A : Pris en charge [2]</td> 
   <td>Z : Non pris en charge</td> 
  </tr> 
  <tr> 
   <td>Apple Safari sur iOS 10.3</td> 
   <td>A : Pris en charge [2]</td> 
   <td>Z : Non pris en charge</td> 
  </tr> 
 </tbody> 
</table>

1. Version ESR (Extended Support Release) de Firefox. [Plus d’informations à ce sujet sur mozilla.org](https://www.mozilla.org/en-US/firefox/organizations/faq/)
1. Prise en charge pour Apple iPad

### Navigateurs pris en charge pour les sites web  {#supported-browsers-for-websites}

En règle générale, la prise en charge du navigateur pour les sites web rendus par AEM Sites dépend de la mise en œuvre des modèles de pages AEM, de la conception et de la sortie des composants. Par conséquent, la responsabilité en revient à celui qui met en œuvre ces composants.

### Clients WebDAV  {#webdav-clients}

**Microsoft Windows 7+**

Pour se connecter avec Microsoft Windows 7 et versions ultérieures à une instance AEM qui n’est pas sécurisée avec SSL, il faut qu’une authentification de base sur un réseau non sécurisé soit activée dans Windows. Pour ce faire, une modification est nécessaire dans le Registre Windows de WebClient :

1. Localisez la sous-clé du Registre :

   * HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\WebClient\Parameters

1. Ajoutez l’entrée de Registre BasicAuthLevel à cette sous-clé en lui attribuant une valeur de 2 (ou plus élevée).

Reportez-vous à l’article [841215 de la Base de connaissances d’assistance Microsoft](https://support.microsoft.com/default.aspx/kb/841215).

Pour améliorer la réactivité du client WebDav sous Windows, consultez l’article [2445570 de la Base de connaissances d’assistance Microsoft](https://support.microsoft.com/kb/2445570).

## Autres remarques relatives aux plates-formes  {#additional-platform-notes}

Vous trouverez dans cette section des remarques et des informations plus détaillées concernant l’exécution d’Adobe Experience Manager et de ses modules complémentaires.

### IPv4 et IPv6  {#ipv-and-ipv}

Tous les éléments d’Adobe Experience Manager (Instance, Dispatcher) peuvent être installés sur des réseaux IPv4 et IPv6.

Tout fonctionne sans problème, dans la mesure où aucune configuration particulière n’est requise. Si nécessaire, vous pouvez simplement indiquer une adresse IP suivant le format approprié au type de réseau.

Cela signifie que lorsqu’une adresse IP doit être indiquée, vous avez le choix entre (suivant les besoins) :

* une adresse IPv6

   par exemple `https://[ab12::34c5:6d7:8e90:1234]:4502`

* une adresse IPv4

   par exemple `https://123.1.1.4:4502`

* un nom de serveur ;

   par exemple, `https://www.yourserver.com:4502`

* la casse par défaut de `localhost` sera interprétée pour les installations réseau IPv4 et IPv6.

   par exemple, `http://localhost:4502`

### Configuration requise pour le module complémentaire AEM Dynamic Media {#requirements-for-aem-dynamic-media-add-on}

Par défaut, AEM Dynamic Media est désactivé. Voir [Activation de Dynamic Media](/help/assets/config-dynamic.md#enabling-dynamic-media).

Lorsque Dynamic Media est activé, les autres configurations requises suivantes s’appliquent :
>[!NOTE]
>
>La configuration requise suivante s&#39;applique **_uniquement_** si vous utilisez le mode Dynamic Media - Hybrid ; Dynamic Media - Le mode hybride est doté d’un serveur d’images intégré, qui est uniquement certifié sur certains systèmes d’exploitation.
>
>Pour les clients Dynamic Media qui exécutent le mode Dynamic Media – Scene7 (mode d’exécution **dynamicmedia_scene7**), il n’existe aucune exigence système supplémentaire spécifique ; la configuration requise est donc la même que pour AEM. L’architecture du mode Dynamic Media – Scene7 utilise le service d’images basé sur le cloud, et non celui intégré dans AEM.

#### Matériel {#hardware}

Les exigences matérielles suivantes s’appliquent aux systèmes d’exploitation Linux et Windows :

* Processeur Intel Xeon ou AMD Opteron avec au moins 4 cœurs
* 16 Go de mémoire vive (RAM) au minimum

#### Linux {#linux}

L’utilisation de Dynamic Media sous Linux requiert les conditions préalables suivantes :

* RedHat Enterprise 7 ou CentOS 7 et versions ultérieures avec les derniers correctifs
* Système d’exploitation 64 bits
* Échange désactivé (recommandé)
* SELinux désactivé (voir la remarque ci-dessous)

>[!NOTE]
>
>Si les paramètres locaux sont définis de sorte que LC_CTYPE n’est pas égal à en_US.UTF-8, cela empêchera Dynamic Media de fonctionner. Pour connaître sa valeur, saisissez &quot;locale&quot; à l’invite de commande. Si la configuration est différente, définissez la variable d’environnement LC_CTYPE sur la chaîne vide en saisissant &quot;export LC_CTYPE=&quot; avant d’exécuter AEM.

>[!NOTE]
>
>**Disabling SELinux (Désactiver SELinux) :** La diffusion d’images ne fonctionne pas lorsque SELinux est activé. Cette option est activée par défaut. Pour remédier à ce problème, modifiez le fichier **/etc/selinux/config** et définissez la valeur SELinux comme suit :
>
>`SELINUX=enforcing` vers  `SELINUX=disabled`

>[!NOTE]
>
>**Architecture NUMA :** Les systèmes équipés de processeurs à architecture AMD64 et Intel EM64T sont généralement configurés comme des plates-formes NUMA (Non Uniform Memory Architecture). Cela signifie que le noyau construit plusieurs nœuds de mémoire lors du démarrage, plutôt que d’en construire un seul.
>
>Cette construction à plusieurs nœuds peut entraîner un épuisement de la mémoire sur un ou plusieurs des nœuds avant l’épuisement des autres. Lorsqu’un épuisement de la mémoire se produit, le noyau peut décider de terminer des processus (Image Server ou Platform Server, par exemple), bien que de la mémoire soit disponible.
>
>Si vous utilisez un système de ce type, Adobe vous conseille donc de désactiver l’architecture NUMA à l’aide de l’option de démarrage **numa=off** afin d’éviter que le noyau termine ces processus.

>[!NOTE]
>
>**Le nom d’hôte du seveur doît être résolvable :** Veillez à ce que le nom de hôte du serveur soit résolvable sur une adresse IP. Si cela s’avère impossible, ajoutez le nom d’hôte complet et l’adresse IP à **/etc/hosts** :
>
>`<ip address> <fully qualified hostname>`

#### Windows {#windows}

* Microsoft Windows Server 2016
* Espace d’échange égal à au moins deux fois la quantité de mémoire physique (RAM).

Pour utiliser Dynamic Media sous Windows, Microsoft Visual Studio 2010, 2013 et 2015 redistributables pour x64 et x86 doit être installé.

x64

* La redistribuable de Microsoft Visual Studio 2010 se trouve à l&#39;adresse [https://www.microsoft.com/en-us/download/details.aspx?id=13523](https://www.microsoft.com/fr-fr/download/details.aspx?id=13523)
* La redistribuable de Microsoft Visual Studio 2013 peut être consultée à l’adresse [https://www.microsoft.com/en-us/download/details.aspx?id=40784](https://www.microsoft.com/fr-fr/download/details.aspx?id=40784)
* La redistribuable de Microsoft Visual Studio 2015 se trouve à l&#39;adresse [https://www.microsoft.com/en-us/download/details.aspx?id=48145](https://www.microsoft.com/fr-fr/download/details.aspx?id=48145)

x86

* La redistribuable de Microsoft Visual Studio 2010 se trouve à l&#39;adresse [https://www.microsoft.com/en-in/download/details.aspx?id=5555](https://www.microsoft.com/en-in/download/details.aspx?id=5555)
* La redistribuable de Microsoft Visual Studio 2013 peut être consultée à l’adresse [https://www.microsoft.com/en-in/download/details.aspx?id=40769](https://www.microsoft.com/en-in/download/details.aspx?id=40769)
* La redistribuable de Microsoft Visual Studio 2015 se trouve à l&#39;adresse [https://www.microsoft.com/en-us/download/details.aspx?id=52685](https://www.microsoft.com/fr-fr/download/details.aspx?id=52685)

#### Mac OS {#macos}

* Versions 10.9.x et ultérieures
* Pris en charge uniquement à des fins d’évaluation et de démonstration

### Exigences pour le générateur de PDF AEM Forms  {#requirements-for-aem-forms-pdf-generator}

<table> 
 <tbody> 
  <tr> 
   <th><p><strong>Produit</strong></p> </th> 
   <th><p><strong>Formats pris en charge pour la conversion en PDF</strong></p> </th> 
  </tr> 
  <tr> 
   <td><p><a href="https://helpx.adobe.com/acrobat/release-note/release-notes-acrobat-reader.html">Acrobat 2017 suivi Classic</a></p> </td> 
   <td><p>XPS, formats d’image (BMP, GIF, JPEG, JPG, TIF, TIFF, PNG, JPF, JPX, JP2, J2K, J2C, JPC), HTML, HTM, DWG, DXF et DWF</p> </td> 
  </tr> 
  <tr> 
   <td>Microsoft® Project 2016</td> 
   <td>MPP</td> 
  </tr> 
  <tr> 
   <td>Microsoft® Publisher 2016</td> 
   <td>PUB</td> 
  </tr> 
  <tr> 
   <td>Microsoft® Office Visio 2016</td> 
   <td>VSD</td> 
  </tr> 
  <tr> 
   <td>Microsoft® Office 2016</td> 
   <td>DOC, DOCX, XLS, XLSX, PPT, PPTX, RTF et TXT</td> 
  </tr> 
  <tr> 
   <td>Microsoft® Office 2013</td> 
   <td>DOC, DOCX, XLS, XLSX, PPT, PPTX, RTF et TXT</td> 
  </tr> 
  <tr> 
   <td>Corel WordPerfect X7</td> 
   <td>WP, WPD<br /> </td> 
  </tr> 
  <tr> 
   <td>OpenOffice 4.1.2</td> 
   <td>ODT, ODP, ODS, ODG, ODF, SXW, SXI, SXC, SXD, XLS, XLSX, DOC, DOCX, PPT, PPTX, formats d’image (BMP, GIF, JPEG, JPG, TIF, TIFF, PNG, JPF, JPX, JP2, J2K, J2C, JPC, HTML, HTM RTF et TXT</td> 
  </tr> 
  <tr> 
   <td><p>OpenOffice 3.4</p> </td> 
   <td><p>ODT, ODP, ODS, ODG, ODF, SXW, SXI, SXC, SXD, XLS, XLSX, DOC, DOCX, PPT, PPTX, formats d’image (BMP, GIF, JPEG, JPG, TIF, TIFF, PNG, JPF, JPX, JP2, J2K, J2C, JPC, HTML, HTM RTF et TXT</p> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>PDF Generator prend en charge uniquement les versions en anglais, français, allemand et japonais des applications et des systèmes d’exploitation pris en charge.
>
>En outre :
>
>* PDF Generator nécessite [Acrobat 2017 suivi Classic version 17.011.30078 ou ultérieure](https://helpx.adobe.com/acrobat/release-note/release-notes-acrobat-reader.html) pour effectuer la conversion.
>* AEM Forms prends en charge uniquement les éditions 32 bits du logiciel pris en charge.
>* Les fonctionnalités OCR PDF (PDF où l’on peut effectuer une recherche), Optimize PDF, et Export PDF sont prises en charge uniquement sous Microsoft Windows.
>* Le service HTML2PDF est obsolète sous AIX.
>* Les conversions de PDF Generator pour OpenOffice sont uniquement prises en charge sous Windows, Linux et Solaris.
>* Les fonctionnalités OCR PDF, Optimize PDF et Export PDF sont prises en charge uniquement sous Windows.
>* Une version d’Acrobat est fournie avec AEM Forms pour permettre la fonctionnalité PDF Generator. La version groupée ne doit être accessible que par programmation et uniquement avec AEM Forms, pendant le terme de la licence AEM Forms pour l’utilisation avec AEM Forms PDF Generator. Pour plus d&#39;informations, reportez-vous à la description du produit AEM Forms selon votre déploiement ([Sur site](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-on-premise.html) ou [Managed Services](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-managed-services.html))&quot;.

>



### Exigences pour l’écriture en différée des métadonnées XMP AEM Assets {#requirements-for-aem-assets-xmp-metadata-write-back}

L’écriture différée XMP est prise en charge et activée pour les plateformes et formats de fichier suivants :

**Systèmes d’exploitation**

* Linux (32 bits, prise en charge des applications 32 bits nécessaire sur les systèmes 64 bits). Pour connaître les étapes d’installation des bibliothèques clientes 32 bits, voir [Comment activer l’extraction XMP et la réécriture sur RedHat Linux 64 bits](https://helpx.adobe.com/experience-manager/kb/enable-xmp-write-back-64-bit-redhat.html).

* Windows Server
* Oracle Solaris
* Mac OS X (64 bits)

**Formats de fichier**

* JPEG
* PNG
* TIFF
* PDF
* INDD
* AI
* EPS

### Exigences pour le lecteur AEM Screens  {#requirements-for-aem-screens-player}

Le lecteur AEM Screens version 3.3.x prend en charge les systèmes d’exploitation suivants :

* Microsoft Windows 10 Enterprise LTSB
* Google Chrome OS 62+
* Google Android 5.1.1 avec mise à jour d&#39;Android System WebView version 52+
* Apple iOS 10.3+
* Apple macOS 10.12+
