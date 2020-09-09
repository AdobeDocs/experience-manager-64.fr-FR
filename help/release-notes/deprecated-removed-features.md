---
title: Fonctionnalités obsolètes et supprimées
description: Notes de mise à jour dédiées aux fonctionnalités obsolètes et supprimées dans Adobe Experience Manager 6.4.
translation-type: tm+mt
source-git-commit: 8e82c691affe3b2c4108beec394cc0ba2d607b61
workflow-type: tm+mt
source-wordcount: '1281'
ht-degree: 45%

---


# Fonctionnalités obsolètes et supprimées {#deprecated-and-removed-features}

Adobe étudie constamment les fonctionnalités du produit de façon à les réinventer au fil du temps ou à remplacer les fonctions plus anciennes par des variantes plus modernes, pour améliorer la valeur client globale, le tout en faisant toujours attention à la compatibilité ascendante.

Pour communiquer la suppression/le remplacement imminent de fonctionnalités d’AEM, les règles suivantes s’appliquent :

1. L’annonce de la suppression arrive en premier. Bien qu&#39;elles soient abandonnées, les capacités sont toujours disponibles, mais elles ne seront pas encore améliorées.
1. La suppression des fonctionnalités obsolètes se produit au plus tôt dans la version majeure suivante. La date de suppression sera annoncée.

Ce processus donne aux clients au moins un cycle de version afin d’adapter leur implémentation à une nouvelle version ou produit de remplacement d’une fonctionnalité obsolète, avant que la suppression ne soit effective.

## Fonctionnalités obsolètes {#deprecated-features}

Le tableau ci-dessous liste les fonctionnalités et fonctionnalités qui ont été marquées comme obsolètes avec AEM 6.4. En règle générale, les fonctionnalités qui doivent être supprimées dans une prochaine version sont définies comme obsolètes en premier, avec une alternative fournie.

Il est conseillé aux clients de réfléchir à leur utilisation de la fonctionnalité dans leur déploiement actuel et de prévoir la modification de leur mise en œuvre de façon à utiliser l’alternative proposée.

<!-- TBD: This MD table is a replacement of the HTML table below. However, it generates validation error hence commenting and replacing with inline text. Restore if required. -->

