---
title: Créer un modèle de formulaire adaptatif personnalisé
seo-title: Creating a custom adaptive form template
description: Cet article décrit comment créer des modèles de formulaires adaptatifs personnalisés.
seo-description: This article describes how to create custom adaptive form templates.
uuid: 8f8c770f-984c-48e8-978c-7cdfcd1af95b
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: customization
discoiquuid: c6115b64-e06f-4b5e-b7f9-876553c7627f
exl-id: 83f978ca-d451-4d27-820f-3620331285cf
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1181'
ht-degree: 60%

---

# Créer un modèle de formulaire adaptatif personnalisé {#creating-a-custom-adaptive-form-template}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

## Prérequis {#prerequisites}

* Compréhension du [modèle de page](/help/sites-authoring/templates.md) d’AEM et de la [création de formulaires adaptatifs](https://helpx.adobe.com/fr/aem-forms/6-1/introduction-forms-authoring.html)

* Compréhension des AEM [Bibliothèques côté client](/help/sites-developing/clientlibs.md)

## Modèle de formulaire adaptatif {#adaptive-form-template}

Un modèle de formulaire adaptatif est un modèle de page AEM spécialisé, avec certaines propriétés et une structure de contenu utilisées pour créer le formulaire adaptatif. Le modèle dispose de mises en page, de styles et d’une structure de contenu initiale de base préconfigurés.

Une fois un formulaire créé, les modifications apportées à la structure de contenu du modèle d’origine ne sont pas prises en compte dans le formulaire.

## Modèles de formulaires adaptatifs par défaut {#default-adaptive-form-templates}

AEM QuickStart fournit les modèles de formulaires adaptatifs suivants :

* De base : Permet de créer un formulaire adaptatif à plusieurs onglets à l’aide d’une disposition d’onglets sur la gauche, dans laquelle vous pouvez consulter les onglets de manière aléatoire.
* De base avec Acrobat Sign : Permet de créer un formulaire avec plusieurs onglets et un assistant. Il utilise une disposition d’onglets sur la gauche qui vous permet de consulter les onglets dans n’importe quel ordre. Il utilise les services d’Adobe Document Cloud eSign pour la signature et la vérification. 
* Modèle vierge : Permet de créer un formulaire sans en-tête, pied de page ni contenu initial. Vous pouvez ajouter des composants tels que des zones de texte, des boutons et des images. Le modèle vierge permet de créer un formulaire que vous pouvez [incorporer dans des pages du site AEM](/help/forms/using/embed-adaptive-form-aem-sites.md).

Ces modèles possèdent la propriété `sling:resourceType` définie sur le composant de page correspondant. Le composant de page effectue le rendu de la page CQ, contenant le conteneur de formulaires adaptatifs, qui à son tour effectue le rendu du formulaire adaptatif.

Le tableau suivant énumère l’association entre les modèles et le composant de page :

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Modèle</strong></p> </td> 
   <td><p><strong>Composant de page </strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>/libs/fd/af/templates/surveyTemplate</p> </td> 
   <td><p>/libs/fd/af/components/page/survey</p> </td> 
  </tr> 
  <tr> 
   <td><p>/libs/fd/af/templates/simpleEnrollmentTemplate</p> </td> 
   <td><p>/libs/fd/af/components/page/base</p> </td> 
  </tr> 
  <tr> 
   <td><p>/libs/fd/af/templates/tabbedEnrollmentTemplate</p> </td> 
   <td><p>/libs/fd/af/components/page/tabbedenrollment</p> </td> 
  </tr> 
  <tr> 
   <td><p>/libs/fd/afaddon/templates/advancedEnrollmentTemplate</p> </td> 
   <td><p>/libs/fd/afaddon/components/page/advancedenrollment</p> </td> 
  </tr> 
 </tbody> 
</table>

## Création d’un modèle de formulaire adaptatif à l’aide de l’éditeur de modèles {#creating-an-adaptive-form-template-using-template-editor}

Vous pouvez spécifier la structure et le contenu initial d’un formulaire adaptatif à l’aide de l’éditeur de modèles. Par exemple, vous souhaitez que tous les auteurs de formulaires aient quelques zones de texte, boutons de navigation et un bouton d’envoi dans un formulaire d’inscription. Vous pouvez créer un modèle que les auteurs peuvent utiliser pour créer un formulaire compatible avec d’autres formulaires d’inscription. AEM Éditeur de modèles vous permet d’effectuer les opérations suivantes :

* Ajout de composants d’en-tête et de pied de page d’un formulaire dans le calque de structure
* Fournissez le contenu initial pour le formulaire.
* Spécifiez un thème.
* Spécifiez des actions telles que l’envoi, la réinitialisation et la navigation.

Pour plus d’informations, voir [Éditeur de modèle](/help/forms/using/template-editor.md).

## Création d’un modèle de formulaire adaptatif à partir de CRXDE {#creating-an-adaptive-form-template-from-crxde}

Au lieu d’utiliser les modèles disponibles, vous pouvez créer un modèle et l’utiliser pour créer des formulaires adaptatifs. Les modèles personnalisés sont basés sur divers composants de page qui référencent des conteneurs de formulaire adaptatif et des éléments de page, tels que l’en-tête et le pied de page.

Vous pouvez créer ces composants à l’aide du composant de page base de votre site Web. Vous pouvez également étendre le composant de page du formulaire adaptatif que les modèles prêts à l’emploi utilisent.

Pour créer un modèle personnalisé comme simpleEnrollmentTemplate, suivez la procédure ci-après.

1. Accédez à CRXDE Lite sur votre instance de création.

1. Sous le répertoire /apps , créez la structure de dossiers de votre application. Par exemple, si le nom de l’application est mycompany, créez un dossier portant ce nom. En règle générale, le dossier de l’application contient des répertoires de composants, de configuration, de modèles, src et d’installation. Dans le cadre de cet exemple, créez les dossiers de composants, de configuration et de modèles.

1. Accédez au dossier /libs/fd/af/templates.
1. Copiez le nœud `simpleEnrollmentTemplate`.
1. Accédez au dossier /apps/mycompany/templates. Cliquez avec le bouton droit dessus et sélectionnez **[!UICONTROL Coller]**.
1. Si nécessaire, renommez le noeud de modèle que vous avez copié. Renommez-le par exemple en tant qu’enrollment-template.

1. Accédez à l’emplacement /apps/mycompany/templates/enrollment-template.

1. Modifiez les propriétés `jcr:title` et `jcr:description` du nœud `jcr:content` pour différencier le modèle de celui que vous avez copié.

1. Le nœud `jcr:content` du modèle modifié contient les composants `guideContainer` et `guideformtitle`. Le composant `guideContainer` est le conteneur qui contient le formulaire adaptatif. Le composant `guideformtitle` affiche le nom, la description et d’autres informations sur l’application.

   A la place du composant `guideformtitle`, vous pouvez inclure un composant personnalisé ou le composant `parsys`. Par exemple, supprimez le composant `guideformtitle` et ajoutez un composant personnalisé ou le nœud de composant `parsys`. Vérifiez que la propriété `sling:resourceType` du composant référence ce dernier et que la même propriété est définie dans le fichier `component.jsp` de la page.

1. Accédez à l’emplacement /apps/mycompany/templates/enrollment-template/jcr:content.

1. Ouvrez l’onglet **[!UICONTROL Properties]** (Propriétés) et modifier la valeur de la propriété `cq:designPath` en /etc/designs/mycompany.

1. Créez maintenant un nœud /etc/designs/mycompany pour le `cq:Page`type 

## Création d’un composant de page de formulaire adaptatif {#create-an-adaptive-form-page-component}

Le modèle personnalisé présente le même style que le modèle par défaut, car il fait référence au composant de page /libs/fd/af/components/page/base. Vous pouvez trouver la référence au composant en tant que propriété `sling:resourceType` définie sur le nœud /apps/mycompany/templates/enrollment-template/jcr:content. Dans la mesure où base est un composant de produit principal, ne le modifiez pas.

1. Accédez au nœud /apps/mycompany/templates/enrollment-template/jcr:content et modifiez la valeur de la propriété `sling:resourceType` en /apps/mycompany/components/page/enrollmentpage
1. Copiez le nœud /libs/fd/af/components/page/base dans le dossier /apps/mycompany/components/page.

1. Renommez le composant copié en `enrollmentpage`.

1. **(Uniquement si vous disposez déjà d’une contentpage)** Exécutez les étapes suivantes (a-d), si vous disposez d’un composant `contentpage` existant pour le site web. Si vous ne disposez pas d’un composant `contentpage` existant pour le site web, vous pouvez laisser la propriété `resourceSuperType` pour qu’elle indique la page de base d’OOTB.

   1. Pour le nœud `enrollmentpage`, définissez la valeur de la propriété `sling:resourceSuperType` sur mycompany/components/page/contentpage. Le composant `contentpage` est le composant de page base de votre site. D’autres composants de page peuvent l’étendre. Supprimez les fichiers de script sous `enrollmentpage`, à l’exception de `head.jsp`, `content.jsp` et `library.jsp`. Le composant `sling:resourceSuperType`, qui correspond à `contentpage` dans le cas présent, comprend tous ces scripts. Les en-têtes, dont la barre de navigation et le pied de page, sont hérités du composant `contentpage`

   1. Ouvrez le fichier `head.jsp`.

      Le fichier JSP contient la ligne `<cq.include script="library.jsp"/>`.

      Le fichier `library.jsp` contient la bibliothèque cliente `guide.theme.simpleEnrollment`, qui comporte les styles du formulaire adaptatif.

      Le composant de page `enrollmentpage` possède un fichier `head.jsp` exclusif qui remplace le fichier `head.jsp` du composant `contentpage`.

   1. Incluez tous les scripts du fichier `head.jsp` du composant `contentpage` dans le fichier `head.jsp` du composant `enrollmentpage`.
   1. Dans le script `content.jsp`, vous pouvez ajouter du contenu de page ou des références supplémentaires à d’autres composants inclus lors du rendu de la page. Par exemple, si vous ajoutez l’`applicationformheader` du composant personnalisé, veillez à ajouter la référence suivante au composant dans le fichier JSP :

      `<cq:include path="applicationformheader" resourceType="mycompany/components/applicationformheader"/>`

      De même, si vous ajoutez un composant `parsys` à la structure du nœud de modèle, incluez également le composant personnalisé.

## Création d’une bibliothèque cliente de formulaire adaptatif {#creating-an-adaptive-form-client-library}

Le fichier `head.jsp` du composant `enrollmentpage` pour le nouveau modèle contient une bibliothèque cliente `guide.theme.simpleEnrollment`. Le modèle par défaut utilise également cette bibliothèque cliente. Modifiez le style du nouveau modèle à l’aide de l’une de ces méthodes :

* Définissez un thème personnalisé et remplacez le thème par défaut `guide.theme.simpleEnrollment` par celui-ci.
* Définissez une nouvelle bibliothèque cliente sous /etc/designs/mycompany. Insérez la bibliothèque cliente après l’entrée de thème par défaut dans la page jsp. Incluez tous les styles remplacés et les autres fichiers JavaScript dans cette bibliothèque cliente.

>[!NOTE]
>
>Un thème désigne une bibliothèque cliente incluse dans le composant de page utilisé pour effectuer le rendu d’un formulaire adaptatif. La bibliothèque cliente contrôle principalement l’aspect d’un formulaire adaptatif.
