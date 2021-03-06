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
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '311'
ht-degree: 91%

---

# Configuration de la solution Correspondence Management {#configuring-a-correspondence-management-solution}

## Définition de l’URL de l’instance d’auteur pour VersionRestoreManagerImpl {#defining-author-instance-url-for-versionrestoremanagerimpl}

Procédez aux étapes suivantes pour définir une URL d’instance d’auteur pour la restauration de la version de l’instance d’auteur :

1. Accédez à *https://:&lt;PublishHost>:&lt;PublishPort>/lc/system/console/configMgr*. Connectez-vous avec les informations d’identification d’utilisateur de la console de gestion OSGi. Les informations d’identification d’administrateur par défaut sont/admin.
1. Recherchez l’icône **[!UICONTROL Modifier]** située en regard du paramètre **[!UICONTROL com.adobe.livecycle.content.activate.impl.VersionRestoreManagerImpl.name]** et cliquez dessus.
1. Dans le champ **[!UICONTROL URL d’auteur VersionRestoreManager]**, spécifiez l’URL de l’instance d’auteur VersionRestoreManager.

   **Chaîne d’URL** :

   `https://<hostname>:<port>:/libs/fd/fdm/content/crud/lc.content.remote.activate.VersionRestoreManager`

   >[!NOTE]
   >
   >S’il existe plusieurs instances d’auteur (en cluster) derrière un équilibreur de charge, spécifiez l’URL de l’équilibreur de charge dans le champ **[!UICONTROL URL d’auteur VersionRestoreManager]**.

1. Cliquez sur **[!UICONTROL Enregistrer]**.

## Définition de l’URL de l’instance de publication pour ActivationManagerImpl (gestionnaire d’activation de l’instance de publication) {#defining-the-publish-instance-url-for-activationmanagerimpl-public-instance-activation-manager}

Suivez ces étapes pour définir l’URL de l’instance de publication pour le gestionnaire d’activation de l’instance de publication :

1. Accédez à *https://:&lt;authorHost>:&lt;authorPort>/lc/system/console/configMgr*. Connectez-vous avec les informations d’identification d’utilisateur de la console de gestion OSGi. Les informations d’identification d’administrateur par défaut sont/admin.
1. Recherchez l’icône **[!UICONTROL Éditer]** située en regard du paramètre **[!UICONTROL com.adobe.livecycle.content.activate.impl.ActivationManagerImpl.name]** et cliquez dessus.
1. Dans le champ **[!UICONTROL ActivationManager Publish URL]** (URL de publication ActivationManager), spécifiez l’URL pour accéder à l’instance de publication ActivationManager. Vous pouvez fournir les URL suivantes.

   * **URL d’équilibreur de charge (recommandée)** : saisissez l’URL de l’équilibreur de charge, si vous avez un serveur Web agissant en tant qu’équilibreur de charge devant la batterie de publication (plusieurs instances de publication non clusterisées).
   * **URL d’instance de publication** : saisissez toute URL d’instance de publication, si vous avez une instance de publication unique ou si le serveur Web donnant la batterie de publication n’est pas accessible à partir de l’environnement d’auteur en raison de restrictions. Dans le cas où l’instance de publication indiquée n’est pas disponible, un mécanisme de secours est disponible pour traiter le côté auteur.
   * **Chaîne d’URL** :

      `https://<hostname>:<port>:/libs/fd/fdm/content/crud/lc.content.remote.activate.activationManager`

1. Cliquez sur **[!UICONTROL Enregistrer]**.

Pour en savoir plus sur la configuration de Correspondence Management, consultez [Propriétés de configuration de Correspondence Management](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/previous-updates/aem-previous-versions.html?lang=fr).
