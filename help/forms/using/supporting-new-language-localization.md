---
title: Support de nouveaux paramètres régionaux pour la localisation de formulaires adaptatifs
seo-title: Support de nouveaux paramètres régionaux pour la localisation de formulaires adaptatifs
description: AEM Forms vous permet d’ajouter de nouveaux paramètres régionaux pour localiser les formulaires adaptatifs. Les paramètres régionaux offertes sont par défaut l’anglais, le français, l’allemand et le japonais.
seo-description: AEM Forms vous permet d’ajouter de nouveaux paramètres régionaux pour localiser les formulaires adaptatifs. Les paramètres régionaux offertes sont par défaut l’anglais, le français, l’allemand et le japonais.
uuid: d4cee51b-c555-4544-9ae9-4aa8d38b2b17
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: Configuration
discoiquuid: e78f539a-109c-444c-8e52-be2260c3509f
translation-type: tm+mt
source-git-commit: c5a78d6c2b8a55cad6266e86e9b990cafc038431
workflow-type: tm+mt
source-wordcount: '721'
ht-degree: 62%

---


# Support de nouveaux paramètres régionaux pour la localisation de formulaires adaptatifs  {#supporting-new-locales-for-adaptive-forms-localization}

## A propos des dictionnaires de paramètres régionaux{#about-locale-dictionaries} 

La localisation des formulaires adaptatifs repose sur deux types de dictionnaires de paramètres régionaux : 

**Dictionnaire spécifique au formulaireContient** des chaînes utilisées dans les formulaires adaptatifs. Par exemple, étiquettes, noms de champs, messages d’erreur, descriptions d’aide, et ainsi de suite. Il est géré sous la forme d’un ensemble de fichiers XLIFF pour chaque paramètre régional et vous pouvez y accéder à l’adresse https://`<host>`:`<port>`/libs/cq/i18n/translator.html.

**** dictionnaires globauxIl existe deux dictionnaires globaux, gérés en tant qu’objets JSON, dans AEM bibliothèque cliente. Ces dictionnaires contiennent les messages d’erreur par défaut, les noms des mois, les symboles de devise, les modèles de date et d’heure, et ainsi de suite. Vous pouvez trouver ces dictionnaires dans CRXDe Lite à l’adresse /libs/fd/xfaforms/clientlibs/I18N. Ces emplacements contiennent des dossiers distincts pour chaque jeu de paramètres régionaux. Étant donné que les dictionnaires globaux ne sont généralement pas mis à jour fréquemment, conserver des fichiers JavaScript distincts pour chaque jeu de paramètres régionaux permet aux navigateurs de les mettre en cache et de réduire l’utilisation de la bande passante du réseau lors de l’accès à différents formulaires adaptatifs sur le même serveur. 

### Comment fonctionne la localisation des formulaires adaptatifs{#how-localization-of-adaptive-form-works} 

Lorsqu’un formulaire adaptatif est rendu, il identifie les paramètres régionaux requis en examinant les paramètres suivants dans l’ordre spécifié : 

* Paramètre de requête `afAcceptLang`

   Pour remplacer les paramètres régionaux du navigateur des utilisateurs, vous pouvez transmettre le paramètre de requête `afAcceptLang` pour forcer les paramètres régionaux. Par exemple, l’URL suivante force le rendu du formulaire dans les paramètres régionaux japonais :

   `https://[*server*]:[*port*]/<*contextPath*>/<*formFolder*>/<*formName*>.html?wcmmode=disabled&afAcceptLang=ja`

* Paramètre régional du navigateur défini pour l’utilisateur, qui est spécifié dans la requête à l’aide de l’en-tête `Accept-Language`.

* Paramètre de langue de l’utilisateur spécifié dans AEM.  

Une fois que le paramètre régional est identifié, le formulaire adaptatif sélectionne le dictionnaire qui lui est spécifique. Si le dictionnaire spécifique aux formulaires correspondant au paramètre régional requis n’est pas trouvé, il utilise le dictionnaire anglais (en). 

