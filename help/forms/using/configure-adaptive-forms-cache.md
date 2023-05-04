---
title: Configurer le cache de formulaires adaptatifs
seo-title: Configure adaptive forms cache
description: Le cache de formulaires adaptatifs est conçu spécifiquement pour les formulaires et documents adaptatifs. Il met en cache les formulaires et documents adaptatifs dans le but de réduire le temps nécessaire au rendu d’un formulaire ou d’un document adaptatif sur le client.
seo-description: The adaptive forms cache is designed specifically for adaptive forms and documents. It caches adaptive forms and adaptive documents with the objective of reducing the time required to render an adaptive form or document on the client.
uuid: 3bd4e405-1eab-4e02-95cd-eb6ac25d18e3
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: Configuration
discoiquuid: dd18f7b5-882d-4e81-ab3d-85f1e5d74992
role: Admin
exl-id: 6a610e9d-beec-486d-b1d2-78b5fec44c52
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 49%

---

# Configurer le cache de formulaires adaptatifs {#configure-adaptive-forms-cache}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Un cache est un mécanisme qui permet de raccourcir les temps d’accès aux données, réduire le temps de réponse et améliorer les vitesses d’entrée/sortie (E/S). Le cache de formulaires adaptatifs stocke uniquement le contenu de HTML et la structure JSON d’un formulaire adaptatif sans enregistrer de données préremplies. Cela permet de réduire le temps nécessaire au rendu d’un formulaire ou d’un document adaptatif sur le client. Il est conçu spécifiquement pour les formulaires adaptatifs et prend également en charge les documents adaptatifs.

>[!NOTE]
>
>Lors de l’utilisation du cache de formulaires adaptatifs, utilisez AEM Dispatcher pour mettre en cache les bibliothèques clientes (CSS et JavaScript) d’un formulaire ou d’un document adaptatif.

>[!NOTE]
>
>Lors du développement des composants personnalisés, sur le serveur utilisé pour le développement, gardez le cache de formulaires adaptatifs désactivé.

## Configuration du cache {#configure-the-cache}

Pour configurer la mise en cache des formulaires adaptatifs, procédez comme suit :

1. Accédez à la page de configuration de la console web AEM à l’adresse `https://[server]:[port]/system/console/configMgr`.
1. Cliquez sur la **configuration de canal web de communication interactive de formulaire adaptatif** pour éditer ses valeurs de configuration.
1. Dans la boîte de dialogue Modifier les valeurs de configuration, spécifiez le nombre maximal de formulaires ou de documents qu’une instance du serveur AEM Forms peut mettre en cache le champ **Nombre de formulaires adaptatifs**. La valeur par défaut est 100.

   >[!NOTE]
   >
   >Pour désactiver le cache, définissez la valeur du champ Nombre de Forms adaptatives sur **0**. Le cache est réinitialisé, et tous les formulaires et documents sont supprimés du cache lorsque vous désactivez ou modifiez la configuration du cache.

   ![Boîte de dialogue de configuration du cache HTML de formulaires adaptatifs](assets/cache-configuration-edit.png)

1. Cliquez sur **Enregistrer** pour enregistrer la configuration.
