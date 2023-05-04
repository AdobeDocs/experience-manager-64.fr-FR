---
title: Configuration de l’éditeur de texte enrichi pour produire des sites accessibles
seo-title: Configuring RTE for Producing Accessible Sites
description: Découvrez comment configurer l’éditeur de texte enrichi AEM pour produire des sites accessibles.
seo-description: Learn how to configure the AEM Rich Text Editor to produce accessible sites.
uuid: 87539fee-3ecc-49f4-af3d-8dde72399c28
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
discoiquuid: ff0f006d-461c-4cc4-b6eb-d665f3f3b498
exl-id: 245e1c28-f702-4300-81cf-5139db9d95ec
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '954'
ht-degree: 50%

---

# Configuration de l’éditeur de texte enrichi pour produire des sites accessibles {#configuring-rte-for-producing-accessible-sites}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

AEM prend en charge les deux éléments suivants :

* fonctions d’accessibilité standard, y compris le texte de remplacement des images
* ainsi que d’autres fonctionnalités accessibles lors de la création de contenu avec des composants qui utilisent l’éditeur de texte enrichi (RTE).

>[!NOTE]
>
>* [Guide rapide relatif à WCAG 2.0](/help/managing/qg-wcag.md)
>* [Création de contenu accessible (conformité WCAG 2.0)](/help/sites-authoring/creating-accessible-content.md)


Les auteurs de contenu peuvent utiliser les fonctionnalités de l’éditeur de texte enrichi pour fournir des informations d’accessibilité lors de l’ajout de contenu à une page. Cela peut inclure l’ajout d’informations structurelles au moyen d’en-têtes et d’éléments de paragraphe.

