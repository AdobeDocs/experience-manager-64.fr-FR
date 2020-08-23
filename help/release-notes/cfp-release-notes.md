---
title: Notes de mise à jour cumulées du pack de correctifs AEM 6.4
description: Notes de mise à jour spécifiques aux packs de correctifs cumulés Adobe Experience Manager 6.4.
contentOwner: AK
mini-toc-levels: 1
translation-type: tm+mt
source-git-commit: b698a1348df3ec2ab455c236422784d10cbcf7c2
workflow-type: tm+mt
source-wordcount: '2158'
ht-degree: 24%

---


# Notes de mise à jour cumulées du pack de correctifs AEM 6.4 {#aem-cumulative-fix-pack-release-notes}

## Informations sur la version {#release-information}

| Produits | **Adobe Experience Manager (AEM) 6.4** |
|---|---|
| Version | 6.4.8.1 |
| Type | Pack de correctifs cumulés  |
| Date | 4 juin 2020 |
| Condition requise | [AEM 6.4 Service Pack 8 (6.4.8.0)](sp-release-notes.md) |
| URL de téléchargement | aem 6.4.8.1 sur la distribution de [logiciels](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq640%2Fcumulativefixpack%2Faem-6.4.8-cfp-1.0.zip) |

## Fonctionnalités présentes dans AEM 6.4.8.1 {#what-s-included-in-aem}

aem Cumulative Fix Pack 6.4.8.1 est une mise à jour importante qui comprend plusieurs correctifs internes et clients depuis la disponibilité générale d&#39;AEM 6.4 Service Pack 8 (6.4.8.0) en mars 2020.

aem Cumulative Fix Pack 6.4.8.1 dépend de AEM 6.4 Service Pack 8. Par conséquent, vous devez installer AEM Cumulative Fix Pack 6.4.8.1 après avoir installé AEM 6.4 Service Pack 8.

Voici quelques-uns des points saillants de l&#39;AEM 6.4.8.1 :

* Suppression de l’intégration Package Share avec Adobe Experience Manager.
* Le référentiel intégré (Apache Jackrabbit Oak) a été mis à niveau vers la version 1.8.21.

For information on CFP and other types of releases, see [AEM Update Release Vehicle Definitions](../sites-deploying/update-release-vehicle-definitions.md)

## Liste des modifications         {#list-of-changes}

Adobe Experience Manager 6.4.8.1 apporte des correctifs aux problèmes suivants.

### Sites {#sites-6481}

* Lorsque le nom d&#39;un composant local d&#39;un LiveCopy est identique au nom d&#39;un composant du plan et que le composant est déployé à partir du plan, le terme _msm_move n&#39;est pas ajouté au nom du composant local (NPR-33207).
* Les paramètres annexés à la requête d’origine ne sont pas inclus dans l’URL de redirection (NPR-33174).
* Lorsque l&#39;option Coral.Select définit emptyOption=true ou contient un élément par défaut avec la valeur = &quot;&quot;, le fichier dropdownshowhide.js rencontre une erreur : Erreur de type non interceptée : component.getValue n&#39;est pas une fonction (NPR-33163).
* Lorsqu&#39;un composant comprend un autre composant en tant que ressource de données, l&#39;espace réservé du composant de conteneur parent est remplacé par l&#39;espace réservé des composants internes (NPR-33119).
* Lorsque vous basez un fragment de contenu sur un schéma et qu’il contient une zone de texte obligatoire ou un champ de chemin d’accès, l’enregistrement du fragment de contenu échoue (NPR-33007)
* Lorsque vous créez un composant personnalisé à l’aide du composant de fragment d’expérience prêt à l’emploi et que vous l’utilisez dans les pages AEM Sites, AEM n’affiche pas les références (utilisation) du composant personnalisé (NPR-32852).
* Lorsqu’une page AEM Sites fait partie d’un grand jeu de contenu comportant plusieurs copies en direct, la prévisualisation d’historique des versions de page ne se charge pas (NPR-32772).
* Lorsque vous promouvez un lancement, il ajoute le mixin &quot;cq:LiveRelationship&quot; à chaque composant ajouté au lancement. Elle a un impact sur tous les lancements, indépendamment du fait qu&#39;un lancement soit créé avec ou sans sélectionner l&#39;option — Hériter les données en direct de la page source — (NPR-32664).
* Lors des débuts de pagination, le sélecteur de fragments d’expérience ne charge pas tous les éléments (NPR-32605).
* Impossible de créer un lancement pour une page AEM Sites. La création du lancement génère une erreur (NPR-32544).
* Gérer la publication n’inclut pas les ressources référencées dans le processus de demande d’activation (NPR-32463).
* La vérification d&#39;intégrité du répartiteur affiche un message d&#39; `Invalid cookie header` avertissement dans les fichiers journaux (NPR-33630).
* L&#39;intégration de Salesforce est vulnérable au SSRF (NPR-32671).
* XSS reflété dans PreferencesServlet (NPR-33439).

