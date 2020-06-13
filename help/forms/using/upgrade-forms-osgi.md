---
title: Mise à niveau vers AEM 6.4 Forms
seo-title: Mise à niveau vers AEM 6.4 Forms
description: 'Vous pouvez effectuer une mise à niveau directe à partir de AEM 6.1 Forms, AEM 6.2 Forms et LiveCycle ES4 SP1 vers AEM 6.3 Forms. '
seo-description: 'Vous pouvez effectuer une mise à niveau directe à partir de AEM 6.1 Forms, AEM 6.2 Forms et LiveCycle ES4 SP1 vers AEM 6.3 Forms. '
uuid: 1435246a-9215-4d88-b52c-59a5c329bb77
content-type: reference
products: SG_EXPERIENCEMANAGER/6.3/FORMS
topic-tags: installing
geptopics: SG_AEMFORMS/categories/jee
discoiquuid: e745033f-8015-4fae-9d82-99d35802c0a6
translation-type: tm+mt
source-git-commit: 61c9abca40007271f1fba49d3d5e3136df91938d
workflow-type: tm+mt
source-wordcount: '883'
ht-degree: 89%

---


# Mise à niveau vers AEM 6.4 Forms on OSGi {#upgrade-to-aem-forms-osgi}

Utilisez l’un des chemins de mise à niveau suivants, selon votre environnement.

## AEM 6.2 Forms ou AEM 6.3 Forms vers AEM 6.4 Forms {#upgrade-aem-forms-62-63-to-64}

Vous pouvez effectuer une mise à niveau directe à partir d’AEM 6.2 Forms ou AEM 6.3 Forms vers AEM 6.4 Forms. Procédez comme suit :

