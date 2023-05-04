---
title: Configuration de la solution Correspondence Management
seo-title: Configuring a Correspondence Management solution
description: Découvrez comment définir une URL d’instance d’auteur pour la restauration de la version de l’instance d’auteur et définir l’URL de l’instance de publication pour le gestionnaire d’activation de l’instance publique.
seo-description: Learn how to define an author instance URL for the author instance version restore and define the Publish instance URL for public instance activation manager.
uuid: 76b25004-fe47-44d7-9bed-7c0fd963306b
topic-tags: correspondence-management
content-type: reference
products: SG_EXPERIENCEMANAGER/6.3/FORMS
discoiquuid: 186ca75c-638b-4057-826e-cd5d56aa0397
feature: Correspondence Management
exl-id: a062957d-a526-4c4b-bbc5-0cda8ab007a3
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 35%

---

# Configuration de la solution Correspondence Management {#configuring-a-correspondence-management-solution}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

## Définition de l’URL de l’instance d’auteur pour VersionRestoreManagerImpl {#defining-author-instance-url-for-versionrestoremanagerimpl}

Suivez les étapes ci-dessous pour définir une URL d’instance de création pour la restauration de version de l’instance de création :

1. Accédez à *https://:&lt;PublishHost>:&lt;PublishPort>/lc/system/console/configMgr*. Connectez-vous avec les informations d’identification d’utilisateur de la console de gestion OSGi. Les informations d’identification d’administrateur par défaut sont/admin.
1. Recherchez l’icône **[!UICONTROL Modifier]** située en regard du paramètre **[!UICONTROL com.adobe.livecycle.content.activate.impl.VersionRestoreManagerImpl.name]** et cliquez dessus.
1. Dans le champ **[!UICONTROL URL d’auteur VersionRestoreManager]**, spécifiez l’URL de l’instance d’auteur VersionRestoreManager.

   **Chaîne d’URL** :

   `https://<hostname>:<port>:/libs/fd/fdm/content/crud/lc.content.remote.activate.VersionRestoreManager`

   >[!NOTE]
   >
   >S’il existe plusieurs instances d’auteur (en cluster) derrière un équilibreur de charge, spécifiez l’URL de l’équilibreur de charge dans le champ **[!UICONTROL URL d’auteur VersionRestoreManager]**.

1. Cliquez sur **[!UICONTROL Enregistrer]**.

## Définition de l’URL de l’instance de publication pour ActivationManagerImpl (gestionnaire d’activation de l’instance publique) {#defining-the-publish-instance-url-for-activationmanagerimpl-public-instance-activation-manager}

Pour définir l’URL de l’instance de publication pour le gestionnaire d’activation de l’instance publique, procédez comme suit :

1. Accédez à *https://:&lt;authorHost>:&lt;authorPort>/lc/system/console/configMgr*. Connectez-vous avec les informations d’identification d’utilisateur de la console de gestion OSGi. Les informations d’identification d’administrateur par défaut sont/admin.
1. Recherchez et cliquez sur le bouton **[!UICONTROL Modifier]** en regard de l’icône **[!UICONTROL com.adobe.livecycle.content.activate.impl.ActivationManagerImpl.name]** .
1. Dans le **[!UICONTROL URL de publication ActivationManager]** , spécifiez l’URL d’accès à l’instance de publication ActivationManager. Vous pouvez fournir les URL suivantes.

   * **URL de l’équilibreur de charge (recommandée)**: Indiquez l’URL de l’équilibreur de charge, si un serveur web agit comme équilibreur de charge devant la batterie de publication (plusieurs instances de publication non clusterisées).
   * **URL de l’instance de publication**: Indiquez toute URL d’instance de publication. Si vous disposez d’une instance de publication unique ou si le serveur Web qui précède la ferme de publication n’est pas accessible à partir de l’environnement de création en raison de restrictions. Si l’instance de publication spécifiée est en panne, un mécanisme de secours est disponible du côté auteur.
   * **Chaîne d’URL** :

      `https://<hostname>:<port>:/libs/fd/fdm/content/crud/lc.content.remote.activate.activationManager`

1. Cliquez sur **[!UICONTROL Enregistrer]**.

Pour plus d’informations sur la configuration de Correspondence Management, voir [Propriétés de configuration de Correspondence Management](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/previous-updates/aem-previous-versions.html?lang=fr).