### Ressources {#assets-6481}

* Le nombre d’actifs ne change pas en fonction du changement de sélection dans la Vue de Liste (NPR-33285).

* Le bouton Suivant n’est pas activé lors de la sélection du noeud parent (où un dossier enfant unique est visible), puis lors de la sélection du dossier enfant (NPR-33284).

* L’interface utilisateur tactile ne parvient pas à s’afficher (avec erreur) pour les utilisateurs qui n’ont pas accès en lecture à la racine du référentiel, lorsque le mode DMS7 ou hybride est activé (NPR-33175).

* Les caractères GB18030 se trouvant dans les dossiers et les noms de fichier deviennent vides dans les fichiers zip téléchargés (NPR-33150).

* Un dossier supplémentaire est créé lors du recadrage intelligent d’un fichier se trouvant dans un dossier parent dont le nom contient un caractère point `.` (NPR-32755).

* Le chargement différé n&#39;est pas déclenché et pas plus de 100 ressources s&#39;affichent lors de la sélection pour consulter les tâches de la boîte de réception des notifications (NPR-32749).

* La page de lien vers la collecte de partage est interrompue en raison d&#39;un changement dans coral-info (NPR-32510).

* Le traitement des ressources pendant le chargement en masse est bloqué (CQ-4293916).

* Vulnérabilité SSRF en Experience Manager (NPR-33437).

### Plate-forme {#platform-6481}

* Le [!DNL Sling] filtre n’est pas appelé si l’entrée de `sling:match` mappage est créée sous `/etc/maps` (NPR-33308).
* Tous les agents de vidage sont déclenchés lors de la désactivation d&#39;une page (NPR-32941).
* Lorsque vous utilisez l’ `ScriptProcessor` API pour réduire la taille d’une bibliothèque JavaScript, le fichier journal affiche un message d’erreur indiquant que le code JavaScript n’est pas conforme au mode strict. L’API ne fournit pas d’option permettant d’activer ou de désactiver le mode strict. (NPR-32746).
* Lorsqu&#39;une requête SQL s&#39;exécute plus longtemps, par exemple pendant 7 heures, AEM cesse de répondre (NPR-33043).

### Interface utilisateur {#ui-6481}

* Lorsque vous recherchez ou parcourez un chemin à l’aide d’une boîte de dialogue de sélection, la boîte de dialogue de sélection affiche tout le contenu du noeud JCR sélectionné au lieu d’afficher uniquement les images (NPR-32712).

### Projets de traduction {#tranlation-6481}

* Une `NullPointerException` erreur s&#39;affiche dans les journaux d&#39;exécution d&#39;une tâche de traduction (NPR-32220).

### Intégrations {#integrations-6481}

* Script intersite pour JSON (NPR-32745).

### Communities {#communities-6481}

* Les auteurs, après avoir créé un nouveau groupe, ne sont pas redirigés vers la section Groupe  communautaire le [!DNL Internet Explorer] 11 (NPR-33202).
* Une erreur se produit lors de l&#39;accès à la page [!UICONTROL Activité Stream] (NPR-33152).
* La modification d&#39;un [!DNL Communities] groupe et de l&#39;image miniature n&#39;actualise pas l&#39;image miniature du groupe (NPR-32603).
* Lors de la création d’une version de notifications et d’abonnements de contenu généré par l’utilisateur (UGC), un ID incorrect de la page source est stocké (CQ-4289703).
* Problème de script intersite (NPR-33212).

### Workflow {#workflow-6481}

* Certains composants ne s’affichent pas dans la boîte de dialogue qui s’affiche lorsqu’un utilisateur termine un processus incluant une étape [!UICONTROL de participant à la] boîte de dialogue (NPR-32989).

* Le chargement de l&#39;option [!UICONTROL Chronologie] dans le rail de gauche prend plus de temps que prévu (NPR-32850).

### Formulaires {#forms-6481}

>[!NOTE]
>
>aem Cumulative Fix Pack n&#39;inclut pas de correctifs pour AEM Forms. Les correctifs sont fournis à l’aide d’un module complémentaire Forms distinct.  En outre, un programme d’installation cumulatif est publié, qui comprend des correctifs pour AEM Forms on JEE. For more information, see [Install AEM Forms add-on package](#install-aem-forms-add-on-package) and [Install AEM Forms JEE installer](#install-aem-forms-jee-installer).

