---
title: Configurer le cache de formulaires adaptatifs
seo-title: Configurer le cache de formulaires adaptatifs
description: 'Le cache de formulaires adaptatifs est spécialement conçu pour les formulaires et documents adaptatifs. Il met en cache des formulaires et documents adaptatifs en vue de réduire le temps nécessaire pour effectuer le rendu d’un formulaire ou d’un document adaptatif sur le client. '
seo-description: 'Le cache de formulaires adaptatifs est spécialement conçu pour les formulaires et documents adaptatifs. Il met en cache des formulaires et documents adaptatifs en vue de réduire le temps nécessaire pour effectuer le rendu d’un formulaire ou d’un document adaptatif sur le client. '
uuid: 3bd4e405-1eab-4e02-95cd-eb6ac25d18e3
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: Configuration
discoiquuid: dd18f7b5-882d-4e81-ab3d-85f1e5d74992
role: Admin
exl-id: 6a610e9d-beec-486d-b1d2-78b5fec44c52
source-git-commit: 3c050c33a384d586d74bd641f7622989dc1d6b22
workflow-type: tm+mt
source-wordcount: '311'
ht-degree: 87%

---

# Configurer le cache de formulaires adaptatifs {#configure-adaptive-forms-cache}

Un cache est un mécanisme qui permet de raccourcir les temps d’accès aux données, réduire le temps de réponse et améliorer les vitesses d’entrée/sortie (E/S). Le cache de formulaires adaptatifs stocke uniquement le contenu HTML et la structure JSON d’un formulaire adaptatif sans enregistrer les données pré-renseignées. Cela permet de réduire le temps nécessaire pour effectuer le rendu d’un formulaire ou d’un document adaptatif sur le client. Il est spécialement conçu pour les formulaires adaptatifs et prend également en charge les documents adaptatifs.

>[!NOTE]
>
>Lorsque vous utilisez le cache de formulaires adaptatifs, utilisez le répartiteur AEM pour masquer les bibliothèques client (CSS et Javascript) d’un formulaire ou d’un document adaptatif.

>[!NOTE]
>
>Lors du développement des composants personnalisés, sur le serveur utilisé pour le développement, gardez le cache de formulaires adaptatifs désactivé.

## Configurer le cache {#configure-the-cache}

Effectuez les étapes suivantes pour configurer le cache de formulaires adaptatifs :

1. Accédez à la page de configuration de la console web AEM à l’adresse `https://[server]:[port]/system/console/configMgr`.
1. Cliquez sur la **configuration de canal web de communication interactive de formulaire adaptatif** pour éditer ses valeurs de configuration.
1. Dans la boîte de dialogue Modifier les valeurs de configuration, indiquez le nombre maximal de formulaires ou documents qu’une instance du serveur AEM Forms peut mettre en cache dans le champ **Nombre de Forms adaptatives**. La valeur par défaut est 100.

   >[!NOTE]
   >
   >Pour désactiver le cache, définissez la valeur du champ Nombre de formulaires adaptatifs sur **0**. Le cache est réinitialisé, et tous les formulaires et documents sont supprimés du cache lorsque vous désactivez ou modifiez la configuration du cache.

   ![Boîte de dialogue de configuration du cache HTML de formulaires adaptatifs](assets/cache-configuration-edit.png)

1. Cliquez sur **Enregistrer** pour enregistrer la configuration.
