---
title: Prise en charge de nouveaux paramètres régionaux pour la localisation de formulaires adaptatifs
seo-title: Supporting new locales for adaptive forms localization
description: AEM Forms vous permet d’ajouter de nouveaux paramètres régionaux pour localiser les formulaires adaptatifs. Les paramètres régionaux pris en charge par défaut sont l’anglais, le français, l’allemand et le japonais.
seo-description: AEM Forms allows you to add new locales for localizing adaptive forms. The supported locales by default are English, French, German, and Japanese.
uuid: d4cee51b-c555-4544-9ae9-4aa8d38b2b17
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: Configuration
discoiquuid: e78f539a-109c-444c-8e52-be2260c3509f
feature: Adaptive Forms
role: Admin
exl-id: 9f0e7284-ac11-406d-8d8c-7682f1d66fff
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '727'
ht-degree: 71%

---

# Prise en charge de nouveaux paramètres régionaux pour la localisation de formulaires adaptatifs {#supporting-new-locales-for-adaptive-forms-localization}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

## À propos des dictionnaires de paramètres régionaux {#about-locale-dictionaries}

La localisation des formulaires adaptatifs repose sur deux types de dictionnaires de paramètres régionaux : 

**Dictionnaire spécifique au formulaire** : il contient des chaînes utilisées dans des formulaires adaptatifs. Par exemple, étiquettes, noms de champs, messages d’erreur, descriptions d’aide, etc. Il est géré sous la forme d’un ensemble de fichiers XLIFF pour chaque paramètre régional et vous pouvez y accéder à l’adresse https://`<host>`:`<port>`/libs/cq/i18n/translator.html.

**Dictionnaires globaux** : la bibliothèque client AEM comporte deux dictionnaires globaux, gérés en tant qu’objets JSON. Ces dictionnaires contiennent les messages d’erreur par défaut, les noms des mois, les symboles de devise, les modèles de date et d’heure, etc. Vous pouvez trouver ces dictionnaires dans CRXDe Lite, à l’adresse /libs/fd/xfaforms/clientlibs/I18N. Ces emplacements contiennent des dossiers distincts pour chaque jeu de paramètres régionaux. Comme les dictionnaires globaux ne sont généralement pas mis à jour fréquemment, conserver des fichiers JavaScript distincts pour chaque paramètre régional permet aux navigateurs de les mettre en cache et de réduire l’utilisation de la bande passante du réseau lors de l’accès à différents formulaires adaptatifs sur le même serveur.

### Comment fonctionne la localisation des formulaires adaptatifs  {#how-localization-of-adaptive-form-works}

Lorsqu’un formulaire adaptatif est rendu, il identifie les paramètres régionaux requis en examinant les paramètres suivants dans l’ordre spécifié :

* Paramètre de requête `afAcceptLang`

   Pour remplacer les paramètres régionaux du navigateur des utilisateurs, vous pouvez transmettre la variable `afAcceptLang` paramètre de requête pour forcer le paramètre régional. Par exemple, l’URL ci-dessous force le rendu du formulaire dans les paramètres régionaux japonais :

   `https://[*server*]:[*port*]/<*contextPath*>/<*formFolder*>/<*formName*>.html?wcmmode=disabled&afAcceptLang=ja`

* La langue du navigateur défini pour l’utilisateur, qui est spécifiée dans la demande par le biais de l’en-tête `Accept-Language`.

* Paramètre de langue de l’utilisateur spécifié dans AEM.

Une fois que le paramètre régional est identifié, le formulaire adaptatif sélectionne le dictionnaire qui lui est spécifique. Si le dictionnaire spécifique au formulaire correspondant au paramètre régional requis est introuvable, il utilise le dictionnaire anglais (en).

S’il n’existe pas de bibliothèque client pour les paramètres régionaux nécessaires, il cherche une bibliothèque cliente correspondant au code de langue présent dans les paramètres régionaux. Par exemple, si le paramètre régional requis est `en_ZA` (anglais Afrique du sud) et qu’il n’existe pas de bibliothèque client correspondant à `en_ZA`, le formulaire adaptatif utilise la bibliothèque client correspondant à la langue `en` (anglais), si elle existe. Toutefois, si aucune de ces bibliothèques n’existe, le formulaire adaptatif utilise le dictionnaire correspondant au paramètre régional `en`.

## Ajoutez la localisation pour les paramètres régionaux non pris en charge {#add-localization-support-for-non-supported-locales}