| Zone | Fonctionnalité | Remplacement |
|---|---|---|
| Interface utilisateur | Adobe ne prévoit pas d’apporter d’autres améliorations à l’interface utilisateur classique. AEM 6.4 inclut l’interface utilisateur classique, et les clients effectuant une mise à niveau à partir de versions antérieures peuvent continuer à l’utiliser en l’état. Notez que l’interface utilisateur classique reste complètement prise en charge alors qu’elle est en passe de devenir obsolète. <ul> <li>`/libs/cq/core/content/welcome.html` </li> <li> `/siteadmin` </li> <li> `/damadmin` </li> <li> `/mcmadmin` </li> <li> `/inbox` </li> <li> `/tagging` </li> <li> `/cf#` (Éditeur de page) </li><li> `/libs/launches/content/admin.html` </li> <li> `/libs/cq/workflow/content/console.html` </li> </ul> | Adobe recommande à ses clients d’utiliser la nouvelle interface utilisateur d’AEM. |
| Composants | Adobe ne prévoit pas d’apporter d’autres améliorations aux composants de base répertoriés ci-dessous. aem 6.4 inclut les composants Foundation, et les clients qui effectuent la mise à niveau à partir de versions antérieures peuvent continuer à les utiliser en l’état. Notez que les composants de base restent entièrement pris en charge tout en étant obsolètes. <ul> <li> foundation/components/account/accountname </li> <li> foundation/components/account/actions </li> <li> foundation/components/account/passwordreset </li> <li> foundation/components/account/requestconfirmation </li> <li> foundation/components/adaptiveimage </li> <li> foundation/components/assetsharepage </li> <li> foundation/components/breadcrumb </li> <li> foundation/components/form/creditcard </li> <li> foundation/components/listchildren </li> <li> foundation/components/login </li> <li> foundation/components/logo </li> <li> foundation/components/mobilefooter </li> <li> foundation/components/mobileimage </li> <li> foundation/components/mobilelist </li> <li> foundation/components/mobilelogo </li> <li> foundation/components/mobilereference </li> <li> foundation/components/mobiletextimage </li> <li> foundation/components/mobiletopnav </li> <li> foundation/components/search </li> <li> foundation/components/sitemap </li> <li> foundation/components/table </li> <li> foundation/components/toolbar </li> <li> foundation/components/topnav </li> <li> foundation/components/userinfo </li> </ul> | Adobe recommande aux clients d’utiliser les composants de base Core Components pour les projets futurs. Les sites existants n’ont pas besoin d’être modifiés. |
| Composants | Adobe ne prévoit pas d’apporter d’autres améliorations aux composants de base répertoriés ci-dessous. aem 6.4 inclut les composants Foundation, et les clients qui effectuent la mise à niveau à partir de versions antérieures peuvent continuer à les utiliser en l’état. Notez que les composants de base restent entièrement pris en charge tout en étant obsolètes. <ul><li>foundation/components/timing</li></ul> | L&#39;Adobe ne prévoit pas de fournir de remplacement. |
| Director Portal | Portal Director est un ensemble de fonctionnalités qui permet l’hébergement de contenu AEM via Portlet sur des serveurs tiers. adobe ne prévoit pas d’apporter d’autres améliorations à la fonctionnalité Director de Portal à l’emplacement indiqué ci-dessous. aem version 6.4 inclut Portal Director, et les clients qui effectuent une mise à niveau à partir de versions antérieures peuvent continuer à l’utiliser en l’état. Notez que Portal Direct reste entièrement pris en charge alors qu’il est obsolète. <ul><li>/libs/portal/Director</li></ul> | L&#39;Adobe ne prévoit pas de fournir de remplacement. |
| Composant de portlet | Les composants de portlet sous /foundation/components/portlet permettent l&#39;hébergement de portlets JSR en AEM en tant que composants. adobe n&#39;envisage pas d&#39;apporter d&#39;autres améliorations à la fonctionnalité Composant de portlet. aem 6.4 inclut le composant Portlet et les clients qui effectuent une mise à niveau à partir de versions antérieures peuvent continuer à l&#39;utiliser en l&#39;état. Notez que le composant Portlet reste entièrement pris en charge alors qu’il est obsolète. | L&#39;Adobe ne prévoit pas de fournir de remplacement. |
| Formulaires | La prise en charge du service de passerelle de migration centrale d’Adobe n’est plus fournie, car le produit Adobe Central n’est plus pris en charge. | Aucun remplacement. |
| Formulaires | Utilisation obsolète de JSONObject dans Requête et OperationOptions. Les API suivantes sont obsolètes : <ul><li>`setArguments(JSONObject arguments)`</li><li> `JSONObject getArguments()`</li><li>`OperationOptions(String operationId, JSONObject arguments)`</li><li>`JSONObject getArguments()`</li><li> `void setArguments(JSONObject arguments)`</li></ul> | Utilisation de l’ `IValueMap` API |
| Formulaires | Service Central Migration Bridge obsolète. | Aucun remplacement n&#39;est proposé. |
| Ressources | Le déchargement des ressources a été abandonné à partir de AEM 6.4. |  |
| Développeurs | Bibliothèque cliente de lodash/trait de soulignement. L&#39;Adobe ne prévoit pas de continuer à gérer et à mettre à jour la bibliothèque cliente Lodash/underscore fournie dans le cadre de la distribution (Quickstart). | adobe recommande aux clients qui ont encore besoin de Lodash/trait de soulignement pour leur code de l&#39;ajouter à leur base de code de projet. |

<!-- Original HTML table that came from helpx during migration.

