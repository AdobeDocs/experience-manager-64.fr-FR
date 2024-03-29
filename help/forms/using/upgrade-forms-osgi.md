---
title: Mise à niveau vers AEM 6.4 Forms
seo-title: Upgrade to AEM 6.4 Forms
description: Vous pouvez effectuer une mise à niveau directe à partir d’AEM 6.1 Forms, AEM 6.2 Forms et LiveCycle ES4 SP1 vers AEM 6.3 Forms.
seo-description: You can perform a direct upgrade from AEM 6.1 Forms, AEM 6.2 Forms, and LiveCycle ES4 SP1 to AEM 6.3 Forms.
uuid: 1435246a-9215-4d88-b52c-59a5c329bb77
content-type: reference
products: SG_EXPERIENCEMANAGER/6.3/FORMS
topic-tags: installing
geptopics: SG_AEMFORMS/categories/jee
discoiquuid: e745033f-8015-4fae-9d82-99d35802c0a6
role: Admin
exl-id: 183ed9c6-6a9a-4932-8405-5ae2c6fac1ec
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '861'
ht-degree: 58%

---

# Mise à niveau vers AEM 6.4 Forms on OSGi {#upgrade-to-aem-forms-osgi}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Utilisez l’un des chemins de mise à niveau suivants, en fonction de votre environnement.

## AEM 6.2 Forms ou AEM 6.3 Forms > Forms 6.4 {#upgrade-aem-forms-62-63-to-64}

Vous pouvez effectuer une mise à niveau directe à partir d’AEM 6.2 Forms ou AEM 6.3 Forms vers AEM 6.4 Forms. Procédez comme suit :

