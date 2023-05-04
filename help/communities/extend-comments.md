---
title: Extension du composant Commentaires
seo-title: Extend Comments Component
description: Étendre le composant Commentaires afin de modifier son aspect ou son comportement pour des utilisations spécifiques
seo-description: Extend the Comments component to alter its appearance or behavior for specific uses
uuid: 6f439097-b1d0-4e7d-afcf-01d8f43aa866
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: a07a4690-0e47-4a76-84cb-96abdc70b835
exl-id: f6722953-ff71-4fba-b76e-1d566f71f6d5
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 3%

---

# Extension du composant Commentaires {#extend-comments-component}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

L’intention de [extension](client-customize.md#extensions) un composant par défaut consiste à modifier l’aspect ou le comportement d’un composant pour des utilisations spécifiques.

Le chemin d’accès au composant est unique et référence le composant par défaut comme type de super-ressource. Il y a moins de risque, car la portée est limitée par rapport à la portée globale d’une superposition de composant.

>[!NOTE]
>
>Extension d’une [superposé](client-customize.md#overlays) n’est pas pris en charge.

## Exemple {#example}

Supposons que l’en-tête du composant de commentaire s’affiche différemment sur un site de l’instance AEM, tout en s’affichant avec l’affichage par défaut sur un autre site. Au lieu de superposer le commentaire par défaut, qui modifie le composant de commentaire pour toutes les instances, une meilleure solution consiste à s’assurer que plusieurs composants de commentaire sont disponibles pour utilisation sur différents sites.

Pour mettre en oeuvre cette solution, créez un composant qui étend (remplace) le composant existant et modifiez le script Handlebars. La zone du site qui utilise les nouveaux commentaires peut utiliser le commentaire étendu, tandis que les sites qui utilisent l’aspect par défaut restent inchangés.

Le composant de commentaire est en fait l’un des deux composants qui composent le système de commentaires. Il existe donc deux composants à étendre : *commentaires* et *comment*. Le script à modifier se trouve dans la variable `header.hbs` pendant que le fichier parent *commentaires* component (le système de commentaires) est ce qu’un auteur ajoute réellement à la page.

Pour étendre les commentaires, vous devez :

1. [Création des composants](extend-create-components.md)
1. [Ajout d’un commentaire à un exemple de page](extend-sample-page.md)
1. [Modification de l’aspect](extend-alter-appearance.md)
