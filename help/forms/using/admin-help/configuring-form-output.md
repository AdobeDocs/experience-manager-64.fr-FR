---
title: Configurer la sortie de formulaire
seo-title: Configuring form output
description: Découvrez comment configurer la sortie de formulaire.
seo-description: Learn how to configure form output.
uuid: 70aad14e-c845-4ef3-a751-ad8860d5d505
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 17c9b69a-3c6f-47e3-a828-841bb90eba8b
exl-id: b19cae88-a549-41ba-b4a6-4b065a995296
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 38%

---

# Configurer la sortie de formulaire{#configuring-form-output}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

## Spécifiez le type de sortie de HTML renvoyée au navigateur web. {#specify-the-type-of-html-output-returned-to-the-web-browser}

1. Dans Administration Console, cliquez sur Services > Forms.
1. Sous Sortie de formulaire, sélectionnez l’une des options suivantes dans la liste Type de sortie :

   **HTML complet :** Pour effectuer le rendu du formulaire dans des balises de HTML complet (une page de HTML complète). Cette valeur est la valeur par défaut.

   **Corps de formulaire :** pour effectuer le rendu du formulaire avec des balises `<BODY>` (page HTML incomplète).

1. Cliquez sur Enregistrer.

## Spécifiez l’emplacement de rendu du contenu du PDF. {#specify-the-location-where-pdf-content-is-rendered}

1. Sous Sortie de formulaire, sélectionnez l’une des options suivantes dans la liste Rendu au :

   **Client :** Pour effectuer le rendu des PDF forms dans Adobe Acrobat ou Adobe Reader. Le rendu côté client améliore les performances d’AEM forms et s’applique uniquement à la transformation PDFForm.

   **Serveur :** Pour effectuer le rendu des PDF forms sur le serveur d’applications.

   **Automatique :** pour effectuer le rendu du formulaire au format PDF à l’emplacement indiqué par la valeur de configuration `dynamicRender` du formulaire XDP. Cette valeur est la valeur par défaut.

1. Cliquez sur Enregistrer.

## Configuration de l’appel de scripts personnalisés avant envoi de formulaire {#configuring-invocation-of-custom-scripts-before-form-submit}

Pour activer cette fonction, effectuez les étapes suivantes :

1. Connectez-vous à Administration Console.
1. Accédez à **Services** > **formulaires**.
1. Définissez le type de sortie sur Corps de formulaire.
1. Enregistrez les paramètres.
1. Saisissez une variable JavaScript, (__CUSTOM_SCRIPTS_VERSION) dans l’en-tête du code HTML et donnez-lui la valeur 1.

   >[!NOTE]
   >
   >*pour désactiver cette fonction, vous pouvez soit supprimer la variable JavaScript, soit lui donner la valeur 0.*
