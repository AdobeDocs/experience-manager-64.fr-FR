---
title: Application de workflows aux pages
seo-title: Applying Workflows to Pages
description: Lors de la création de pages, vous avez la possibilité d’utiliser des workflows pour exécuter des actions sur vos pages. Il est possible d’appliquer plusieurs workflows.
seo-description: When authoring, you can invoke workflows to take action on your pages; it is also possible to apply more than one workflow..
uuid: 8a1d16f8-69fc-4e3a-b72a-b799ea381024
contentOwner: AEM Docs
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: site-features
discoiquuid: 8556d20a-99bd-4942-b7b8-2db69f64e67c
exl-id: 05c52802-adfd-4b5f-a273-d6a261a00659
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '683'
ht-degree: 67%

---

# Application de workflows aux pages{#applying-workflows-to-pages}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Lors de la création de pages, vous avez la possibilité d’utiliser des workflows pour exécuter des actions sur vos pages. Il est possible d’appliquer plusieurs workflows.

Lorsque vous appliquez le workflow, vous spécifiez les informations suivantes :

* Workflow à appliquer.

   Vous pouvez appliquer n’importe quel workflow (auquel vous avez accès, selon les affectations réalisées par votre administrateur AEM).

* Éventuellement, un titre qui permet d’identifier l’instance de workflow dans la boîte de réception d’un utilisateur.
* la charge utile du workflow ; il peut s’agir d’une ou de plusieurs pages.

Les workflows peuvent être démarrés à partir des éléments suivants :

* la valeur **[Sites](#starting-a-workflow-from-the-sites-console)** console.
* lors de la modification d’une page, via **[Informations sur la page](#starting-a-workflow-from-the-page-editor)**.

>[!NOTE]
>
>Voir également :
>
>* [Application de workflows à des ressources de gestion des ressources numériques](/help/assets/assets-workflow.md).
>* [Utilisation des workflows de projet](/help/sites-authoring/projects-with-workflows.md).
>


>[!NOTE]
>
>AEM administrateurs peuvent [démarrer des workflows à l’aide de plusieurs autres méthodes ;](/help/sites-administering/workflows-starting.md).

## Démarrage d’un workflow à partir de la console Sites {#starting-a-workflow-from-the-sites-console}

Vous pouvez démarrer un workflow des deux manières suivantes :

* Utiliser l’option **[Créer](#starting-a-workflow-from-the-sites-toolbar)** de la barre d’outils Sites.
* Utiliser le rail **[Chronologie](#starting-a-workflow-from-the-timeline)** de la console Sites.

Dans les deux cas, vous devrez :

* [Spécification des détails du workflow dans l’assistant Créer un workflow](#specifying-workflow-details-in-the-create-workflow-wizard).

### Démarrage d’un workflow à partir de la barre d’outils Sites {#starting-a-workflow-from-the-sites-toolbar}

Vous pouvez démarrer un workflow à partir de la barre d’outils de la console **Sites** :

1. Recherchez et sélectionnez la page voulue.

1. À partir de l’option **Créer** de la barre d’outils, vous pouvez maintenant sélectionner **Workflow**.

   ![screen_shot_2019-03-06at121237pm](assets/screen_shot_2019-03-06at121237pm.png)

1. L’assistant **Créer un workflow** vous aidera à [spécifier les détails du workflow](#specifying-workflow-details-in-the-create-workflow-wizard).

### Démarrage d’un workflow à partir de la chronologie {#starting-a-workflow-from-the-timeline}

Dans la **Chronologie**, vous pouvez démarrer un workflow à appliquer à la ressource sélectionnée.

1. [Sélectionnez la ressource](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources) et ouvrez la [Chronologie](/help/sites-authoring/basic-handling.md#timeline) (ou ouvrez la chronologie, puis sélectionnez la ressource).
1. La pointe de la flèche située en regard du champ de commentaire peut être utilisée pour afficher **Démarrer le workflow** :

   ![wf-51](assets/wf-51.png)

1. L’assistant **Créer un workflow** vous aidera à [spécifier les détails du workflow](#specifying-workflow-details-in-the-create-workflow-wizard).

### Spécification des détails du workflow dans l’assistant Créer un workflow {#specifying-workflow-details-in-the-create-workflow-wizard}

Le **Créer un workflow** L’assistant vous aidera à sélectionner le workflow et à spécifier les détails requis.

Après avoir ouvert la **Créer un workflow** à partir de l’un des éléments suivants :

* Utiliser l’option **[Créer](#starting-a-workflow-from-the-sites-toolbar)** de la barre d’outils Sites.
* Utiliser le rail **[Chronologie](#starting-a-workflow-from-the-timeline)** de la console Sites.

Vous pouvez spécifier les détails suivants :

1. Dans le **Propriétés** , les options de base du workflow sont définies :

   * **Modèle de workflow**
   * **Titre du workflow**

      * Vous pouvez spécifier un titre pour cette instance afin de l’identifier ultérieurement.

   Selon le modèle de workflow, les options suivantes sont également disponibles. Ils permettent de conserver le module créé en tant que charge utile une fois le workflow terminé.

   * **Conserver le module de processus**
   * **Titre de module**

      * Pour faciliter l’identification, vous pouvez spécifier un titre pour le module.
   >[!NOTE]
   >
   >L’option **Conserver le package de workflow** est disponible lorsque le workflow a été configuré pour la [prise en charge multi-ressource](/help/sites-developing/workflows-models.md#configuring-a-workflow-for-multi-resource-support) et que plusieurs ressources ont été sélectionnées.

   Une fois que vous avez terminé, cliquez sur **Suivant** pour continuer.

   ![wf-52](assets/wf-52.png)

1. À l’étape **Domaine**, vous pouvez sélectionner :

   * **Ajouter du contenu** pour ouvrir [l’explorateur de chemins d’accès](/help/sites-authoring/author-environment-tools.md#path-browser) et sélectionner des ressources supplémentaires. Lorsque vous êtes dans l’explorateur, cliquez/appuyez sur **l’option de sélection** pour ajouter du contenu à l’instance de workflow.
   * Une ressource existante pour afficher d’autres actions :

      * **Inclure les enfants** pour indiquer que les enfants de la ressource seront inclus dans le workflow.

         Une boîte de dialogue s’ouvre pour vous permettre d’affiner la sélection selon les critères suivants :

         * Inclure seulement les enfants immédiats
         * Inclure seulement les pages modifiées
         * Inclure seulement les pages déjà publiées

         Tous les enfants spécifiés sont ajoutés à la liste des ressources auxquelles le workflow s’appliquera.

      * **Supprimer la sélection** pour supprimer cette ressource du workflow.

   ![wf-53](assets/wf-53.png)

   >[!NOTE]
   >
   >Si vous ajoutez des ressources, vous pouvez utiliser l’option **Retour** pour ajuster le paramètre **Conserver le package de workflow** à l’étape **Propriétés**.

1. Utilisez l’option **Créer** pour fermer l’assistant et créer l’instance du workflow. Une notification s’affiche dans la console Sites.

## Démarrage d’un workflow à partir de l’éditeur de page {#starting-a-workflow-from-the-page-editor}

Lorsque vous modifiez une page, vous pouvez sélectionner **Informations sur la page** dans la barre d’outils. Le menu déroulant comporte l’option . **Démarrer dans le workflow**. Cette option ouvre une boîte de dialogue dans laquelle vous pouvez spécifier le workflow requis, ainsi qu’un titre si nécessaire :

![wf-54](assets/wf-54.png)
