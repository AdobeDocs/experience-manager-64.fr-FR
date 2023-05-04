---
title: Créer un composant de champ d’IU Granite
seo-title: Creating a New Granite UI Field Component
description: L’interface utilisateur Granite fournit toute une gamme de composants conçus pour être utilisés dans les formulaires, appelés champs.
seo-description: Granite UI provides a range of components designed to be used in forms, called fields
uuid: cf26e057-4b0c-45f4-8975-2c658517f20e
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: platform
content-type: reference
discoiquuid: 94b9eeee-aae3-4b28-9d6f-1be0e4acd982
exl-id: 9a6cc25e-e54e-4b8a-8fdd-bcd65d8fe601
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '575'
ht-degree: 44%

---

# Créer un composant de champ d’IU Granite{#creating-a-new-granite-ui-field-component}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

L’IU Granite fournit toute une gamme de composants conçus pour être utilisés dans des formulaires. Ils sont appelés *champs* selon la terminologie de l’IU Granite. Les composants de formulaire Granite standard sont disponibles sous :

`/libs/granite/ui/components/foundation/form/*`

>[!NOTE]
>
>Ces champs de formulaire de l’IU Granite sont particulièrement intéressants, car ils sont utilisés pour [boîtes de dialogue de composant](/help/sites-developing/developing-components.md).

>[!NOTE]
>
>Pour plus d’informations sur les champs, reportez-vous à la section [Documentation de l’interface utilisateur Granite](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/granite-ui/api/index.html).

Utilisez la structure de base de l’IU Granite pour développer et/ou étendre les composants Granite. Celui-ci comporte deux éléments :

* côté serveur :

   * un ensemble de composants de base ;

      * foundation : modulaire, composable, lisible, réutilisable
      * Composants : composants Sling
   * aide au développement des applications


* côté client :

   * un ensemble de clientlibs fournissant un certain vocabulaire (c’est-à-dire une extension du langage de HTML) pour obtenir des modèles d’interaction génériques par le biais d’une interface utilisateur pilotée par Hypermedia.

Le composant d’IU Granite générique `field` se compose de deux fichiers d’intérêt :

* `init.jsp` : gère le traitement générique ; le balisage et la description, et fournit la valeur de formulaire dont vous aurez besoin lors du rendu du champ.
* `render.jsp` : il s’agit de l’emplacement où le rendu du champ est effectué, il doit être remplacé pour votre champ personnalisé ; il est inclus par `init.jsp`.

Reportez-vous à la section [Documentation de l’IU Granite - Champ](https://helpx.adobe.com/fr/experience-manager/6-4/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/components/foundation/form/field/index.html) si vous voulez plus de détails.

Pour consulter des exemples, voir :

* `cqgems/customizingfield/components/colorpicker`

   * fourni par l’[exemple de code](/help/sites-developing/developing-components-samples.md#code-sample-how-to-customize-dialog-fields)

* `granite/ui/components/foundation/form`

>[!NOTE]
>
>Ce mécanisme utilisant JSP, i18n et XSS ne sont pas fournis prêts à l’emploi. Cela signifie que vous devrez internationaliser et échapper vos chaînes. Le répertoire suivant contient les champs génériques d’une instance standard. Vous pouvez les utiliser comme référence :
>
>Référentiel `/libs/granite/ui/components/foundation/form`

## Création du script côté serveur pour le composant {#creating-the-server-side-script-for-the-component}

Le champ personnalisé doit remplacer uniquement le script `render.jsp`, où vous fournissez le balisage de votre composant. Vous pouvez considérer le JSP (c’est-à-dire le script de rendu) comme un wrapper pour votre balisage.

1. Créez un composant qui utilise la propriété `sling:resourceSuperType` à hériter de :

   `/libs/granite/ui/components/foundation/form/field`

1. Remplacez le script :

   `render.jsp`

   Dans ce script, vous devez générer le balisage hypermédia (c’est-à-dire enrichi, contenant l’abordage hypermédia) afin que le client sache interagir avec l’élément généré. Cela doit respecter le style de codage côté serveur de l’IU Granite.

   Lors de la personnalisation, vous *devez* avoir lu la valeur du formulaire (initialisée dans `init.jsp`) à partir de la requête à l’aide de :

   ```
   // Delivers the value of the field (read from the content)
   ValueMap vm = (ValueMap) request.getAttribute(Field.class.getName());
   vm.get("value, String.class"); 
   ```

   Pour plus d’informations, consultez la mise en œuvre des champs prêts à l’emploi de l’IU Granite, par exemple, `/libs/granite/ui/components/foundation/form/textfield`.

   >[!NOTE]
   >
   >Actuellement, JSP est la méthode de script préférée, car la transmission d’informations d’un composant à un autre (qui est assez fréquente dans le contexte de formulaire/champs) n’est pas facilement réalisée dans HTL.

## Création de la bibliothèque-client pour le composant {#creating-the-client-library-for-the-component}

Pour ajouter un comportement client spécifique à votre composant :

1. Créez une bibliothèque cliente de la catégorie `cq.authoring.dialog`.
1. Créez une bibliothèque cliente de la catégorie `cq.authoring.dialog` et définissez votre `CSS`/`JS` à l’intérieur de celle-ci.

   Définissez votre `CSS`/`JS` à l’intérieur de la bibliothèque cliente.

   >[!NOTE]
   >
   >Actuellement, l’interface utilisateur Granite ne fournit aucun écouteur ou crochets prêts à l’emploi que vous pouvez utiliser directement pour ajouter un comportement JS. Ainsi, pour ajouter un comportement JS supplémentaire à votre composant, vous devez implémenter un crochet JS à une classe personnalisée que vous affectez ensuite à votre composant pendant la génération du balisage.
