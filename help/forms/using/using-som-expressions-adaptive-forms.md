---
title: Utilisation d’expressions SOM dans des formulaires adaptatifs
seo-title: Utilisation d’expressions SOM dans des formulaires adaptatifs
description: Découvrez comment extraire les expressions SOM d’un panneau de formulaire adaptatif.
seo-description: Découvrez comment extraire les expressions SOM d’un panneau de formulaire adaptatif.
uuid: 4bc80e2a-3563-48a3-996d-021b701bc2ee
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: 7dff7ef2-80d1-434a-b9b0-ac6654736602
translation-type: tm+mt
source-git-commit: f824b449b85ad7900aaf73fd79614f5e6140f873
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 89%

---


# Utilisation d’expressions SOM dans des formulaires adaptatifs  {#using-som-expressions-in-adaptive-forms}

Les formulaires adaptatif sont modélisés comme des pages AEM, représentées par des structures de contenu JCR dans le référentiel AEM. L’élément clé de la structure de contenu est le nœud du guideContainer. Sous le guideContainer, il existe un rootPanel pouvant contenir un panneau et des champs imbriqués.

Vous pouvez utiliser un modèle d’objet de script (SOM) pour référencer des valeurs, des propriétés et des méthodes dans un modèle d’objet de document (DOM) particulier. Un DOM organise les objets et les propriétés de mémoire dans une arborescence. Une expression SOM référence des champs ou des éléments de dessin et des panneaux.

L’image suivante illustre une structure de noeud à laquelle un formulaire adaptatif se traduit lorsque vous ajoutez des composants à un formulaire. Par exemple, vous pouvez ajouter un panneau au panneau racine et un bouton radio au panneau transformé en DOM à l’exécution. L’Expression SOM du champ de bouton radio dans le formulaire adaptatif est spécifiée comme `guide[0].guide1[0].guideRootPanel[0].panel1[0].radiobutton[0]`.

![Arborescence DOM](assets/hierarchy-1.png)

Une expression SOM pour tout élément dans un formulaire adaptatif est précédée de `guide[0].guide1[0]`. La position d’un composant dans la hiérarchie de la structure de nœud est utilisée pour dériver son expression SOM.

![Arborescence DOM à deux boutons radio](assets/hierarchy_radio_button.png)

L’expression SOM change lorsque vous modifiez la position des boutons radio dans le formulaire adaptatif. Dans le mode création, vous pouvez afficher l’expression SOM d’un champ ou d’un élément dans AEM Forms à l’aide de l’option Visualiser l’expression SOM. L’option apparaît dans le panneau et lorsque vous faites un clic droit sur le champ ou sur l’élément.

![Extraction des expressions SOM dans un formulaire adaptatif](assets/som-expressions.png)

Dans les panneaux, vous pouvez accéder à la fonction depuis la barre d’outils du panneau. La fonction facilite la création de scripts par les auteurs de formulaires adaptatifs.

![Extraction des expressions SOM à l’aide de la barre d’outils du panneau](assets/som-expression.png)

Certaines API répertoriées dans [GuideBridge](https://helpx.adobe.com/aem-forms/6/javascript-api/GuideBridge.md) utilisent l’expression SOM d’un élément. Par exemple, pour centrer l’attention sur un champ particulier d’un formulaire adaptatif, transmettez l’expression SOM correspondante à l’`getFocus`API dans le `guideBridge`.

