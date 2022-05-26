---
title: Incorporation d’Adobe Sign à AEM Forms
seo-title: Integrate Adobe Sign with AEM Forms
description: Découvrez comment configurer Adobe Sign pour AEM Forms
seo-description: Learn how to configure Adobe Sign for AEM Forms
uuid: 9efd5c44-3d87-4c56-aa6c-e65397fff243
contentOwner: sashanka
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: 7d494c2e-d457-4d52-89be-a77ffa07eb88
feature: Adaptive Forms, Adobe Sign
exl-id: e7c27623-a889-4bd5-bfff-cfe513cd1a35
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '967'
ht-degree: 92%

---

# Incorporation d’Adobe Sign à AEM Forms {#integrate-adobe-sign-with-aem-forms}

Adobe Sign autorise les processus de signature électronique pour les formulaires adaptatifs. Les signatures électroniques améliorent les processus de traitement des documents pour les services juridiques, commercial, des ressources humaines, et bien d’autres domaines.

Dans un scénario Adobe Sign et de formulaires adaptatifs standard, un utilisateur remplit un formulaire adaptatif pour effectuer une **demande de service**. Par exemple, un formulaire de demande de carte de paiement et d’allocation. Lorsqu’un utilisateur remplit, envoie et signe le formulaire de demande, le formulaire est envoyé au prestataire de services qui décidera des actions à entreprise. Le prestataire de services passe en revue la demande et utilise Adobe Sign pour marquer la demande approuvée. Pour activer les processus de signature électronique similaires, vous pouvez intégrer Adobe Sign à AEM Forms.

Pour utiliser Adobe Sign avec AEM Forms, configurez Adobe Sign dans AEM Cloud Services :

## Prérequis {#prerequisites}

Vous avez besoin de ce qui suit pour intégrer Adobe Sign à AEM Forms :

