---
title: Configuration du message du jour
seo-title: Setting the message of the day
description: Le message du jour vous permet de définir un message à afficher sur la page d’accueil de l’interface utilisateur de Workspace.
seo-description: The message of the day let you set a message to be displayed on the Welcome page in the Workspace user interface.
uuid: 9c664438-6fc0-498e-bb3f-4c6bcb9414a7
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_workspace
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: c2b3a412-70c2-4257-bfb4-1430bb1f8891
exl-id: 7ddd5a4d-2b46-4408-b241-81e16cfead3c
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 26%

---

# Configuration du message du jour {#setting-the-message-of-the-day}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Vous pouvez définir un message à afficher sur la page d’accueil de l’interface utilisateur de Workspace.

Si nécessaire, vous pouvez utiliser les balises de HTML prises en charge par Adobe Flash® Player pour mettre en forme l’aspect du texte :

* &lt;a> Balise d’ancrage
* &lt;b> Balise de caractères gras
* &lt;br> Balise de saut
* &lt;font> Balise de police
* &lt;img> Balise d’image
* &lt;i> Balise italique
* &lt;li> Balise d’élément de liste
* &lt;p> Balise de paragraphe
* &lt;span> Balise span
* &lt;textformat> Balise de format texte
* &lt;u> Balise de soulignement

Pour plus d’informations sur les balises prises en charge, voir la définition de la propriété `htmlText` de la classe TextField dans le document [Flex Language Reference](https://flex.apache.org/).

## Définition du message du jour {#set-the-message-of-the-day}

1. Dans Administration Console, cliquez sur Services > Workspace > Message du jour.
1. Dans la zone Message du jour, indiquez le texte à afficher sur l’écran de bienvenue.
1. Cliquez sur Enregistrer.

>[!NOTE]
>
>L’espace de travail Flex est obsolète pour la version d’AEM Forms.