S’il n’existe pas de bibliothèque client pour le paramètre régional requis, il recherche une bibliothèque client correspondant au code de langue présent dans le paramètre régional. Par exemple, si le paramètre régional requis est `en_ZA`  ( (anglais Afrique du sud) et qu’il n’existe pas de bibliothèque client correspondant à `en_ZA`, le formulaire adaptatif utilise la bibliothèque client correspondant à la langue `en` (anglais), si elle existe. Toutefois, si aucune de ces bibliothèques n’existe, le formulaire adaptatif utilise le dictionnaire correspondant au paramètre régional `en`.

## Ajoutez la localisation pour les paramètres régionaux non pris en charge{#add-localization-support-for-non-supported-locales} 

AEM Forms prend actuellement en charge la localisation du contenu des formulaires adaptatifs en anglais (en), espagnol (es), français (fr), italien (it), allemand (de), japonais (ja), portugais-brésilien (pt-BR, chinois- (zh-CN), chinois-Taïwan (zh-TW) et coréen (ko-KR).

Pour ajouter un nouveau paramètre régional lors de l’exécution des formulaires adaptatifs :

1. [Ajouter un paramètre régional au service GuideLocalizationService](/help/forms/using/supporting-new-language-localization.md#p-add-a-locale-to-the-guide-localization-service-br-p)

1. [Ajouter la bibliothèque XFA client pour un paramètre régional](/help/forms/using/supporting-new-language-localization.md#p-add-xfa-client-library-for-a-locale-br-p)

1. [Ajouter la bibliothèque cliente de formulaires adaptatifs pour un paramètre régional](/help/forms/using/supporting-new-language-localization.md#p-add-adaptive-form-client-library-for-a-locale-br-p)
1. [Ajouter un support pour la langue du dictionnaire](/help/forms/using/supporting-new-language-localization.md#p-add-locale-support-for-the-dictionary-br-p)
1. [Redémarrez le serveur](/help/forms/using/supporting-new-language-localization.md#p-restart-the-server-p)

### Ajouter un paramètre régional au service Guide Localisation {#add-a-locale-to-the-guide-localization-service-br}

1. Accédez à `https://[server]:[port]/system/console/configMgr`.
1. Cliquer pour modifier le composant **Guide Localization Service**.
1. Ajouter le paramètre régional que vous souhaitez à la liste des paramètres régionaux de supports

![GuideLocalizationSevice](assets/configservice.png)

### Ajouter la bibliothèque XFA client pour un paramètre régional {#add-xfa-client-library-for-a-locale-br}

Créez un noeud de type `cq:ClientLibraryFolder` sous `etc/<folderHierarchy>`, avec la catégorie `xfaforms.I18N.<locale>`, et ajoutez les fichiers suivants à la bibliothèque cliente :

* **I18N.** jsdéfinition  `xfalib.locale.Strings` pour la  `<locale>` fonction définie dans  `/etc/clientlibs/fd/xfaforms/I18N/ja/I18N`la.

* **js.txt** contenant les éléments suivants :

```
/libs/fd/xfaforms/clientlibs/I18N/Namespace.js
I18N.js
/etc/clientlibs/fd/xfaforms/I18N/LogMessages.js
```

### Ajouter la bibliothèque cliente de formulaires adaptatifs pour un paramètre régional {#add-adaptive-form-client-library-for-a-locale-br}

Créez un noeud de type `cq:ClientLibraryFolder` sous `etc/<folderHierarchy>`, avec la catégorie `guides.I18N.<locale>` et les dépendances `xfaforms.3rdparty`, `xfaforms.I18N.<locale>` et `guide.common`. &quot;

Ajouter les fichiers suivants à la bibliothèque client :

* **i18n.** jsdefinition  `guidelib.i18n`, ayant des modèles de &quot;calendarSymbols&quot;,  `datePatterns`,  `timePatterns`,  `dateTimeSymbols`,  `numberPatterns`,  `numberSymbols`, , , pour les selon les spécifications XFA décrites dans le  de spécification des ensembles de paramètres régionaux de l’.[`<locale>``currencySymbols``typefaces`](https://helpx.adobe.com/fr/content/dam/Adobe/specs/xfa_spec_3_3.pdf) Vous pouvez également voir comment il est défini pour les autres paramètres régionaux pris en charge dans `/etc/clientlibs/fd/af/I18N/fr/javascript/i18n.js`.

* **LogMessages.** jsdefinition  `guidelib.i18n.strings` et  `guidelib.i18n.LogMessages` pour la  `<locale>` fonction définie dans  `/etc/clientlibs/fd/af/I18N/fr/javascript/LogMessages.js`la.

* **js.txt** contenant les éléments suivants :

```
i18n.js
LogMessages.js
```

### Ajouter un support pour la langue du dictionnaire {#add-locale-support-for-the-dictionary-br}

Effectuez cette étape uniquement si le `<locale>` que vous ajoutez n&#39;est pas compris dans `en`, `de`, `es`, `fr`, `it`, `pt-br`, `zh-cn`, `zh-tw`, `ja`, `ko-kr`.

1. Créez un `nt:unstructured` noeud `languages` sous `etc`, s’il n’est pas déjà présent.

1. Ajoutez une propriété de chaîne à plusieurs valeurs `languages` au noeud, si elle n’est pas déjà présente.
1. Ajoutez les valeurs de paramètres régionaux par défaut `<locale>` `de`, `es`, `fr`, `it`, `pt-br`, `zh-cn`, `zh-tw`, `ja`, `ko-kr`, si elles ne sont pas déjà présentes.

1. Ajoutez `<locale>` sur les valeurs de la propriété `languages` de `/etc/languages`.

Le `<locale>` apparaît à `https://[server]:[port]/libs/cq/i18n/translator.html`.

### Redémarrez le serveur {#restart-the-server}

Redémarrez le serveur AEM pour que le paramètre régional ajouté entre en vigueur.

## Exemples de bibliothèques pour ajouter la prise en charge de l&#39;espagnol{#sample-libraries-for-adding-support-for-spanish} 

Exemples de bibliothèques clientes pour ajouter la prise en charge de l’espagnol

[Obtenir le fichier](assets/sample.zip)
