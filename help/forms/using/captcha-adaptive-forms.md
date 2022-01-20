---
title: Utilisation de CAPTCHA dans les formulaires adaptifs
seo-title: Using CAPTCHA in adaptive forms
description: Découvrez comment configurer le service AEM CAPTCHA ou Google reCAPTCHA dans les formulaires adaptatifs.
seo-description: Learn how to configure AEM CAPTCHA or Google reCAPTCHA service in adaptive forms.
uuid: 8bcb0dd7-b43c-4a36-8f6b-7875b68f9ba1
contentOwner: vishgupt
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author, adaptive_forms
discoiquuid: 32369b0b-5abf-487d-ae6b-972c254eb7e2
feature: Adaptive Forms
exl-id: 1129004b-5e8b-42fd-98ed-f203edde93b9
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '655'
ht-degree: 98%

---

# Utilisation de CAPTCHA dans les formulaires adaptifs {#using-captcha-in-adaptive-forms}

CAPTCHA (Completely Automated Public Turing test to tell Computers and Humans Apart, Test public de Turing complètement automatique ayant pour but de différencier les humains des ordinateurs) est un programme couramment utilisé dans les transactions en ligne pour différencier les humains des programmes automatisés ou des robots. Cela pose un défi et évalue la réponse de l’utilisateur pour déterminer s’il s’agit d’un humain ou d’un robot interagissant avec le site. Cela empêche l’utilisateur de continuer si le test échoue et permet de sécuriser les transactions en ligne en empêchant les robots d’envoyer du spam ou des éléments malveillants.

AEM Forms prend en charge CAPTCHA dans les formulaires adaptatifs. Vous pouvez utiliser le service reCAPTCHA de Google pour implémenter CAPTCHA.

>[!NOTE]
>
>AEM Forms prend en charge uniquement reCaptcha 2. Toute autre version n’est pas prise en charge.
>
>CAPTCHA dans les formulaires adaptatifs n’est pas pris en charge dans le mode hors ligne sur l’application AEM Forms.

## Configuration du service ReCAPTCHA de Google {#google-recaptcha}

Les auteurs du formulaire peuvent utiliser le service reCAPTCHA de Google pour mettre en place CAPTCHA dans les formulaires adaptatifs. Il offre des fonctionnalités CAPTCHA avancées pour protéger votre site. Pour plus d’informations sur le fonctionnement de reCAPTCHA, voir [Google reCAPTCHA](https://developers.google.com/recaptcha/).

![recaptcha](assets/recaptcha.png)

Pour mettre en place le service reCAPTCHA dans AEM Forms :

1. Obtenez la [paire de clés API reCAPTCHA](https://www.google.com/recaptcha/admin) auprès de Google. Elle comprend une clé de site et une clé secrète.
1. Créez un conteneur de configurations pour les services cloud.

   1. Accédez à **[!UICONTROL Outils > Général > Navigateur de configuration]**.
      * Pour plus d’informations, consultez la documentation relative au [](/help/sites-administering/configurations.md)Navigateur de configuration.
   1. Procédez comme suit pour activer le dossier global pour les configurations cloud ou ignorez cette étape pour créer et configurer un autre dossier pour les configurations de service cloud.

      1. Dans le navigateur de configuration, sélectionnez le dossier **[!UICONTROL global]** et appuyez sur **[!UICONTROL Propriétés]**.
      1. Dans la boîte de dialogue Propriétés de configuration, activez **[!UICONTROL Configurations cloud]**.
      1. Appuyez sur **[!UICONTROL Enregistrer et fermer]** pour enregistrer la configuration et fermer la boîte de dialogue.
   1. Dans le navigateur de configuration, appuyez sur **[!UICONTROL Créer]**.
   1. Dans la boîte de dialogue Créer une configuration, indiquez un titre pour le dossier et activez **[!UICONTROL Configurations cloud]**.
   1. Appuyez sur **[!UICONTROL Créer]** pour créer le dossier activé pour les configurations de service cloud.


1. Configurez le service cloud pour reCAPTCHA.

   1. Sur votre instance d’auteur AEM, accédez à ![outils](assets/tools.png) >  **Cloud Services**.
   1. Appuyez sur **[!UICONTROL reCAPTCHA]**. La page Configurations s’ouvre. Sélectionnez le conteneur de configurations créé à l’étape précédente et appuyez sur **[!UICONTROL Créer]**.
   1. Indiquez le nom, la clé de site et la clé secrète pour le service reCAPTCHA, puis appuyez sur **[!UICONTROL Créer]** pour créer la configuration du service cloud.
   1. Dans cette boîte de dialogue, spécifiez le site et les clés de site et secrète obtenues à l’étape 1. Appuyez sur **[!UICONTROL Enregistrer les paramètres]** puis sur **[!UICONTROL OK]** pour terminer la configuration.

   Une fois que le service reCAPTCHA est configuré, il peut être utilisé dans les formulaires adaptatifs. Pour plus d’informations, voir [Utilisation de CAPTCHA dans les formulaires adaptatifs](#using-captcha).

## Utiliser CAPTCHA dans les formulaires adaptatifs {#using-captcha}

Pour utiliser CAPTCHA dans les formulaires adaptatifs :

1. Ouvrez un formulaire adaptatif en mode d’édition.

   >[!NOTE]
   >
   >Assurez-vous que le conteneur de configurations sélectionné lors de la création d’un formulaire adaptatif contient le service cloud reCAPTCHA. Vous pouvez également modifier les propriétés de formulaire adaptatif pour modifier le conteneur de configurations associé au formulaire.

1. À partir du navigateur de composant, faites glisser et déposez le composant **[!UICONTROL Captcha]** sur le formulaire adaptatif.

   >[!NOTE]
   >
   >L’utilisation de plusieurs composants Captcha dans un formulaire adaptatif n’est pas prise en charge. En outre, il n’est pas recommandé d’utiliser CAPTCHA dans un panneau marqué pour le chargement différé ou dans un fragment.

   >[!NOTE]
   >
   >Captcha est sensible au facteur temps et expire dans la minute. Par conséquent, il est recommandé de placer le composant Captcha juste avant le bouton Envoyer dans le formulaire adaptatif.

1. Sélectionnez le composant Captcha que vous avez ajouté et appuyez sur ![cmppr](assets/cmppr.png) pour modifier ses propriétés.
1. Indiquez un titre pour le widget CAPTCHA. La valeur par défaut est **Captcha**. Sélectionnez **[!UICONTROL Masquer le titre]** si vous ne voulez pas que le titre apparaisse.
1. Dans le menu déroulant **[!UICONTROL Service Captcha]**, sélectionnez **[!UICONTROL reCaptcha]** pour activer le service reCAPTCHA si vous l’avez configuré comme décrit dans [Service ReCAPTCHA de Google](#google-recaptcha). Sélectionnez une configuration dans la liste déroulante Paramètres. En outre, sélectionnez la taille **[!UICONTROL Normal]** ou **[!UICONTROL Compact]** pour le widget reCAPTCHA.

   >[!NOTE]
   >
   >Ne sélectionnez pas **[!UICONTROL Par défaut]** dans le menu déroulant Service Captcha puisque le service par défaut AEM CAPTCHA est obsolète.

1. Enregistrez les propriétés.

Le service reCAPTCHA est activé sur le formulaire adaptatif. Vous pouvez prévisualiser le formulaire et voir le fonctionnement de CAPTCHA.
