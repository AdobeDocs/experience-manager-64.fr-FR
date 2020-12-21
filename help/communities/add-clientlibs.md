---
title: Ajouter les bibliothèques clientes
seo-title: Ajouter les bibliothèques clientes
description: Ajouter un dossier ClientLibrary
seo-description: Ajouter un dossier ClientLibrary
uuid: cdc1d258-2011-4517-9206-dd2b5d1f7e0d
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: c84040b0-7850-4960-b676-ffa0a74c8cb2
translation-type: tm+mt
source-git-commit: 805e4411930749ff4b6b05ea4a8b87b4f96d72fd
workflow-type: tm+mt
source-wordcount: '704'
ht-degree: 8%

---


# Ajouter les bibliothèques clientes {#add-clientlibs}

## Ajouter un dossier ClientLibraryFolder (clientlibs) {#add-a-clientlibraryfolder-clientlibs}

Créez un dossier ClientLibraryFolder nommé `clientlibs`qui contiendra les fichiers JS et CSS utilisés pour générer les pages de votre site.

La valeur de propriété `categories`attribuée à cette bibliothèque cliente est l&#39;identifiant utilisé pour inclure directement cette bibliothèque cliente à partir d&#39;une page de contenu ou pour l&#39;incorporer dans d&#39;autres bibliothèques clientes.

1. En utilisant **[!UICONTROL CRXDE Lite]**, développez `/etc/designs`

1. Cliquez avec le bouton droit sur `an-scf-sandbox` et sélectionnez `Create Node`

   * Nom : `clientlibs`
   * Type : `cq:ClientLibraryFolder`

1. Cliquez sur **[!UICONTROL OK]**

![chlimage_1-220](assets/chlimage_1-220.png)

Dans l&#39;onglet **[!UICONTROL Propriétés]** du nouveau noeud `clientlibs`, saisissez la propriété **`categories`** :

* Nom :**[!UICONTROL catégories]**
* Type :**[!UICONTROL chaîne]**
* Valeur : **[!UICONTROL apps.an-scf-sandbox]**
* Cliquez sur **[!UICONTROL Ajouter]**
* Cliquez sur **[!UICONTROL Enregistrer tout]**

Remarque : la préface de la valeur catégories avec &quot;applications&quot;. est une convention permettant d&#39;identifier l&#39;application propriétaire comme se trouvant dans le dossier /apps et non /libs.  IMPORTANT : Ajoutez les fichiers d’espace réservé `js.txt` et `css.txt`. (Il ne s’agit pas officiellement d’un cq:ClientLibraryFolder sans eux.)


1. Cliquez avec le bouton droit sur **`/etc/designs/an-scf-sandbox/clientlibs`**
1. Sélectionnez **[!UICONTROL Créer un fichier...]**
1. Saisissez **[!UICONTROL Nom]** : `css.txt`

1. Sélectionnez **[!UICONTROL Créer un fichier...]**
1. Saisissez **[!UICONTROL Nom]** : `js.txt`

1. Cliquez sur **[!UICONTROL Enregistrer tout]**

![chlimage_1-221](assets/chlimage_1-221.png)

La première ligne des fichiers css.txt et js.txt identifie l’emplacement de base à partir duquel les listes de fichiers suivantes doivent être trouvées.

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

Dans l&#39;onglet **[!UICONTROL Propriétés]** du noeud `clientlibs`, saisissez la propriété String à plusieurs valeurs **[!UICONTROL embed]**. Cela incorporera les [bibliothèques côté client (clientlibs) nécessaires pour les composants SCF](client-customize.md#clientlibs-for-scf). Pour ce tutoriel, nous allons ajouter plusieurs clientlibs nécessaires pour les composants Communautés.

**Il** convient de noter que cette approche peut ou non être souhaitée pour un site de production car il y a des considérations de commodité par rapport à la taille/vitesse des clientlibs téléchargés pour chaque page.

Si vous n&#39;utilisez qu&#39;une seule fonction sur une page, vous pouvez inclure directement la bibliothèque cliente complète de cette fonction sur la page, par exemple &lt;% ui:includeClientLib catégories=cq.social.hbs.forum&quot; %>

Dans ce cas, nous les incluons tous, et nous préférerions donc les clientlibs SCF les plus basiques qui sont les clientlibs d&#39;auteur :

* Nom : **`embed`**
* Type : **`String`**

* Cliquez sur **`Multi`**
* Valeur : **`cq.social.scf`**

   *&lt;enter> apparaîtra dans une boîte de dialogue*

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

