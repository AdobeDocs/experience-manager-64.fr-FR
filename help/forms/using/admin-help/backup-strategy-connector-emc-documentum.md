---
title: Stratégie de sauvegarde pour les utilisateurs et utilisatrices de Connector for EMC Documentum
seo-title: Backup strategy for Connector for EMC Documentum users
description: Découvrez comment créer une stratégie de sauvegarde pour les utilisateurs de Connector for EMC Documentum.
seo-description: Check how to create a backup strategy for Connector for EMC Documentum users.
uuid: 5d8a0476-5231-4e1d-96c4-ae3df68e09f0
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/aem_forms_backup_and_recovery
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: e83b1a59-a730-4d22-9d58-1c9c38e5d534
exl-id: 933c3903-2040-41f4-b803-4d672ce9a2dc
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '192'
ht-degree: 12%

---

# Stratégie de sauvegarde pour les utilisateurs et utilisatrices de Connector for EMC Documentum {#backup-strategy-for-connector-for-emc-documentum-users}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Si Connector for EMC Documentum est installé, outre les instructions de ce chapitre, votre stratégie de sauvegarde et de récupération doit inclure la sauvegarde (ou la récupération) de l’ordinateur sur lequel le système ECM est installé. (Voir la documentation d’ECM Documentum).

Sauvegardez votre environnement d’AEM forms à l’aide du référentiel ECM et effectuez les tâches suivantes :

* Sauvegardez AEM formulaires en suivant les instructions décrites dans ce document.
* Sauvegardez votre système ECM Documentum en suivant les instructions de la section [Sauvegarde d’EMC Documentum Content Server](/help/forms/using/admin-help/backing-recovering-emc-documentum-repository.md#back-up-the-emc-documentum-content-server).

Restaurez l’environnement d’AEM forms à l’aide du référentiel ECM et procédez comme suit :

* Restaurez votre système ECM respectif en suivant les instructions de la section [Restauration d’EMC Documentum Content Server](/help/forms/using/admin-help/backing-recovering-emc-documentum-repository.md#restore-the-emc-documentum-content-server).
* Restaurez AEM formulaires en suivant les instructions décrites dans ce document.
