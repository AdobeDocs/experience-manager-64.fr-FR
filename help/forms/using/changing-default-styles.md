---
title: Modifiier les styles par défaut des formulaires HTML5
seo-title: Changing default styles of HTML5 forms
description: Le style de HTML5 forms est basé sur CSS. Vous pouvez modifier les styles par défaut du formulaire.
seo-description: HTML5 forms styling is based on CSS. You can change the default styles of the form.
uuid: dab888b1-d1a9-4990-ab21-96570beafd26
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: a9ab5a78-2add-46e1-a8f2-444d0f25f43a
feature: Mobile Forms
exl-id: 74e54d96-e418-40aa-9b93-561fbdd6312d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '351'
ht-degree: 50%

---

# Modifiier les styles par défaut des formulaires HTML5 {#changing-default-styles-of-html-forms}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Les formulaires HTML5 sont rendu utilisant des fonctionnalités HTML5 et le style du formulaire rendu est fait utilisant CSS. L’apparence par défaut des formulaires HTML5 est similaire à son rendu PDF. Les développeurs peuvent utiliser une page CSS personnalisée pour modifier l’aspect par défaut des formulaires HTML5.

Cet article contient des informations détaillées sur la modification du style d’un formulaire HTML5 et l’article [Introduction aux styles](/help/forms/using/css-styles.md) contient des informations détaillées sur divers aspects de style de formulaires HTML5. Assurez-vous d’avoir lu l’article Introduction aux styles avant d’effectuer les étapes mentionnées dans cet article.

Les deux images qui suivent montrent la différence entre les styles par défaut et les styles personnalisés.

![pictures-002-small](assets/pictures-002-small.png)

## Donner du style à vos formulaires {#style-your-forms}

1. **Sélection d’un profil pour ajouter des styles personnalisés**

   Accédez à l’interface de CRX DE à lʼadresse suivante :**https://&lt;server>:&lt;port>/crx/de** et créez un profil ou sélectionnez un profil existant. Pour savoir comment créer un profil, consultez la section [Créer un profil](/help/forms/using/custom-profile.md).

1. **Création d’une feuille de style CSS pour le style des formulaires HTML5**

   Accédez au dossier dans lequel vous avez créé le rendu de profil et créez un fichier de feuille de style CSS. Les étapes à suivre sont les suivantes :

   1. Cliquez avec le bouton droit sur le dossier et sélectionnez **create** -> **créer un fichier** depuis le menu
   Pour savoir quelles classes CSS créer pour un composant particulier de vos formulaires HTML5, voir [Présentation des styles](/help/forms/using/css-styles.md).

1. **Inclure la feuille de style dans le rendu de profil**

   Ouvrez la page Rendu du profil (fichier jsp) dans CRX DE et insérez le fichier CSS dans la page juste en dessous de la bibliothèque cliente XFA. Effectuez les étapes suivantes pour inclure le fichier CSS dans le profil.

   1. Recherchez la ligne suivante dans la page du rendu :

      &lt;cq:includeClientLib categories=&quot;xfaforms.profile&quot; />

   1. Insérez les éléments suivants sous la ligne ci-dessus pour inclure la feuille de style :

      &lt;link href=&quot;/path/to/stylesheet&quot; rel=&quot;stylesheet&quot; type=&quot;text/css&quot;/>

   1. Enregistrez le fichier.