* Correspondence Management : Lorsqu’un utilisateur colle du contenu à partir d’un [!DNL Word] document, le fragment de document de texte ne conserve pas la mise en forme (NPR-33213).
* Forms adaptatif : Une nouvelle ligne d’une chaîne dans un dictionnaire de formulaires adaptatifs ajoute `&#xa;` des caractères au dictionnaire (NPR-33265).
* Forms adaptatif : L’utilisateur ne peut pas enregistrer de formulaire adaptatif contenant plusieurs pièces jointes (NPR-33214).
* Forms adaptatif : `AddInstance` et `RemoveInstance` les méthodes de la classe Instance Manager n’ajoutent pas de nombre dynamique d’instances pour les fragments de chargement différé sur [!DNL Internet Explorer 11] (NPR-33201).
* Forms adaptatif : Les analyses activées sur un formulaire adaptatif incorporé dans une [!DNL Sites] page n’enregistrent pas les données des événements Envoyer et Abandon (NPR-31359).
* Forms adaptatif : Lorsqu’un utilisateur colle le contenu d’un [!DNL Word] document à un formulaire adaptatif et l’envoie, le formulaire adaptatif envoyé comprend des caractères Unicode. En outre, la conversion PDF/A échoue en raison de caractères Unicode (NPR-33348).
* BackendIntegration : Les demandes de modèle de données de formulaire échouent lorsque le jeton d’actualisation expire en raison d’un état inactif incorrect (NPR-33168).
* Document Services : Le service Convert PDF ne parvient pas à convertir les documents PDF en PostScript en raison de l’absence de jars Gibson pour [!DNL WebLogic] [!DNL Linux] le serveur (NPR-33515, CQ-4292239).
* Document Services : Lorsqu’un utilisateur convertit un fichier texte au format PDF, les caractères japonais ne s’affichent pas correctement (NPR-33239).
* Stockage de XSS avec le GuideSOMProviderServlet (NPR-32701).


## Install 6.4.8.1 {#install}

### Conditions requises {#setup-requirements}

<!--

