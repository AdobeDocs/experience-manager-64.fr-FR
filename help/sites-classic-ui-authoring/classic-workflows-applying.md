---
title: Application de workflows aux pages
seo-title: Applying Workflows to Pages
description: Les processus peuvent être démarrés à partir de la console Sites web ou, lors de la modification d’une page, à partir du sidekick.
seo-description: Workflows can be started from either the Websites console or, when editing a page, from Sidekick.
uuid: 55f6f1d7-da54-4732-b9ff-b7479622db51
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: site-features
discoiquuid: 22712b73-90f2-4329-b32f-dbb7ce802d1d
exl-id: f10680e5-e8ae-49a0-ae52-3aa1f22b2d3e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '289'
ht-degree: 39%

---

# Application de workflows aux pages{#applying-workflows-to-pages}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Lorsque vous appliquez le workflow, vous spécifiez les informations suivantes :

* Workflow à appliquer.

   Vous pouvez appliquer n’importe quel workflow (auquel vous avez accès, selon les affectations réalisées par votre administrateur AEM).
* Facultatif :

   * Un commentaire qui fournit des informations sur la raison pour laquelle vous avez démarré le workflow.
   * Titre permettant d’identifier l’instance de workflow dans la boîte de réception d’un utilisateur.

>[!NOTE]
>
>AEM administrateurs peuvent démarrer des workflows à l’aide de [plusieurs autres méthodes](/help/sites-administering/workflows-starting.md).

## Application de workflows {#applying-workflows}

Les processus peuvent être démarrés à partir de la console Sites web ou, lors de la modification d’une page, à partir du sidekick.

La colonne **Statut** de la console **Sites web** indique si un workflow a été appliqué à une page :

![WorkflowStatus](assets/workflowstatus.png)

### Démarrage d’un workflow à partir de la console Sites web {#starting-a-workflow-from-the-websites-console}

1. Ouvrez la console Sites web . ([http://localhost:4502/siteadmin](http://localhost:4502/siteadmin))
1. Dans l’arborescence Sites Web, sélectionnez le parent de la page à laquelle vous souhaitez appliquer le workflow.
1. Dans la liste de pages, sélectionnez la page, puis cliquez sur Workflow.
1. Dans la boîte de dialogue Démarrer le processus , sélectionnez le processus à appliquer. Vous pouvez éventuellement saisir un commentaire et un titre. Cliquez ensuite sur Démarrer.

### Démarrage d’un workflow à l’aide du sidekick {#starting-a-workflow-using-sidekick}

1. Ouvrez la console Sites web .
1. Ouvrez la page requise.
1. Sélectionnez l’onglet Workflow dans le sidekick.
1. Développez la boîte de dialogue **Workflow** afin de sélectionner le **Workflow**. Si vous le souhaitez, entrez le **Titre du workflow** et un **Commentaire**.

   ![workflowstartsidekick](assets/workflowstartsidekick.png)

1. Cliquez sur **Démarrer le processus** pour démarrer une nouvelle instance de workflow avec les propriétés que vous avez configurées et la page active comme charge utile. Le workflow est maintenant en cours d’exécution.
