---
title: Contenu initial du sandbox
seo-title: Contenu initial du sandbox
description: Créer le contenu
seo-description: Créer le contenu
uuid: 9810fe47-8d1a-4238-9b9c-0cc47c63d97a
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: e8f28cd5-7950-4aab-bf62-3d4ed3d33cbd
translation-type: tm+mt
source-git-commit: 2d1e39120d79de029927011d48f7397b53ad91bc
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 7%

---


# Contenu initial du sandbox {#initial-sandbox-content}

Dans cette section, vous créez les pages suivantes qui utilisent toutes le [modèle de page](initial-app.md#createthepagetemplate) :

* Site Sandbox SCF, qui redirige vers la version anglaise de la page principale

   * SCF Sandbox - Page principale de la version anglaise du site

      * Lecture SCF - Enfant de la page principale sur laquelle lire

Bien que ce didacticiel ne traite pas des [copies de langue](../../help/sites-administering/tc-prep.md), il est conçu de sorte que la page racine puisse implémenter la détection de la langue préférée pour l&#39;utilisateur via l&#39;en-tête HTML et la redirection vers la page principale appropriée pour la langue. La convention consiste à utiliser le code de pays à deux lettres pour le nom de noeud de la page, par exemple &quot;en&quot; pour l’anglais, &quot;fr&quot; pour le français, etc.

## Créer des premières pages {#create-first-pages}

Maintenant qu&#39;il existe un [modèle de page](initial-app.md#createthepagetemplate), nous pouvons établir la page racine du site Web dans le répertoire /content.

1. L’interface utilisateur standard fournit actuellement des plans pour la création de sites. Comme ce tutoriel crée un site simple, l&#39;interface utilisateur classique est utile.

   Pour passer à l’interface utilisateur classique, sélectionnez une navigation globale et passez la souris sur le côté droit de l’icône Projets. Sélectionnez l&#39;icône *Passer à l&#39;interface utilisateur classique* qui s&#39;affiche :

   ![chlimage_1-36](assets/chlimage_1-36.png)

   La possibilité de passer à l’interface utilisateur classique doit être [activée par un administrateur](../../help/sites-administering/enable-classic-ui.md).

1. Dans la [page d&#39;accueil classique de l&#39;interface utilisateur](http://localhost:4502/welcome.html), sélectionnez **[!UICONTROL Sites Web]**.

   ![chlimage_1-37](assets/chlimage_1-37.png)

   Vous pouvez également accéder directement à l&#39;interface utilisateur classique des sites Web en accédant à [/siteadmin.](http://localhost:4502/siteadmin)

1. Dans le volet explorateur, sélectionnez **[!UICONTROL Sites Web]**, puis, dans la barre d&#39;outils, sélectionnez **[!UICONTROL Nouveau > Nouvelle page]**.

   Dans la boîte de dialogue **[!UICONTROL Créer une page]**, saisissez ce qui suit :

   * Titre: `SCF Sandbox Site`
   * Nom : `an-scf-sandbox`
   * Sélectionner **[!UICONTROL Un modèle de lecture de sandbox SCF]**
   * Cliquez sur **[!UICONTROL Créer]**

   ![chlimage_1-38](assets/chlimage_1-38.png)

1. Dans le volet explorateur, sélectionnez la page que vous venez de créer, `/Websites/SCF Sandbox Site`, puis cliquez sur **[!UICONTROL Nouveau > Nouvelle page]** :

   * Titre: `SCF Sandbox`
   * Nom : `en`
   * Sélectionner **Un modèle de lecture de sandbox SCF**
   * Cliquez sur **Créer**

1. Dans le volet explorateur, sélectionnez la page que vous venez de créer, `/Websites/SCF Sandbox Site/SCF Sandbox`, puis cliquez sur **[!UICONTROL Nouveau > Nouvelle page]**.

   * Titre: `SCF Play`
   * Nom : `play`
   * Sélectionner **[!UICONTROL Un modèle de lecture de sandbox SCF]**
   * Cliquez sur **[!UICONTROL Créer]**

1. C’est ainsi que le site Web s’affiche désormais dans la console Sites Web. Notez que les pages enfants de l&#39;élément sélectionné dans le volet explorateur s&#39;affichent dans le volet de droite où elles peuvent être gérées.

   ![chlimage_1-39](assets/chlimage_1-39.png)

   Il s’agit de la vue de référentiel de ce qui a été créé à l’aide de l’outil Site Web et du modèle :

   ![chlimage_1-40](assets/chlimage_1-40.png)

## Ajouter le chemin de conception {#add-the-design-path}

Lorsque ` [/etc/designs/an-scf-sandbox](setup-website.md#setupthedesigntreeetcdesigns)` a été créé à l&#39;aide de la section conceptions de la console Outils, la propriété &quot;

* `cq:template="/libs/wcm/core/templates/designpage"`

a été défini, ce qui permet facultativement de référencer des ressources de conception dans un script à l’aide de `currentDesign.getPath()`. Par exemple :

* &lt;>


   * Nom : `cq:designPath`
   * Type : `String`
   * Valeur : `/etc/designs/an-scf-sandbox`

* Cliquez sur le vert `[+] Add`

Le référentiel doit apparaître comme suit :

![chlimage_1-41](assets/chlimage_1-41.png)

* Cliquez sur **[!UICONTROL Enregistrer tout]**

[ Des problèmes d&#39;épargne ? Se reconnecter ! ]

>[!NOTE]
>
>L&#39;utilisation de cq:designPath est facultative et n&#39;est pas liée à l&#39;[utilisation de clientlibs](develop-app.md#includeclientlibsintemplate), qui sont essentiellement requises car les composants SCF utilisent [clientlibs](client-customize.md#clientlibs-for-scf) pour gérer leurs fichiers JS et CSS.