>[!NOTE]
>
>For successful installation of AEM 6.4.6.0 on the instance, it is strongly recommended to upgrade the version of com.adobe.granite.oak.s3connector to 1.8.4 for the customers who are on the older version of s3 connector.
>The process of upgrading the com.adobe.granite.oak.s3connector is available at [https://helpx.adobe.com/in/experience-manager/6-4/sites/deploying/using/data-store-config.html](https://helpx.adobe.com/in/experience-manager/6-4/sites/deploying/using/data-store-config.html).
>Download the latest version of com.adobe.granite.oak.s3connector from: [https://repo.adobe.com/nexus/content/groups/public/com/adobe/granite/com.adobe.granite.oak.s3connector/](https://repo.adobe.com/nexus/content/groups/public/com/adobe/granite/com.adobe.granite.oak.s3connector/)

-->

>[!CAUTION]
>
>Pour les clients dont les Feature Packs sont installés sur AEM 6.4. Les Feature Packs facultatifs fournis par Adobe dépendent de la version de publication et des Service Packs. Si vous disposez d’un pack de fonctionnalités, contactez l’équipe d’assistance AEM clientèle afin de vérifier la compatibilité de ces packs de fonctionnalités avec ce pack de correctifs cumulatif pour AEM 6.4.

* AEM 6.4.8.1 requires AEM 6.4.8.0. Please visit [upgrade documentation](../sites-deploying/upgrade.md) for detailed instructions.
* Lors d’un déploiement avec MongoDB et plusieurs instances, installez AEM 6.4.8.1 sur l’une des instances d’auteur à l’aide du gestionnaire de modules.
* Avant d’installer le pack de correctifs cumulatifs, veillez à disposer d’un instantané ou d’une nouvelle sauvegarde de votre instance AEM.
* Redémarrez l’instance avant l’installation. Cela est nécessaire uniquement lorsque l’instance reste en mode de mise à jour (ce qui est le cas lorsque l’instance vient d’être mise à jour depuis une version antérieure). Toutefois, cela est généralement recommandé si l’instance s’est exécutée pendant longtemps.

>[!NOTE]
>
>Adobe recommande de ne pas supprimer ni désinstaller le package AEM 6.4.8.1.

### Installation du Cumulative Fix Pack {#install-cumulative-fix-pack}

Suivez les étapes suivantes pour installer le pack de correctifs cumulés sur une instance 6.4.8.0 existante :

1. Cliquez sur le lien Distribution [de](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/cumulativefixpack/aem-6.4.8-cfp-1.0.zip) logiciels pour télécharger le package.

1. Open [Package Manager](http://localhost:4502/crx/packmgr/index.jsp) and click **[!UICONTROL Upload Package]** to upload the package.

1. Select the package name and click **[!UICONTROL Install]**.

>[!NOTE]
>
>**La boîte de dialogue sur l’interface utilisateur de Package Manager se ferme parfois de manière impromptue lors de l’installation de la version 6.4.8.1**
>
>Il est donc recommandé d’attendre que les journaux d’erreurs se stabilisent avant d’accéder à l’instance. L&#39;utilisateur doit attendre les journaux spécifiques liés à la désinstallation du lot de mise à jour avant de s&#39;assurer que l&#39;installation est réussie. Cela se produit généralement sur Safari, mais peut se produire par intermittence sur n’importe quel navigateur.

### Installation automatique {#auto-installation}

Il existe deux manières d’installer automatiquement AEM 6.4.8.1 dans une instance en cours d’exécution :

A. Placez le package dans le dossier ..*/crx-quickstart/install* pendant que le serveur est en cours d’exécution. Le package est automatiquement installé.

B. Use the [HTTP API from Package Manager](https://docs.adobe.com/content/docs/en/crx/2-3/how_to/package_manager.html) - make sure you use `cmd=install&recursive=true` - so the nested package are installed.

>[!NOTE]
>
>AEM 6.4.8.1 ne prend pas en charge l’installation de Bootstrap.

### Validation de l’installation {#validate-install}

1. La page Informations sur le produit (*/system/console/productinfo*) doit maintenant afficher la chaîne de version mise à jour « Adobe Experience Manager, Version 6.4.8.1. » sous Produits installés.
1. Tous les lots OSGI sont ACTIFS ou FRAGMENT dans la console OSGI (utiliser la console web : /system/console/bundles).
1. Le lot OSGI org.apache.jackrabbit.oak-core est sur la version 1.8.17 ou ultérieure (utilisez la console Web : /system/console/bundles).

To determine the certified platform for running with this release of AEM Sites and Assets, see [Technical Requirements](../sites-deploying/technical-requirements.md).

>[!NOTE]
>On successful installation of the package, an informational message appears indicating that the content package has installed successfully, such as **&quot;Content Package AEM-6.4-Service-Pack-7 installed successfully.&quot;**

### Mise à jour des visionneuses de médias dynamiques (5.10.1) {#update-dynamic-media-viewers}

aem 6.4.8.1 contient la nouvelle version des visionneuses de contenu Contenu multimédia dynamique (5.10.1) qui permet de vérifier les noms des duplicata sur la page Paramètres d’image prédéfinis. Il est conseillé aux utilisateurs de Contenu multimédia dynamique d’exécuter la commande suivante afin de mettre à jour les paramètres prédéfinis de la visionneuse prête à l’emploi.

`curl -u admin:admin http://localhost:4502/libs/settings/dam/dm/presets/viewer.pushviewerpresets`

qui copiera les nouveaux paramètres prédéfinis de la visionneuse à l’emplacement /conf.

### Installation du module complémentaire AEM Forms {#install-aem-forms-add-on-package}

>[!NOTE]
>
>Passez cette étape si vous n’utilisez pas AEM Forms. Les correctifs dans AEM Forms sont fournis dans un module complémentaire distinct.

1. Assurez-vous d’avoir installé l’AEM Cumulative Fix Pack.
1. Download the corresponding forms add-on package listed at [AEM Forms releases](https://helpx.adobe.com/fr/aem-forms/kb/aem-forms-releases.html) for your operating system.
1. Install the forms add-on package as described in [Installing AEM forms add-on packages](https://docs.adobe.com/content/help/en/experience-manager-64/forms/install-aem-forms/osgi-installation/installing-configuring-aem-forms-osgi.html#install-aem-forms-add-on-package).

### Installation du programme d’installation d’AEM Forms JEE {#install-aem-forms-jee-installer}

>[!NOTE]
>
>Passez cette étape si vous n’utilisez pas AEM Forms sous JEE. Les correctifs dans AEM Forms JEE sont fournis dans un programme d’installation distinct.

Pour plus d’informations sur l’installation du programme d’installation cumulatif pour AEM Forms JEE et la configuration post-déploiement, voir [AEM Forms JEE Patch Installer 0016](https://helpx.adobe.com/aem-forms/quick-fixes/6-4/jee-patch-0016.html).

### Uber Jar {#uber-jar}

The Uber Jar for AEM 6.4.8.1 is available in the [Adobe Public Maven repository](https://repo.adobe.com/nexus/content/groups/public/com/adobe/aem/uber-jar/6.4.8.1/).

To use Uber Jar in a Maven project, refer to the article, [How to use Uber jar](../sites-developing/ht-projects-maven.md) and include the following dependency in your project POM:

```shell
<dependency>
      <groupId>com.adobe.aem</groupId>
      <artifactId>uber-jar</artifactId>
      <version>6.4.8.1</version>
      <classifier>apis</classifier>
      <scope>provided</scope>
</dependency>
```

## Fonctionnalités supprimées / obsolètes {#removed-deprecated-features}

Cette section répertorie les fonctionnalités qui ont été supprimées ou désignées comme obsolètes dans AEM 6.4.

| Zone | Fonctionnalité | Remplacement | Version |
|---|---|---|---|
| Ressources | Gérer l’action de balise pour les sous-ensembles | Aucun remplacement. | AEM 6.4.2.0 |
| Intégration des Ressources et d’Adobe Creative Cloud | [aem au partage](https://docs.adobe.com/content/help/en/experience-manager-64/assets/administer/aem-cc-folder-sharing-best-practices.html) des dossiers des Creative Cloud a été introduit dans AEM 6.2 pour permettre aux utilisateurs créatifs d’accéder aux ressources à partir d’AEM. Adobe Asset Link, nouvelle fonctionnalité proposée dans l’application Creative Cloud, offre une expérience utilisateur améliorée et un accès plus puissant aux ressources d’AEM directement à partir de Photoshop, InDesign et Illustrator. Adobe n’apportera pas d’améliorations supplémentaires à la fonctionnalité de partage de dossiers. Bien que la fonction soit incluse dans AEM, les clients sont (il est fortement conseillé d’utiliser le remplacement). | Lien de ressources d’Adobe ou application de bureau. Pour plus d’informations, reportez-vous à l’article [Intégration d’AEM Creative Cloud](/help/assets/aem-cc-integration-best-practices.md). | AEM 6.4.4.0 |

## Problèmes connus {#known-issues}

* Lors de l’installation de AEM 6.4.8.1, la mise à jour de la [!DNL Chrome] version 83 entraîne un problème lors de la création de packages. Utilisez d’autres navigateurs disponibles, tels que [!DNL Internet Explorer] et [!DNL Firefox], ou d’autres options d’installation de packs standard AEM pour résoudre ce problème. Le problème est résolu après l’installation AEM 6.4.8.1.

* Impossible d&#39;envoyer un courrier électronique au serveur SMTP distant à l&#39;aide de l&#39;expéditeur de courrier par défaut AEM, car il permet uniquement la communication à l&#39;aide de TLS v1.2. Supprimez le lot `javax.mail:mail:1.5.0-b01` de `system/console` et actualisez les lots pour résoudre le problème.

Pour plus d’informations sur les problèmes connus du Service Pack AEM 6.4.8.0, voir [AEM 6.4.8.0 Notes](sp-release-notes.md)de mise à jour du Service Pack.

## Lots OSGi et packages de contenu inclus {#osgi-bundles-and-content-packages-included}

Les documents de texte suivants liste les lots OSGi et les packages de contenu inclus dans l&#39;AEM 6.4.8.1.

Liste des lots OSGi inclus dans AEM 6.4.8.1

[Obtenir le fichier](assets/6.4.8.1_osgi_bundles.txt)

Liste des packages de contenu inclus dans AEM 6.4.8.1

[Obtenir le fichier](assets/6.4.8.1_content_packages.txt)

## Ressources utiles {#helpful-resources}

* [Notes de mise à jour d’AEM 6.4](../release-notes/release-notes.md)
* [Page de produits AEM ](https://www.adobe.com/solutions/web-experience-management.html)
* [Documentation d’AEM 6.4](https://helpx.adobe.com/fr/support/experience-manager/6-4.html)
* Subscribe to [Adobe priority product updates](https://www.adobe.com/subscription/priority-product-update.html)

## Sites restreints {#restricted-sites-new}

Seuls les clients peuvent accéder à ces sites. Si vous devez y accéder en tant que client, contactez votre gestionnaire de compte Adobe.

* [Téléchargement du produit à l’adresse licensing.adobe.com](https://licensing.adobe.com/)
* [Contacter l’assistance client](https://docs.adobe.com/content/help/en/customer-one/using/home.html)
