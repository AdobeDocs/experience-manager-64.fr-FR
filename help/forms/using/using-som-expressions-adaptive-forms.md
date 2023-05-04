---
title: Utiliser des expressions SOM dans des formulaires adaptatifs
seo-title: Using SOM expressions in adaptive forms
description: Découvrez comment extraire les expressions SOM d’un panneau d’un formulaire adaptatif.
seo-description: Learn how to extract SOM expressions of a panel of an adaptive form.
uuid: 4bc80e2a-3563-48a3-996d-021b701bc2ee
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: 7dff7ef2-80d1-434a-b9b0-ac6654736602
feature: Adaptive Forms
exl-id: e4680ede-6a02-4b8b-8a6f-9599a05da8e7
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 53%

---

# Utiliser des expressions SOM dans des formulaires adaptatifs {#using-som-expressions-in-adaptive-forms}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Les formulaires adaptatifs sont modélisés comme AEM Page qui est représenté comme structure de contenu JCR dans AEM référentiel. L’élément clé de la structure de contenu est le noeud guideContainer . Sous le guideContainer, il existe un rootPanel qui peut contenir un panneau et des champs imbriqués.

Vous pouvez utiliser un modèle d’objet de script (SOM) pour référencer des valeurs, des propriétés et des méthodes dans un modèle d’objet de document (DOM) particulier. Un DOM organise les objets et les propriétés de mémoire dans une hiérarchie d’arborescence. Une expression SOM référence des champs/éléments de dessin et des panneaux.

L’image suivante illustre une structure de nœud d’un formulaire adaptatif traduite lorsque vous ajoutez des composants à un formulaire. Par exemple, vous pouvez ajouter un panneau au panneau racine et un bouton radio au panneau transformé en DOM à l’exécution. L’expression SOM du champ de bouton radio du formulaire adaptatif est spécifiée comme `guide[0].guide1[0].guideRootPanel[0].panel1[0].radiobutton[0]`.

![Arborescence DOM](assets/hierarchy-1.png)

Une expression SOM pour tout élément dans un formulaire adaptatif est précédée de `guide[0].guide1[0]`. La position d’un composant dans la hiérarchie de la structure de nœud est utilisée pour dériver son expression SOM.

![Arborescence DOM à deux boutons radio](assets/hierarchy_radio_button.png)

L’expression SOM change lorsque vous modifiez la position des boutons radio dans le formulaire adaptatif. En mode création, vous pouvez afficher l’expression SOM d’un champ ou d’un élément dans AEM Forms à l’aide de l’option Afficher l’expression SOM . L’option apparaît dans le panneau et lorsque vous cliquez avec le bouton droit sur le champ ou sur l’élément.

![Extraction des expressions SOM dans un formulaire adaptatif](assets/som-expressions.png)

Dans les panneaux, vous pouvez accéder à la fonction depuis la barre d’outils du panneau. La fonction facilite la création de scripts par les auteurs de formulaires adaptatifs.

![Extraction des expressions SOM à l’aide de la barre d’outils du panneau](assets/som-expression.png)

Certaines API répertoriées dans [GuideBridge](https://helpx.adobe.com/aem-forms/6/javascript-api/GuideBridge.md) utilisent l’expression SOM d’un élément. Par exemple, pour centrer l’attention sur un champ particulier d’un formulaire adaptatif, transmettez l’expression SOM correspondante à l’`getFocus`API dans le `guideBridge`.
