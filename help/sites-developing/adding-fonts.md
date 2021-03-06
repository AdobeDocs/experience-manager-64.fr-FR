---
title: Ajout de polices pour le rendu graphique
seo-title: Adding Fonts for Graphic-Rendering
description: AEM vous permet de générer des objets graphiques incorporant du texte extrait dynamiquement de votre contenu
seo-description: AEM allows you to generate graphics incorporating text dynamically taken from your content
uuid: 67d9b10f-e986-4d29-bde2-10e08075fe17
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: platform
content-type: reference
discoiquuid: 6af48ef5-75e6-4b66-bc0d-ecf254b1c4ef
exl-id: f29868e3-d05c-4898-94d1-0c77ab6b72eb
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 66%

---

# Ajout de polices pour le rendu graphique{#adding-fonts-for-graphic-rendering}

AEM vous permet de générer des objets graphiques incorporant du texte extrait dynamiquement de votre contenu.

Pour ce faire, vous pouvez également charger et utiliser vos propres polices.

Actuellement, toutes les implémentations de la plate-forme Java prennent en charge les polices [TrueType](https://en.wikipedia.org/wiki/Truetype).

1. Ouvrez CRXDE Lite et accédez au dossier de l’application de projet :

   `/apps/<your-project>/`

1. Sous `/apps/<your-project>/` créez un noeud :

   * **Nom** : `fonts`
   * **Type** : `sling:Folder`

   Enregistrez toutes les modifications.

1. Copiez les fichiers de polices dans ce dossier, par exemple, au moyen de WebDAV.

   >[!NOTE]
   >
   >Les fichiers de polices du référentiel doivent comporter le suffixe `*.ttf` ou `*.TTF`.

1. Mettez à jour la [configuration OSGi](/help/sites-deploying/configuring-osgi.md) de [Day Commons GFX Font Helper](/help/sites-deploying/osgi-configuration-settings.md). Ajoutez le chemin d’accès à votre dossier de polices. c’est-à-dire `/apps/<your-project>/fonts`.

1. Revenez à CRXDE Lite. Vous devriez maintenant voir une `.fontlist` dans votre dossier contenant le nom des polices importées.

   Ces polices sont désormais prêtes à être déployées dans l’API Java.

Pour plus d’informations sur l’utilisation des polices avec l’API Java, consultez la [documentation de la classe Font de l’API Java](https://download.oracle.com/javase/6/docs/api/java/awt/Font.html).
