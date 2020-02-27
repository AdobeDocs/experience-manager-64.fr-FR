---
title: Ajouter des bibliothèques clientes
seo-title: Ajouter des bibliothèques clientes
description: Ajout d’un dossier ClientLibrary
seo-description: Ajout d’un dossier ClientLibrary
uuid: cdc1d258-2011-4517-9206-dd2b5d1f7e0d
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: c84040b0-7850-4960-b676-ffa0a74c8cb2
translation-type: tm+mt
source-git-commit: 2d1e39120d79de029927011d48f7397b53ad91bc

---


# Ajouter des bibliothèques clientes {#add-clientlibs}

## Ajout d’un dossier ClientLibraryFolder (clientlibs) {#add-a-clientlibraryfolder-clientlibs}

Créez un dossier ClientLibraryFolder nommé `clientlibs`qui contiendra les fichiers JS et CSS utilisés pour rendre les pages de votre site.

La valeur de `categories`propriété donnée à cette bibliothèque cliente est l’identifiant utilisé pour inclure directement cette bibliothèque cliente à partir d’une page de contenu ou pour l’incorporer à d’autres bibliothèques clientes.

1. Using **[!UICONTROL CRXDE Lite]**, expand `/etc/designs`

1. Cliquez avec le bouton droit `an-scf-sandbox` et sélectionnez `Create Node`

   * Nom: `clientlibs`
   * Type: `cq:ClientLibraryFolder`

1. Cliquez sur **[!UICONTROL OK]**

![chlimage_1-220](assets/chlimage_1-220.png)

Dans l’onglet **[!UICONTROL Propriétés]** du nouveau `clientlibs` noeud, saisissez la **`categories`** propriété :

* Nom :**[!UICONTROL catégories]**
* Type : **[!UICONTROL Chaîne]**
* Valeur : **[!UICONTROL apps.an-scf-sandbox]**
* Cliquez sur **[!UICONTROL Ajouter]**
* Cliquez sur **[!UICONTROL Enregistrer tout]**

Remarque : la préface de la valeur de catégories avec &quot;apps&quot;. est une convention permettant d&#39;identifier l&#39;application propriétaire comme se trouvant dans le dossier /apps et non /libs.  IMPORTANT : Ajoutez un espace réservé `js.txt` et `css.txt` des fichiers. (Il ne s’agit pas officiellement d’un dossier cq:ClientLibraryFolder sans eux.)


1. Clic droit sur **`/etc/designs/an-scf-sandbox/clientlibs`**
1. Sélectionner **[!UICONTROL Créer un fichier...]**
1. Enter **[!UICONTROL Name]**: `css.txt`

1. Sélectionner **[!UICONTROL Créer un fichier...]**
1. Enter **[!UICONTROL Name]**: `js.txt`

1. Cliquez sur **[!UICONTROL Enregistrer tout]**

![chlimage_1-221](assets/chlimage_1-221.png)

La première ligne de css.txt et js.txt identifie l’emplacement de base à partir duquel les listes de fichiers suivantes doivent être trouvées.

Essayez de définir le contenu de css.txt sur :

```
#base=.
 style.css
```

Créez ensuite un fichier sous clientlibs nommé style.css, puis définissez le contenu sur :

`body {`

`background-color: #b0c4de;`

`}`

## Incorporer les bibliothèques clientes SCF {#embed-scf-clientlibs}

