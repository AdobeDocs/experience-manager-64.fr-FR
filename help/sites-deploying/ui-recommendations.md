---
title: Recommandations d’interfaces utilisateur aux clients
seo-title: Recommandations d’interfaces utilisateur aux clients
description: 'Liste de recommandations relatives aux interfaces utilisateur classiques et aux interfaces utilisateur optimisées pour les écrans tactiles. '
seo-description: 'Liste de recommandations relatives aux interfaces utilisateur classiques et aux interfaces utilisateur optimisées pour les écrans tactiles. '
uuid: c661fb10-4dbc-4f8b-93be-3e77af1ad095
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: 42bf42cb-0c6c-4390-8170-2c540c4d3ed3
translation-type: tm+mt
source-git-commit: b01e95110bffc1ee96e0814e782d716ed949c1b4
workflow-type: tm+mt
source-wordcount: '808'
ht-degree: 98%

---


# Recommandations d’interfaces utilisateur aux clients{#user-interface-recommendations-for-customers}

Adobe Experience Manager 6.4 est livré avec deux interfaces utilisateur : l’IU unifiée Experience Cloud et l’IU classique.

Ce document vise à guider les clients dans leur choix d’interface utilisateur en fonction de leurs besoins.

Termes à retenir : 

* **IU (ou IU standard)** Interface utilisateur moderne, introduite avec la version 5.6.0 en tant qu’aperçu de la technologie, puis développée avec les versions suivantes. Elle est basée sur l’expérience utilisateur unifiée pour Adobe Experience Cloud, connue précédemment sous le nom d’interface utilisateur tactile.

* **IU classique** Interface utilisateur basée sur la technologie ExtJS introduite avec CQ 5.1 en 2008.

* **L’administrateur du site** Fonctionnalités de gestion de la hiérarchie du site (déplacer, activer, gérer les références) et de création de nouvelles pages.

* **Création de pages** Fonctionnalités de modification du contenu d’une page.

* **Administrateur DAM/Assets** Fonctionnalités de gestion des ressources numériques (y compris les images, les vidéos, les documents et les téléchargements).

* **ContextHub** Fonctionnalités de regroupement des informations sur le visiteur en vue de les utiliser pour différents objectifs. Fournit une interface utilisateur pour simuler des personnes qui visitent le site. Depuis AEM 6.2, ContextHub a remplacé la technologie précédente, ClientContext.

## Général {#general}

Au cours des dernières années, Adobe a mis à jour toutes les solutions Adobe Experience Cloud grâce à une interface utilisateur unifiée. Les utilisateurs bénéficient d’une expérience constante sur l’ensemble des solutions Experience Cloud avec des modèles communs expliquant comment utiliser et activer les applications. Avec chaque version, Adobe a optimisé son interface utilisateur à l’aide des commentaires des clients utilisant les différentes solutions.

L’interface utilisateur d’origine pour Adobe Experience Manager (précédemment nommé CQ5), introduite en 2008 et utilisée par les clients utilisant les versions 5.0 à 5.6.1, est présente dans AEM 6.4. Ceci garantit que les clients peuvent effectuer la mise à jour vers la version 6.4 et bénéficier d’une plateforme mise à jour avec de nouvelles fonctionnalités, tout en utilisant la même interface d’utilisateur.

Adobe recommande aux utilisateurs de planifier le passage à la nouvelle interface utilisateur en 2018 ou 2019. Cela peut être effectué au cours de la mise à jour vers la version 6.4 ou dans un projet distinct après la mise à jour, qui inclut les réglages nécessaires aux personnalisations et aux boîtes de dialogue de composant. 

Adobe ne prévoit pas d’apporter d’autres améliorations à l’interface utilisateur classique à partir d’AEM 6.4. Notez que l’interface utilisateur classique continuera de bénéficier d’une prise en charge totale, bien qu’elle soit obsolète.

## Règles et recommandations {#rules-and-recommendations}

Voici une liste de recommandations de la gestion du produit pour Adobe Experience Manager 6.4 :

