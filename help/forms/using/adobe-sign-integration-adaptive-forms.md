---
title: Intégration d’Acrobat Sign à AEM Forms
seo-title: Integrate Acrobat Sign with AEM Forms
description: Découvrez comment configurer Acrobat Sign pour AEM Forms
seo-description: Learn how to configure Acrobat Sign for AEM Forms
uuid: 9efd5c44-3d87-4c56-aa6c-e65397fff243
contentOwner: sashanka
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: 7d494c2e-d457-4d52-89be-a77ffa07eb88
feature: Adaptive Forms, Acrobat Sign
exl-id: e7c27623-a889-4bd5-bfff-cfe513cd1a35
source-git-commit: f8b19b6723d333e76fed111b9fde376b3bb13a1d
workflow-type: tm+mt
source-wordcount: '967'
ht-degree: 47%

---

# Intégration d’Acrobat Sign à AEM Forms {#integrate-adobe-sign-with-aem-forms}

Acrobat Sign active les processus de signature électronique pour les formulaires adaptatifs. Les signatures électroniques améliorent les processus de traitement des documents pour les services juridiques, commercial, des ressources humaines, et bien d’autres domaines.

Dans un scénario Acrobat Sign et de formulaires adaptatifs type, un utilisateur remplit un formulaire adaptatif sur **demander un service**. Par exemple, un formulaire de demande de carte bancaire et d’allocation. Lorsqu’un utilisateur remplit, envoie et signe le formulaire de demande, le formulaire est envoyé au prestataire de services qui décidera des actions à entreprise. Le fournisseur de services examine la demande et utilise Acrobat Sign pour marquer la demande approuvée. Pour activer des processus de signature électronique similaires, vous pouvez intégrer Acrobat Sign à AEM Forms.

Pour utiliser Acrobat Sign avec AEM Forms, configurez Acrobat Sign dans AEM Cloud Services :

## Prérequis {#prerequisites}

Pour intégrer Acrobat Sign à AEM Forms, vous devez disposer des éléments suivants :

