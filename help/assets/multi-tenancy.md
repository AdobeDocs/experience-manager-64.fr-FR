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


# Multi-tenancy for collections, snippets, and snippet templates {#multi-tenancy-for-collections-snippets-and-snippet-templates}

La fonction multiclient permet de séparer du contenu dans CRX en fonction du préfixe et de l’identifiant d’organisation, de sorte à protéger le contenu contre tout accès non autorisé par les utilisateurs d’autres organisations.

Adobe Experience Manager (AEM) Assets stocke les données de chaque organisation à un chemin d’accès différent. Chaque chemin d’accès spécifique à l’organisation est identifié par le préfixe et l’ID d’organisation.inclus dans l’emplacement traditionnel où différents types de ressources sont stockés dans CRX.

For example, if you create a folder named `Demo`, AEM assets by default stores the folder at `../content/dam/Demo` location in CRX. La fonction de multitenanciation étant activée, vous pouvez stocker les données à `../content/dam/<organization prefix>/<organization id>Demo`l’emplacement suivant :

For example, for Adobe Marketing Cloud users of AEM Assets (on-demand) that are assigned to `aodpremium` organization, you can use the multi-tenancy feature to configure the following path to `../content/dam/mac/aodpremiumDemo`, segregate the content. Dans cet exemple, `mac` est le préfixe d’organisation et `aodpremium` l’ID d’organisation.

En fonction de l’organisation et de l’identifiant de l’utilisateur, ce chemin d’accès s’affiche dans l’interface d’AEM Assets et dans différents assistants, notamment les assistants Déplacement et Création de fragment de code, pour appliquer la séparation.

La fonction de tenanciation multiple vous permet de segmenter les types d’actifs et de composants suivants :

* Collections
* Collections publiques
* Catalogues (y compris l’assistant Ajouter/Sélectionner une page)
* Modèles
* Modèles de fragments de code
* Lightbox