* Un compte de développeur [Adobe Sign actif.](https://acrobat.adobe.com/fr/fr/why-adobe/developer-form.html)
* Un serveur AEM Forms [SSL](/help/sites-administering/ssl-by-default.md).
* Une [application API Adobe Sign](https://www.adobe.io/apis/documentcloud/sign/docs.html#!adobedocs/adobe-sign/master/gstarted/create_app.md).
* Informations d’identification (ID client et secret client) de l’application API Adobe Sign.
* Lors de la reconfiguration, supprimez la configuration Adobe Sign existante des instances d’auteur et de publication.
* Une [crypto-clé identique](/help/sites-administering/security-checklist.md#make-sure-you-properly-replicate-encryption-keys-when-needed) pour les instances d’auteur et de publication.

## Configurer Adobe Sign avec AEM Forms {#configure-adobe-sign-with-aem-forms}

Une fois les conditions préalables en place, procédez comme suit pour configurer Adobe Sign avec AEM Forms sur l’instance d’auteur :

1. Dans l’instance d’auteur AEM Forms, accédez à **Outils** ![hammer](assets/hammer.png) > **Général** > **Navigateur de configuration**.
   * Pour plus d’informations, consultez la documentation relative au [](/help/sites-administering/configurations.md)Navigateur de configuration.
1. Sur la page du **[!UICONTROL navigateur de configuration]**, appuyez sur **[!UICONTROL Créer]**.
1. Dans la boîte de dialogue **[!UICONTROL Créer une configuration]**, indiquez un **[!UICONTROL titre]** pour la configuration, activez **[!UICONTROL Configurations cloud]** et appuyez sur **[!UICONTROL Créer]**. Un conteneur de configuration pour les services cloud est créé.
1. Accédez à **Outils** ![marteau](assets/hammer.png) > **Cloud Services** > **Adobe Sign** et sélectionnez le conteneur de configuration que vous avez créé à l’étape précédente.

   >[!NOTE]
   >
   >Vous pouvez exécuter les étapes 1 à 4 pour créer un conteneur de configuration et créer une configuration Adobe Sign dans le conteneur ou utiliser le conteneur existant `global` dossier dans **Outils** ![marteau](assets/hammer.png) > **Cloud Services** > **Adobe Sign**. Si vous créez la configuration dans le nouveau conteneur de configuration, veillez à spécifier le nom du conteneur dans le champ **[!UICONTROL Conteneur de configuration]** lorsque vous créez un formulaire adaptatif.

   >[!NOTE]
   Vérifiez que l’URL de la page de configuration des services cloud commence par **HTTPS**. Si ce n’est pas le cas, [activez SSL](/help/sites-administering/ssl-by-default.md) pour le serveur AEM Forms.

1. Sur la page de configuration, appuyez sur . **[!UICONTROL Créer]** pour créer une configuration Adobe Sign dans AEM Forms.
1. Dans l’onglet **[!UICONTROL Généralités]** de la page **[!UICONTROL Créer une configuration Adobe Sign]**, spécifiez un **Nom** de configuration et appuyez sur **Suivant**. Vous avez la possibilité d’indiquer un titre et de rechercher et de sélectionner une vignette pour la configuration.

1. Copiez l’URL dans la fenêtre active du navigateur dans un bloc-notes. Vous en avez besoin pour configurer l’application Adobe Sign avec AEM Forms.

1. Configurez les paramètres OAuth pour l’application Adobe Sign :

   1. Ouvrez une fenêtre de navigateur et connectez-vous au compte de développeur Adobe Sign.
   1. Sélectionnez l’application configurée pour AEM Forms, puis appuyez sur Configurer OAuth pour l’application.
   1. Dans la zone **URL de redirection**, ajoutez l’URL HTTPS copiée à l’étape précédente et cliquez sur **Enregistrer**.
   1. Activez les paramètres OAuth suivants pour l’application Adobe Sign et cliquez sur **Enregistrer**.
   * aggrement_read
   * aggrement_write
   * aggrement_send
   * widget_write
   * workflow_read

   Pour obtenir des informations détaillées sur la configuration des paramètres OAuth pour une application Adobe Sign et l’obtention des clés, voir [Configurer les paramètres oAuth pour la documentation](https://www.adobe.io/apis/documentcloud/sign/docs.html#!adobedocs/adobe-sign/master/gstarted/configure_oauth.md) dans la documentation du développeur.

   ![Configuration OAuth](assets/oauthconfig_new.png)

1. Revenez à la page **Créer une configuration Adobe Sign**. Dans l’onglet **[!UICONTROL Paramètres]**, le champ **[!UICONTROL URL OAuth]** indique l’URL suivante par défaut :

   `https://secure.na1.echosign.com/public/oauth`

   où :

   **na1** fait référence au partitionnement de base de données par défaut.

   Vous pouvez modifier la valeur du partitionnement de base de données. Redémarrez le serveur pour pouvoir utiliser la nouvelle valeur pour le partitionnement de base de données.

1. Spécifiez les valeurs **ID client** (également appelé ID d’application) et **clé secrète client**. Sélectionnez l’option **Activer Adobe Sign pour les pièces jointes également** pour ajouter les fichiers joints à un formulaire adaptatif au document Adobe Sign correspondant envoyé à des fins de signature.

   Appuyez sur **[!UICONTROL Se connecter à Adobe Sign]**. Lorsque vous êtes invité à fournir vos informations d’identification, indiquez le nom d’utilisateur et le mot de passe du compte utilisé lors de la création de l’application Adobe Sign.

   Appuyez sur **[!UICONTROL Créer]** pour créer la configuration Adobe Sign.

1. Ouvrez la console Web AEM. L’URL est `https://'[server]:[port]'/system/console/configMgr`
1. Ouvrez le **service de configuration commun aux formulaires.**
1. Dans le champ **Autoriser**, **sélectionnez** Tous les utilisateurs : tous les utilisateurs, anonymes ou connectés, peuvent afficher un aperçu des pièces jointes, vérifier et signer des formulaires, puis cliquez sur **Enregistrer.** L’instance d’auteur est configurée pour utiliser Adobe Sign.
1. Utilisez la [réplication](/help/sites-deploying/replication.md) pour créer une configuration identique sur les instances de publication correspondantes.

Désormais, Adobe Sign est intégré à AEM Forms et prêt à être utilisé dans les formulaires adaptatifs. Pour [utiliser le service Adobe Sign dans un formulaire adaptatif](../../forms/using/working-with-adobe-sign.md#configure-adobe-sign-for-an-adaptive-form), spécifiez le conteneur de configuration créé ci-dessus dans les propriétés du formulaire adaptatif.

## Configurer le planificateur Adobe Sign pour synchroniser l’état de signature {#configure-adobe-sign-scheduler-to-sync-the-signing-status}

Un formulaire adaptatif Adobe Sign est envoyé uniquement après que tous les signataires ont terminé le processus de signature. Par défaut, les services du planificateur Adobe Sign doivent vérifier (interroger) la réponse du signataire toutes les 24 heures. Vous pouvez modifier l’intervalle par défaut pour votre environnement. Procédez comme suit pour modifier l’intervalle par défaut :

1. Connectez-vous au serveur AEM Forms avec les informations d’identification d’administrateur et accédez à **Outils**> **Opérations**> **Console Web**.

   Vous pouvez également ouvrir l’URL suivante dans une fenêtre de navigateur :
   `https://[localhost]:'port'/system/console/configMgr`

1. Recherchez et ouvrez l’option **Service de configuration Adobe Sign**. Spécifiez une [expression cron](https://en.wikipedia.org/wiki/Cron#CRON_expression) dans le champ **Expression du planificateur de mise à jour de l’état** et cliquez sur **Enregistrer**. Par exemple, pour exécuter le service de configuration tous les jours à minuit, indiquez `0 0 0 1/1 * ? *` dans le champ **Expression du planificateur de mise à jour de l’état**.

L’intervalle par défaut pour synchroniser l’état d’Adobe Sign est désormais modifié.

## Articles connexes {#related-articles}

* [Utilisation d’Adobe Sign dans un formulaire adaptatif](../../forms/using/working-with-adobe-sign.md)
* [Utiliser Adobe Sign avec AEM Forms (vidéo)](https://helpx.adobe.com/fr/experience-manager/kt/forms/using/adobe-sign-integration-feature-video.html)
* [Incorporation d’Adobe Sign à AEM Forms](../../forms/using/adobe-sign-integration-adaptive-forms.md)
