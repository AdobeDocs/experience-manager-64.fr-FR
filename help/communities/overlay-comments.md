---
title: Composant des commentaires de superposition
seo-title: Composant des commentaires de superposition
description: Présentation du composant Commentaires de superposition
seo-description: Présentation du composant Commentaires de superposition
uuid: 634240e2-99bb-4107-89f5-c66d53e2515d
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 4849da13-518c-40c8-b80e-1b2264d7f8f5
exl-id: 31528814-02bc-4978-87fa-5c8074b454ed
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 0%

---

# Composant des commentaires de superposition {#overlay-comments-component}

L’intention de [superposer](client-customize.md#overlays) un composant par défaut est de modifier l’aspect ou le comportement d’un composant globalement, pour toutes les références relatives au composant. Il repose sur la nature de sling à résoudre dans le dossier /apps avant de rechercher dans le dossier /libs . Par conséquent, le chemin d’accès au composant est identique à celui du composant par défaut, sauf qu’il se trouve dans le dossier /apps et non dans le dossier /libs .

## Exemple {#example}

Supposons que vous souhaitiez modifier la fonction de commentaire afin qu’elle corresponde à la conception de votre site web, en modifiant l’en-tête du commentaire afin qu’il n’affiche plus l’avatar pour un commentaire. Les solutions pour masquer l’avatar utilisent soit CSS, soit, comme décrit ici, le recouvrement du fichier header.jsp dans le dossier des applications afin que le code HTML contenant l’avatar ne soit jamais envoyé au client.

Pour superposer des commentaires, vous devez :

1. [Page Commentaires](overlay-create-comments-page.md)
1. [Création de noeuds](overlay-create-nodes.md)
1. [Modification de l’aspect](overlay-alter-appearance.md)
