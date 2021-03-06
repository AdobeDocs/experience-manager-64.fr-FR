---
title: Intégration du composant Link dans une page
seo-title: Embedding link component in a page
description: 'Vous pouvez utiliser le composant Link pour lier un document adaptatif ou un formulaire adaptatif depuis la page que vous souhaitez.  '
seo-description: You can use the link component to link an adaptive document or an adaptive form from any page.
uuid: fde56b5f-634c-406f-a026-875f972f7c8f
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: publish
discoiquuid: a4a36e73-3f7a-4173-8807-931f26daa35a
exl-id: eb816a35-0773-4eda-95b2-1d351c71be8b
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 100%

---

# Intégration du composant Link dans une page{#embedding-link-component-in-a-page}

## Prérequis {#prerequisites}

Le composant Link est membre de la catégorie Document Services. Assurez-vous que la catégorie Document Services est visible dans le navigateur de composants d’AEM. Si la catégorie n’est pas répertoriée, suivez la procédure décrite à la section [Activation des composants d’un portail de formulaires](/help/forms/using/enabling-forms-portal-components.md).

## Composant Link {#link-component}

Le composant Link permet aux créateurs de portails de formulaires de créer un lien vers un formulaire adaptatif depuis n’importe quel point d’une page. Le composant Link est disponible dans la section Document Services du navigateur de composants.

Suivez les étapes ci-après pour ajouter un composant Link à la page :

1. Faites glisser le composant **Link** sur la page. Sélectionnez un composant et appuyez sur ![cmppr](assets/cmppr.png). La boîte de dialogue Modifier le composant de lien s’ouvre.

   ![edit-link-component](assets/edit-link-component.png)

1. Dans l’onglet **Affichage**, spécifiez ce qui suit :

   * **Link Caption** : texte ou légende du lien.
   * **Link Tooltip** : info-bulle du lien.
   * **Modèle de mise en page** : modèle pour la mise en page du composant Link.

1. Ouvrez l’onglet **Informations d’actif** et spécifiez le type d’actif. Une ressource peut être un **formulaire**. Selon le type de fichier sélectionné, les options ci-dessous s’affichent : 

   * **Chemin d’accès à l’actif** : chemin d’accès au référentiel de stockage de l’actif.
   * **Type de rendu** : le format de rendu : PDF, HTML ou Auto. Le type de rendu Auto détecte l’environnement de l’utilisateur et effectue le rendu du formulaire en conséquence, au format HTML ou PDF. Par exemple, si le formulaire est utilisé sur un périphérique mobile, le type de rendu Auto est effectué au format HTML.
   * **URL d’envoi :** URL du serveur vers lequel sont envoyées les données du formulaire.
   * **Profil HTML** : profil de rendu du formulaire au format HTML.
   * **Profil PDF** : profil de rendu du formulaire au format PDF.

1. Ouvrez l’onglet **Avancé**. Vous pouvez spécifier des paramètres supplémentaires au format de paire clé-valeur. Lorsqu’un clic est effectué sur le lien, ces paramètres supplémentaires sont transmis avec le formulaire.

   Appuyez sur **Terminé** pour enregistrer la règle.

## Méthodes recommandées pour l’utilisation du composant Link {#best-practices-for-using-link-component-br}

* Veillez à sélectionner PDF comme type de rendu si le chemin spécifié sous Form Path pointe vers un document dont le format de rendu autorisé est PDF.
* La valeur Submit URL d’un formulaire peut être spécifiée à plusieurs emplacements et l’ordre de priorité s’établit comme suit :

   1. La valeur Submit URL intégrée dans le formulaire (dans le bouton d’envoi) a la priorité la plus élevée.
   1. La valeur Submit URL mentionnée dans Forms Manager possède une priorité moyenne.
   1. La valeur Submit URL mentionnée dans Forms Portal a la priorité la plus faible.
