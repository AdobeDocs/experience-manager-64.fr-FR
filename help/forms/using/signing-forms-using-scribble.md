---
title: Application de signatures électroniques à un formulaire à l’aide de signatures tactiles
seo-title: Apply electronic signatures to a form using scribble signatures
description: Signature de formulaires à l’aide de la saisie tactile
seo-description: Signing forms using scribble
uuid: e807d0de-6d5f-458e-be3e-273ed7a521c0
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: 6a806727-28c5-430e-9a83-b43e0e9d9e1c
feature: Adaptive Forms
exl-id: a870c4b7-4040-4bd8-b477-286ebe6a4b01
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '534'
ht-degree: 63%

---

# Application de signatures électroniques à un formulaire à l’aide de signatures tactiles {#apply-electronic-signatures-to-a-form-using-scribble-signatures}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Vous pouvez utiliser le composant **Signature tactile** et le composant **Étape de signature** pour tracer la signature (saisie tactile) sur un formulaire adaptatif. Le composant Étape de signature affiche une version PDF du formulaire adaptatif. Vous avez besoin de l’option Document d’enregistrement activée ou de formulaires adaptatifs basés sur un modèle de formulaire pour utiliser le composant Étape de signature.

Les deux composants présentent une fenêtre, comme illustré ci-dessous, pour signer un formulaire. Vous pouvez également cliquer sur l’icône de géolocalisation ![aem_6_3_geolocation](assets/aem_6_3_geolocation.png) pour ajouter la géolocalisation à la signature.

![Boîte de dialogue de signature tactile](assets/scribble-signature.png)

## Configuration d’un formulaire adaptatif pour utiliser la signature tactile {#configure-an-adaptive-form-to-use-scribble-signature}

1. Créez une option Document d’enregistrement activée ou un formulaire adaptatif basé sur modèle de formulaire. Pour obtenir des informations détaillées, voir [Création d’un formulaire adaptatif](/help/forms/using/creating-adaptive-form.md).
1. Faites glisser et déposez le composant **Signature tactile** du navigateur de composant vers le formulaire adaptatif.
1. Appuyez sur l’icône de ![configuration](assets/configure.png) **Configurer**. Vous ouvrez ainsi le navigateur de propriétés qui affiche les propriétés du composant Signature tactile. Configurez les propriétés du composant Signature tactile.
1. Faites glisser et déposez le composant Étape de signature du navigateur de composant vers le formulaire adaptatif.

   >[!NOTE]
   >
   >Le composant Étape de signature prend toute la largeur disponible pour le formulaire. Il est recommandé de ne pas avoir d’autre composant sur la section contenant le composant Étape de signature.

1. Dans l’explorateur de contenu, appuyez sur **Conteneur de formulaires**, puis sur l’icône **Configurer** ![configure](assets/configure.png). L’explorateur de propriétés s’ouvre et affiche les propriétés du conteneur de formulaires adaptatifs. Accédez à **Conteneur de formulaires adaptatifs** > **Signature électronique** et désélectionnez l’option **Activer Acrobat Sign** . Appuyez sur l’icône Terminé ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png) pour enregistrer les modifications.

   >[!NOTE]
   >
   >Lorsque vous ajoutez un composant Étape de signature à un formulaire adaptatif, l’option Activer Acrobat Sign est sélectionnée automatiquement.

1. Appuyez sur l’icône de ![configuration](assets/configure.png) **Configurer**. Il ouvre l’explorateur de propriétés et affiche les propriétés de l’étape Signature. Configurez les propriétés suivantes :

   * **Nom de l’élément** : spécifiez le nom du composant.
   * **Titre :** Spécifiez le titre unique du composant.
   * **Message du modèle :** Spécifiez le message à afficher pendant le chargement du PDF de signatures. Les services Acrobat Sign prennent du temps pour préparer et charger le PDF de signatures.
   * **Service de signature :** sélectionnez l’option **Signature tactile**.
   * **Classe CSS** : spécifiez la classe CSS de la bibliothèque client, le cas échéant. Il est recommandé d’utiliser des [thèmes](/help/forms/using/themes.md) et des [styles en ligne](/help/forms/using/inline-style-adaptive-forms.md) au lieu de la classe CSS.

   Appuyez sur l’icône Terminé ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png) pour enregistrer les modifications. La signature est configurée correctement.

   Désormais, lorsque vous remplissez un formulaire, une version PDF du formulaire adaptatif s’affiche et des options pour signer le document du PDF sont fournies. Pour plus d’informations, voir [Signature d’un formulaire adaptatif en utilisant la signature tactile](/help/forms/using/signing-forms-using-scribble.md#p-sign-an-adaptive-form-using-scribble-signature-p).

## Signature d’un formulaire adaptatif à l’aide de la signature tactile {#sign-an-adaptive-form-using-scribble-signature}

1. Une fois que vous avez rempli un formulaire adaptatif et atteint la page Étape de signature, l’écran de signature s’affiche.

   ![Écran de signature de la page EchoSign](assets/esignscribblesign.jpg)

1. Cliquez sur **[!UICONTROL Sign]**. La boîte de dialogue de signature tactile s’affiche. Signez le formulaire et cliquez sur l’icône Terminé ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png) pour enregistrer la signature.

   ![Boîte de dialogue de signature tactile](assets/scribblewidget.jpg)

1. Cliquez sur Terminer pour terminer le processus de signature.

   ![Terminer le processus de signature](assets/scribblecomplete.jpg)

Les signatures sont ajoutées au formulaire, et le contrôle de formulaire passe au panneau suivant.
