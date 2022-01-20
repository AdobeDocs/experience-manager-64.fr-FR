---
title: Création d’une racine de langue à l’aide de l’interface utilisateur classique
seo-title: Creating a Language Root Using the Classic UI
description: Découvrez comment créer une racine de langue à l’aide de l’interface utilisateur classique.
seo-description: Learn how to create a language root using the Classic UI.
uuid: d44a51a0-1507-4838-851c-cacff48ad825
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: site-features
content-type: reference
discoiquuid: 237b8cc6-158e-4c51-970d-4c9cc74f6496
feature: Language Copy
exl-id: 316903a8-22cf-45e6-a9f3-ac1d75beddec
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 79%

---

# Création d’une racine de langue à l’aide de l’interface utilisateur classique{#creating-a-language-root-using-the-classic-ui}

La procédure ci-dessous utilise l’interface utilisateur classique pour créer la racine de langue d’un site. Pour plus d’informations, voir [Création d’une racine de langue](/help/sites-administering/tc-prep.md#creating-a-language-root).

1. Dans la console Sites web, dans l’arborescence des sites web, sélectionnez la page racine du site. ([http://localhost:4502/siteadmin#](http://localhost:4502/siteadmin#))
1. Ajoutez une nouvelle page enfant représentant la version de langue du site :

   1. Sélectionnez Nouveau > Nouvelle page.
   1. Dans la boîte de dialogue, spécifiez le titre et le nom. Le nom doit être au format de `<language-code>` ou `<language-code>_<country-code>`, par exemple en, en_US, en_us, en_GB, en_gb.

      * Le code langue pris en charge est un code à deux lettres en minuscules, défini par la norme ISO-639-1.
      * Le code pays pris en charge est un code à deux lettres en minuscules ou en majuscules, défini par la norme ISO-3166.
   1. Sélectionnez le modèle et cliquez sur Créer.

   ![newpagefr](assets/newpagefr.png)

1. Dans la console Sites web, dans l’arborescence des sites web, sélectionnez la page racine du site.
1. Dans le menu Outils, sélectionnez Copie de la langue.

   ![toolslanguagecopy](assets/toolslanguagecopy.png)

   La boîte de dialogue Copie de la langue affiche un tableau des versions linguistiques et des pages web disponibles. Une croix, « x », dans une colonne de langue signifie que la page est disponible dans cette langue.

   ![languagecopydialog](assets/languagecopydialog.png)

1. Pour copier une page existante ou une arborescence de pages d’une version de langue, sélectionnez la cellule de la page en question dans la colonne de langue. Cliquez sur la flèche et sélectionnez le type de copie à créer.

   Dans l’exemple ci-dessous, la page équipement/lunettes/irian est copiée dans la version de langue française.

   ![languagecopydilogdropdown](assets/languagecopydilogdropdown.png)

   | Type de copie de langue | Description |
   |---|---|
   | auto | Utilise le comportement des pages parentes |
   | ignore | Ne crée pas de copie de cette page et de ses enfants |
   | `<language>+` (Français+, par exemple) | Copie la page et tous ses enfants de cette langue |
   | `<language>` (Français, par exemple) | Copie uniquement la page à partir de cette langue |

1. Cliquez sur OK pour fermer la boîte de dialogue.
1. Dans la boîte de dialogue suivante, cliquez sur Oui pour confirmer la copie.
