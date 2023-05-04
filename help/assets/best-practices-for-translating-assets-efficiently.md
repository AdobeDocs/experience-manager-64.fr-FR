---
title: Bonnes pratiques relatives à la traduction efficace des ressources
description: Bonnes pratiques pour une gestion efficace des ressources afin de synchroniser les diverses versions traduites et de rationaliser les workflows de traduction.
contentOwner: AG
feature: Translation
role: User,Admin
exl-id: 15162b80-ddef-4ec0-9db6-36695c93ebb1
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '534'
ht-degree: 13%

---

# Bonnes pratiques relatives à la traduction des ressources efficace {#best-practices-for-translating-assets-efficiently}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Adobe Experience Manager Assets prend en charge les workflows multilingues pour traduire les fichiers binaires, les métadonnées et les balises des ressources numériques en plusieurs langues et pour gérer les ressources traduites. Pour plus d’informations, consultez [Ressources multilingues](multilingual-assets.md).

Pour une gestion efficace des ressources afin de garantir que les différentes versions traduites restent synchronisées, créez [copies de langue](preparing-assets-for-translation.md) de ressources avant d’exécuter des workflows de traduction.

Une copie de langue d’une ressource ou d’un groupe de ressources est un frère de langue (ou une version des ressources dans une langue commune) avec une hiérarchie de contenu similaire.

Chaque copie de langue est une ressource indépendante. Par conséquent, la traduction de ressources en plusieurs paramètres régionaux peut augmenter considérablement la taille du référentiel CRX. Par exemple, la traduction de ressources d’une taille combinée de 10 Go en deux langues peut augmenter la taille du référentiel d’environ 20 Go (10 Go pour chaque langue).

Les fichiers binaires des ressources occupent un espace de stockage beaucoup plus important que les métadonnées et les balises. Par conséquent, si la traduction des métadonnées et des balises est adaptée à votre objectif, omettez de traduire les binaires. Vous pouvez conserver la copie d’origine des binaires dans le référentiel pour l’associer aux métadonnées et aux balises traduites dans différents paramètres régionaux. La conservation d’une seule copie de binaires, au lieu de plusieurs versions traduites, réduit l’impact sur la taille du référentiel.

File Data Store et Amazon S3 Data Store fournissent une infrastructure de stockage qui convient le mieux à ces scénarios. Ces référentiels de stockage stockent une seule copie des binaires de ressources (y compris les rendus) qui peut être partagée par les métadonnées et les balises dans plusieurs paramètres régionaux. Par conséquent, la création de copies de langue de ressource et la traduction des métadonnées et des balises n’ont aucune incidence sur la taille du référentiel.

Vous pouvez également apporter quelques modifications de configuration à quelques workflows et à la structure d’intégration de traduction afin de rationaliser davantage le processus.

1. Utilisez l’une des méthodes suivantes :

   * [Configurer le magasin de données basé sur les fichiers](/help/sites-deploying/data-store-config.md)
   * [Configurer le magasin de données Amazon S3](/help/sites-deploying/data-store-config.md)

1. Désactivez le [Écriture différée des métadonnées de gestion des actifs numériques](/help/sites-administering/workflow-offloader.md#disable-offloading) workflow

   Comme son nom l’indique, la variable *Écriture différée des métadonnées de gestion des actifs numériques* workflow réécrit les métadonnées dans le fichier binaire. Les métadonnées étant modifiées après traduction, l’écriture différée dans le fichier binaire génère un fichier binaire différent pour une copie de langue.

   >[!NOTE]
   >
   >Désactivation de la variable *Écriture différée des métadonnées de gestion des actifs numériques* workflow désactive XMP’écriture différée des métadonnées sur les fichiers binaires de ressources. Par conséquent, les futures modifications apportées aux métadonnées ne seront plus enregistrées dans les ressources. Évaluez les conséquences avant de désactiver ce workflow.

1. Activez la variable *Définir la date de dernière modification* workflow.

   Le *Écriture différée des métadonnées de gestion des actifs numériques* workflow configure la date de dernière modification d’une ressource. Comme vous désactivez ce workflow à l’étape 2, [!DNL Experience Manager Assets] n’est plus en mesure de maintenir à jour la date de dernière modification des ressources. Par conséquent, activez la variable *Définir la date de dernière modification* pour vous assurer que les dates de dernière modification des ressources sont à jour. Les ressources dont les dates de dernière modification sont obsolètes peuvent entraîner des erreurs.

1. [Configuration de la structure d’intégration de traduction](/help/sites-administering/tc-tic.md) pour arrêter la traduction des fichiers binaires de ressources. Désélectionnez l’option &quot;Traduire les ressources&quot; sous l’onglet Ressources pour arrêter la traduction des fichiers binaires des ressources.
1. Traduire les métadonnées/balises de ressources à l’aide de [Workflows de ressources multilingues](multilingual-assets.md).
