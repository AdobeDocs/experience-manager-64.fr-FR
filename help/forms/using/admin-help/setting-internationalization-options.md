---
title: Options de définition de l’internationalisation
seo-title: Setting internationalization options
description: Découvrez comment spécifier le paramètre régional utilisé pour le rendu des formulaires et spécifier le jeu de caractères utilisé pour encoder le flux de sortie.
seo-description: Learn how to specify the locale used to render forms and how to specify the character set used to encode the output stream.
uuid: bb77f5f3-634f-4285-9b10-c4dd40085e69
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: e845d13f-bef2-442d-af9a-4f92d7616a46
exl-id: 1fb51e4a-e0e8-4a58-8877-98337fe29fac
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 100%

---

# Options de définition de l’internationalisation{#setting-internationalization-options}

## Indication des paramètres régionaux utilisés pour effectuer le rendu du formulaire {#specify-the-locale-used-to-render-forms}

Vous pouvez préciser les paramètres régionaux utilisés au moment de effectuer le rendu du formulaire au format PDF. Les champs d’un formulaire au format PDF se servent des paramètres régionaux indiqués pour afficher les données. Par exemple, si les paramètres régionaux sont en allemand, le formulaire utilise les séparateurs décimaux allemands pour les valeurs numériques. Les paramètres régionaux servent également à envoyer des messages de validation vers les périphériques clients, tels que les navigateurs Web, dans le cadre des transformations HTML.

1. Dans Administration Console, cliquez sur Services > Forms.
1. Dans la liste de langues, dans l’onglet Internationalisation, sélectionnez les paramètres régionaux utilisés pour effectuer le rendu d’un formulaire. La valeur par défaut Anglais (Etats-Unis).
1. Cliquez sur Enregistrer.

## Définition du jeu de caractères utilisé pour encoder le flux de sortie {#specify-the-character-set-used-to-encode-the-output-stream}

1. Sous Internationalisation, dans la liste Jeu de caractères, sélectionnez un jeu de caractères. Ce paramètre dépend de l’API utilisée, à savoir renderHTMLForm ou renderPDFForm. Pour spécifier un jeu de caractères ne figurant pas dans la liste, sélectionnez Personnalisé et spécifiez la valeur d’encodage dans la zone qui s’affiche.

   Pour les transformations HTML, AEM forms prend en charge les valeurs d’encodage de caractères définies par le package `java.nio.charset` Si le paramètre sFormPreference prend la valeur PDFForm, seuls des jeux de caractères spécifiques sont pris en charge. Le nom du jeu de caractères doit être un nom canonique valide. La valeur par défaut est ISO-8859-1.

1. Cliquez sur Enregistrer.
