---
title: Fonction multiclient pour les collections, les fragments de code et les modèles de fragments de code
description: Segmentez du contenu dans le référentiel CRX en fonction de l’organisation du client afin d’empêcher tout accès non autorisé.
contentOwner: AG
feature: Collections
role: Architect,Admin,Leader
exl-id: d00a671a-6707-4941-868d-fa13510b7b60
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 12%

---

# Fonction multiclient pour les collections, les fragments de code et les modèles de fragments de code {#multi-tenancy-for-collections-snippets-and-snippet-templates}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

La fonctionnalité multiclient permet de séparer le contenu dans CRX en fonction du préfixe de l’organisation et de l’ID d’organisation afin de protéger le contenu contre tout accès non autorisé par les utilisateurs d’autres organisations.

Adobe Experience Manager (AEM) Assets stocke les données pour chaque organisation dans un chemin d’accès différent. Chaque chemin d’accès spécifique à l’organisation est identifié par le préfixe d’organisation et l’ID d’organisation. Il est inclus à l’emplacement traditionnel où différents types de ressources sont stockés dans CRX.

Par exemple, si vous créez un dossier nommé `Demo`, AEM ressources stocke par défaut le dossier à l’emplacement `../content/dam/Demo` emplacement dans CRX. Lorsque la fonction multi-location est activée, vous pouvez stocker les données à l’adresse `../content/dam/<organization prefix>/<organization id>Demo`.

Par exemple, pour les utilisateurs Adobe Marketing Cloud d’AEM Assets (à la demande) affectés à `aodpremium` organisation, vous pouvez utiliser la fonction multi-location pour configurer le chemin suivant vers `../content/dam/mac/aodpremiumDemo`, séparez le contenu. Dans cet exemple `mac` est le préfixe de l’organisation et `aodpremium` est l’ID d’organisation.

En fonction de l’organisation et de l’identifiant de l’utilisateur, ce chemin d’accès qualifié s’affiche dans l’interface d’AEM Assets et dans divers assistants, y compris les assistants Déplacer et Création de fragments de code pour appliquer la segmentation.

La fonctionnalité multi-location vous permet de segmenter les types de ressources et de composants suivants :

* Collections
* Collections publiques
* Catalogues (notamment l’assistant Ajouter/Sélectionner une page)
* Modèles
* Modèles de fragment de code
* Lightbox