1. Mettez à niveau l’instance AEM existante vers AEM 6.4. Les étapes sont énumérées ci-dessous :

   1. Installez le dernier Service Pack et les derniers correctifs pour AEM 6.2 Forms ou AEM 6.3 Forms. Pour plus d’informations, voir :

      * [Notes de mise à jour d’AEM 6.2](https://helpx.adobe.com/fr/experience-manager/6-2/release-notes.html)
      * [Notes de mise à jour d’AEM 6.3](https://helpx.adobe.com/fr/experience-manager/6-3/release-notes.html)
      * [AEM Sustenance Hub](https://helpx.adobe.com/fr/experience-manager/aem-releases-updates.html)
   1. Préparez l’instance source pour la mise à niveau. Pour obtenir des instructions détaillées, reportez-vous à l’article [Mise à niveau vers AEM 6.4](/help/sites-deploying/upgrade.md#preparing%20the%20source%20instance).
   1. Téléchargez [AEM 6.4 QuickStart](/help/sites-deploying/deploy.md#getting%20the%20software).
   1. **(Installations Unix/Linux uniquement)** Si vous utilisez UNIX ou Linux en tant que système d’exploitation sous-jacent, ouvrez la fenêtre de terminal, accédez au dossier contenant crx-quickstart et exécutez la commande suivante :

      `chmod -R 755 ../crx-quickstart`

   1. Upgrade your AEM instance to AEM 6.3. For step by step instructions, see [Upgrading to AEM 6.4](/help/sites-deploying/upgrade.md).

      Avant de passer aux étapes suivantes, attendez que le journal &lt;crx-repository>/error.log contiennent les messages ServiceEvent REGISTERED et ServiceEvent UNREGISTERED.

      >[!NOTE]
      >
      >Une fois le serveur en marche, quelques lots AEM Forms conservent l’état d’installation. Le nombre de lots peut varier d’une installation à l’autre. Vous pouvez ignorer l’état de ces lots en toute sécurité. Les lots sont répertoriés à `https://[server]:[port]/system/console/`.


1. Installation du module complémentaire AEM Forms. Les étapes sont énumérées ci-dessous :

   1. Connectez-vous au serveur AEM en tant qu’administrateur, puis ouvrez le partage de package. L’URL par défaut du partage de package est `https://[server]:[port]/crx/packageshare`.
   1. Dans le partage de package, recherchez les **[!UICONTROL packages de modules complémentaires d’AEM 6.4 Forms]**, cliquez sur le package correspondant à votre système d’exploitation, puis sur **[!UICONTROL Télécharger]**. Lisez et acceptez l’accord de licence, puis cliquez sur **[!UICONTROL OK]**. Le téléchargement démarre. Une fois le téléchargement effectué, le mot **[!UICONTROL Téléchargé]** apparaît en regard du package.

      Alternately, you can also use the hyperlinks listed in [AEM Forms releases](https://helpx.adobe.com/fr/aem-forms/kb/aem-forms-releases.html) to manually download a package.

   1. Une fois le téléchargement terminé, cliquez sur **[!UICONTROL Téléchargé]**. Vous êtes redirigé vers le gestionnaire de package. Dans le gestionnaire de packages, recherchez le package téléchargé, puis cliquez sur **[!UICONTROL Installer]**.

      Si vous téléchargez manuellement le package à l’aide du lien direct répertorié dans les [versions d’AEM Forms](https://helpx.adobe.com/fr/aem-forms/kb/aem-forms-releases.html), ouvrez AEM Package Manager, cliquez sur **[!UICONTROL Télécharger le package]**, sélectionnez le package téléchargé et cliquez sur Télécharger. After the package is uploaded, click package name, and click **[!UICONTROL Install]**.

      >[!NOTE]
      >
      >Une fois le package installé, vous êtes invité à redémarrer l’instance AEM. **Ne redémarrez pas immédiatement le serveur.** Avant d’arrêter le serveur AEM Forms, attendez que les messages ServiceEvent REGISTERED et ServiceEvent UNREGISTERED cessent d’apparaître dans le fichier &lt;crx-repository>/error.log et que le journal soit stable. Notez également que quelques packages peuvent rester à l’état installé. Vous pouvez ignorer l’état de ces packages en toute sécurité.

   1. Arrêtez l’instance AEM et supprimez les fichiers suivants :

      * `[AEM_Installation_Directory]\[crx-quickstart]\launchpad\ext\bcmail-jdk15-1.35`
      * `[AEM_Installation_Directory]\[crx-quickstart]\launchpad\ext\bcprov-jdk15-1.35`
   1. Démarrez l’instance AEM.


1. Procédez aux activités de post-installation.

   * **Exécuter l’utilitaire de migration**

      L’utilitaire de migration rend les formulaires adaptatifs et les actions de gestion de la correspondance des versions antérieures compatibles avec les formulaires AEM 6.4. Vous pouvez télécharger l’utilitaire à partir du partage de package AEM. Pour des informations détaillées sur la configuration et l’utilisation de l’utilitaire de migration, voir [l’utilitaire de migration](/help/forms/using/migration-utility.md).

      Si vous utilisez [Exemple pour l’intégration du composant brouillons et envois](integrate-draft-submission-database.md) avec la base de données et que vous mettez à niveau à partir d’une version précédente, exécutez les requêtes SQL suivantes après avoir effectué la mise à niveau :

      ```
      UPDATE metadata m, additionalmetadatatable am
      SET m.dataType = am.value
      WHERE m.id = am.id
      AND am.key = 'dataType'
      ```

      ```
      DELETE from additionalmetadatatable
      WHERE `key` = 'dataType'
      ```

   * **(Si la mise à niveau d’AEM Forms 6.2 ou des versions antérieures uniquement) Reconfiguration de Adobe Sign**

      Si vous avez configuré Adobe Sign dans la version précédente d’AEM Forms, reconfigurez Adobe Sign à partir des services cloud AEM. Pour plus d’informations, voir [Incorporation d’Adobe Sign à AEM Forms](/help/forms/using/adobe-sign-integration-adaptive-forms.md).

   * **(Si vous effectuez une mise à niveau à partir d’AEM 6.2 Forms ou de versions précédentes uniquement) Reconfigurez l’analyse et les rapports**

      Dans AEM 6.4 Forms, la variable de trafic pour la source et l’événement de réussite pour l’impression ne sont pas disponibles. Ainsi, lorsque vous effectuez une mise à niveau à partir d’AEM 6.2 Forms ou de versions précédentes, AEM Forms cesse d’envoyer des données au serveur Adobe Analytics et les rapports d’analyse pour les formulaires adaptatifs ne sont pas disponibles. En outre, AEM 6.4 Forms introduit une variable de trafic pour la version de l’analyse de formulaire et de l’événement de réussite pour le temps passé sur un champ. Vous devez donc reconfigurer les analyses et les rapports pour votre environnement AEM Forms. Pour les étapes détaillées, voir [Configuration des analyses et des rapports](/help/forms/using/configure-analytics-forms-documents.md).

1. Vérifiez que le serveur a été mis à niveau avec succès, que toutes les données ont également été migrées avec succès, et qu’il peut fonctionner normalement.

   * **Vérifiez l’état des bundles :** assurez-vous que tous les bundles sont actifs.
   * **Vérifiez la réplication et la réplication inversée :** publiez, remplissez et envoyez quelques formulaires migrés. Vérifiez également les données envoyées.
   * **Vérifiez l’accès aux interfaces utilisateur d’administrateur et de développeur :** connectez-vous à une instance d’AEM à partir d’un compte administrateur et vérifiez que vous avez accès aux URL suivantes :

      * `https://[server]:[port]/crx/packmgr`
      * `https://[server]:[port]/crx/de`
      * `https://[server]:[port]/aem/forms.html/content/dam/formsanddocuments`

   >[!NOTE]
   Dans AEM 6.4 Forms, la structure du référentiel crx a changé. Après la mise à niveau vers AEM 6.4 Forms, utilisez les chemins d’accès modifiés pour la personnalisation que vous créez à nouveau. Pour la liste complète des chemins modifiés, voir [Restructuration du référentiel des formulaires dans AEM 6.4](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md).

## AEM 6.0 Forms et AEM 6.1 Forms vers AEM 6.4 Forms {#upgrade-aem-forms-60-61-to-64}

Le chemin de mise à niveau directe d’**AEM 6.0 Forms** et **AEM 6.1 Forms** vers AEM 6.4 Forms n’est pas disponible. Perform an intermediate [upgrade to AEM 6.2 Forms](/help/forms/using/upgrade.md) or [upgrade to AEM 6.3 Forms](/help/forms/using/upgrade.md) and then upgrade from AEM 6.2 Forms or AEM 6.3 Forms to AEM 6.4 Forms.
