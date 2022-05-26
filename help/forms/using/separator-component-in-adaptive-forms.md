---
title: Composant Separator dans les formulaires adaptatifs
seo-title: Separator component in adaptive forms
description: Vous pouvez utiliser le composant séparateur pour isoler visuellement les sections d’un formulaire.
seo-description: You can use the separator component to visually segregate sections of a form.
uuid: d51c3797-8227-41ed-88cd-c56cc129eb86
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: ba674a2d-7c78-430e-8e17-1a18619e71cb
feature: Adaptive Forms
exl-id: 7e37401a-8c63-4711-8a33-61e6bd4b419f
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 94%

---

# Composant Separator dans les formulaires adaptatifs {#separator-component-in-adaptive-forms}

Vous pouvez utiliser le composant séparateur pour isoler visuellement les panneaux d’un formulaire. Vous pouvez définir l’aspect général et le style d’un composant séparateur en spécifiant les propriétés suivantes du composant :

* **Nom d’élément :** spécifie le nom du composant. L’expression SOM intègre au composant la valeur spécifiée dans le champ de nom d’élément.
* **Épaisseur :** indique l’épaisseur en pixels du composant séparateur.
* **Colspan :** spécifie le nombre de colonnes auquel s’applique un composant de séparateur.
* **Classe CSS :** spécifie la classe CSS personnalisée pour le composant séparateur
* **Styles en ligne :** avec AEM Forms, vous pouvez désormais appliquer des styles CSS en ligne à chaque composant de formulaire adaptatif et prévisualiser les modifications en temps réel.

Pour définir les propriétés d’un composant séparateur :

1. Sélectionnez un composant séparateur et appuyez sur ![cmppr](assets/cmppr.png). Les propriétés s’ouvrent dans la zone latérale.
1. Cliquez sur un onglet dans la section Propriétés CSS intégrées pour spécifier les propriétés CSS. Par exemple, dans l’onglet Champ, cliquez sur **Ajouter un élément**. Une ligne avec deux champs est ajoutée.
1. Dans le premier champ de gauche, spécifiez une propriété CSS3 à appliquer. Par exemple, la **bordure**. Vous pouvez également sélectionner une propriété en cliquant sur le bouton de flèche vers le bas. La liste déroulante n’est pas exhaustive et vous pouvez spécifier n’importe quel nom de propriété CSS3 prise en charge dans ce champ.
1. Dans le champ adjacent, spécifiez une valeur valide pour la propriété CSS3 spécifiée. Par exemple,**noir 3px**.
1. Cliquez sur **Ajouter un élément** pour définir une autre propriété et sa valeur.
1. Cliquez sur **Aperçu** pour prévisualiser les modifications dans le formulaire.
1. Cliquez sur **OK** pour confirmer les modifications ou **Annuler **pour quitter la boîte de dialogue sans aucune modification.