* Une principale [Compte de développeur Acrobat Sign.](https://acrobat.adobe.com/fr/fr/why-adobe/developer-form.html)
* Un serveur AEM Forms [SSL](/help/sites-administering/ssl-by-default.md).
* Un [Application d’API Acrobat Sign](https://www.adobe.io/apis/documentcloud/sign/docs.html#!adobedocs/adobe-sign/master/gstarted/create_app.md).
* Informations d’identification (identifiant client et secret client) de l’application API Acrobat Sign.
* Lors de la reconfiguration, supprimez la configuration Acrobat Sign existante des instances d’auteur et de publication.
* Une [crypto-clé identique](/help/sites-administering/security-checklist.md#make-sure-you-properly-replicate-encryption-keys-when-needed) pour les instances d’auteur et de publication.

## Configuration d’Acrobat Sign avec AEM Forms {#configure-adobe-sign-with-aem-forms}

Une fois les conditions préalables en place, procédez comme suit pour configurer Acrobat Sign avec AEM Forms sur l’instance d’auteur :

1. Dans l’instance d’auteur AEM Forms, accédez à **Outils** ![hammer](assets/hammer.png) > **Général** > **Navigateur de configuration**.
   * Pour plus d’informations, consultez la documentation relative au [](/help/sites-administering/configurations.md)Navigateur de configuration.
1. Sur la page du **[!UICONTROL navigateur de configuration]**, appuyez sur **[!UICONTROL Créer]**.
1. Dans la boîte de dialogue **[!UICONTROL Créer une configuration]**, indiquez un **[!UICONTROL titre]** pour la configuration, activez **[!UICONTROL Configurations cloud]** et appuyez sur **[!UICONTROL Créer]**. Un conteneur de configuration pour les services cloud est créé.
1. Accédez à **Outils** ![marteau](assets/hammer.png) > **Cloud Services** > **Acrobat Sign** et sélectionnez le conteneur de configuration que vous avez créé à l’étape ci-dessus.

   >[!NOTE]
   >
   >Vous pouvez exécuter les étapes 1 à 4 pour créer un conteneur de configuration et créer une configuration Acrobat Sign dans le conteneur ou utiliser le conteneur existant `global` dossier dans **Outils** ![marteau](assets/hammer.png) > **Cloud Services** > **Acrobat Sign**. Si vous créez la configuration dans le nouveau conteneur de configuration, veillez à spécifier le nom du conteneur dans le champ **[!UICONTROL Conteneur de configuration]** lorsque vous créez un formulaire adaptatif.

   >[!NOTE]
   Vérifiez que l’URL de la page de configuration des services cloud commence par **HTTPS**. Si ce n’est pas le cas, [activez SSL](/help/sites-administering/ssl-by-default.md) pour le serveur AEM Forms.

1. Sur la page de configuration, appuyez sur . **[!UICONTROL Créer]** pour créer une configuration Acrobat Sign dans AEM Forms.
1. Dans le **[!UICONTROL Général]** de l’onglet **[!UICONTROL Création d’une configuration Acrobat Sign]** , spécifiez une **Nom** pour la configuration et appuyez sur **Suivant**. Vous avez la possibilité d’indiquer un titre et de rechercher et de sélectionner une vignette pour la configuration.

1. Copiez l’URL dans la fenêtre active du navigateur dans un bloc-notes. Il est nécessaire de configurer l’application Acrobat Sign avec AEM Forms.

1. Configurez les paramètres OAuth pour l’application Acrobat Sign :

   1. Ouvrez une fenêtre de navigateur et connectez-vous au compte de développeur Acrobat Sign.
   1. Sélectionnez l’application configurée pour AEM Forms, puis appuyez sur Configurer OAuth pour l’application.
   1. Dans la zone **URL de redirection**, ajoutez l’URL HTTPS copiée à l’étape précédente et cliquez sur **Enregistrer**.
   1. Activez les paramètres OAuth suivants pour l’application Acrobat Sign et cliquez sur **Enregistrer**.
   * aggrement_read
   * aggrement_write
   * aggrement_send
   * widget_write
   * workflow_read

   Pour obtenir des informations détaillées sur la configuration des paramètres OAuth pour une application Acrobat Sign et l’obtention des clés, voir [Configuration des paramètres oAuth pour l’application](https://www.adobe.io/apis/documentcloud/sign/docs.html#!adobedocs/adobe-sign/master/gstarted/configure_oauth.md) documentation destinée aux développeurs.

   ![Configuration OAuth](assets/oauthconfig_new.png)

1. Revenez au **Création d’une configuration Acrobat Sign** page. Dans l’onglet **[!UICONTROL Paramètres]**, le champ **[!UICONTROL URL OAuth]** indique l’URL suivante par défaut :

   `https://secure.na1.echosign.com/public/oauth`

   où :

   **na1** fait référence au partitionnement de base de données par défaut.

   Vous pouvez modifier la valeur du partitionnement de base de données. Redémarrez le serveur pour pouvoir utiliser la nouvelle valeur pour le partitionnement de base de données.

1. Spécifiez les valeurs **ID client** (également appelé ID d’application) et **clé secrète client**. Sélectionnez la **Activation d’Acrobat Sign pour les pièces jointes également** pour ajouter des fichiers joints à un formulaire adaptatif au document Acrobat Sign correspondant envoyé pour signature.

   Appuyer **[!UICONTROL Connexion à Acrobat Sign]**. Lorsque vous y êtes invité, indiquez le nom d’utilisateur et le mot de passe du compte utilisé lors de la création de l’application Acrobat Sign.

   Appuyer **[!UICONTROL Créer]** pour créer la configuration Acrobat Sign.

1. Ouvrez la console Web AEM. L’URL est `https://'[server]:[port]'/system/console/configMgr`
1. Ouvrez le **service de configuration commun aux formulaires.**
1. Dans le champ **Autoriser**, **sélectionnez** Tous les utilisateurs : tous les utilisateurs, anonymes ou connectés, peuvent afficher un aperçu des pièces jointes, vérifier et signer des formulaires, puis cliquez sur **Enregistrer.** L’instance d’auteur est configurée pour utiliser Acrobat Sign.
1. Utilisez la [réplication](/help/sites-deploying/replication.md) pour créer une configuration identique sur les instances de publication correspondantes.

Désormais, Acrobat Sign est intégré à AEM Forms et prêt à être utilisé dans les formulaires adaptatifs. À [utilisation du service Acrobat Sign dans un formulaire adaptatif](../../forms/using/working-with-adobe-sign.md#configure-adobe-sign-for-an-adaptive-form), spécifiez le conteneur de configuration créé ci-dessus dans les propriétés du formulaire adaptatif.

## Configuration du planificateur Acrobat Sign pour synchroniser l’état de signature {#configure-adobe-sign-scheduler-to-sync-the-signing-status}

Un formulaire adaptatif activé par Acrobat Sign n’est envoyé qu’une fois que tous les signataires ont terminé le processus de signature. Par défaut, les services du planificateur Acrobat Sign sont programmés pour vérifier (interroger) la réponse du signataire toutes les 24 heures. Vous pouvez modifier l’intervalle par défaut pour votre environnement. Procédez comme suit pour modifier l’intervalle par défaut :

1. Connectez-vous au serveur AEM Forms avec les informations d’identification d’administrateur et accédez à **Outils**> **Opérations**> **Console Web**.

   Vous pouvez également ouvrir l’URL suivante dans une fenêtre de navigateur :
   `https://[localhost]:'port'/system/console/configMgr`

1. Recherchez et ouvrez le **Service de configuration Acrobat Sign** . Spécifiez une [expression cron](https://en.wikipedia.org/wiki/Cron#CRON_expression) dans le champ **Expression du planificateur de mise à jour de l’état** et cliquez sur **Enregistrer**. Par exemple, pour exécuter le service de configuration tous les jours à minuit, indiquez `0 0 0 1/1 * ? *` dans le champ **Expression du planificateur de mise à jour de l’état**.

L’intervalle par défaut pour synchroniser l’état d’Acrobat Sign a désormais été modifié.

## Articles connexes {#related-articles}

* [Utilisation d’Acrobat Sign dans un formulaire adaptatif](../../forms/using/working-with-adobe-sign.md)
* [Utilisation d’Acrobat Sign avec AEM Forms (vidéo)](https://helpx.adobe.com/fr/experience-manager/kt/forms/using/adobe-sign-integration-feature-video.html)
* [Intégration d’Acrobat Sign à AEM Forms](../../forms/using/adobe-sign-integration-adaptive-forms.md)