<table> 
 <tbody>
  <tr>
   <td>Area</td> 
   <td>Feature</td> 
   <td>Replacement</td> 
  </tr>
  <tr>
   <td>UI</td> 
   <td><p>Adobe does not plan to make further enhancements to the Classic UI. AEM 6.4 has the Classic UI included, and customers upgrading from earlier releases can keep using it as is. Note that Classic UI remains fully supported while being deprecated. </p> 
    <ul> 
     <li>/libs/cq/core/content/welcome.html</li> 
     <li>/siteadmin</li> 
     <li>/damadmin</li> 
     <li>/mcmadmin</li> 
     <li>/inbox</li> 
     <li>/tagging</li> 
     <li>/cf# (Page Editor)</li> 
     <li>/libs/launches/content/admin.html</li> 
     <li>/libs/cq/workflow/content/console.html</li> 
    </ul> </td> 
   <td><p>Customers are advised to switch to use the new AEM UI.</p> <p> </p> </td> 
  </tr>
  <tr>
   <td>Components</td> 
   <td><p>Adobe does not plan to make further enhancements to the Foundation Components listed below. AEM 6.4 has the Foundation Components included, and customers upgrading from earlier releases can keep using them as is. Note that Foundation Components remain fully supported while being deprecated. </p> 
    <ul> 
     <li>foundation/components/account/accountname</li> 
     <li>foundation/components/account/actions</li> 
     <li>foundation/components/account/passwordreset</li> 
     <li>foundation/components/account/requestconfirmation</li> 
     <li>foundation/components/adaptiveimage</li> 
     <li>foundation/components/assetsharepage</li> 
     <li>foundation/components/breadcrumb</li> 
     <li>foundation/components/form/creditcard</li> 
     <li>foundation/components/listchildren</li> 
     <li>foundation/components/login</li> 
     <li>foundation/components/logo</li> 
     <li>foundation/components/mobilefooter</li> 
     <li>foundation/components/mobileimage</li> 
     <li>foundation/components/mobilelist</li> 
     <li>foundation/components/mobilelogo</li> 
     <li>foundation/components/mobilereference</li> 
     <li>foundation/components/mobiletextimage</li> 
     <li>foundation/components/mobiletopnav</li> 
     <li>foundation/components/search</li> 
     <li>foundation/components/sitemap</li> 
     <li>foundation/components/table</li> 
     <li>foundation/components/toolbar</li> 
     <li>foundation/components/topnav</li> 
     <li>foundation/components/userinfo</li> 
    </ul> </td> 
   <td>Customers are advised to use the Core Components for future projects. Existing sites do not need to be changed.</td> 
  </tr>
  <tr>
   <td>Components</td> 
   <td><p>Adobe does not plan to make further enhancements to the Foundation Components listed below. AEM 6.4 has the Foundation Components included, and customers upgrading from earlier releases can keep using them as is. Note that Foundation Components remain fully supported while being deprecated.</p> 
    <ul> 
     <li>foundation/components/timing</li> 
    </ul> </td> 
   <td>At the point of writing, it's not planned to provide a replacement.</td> 
  </tr>
  <tr>
   <td>Portal Director</td> 
   <td><p>The Portal Director is a set of features, that enables the hosting of AEM content via Portlet in 3rd party servers.</p> <p>Adobe does not plan to make further enhancements to the Portal Director feature under the location listed below. AEM 6.4 has the Portal Director included, and customers upgrading from earlier releases can keep using it as is. Note that Portal Direct remains fully supported while being deprecated.</p> 
    <ul> 
     <li>/libs/portal/director</li> 
    </ul> </td> 
   <td>At the point of writing, it's not planned to provide a replacement.</td> 
  </tr>
  <tr>
   <td>Portlet Component</td> 
   <td><p>Portlet Components under /foundation/components/portlet enables the hosting of JSR Portlets in AEM as components.</p> <p>Adobe does not plan to make further enhancements to the Portlet Component feature. AEM 6.4 has the Portlet Component included, and customers upgrading from earlier releases can keep using it as is. Note that Portlet Component remains fully supported while being deprecated.</p> </td> 
   <td>At the point of writing, it's not planned to provide a replacement.</td> 
  </tr>
  <tr>
   <td>Forms</td> 
   <td><p>Support for Adobe Central Migration Bridge service has been deprecated as Adobe Central product is no longer supported.</p> </td> 
   <td>No replacement </td> 
  </tr>
    <tr>
   <td>Forms</td> 
   <td><p>Deprecated use of JSONObject in Query and OperationOptions. The following APIs are deprecated:
   <ul><li>setArguments(JSONObject arguments)</li><li>JSONObject getArguments()</li><li>OperationOptions(String operationId, JSONObject arguments</li><li>JSONObject getArguments()</li><li>void setArguments(JSONObject arguments)</li></ul>
   </p> </td> 
   <td>Use the IValueMap API </td> 
  </tr>
  <tr>
   <td>Forms</td> 
   <td><p>Deprecated Central Migration Bridge service</p> </td> 
   <td> No replacement </td> 
  </tr>
  <tr>
   <td>Assets</td> 
   <td><p>Assets Offloading has been deprecated starting with AEM 6.4</p> </td> 
   <td> </td> 
  </tr>
 </tbody>
</table>
-->

## Fonctionnalités supprimées {#removed-features}

Le tableau ci-dessous liste les fonctionnalités et les fonctionnalités qui ont été supprimées de AEM 6.4. Les versions précédentes avaient ces fonctionnalités désignées comme obsolètes.

| Zone | Fonctionnalité | Remplacement |
|---|---|---|
| Activity Map dans Analytics | Version d’Activity Map incluse dans AEM. | En raison de modifications de sécurité dans l’API Adobe Analytics, il n’est plus possible d’utiliser la version d’Activity Map incluse dans AEM. The [ActivityMap plug-in provided by Adobe Analytics](https://docs.adobe.com/content/help/fr-FR/analytics/analyze/activity-map/getting-started/get-started-users/activitymap-install.html) should now be used. |
| Composants-Forms | Captcha de formulaire (foundation/components/form/captcha) | Utilisez le composant ReCaptcha de Google à la place. |
| Composants | Diaporama (foundation/components/slideshow) | Aucun remplacement |
| Composants | Flash (foundation/components/flash) | Aucun remplacement |
| Composants | Retrait de la prise en charge de la lecture des fichiers SWF dans le composant vidéo (foundation/components/video) | Utilisez des formats vidéo qui ne sont pas basés sur Flash. |
| Composants | Tableau des produits (commerce/components/product_table) | Aucun remplacement |
| Gestion des tâches | Gestion des tâches de l’interface utilisateur classique (/libs/cq/taskmanagement/content/taskmanager.html) | Obsolète depuis la version 6.0. Utilisez la nouvelle gestion des tâches qui est combinée avec l’interface utilisateur de workflow. |
| Workflow | L’interface utilisateur de notification utilisée entre les versions 5.6 et 6.2 (/libs/cq/workflow/content/notifications.html) | Boîte de réception de workflow /aem/inbox |
| Formulaires | L’exportation des fichiers PDF au format PDF/E-1 avec PDF Generator a été supprimée. | PDF Generator continue à prendre en charge l’exportation des formats PDF aux formats PDF/A-1a/b, PDF/A-2a/b et PDF/A-3a/b. |
| Formulaires | La prise en charge des images dans des fragments de documents a été supprimée. | Les communications interactives permettent d’utiliser des images directement dans les canaux web et d’impression. |
| Formulaires | Mise à niveau dynamique | La prise en charge de la mise à niveau hors site n&#39;est pas disponible |
| Formulaires | Sidegrade pour les migrations TarMK vers DocumentMK | Vous pouvez exporter les données de l’ancien système, puis les importer dans un nouveau système de configuration. Pour obtenir des instructions détaillées, voir Documentation sur la mise à niveau d’AEM Forms on JEE. |
| Formulaires | Programme d’installation AEM Forms on JEE 32 bits non disponible. | adobe a arrêté d’envoyer le programme d’installation 32 bits de AEM Forms on JEE. Vous pouvez continuer à utiliser le programme d’installation 64 bits pour installer AEM Forms on JEE. |
| Formulaires | Suppression de la prise en charge de l’utilisation d’images DAM dans le composant de fragment de Document. | Vous pouvez utiliser le composant Image et Graphique dans le canal d’impression de la communication interactive. Si vous utilisez un composant de fragment de document de document adaptatif dans les formulaires adaptatifs, il ne fonctionne plus après la mise à niveau vers AEM 6.4 Forms. |
| Formulaires | Suppression de la fonction Documents adaptatifs | Vous pouvez utiliser la fonction de communications interactives pour créer des communications imprimées et Web. Si vous utilisez des Documents adaptatifs, installez le package de compatibilité pour continuer à utiliser les documents adaptatifs existants. |
| Formulaires | Suppression d’un landing page spécifique à AEM Forms on JEE. | Le landing page AEM Forms on JEE est remplacé par le landing page AEM (/aem/start.html). |
| Formulaires | Suppression de la prise en charge de Captcha par défaut | Utilisez le service reCAPTCHA de Google. |
| Formulaires | Suppression de la prise en charge des champs Flash dans AEM Designer. aem Designer ne permet pas de modifier les champs Flash utilisés dans un formulaire. | Vous pouvez utiliser AEM Designer publié pour une version précédente pour modifier de tels formulaires. |
| Communities | La prise en charge de la vérification de Captcha a été supprimée. | Utilisez l’intégration captcha personnalisée (telle que reCAPTCHA par Google) pour la vérification. |

## Annonce préalable à la prochaine version {#pre-announcement-for-next-release}

Le tableau ci-dessous présente une liste de modifications pour les versions ultérieures, qui ne sont pas obsolètes, mais peuvent avoir un impact sur les clients. Elles sont fournies à des fins de planification.

| Zone | Fonctionnalité | Annonce |
|---|---|---|
| Prise en charge des navigateurs | Microsoft Internet Explorer  | AEM 6.4 est la dernière version prenant en charge Microsoft Internet Explorer 11. |
| Foundation | Structure de l’IU | En 2019, l’Adobe a abandonné les composants de l’interface utilisateur 2 de Coral. aem 6.4 est entièrement basé sur l&#39;interface utilisateur 3 de Coral (introduite avec AEM 6.2). adobe recommande à ses clients et partenaires qui ont créé des interfaces utilisateur personnalisées avec Coral 2 de les reconfigurer en Coral 3. Adobe offers a tool to convert Coral 2 dialogs to Coral 3 - [Read more](/help/sites-developing/dialog-conversion.md). |
