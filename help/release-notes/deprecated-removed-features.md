---
title: Fonctionnalités obsolètes et supprimées
description: Notes de mise à jour dédiées aux fonctionnalités obsolètes et supprimées dans Adobe Experience Manager 6.4
exl-id: 2fe0dad7-fc78-4aac-afa3-79a278008453
source-git-commit: 0f4f8c2640629f751337e8611a2c8f32f21bcb6d
workflow-type: tm+mt
source-wordcount: '1308'
ht-degree: 52%

---

# Fonctionnalités obsolètes et supprimées {#deprecated-and-removed-features}

Adobe étudie constamment les fonctionnalités du produit de façon à les réinventer au fil du temps ou à remplacer les fonctions plus anciennes par des variantes plus modernes, pour améliorer la valeur client globale, le tout en faisant toujours attention à la compatibilité ascendante.

Pour communiquer la suppression/le remplacement imminent de fonctionnalités d’AEM, les règles suivantes s’appliquent :

1. L’annonce de la suppression arrive en premier. Bien qu’elles soient obsolètes, les fonctionnalités sont toujours disponibles, mais elles ne seront pas améliorées.
1. La suppression des fonctionnalités obsolètes se produit au plus tôt dans la version majeure suivante. La date précise de suppression sera annoncée.

Ce processus donne aux clients au moins un cycle de version pour adapter leur implémentation à une nouvelle version ou à un produit de remplacement pour une fonctionnalité obsolète, avant que la suppression ne soit effective.

## Fonctionnalités obsolètes {#deprecated-features}

Le tableau ci-dessous répertorie les fonctionnalités qui ont été marquées comme obsolètes dans AEM 6.4. En règle générale, les fonctionnalités qui doivent être supprimées dans une version ultérieure sont d’abord définies comme obsolètes, avec une alternative fournie.

Il est conseillé aux clients de réfléchir à leur utilisation de la fonctionnalité dans leur déploiement actuel et de prévoir la modification de leur mise en œuvre de façon à utiliser l’alternative proposée.

<!-- TBD: This MD table is a replacement of the HTML table below. However, it generates validation error hence commenting and replacing with inline text. Restore if required. -->