1. Mettez à niveau l’instance AEM existante vers AEM 6.4. Les étapes sont énumérées ci-dessous :

   1. Installez le dernier Service Pack et les derniers correctifs pour AEM 6.2 Forms ou AEM 6.3 Forms. Pour plus d’informations, voir :

      * [Notes de mise à jour d’AEM 6.2](https://helpx.adobe.com/fr/experience-manager/6-2/release-notes.html)
      * [Notes de mise à jour d’AEM 6.3](https://helpx.adobe.com/fr/experience-manager/6-3/release-notes.html)
      * [Hub de subsistance AEM](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/aem-releases-updates.html?lang=fr)
   1. Préparez l’instance source pour la mise à niveau. Pour obtenir des instructions détaillées, reportez-vous à l’article [Mise à niveau vers AEM 6.4](/help/sites-deploying/upgrade.md#preparing%20the%20source%20instance).
   1. Téléchargez [AEM 6.4 QuickStart](/help/sites-deploying/deploy.md#getting%20the%20software).
   1. **(Installations Unix/Linux uniquement)** Si vous utilisez UNIX ou Linux en tant que système d’exploitation sous-jacent, ouvrez la fenêtre de terminal, accédez au dossier contenant crx-quickstart et exécutez la commande suivante :

      `chmod -R 755 ../crx-quickstart`

   1. Mettez à niveau votre instance AEM vers AEM 6.4. Pour obtenir des instructions étape par étape, voir [Mettre à niveau vers AEM 6.5](/help/sites-deploying/upgrade.md).

      Avant de passer aux étapes suivantes, attendez que le journal &lt;crx-repository>/error.log contiennent les messages ServiceEvent REGISTERED et ServiceEvent UNREGISTERED.

      >[!NOTE]
      >
      >Une fois le serveur en cours d’exécution, quelques lots AEM Forms restent à l’état d’installation. Le nombre de lots peut varier pour chaque installation. Vous pouvez ignorer l’état de ces lots en toute sécurité. Les lots sont répertoriés à l’adresse `https://[server]:[port]/system/console/`.


1. Installation du package complémentaire AEM Forms. Les étapes sont répertoriées ci-dessous :

   1. Ouvrez la [Distribution de logiciels](https://experience.adobe.com/downloads). Vous avez besoin d’un Adobe ID pour vous connecter à la Distribution de logiciels.
   1. Appuyez sur **[!UICONTROL Adobe Experience Manager]** disponible dans le menu d’en-tête.
   1. Dans le **[!UICONTROL Filtres]** section :
      1. Sélectionner **[!UICONTROL Forms]** de la **[!UICONTROL Solution]** liste déroulante.
      1. Sélectionnez la version et le type du package. Vous pouvez également utiliser l’option **[!UICONTROL Rechercher des téléchargements]** pour filtrer les résultats.
   1. Appuyez sur le nom de package applicable à votre système d’exploitation, sélectionnez **[!UICONTROL Accepter les conditions du CLUF]**, puis appuyez sur **[!UICONTROL Télécharger]**.
   1. Ouvrez [Package Manager](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html?lang=fr) et cliquez sur **[!UICONTROL Télécharger le package]** pour télécharger le package.
   1. Sélectionnez le package et cliquez sur **[!UICONTROL Installer]**.

      Vous pouvez également télécharger le package via le lien direct répertorié dans l’article [Versions d’AEM Forms](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=fr).

      >[!NOTE]
      >
      >Une fois le package installé, vous êtes invité à redémarrer l’instance AEM. **N’arrêtez pas le serveur immédiatement.** Avant d’arrêter le serveur AEM Forms, attendez que les messages ServiceEvent REGISTERED et ServiceEvent UNREGISTERED cessent d’apparaître dans le fichier &lt;crx-repository>/error.log et que le journal soit stable. Notez également que quelques packages peuvent rester à l’état installé. Vous pouvez ignorer l’état de ces modules en toute sécurité.

   1. Arrêtez l’instance AEM et supprimez les fichiers suivants :

      * `[AEM_Installation_Directory]\[crx-quickstart]\launchpad\ext\bcmail-jdk15-1.35`
      * `[AEM_Installation_Directory]\[crx-quickstart]\launchpad\ext\bcprov-jdk15-1.35`
   1. Démarrez l’instance AEM.


1. Exécutez les activités de post-installation.

   * **Exécuter l’utilitaire de migration**

      L’utilitaire de migration rend les formulaires adaptatifs et les actions de gestion de la correspondance des versions antérieures compatibles avec les formulaires AEM 6.4. Vous pouvez télécharger l’utilitaire à partir de la Distribution de logiciels AEM. Pour des informations détaillées sur la configuration et l’utilisation de l’utilitaire de migration, voir [l’utilitaire de migration](/help/forms/using/migration-utility.md).

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

   * **(Si vous effectuez une mise à niveau à partir d’AEM 6.2 Forms ou de versions précédentes uniquement) Reconfigurez Acrobat Sign**

      Si Acrobat Sign était configuré dans la version précédente d’AEM Forms, reconfigurez Acrobat Sign à partir des services cloud AEM. Pour plus d’informations, voir [Intégration d’Acrobat Sign à AEM Forms](/help/forms/using/adobe-sign-integration-adaptive-forms.md).

   * **(Si vous effectuez une mise à niveau à partir d’AEM 6.2 Forms ou de versions précédentes uniquement) Reconfigurez l’analyse et les rapports**

      Dans AEM Forms 6.4, la variable de trafic pour la source et l’événement de succès pour l’impression ne sont pas disponibles. Ainsi, lorsque vous effectuez une mise à niveau à partir d’AEM 6.2 Forms ou de versions précédentes, AEM Forms cesse d’envoyer des données au serveur Adobe Analytics et les rapports d’analyse pour les formulaires adaptatifs ne sont pas disponibles. En outre, AEM 6.4 Forms introduit une variable de trafic pour la version de l’analyse de formulaire et de l’événement de succès pour la durée de consultation d’un champ. Par conséquent, reconfigurez les analyses et les rapports pour votre environnement AEM Forms. Pour obtenir des instructions détaillées, voir [Configuration des analyses et des rapports](/help/forms/using/configure-analytics-forms-documents.md).

1. Vérifiez que le serveur a été mis à niveau avec succès, que toutes les données ont également été migrées avec succès, et qu’il peut fonctionner normalement.

   * **Vérifiez l’état des bundles :** assurez-vous que tous les bundles sont actifs.
   * **Vérifiez la réplication et la réplication inverse :** Publiez, remplissez et envoyez quelques formulaires migrés. Vérifiez également les données envoyées.
   * **Vérifiez l’accès aux interfaces utilisateur administrateur et développeur :** Connectez-vous à l’instance AEM à partir d’un compte administrateur et vérifiez que vous avez accès aux URL suivantes :

      * `https://[server]:[port]/crx/packmgr`
      * `https://[server]:[port]/crx/de`
      * `https://[server]:[port]/aem/forms.html/content/dam/formsanddocuments`

   >[!NOTE]
   Dans AEM 6.4 Forms, la structure du référentiel crx a changé. Après la mise à niveau vers AEM 6.4 forms, utilisez les chemins modifiés pour la personnalisation que vous créez à nouveau. Pour obtenir la liste complète des chemins modifiés, voir [Restructuration des référentiels Forms dans AEM 6.4](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md).

## AEM 6.0 Forms et AEM 6.1 Forms > Forms 6.4 {#upgrade-aem-forms-60-61-to-64}

Chemin de mise à niveau directe à partir de **Forms AEM 6.0** et **AEM 6.1 Forms** vers AEM 6.4 Forms n’est pas disponible. Effectuer une opération intermédiaire [Mise à niveau vers AEM 6.2 Forms](/help/forms/using/upgrade.md) ou [Mise à niveau vers AEM 6.3 Forms](/help/forms/using/upgrade.md) puis effectuez une mise à niveau d’AEM 6.2 Forms ou d’AEM 6.3 Forms vers la version 6.4 Forms.
