---
title: Contenu d’environnement de test initial
seo-title: Initial Sandbox Content
description: Créer le contenu
seo-description: Create content
uuid: 9810fe47-8d1a-4238-9b9c-0cc47c63d97a
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: e8f28cd5-7950-4aab-bf62-3d4ed3d33cbd
exl-id: 171fd95d-51f6-468b-84ed-4a757dba868e
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '464'
ht-degree: 7%

---

# Contenu d’environnement de test initial {#initial-sandbox-content}

Dans cette section, vous créez les pages suivantes qui utilisent toutes le [modèle de page](initial-app.md#createthepagetemplate):

* SCF Sandbox Site, qui redirige vers la version anglaise de la page principale.

   * Environnement de test SCF : page principale de la version anglaise du site.

      * Lecture SCF - Enfant de la page principale sur laquelle lire

Bien que ce tutoriel ne décrit pas [copies de langue](../../help/sites-administering/tc-prep.md), il est conçu de sorte que la page racine puisse mettre en oeuvre la détection de la langue souhaitée pour l’utilisateur par le biais de l’en-tête du HTML et rediriger vers la page principale appropriée pour la langue. La convention consiste à utiliser le code de pays à deux lettres pour le nom de noeud de la page, par exemple &quot;en&quot; pour l’anglais, &quot;fr&quot; pour le français, etc.

## Créer les premières pages {#create-first-pages}

Maintenant, il y a une [modèle de page](initial-app.md#createthepagetemplate), nous pouvons établir la page racine du site web dans le répertoire /content .

1. L’interface utilisateur standard fournit actuellement des plans directeurs pour la création de sites. Comme ce tutoriel crée un site simple, l’IU classique est utile.

   Pour passer à l’IU classique, sélectionnez la navigation globale et survolez le côté droit de l’icône Projets . Sélectionnez la *Basculer vers l’interface utilisateur classique* qui s’affiche :

   ![chlimage_1-36](assets/chlimage_1-36.png)

   La possibilité de passer à l’IU classique doit être [activé par un administrateur](../../help/sites-administering/enable-classic-ui.md).

1. Dans la [page d’accueil de l’IU classique](http://localhost:4502/welcome.html), sélectionnez **[!UICONTROL Sites web]**.

   ![chlimage_1-37](assets/chlimage_1-37.png)

   Vous pouvez également accéder directement à l’IU classique des sites web en accédant à [/siteadmin.](http://localhost:4502/siteadmin)

1. Dans le volet de l’explorateur, sélectionnez **[!UICONTROL Sites web]** puis, dans la barre d’outils, sélectionnez **[!UICONTROL Nouveau > Nouvelle page]**.

   Dans le **[!UICONTROL Créer une page]** , saisissez ce qui suit :

   * Titre : `SCF Sandbox Site`
   * Nom : `an-scf-sandbox`
   * Sélectionner **[!UICONTROL Modèle SCF Sandbox Play]**
   * Cliquez sur **[!UICONTROL Créer]**

   ![chlimage_1-38](assets/chlimage_1-38.png)

1. Dans le volet de l&#39;explorateur, sélectionnez la page que vous venez de créer, `/Websites/SCF Sandbox Site`, puis cliquez sur **[!UICONTROL Nouveau > Nouvelle page]**:

   * Titre : `SCF Sandbox`
   * Nom : `en`
   * Sélectionner **Modèle SCF Sandbox Play**
   * Cliquez sur **Créer**

1. Dans le volet de l&#39;explorateur, sélectionnez la page que vous venez de créer, `/Websites/SCF Sandbox Site/SCF Sandbox`, puis cliquez sur **[!UICONTROL Nouveau > Nouvelle page]**

   * Titre : `SCF Play`
   * Nom : `play`
   * Sélectionner **[!UICONTROL Modèle SCF Sandbox Play]**
   * Cliquez sur **[!UICONTROL Créer]**

1. C’est ainsi que le site web apparaît désormais dans la console Sites web . Notez que les pages enfants de l’élément sélectionné dans le volet de l’explorateur s’affichent dans le volet de droite où elles peuvent être gérées.

   ![chlimage_1-39](assets/chlimage_1-39.png)

   Il s’agit de la vue référentiel de ce qui a été créé à l’aide de l’outil Site Web et du modèle :

   ![chlimage_1-40](assets/chlimage_1-40.png)

## Ajout du chemin de conception {#add-the-design-path}

When ` [/etc/designs/an-scf-sandbox](setup-website.md#setupthedesigntreeetcdesigns)` a été créé à l’aide de la section conceptions de la console Outils, la propriété &quot;

* `cq:template="/libs/wcm/core/templates/designpage"`

a été défini, ce qui permet facultativement de référencer des ressources de conception dans un script à l’aide de la fonction `currentDesign.getPath()`. Par exemple :

* &lt;% ChaîneIcon = currentDesign.getPath() + &quot;/favicon.ico&quot;; %>


   * Nom : `cq:designPath`
   * Type : `String`
   * Valeur : `/etc/designs/an-scf-sandbox`

* Cliquez sur le vert `[+] Add`

Le référentiel doit se présenter comme suit :

![chlimage_1-41](assets/chlimage_1-41.png)

* Cliquez sur **[!UICONTROL Enregistrer tout]**

[ Des problèmes d&#39;épargne ? Reconnectez-vous ! ]

>[!NOTE]
>
>L’utilisation de cq:designPath est facultative et n’est pas liée à la variable [utilisation de clientlibs](develop-app.md#includeclientlibsintemplate), qui sont essentiellement requis lorsque les composants SCF utilisent [clientlibs](client-customize.md#clientlibs-for-scf) pour gérer leurs fichiers JS et CSS.
