---
title: Générer l’aperçu HTML5 d’un formulaire XDP
seo-title: Generate HTML5 preview of an XDP form
description: L’onglet Aperçu du HTML dans LiveCycle Designer permet de prévisualiser les formulaires tels qu’ils apparaissent dans un navigateur.
seo-description: Preview HTML tab in LiveCycle Designer can be used to preview forms as they appear in a browser.
uuid: d004e75d-e569-4e85-8dfa-5c411bc959af
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: c142d7b3-301b-447c-a715-452c905565d1
feature: Mobile Forms
exl-id: f855d3f9-cf3c-4883-b82b-d607250c3dae
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '831'
ht-degree: 47%

---

# Générer l’aperçu HTML5 d’un formulaire XDP {#generate-html-preview-of-an-xdp-form}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Lors de la conception d’un formulaire dans AEM Forms Designer, en plus de la prévisualisation du rendu du PDF d’un formulaire, vous pouvez également prévisualiser un rendu HTML5 de celui-ci. Vous pouvez utiliser la variable **Prévisualiser le HTML** pour prévisualiser un formulaire tel qu’il apparaîtra dans un navigateur.

## Activation de l’aperçu du HTML pour les formulaires XDP dans Designer {#html-preview-of-forms-in-forms-designer}

Pour permettre à Designer de générer l’aperçu du HTML des formulaires XDP, effectuez les configurations suivantes :

* Configurer le service d’authentification Apache Sling
* Désactiver le mode Protégé
* Spécification des détails sur le serveur AEM Forms

### Configurer le service d’authentification Apache Sling {#configure-apache-sling-authentication-service}

1. Accédez à `https://[server]:[port]/system/console/configMgr` sur AEM Forms s’exécutant sur OSGi ou

   `https://[server]:[port]/lc/system/console/configMgr` sur AEM Forms s’exécutant sur JEE.

1. Localisez et cliquez sur la boîte de configuration **Service d’authentification Apache Sling** pour l’ouvrir en mode d’édition.

1. Selon que vous exécutez AEM Forms sur OSGi ou JEE, ajoutez ce qui suit dans le **champ** Conditions d’authentification requises : 

   *  d’AEM Forms sur JEE

      * -/content/xfaforms
      * -/etc/clientlibs
   * AEM Forms sur OSGi

      * -/content/xfaforms
      * -/etc/clientlibs/fd/xfaforms

   >[!NOTE]
   >
   >Ne copiez pas et ne collez pas la valeur spécifiée dans le champ Exigences d’authentification , car cela peut endommager les caractères spéciaux de la valeur. Saisissez plutôt la valeur spécifiée dans le champ .

1. Indiquez un nom d’utilisateur et un mot de passe dans **[!UICONTROL Nom d’utilisateur anonyme]** et **[!UICONTROL Mot de passe utilisateur anonyme]** , respectivement. Les informations d’identification spécifiées sont utilisées pour gérer l’authentification anonyme et autoriser l’accès aux utilisateurs anonymes.
1. Cliquez sur **Enregistrer** pour enregistrer la configuration.

### Désactiver le mode Protégé {#disable-protected-mode}

Le [mode protégé](/help/forms/using/get-xdp-pdf-documents-aem.md) est activé, par défaut. Laissez-la activée pour les environnements de production. Vous pouvez la désactiver pour qu’un environnement de développement prévisualise HTML5 Forms dans Designer. Procédez comme suit pour le désactiver :

1. Connectez-vous à la console Web AEM en tant qu’administrateur. 

   * L’URL d’AEM Forms on OSGi est `https://[server]:[port]/system/console/configMgr`
   * L’URL d’AEM Forms on JEE est `https://[server]:[port]/lc/system/console/configMgr`

1. Ouvrir **[!UICONTROL Configurations de Mobile Forms]** pour modification.
1. Désélectionnez l’option **[!UICONTROL Mode protégé]** et cliquez sur **[!UICONTROL Enregistrer]**.

### Fournir des détails sur le serveur AEM Forms {#provide-details-of-aem-forms-server}

