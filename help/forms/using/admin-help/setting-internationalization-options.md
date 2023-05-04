---
title: Paramétrer les options d’internationalisation
seo-title: Setting internationalization options
description: Découvrez comment spécifier les paramètres régionaux utilisés pour le rendu des formulaires et comment spécifier le jeu de caractères utilisé pour encoder le flux de sortie.
seo-description: Learn how to specify the locale used to render forms and how to specify the character set used to encode the output stream.
uuid: bb77f5f3-634f-4285-9b10-c4dd40085e69
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: e845d13f-bef2-442d-af9a-4f92d7616a46
exl-id: 1fb51e4a-e0e8-4a58-8877-98337fe29fac
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '258'
ht-degree: 31%

---

# Paramétrer les options d’internationalisation{#setting-internationalization-options}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

## Spécification des paramètres régionaux utilisés pour le rendu des formulaires {#specify-the-locale-used-to-render-forms}

Vous pouvez spécifier les paramètres régionaux utilisés lors du rendu d’un formulaire de PDF. Les champs d’un formulaire de PDF utilisent les paramètres régionaux spécifiés pour afficher les données. Par exemple, si le paramètre régional est défini sur Allemand, le formulaire utilise des séparateurs décimaux allemands pour les valeurs numériques. Les paramètres régionaux sont également utilisés pour envoyer des messages de validation aux appareils clients, tels que les navigateurs web, dans le cadre de transformations de HTML.

1. Dans la console d’administration, cliquez sur Services > Forms.
1. Sous Internationalisation, dans la liste Langue, sélectionnez le paramètre régional utilisé pour générer un formulaire. La valeur par défaut est Anglais (Etats-Unis).
1. Cliquez sur Enregistrer.

## Définition du jeu de caractères utilisé pour encoder le flux de sortie {#specify-the-character-set-used-to-encode-the-output-stream}

1. Sous Internationalisation, dans la liste Jeu de caractères, sélectionnez un jeu de caractères. Ce paramètre dépend de l’API utilisée, renderHTMLForm ou renderPDFForm. Pour spécifier un jeu de caractères ne figurant pas dans la liste, sélectionnez Personnalisé et spécifiez la valeur d’encodage dans la zone qui s’affiche.

   Pour les transformations HTML, AEM forms prend en charge les valeurs d’encodage de caractères définies par le package `java.nio.charset` Si le paramètre sFormPreference prend la valeur PDFForm, seuls des jeux de caractères spécifiques sont pris en charge. Le jeu de caractères doit être un nom canonique valide. La valeur par défaut est ISO-8859-1.

1. Cliquez sur Enregistrer.
