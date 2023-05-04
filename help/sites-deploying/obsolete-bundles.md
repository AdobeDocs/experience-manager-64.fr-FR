---
title: Liste des lots obsolètes désinstallés après la mise à niveau
seo-title: List of Obsolete Bundles Uninstalled After the Upgrade
description: Liste répertoriant les lots automatiquement désinstallées lors de la mise à niveau vers AEM 6.3.
seo-description: A list detailing the bundles that are automatically uninstalled when upgrading to AEM 6.3.
uuid: b015e857-31c1-4982-b71c-f3201b49ec8e
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: upgrading
content-type: reference
discoiquuid: 797a6f3b-d2a8-4835-81ab-a1602677417f
feature: Upgrading
exl-id: 0f075a01-f286-4e16-9061-4e902c553eb9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '203'
ht-degree: 47%

---

# Liste des lots obsolètes désinstallés après la mise à niveau{#list-of-obsolete-bundles-uninstalled-after-the-upgrade}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

>[!NOTE]
>
>Si votre code repose sur ces lots, contactez l’assistance technique d’Adobe et demandez un package de compatibilité pour la zone concernée.

Lorsque vous effectuez la mise à niveau vers AEM 6.3, les lots suivants sont automatiquement désinstallées, en fonction de la version d’AEM à partir de laquelle la mise à niveau a été effectuée :

**AEM 6.1 :**

* org.eclipse.equinox.region, version 1.1.0.v20120522-1841, Principal
* org.apache.sling.installer.factory.subsystems, version 1.0.0, Active
* org.apache.aries.subsystem.core, version 1.2.0, Principal
* org.apache.aries.subsystem.api, version 1.1.0, Principal
* org.apache.felix.resolver, version 1.0.0, Principal
* org.osgi.service.subsystem.region.context.0, version 1.0.0, Principal
* com.adobe.cq.cq-creativecloud-cloudims, version 0.0.10, Principal
* com.adobe.cq.cq-creativecloud-commons, version 0.0.8, Principal
* com.adobe.cq.cq-creativecloud-filesync, version 0.0.12, installé
* com.adobe.cq.cq-creativecloud-storage, version 0.0.8, installé
* biz.Quate.bndlib, version 1.43.0, Principal
* com.day.cq.dam.commons.nekohtml, version 0.9.5, Principal
* com.day.cq.mcm.cq-mcm-silverpop-integration, version 1.2.2. Active

**AEM 6.0 :**

* org.apache.sling.discovery.impl, version 1.1.6. Active
* com.adobe.granite.installer.patch, version 0.4.0, Principal
* biz.Quate.bndlib, version 1.43.0, Principal
* com.day.cq.cq-jobs-core, version 5.4.0, Principal
* com.day.cq.cq-opensocial, version 5.7.2, Principal
* com.day.cq.cq-pinauthhandler, version 1.1.2, Principal
* com.day.cq.dam.commons.nekohtml, version 0.9.5, Principal
* com.day.cq.mcm.cq-mcm-silverpop-integration, version 1.1.6. Active
* com.day.cq.wcm.cq-wcm-mobile-phonegap-build-integration, version 5.7.18, Principal

**CQ 5.6.1 :**

* biz.Quate.bndlib, version 1.43.0, Principal
* com.day.cq.cq-pinauthhandler, version 1.0.0, Principal
* com.day.cq.dam.commons.nekohtml, version 0.9.5, Principal
* com.day.crx.crxde-support, version 2.3.14, Installé
* com.day.cq.mcm.cq-mcm-silverpop-integration, version 1.0.2. Active

**CQ 5.6.0 :**

* com.day.cq.cq-pinauthhandler, version 1.0.0, Principal
* com.day.cq.dam.commons.nekohtml, version 0.9.5, Principal
* com.day.crx.crxde-support, version 2.3.14, Installé