1. Dans Designer, cliquez sur **Tools** > **Options**.
1. Dans la fenêtre Options, sélectionnez la page **Options du serveur**, fournissez les détails suivants, puis cliquez sur **OK**.

   * **URL de serveur** : URL du serveur d’AEM Forms.
   * **Numéro de port HTTP**: AEM port du serveur. La valeur par défaut est 4502.
   * **Contexte d’aperçu HTML :** chemin du profil pour le rendu des formulaires XFA. Les profils par défaut suivants sont utilisés pour afficher l’aperçu du formulaire dans Designer. Cependant, vous pouvez également spécifier un chemin vers un profil personnalisé.

      * `/content/xfaforms/profiles/default.html` (AEM Forms on OSGi)
      * `/lc/content/xfaforms/profiles/default.html` (AEM Forms on JEE)
   * **Contexte de Forms Manager :** Chemin d’accès au contexte à l’emplacement où l’interface utilisateur de Forms Manager est déployée. Les valeurs par défaut sont les suivantes :

      * `/aem/forms` (AEM Forms on OSGi)
      * `/lc/forms` (AEM Forms on JEE)

   **Remarque :** *Vérifiez que le serveur AEM Forms est opérationnel. L’aperçu HTML se connecte au serveur CRX pour * générer *un aperçu.*

   ![Options d’AEM Forms Designer ](assets/server_options.png)

   Options d’AEM Forms Designer

1. Pour prévisualiser un formulaire au format HTML, cliquez sur l’onglet **Aperçu HTML**.

   >[!NOTE]
   >
   >Si l’onglet Aperçu du HTML est fermé, appuyez sur la touche F4 pour ouvrir l’onglet HTML de prévisualisation . Vous pouvez également sélectionner Aperçu du HTML dans le menu Affichage pour ouvrir l’onglet HTML de prévisualisation .

   >[!NOTE]
   >
   >l’aperçu HTML ne prend pas en charge les documents PDF, il est uniquement dédié aux documents au format XDP.

## Pour prévisualiser un formulaire à l’aide de données d’exemple {#to-preview-a-form-using-sample-data}

Designer vous permet de prévisualiser et de tester votre formulaire à l’aide d’exemples de données XML. Il est recommandé de tester fréquemment votre formulaire à l’aide de données d’exemple afin de vous assurer qu’il s’affiche correctement.

Si vous ne disposez pas de données d’exemple, Designer peut les créer ou vous pouvez les créer vous-même. (Voir [Génération automatique de données d’exemple pour la prévisualisation du formulaire](https://help.adobe.com/fr_FR/AEMForms/6.1/DesignerHelp/WS107c29ade9134a2c136ae6f212a1f379c94-8000.2.html#WS92d06802c76abadb-728f46ac129b395660c-7efe.2) et [Pour créer des exemples de données afin de prévisualiser le formulaire](https://help.adobe.com/fr_FR/AEMForms/6.1/DesignerHelp/WS107c29ade9134a2c136ae6f212a1f379c94-8000.2.html#WS92d06802c76abadb-728f46ac129b395660c-7eff.2).)

Le test de votre formulaire à l’aide d’une source de données d’exemple permet de s’assurer que les données et les champs sont mappés et que les sous-formulaires qui se répètent se répètent comme prévu. Vous pouvez créer une disposition de formulaire équilibrée qui offre un espace approprié à chaque objet pour afficher les données fusionnées.

1. Sélectionnez **Fichier > Propriétés du formulaire**.

1. Cliquez sur l’onglet **Aperçu** et, dans la zone Fichier de données, indiquez le chemin d’accès complet au fichier de données de test. Vous pouvez également vous servir du bouton Parcourir pour naviguer jusqu’au fichier.

1. Cliquez sur **OK**. La prochaine fois que vous prévisualiserez le formulaire dans l’onglet **Aperçu HTML**, les valeurs des données de l’exemple de fichier XML apparaîtront dans les objets respectifs.

## Aperçu des formulaires situés dans un référentiel {#html-preview-of-forms-in-forms-manager}

Dans AEM Forms, vous pouvez prévisualiser des formulaires et des documents dans un référentiel. L’aperçu permet de déterminer exactement l’apparence et le comportement des formulaires lorsqu’ils seront utilisés par les utilisateurs finaux.

[**Contacter le support technique**](https://www.adobe.com/account/sign-in.supportportal.html)
