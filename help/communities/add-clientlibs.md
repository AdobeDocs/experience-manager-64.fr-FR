---
title: Ajout de bibliothèques clientes
seo-title: Add Clientlibs
description: Ajout d’un dossier ClientLibraryFolder
seo-description: Add a ClientLibraryFolder
uuid: cdc1d258-2011-4517-9206-dd2b5d1f7e0d
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: c84040b0-7850-4960-b676-ffa0a74c8cb2
exl-id: 9b8c3d1c-a9b1-4dde-9044-46c8f2b22c22
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '735'
ht-degree: 9%

---

# Ajout de bibliothèques clientes {#add-clientlibs}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

## Ajout d’un dossier ClientLibraryFolder (clientlibs) {#add-a-clientlibraryfolder-clientlibs}

Création d’un dossier ClientLibraryFolder nommé `clientlibs`qui contiendra les éléments JS et CSS utilisés pour effectuer le rendu des pages de votre site.

Le `categories`La valeur de propriété donnée à cette bibliothèque cliente est l’identifiant utilisé pour inclure directement cette bibliothèque cliente à partir d’une page de contenu ou pour l’incorporer dans d’autres bibliothèques clientes.

1. Utilisation **[!UICONTROL CRXDE Lite]**, développer `/etc/designs`

1. Clic droit sur `an-scf-sandbox` et sélectionnez `Create Node`

   * Nom : `clientlibs`
   * Type : `cq:ClientLibraryFolder`

1. Cliquez sur **[!UICONTROL OK]**

![chlimage_1-220](assets/chlimage_1-220.png)

Dans le **[!UICONTROL Propriétés]** pour le nouvel onglet `clientlibs` , saisissez le **`categories`** property:

* Nom : **[!UICONTROL categories]**
* Type :**[!UICONTROL chaîne]**
* Valeur : **[!UICONTROL apps.an-scf-sandbox]**
* Cliquez sur **[!UICONTROL Ajouter]**
* Cliquez sur **[!UICONTROL Enregistrer tout]**

Remarque : la préface de la valeur categories avec &quot;apps&quot;. est une convention permettant d’identifier &quot;l’application propriétaire&quot; comme se trouvant dans le dossier /apps, et non /libs.  IMPORTANT : Ajouter un espace réservé `js.txt` et `css.txt` fichiers . (Il ne s’agit pas officiellement d’un cq:ClientLibraryFolder sans ces éléments.)


1. Clic droit sur **`/etc/designs/an-scf-sandbox/clientlibs`**
1. Sélectionner **[!UICONTROL Créer un fichier...]**
1. Entrée **[!UICONTROL Nom]**: `css.txt`

1. Sélectionner **[!UICONTROL Créer un fichier...]**
1. Entrée **[!UICONTROL Nom]**: `js.txt`

1. Cliquez sur **[!UICONTROL Enregistrer tout]**

![chlimage_1-221](assets/chlimage_1-221.png)

La première ligne des fichiers css.txt et js.txt identifie l’emplacement de base à partir duquel se trouvent les listes de fichiers suivantes.

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

