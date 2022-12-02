---
title: Consoles d’administration
seo-title: Admin Consoles
description: Comment utiliser les consoles d’administration disponibles dans AEM.
seo-description: Lear how to use the Admin Consoles available in AEM.
uuid: 701dc57c-f7b4-421e-a847-577ae2585e80
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
discoiquuid: 98ba3093-1edb-4891-abbe-47cf6e4f1feb
exl-id: f3c03562-aaeb-4d43-aee1-d92d661ee329
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 92%

---

# Consoles d’administration{#admin-consoles}

Par défaut, la possibilité de basculer vers l’IU classique via les consoles d’administration a été désactivée. Par conséquent, les icônes contextuelles qui s’affichaient lors du survol du curseur sur certaines icônes de la console, et qui permettaient d’accéder à l’IU classique, ne sont plus affichées.

![screen_shot_2018-03-23at111956](assets/screen_shot_2018-03-23at111956.png)

Chaque console qui possède une version d’IU classique dans `/libs/cq/core/content/nav` peut être réactivée individuellement afin que l’option **IU classique** s’affiche à nouveau lors du survol du curseur sur l’icône de la console.

Dans cet exemple, nous réactivons l’IU classique pour la console Sites.

1. À l’aide de CRXDE Lite, recherchez le noeud correspondant à la console d’administration pour laquelle vous souhaitez réactiver l’interface utilisateur classique. Il se trouve sous :

   `/libs/cq/core/content/nav`

   Par exemple :

   [ `http://localhost:4502/crx/de/index.jsp#/libs/cq/core/content/nav`](http://localhost:4502/crx/de/index.jsp#/libs/cq/core/content/nav)

1. Sélectionnez le nœud correspondant à la console pour laquelle vous souhaitez réactiver l’IU classique. Dans notre exemple, nous allons recréer l’IU classique pour la console Sites.

   `/libs/cq/core/content/nav/sites`

1. Créez un recouvrement à l’aide de l’option **Nœud de recouvrement** ; par exemple :

   * **Chemin** : `/apps/cq/core/content/nav/sites`
   * **Emplacement du recouvrement** : `/apps/`
   * **Faire correspondre les types de nœuds** : actif (cochez la case)

1. Ajoutez la propriété booléenne suivante au nœud recouvert :

   `enableDesktopOnly = {Boolean}true`

1. L’option **IU classique** est toujours disponible en tant qu’option d’élément contextuel dans la console d’administration.

   ![screen_shot_2018-03-23at111924](assets/screen_shot_2018-03-23at111924.png)

Répétez ces étapes pour chaque console pour laquelle vous souhaitez réactiver l’accès à la version d’IU classique.
