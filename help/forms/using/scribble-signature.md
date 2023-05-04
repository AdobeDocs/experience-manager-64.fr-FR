---
title: Utiliser la signature tactile dans les formulaires HTML5
seo-title: Using Scribble Signature in HTML5 forms
description: Les formulaires HTML5 sont de plus en plus utilisés sur les périphériques tactiles, qui prennent tous en charge les signatures. La signature de documents sur les périphériques mobiles devient une méthode acceptée de signature de formulaires sur les périphériques mobiles.
seo-description: HTML5 forms are increasingly used on touch devices, and one common requirement is to support signatures. Signing documents on mobile devices is becoming an accepted way of signing forms on mobile devices.
uuid: afac2d37-ef0d-428b-aed7-64a00d62792d
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: designer
discoiquuid: abb5513f-c824-4dc2-8617-29ea47684afe
feature: Designer
exl-id: 8b6b151d-2422-4261-9edb-66efe3d33f8b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '694'
ht-degree: 31%

---

# Utiliser la signature tactile dans les formulaires HTML5 {#using-scribble-signature-in-html-forms}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Les formulaires HTML5 sont de plus en plus utilisés sur les périphériques tactiles, qui prennent tous en charge les signatures. L’écriture de scripts (avec un stylet ou un doigt) devient une méthode acceptée de signature de formulaires sur les périphériques mobiles. Les formulaires HTML5 et Forms Designer offrent désormais la possibilité d’afficher un champ de signature tactile dans le formulaire. Lorsque le formulaire est rendu dans le navigateur, vous pouvez vous connecter à ces champs à l’aide d’un stylet, d’une souris ou d’un doigt.

## Comment concevoir un formulaire à l’aide d’un champ de signature tactile {#how-to-design-a-form-using-scribble-signature-field}

1. Ouvrez un formulaire dans Forms Designer.
1. Faites glisser le champ de signature tactile vers la page.

   ![designer_scribble](assets/designer_scribble.png)

   >[!NOTE]
   >
   >Les dimensions du champ sélectionné dans Forms Designer sont reflétées quand le champ est rendu. Toutefois, la dimension de la zone de signature rendue est calculée en fonction des proportions du champ et non de la dimension spécifiée dans Forms Designer.

1. Configurez le champ de signature tactile.

   Par défaut, le champ de signature tactile marque les informations de géolocalisation comme étant obligatoires pendant le processus de signature sur iPad (elles sont facultatives pour les autres périphériques). Ce comportement par défaut peut être remplacé en modifiant la valeur de la propriété `geoLocMandatoryOnIpad`. Cette propriété est exposée sous la forme d’extras dans le champ de signature tactile. Les étapes de modification sont les suivantes :

   1. Sur le formulaire, sélectionnez le champ de signature tactile.
   1. Sélectionnez l’onglet **Source XML**.

      >[!NOTE]
      >
      >Pour ouvrir l’onglet Source XML, cliquez sur **Affichage** > **Source XML**.

   1. Recherchez la balise `<ui>` dans la balise `<field>` et modifiez le code source pour qu’il ressemble à l’exemple suivant :

      ```xml
      <extras name="x-scribble-add-on">
      <boolean name="geoLocMandatoryOnIpad">0</boolean>
      </extras>
      ```

   1. Sélectionnez la **Vue de conception** . Dans la boîte de confirmation, cliquez sur **Oui**.
   1. Enregistrez le formulaire.

1. Effectuez le rendu du formulaire sur un navigateur d’appareil/de bureau pris en charge.

## Interface avec les signatures tactiles {#interfacing-with-the-scribble-signatures}

### Signature {#signing}

Une fois qu’un champ de signature tactile a été ajouté au formulaire et rendu, cliquez ou appuyez sur le champ pour ouvrir une boîte de dialogue. L’utilisateur peut apposer une signature tactile dans la zone de dessin désignée par un rectangle en pointillés, à l’aide d’une souris, d’un doigt ou d’un stylet.

![géolocalisation](assets/geolocation.png)

**A.** Pinceau **B.** Gomme **C.** Géolocalisation **D.** Informations de géolocalisation

### Géo-balisage {#geo-tagging}

Lorsque vous cliquez sur l’icône de géolocalisation lors de la création de la saisie tactile, l’emplacement géographique et les informations temporelles sont incorporés dans le champ.

>[!NOTE]
Dans iPad, l’incorporation des informations de géolocalisation est obligatoire par défaut.

Dans iPad, l’icône de géolocalisation n’est pas affichée par défaut et les informations de géolocalisation sont automatiquement incorporées lorsque vous cliquez sur **OK**.

Pour les iPad, ce paramètre peut être modifié en remplaçant la valeur du paramètre `geoLocManadatoryOnIpad` par `0`, dans les paramètres initiaux du champ.

* Lorsque les informations de géolocalisation sont obligatoires, une zone de dessin réduite est présentée à l’utilisateur. Le texte de géolocalisation est ajouté lorsque l’utilisateur clique **OK** sur la zone restante.
* Dans d’autres cas, l’utilisateur se voit présenter une zone de dessin complète. Si l’utilisateur choisit d’incorporer des informations de géolocalisation, cette zone est redimensionnée pour s’adapter au texte de géolocalisation.

### Effacement d’une signature {#clearing-a-signature}

Lorsque vous utilisez cette fonctionnalité, un utilisateur peut cliquer sur l’icône **Gomme** pour effacer le champ et recommencer. Si des informations de géolocalisation ont été ajoutées, elles sont également effacées.

### Enregistrement d’une signature {#saving-a-signature}

Cliquez sur le bouton **OK** enregistre la saisie tactile sous forme d’image dans le champ. L’image et les valeurs peuvent être envoyées au serveur pour un traitement ultérieur. Une fois qu’un utilisateur a cliqué sur **OK**, la saisie tactile effectuée est verrouillée. La signature ne peut plus être modifiée à l’aide du widget de saisie tactile.

Appuyez ou cliquez sur le champ de saisie tactile pour ouvrir la boîte de dialogue en mode lecture seule.

![3](assets/3.png)

### Sélection de la taille du stylo {#selecting-pen-size}

Cliquez sur l’icône **Brosses** pour afficher la liste des tailles de stylo disponibles. Cliquez ou appuyez sur la taille d’un stylo pour utiliser le stylo correspondant.

### Suppression des signatures du formulaire {#delete-signatures-from-the-form}

Pour supprimer les signatures du formulaire :

* (Appareils mobiles) Appuyez longuement sur le champ de signature, puis, dans la boîte de dialogue de confirmation, appuyez sur **Oui**.
* (Bureau) Pointez sur le champ de signature, puis cliquez sur le bouton **Annuler** puis, dans la boîte de dialogue de confirmation, cliquez sur **Oui**.
