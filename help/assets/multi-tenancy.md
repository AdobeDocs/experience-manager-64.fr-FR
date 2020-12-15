---
title: Multiplénitude pour les collections, les fragments et les modèles de fragments de code
description: Séparez le contenu du référentiel CRX en fonction de l’entreprise cliente afin d’empêcher tout accès non autorisé.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0d70a672a2944e2c03b54beb3b5f734136792ab1
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 34%

---


# Multitenancy pour les collections, les extraits de code et les modèles de fragment de code {#multi-tenancy-for-collections-snippets-and-snippet-templates}

La fonction multiclient permet de séparer du contenu dans CRX en fonction du préfixe et de l’identifiant d’organisation, de sorte à protéger le contenu contre tout accès non autorisé par les utilisateurs d’autres organisations.

Adobe Experience Manager (AEM) Assets stocke les données de chaque organisation à un chemin d’accès différent. Chaque chemin d’accès spécifique à l’organisation est identifié par le préfixe et l’ID d’organisation de l’organisation.
qui est inclus dans l’emplacement traditionnel où différents types de ressources sont stockés dans CRX.

Par exemple, si vous créez un dossier nommé `Demo`, AEM ressources stockent par défaut le dossier à l’emplacement `../content/dam/Demo` dans CRX. La fonction de multitenanciation étant activée, vous pouvez stocker les données à `../content/dam/<organization prefix>/<organization id>Demo`.

Par exemple, pour les utilisateurs Adobe Marketing Cloud de AEM Assets (à la demande) affectés à une organisation `aodpremium`, vous pouvez utiliser la fonction de multilocation pour configurer le chemin d’accès suivant vers `../content/dam/mac/aodpremiumDemo`, en séparant le contenu. Dans cet exemple, `mac` correspond au préfixe d&#39;organisation et `aodpremium` à l&#39;ID d&#39;organisation.

En fonction de l’organisation et de l’identifiant de l’utilisateur, ce chemin d’accès s’affiche dans l’interface d’AEM Assets et dans différents assistants, notamment les assistants Déplacement et Création de fragment de code, pour appliquer la séparation.

La fonction de tenanciation multiple vous permet de segmenter les types d’actifs et de composants suivants :

* Collections
* Collections publiques
* Catalogues (y compris l’assistant Ajouter/Sélectionner une page)
* Modèles
* Modèles de fragments de code
* Lightbox
