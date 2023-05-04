---
title: Utilisation des workflows
seo-title: Working with Workflows
description: Les workflows dans AEM permettent d’automatiser une série d’étapes exécutées sur une page ou une ressource.
seo-description: Workflows in AEM allow you to automate a series of steps that are performed on a page or asset.
uuid: c4442d2a-c6b0-49d4-a1ce-384017c45bf0
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: site-features
discoiquuid: 7cb99618-d903-4cfb-b0d9-b23d189f6e78
exl-id: 8d318fd5-3d8f-4144-95c8-d90685378a91
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 39%

---

# Utilisation des workflows{#working-with-workflows}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Les workflows AEM permettent d’automatiser une série d’étapes exécutées sur une ou plusieurs pages et/ou ressources.

Par exemple, lors de la publication, un éditeur doit réviser le contenu, avant qu’un administrateur du site active la page. Un workflow qui automatise cet exemple avertit chaque participant lorsqu’il est temps qu’il effectue sa tâche :

1. L’auteur applique le workflow à la page.
1. L’éditeur reçoit une tâche qui indique qu’il est nécessaire de réviser le contenu de la page. Une fois leur tâche terminée, ils indiquent que leur tâche est terminée.
1. L’administrateur du site reçoit ensuite une tâche qui demande l’activation de la page. Une fois leur tâche terminée, ils indiquent que leur tâche est terminée.

En règle générale :

* Les auteurs de contenu appliquent des workflows aux pages et participent aux workflows.
* Les workflows que vous utilisez sont spécifiques aux processus d’entreprise de votre entreprise.

Les pages suivantes couvrent :

* [Application de workflows aux pages](/help/sites-authoring/workflows-applying.md)
* [Participation aux workflows](/help/sites-authoring/workflows-participating.md)
