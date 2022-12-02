---
title: Texte d’espace réservé dans AEM Forms
seo-title: Placeholder text in AEM Forms
description: Le texte d’espace réservé est destiné à aider l’utilisateur à saisir des données lorsque la valeur de la commande est vide. Il peut s’agir d’un exemple de valeur ou une brève description du format attendu.
seo-description: Placeholder text is intended to aid the user with data entry when the control has no value. It could be a sample value or a brief description of the expected format.
uuid: 553ed988-ad2c-4bdb-bf1e-332e48cf7dfa
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: 2d7367fa-6cb8-40a1-8566-1fd0d46fdfde
feature: Adaptive Forms
exl-id: 26a1a5f7-b4d4-4f38-81a4-5f2d39702138
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '215'
ht-degree: 100%

---

# Texte d’espace réservé dans AEM Forms {#placeholder-text-in-aem-forms}

Le texte d’espace réservé représente un mot ou un groupe de mots court. Il est destiné à aider l’utilisateur à saisir des données lorsque la valeur de la commande est vide. Un texte d’espace réservé peut être un exemple de valeur ou une brève description du format attendu. Le texte d’espace réservé s’affiche avant que l’utilisateur ne saisisse une valeur et il est supprimé lorsque l’utilisateur saisit ou sélectionne une valeur.

>[!NOTE]
>
>Le texte d’espace réservé doit avoir, le cas échéant, une valeur qui ne contient aucun caractère de nouvelle ligne.

![Un composant de date avec et sans le texte d’espace réservé](assets/dat-picker-place-holder-text.png)

**A.** Composant de date avec le texte d’espace réservé **B.** Composant de date sans le texte d’espace réservé

AEM Forms prend en charge le texte d’espace réservé pour la zone Mot de passe, le sélecteur de date, la zone numérique et les champs de zone de texte.\
Les textes d’espace réservé ne sont pas pris en charge pour le widget natif de date en HTML5. Pour spécifier un texte d’espace réservé :

1. Effectuez un clic droit sur un composant prenant en charge le texte d’espace réservé et cliquez sur **Modifier**. La boîte de dialogue Modifier le composant apparaît.

1. Ouvrez l’onglet **Titre et texte.**
1. Indiquez un mot ou un groupe de mots court dans **la zone d’espace réservé**. Cliquez sur **OK**.

>[!NOTE]
>
>Le texte d’espace réservé n’est pas pris en charge sous Microsoft Internet Explorer 9.