<table> 
 <tbody> 
  <tr> 
   <th>Mon projet…</th> 
   <th>Recommandations</th> 
  </tr> 
  <tr> 
   <td>Vient de commencer à utiliser Adobe Experience Manager.</td> 
   <td>Utilisez l’IU par défaut.</td> 
  </tr> 
  <tr> 
   <td><p>Utilise AEM depuis un certain temps.</p> <p>A utilisé l’IU du produit prête à l’emploi et développé des composants personnalisés pour les sites.<br /> </p> </td> 
   <td> 
    <ol> 
     <li>Effectuez la mise à jour vers la version 6.4.</li> 
     <li>Utilisez l’IU par défaut pour l’administration de site, les ressources, etc.<br /> </li> 
     <li>Configurez l’action « Modifier la page » pour ouvrir l’éditeur de page de l’IU classique. Voir <a href="#selecting-your-ui">Choix de l’interface utilisateur</a>.</li> 
    </ol> <p>Ensuite, lors d’une seconde phase :</p> 
    <ol> 
     <li>Mettez à jour vos boîtes de dialogue de composants pour utiliser le format de boîte de dialogue Coral 3. Adobe recommande d’utiliser l’<a href="/help/sites-developing/dialog-conversion.md">outil de conversion de boîte de dialogue</a> pour mettre à jour les composants.</li> 
    </ol> </td> 
  </tr> 
  <tr> 
   <td>A créé un site utilisant ClientContext avec les intégrations.<br /> </td> 
   <td> 
    <ol> 
     <li>Effectuez la mise à jour vers la version 6.4.</li> 
     <li>Utilisez l’IU par défaut pour l’administration de site, les ressources, etc.</li> 
     <li>Configurez l’action « Modifier la page » pour ouvrir l’éditeur de page de l’IU classique. Voir <a href="#selecting-your-ui">Choix de l’interface utilisateur</a>.</li> 
    </ol> <p>Ensuite, lors d’une seconde phase :</p> 
    <ol> 
     <li>Mettez à jour vos boîtes de dialogue de composants pour utiliser le format de boîte de dialogue Coral 3. Adobe recommande d’utiliser l’<a href="/help/sites-developing/dialog-conversion.md">outil de conversion de boîte de dialogue</a> pour mettre à jour les composants.</li> 
     <li>Configurez ContextHub (le remplacement de ClientContext) et mettez à jour les modèles de pages pour utiliser ContextHub. Notez que le ContextHub a un mode de compatibilité qui permet de transférer les entrepôts ClientContext personnalisés.</li> 
    </ol> </td> 
  </tr> 
  <tr> 
   <td><p>Utilise CQ/AEM depuis de nombreuses années.</p> <p>A développé l’IU du produit (par exemple, administrateur de site) et créé des composants avec des boîtes de dialogue de modification complètes.</p> </td> 
   <td><p>Passez à la version 6.4 et configurez l’IU classique en tant qu’interface utilisateur par défaut pour la création de page pour tous les utilisateurs. Voir <a href="#selecting-your-ui">Choix de l’interface utilisateur</a>.</p> <p>Démarrez ensuite un projet pour appliquer la personnalisation et optimiser les boîtes de dialogue du composant au format Coral 3. Voir <a href="#resources-to-help">Ressources d’aide</a>.<br /> </p> </td> 
  </tr> 
 </tbody> 
</table>

## FAQ {#faq}

Voir l’article de la base de connaissances, [FAQ sur la création dans l’interface utilisateur tactile](https://helpx.adobe.com/experience-manager/kb/index/touchui_faq.html) pour en savoir plus, notamment sur la planification du déclassement de l’IU classique.

## Choix de l’interface utilisateur  {#selecting-your-ui}

Voir [Choix de l’interface utilisateur](/help/sites-authoring/select-ui.md) pour plus d’informations sur la configuration de votre système.

## État de l’interface utilisateur optimisée pour les écrans tactiles {#touch-optimized-ui-status}

Pour plus d’informations sur les améliorations apportées à l’interface utilisateur optimisée pour les écrans tactiles dans AEM 6.3 voir la section [Nouveautés](/help/release-notes/release-notes.md#what-s-new) dans les notes de mise à jour.

Pour une présentation complète, voir la page [État des fonctionnalités de l’interface utilisateur optimisée pour les écrans tactiles](/help/release-notes/touch-ui-features-status.md)

## Ressources d’aide {#resources-to-help}

Pour plus d’informations sur la gestion de base :

* [Utilisation de l’environnement de création](/help/sites-authoring/home.md).
* [Création de pages](/help/sites-authoring/author-environment-tools.md).

Pour des informations détaillées de développement :

* [Architecture de l’interface utilisateur optimisée pour les écrans tactiles](/help/sites-developing/touch-ui-concepts.md). 
* Utilisez l’[outil de conversion des boîtes de dialogue](/help/sites-developing/dialog-conversion.md) pour convertir les boîtes de dialogue de modification des composants de l’IU classique à l’IU optimisée pour les écrans tactiles.

* [Structure de l’interface utilisateur optimisée pour les écrans tactiles](/help/sites-developing/touch-ui-structure.md). 

* [Personnalisation des consoles de l’IU optimisée pour les écrans tactiles](/help/sites-developing/customizing-consoles-touch.md) (inclut un exemple de code).

* [Personnalisation de la création de la page dans l’IU optimisée pour les écrans tactiles](/help/sites-developing/customizing-page-authoring-touch.md) (inclut un exemple de code).

* [Séance AEM sur la personnalisation de l’IU optimisée pour les écrans tactiles](https://docs.adobe.com/content/ddc/en/gems/user-interface-customization-for-aem-6.html).
* [Documentation sur l’interface utilisateur Granite](https://helpx.adobe.com/fr/experience-manager/6-4/sites/developing/using/reference-materials/granite-ui/api/index.html).

