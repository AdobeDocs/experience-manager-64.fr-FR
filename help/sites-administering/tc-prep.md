---
title: Préparation du contenu à traduire
seo-title: Preparing Content for Translation
description: Découvrez comment préparer le contenu à traduire.
seo-description: Learn how to prepare content for translation.
uuid: 369630a8-2ed7-48db-973e-bd8213231d49
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: site-features
content-type: reference
discoiquuid: 8bd67d71-bcb7-4ca0-9751-3ff3ee054011
feature: Language Copy
exl-id: 1a7fe230-093b-4d2b-95cb-f9479c0febe5
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '717'
ht-degree: 74%

---

# Préparation du contenu à traduire{#preparing-content-for-translation}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Les sites web multilingues fournissent généralement une certaine quantité de contenu dans plusieurs langues. Le site est créé dans une langue, puis traduit dans d’autres langues. En règle générale, les sites multilingues se composent de branches de pages, où chaque branche contient les pages du site dans une langue différente.

L’exemple de site de démonstration de Geometrixx comprend plusieurs branches de langue et utilise la structure suivante :

```xml
/content
    |- geometrixx
             |- en
             |- fr
             |- de
             |- es
             |- it
             |- ja
             |- zh
```

Chaque branche de langue d’un site est appelée « copie de langue ». La page racine d’une copie de langue, appelée « racine de langue », identifie la langue du contenu de la copie de langue. Par exemple, `/content/geometrixx/fr` est la racine de langue de la copie en français. Les copies de langue doivent utiliser une [racine de langue configurée correctement](/help/sites-administering/tc-prep.md#creating-a-language-root) afin que la langue appropriée soit ciblée lorsque des sources sont traduites.

La copie de langue pour laquelle vous créez initialement le contenu du site est le gabarit de langue. Le gabarit de langue est la source qui est traduite dans d’autres langues.

Procédez comme suit pour préparer la traduction de votre site :

1. Créez la racine de langue de votre gabarit de langue. Par exemple, la racine de langue du site de démonstration Geometrixx en anglais est /content/geometrixx/en. Vérifiez que la racine de langue est configurée conformément aux informations de la section [Création d’une racine de langue](/help/sites-administering/tc-prep.md#creating-a-language-root).
1. Créez le contenu de votre gabarit de langue.
1. Créez la racine de langue de chaque copie de langue pour votre site. Par exemple, la copie en français de l’exemple de site de Geometrixx est /content/geometrixx/fr.

Après avoir préparé le contenu à traduire, vous pouvez créer automatiquement les pages manquantes dans les copies de langue et les projets de traduction associés. (Voir [Création d’un projet de traduction](/help/sites-administering/tc-manage.md).) Pour obtenir une présentation du processus de traduction de contenu dans AEM, consultez [Traduction de contenu pour des sites multilingues](/help/sites-administering/translation.md).

## Création d’une racine de langue {#creating-a-language-root}

Créez une racine de langue comme page racine d’une copie de langue qui identifie la langue du contenu. Après avoir créé la racine de langue, vous pouvez créer des projets de traduction qui incluent la copie de langue.

Pour créer la racine de langue, créez une page, puis utilisez le code de langue ISO comme valeur de la propriété Nom. Le code de la langue doit être dans l’un des formats suivants :

* `<language-code>`Le code de langue pris en charge est un code à deux lettres défini par la norme ISO-639-1, par exemple `en`.

* `<language-code>_<country-code>` ou `<language-code>-<country-code>`Le code pays pris en charge est un code à deux lettres, en minuscules ou en majuscules, défini par la norme ISO 3166. par exemple `en_US`, `en_us`, `en_GB`, `en-gb`.

Vous pouvez utiliser l’un de ces formats en fonction de la structure choisie pour votre site international. Par exemple, la propriété Nom de la page racine de la copie de langue française de l’exemple de site Geometrixx est définie sur `fr`. Notez que la propriété Nom est utilisée comme nom du nœud de page dans le référentiel et détermine donc le chemin d’accès à la page. (http://localhost:4502/content/geometrixx/fr.html)

La procédure ci-dessous utilise l’interface utilisateur optimisée pour les écrans tactiles pour créer une copie de langue d’un site web. Pour obtenir des instructions sur l’utilisation de l’interface utilisateur classique, voir [Création d’une racine de langue à l’aide de l’interface utilisateur classique](/help/sites-administering/tc-lroot-classic.md).

1. Accédez à Sites.
1. Cliquez ou appuyez sur le site pour lequel vous souhaitez créer une copie de langue.

   Par exemple, pour créer une copie de langue du site Geometrixx Outdoors, cliquez ou appuyez sur Site Geometrixx Outdoors.

1. Cliquez ou appuyez sur Créer, puis sur Créer une page.

   ![chlimage_1-21](assets/chlimage_1-21.png)

1. Sélectionnez le modèle de page, puis cliquez ou appuyez sur Suivant.
1. Dans le champ Nom, entrez le code de pays au format `<language-code>` ou `<language-code>_<country-code>`, par exemple `en`, `en_US`, `en_us`, `en_GB`, `en_gb`. Saisissez un titre pour la page.

   ![chlimage_1-22](assets/chlimage_1-22.png)

1. Cliquez ou appuyez sur Créer. Dans la boîte de dialogue de confirmation, cliquez ou appuyez sur **Terminé** pour revenir à la console Sites ou sur **Ouvrir** pour ouvrir la copie de langue.

## Affichage de le statut des racines de langue {#seeing-the-status-of-language-roots}

L’IU optimisée pour les écrans tactiles fournit un panneau Références qui affiche la liste des racines de langue qui ont été créées.

![chlimage_1-23](assets/chlimage_1-23.png)

La procédure ci-dessous utilise l’interface utilisateur optimisée pour les écrans tactiles afin d’afficher le panneau Références d’une page.

1. Dans la console Sites, sélectionnez une page du site, puis cliquez ou appuyez sur **Références**.

   ![chlimage_1-24](assets/chlimage_1-24.png)

1. Dans le panneau Références, cliquez ou appuyez sur **Copies de langue**. Le panneau Copies de langue affiche les copies de langue du site web.
