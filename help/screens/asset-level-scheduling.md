---
title: Planification au niveau des ressources
seo-title: Planification au niveau des ressources
description: 'Consultez cette page pour apprendre comment activer une ressource spécifique dans un canal pour une période planifiée dans le fuseau horaire local du lecteur. '
seo-description: 'Consultez cette page pour apprendre comment activer une ressource spécifique dans un canal pour une période planifiée dans le fuseau horaire local du lecteur. '
uuid: b79d521b-19d4-47c8-a41a-148d7bbf6ac9
contentOwner: jsyal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/SCREENS
topic-tags: authoring
discoiquuid: da25cdc7-c814-493e-8d8e-b6191fee2831
noindex: true
translation-type: tm+mt
source-git-commit: 4b2c0f3a1ef8759eb3182b93cffa09c4afc23b6a

---


# Planification au niveau des ressources {#asset-level-scheduling}

Cette section décrit la planification au niveau des ressources pour les ressources utilisées dans les canaux.

Cette section aborde les sujets suivants :

* Présentation
* Utilisation de la planification au niveau des ressources
* Gestion de la périodicité pour les ressources
* Planification multiressource

>[!CAUTION]
>
>Cette fonctionnalité d’AEM Screens est disponible uniquement si vous avez installé AEM 6.3 Feature Pack 3 ou AEM 6.4 Screens Feature Pack 1.
>
>Pour accéder à ce Feature Pack, vous devez contacter l’assistance d’Adobe et demander à y accéder. Une fois que vous disposez des autorisations nécessaires, vous pouvez le télécharger à partir de Package Share.

## Présentation {#overview}

***La planification au niveau des ressources*** vous permet d’activer une ressource spécifique dans un canal pour une période planifiée dans le fuseau horaire local du lecteur. Cette option est disponible pour les images, les vidéos, les transitions, les pages et les canaux incorporés (dynamiques ou statiques).

*Par exemple*, vous souhaitez qu’une promotion spéciale s’affiche uniquement pendant la Happy Hour (de 14h00 à 17h00) les lundis et les mercredis.

Avec cette fonctionnalité, vous pouvez non seulement spécifier la date et l’heure de début et de fin, mais également un modèle de périodicité.

## Utilisation de la planification au niveau des ressources {#using-asset-level-scheduling}

La planification au niveau des ressources s’effectue en configurant l’onglet **Activation** lors de l’accès aux propriétés d’une ressource.

Suivez les étapes ci-dessous pour effectuer une planification au niveau des ressources :

1. Sélectionnez un canal et cliquez sur **Modifier** dans la barre d’actions pour ajouter ou modifier du contenu dans votre canal.

   ![screen_shot_2018-04-23at111422am](assets/screen_shot_2018-04-23at111422am.png)

   >[!NOTE]
   >
   >Pour apprendre en détail comment
   >
   >* créer un projet, voir [Création d’un projet](creating-a-screens-project.md).
   >* créer et ajouter du contenu à un canal, voir [Gestion des canaux](managing-channels.md).


1. Cliquez sur **Modifier** pour ouvrir l&#39;éditeur de canaux et sélectionner une ressource à laquelle vous souhaitez appliquer la planification.

   ![screen_shot_2018-04-24at90434pm](assets/screen_shot_2018-04-24at90434pm.png)

1. Sélectionnez la ressource et cliquez sur l’icône **Configurer** en haut à gauche pour ouvrir les propriétés de l’image.

   Cliquez sur l’onglet **Activation**.

   ![screen_shot_2018-04-23at112348am](assets/screen_shot_2018-04-23at112348am.png)

1. You can specify the date from the date picker from the **Active from** and **Active until** fields.

   If you select the** Active from** and **Active until** date and time, the asset will display and loop only between that start date/time and end date/time respectively.

   ![screen_shot_2018-04-23at113545am](assets/screen_shot_2018-04-23at113545am.png)

## Gestion de la périodicité pour les ressources {#handling-recurrence-in-assets}

Vous pouvez planifier l’activation périodique des ressources à certains intervalles, tous les jours, toutes les semaines ou tous les mois, selon vos besoins.

Supposons que vous souhaitiez afficher une image uniquement le vendredi de 13h00 à 22h00. Vous pouvez utiliser l’onglet Activation pour définir l’intervalle périodique souhaité pour votre ressource.

### Ajout d’un événement périodique pour votre ressource {#adding-a-recurring-event-for-your-asset}

1. Sélectionnez la ressource et cliquez sur l’icône **Configurer** pour ouvrir la boîte de dialogue des propriétés.
1. Après avoir saisi la date/l’heure de début et la date/heure de fin, vous pouvez utiliser une expression cron ou une version textuelle naturelle pour spécifier votre planification de périodicité.

   Vous pouvez rechercher sur Internet un générateur d’expression cron gratuit, puis copier et coller l’expression cron dans la **Planification**. Votre ressource s’affichera alors pour l’intervalle de jours et d’heures spécifié.

   *Vous pouvez également*, au lieu d’utiliser l’expression cron, utiliser la version textuelle naturelle, comme *après 6h00 et avant 18h00* le vendredi, pour accomplir votre tâche. Saisissez le texte dans le **Planification** pour afficher votre ressource.

## Planification multiressource {#multi-asset-scheduling}

>[!CAUTION]
>
>La fonction de **planification multiressource** n’est disponible que si vous avez installé AEM 6.3 Feature Pack 5 ou AEM 6.4 Feature Pack 3.

La ***planification multiressource*** permet à l’utilisateur de sélectionner plusieurs ressources et d’appliquer une planification d’exécution à toutes les ressources sélectionnées.

### Conditions préalables {#prerequisites}

Pour utiliser la planification au niveau multiressource pour vos ressources, créez un projet AEM Screens avec un canal de séquence. Par exemple, le cas d’utilisation suivant montre l’implémentation de la fonctionnalité :

* Créez un projet AEM Screens intitulé **MultiAssetDemo**
* Créez un canal intitulé **MultiAssetChannel** et ajoutez du contenu au canal, comme illustré ci-dessous.

![screen_shot_2018-12-21at70128am](assets/screen_shot_2018-12-21at70128am.png)

Pour sélectionner plusieurs ressources et planifier leur affichage dans un projet AEM Screens, procédez comme suit :

1. Sélectionnez **MultiAssetChannel** et cliquez sur **Modifier** dans la barre d’actions pour ouvrir l’éditeur.

   ![screen_shot_2018-12-21at70313am](assets/screen_shot_2018-12-21at70313am.png)

1. Sélectionnez plusieurs ressources dans l’éditeur, puis cliquez sur **Modifier l’activation** (icône en haut à gauche).

   ![screen_shot_2018-12-21at70550am](assets/screen_shot_2018-12-21at70550am.png)

1. Select the date and time in **Active from** and **Active until **from the **Component Activation** dialog box. Cliquez sur l&#39;icône en forme de coche lorsque vous avez terminé de sélectionner les planifications.

   ![screen_shot_2018-12-17at20337pm](assets/screen_shot_2018-12-17at20337pm.png)

1. Cliquez sur Actualiser pour vérifier les ressources auxquelles une planification multiressource est appliquée.

   >[!NOTE]
   >
   >L’icône de planification s’affiche dans l’angle supérieur droit pour les ressources qui comportent une planification multiressource.

   ![screen_shot_2018-12-21at70722am](assets/screen_shot_2018-12-21at70722am.png)