| Zone | Fonctionnalité | Remplacement |
|---|---|---|
| Interface utilisateur | Adobe ne prévoit pas d’apporter d’autres améliorations à l’interface utilisateur classique. AEM 6.4 inclut l’interface utilisateur classique, et les clients effectuant une mise à niveau à partir de versions antérieures peuvent continuer à l’utiliser en l’état. Notez que l’interface utilisateur classique reste complètement prise en charge alors qu’elle est en passe de devenir obsolète. <ul> <li>`/libs/cq/core/content/welcome.html` </li> <li> `/siteadmin` </li> <li> `/damadmin` </li> <li> `/mcmadmin` </li> <li> `/inbox` </li> <li> `/tagging` </li> <li> `/cf#` (Éditeur de page) </li><li> `/libs/launches/content/admin.html` </li> <li> `/libs/cq/workflow/content/console.html` </li> </ul> | Adobe recommande à ses clients d’utiliser la nouvelle interface utilisateur d’AEM. |
| Composants | Adobe ne prévoit pas d’apporter d’autres améliorations aux composants de base répertoriés ci-dessous. AEM 6.4 inclut les composants de base, et les clients effectuant une mise à niveau à partir de versions antérieures peuvent continuer à les utiliser en l’état. Notez que les composants de base restent entièrement pris en charge alors qu’ils sont obsolètes. <ul> <li> foundation/components/account/accountname </li> <li> foundation/components/account/actions </li> <li> foundation/components/account/passwordreset </li> <li> foundation/components/account/requestconfirmation </li> <li> foundation/components/adaptiveimage </li> <li> foundation/components/assetsharepage </li> <li> foundation/components/breadcrumb </li> <li> foundation/components/form/creditcard </li> <li> foundation/components/listchildren </li> <li> foundation/components/login </li> <li> foundation/components/logo </li> <li> foundation/components/mobilefooter </li> <li> foundation/components/mobileimage </li> <li> foundation/components/mobilelist </li> <li> foundation/components/mobilelogo </li> <li> foundation/components/mobilereference </li> <li> foundation/components/mobiletextimage </li> <li> foundation/components/mobiletopnav </li> <li> foundation/components/search </li> <li> foundation/components/sitemap </li> <li> foundation/components/table </li> <li> foundation/components/toolbar </li> <li> foundation/components/topnav </li> <li> foundation/components/userinfo </li> </ul> | Adobe recommande aux clients d’utiliser les composants de base Core Components pour les projets futurs. Les sites existants n’ont pas besoin d’être modifiés. |
| Composants | Adobe ne prévoit pas d’apporter d’autres améliorations aux composants de base répertoriés ci-dessous. AEM 6.4 inclut les composants de base, et les clients effectuant une mise à niveau à partir de versions antérieures peuvent continuer à les utiliser en l’état. Notez que les composants de base restent entièrement pris en charge alors qu’ils sont obsolètes. <ul><li>foundation/components/timing</li></ul> | Adobe ne prévoit pas de fournir de remplacement. |
| Director du portail | Portal Director est un ensemble de fonctionnalités qui permet l’hébergement de contenu AEM via Portlet sur des serveurs tiers. Adobe ne prévoit pas d’apporter d’autres améliorations à la fonctionnalité Director de portail à l’emplacement indiqué ci-dessous. La version 6.4 d’AEM est incluse dans le Director du portail, et les clients effectuant une mise à niveau à partir de versions antérieures peuvent continuer à l’utiliser en l’état. Notez que Portal Direct reste entièrement pris en charge alors qu’il est obsolète. <ul><li>/libs/portal/director</li></ul> | Adobe ne prévoit pas de fournir de remplacement. |
| Composant Portlet | Les composants de portlet sous /foundation/components/portlet permettent l’hébergement de portlets JSR dans AEM en tant que composants. Adobe ne prévoit pas d’apporter d’autres améliorations à la fonctionnalité Composant Portlet. AEM 6.4 inclut le composant Portlet, et les clients effectuant une mise à niveau à partir de versions antérieures peuvent continuer à l’utiliser en l’état. Notez que le composant Portlet reste entièrement pris en charge tout en étant obsolète. | Adobe ne prévoit pas de fournir de remplacement. |
| Forms | La prise en charge du service de passerelle de migration centrale d’Adobe n’est plus fournie, car le produit Adobe Central n’est plus pris en charge. | Aucun remplacement. |
| Forms | Utilisation obsolète de JSONObject dans Query et OperationOptions. Les API suivantes sont obsolètes : <ul><li>`setArguments(JSONObject arguments)`</li><li> `JSONObject getArguments()`</li><li>`OperationOptions(String operationId, JSONObject arguments)`</li><li>`JSONObject getArguments()`</li><li> `void setArguments(JSONObject arguments)`</li></ul> | Utilisez la variable `IValueMap` API |
| Forms | Service Central Migration Bridge obsolète. | Aucun remplacement n’est proposé. |
| Ressources | Le déchargement des ressources a été abandonné à partir d’AEM 6.4. |  |
| Développeurs | Bibliothèque cliente Lodash / Underscore. Adobe ne prévoit pas de gérer ni de mettre à jour la bibliothèque cliente Lodash/Underscore avec la distribution (Quickstart). | Adobe recommande aux clients qui ont toujours besoin de Lodash/Underscore pour leur code de l’ajouter à leur base de code de projet. |

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

Le tableau ci-dessous répertorie les fonctionnalités qui ont été supprimées d’AEM 6.4. Ces fonctionnalités étaient marquées comme obsolètes dans les versions antérieures.