Dans le **[!UICONTROL Propriétés]** pour la `clientlibs` , saisissez la propriété String à plusieurs valeurs. **[!UICONTROL embed]**. Cela incorporera les [bibliothèques côté client (clientlibs) pour les composants SCF](client-customize.md#clientlibs-for-scf). Pour ce tutoriel, nous allons ajouter de nombreuses clientlibs nécessaires aux composants Communities.

**Remarque** qu’il s’agit ou non de l’approche souhaitée à utiliser pour un site de production, car il y a des considérations pratiques par rapport à la taille/vitesse des clientlibs téléchargées pour chaque page.

Si vous utilisez une seule fonction sur une page, vous pouvez inclure la bibliothèque cliente complète de cette fonction directement sur la page, par exemple &lt;% ui:includeClientLib categories=cq.social.hbs.forum&quot; %>

Dans ce cas, nous les incluons tous, et nous préférerions donc les clientlibs SCF les plus basiques qui sont les clientlibs de création :

* Nom : **`embed`**
* Type : **`String`**

* Cliquez sur **`Multi`**
* Valeur : **`cq.social.scf`**

   *&lt;enter> s’affiche dans une boîte de dialogue.*

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

Sans inclure la variable `apps.an-scf-sandbox` Dans la catégorie ClientLibraryFolder de la page, les composants SCF ne seront ni fonctionnels ni stylisés, car le ou les codes JavaScript et le ou les styles nécessaires ne seront pas disponibles.

Par exemple, sans inclure les clientlibs, le composant de commentaires SCF apparaît sans style :

![chlimage_1-224](assets/chlimage_1-224.png)

Une fois les bibliothèques clientes apps.an-scf-sandbox incluses, le composant de commentaires SCF apparaît avec le style suivant :

![chlimage_1-225](assets/chlimage_1-225.png)

L’instruction d’inclusion appartient à la variable `<head>` de la section `<html>` script. La valeur par défaut **`foundation head.jsp`** inclut un script qui peut être superposé : **`headlibs.jsp`**.

**Copiez headlibs.jsp et incluez clientlibs :**

1. Utilisation **[!UICONTROL CRXDE Lite]**, sélectionnez **`/libs/foundation/components/page/headlibs.jsp`**
1. Cliquez avec le bouton droit et sélectionnez **[!UICONTROL Copier]** (ou sélectionnez Copier dans la barre d’outils)
1. Sélectionner **`/apps/an-scf-sandbox/components/playpage`**
1. Cliquez avec le bouton droit et sélectionnez **[!UICONTROL Coller]** (ou sélectionnez Coller dans la barre d’outils)
1. Double-cliquez sur **`headlibs.jsp`** pour l’ouvrir
1. Ajoutez la ligne suivante à la fin du fichier.

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

Chargez votre site web dans le navigateur et vérifiez si l’arrière-plan n’est pas bleu.

[http://localhost:4502/content/an-scf-sandbox/en/play.html](http://localhost:4502/content/an-scf-sandbox/en/play.html)

![chlimage_1-226](assets/chlimage_1-226.png)

## Sauver votre travail jusqu&#39;à présent {#saving-your-work-so-far}

À ce stade, il existe un environnement de test minimaliste. Il peut être intéressant de l’enregistrer sous la forme d’un package. Ainsi, lors de la lecture, si votre référentiel est corrompu et que vous souhaitez recommencer, vous pouvez désactiver votre serveur, renommer ou supprimer le dossier crx-quickstart/, activer votre serveur, télécharger et installer ce package enregistré, sans avoir à répéter ces étapes les plus basiques.

Ce module existe sur la variable [Création d’un exemple de page](create-sample-page.md) tutoriel pour ceux qui ne peuvent pas attendre d&#39;entrer et de commencer à jouer !..

Pour créer un package :


* De **[!UICONTROL CRXDE Lite]**, cliquez sur le bouton [Icône Package](http://localhost:4502/crx/packmgr/)
* Cliquez sur **[!UICONTROL Créer un package]**

   * Nom du module: `an-scf-sandbox-minimal-pkg`
   * Version: `0.1`
   * Groupe : &lt;leave as=&quot;&quot; default=&quot;&quot;>
   * Cliquez sur **[!UICONTROL OK]**

* Cliquez sur **[!UICONTROL Modifier]**

   * Sélectionner **[!UICONTROL Filtres]** tab

      * Cliquez sur **[!UICONTROL Ajouter un filtre]**
      * Chemin racine : &lt;browse to=&quot;&quot; span=&quot;&quot; id=&quot;0&quot; translate=&quot;no&quot; />>`/apps/an-scf-sandbox`
      * Cliquez sur **[!UICONTROL Terminé]**
      * Cliquez sur **[!UICONTROL Ajouter un filtre]**
      * Chemin racine : &lt;browse to=&quot;&quot; span=&quot;&quot; id=&quot;0&quot; translate=&quot;no&quot; />>`/etc/designs/an-scf-sandbox`
      * Cliquez sur **[!UICONTROL Terminé]**
      * Cliquez sur **[!UICONTROL Ajouter un filtre]**
      * Chemin racine : &lt;browse to=&quot;&quot; span=&quot;&quot; id=&quot;0&quot; translate=&quot;no&quot; />>`/content/an-scf-sandbox`
      * Cliquez sur **[!UICONTROL Terminé]**
   * Cliquez sur **[!UICONTROL Enregistrer]**


* Cliquez sur **[!UICONTROL Concevoir]**

Maintenant, vous pouvez sélectionner **[!UICONTROL Télécharger]** pour l’enregistrer sur le disque et **[!UICONTROL Télécharger le module]** ailleurs, puis sélectionnez **[!UICONTROL Plus > Répliquer]** afin de pousser l’environnement de test vers une instance de publication localhost pour développer le domaine de votre environnement de test.
