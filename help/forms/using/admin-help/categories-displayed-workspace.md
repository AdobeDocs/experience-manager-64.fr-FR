---
title: Gérer les catégories affichées dans Workspace
seo-title: Managing the categories displayed in Workspace
description: Dans Workspace, les processus qu’un utilisateur peut démarrer s’affichent dans des catégories dans le volet de navigation de gauche. Découvrez comment gérer ces catégories affichées dans Workspace.
seo-description: In Workspace, the processes that a user can start are displayed in categories in the left navigation pane. Learn how you can manage these categories displayed in Workspace.
uuid: c2a275f5-872e-467f-9f07-4b130631e8a8
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_workspace
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 0d1536a2-10ac-4031-bd7f-264b02d0d75f
exl-id: 5a2bd0ea-2c5e-4e0c-aff1-dba06be6a5b7
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '517'
ht-degree: 10%

---

# Gérer les catégories affichées dans Workspace {#managing-the-categories-displayed-in-workspace}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Dans Workspace, les processus qu’un utilisateur peut démarrer s’affichent dans des catégories dans le volet de navigation de gauche. Vous pouvez configurer les catégories dans Administration Console ou les concepteurs de processus peuvent les configurer dans Workbench. Lorsque les concepteurs de processus créent des processus, ils les affectent à des catégories.

Lorsque vous spécifiez des noms de catégorie, créez-les afin qu’ils s’affichent correctement dans le volet de navigation de Workspace. Par défaut, le volet de navigation de gauche a une largeur fixe de 210 pixels, soit environ 24 caractères. Si le nom de la catégorie que vous indiquez est trop long pour tenir dans la largeur fixe du volet de navigation de gauche, il est tronqué. Le nom complet s’affiche uniquement lorsque le pointeur de la souris le survole. Evitez de tronquer les noms de catégorie. Les exemples suivants illustrent les noms de catégorie qui conviennent et ceux qui sont tronqués :

**Nom de la catégorie qui est adapté :** présence et absence.

**Nom de la catégorie qui est tronqué :** présence et absence (France).

Dans Workspace, les processus d’une catégorie sont généralement affichés sous forme de cartes sur la page Start Process. En règle générale, six cartes peuvent s’afficher à l’écran pour une catégorie avant que l’utilisateur n’ait à faire défiler pour afficher les cartes restantes. Comme le défilement rend la recherche d’un processus plus difficile, pensez à limiter chaque catégorie à six processus ou, selon votre résolution, au nombre de processus pouvant être affichés à l’écran sans avoir besoin de défilement.

Si vous utilisez MySQL comme base de données d’AEM forms, Administration Console ne peut pas distinguer deux noms de catégorie qui ne diffèrent que par l’utilisation de caractères étendus. Par exemple, si vous créez une catégorie nommée abcde et une autre appelée âbcdè, elles sont considérées comme identiques.

## Ajouter une catégorie {#add-a-category}

1. Dans Administration Console, cliquez sur Services > Applications et services > Gestion des catégories.
1. Cliquez sur Ajouter. Si vous souhaitez ajouter une sous-catégorie, sélectionnez une catégorie, puis cliquez sur Ajouter.
1. Dans la zone Name, saisissez le nom de la catégorie, puis, dans la zone Description, saisissez une description de la catégorie.
1. Cliquez sur Ajouter. La catégorie s’affiche sur la page Gestion des catégories .

   ***Remarque ** : vous êtes limité à cinq niveaux de hiérarchie lorsque vous créez des catégories.*

## Modifier une catégorie {#edit-a-category}

1. Dans Administration Console, cliquez sur Services > Applications et services > Gestion des catégories.
1. Sélectionnez la catégorie à modifier, puis cliquez sur Modifier. Vous pouvez également double-cliquer sur une catégorie à modifier.
1. Editez le nom de la catégorie dans la zone Nom .

## Supprimer une catégorie {#remove-a-category}

Vous pouvez supprimer uniquement les catégories qui ne sont pas utilisées.

1. Dans Administration Console, cliquez sur Services > Applications et services > Gestion des catégories.
1. Sur la page Gestion des catégories, cochez la case correspondant à la catégorie à supprimer, puis cliquez sur Supprimer. La catégorie n’est plus affichée.