AEM Forms prend actuellement en charge la localisation du contenu des formulaires adaptatifs en anglais (en), espagnol (es), français (fr), italien (it), allemand (de), japonais (ja), portugais-brésilien (pt-BR, chinois- (zh-CN), chinois-taïwanais (zh-TW) et coréen (ko-KR).

Pour ajouter un nouveau paramètre régional lors de l’exécution des formulaires adaptatifs :

1. [Ajouter des paramètres régionaux au service GuideLocalizationService](/help/forms/using/supporting-new-language-localization.md#p-add-a-locale-to-the-guide-localization-service-br-p)

1. [Ajouter une bibliothèque XFA cliente pour des paramètres régionaux](/help/forms/using/supporting-new-language-localization.md#p-add-xfa-client-library-for-a-locale-br-p)

1. [Ajouter la bibliothèque cliente de formulaires adaptatifs pour un paramètre régional](/help/forms/using/supporting-new-language-localization.md#p-add-adaptive-form-client-library-for-a-locale-br-p)
1. [Ajouter la prise en charge des paramètres régionaux pour la langue du dictionnaire](/help/forms/using/supporting-new-language-localization.md#p-add-locale-support-for-the-dictionary-br-p)
1. [Redémarrer le serveur](/help/forms/using/supporting-new-language-localization.md#p-restart-the-server-p)

### Ajouter des paramètres régionaux au Guide Localization Service {#add-a-locale-to-the-guide-localization-service-br}

1. Accédez à `https://[server]:[port]/system/console/configMgr`.
1. Cliquez pour modifier le **Guide Localization Service** composant.
1. Ajoutez les paramètres régionaux à ajouter à la liste des paramètres régionaux pris en charge.

![GuideLocalizationService](assets/configservice.png)

### Ajouter la bibliothèque XFA cliente pour des paramètres régionaux {#add-xfa-client-library-for-a-locale-br}

Créez un nœud de type `cq:ClientLibraryFolder` sous `etc/<folderHierarchy>`, avec la catégorie `xfaforms.I18N.<locale>` et ajoutez les fichiers ci-dessous à la bibliothèque cliente :

* **I18N.js** qui définit `xfalib.locale.Strings` pour `<locale>`, comme défini dans `/etc/clientlibs/fd/xfaforms/I18N/ja/I18N`.

* **js.txt** qui contient les éléments suivants :

```
/libs/fd/xfaforms/clientlibs/I18N/Namespace.js
I18N.js
/etc/clientlibs/fd/xfaforms/I18N/LogMessages.js
```

### Ajouter la bibliothèque cliente de formulaires adaptatifs pour un paramètre régional {#add-adaptive-form-client-library-for-a-locale-br}

Créez un nœud de type `cq:ClientLibraryFolder` sous `etc/<folderHierarchy>`, avec la catégorie `guides.I18N.<locale>` et les dépendances `xfaforms.3rdparty`, `xfaforms.I18N.<locale>` et `guide.common`.

Ajouter les fichiers suivants à la bibliothèque cliente :

* **i18n.js** qui définit `guidelib.i18n`, comportant des motifs « calendarSymbols », `datePatterns`, `timePatterns`, `dateTimeSymbols`, `numberPatterns`, `numberSymbols`, `currencySymbols`, `typefaces` pour `<locale>` conformément aux spécifications XFA décrites dans [Spécification du jeu de paramètres régionaux](https://helpx.adobe.com/content/dam/Adobe/specs/xfa_spec_3_3.pdf). Vous pouvez également voir comment les autres paramètres locaux sont définis sur `/etc/clientlibs/fd/af/I18N/fr/javascript/i18n.js`.

* **LogMessages.js** qui définit `guidelib.i18n.strings` et `guidelib.i18n.LogMessages` pour `<locale>`, défini dans `/etc/clientlibs/fd/af/I18N/fr/javascript/LogMessages.js`.

* **js.txt** qui contient les éléments suivants :

```
i18n.js
LogMessages.js
```

### Ajouter la prise en charge des paramètres régionaux pour la langue du dictionnaire {#add-locale-support-for-the-dictionary-br}

Exécutez cette étape uniquement si l’élément `<locale>` que vous ajoutez ne se trouve pas parmi `en`, `de`, `es`, `fr`, `it`, `pt-br`, `zh-cn`, `zh-tw`, `ja`, `ko-kr`.

1. Créez un nœud `nt:unstructured` `languages` sous `etc`, s’il n’existe pas déjà.

1. Ajoutez une propriété comprenant plusieurs valeurs `languages` au nœud, s’il ne sont pas déjà présents.
1. Ajoutez les valeurs des paramètres régionaux par défaut `<locale>` `de`, `es`, `fr`, `it`, `pt-br`, `zh-cn`, `zh-tw`, `ja`, `ko-kr`, si elles ne sont pas déjà présentes.

1. Ajoutez `<locale>` aux valeurs de la propriété `languages` de `/etc/languages`.

L’élément `<locale>` s’affiche au niveau de `https://[server]:[port]/libs/cq/i18n/translator.html`.

### Redémarrer le serveur {#restart-the-server}

Redémarrez le serveur AEM pour que les paramètres régionaux ajoutés entrent en vigueur.

## Exemples de bibliothèques pour ajouter la prise en charge de l’espagnol {#sample-libraries-for-adding-support-for-spanish}

Exemples de bibliothèques clientes pour ajouter la prise en charge de l’espagnol

[Obtenir le fichier](assets/sample.zip)
