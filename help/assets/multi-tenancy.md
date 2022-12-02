---
title: Fonction multiclient pour les collections, les fragments de code et les modèles de fragments de code
description: Segmentez du contenu dans le référentiel CRX en fonction de l’organisation du client afin d’empêcher tout accès non autorisé.
contentOwner: AG
feature: Collections
role: Architect,Admin,Leader
exl-id: d00a671a-6707-4941-868d-fa13510b7b60
source-git-commit: 5d96c09ef764b02e08dcdf480da1ee18f4d9a30c
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 43%

---

# Fonction multiclient pour les collections, les fragments de code et les modèles de fragments de code {#multi-tenancy-for-collections-snippets-and-snippet-templates}

La fonction multiclient permet de séparer du contenu dans CRX en fonction du préfixe et de l’identifiant d’organisation, de sorte à protéger le contenu contre tout accès non autorisé par les utilisateurs d’autres organisations.

Adobe Experience Manager (AEM) Assets stocke les données de chaque organisation à un chemin d’accès différent. Chaque chemin d’accès spécifique à l’organisation est identifié par le préfixe d’organisation et l’ID d’organisation. Il est inclus à l’emplacement traditionnel où différents types de ressources sont stockés dans CRX.

Par exemple, si vous créez un dossier nommé `Demo`, AEM ressources stocke par défaut le dossier à l’emplacement `../content/dam/Demo` emplacement dans CRX. Lorsque la fonction multi-location est activée, vous pouvez stocker les données à l’adresse `../content/dam/<organization prefix>/<organization id>Demo`.

Par exemple, pour les utilisateurs Adobe Marketing Cloud d’AEM Assets (à la demande) affectés à `aodpremium` organisation, vous pouvez utiliser la fonction multi-location pour configurer le chemin suivant vers `../content/dam/mac/aodpremiumDemo`, séparez le contenu. Dans cet exemple `mac` est le préfixe de l’organisation et `aodpremium` est l’ID d’organisation.

En fonction de l’organisation et de l’identifiant de l’utilisateur, ce chemin d’accès s’affiche dans l’interface d’AEM Assets et dans différents assistants, notamment les assistants Déplacement et Création de fragment de code, pour appliquer la séparation.

La fonctionnalité multi-location vous permet de segmenter les types de ressources et de composants suivants :

* Collections
* Collections publiques
* Catalogues (notamment l’assistant Ajouter/Sélectionner une page)
* Modèles
* Modèles de fragments de code
* Lightbox
