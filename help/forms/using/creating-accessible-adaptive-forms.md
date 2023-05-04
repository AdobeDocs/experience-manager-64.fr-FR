---
title: Créer des formulaires adaptatifs accessibles
seo-title: Creating accessible adaptive forms
description: AEM Forms vous fournit des outils, ainsi que la création de formulaires adaptatifs accessibles, et vous aide à vous conformer aux normes d’accessibilité.
seo-description: AEM Forms provides you tools and to create accessible adaptive forms and helps comply with accessibility standards.
uuid: eceb3282-0b90-4e0a-8b89-137d27029747
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: 96d9ad52-074b-4084-b818-abce79282776
feature: Adaptive Forms
exl-id: adad26fa-b27a-4bd7-806c-4ddfbaae7a37
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '939'
ht-degree: 35%

---

# Créer des formulaires adaptatifs accessibles {#creating-accessible-adaptive-forms}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

## Présentation {#introduction}

Un formulaire accessible est un formulaire utilisable par tout le monde, y compris par les utilisateurs souffrant de handicaps. Adobe Experience Manager (AEM) comprend un certain nombre de fonctions et de fonctionnalités qui améliorent la convivialité des formulaires adaptatifs pour les utilisateurs avec des fonctionnalités différentes. Cette solution aide également les auteurs à créer des formulaires adaptatifs accessibles.

L’intégration de l’accessibilité dans les formulaires adaptatifs permet non seulement le plus large public possible de contenu, mais elle est également requise lors de la fourniture de documents dans des zones géographiques où la conformité aux normes d’accessibilité est obligatoire. AEM Forms aide les développeurs à se conformer à ces normes d’accessibilité.

Lors de la création d’un formulaire adaptatif, l’auteur doit tenir compte des points suivants pour créer un formulaire adaptatif accessible :

* Fournissez des libellés appropriés pour les commandes de formulaire
* Fournissez des équivalents textuels pour les images
* Fournissez un contraste des couleurs suffisant
* Assurez-vous que les commandes de formulaire sont accessibles au clavier

## Fournissez des libellés appropriés pour les commandes de formulaire {#provide-proper-labels-for-form-controls}

Le libellé ou le titre d’un composant de formulaire identifie ce qu’il représente. Par exemple, le texte &quot;Prénom&quot; indique aux utilisateurs qu’ils doivent saisir leur prénom dans un champ de texte. Pour être accessible par les lecteurs d’écran, le libellé est associé par programmation à un composant de formulaire. La commande de formulaire peut également être configurée avec des informations d’accessibilité supplémentaires.

Le libellé qui est perçu par les lecteurs d’écran ne doit pas nécessairement être le même que la légende visuelle. Dans certains cas, vous souhaiterez peut-être être plus précis sur l’objectif du contrôle. Pour chaque objet de champ d’un formulaire, les options d’accessibilité permettent de spécifier ce que le lecteur d’écran annonce pour identifier le champ de formulaire spécifique.

Pour utiliser l’option Accessibilité, procédez comme suit :