| Zone | Fonctionnalité | Remplacement |
|---|---|---|
| Intégration à [!DNL Experience Cloud] | Vous pouvez synchroniser vos ressources avec [!DNL Experience Cloud] en utilisant un paramétrage à l’aide d’[!DNL Adobe I/O]. [!DNL Adobe Experience Cloud] était précédemment appelé [!DNL Adobe Marketing Cloud]. | Si vous avez des requêtes, contactez [Service clientèle d’Adobe](https://experienceleague.adobe.com/?support-solution=General&amp;lang=fr#support). |
| Activity Map dans Analytics | Version d’Activity Map incluse dans AEM. | En raison de modifications de sécurité dans l’API Adobe Analytics, il n’est plus possible d’utiliser la version d’Activity Map incluse dans AEM. Le [Module d’Activity Map fourni par Adobe Analytics](https://experienceleague.adobe.com/docs/analytics/analyze/activity-map/getting-started/get-started-users/activitymap-install.html?lang=fr) doit maintenant être utilisé. |
| Components-Forms | Captcha de formulaire (foundation/components/form/captcha) | Utilisez le composant ReCaptcha de Google à la place. |
| Composants | Diaporama (foundation/components/slideshow) | Aucun remplacement. |
| Composants | Flash (foundation/components/flash) | Aucun remplacement. |
| Composants | Retrait de la prise en charge de la lecture des fichiers SWF dans le composant vidéo (foundation/components/video) | Utilisez des formats vidéo qui ne sont pas basés sur Flash. |
| Composants | Tableau des produits (commerce/components/product_table) | Aucun remplacement. |
| Gestion des tâches | Gestion des tâches de l’interface utilisateur classique (/libs/cq/taskmanagement/content/taskmanager.html) | Obsolète depuis la version 6.0. Utilisez la nouvelle gestion des tâches qui est combinée avec l’interface utilisateur de workflow. |
| Workflow | L’interface utilisateur de notification utilisée entre les versions 5.6 et 6.2 (/libs/cq/workflow/content/notifications.html) | Boîte de réception de workflow /aem/inbox |
| Forms | L’exportation des fichiers PDF au format PDF/E-1 avec PDF Generator a été supprimée. | PDF Generator continue à prendre en charge l’exportation de PDF vers les formats PDF/A-1a/b, PDF/A-2a/b et PDF/A-3a/b. |
| Forms | La prise en charge des images dans des fragments de documents a été supprimée. | Les communications interactives permettent d’utiliser des images directement dans les canaux web et d’impression. |
| Forms | Mise à niveau dynamique | La prise en charge de l’upgrade prêt à l’emploi n’est pas disponible |
| Forms | Sidegrade pour les migrations TarMK vers DocumentMK | Vous pouvez exporter les données de l’ancien système, puis les importer dans un nouveau système. Pour obtenir des instructions détaillées, voir la documentation sur la mise à niveau d’AEM Forms on JEE |
| Forms | Programme d’installation d’AEM Forms on JEE 32 bits non disponible. | Adobe a arrêté de livrer le programme d’installation d’AEM Forms on JEE 32 bits. Vous pouvez continuer à utiliser le programme d’installation 64 bits pour installer AEM Forms on JEE. |
| Forms | Suppression de la prise en charge de l’utilisation des images DAM dans le composant de fragment de document. | Vous pouvez utiliser le composant Image et graphique dans le canal d’impression de la communication interactive. Si vous utilisez le composant de fragment de document adaptatif dans les formulaires adaptatifs, il cesse de fonctionner après la mise à niveau vers AEM Forms 6.4. |
| Forms | Suppression de la fonction Documents adaptatifs | Vous pouvez utiliser la fonction de communications interactives pour créer des communications imprimées et Web. Si vous utilisez des documents adaptatifs, installez-les pour continuer à utiliser les documents adaptatifs existants. |
| Forms | Suppression de la page d’entrée spécifique à AEM Forms on JEE. | La page d’entrée d’AEM Forms on JEE est remplacée par AEM page d’entrée (/aem/start.html) |
| Forms | Suppression de la prise en charge du Captcha par défaut | Utilisez le service reCAPTCHA de Google. |
| Forms | Suppression de la prise en charge des champs Flash dans AEM Designer. AEM Designer n’autorise pas la modification des champs Flash utilisés dans un formulaire. | Vous pouvez utiliser AEM Designer disponible pour une version précédente pour modifier de tels formulaires. |
| Communities | La prise en charge de la vérification Captcha a été supprimée. | Utilisez l’intégration de captcha personnalisée (par exemple reCAPTCHA par Google) pour la vérification. |

## Annonce préalable à la prochaine version {#pre-announcement-for-next-release}

Le tableau ci-dessous contient une liste des modifications à apporter à une version ultérieure, qui ne sont pas obsolètes, mais qui peuvent avoir un impact sur les clients. Elles sont fournies à des fins de planification.

| Zone | Fonctionnalité | Annonce |
|---|---|---|
| Prise en charge des navigateurs | Microsoft Internet Explorer  | AEM 6.4 est la dernière version prenant en charge Microsoft Internet Explorer 11. |
| Foundation | Structure de l’IU | Adobe abandonne les composants de l’interface utilisateur Coral 2 en 2019. AEM 6.4 est entièrement basé sur l’interface utilisateur Coral 3 (introduite avec AEM 6.2). Adobe recommande à ses clients et partenaires qui ont créé des interfaces utilisateur personnalisées avec Coral 2 de les restructurer en Coral 3. Adobe propose un outil pour convertir les boîtes de dialogue Coral 2 en Coral 3 - [En savoir plus.](/help/sites-developing/modernization-tools.md) |
