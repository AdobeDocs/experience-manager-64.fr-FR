---
title: Configurer les messages de validation
seo-title: Configuring validation messages
description: Découvrez comment spécifier le mode d’affichage des messages de validation et leur emplacement par rapport au formulaire renvoyé dans le navigateur web.
seo-description: Learn how to specify how validation messages are displayed and their location relative to the form returned in the web browser.
uuid: f6bff4fa-f90f-4135-ae40-7ab3d3613122
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 5f2f8129-e45e-4f3f-ae30-c09330d0e152
exl-id: 2016ac85-12a1-42cb-bc03-fced94947010
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 6%

---

# Configurer les messages de validation {#configuring-validation-messages}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Pour les formulaires rendus en HTML, les erreurs de validation de formulaire qui se produisent s’affichent pour l’utilisateur. Vous pouvez personnaliser le mode d’affichage des messages de validation. Selon l’emplacement d’affichage des messages de validation, vous pouvez également contrôler l’emplacement du message dans le formulaire et la taille de la bordure du cadre.

## Définition du mode d’affichage des messages de validation {#specify-how-validation-messages-are-displayed}

1. Dans Administration Console, cliquez sur Services > Forms.
1. Sous Sortie de validation, dans la liste Création de rapports, sélectionnez l’une des options suivantes :

   **Zone de message :** Pour afficher les messages de validation dans une boîte de dialogue distincte.

   **Image :** Pour afficher les messages de validation dans un cadre de la même fenêtre.

   **Aucun cadre :** Pour afficher les messages de validation dans la même fenêtre. Cette valeur est la valeur par défaut.

   **Via API (avec données) :** Pour renvoyer les messages de validation via l’API (avec des données). Les messages de validation ne s’affichent pas à l’écran.

   **Via API (avec formulaire) :** Pour renvoyer les messages de validation via l’API (avec le formulaire). Les messages de validation ne s’affichent pas à l’écran.

   **Aucun :** Pour ne pas afficher de messages de validation.

1. Cliquez sur Enregistrer.

## Spécifier l’emplacement des messages de validation par rapport au formulaire renvoyé dans le navigateur web {#specify-the-location-of-validation-messages-relative-to-the-form-returned-in-the-web-browser}

Lorsque la création de rapports est définie sur Cadre ou Aucun cadre, vous pouvez spécifier l’emplacement des messages de validation.

1. Sous Sortie de validation, sélectionnez l’une des options suivantes dans la liste Position :

   **Left :** Pour afficher les messages de validation sur le côté gauche du navigateur web.

   **Droite :** Pour afficher les messages de validation sur le côté droit du navigateur web.

   **Haut**: Pour afficher les messages de validation en haut du navigateur web. Cette valeur est la valeur par défaut.

   **Bas**: Pour afficher les messages de validation au bas du navigateur web.

1. Cliquez sur Enregistrer.

## Définition de la taille de bordure du cadre {#specify-the-frame-border-size}

Lorsque l’option Rapport est définie sur Cadre, vous pouvez spécifier la taille de la bordure du cadre.

1. Sous Sortie de validation, dans la zone Taille de bordure, saisissez la taille de la bordure du cadre, en pixels.

   La taille de la bordure doit être supérieure ou égale à 0. La valeur par défaut est 1.

1. Cliquez sur Enregistrer.