1. Sélectionnez un composant et appuyez sur ](assets/cmppr.png)cmppr![.
1. Cliquez sur **Accessibilité** dans la barre latérale pour sélectionner l’option d’accessibilité de votre choix.

### Options d’accessibilité dans des composants de formulaire {#accessibility-options-in-form-components}

![Options d’accessibilité dans des composants de formulaire](assets/accessibility-options.png)

**Texte personnalisé** : les auteurs de formulaires indiquent le contenu dans la zone de texte Personnalisé de l’option d’accessibilité. La technologie d’assistance, dont tirent parti les lecteurs d’écran, utilise ce texte personnalisé. L’utilisation du paramètre Titre est la meilleure option dans la plupart des scénarios. N’envisagez la création d’un texte de Reader d’écran personnalisé que lorsque l’utilisation du titre ou d’une brève description n’est pas possible.

**Description brève** : pour la majorité des composants, une description brève s’affiche lors de l’exécution lorsque l’utilisateur place le pointeur de la souris sur un composant. Vous pouvez définir cette option dans le champ approprié, sous l’option du contenu d’aide.

**Titre** : utilisez cette option pour permettre à AEM Forms d’utiliser le libellé visuel associé au champ de formulaire comme texte de lecteur d’écran.

**Nom** : vous pouvez définir une valeur dans le champ Nom de l’onglet Liaison. Le nom ne peut pas contenir d’espaces.

**Aucun** : lorsque vous sélectionnez Aucun, aucun nom n’est associé à l’objet de formulaire dans le formulaire publié. Aucun n’est pas un paramètre recommandé pour les commandes de formulaire.

>[!NOTE]
>
>Dans le cas de la case d’option et de la case à cocher, deux options seulement sont possibles dans le cadre de l’accessibilité à savoir : Texte personnalisé et Titre.

>[!NOTE]
>
>Pour les formulaires adaptatifs basés sur XFA, l’option d’accessibilité est héritée des options d’accessibilité définies dans le fichier XDP. Les info-bulles du fichier XDP sont mappées sur la description courte et la légende sur le titre. Les autres options fonctionnent normalement.

## Fournissez des équivalents textuels pour les images {#provide-text-equivalents-for-images}

Les images peuvent aider à améliorer la compréhension pour certains utilisateurs. Toutefois, pour les utilisateurs utilisant des lecteurs d’écran, les images réduisent l’accessibilité de votre formulaire. Si vous choisissez d’utiliser des images, fournissez des descriptions textuelles pour toutes les images.

Assurez-vous que le texte décrit l’objet et son objectif dans le formulaire. Un lecteur d’écran lit ce texte alternatif lorsqu’il rencontre une image. Un texte alternatif doit toujours être spécifié pour une image.

Sélectionnez un composant d’image et appuyez sur ![cmppr](assets/cmppr.png). Dans la barre latérale, sous Propriétés, indiquez le texte alternatif d’une image.

![Texte alternatif d’une image](assets/image-properties.png)

## Fournissez un contraste des couleurs suffisant {#provide-sufficient-color-contrast}

La conception de l’accessibilité implique la prise en compte d’instructions supplémentaires pour l’utilisation des couleurs. Les auteurs de formulaires peuvent utiliser des couleurs pour améliorer l’aspect des formulaires en mettant en surbrillance différents composants de formulaire. Cependant, une utilisation incorrecte des couleurs peut rendre un formulaire difficile ou impossible à lire pour les personnes ayant des capacités différentes.

Les utilisateurs ayant une déficience visuelle s’appuient sur le contraste prononcé entre le texte et l’arrière-plan pour lire du contenu numérique. En l’absence de contraste suffisant, la lecture d’un formulaire peut s’avérer difficile, voire impossible, pour certains utilisateurs.

Il est recommandé d’utiliser la police et les couleurs d’arrière-plan par défaut, c’est-à-dire le contenu en noir sur fond blanc. Si vous modifiez les couleurs par défaut, choisissez une couleur de premier plan foncée sur un arrière-plan clair, ou inversement.

Voir [Création de thèmes personnalisés pour les formulaires adaptatifs](/help/forms/using/creating-custom-adaptive-form-themes.md), pour plus d’informations sur la modification du contraste de couleur et du thème pour les formulaires adaptatifs.

## Assurez-vous que les commandes de formulaire sont accessibles au clavier {#ensure-that-form-controls-are-keyboard-accessible}

Un formulaire accessible peut être entièrement rempli à l’aide du clavier ou d’un appareil de saisie équivalent. Les utilisateurs ayant une mobilité réduite ou une déficience visuelle peuvent n’avoir d’autre choix que d’utiliser le clavier. De plus, de nombreux utilisateurs qui peuvent utiliser une souris préfèrent saisir leur clavier. En proposant les différentes méthodes de saisie, vous pouvez non seulement créer des formulaires accessibles, mais également des formulaires mieux adaptés aux préférences de tous les utilisateurs.

Les raccourcis clavier suivants sont disponibles dans AEM Forms.

| Action | Raccourci clavier |
|---|---|
| Déplacer le curseur vers l’avant dans un formulaire | Tabulation |
| Déplacer le curseur vers l’arrière dans un formulaire | Maj+Tabulation |
| Accéder au panneau suivant | Alt+Flèche Droite |
| Accéder au panneau précédent | Alt+Flèche Gauche |
| Réinitialiser les données renseignées dans un formulaire | Alt+R |
| Envoyer un formulaire | Alt+S | configuring-watched-folder-endpoints.md |
