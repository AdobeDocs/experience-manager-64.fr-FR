---
title: Fonctionnalités obsolètes et supprimées
seo-title: Fonctionnalités obsolètes et supprimées
description: Notes de mise à jour dédiées aux fonctionnalités obsolètes et supprimées dans Adobe Experience Manager 6.4.
seo-description: Notes de mise à jour dédiées aux fonctionnalités obsolètes et supprimées dans Adobe Experience Manager 6.4.
uuid: 2619039b-72b4-4c6c-a813-90eed622b423
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4
topic-tags: release-notes
content-type: reference
discoiquuid: 15819d42-4897-40fa-a013-e019d1580fa2
translation-type: tm+mt
source-git-commit: 3316dbc8ef268be2b305d22da9003ae40414b4e1

---


# Fonctionnalités obsolètes et supprimées {#deprecated-and-removed-features}

Adobe étudie constamment les fonctionnalités du produit de façon à les réinventer au fil du temps ou à remplacer les fonctions plus anciennes par des variantes plus modernes, pour améliorer la valeur client globale, le tout en faisant toujours attention à la compatibilité ascendante.

Pour communiquer la suppression/le remplacement imminent de fonctionnalités d’AEM, les règles suivantes s’appliquent :

1. L’annonce de la suppression arrive en premier. Lorsqu’elles sont obsolètes, les fonctionnalités sont toujours disponibles, mais elles ne seront plus développées.
1. La suppression des fonctionnalités obsolètes se produit au plus tôt dans la version majeure suivante. La date de suppression sera annoncée.

Ce processus donne aux clients au moins un cycle de version afin d’adapter leur implémentation à une nouvelle version ou produit de remplacement d’une fonctionnalité obsolète, avant que la suppression ne soit effective.

## Fonctionnalités obsolètes {#deprecated-features}

Cette section répertorie les fonctionnalités qui ont été signalées comme obsolètes dans AEM 6.4. En général, les fonctionnalités qui seront supprimées dans une prochaine version sont d’abord annoncées comme obsolètes, et une alternative est fournie.

Il est conseillé aux clients de réfléchir à leur utilisation de la fonctionnalité dans leur déploiement actuel et de prévoir la modification de leur mise en œuvre de façon à utiliser l’alternative proposée.