Dans l’onglet **[!UICONTROL Propriétés]** du `clientlibs` noeud, saisissez la propriété Chaîne à plusieurs valeurs **[!UICONTROL incorporée]**. Les bibliothèques côté [client (clientlibs) nécessaires seront ainsi intégrées aux composants](client-customize.md#clientlibs-for-scf)SCF. Pour ce tutoriel, nous ajouterons plusieurs clientlibs nécessaires aux composants Communautés.

**Notez** qu’il peut s’agir de l’approche souhaitée ou non pour un site de production, car il y a des considérations de commodité par rapport à la taille/vitesse des clients téléchargés pour chaque page.

Si vous utilisez une seule fonctionnalité sur une page, vous pouvez inclure directement la bibliothèque cliente complète de cette fonctionnalité sur la page, par exemple, &lt;% ui:includeClientLib categories=cq.social.hbs.forum&quot; %>

Dans ce cas, nous les incluons tous, et nous préférerions donc les clientlibs SCF les plus basiques qui sont les clientlibs d&#39;auteur :

* Nom: **`embed`**
* Type: **`String`**

* Cliquez sur **`Multi`**
* Valeur: **`cq.social.scf`**

   *&lt;enter> affiche une boîte de dialogue*

   *Cliquez sur **[+]**après chaque entrée pour ajouter les catégories clientlib suivantes :*

   * **`cq.ckeditor`**
   * **`cq.social.author.hbs.comments`**
   * **`cq.social.author.hbs.forum`**
   * **`cq.social.author.hbs.rating`**
   * **`cq.social.author.hbs.reviews`**
   * **`cq.social.author.hbs.voting`**
   * Cliquez sur **[!UICONTROL OK]**

* Cliquez sur **[!UICONTROL Enregistrer tout]**

![chlimage_1-222](assets/chlimage_1-222.png)

Voici comment `/etc/designs/an-scf-sandbox/clientlibs` apparaître dans le référentiel :

![chlimage_1-223](assets/chlimage_1-223.png)

## Inclure les bibliothèques clientes dans le modèle PlayPage {#include-clientlibs-in-playpage-template}

Sans inclure la catégorie `apps.an-scf-sandbox` ClientLibraryFolder sur la page, les composants SCF ne seront pas fonctionnels ni stylisés, car les scripts JavaScript et le ou les styles nécessaires ne seront pas disponibles.

Par exemple, sans inclure les clientlibs, le composant de commentaires SCF apparaît sans style :

![chlimage_1-224](assets/chlimage_1-224.png)

Une fois les clients apps.an-scf-sandbox inclus, le composant de commentaires SCF s’affiche avec le style suivant :

![chlimage_1-225](assets/chlimage_1-225.png)

L’instruction include appartient au <head><meta http-equiv="Content-Type" content="text/html; charset=UTF-8"> de la section <html> script. La valeur par défaut **`foundation head.jsp`** inclut un script qui peut être superposé : **`headlibs.jsp`**.

**Copiez headlibs.jsp et incluez clientlibs :**

1. Using **[!UICONTROL CRXDE Lite]**, select **`/libs/foundation/components/page/headlibs.jsp`**
1. Cliquez avec le bouton droit de la souris et sélectionnez **[!UICONTROL Copier]** (ou sélectionnez Copier dans la barre d’outils).
1. Sélectionner **`/apps/an-scf-sandbox/components/playpage`**
1. Cliquez avec le bouton droit et sélectionnez **[!UICONTROL Coller]** (ou choisissez Coller dans la barre d’outils).
1. Double-cliquez sur **`headlibs.jsp`** pour l’ouvrir.
1. Ajouter la ligne suivante à la fin du fichier

   **`<ui:includeClientLib categories="apps.an-scf-sandbox"/>`**

1. Cliquez sur **[!UICONTROL Enregistrer tout]**


```xml
<%@ page session="false" %><%
%><%@include file="/libs/foundation/global.jsp" %><%
%><ui:includeClientLib categories="cq.foundation-main"/><%
%>
<cq:include script="/libs/cq/cloudserviceconfigs/components/servicelibs/servicelibs.jsp"/>
<% currentDesign.writeCssIncludes(pageContext); %>
<ui:includeClientLib categories="apps.an-scf-sandbox"/>
```

Chargez votre site Web dans le navigateur et voyez si l’arrière-plan n’est pas bleu.

[http://localhost:4502/content/an-scf-sandbox/en/play.html](http://localhost:4502/content/an-scf-sandbox/en/play.html)

![chlimage_1-226](assets/chlimage_1-226.png)

## Sauver votre travail jusqu&#39;à présent {#saving-your-work-so-far}

A ce stade, il existe un sandbox minimaliste, et il peut être utile d&#39;enregistrer sous forme de package pour que, lors de la lecture, si votre référentiel est corrompu et que vous souhaitez recommencer, vous puissiez désactiver votre serveur, renommer ou supprimer le dossier crx-quickstart/, activer votre serveur, télécharger et installer ce package enregistré, sans avoir à répéter ces étapes de base.

Ce paquet existe dans le didacticiel [Créer un exemple de page](create-sample-page.md) pour ceux qui ne peuvent pas attendre d&#39;entrer et commencer à jouer!...

Pour créer un pack :


* Dans **[!UICONTROL CRXDE Lite]**, cliquez sur l’icône [Package](http://localhost:4502/crx/packmgr/)
* Cliquez sur **[!UICONTROL Créer un package]**

   * Nom du module: `an-scf-sandbox-minimal-pkg`
   * Version: `0.1`
   * Groupe : &lt;laisser comme valeur par défaut>
   * Cliquez sur **[!UICONTROL OK]**

* Cliquez sur **[!UICONTROL Modifier]**

   * Onglet **[!UICONTROL Filtres]** de sélection

      * Click **[!UICONTROL Add filter]**
      * Chemin racine : &lt;accédez à `/apps/an-scf-sandbox`>
      * Cliquez sur **[!UICONTROL Terminé]**
      * Click **[!UICONTROL Add filter]**
      * Chemin racine : &lt;accédez à `/etc/designs/an-scf-sandbox`>
      * Cliquez sur **[!UICONTROL Terminé]**
      * Click **[!UICONTROL Add filter]**
      * Chemin racine : &lt;accédez à `/content/an-scf-sandbox`>
      * Cliquez sur **[!UICONTROL Terminé]**
   * Cliquez sur **[!UICONTROL Enregistrer]**


* Click **[!UICONTROL Build]**

Vous pouvez maintenant sélectionner **[!UICONTROL Télécharger]** pour l’enregistrer sur le disque et **[!UICONTROL Télécharger le package]** ailleurs, ainsi que **[!UICONTROL Plus > Répliquer]** pour pousser le sandbox vers une instance de publication localhost afin d’étendre le domaine de votre sandbox.