Voici comment `/etc/designs/an-scf-sandbox/clientlibs` doit maintenant apparaître dans le référentiel :

![chlimage_1-223](assets/chlimage_1-223.png)

## Inclure les bibliothèques clientes dans le modèle PlayPage {#include-clientlibs-in-playpage-template}

Sans inclure la catégorie `apps.an-scf-sandbox` ClientLibraryFolder sur la page, les composants SCF ne seront pas fonctionnels ni stylisés, car le(s) code(s) JavaScript et le(s) style(s) nécessaire(s) ne seront pas disponibles.

Par exemple, sans inclure les clientlibs, le composant de commentaires SCF apparaît sans style :

![chlimage_1-224](assets/chlimage_1-224.png)

Une fois les clientlibs apps.an-scf-sandbox inclus, le composant de commentaires SCF s’affiche avec le style suivant :

![chlimage_1-225](assets/chlimage_1-225.png)

L&#39;instruction include appartient à la section `<head>` du script `<html>`. Le script par défaut **`foundation head.jsp`** comprend un script qui peut être superposé : **`headlibs.jsp`**.

**Copiez headlibs.jsp et incluez clientlibs :**

1. En utilisant **[!UICONTROL CRXDE Lite]**, sélectionnez **`/libs/foundation/components/page/headlibs.jsp`**
1. Cliquez avec le bouton droit et sélectionnez **[!UICONTROL Copier]** (ou sélectionnez Copier dans la barre d&#39;outils).
1. Sélectionner **`/apps/an-scf-sandbox/components/playpage`**
1. Cliquez avec le bouton droit et sélectionnez **[!UICONTROL Coller]** (ou sélectionnez Coller dans la barre d&#39;outils).
1. Cliquez sur **`headlibs.jsp`** doublon pour l&#39;ouvrir.
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

Chargez votre site Web dans le navigateur et vérifiez si l’arrière-plan n’est pas bleu.

[http://localhost:4502/content/an-scf-sandbox/en/play.html](http://localhost:4502/content/an-scf-sandbox/en/play.html)

![chlimage_1-226](assets/chlimage_1-226.png)

## Sauvegarder votre travail jusqu&#39;à présent {#saving-your-work-so-far}

A ce stade, il existe un sandbox minimaliste, et il peut être utile d&#39;enregistrer sous forme de package pour que, lors de la lecture, si votre référentiel est corrompu et que vous souhaitez le début, vous puissiez désactiver votre serveur, renommer ou supprimer le dossier crx-quickstart/, activer votre serveur, télécharger et installer ce package enregistré, et ne pas avoir à répéter ces étapes les plus basiques.

Ce package existe sur le didacticiel [Créer un exemple de page](create-sample-page.md) pour ceux qui ne peuvent pas attendre d&#39;entrer et de jouer à début !...

Pour créer un pack :


* Dans **[!UICONTROL CRXDE Lite]**, cliquez sur l’icône [Package](http://localhost:4502/crx/packmgr/)
* Cliquez sur **[!UICONTROL Créer un package]**

   * Nom du module: `an-scf-sandbox-minimal-pkg`
   * Version: `0.1`
   * Groupe : &lt;laisser comme valeur par défaut>
   * Cliquez sur **[!UICONTROL OK]**

* Cliquez sur **[!UICONTROL Modifier]**

   * Sélectionner **[!UICONTROL Filtres]** onglet

      * Cliquez sur **[!UICONTROL Ajouter le filtre]**
      * Chemin racine : &lt;accédez à &lt;a0/&quot;`/apps/an-scf-sandbox`
      * Cliquez sur **[!UICONTROL Terminé]**
      * Cliquez sur **[!UICONTROL Ajouter le filtre]**
      * Chemin racine : &lt;accédez à &lt;a0/&quot;`/etc/designs/an-scf-sandbox`
      * Cliquez sur **[!UICONTROL Terminé]**
      * Cliquez sur **[!UICONTROL Ajouter le filtre]**
      * Chemin racine : &lt;accédez à &lt;a0/&quot;`/content/an-scf-sandbox`
      * Cliquez sur **[!UICONTROL Terminé]**
   * Cliquez sur **[!UICONTROL Enregistrer]**


* Cliquez sur **[!UICONTROL Créer]**

Vous pouvez désormais sélectionner **[!UICONTROL Télécharger]** pour l’enregistrer sur le disque et **[!UICONTROL Télécharger le package]** ailleurs, ainsi que **[!UICONTROL Plus > Répliquer]** pour pousser le sandbox vers une instance de publication hôte local afin de développer le domaine de votre sandbox.