<table> 
 <tbody>
  <tr>
   <td>Zone</td> 
   <td>Fonctionnalité</td> 
   <td>Remplacement</td> 
  </tr>
  <tr>
   <td>Interface utilisateur</td> 
   <td><p>Adobe ne prévoit pas d’apporter d’autres améliorations à l’interface utilisateur classique. AEM 6.4 inclut l’interface utilisateur classique, et les clients effectuant une mise à niveau à partir de versions antérieures peuvent continuer à l’utiliser en l’état. Notez que l’interface utilisateur classique reste complètement prise en charge alors qu’elle est en passe de devenir obsolète. </p> 
    <ul> 
     <li>/libs/cq/core/content/welcome.html</li> 
     <li>/siteadmin</li> 
     <li>/damadmin</li> 
     <li>/mcmadmin</li> 
     <li>/inbox</li> 
     <li>/tagging</li> 
     <li>/cf# (éditeur de pages)</li> 
     <li>/libs/launches/content/admin.html</li> 
     <li>/libs/cq/workflow/content/console.html</li> 
    </ul> </td> 
   <td><p>Adobe recommande à ses clients d’utiliser la nouvelle interface utilisateur d’AEM.</p> <p> </p> </td> 
  </tr>
  <tr>
   <td>Composants</td> 
   <td><p>Adobe ne prévoit pas d’apporter d’autres améliorations aux composants de base répertoriés ci-dessous. AEM 6.4 inclut les composants Foundation, et les clients qui effectuent une mise à niveau depuis des versions antérieures peuvent continuer à les utiliser en l’état. Notez que les composants de base restent entièrement pris en charge lorsqu’ils sont obsolètes. </p> 
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
   <td>Adobe recommande aux clients d’utiliser les composants de base Core Components pour les projets futurs. Les sites existants n’ont pas besoin d’être modifiés.</td> 
  </tr>
  <tr>
   <td>Composants</td> 
   <td><p>Adobe ne prévoit pas d’apporter d’autres améliorations aux composants de base répertoriés ci-dessous. AEM 6.4 inclut les composants Foundation, et les clients qui effectuent une mise à niveau depuis des versions antérieures peuvent continuer à les utiliser en l’état. Notez que les composants de base restent entièrement pris en charge lorsqu’ils sont obsolètes.</p> 
    <ul> 
     <li>foundation/components/timing</li> 
    </ul> </td> 
   <td>Au moment où nous écrivons, il n'est pas prévu de fournir un remplaçant.</td> 
  </tr>
  <tr>
   <td>Directeur du portail</td> 
   <td><p>Portal Director est un ensemble de fonctionnalités qui permet l’hébergement de contenu AEM via Portlet sur des serveurs tiers.</p> <p>Adobe n’envisage pas d’apporter d’autres améliorations à la fonction Portal Director à l’emplacement indiqué ci-dessous. AEM 6.4 inclut Portal Director et les clients qui effectuent une mise à niveau depuis des versions antérieures peuvent continuer à l’utiliser en l’état. Notez que Portal Direct reste entièrement pris en charge lors de la désapprobation.</p> 
    <ul> 
     <li>/libs/portal/Director</li> 
    </ul> </td> 
   <td>Au moment où nous écrivons, il n'est pas prévu de fournir un remplaçant.</td> 
  </tr>
  <tr>
   <td>Composant de portlet</td> 
   <td><p>Les composants de portlet sous /foundation/components/portlet permettent l’hébergement de portlets JSR dans AEM en tant que composants.</p> <p>Adobe n’envisage pas d’apporter d’autres améliorations à la fonctionnalité Composant de portlet. AEM 6.4 comprend le composant Portlet et les clients qui effectuent une mise à niveau depuis des versions antérieures peuvent continuer à l’utiliser en l’état. Notez que le composant Portlet reste entièrement pris en charge lors de sa désapprobation.</p> </td> 
   <td>Au moment où nous écrivons, il n'est pas prévu de fournir un remplaçant.</td> 
  </tr>
  <tr>
   <td>Forms</td> 
   <td><p>La prise en charge du service de passerelle de migration centrale d’Adobe n’est plus fournie, car le produit Adobe Central n’est plus pris en charge.</p> </td> 
   <td>Aucun remplacement. </td> 
  </tr>
    <tr>
   <td>Forms</td> 
   <td><p>Utilisation obsolète de JSONObject dans les  et OperationOptions. Les API suivantes sont obsolètes :
   <ul><li>setArguments(arguments JSONObject)</li><li>JSONObject getArguments()</li><li>OperationOptions(String operationId, arguments JSONObject</li><li>JSONObject getArguments()</li><li>void setArguments(JSONObject arguments)</li></ul>
   </p> </td> 
   <td>Utilisation de l’API IValueMap </td> 
  </tr>
  <tr>
   <td>Ressources</td> 
   <td><p>Le déchargement des ressources a été abandonné à partir d’AEM 6.4.</p> </td> 
   <td> </td> 
  </tr>
 </tbody>
</table>

## Fonctionnalités supprimées {#removed-features}

Cette section les fonctionnalités et fonctionnalités qui ont été supprimées d’AEM 6.4. Les versions antérieures indiquaient que ces fonctionnalités étaient obsolètes.

<table> 
 <tbody>
  <tr>
   <td><strong>Zone</strong></td> 
   <td><strong>Fonctionnalité</strong></td> 
   <td><strong>Remplacement</strong></td> 
  </tr>
  <tr>
   <td>Carte des  Analytics </td> 
   <td>Version du  de mappage de  incluse dans AEM.</td> 
   <td>En raison de modifications de sécurité dans l’API Adobe Analytics, il n’est plus possible d’utiliser la version d’Activity Map incluse dans AEM.<br><br>Le module externe <a href="https://docs.adobe.com/content/help/en/analytics/analyze/activity-map/getting-started/get-started-users/activitymap-install.html">ActivityMap fourni par Adobe Analytics</a> doit maintenant être utilisé.</td> 
  </tr>
  <tr>
   <td>Composants</td> 
   <td>Captcha de formulaire <br />(foundation/components/form/captcha)</td> 
   <td>Utilisez le composant ReCaptcha de Google à la place.</td> 
  </tr>
  <tr>
   <td>Composants</td> 
   <td>Diaporama<br /> (foundation/components/slideshow)</td> 
   <td>Aucun remplacement</td> 
  </tr>
  <tr>
   <td>Composants</td> 
   <td>Flash<br /> (foundation/components/flash)</td> 
   <td>Aucun remplacement</td> 
  </tr>
  <tr>
   <td>Composants</td> 
   <td>Retrait de la prise en charge de la lecture des fichiers SWF dans le composant vidéo <br />(foundation/components/video)</td> 
   <td>Utilisez des formats vidéo qui ne sont pas basés sur Flash.</td> 
  </tr>
  <tr>
   <td>Composants</td> 
   <td>Tableau des produits <br />(commerce/components/product_table)</td> 
   <td>Aucun remplacement</td> 
  </tr>
  <tr>
   <td>Gestion des tâches</td> 
   <td>Gestion des tâches de l’interface utilisateur classique <br />(/libs/cq/taskmanagement/content/taskmanager.html)</td> 
   <td>Obsolète depuis la version 6.0. Utilisez la nouvelle gestion des tâches qui est combinée avec l’interface utilisateur de workflow.</td> 
  </tr>
  <tr>
   <td>Workflow</td> 
   <td>L’interface utilisateur de notification utilisée entre les versions 5.6 et 6.2 <br />(/libs/cq/workflow/content/notifications.html)</td> 
   <td>Boîte de réception de workflow /aem/inbox</td> 
  </tr>
  <tr>
   <td>Forms</td> 
   <td>L’exportation des fichiers PDF au format PDF/E-1 avec PDF Generator a été supprimée.</td> 
   <td>PDF Generator prend toujours en charge l’exportation de fichiers PDF aux formats PDF/A-1a/b, PDF/A-2a/b et PDF/A-3a/b.</td> 
  </tr>
  <tr>
   <td>Forms</td> 
   <td>La prise en charge du service AEM Captcha par défaut dans les formulaires adaptatifs a été supprimée. </td> 
   <td>Utilisez ReCaptcha de Google à la place.</td> 
  </tr>
  <tr>
   <td>Forms</td> 
   <td>La prise en charge des images dans des fragments de documents a été supprimée. </td> 
   <td>Les communications interactives permettent d’utiliser des images directement dans les canaux web et d’impression.<br /> </td> 
  </tr>
    <tr>
   <td>Forms</td> 
   <td> Mise à niveau hors du lieu </td> 
   <td>La prise en charge de la mise à niveau hors site n'est pas disponible <br/> </td> 
  </tr>
  <tr>
   <td>Forms</td> 
   <td> Sidegrade pour les migrations TarMK vers DocumentMK </td> 
   <td> Vous pouvez exporter les données à partir d’un système plus ancien, puis les importer dans un nouveau système de configuration. Pour obtenir des instructions détaillées, reportez-vous à la documentation de mise à niveau d’AEM Forms sur JEE. <br/> </td> 
  </tr>
    <tr>
   <td>Forms</td> 
 <td>Programme d’installation AEM Forms sur JEE 32 bits non disponible.</td> 
   <td>Adobe a arrêté d’envoyer le programme d’installation 32 bits d’AEM Forms sur JEE. Vous pouvez continuer à utiliser le programme d’installation 64 bits pour installer AEM Forms sur JEE. </td>  
  </tr>
    <tr>
    <td>Forms</td> 
    <td>Suppression de la prise en charge de l’utilisation des images DAM dans le composant de fragment .</td> 
    <td> Vous pouvez utiliser le composant Image et Graphique dans le  d’impression de la communication interactive. Si vous utilisez le composant de  de fragments de adaptatif  dans les formulaires adaptatifs, il cesse de fonctionner après la mise à niveau vers AEM Forms 6.4. </td>  
  </tr>
  <tr>
   <td>Forms</td> 
   <td> Suppression de la fonction  de adaptatif</td> 
   <td> Vous pouvez utiliser la fonction de communications interactives pour créer des communications imprimées et basées sur le Web. Si vous utilisez des  adaptatifs, installez le package de compatibilité pour continuer à utiliser le adaptatif existant<br/> </td> 
  </tr>
    <tr>
    <td>Forms</td> 
    <td>Suppression des  spécifiques d’AEM Forms sur JEE.</td> 
    <td>Le AEM Forms sur JEE est remplacé par le AEM (/aem/start.html). </td>  
  </tr>
   <tr>
   <td>Forms</td> 
   <td>Suppression de la prise en charge de Captcha par défaut</td> 
   <td>Utilisez le service reCAPTCHA de Google.</td> 
  </tr>
   <tr>
   <td>Forms</td> 
   <td>Suppression de la prise en charge de Captcha par défaut</td> 
   <td>Utilisez le service reCAPTCHA de Google.</td> 
  </tr>
  <tr>
   <td>Communities</td> 
   <td>La prise en charge de la vérification de Captcha a été supprimée.</td> 
   <td>Utilisez l’intégration captcha personnalisée (telle que reCAPTCHA par Google) pour la vérification.</td> 
  </tr>
 </tbody>
</table>

## Annonce préalable à la prochaine version {#pre-announcement-for-next-release}

Cette section vise à annoncer les modifications à venir dans la prochaine version, qui ne sont pas obsolètes, mais qui auront une incidence sur les clients. Elles sont fournies à des fins de planification.

<table> 
 <tbody>
  <tr>
   <td>Zone<br /> </td> 
   <td>Fonctionnalité<br /> </td> 
   <td>Annonce</td> 
  </tr>
  <tr>
   <td>Prise en charge des navigateurs</td> 
   <td>Microsoft Internet Explorer </td> 
   <td>AEM 6.4 est la dernière version prenant en charge Microsoft Internet Explorer 11.</td> 
  </tr>
  <tr>
   <td>Foundation</td> 
   <td>Structure de l’interface utilisateur</td> 
   <td>Adobe abandonne les composants de l’interface utilisateur 2 de Coral en 2019. AEM 6.4 est entièrement basé sur l’interface utilisateur 3 de Coral (introduite avec AEM 6.2). Adobe recommande à ses clients et partenaires qui ont créé des interfaces utilisateur personnalisées avec Coral 2 de les reconfigurer en Coral 3. Adobe offers a tool to convert Coral 2 dialogs to Coral 3 - <a href="/help/sites-developing/dialog-conversion.md">Read more</a>.</td> 
  </tr>
 </tbody>
</table>