Vous pouvez [configurer et personnaliser ces fonctionnalités en configurant les modules externes de l’éditeur de texte enrichi](#configuring-the-plugin-features) pour le composant. Par exemple, la variable `paraformat` vous permet d’ajouter des éléments sémantiques de niveau bloc supplémentaires, y compris d’étendre le nombre de niveaux d’en-tête pris en charge au-delà des niveaux de base. `H1`, `H2` et `H3` fourni par défaut.

L’éditeur de texte enrichi est disponible dans divers composants de l’interface utilisateur tactile et classique. Cependant, le composant Principal pour l’utilisation de l’éditeur de texte enrichi est le suivant : **Texte** composant.

Le **Texte** dans AEM est disponible pour les IU tactile et classique. Les illustrations suivantes montrent l’éditeur de texte enrichi avec un éventail de modules externes activés, y compris `paraformat`:

* Le **Texte** dans l’interface utilisateur tactile :

   ![Composant Texte (éditeur de texte enrichi) en mode plein écran dans l’IU optimisée pour les écrans tactiles](assets/chlimage_1-206.png)

* Le **Texte** dans l’IU classique :

   ![Boîte de dialogue Modifier (éditeur de texte enrichi) du composant Texte dans l’IU classique](assets/chlimage_1-207.png)

>[!NOTE]
>
>Il existe des différences entre les fonctionnalités de l’éditeur de texte enrichi disponibles dans l’IU classique et l’IU tactile. Pour plus d’informations, voir
>
>* [Modules externes et leurs fonctionnalités](/help/sites-administering/rich-text-editor.md#aboutplugins)
>* [Modules externes et leurs fonctionnalités - IU tactile](/help/sites-administering/rich-text-editor.md#aboutplugins)
>


## Configuration des fonctionnalités du module externe {#configuring-the-plugin-features}

Vous trouverez des instructions complètes sur la configuration de l’éditeur de texte enrichi sur la page [Configuration de l’éditeur de texte enrichi](/help/sites-administering/rich-text-editor.md) page. Celle-ci couvre tous les problèmes, y compris les principales étapes :

* [Modules externes et leurs fonctionnalités](/help/sites-administering/rich-text-editor.md#aboutplugins)
* [Emplacements de configuration](/help/sites-administering/rich-text-editor.md#understand-the-configuration-paths-and-locations)
* [Activation d’un module externe et configuration de la propriété features](/help/sites-administering/rich-text-editor.md#enable-rte-functionalities-by-activating-plug-ins)
* [Configuration d’autres fonctionnalités de l’éditeur de texte enrichi](/help/sites-administering/rich-text-editor.md#enable-rte-functionalities-by-activating-plug-ins)

En configurant un module externe dans le `rtePlugins` sous-branche dans CRXDE Lite (voir l’image suivante), vous pouvez activer toutes les fonctionnalités de ce module ou certaines fonctionnalités spécifiques.

![CRXDE Lite présentant un exemple de rtePlugin](assets/chlimage_1-208.png)

### Exemple - Spécification des formats de paragraphe disponibles dans le champ de sélection de l’éditeur de texte enrichi {#example-specifying-paragraph-formats-available-in-rte-selection-field}

De nouveaux formats de bloc sémantique peuvent être mis à disposition pour sélection par :

1. Selon votre éditeur de texte enrichi, déterminez son [emplacement de configuration](/help/sites-administering/rich-text-editor.md#understand-the-configuration-paths-and-locations) et accédez-y.
1. [Activation du champ de sélection Paragraphes](/help/sites-administering/rich-text-editor.md); par [activation du module externe](/help/sites-administering/rich-text-editor.md#enable-rte-functionalities-by-activating-plug-ins).
1. [Spécifiez les formats qui doivent être disponibles dans le champ de sélection Paragraphes .](/help/sites-administering/rich-text-editor.md).
1. Les formats de paragraphe sont ensuite à la disposition de l’auteur du contenu des champs de sélection dans l’éditeur de texte enrichi. Ils sont accessibles :

   * Utilisation du paragraphe ([pilcrow](https://en.wikipedia.org/wiki/Pilcrow)) dans l’IU tactile :

   ![Icône de paragraphe (pied-de-mouche).](do-not-localize/chlimage_1-7.png)

   * En utilisant la variable **Format** (sélecteur de liste déroulante) dans l’IU classique.


Avec les éléments structurels disponibles dans l’éditeur de texte enrichi via les options de format de paragraphe, AEM constitue une bonne base pour le développement de contenu accessible. Les auteurs de contenu ne peuvent pas utiliser l’éditeur de texte enrichi pour formater la taille de la police ou les couleurs ou d’autres attributs associés, ce qui empêche toute création de formatage en ligne. À la place, ils doivent sélectionner les éléments structurels appropriés comme les en-têtes et utiliser des styles globaux choisis via l’option Styles. Cela garantit un balisage propre, de plus grandes options pour les utilisateurs qui naviguent avec leurs propres feuilles de style et du contenu correctement structuré.

## Utilisation de l’option Modification de la source  {#use-of-the-source-edit-feature}

Dans certains cas, les auteurs de contenu constateront qu’il est nécessaire d’examiner et d’ajuster le code source HTML créé à l’aide de l’éditeur de texte enrichi. Par exemple, un élément de contenu créé dans l’éditeur de texte enrichi peut nécessiter une mise en forme supplémentaire pour être conforme à la norme WCAG 2.0. Ceci peut s’effectuer avec l’option [Modification de la source](/help/sites-administering/rich-text-editor.md#aboutplugins) de l’éditeur de texte enrichi. Vous pouvez spécifier la [ fonctionnalité `sourceedit` dans le plugin `misctools`](/help/sites-administering/rich-text-editor.md#aboutplugins).

>[!CAUTION]
>
>Utilisez la fonction `sourceedit` avec prudence. Les fautes de frappe et/ou les fonctions non prises en charge peuvent entraîner d’autres problèmes.

## Ajout de la prise en charge d’éléments et d’attributs de HTML supplémentaires {#adding-support-for-additional-html-elements-and-attributes}

Pour étendre davantage les fonctions d’accessibilité d’AEM, vous pouvez étendre les composants existants (par exemple, les composants **Texte** et **Tableau**) en fonction de l’éditeur de texte enrichi avec des éléments et attributs supplémentaires.

La procédure suivante explique comment étendre le composant **Tableau** avec un élément **Légende** qui fournit des informations sur un tableau de données aux utilisateurs de la technologie d’assistance :

### Exemple - Ajout de la légende à la boîte de dialogue Propriétés du tableau {#example-adding-the-caption-to-the-table-properties-dialog}

Dans le constructeur de l’élément `TablePropertiesDialog`, ajoutez un champ de saisie de texte supplémentaire utilisé pour modifier la légende. Notez que `itemId` doit être défini sur `caption` (à savoir le nom de l’attribut DOM) pour traiter automatiquement son contenu.

Dans **Tableau** vous devez définir ou supprimer explicitement l’attribut vers/depuis l’élément DOM. La valeur est transmise par la boîte de dialogue dans l’objet `config`. Notez que les attributs DOM doivent être définis ou supprimés à l’aide des méthodes `CQ.form.rte.Common` correspondantes (`com` est un raccourci de `CQ.form.rte.Common`) pour éviter les pièges courants des mises en œuvre de navigateur.

>[!NOTE]
>
>Cette procédure ne convient qu’à l’IU classique.

### Instructions étape par étape {#step-by-step-instructions}

1. Démarrez CRXDE Lite. Par exemple : [http://localhost:4502/crx/de/](http://localhost:4502/crx/de/)
1. Copier :

   `/libs/cq/ui/widgets/source/widgets/form/rte/commands/Table.js`

   vers :

   `/apps/cq/ui/widgets/source/widgets/form/rte/commands/Table.js`

   >[!NOTE]
   >
   >Vous devrez peut-être créer des dossiers intermédiaires si ceux-ci n’existent pas déjà.

1. Copier :

   `/libs/cq/ui/widgets/source/widgets/form/rte/plugins/TablePropertiesDialog.js`

   vers :

   `/apps/cq/ui/widgets/source/widgets/form/rte/plugins/TablePropertiesDialog.js`.

1. Ouvrez le fichier suivant pour le modifier (ouvrez-le en double-cliquant dessus) :

   `/apps/cq/ui/widgets/source/widgets/form/rte/plugins/TablePropertiesDialog.js`

1. Dans la méthode `constructor`, avant la lecture de ligne :

   ```
   var dialogRef = this;
   ```

   Ajoutez le code suivant :

   ```
   editItems.push({
       "itemId": "caption",
       "name": "caption",
       "xtype": "textfield",
       "fieldLabel": CQ.I18n.getMessage("Caption"),
       "value": (this.table && this.table.caption ? this.table.caption.textContent : "")
   });
   ```

1. Ouvrez le fichier suivant :

   `/apps/cq/ui/widgets/source/widgets/form/rte/commands/Table.js`.

1. Ajoutez le code suivant à la fin de la méthode `transferConfigToTable` :

   ```
   /**
    * Adds Caption Element
   */
   var captionElement;
   if (dom.firstChild && dom.firstChild.tagName.toLowerCase() == "caption")
   {
      captionElement = dom.firstChild;
   }
   if (config.caption)
   {
       var captionTextNode = document.createTextNode(config.caption)
       if (captionElement)
       {
          dom.replaceNode(captionElement.firstChild,captionTextNode);
       } else
       {
           captionElement = document.createElement("caption");
           captionElement.appendChild(captionTextNode);
           if (dom.childNodes.length>0)
           {
              dom.insertBefore(captionElement, dom.firstChild);
           } else
           {
              dom.appendChild(captionElement);
           }
       }
   } else if (captionElement)
   {
     dom.removeChild(captionElement);
   }
   ```

1. Enregistrez vos modifications à l’aide de **Enregistrer tout**

>[!NOTE]
>
>Le champ de texte brut n’est pas le seul type d’entrée autorisé pour la valeur de l’élément de légende. Tout widget ExtJS qui fournit la valeur de la légende via son `getValue()` , peut être utilisée.
>
>Pour ajouter des fonctionnalités de modification pour d’autres éléments et attributs, assurez-vous à la fois :
>
>* Que la propriété `itemId` de chaque champ correspondant est définie sur le nom de l’attribut DOM approprié (`TablePropertiesDialog`).
>* Que l’attribut est défini et/ou supprimé sur l’élément DOM de manière explicite (`Table`).

