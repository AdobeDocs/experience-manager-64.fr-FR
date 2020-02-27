---
title: Composant de commentaires d’incrustation
seo-title: Composant de commentaires d’incrustation
description: Présentation du composant de commentaires d’incrustation
seo-description: Présentation du composant de commentaires d’incrustation
uuid: 634240e2-99bb-4107-89f5-c66d53e2515d
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 4849da13-518c-40c8-b80e-1b2264d7f8f5
translation-type: tm+mt
source-git-commit: 8f169bb9b015ae94b9160d3ebbbd1abf85610465

---


# Composant de commentaires d’incrustation {#overlay-comments-component}

L’intention de [superposer](client-customize.md#overlays) un composant par défaut est de modifier globalement l’aspect ou le comportement d’un composant, pour toutes les références relatives au composant. Il dépend de la nature de sling pour résoudre le problème dans le dossier /apps avant de rechercher dans le dossier /libs. Le chemin d’accès au composant est donc identique au chemin d’accès au composant par défaut, sauf qu’il se trouve dans le dossier /apps et non dans le dossier /libs.

## Exemple {#example}

Supposons que vous souhaitiez modifier la fonction de commentaire afin qu’elle corresponde à la conception de votre site Web, en modifiant l’en-tête du commentaire afin qu’il n’affiche plus l’avatar d’un commentaire. Les solutions de masquage de l’avatar utilisent CSS ou, comme décrit ici, superposent le fichier header.jsp dans le dossier des applications afin que le code HTML contenant l’avatar ne soit jamais envoyé au client.

Pour superposer des commentaires, vous devez :

1. [Page Commentaires](overlay-create-comments-page.md)
1. [Création de noeuds](overlay-create-nodes.md)
1. [Modifier l’aspect](overlay-alter-appearance.md)

