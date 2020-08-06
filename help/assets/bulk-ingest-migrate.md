---
title: Installation de Feature Pack 18912 pour la migration des ressources en vrac
seo-title: Installation de Feature Pack 18912 pour la migration des ressources en vrac
description: Feature Pack 18912 vous permet soit d’assimiler des fichiers en masse par FTP, soit de migrer des fichiers de Dynamic Media Classic vers Dynamic Media dans AEM. Ce Feature Pack optionnel est fourni par le support Adobe.
seo-description: Feature Pack 18912 vous permet soit d’assimiler des fichiers en masse par FTP, soit de migrer des fichiers de Dynamic Media Classic vers Dynamic Media dans AEM. Ce Feature Pack optionnel est fourni par le support Adobe.
uuid: 316d77e3-3d61-4cf0-8955-726ee54e268c
contentOwner: rbrough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: 6198e613-a867-49a8-b9a5-a05e7889821c
translation-type: tm+mt
source-git-commit: b1603091bb05493c9cfffa6067f414f73774edb2
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 15%

---


# Installing feature pack 18912 for bulk asset migration {#installing-feature-pack}

The installation of feature pack 18912 is _optional_.

Feature Pack 18912 vous permet soit d’assimiler des fichiers en masse directement dans le mode Contenu multimédia dynamique - Scene 7 sur AEM par FTP, soit de migrer des fichiers de Contenu multimédia dynamique vers le mode Contenu multimédia dynamique - Scene7 sur AEM. Le Feature Pack est disponible à partir de [Adobe Professional Services](https://www.adobe.com/fr/experience-cloud/consulting-services.html).

>[!NOTE]
>
>Bien qu’il soit possible d’utiliser le pack de fonctionnalités pour migrer en masse des fichiers vous-même de Contenu multimédia dynamique vers Contenu multimédia dynamique - Scene 7 en mode AEM ou migrer en masse des fichiers à l’aide de la fonction FTP dans Contenu multimédia dynamique classique, l’Adobe *ne recommande pas* cette méthode en raison de la complexité de la procédure.
>
>Par conséquent, les packs de fonctionnalités de migration, comme celui-ci, sont *uniquement* pris en charge dans le cadre d’un projet de migration via [Adobe Professional Services](https://www.adobe.com/fr/experience-cloud/consulting-services.html).

Avant d’installer ce Feature Pack, vous devez d’abord créer un utilisateur de service et fournir ces informations à l’Adobe.

See also [Configuring Dynamic Media - Scene7 mode](https://helpx.adobe.com/experience-manager/6-4/assets/using/config-dms7.html).

**Pour installer Feature Pack 18912 pour la migration** de ressources en vrac,

1. In your AEM instance, navigate to **[!UICONTROL Tools > Security > Users > Create User]**. This service user must have read/write permissions to `/content/dam`.
1. In the **[!UICONTROL ID]** and **[!UICONTROL Password]** fields, enter a user name and password; for example, `FTP User`. Ce nom apparaît dans la chronologie en tant qu’utilisateur qui a créé cette ressource. Lorsqu’une ressource est transférée à partir du FTP, elle est considérée créée lorsqu’elle est transférée sur le serveur FTP et envoyée vers AEM.
1. Contactez le Support aux entreprises [Adobes pour les Experience Manager](https://helpx.adobe.com/fr/contact/enterprise-support.ec.html) afin de demander l’accès à Feature Pack 18912 pour le téléchargement. Vous aurez peut-être besoin des informations suivantes lorsque vous contactez l&#39;assistance :

   * Adresse IP du serveur de votre instance d’auteur, y compris le numéro de port (par défaut, le numéro de port est 4502).
   * AEM nom d’utilisateur et mot de passe du service de maintenance de l’étape précédente.

1. Adobe Enterprise Support for AEM fournit les informations d’identification FTP et l’accès à Feature Pack 18912.

1. Lorsque vous recevez Feature Pack 18912, installez-le.

   See [How to work with packages](/help/sites-administering/package-manager.md) for more information on using Software Distribution and packages in AEM.
