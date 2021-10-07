---
title: Installation du Feature Pack 18912 pour la migration des ressources en masse
seo-title: Installing Feature Pack 18912 for bulk asset migration
description: Le Feature Pack 18912 vous permet soit d’ingérer des ressources par FTP en masse, soit de migrer des ressources de Dynamic Media Classic vers Dynamic Media dans AEM. Ce Feature Pack optionnel est fourni par le support Adobe.
seo-description: Feature pack 18912 lets you either bulk ingest assets by way of FTP, or migrate assets from Dynamic Media Classic to Dynamic Media in AEM. This optional feature pack is available from Adobe support.
uuid: 316d77e3-3d61-4cf0-8955-726ee54e268c
contentOwner: rbrough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: 6198e613-a867-49a8-b9a5-a05e7889821c
exl-id: f9bb59f6-39a5-4804-8abe-12783d4162c9
feature: Configuration
role: Admin,User
source-git-commit: 63a4304a1a10f868261eadce74a81148026390b6
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 15%

---

# Installation du Feature Pack 18912 pour la migration de ressources en masse {#installing-feature-pack}

L’installation du Feature Pack 18912 est _optionnel_.

Le Feature Pack 18912 vous permet soit d’ingérer des ressources en masse directement dans Dynamic Media - mode Scene 7 sur AEM par FTP, soit de migrer des ressources de Dynamic Media Classic vers le mode Dynamic Media - Scene7 sur AEM. Le Feature Pack est disponible à partir de [Adobe Professional Services](https://www.adobe.com/fr/experience-cloud/consulting-services.html).

>[!NOTE]
>
>Bien qu’il soit possible d’utiliser le Feature Pack pour migrer en masse des ressources vous-même de Dynamic Media Classic vers Dynamic Media - mode Scene 7 dans AEM ou migrer en masse des ressources à l’aide de la fonctionnalité FTP dans Dynamic Media Classic, Adobe ne recommande *pas* cette méthode en raison de la complexité impliquée.
>
>Par conséquent, les packs de fonctionnalités de migration, comme celui-ci, sont *uniquement* pris en charge dans le cadre d’un projet de migration via [Adobe Professional Services](https://www.adobe.com/experience-cloud/consulting-services.html).

Avant de pouvoir installer ce Feature Pack, vous devez d’abord créer un utilisateur du service et fournir ces informations à Adobe.

Voir aussi [Configuration de Dynamic Media - mode Scene7](https://helpx.adobe.com/experience-manager/6-4/assets/using/config-dms7.html).

**Pour installer le Feature Pack 18912 pour la migration** de ressources en masse,

1. Dans votre instance AEM, accédez à **[!UICONTROL Outils > Sécurité > Utilisateurs > Créer un utilisateur]**. Cet utilisateur du service doit disposer d’autorisations de lecture/écriture sur `/content/dam`.
1. Dans les champs **[!UICONTROL ID]** et **[!UICONTROL Mot de passe]**, saisissez un nom d’utilisateur et un mot de passe ; par exemple, `FTP User`. Ce nom apparaît dans la chronologie en tant qu’utilisateur qui a créé cette ressource. Lorsqu’une ressource est transférée à partir du FTP, elle est considérée créée lorsqu’elle est transférée sur le serveur FTP et envoyée vers AEM.
1. Contactez le [service clientèle Adobe pour Experience Manager](https://helpx.adobe.com/fr/contact/enterprise-support.ec.html) pour demander l’accès au Feature Pack 18912 pour le téléchargement. Vous aurez peut-être besoin des informations suivantes lorsque vous contactez l’assistance :

   * Adresse IP du serveur pour votre instance d’auteur, y compris le numéro de port (par défaut, le numéro de port est 4502).
   * AEM nom d’utilisateur et mot de passe de l’utilisateur du service de l’étape précédente.

1. Le service clientèle d’Adobe pour AEM vous fournit les informations d’identification FTP et l’accès au Feature Pack 18912.

1. Lorsque vous recevez le Feature Pack 18912, installez-le.

   Voir [Comment utiliser les packages](/help/sites-administering/package-manager.md) pour plus d’informations sur l’utilisation de Distribution logicielle et des packages dans AEM.
