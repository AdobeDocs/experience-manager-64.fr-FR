---
title: Ajout d’une action ou d’un bouton personnalisé à l’interface utilisateur de création de correspondance
seo-title: Add custom action/button in Create Correspondence UI
description: Découvrez comment ajouter une action/un bouton personnalisé(e) à l’interface utilisateur Création de correspondance.
seo-description: Learn how to add custom action/button in Create Correspondence UI
uuid: e3609371-caaa-4efe-8f63-4d982cd456ab
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: correspondence-management
discoiquuid: 481856df-5db1-4ef5-80d3-3722b5bf8b67
feature: Correspondence Management
exl-id: 5bcb26dc-aeb7-4a81-b905-23c8fb05d6d0
source-git-commit: e608249c3f95f44fdc14b100910fa11ffff5ee32
workflow-type: tm+mt
source-wordcount: '1855'
ht-degree: 91%

---

# Ajout d’une action ou d’un bouton personnalisé à l’interface utilisateur de création de correspondance {#add-custom-action-button-in-create-correspondence-ui}

## Présentation {#overview}

La solution Correspondence Management vous permet d’ajouter des actions personnalisées à l’interface utilisateur de création de correspondance.

Le scénario présenté dans ce document explique comment créer un bouton dans l’interface utilisateur de création de correspondance pour partager une lettre sous la forme d’un PDF de révision joint à un e-mail.

### Prérequis {#prerequisites}

Les éléments suivants sont requis pour terminer ce scénario :

* Connaissances de CRX et Javascript
* Serveur LiveCycle

## Scénario : Création du bouton dans l’interface utilisateur de création de correspondance en vue de la révision d’une lettre {#scenario-create-the-button-in-the-create-correspondence-user-interface-to-send-a-letter-for-review}

L’ajout d’un bouton d’action (ici : envoi de la lettre pour révision) à l’interface utilisateur de création de correspondance comprend :

1. L’ajout du bouton à l’interface utilisateur de création de correspondance
1. L’ajout d’un traitement d’action au bouton
1. Ajout du processus de LiveCycle pour activer l’action &quot;gestion&quot;

### Ajout du bouton à l’interface utilisateur de création de correspondance {#add-the-button-to-the-create-correspondence-user-interface}

1. Accédez à `https://[server]:[port]/[ContextPath]/crx/de` et connectez-vous en tant qu’administrateur.
1. Dans le dossier des applications, créez un dossier appelé `defaultApp` avec un chemin d’accès / structure similaire au dossier defaultApp (situé dans le dossier de configuration). Procédez comme suit pour créer le dossier :

   * Faites un clic droit sur le dossier **[!UICONTROL defaultApp]** à l’emplacement suivant et sélectionnez **[!UICONTROL Nœud de recouvrement]** :

      /libs/fd/cm/config/defaultApp/

      ![Nœud de recouvrement](assets/1_defaultapp.png)

   * Assurez-vous que la boîte de dialogue du nœud de recouvrement possède les valeurs suivantes :

      **[!UICONTROL Chemin d’accès :]** /libs/fd/cm/config/defaultApp/

      **[!UICONTROL Emplacement du recouvrement :]** /apps/

      **[!UICONTROL Correspondance des types de nœuds :]** activé.

      ![Nœud de recouvrement](assets/2_defaultappoverlaynode.png)

   * Cliquez sur **[!UICONTROL OK]**.
   * Cliquez sur **[!UICONTROL Enregistrer tout]**.

1. Effectuez une copie du fichier acmExtensionsConfig.xml (branche /libs) sous la branche /apps.

   * Accédez à « /libs/fd/cm/config/defaultApp/acmExtensionsConfig.xml ».

   * Faites un clic droit sur le fichier acmExtensionsConfig.xml et sélectionnez **[!UICONTROL Copier]**.

      ![Copie du fichier acmExtensionsConfig.xml](assets/3_acmextensionsconfig_xml_copy.png)

   * Faites un clic droit sur le dossier **[!UICONTROL defaultApp]** sous « /applications/fd/cm/config/defaultApp/, » et sélectionnez **[!UICONTROL Coller]**.
   * Cliquez sur **[!UICONTROL Enregistrer tout]**.

1. Double-cliquez sur la copie du fichier acmExtentionsConfig.xml créée dans le dossier d’applications. Le fichier à modifier s’ouvre.
1. Recherchez le code suivant :

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <extensionsConfig>
       <modelExtensions>
           <modelExtension type="LetterInstance">
     <customAction name="Preview" label="loc.letterInstance.preview.label" tooltip="loc.letterInstance.preview.tooltip" styleName="previewButton"/>
               <customAction name="Submit" label="loc.letterInstance.submit.label" tooltip="loc.letterInstance.submit.tooltip" styleName="submitButton" permissionName="forms-users"/>
               <customAction name="SaveAsDraft" label="loc.letterInstance.saveAsDraft.label" tooltip="loc.letterInstance.saveAsDraft.tooltip" styleName="submitButton" permissionName="forms-users"/>
               <customAction name="Close" label="loc.letterInstance.close.label" tooltip="loc.letterInstance.close.tooltip" styleName="closeButton"/>
           </modelExtension>
       </modelExtensions>
   </extensionsConfig> 
   ```

1. Pour envoyer la lettre par courrier électronique, vous pouvez utiliser le flux de travail LiveCycle Forms. Pour ajouter une balise customAction sous la balise modelExtension dans le fichier acmExtensionsConfig.xml, procédez comme suit :

   ```xml
    <customAction name="Letter Review" label="Letter Review" tooltip="Letter Review" styleName="" permissionName="forms-users" actionHandler="CM.domain.CCRCustomActionHandler">
         <serviceName>Forms Workflow -> SendLetterForReview/SendLetterForReviewProcess</serviceName>
       </customAction>
   ```

   ![balise customAction](assets/5_acmextensionsconfig_xml.png)

   La balise modelExtension dispose d’un jeu de balises enfant customAction qui permet de configurer l’action, les autorisations et l’aspect du bouton d’action. Voici la liste des balises de configuration customAction :

   | **Nom** | **Description** |
   |---|---|
   | name | Le nom alphanumérique de l’action à exécuter. La valeur de cette balise est obligatoire, doit être unique (dans la balise modelExtension) et doit commencer par une lettre de l’alphabet. |
   | label | Libellé du bouton d’action. |
   | tooltip | Texte de l’info-bulle du bouton, qui s’affiche lorsque l’utilisateur passe le pointeur de la souris sur le bouton. |
   | styleName | Nom du style personnalisé appliqué au bouton d’action. |
   | permissionName | L’action correspondante s’affiche uniquement si l’utilisateur dispose de l’autorisation spécifiée par la valeur permissionName. Lorsque vous spécifiez la valeur permissionName en tant que `forms-users`, tous les utilisateurs ont accès à cette option. |
   | actionHandler | Nom complet de la classe ActionHandler appelée lorsque l’utilisateur clique sur le bouton. |

   Outre les paramètres ci-dessus, des configurations supplémentaires associées à une action personnalisée customAction peuvent exister. Ces configurations supplémentaires sont accessibles au gestionnaire via l’objet CustomAction.

   | **Nom** | **Description** |
   |---|---|
   | serviceName | Si une action personnalisée customAction comprend une balise enfant nommée serviceName, le fait de cliquer sur le bouton/lien correspondant appelle un processus dont le nom est représenté par la balise serviceName. Vérifiez que ce processus présente la même signature que le post-processus de lettre. Ajoutez le préfixe « Flux de travail Forms - > » au nom du service. |
   | Paramètres contenant le préfixe cm_ dans le nom de balise | Si une action personnalisée (customAction) contient une balise enfant dont le nom commence par cm_, au cours du post-processus (qu’il s’agisse d’un post-processus de lettre ou d’un processus spécifique représenté par la balise serviceName), ces paramètres sont disponibles dans le code XML d’entrée, sous la balise correspondante et sans le préfixe cm_. |
   | actionName | Lorsqu’un post-processus est généré par un clic, les données XML soumises présentent une balise spéciale dont le nom contient le nom de l’action utilisateur. |

1. Cliquez sur **[!UICONTROL Enregistrer tout]**.

#### Création d’un dossier de paramètres régionaux avec le fichier de propriétés dans la branche /apps {#create-a-locale-folder-with-properties-file-in-the-apps-branch}

Le fichier ACMExtensionsMessages.properties comprend des libellés et des messages d’info-bulles correspondant à plusieurs champs de l’interface utilisateur de création de correspondance. Effectuez une copie de ce fichier dans la branche /apps afin que les actions/boutons personnalisé(e)s fonctionnent.

1. Faites un clic droit sur le dossier **[!UICONTROL Paramètres régionaux]** au chemin d’accès suivant et sélectionnez **[!UICONTROL Nœud de recouvrement]** :

   /libs/fd/cm/config/defaultApp/locale

1. Assurez-vous que la boîte de dialogue du nœud de recouvrement possède les valeurs suivantes :

   **[!UICONTROL Chemin d’accès :]** /libs/fd/cm/config/defaultApp/locale

   **[!UICONTROL Emplacement du recouvrement :]** /apps/

   **[!UICONTROL Respect des types de nœud :]** activé

1. Cliquez sur **[!UICONTROL OK]**.
1. Cliquez sur **[!UICONTROL Enregistrer tout]**.
1. Faites un clic droit sur le fichier suivant et sélectionnez **[!UICONTROL Copier]** :

   `/libs/fd/cm/config/defaultApp/locale/ACMExtensionsMessages.properties`

1. Faites un clic droit sur le dossier **[!UICONTROL Paramètres régionaux]** à l’emplacement suivant et sélectionnez **[!UICONTROL Coller]** :

   `/apps/fd/cm/config/defaultApp/locale/`

   Le fichier ACMExtensionsMessages.properties est copié dans le dossier de paramètres régionaux.

1. Pour localiser les libellés de l’action/du bouton personnalisé(e) nouvellement ajouté(e), créez le fichier ACMExtensionsMessages.properties correspondant au paramètre régional approprié dans `/apps/fd/cm/config/defaultApp/locale/`.

   Par exemple, pour localiser l’action/le bouton personnalisé(e) créé(e) dans cet article, créez un fichier nommé ACMExtensionsMessages_fr.properties avec l’entrée suivante :

   `loc.letterInstance.letterreview.label=Revue De Lettre`

   De même, vous pouvez ajouter des propriétés supplémentaires (par rapport à l’info-bulle et au style, par exemple) dans ce fichier.

1. Cliquez sur **[!UICONTROL Enregistrer tout]**.

#### Redémarrage du lot du bloc de création Adobe Asset Composer {#restart-the-adobe-asset-composer-building-block-bundle}

Après avoir effectué chaque modification côté serveur, redémarrez le lot du bloc de création Adobe Asset Composer. Dans ce scénario, les fichiers acmExtensionsConfig.xml et ACMExtensionsMessages.properties côté serveur sont modifiés et, par conséquent, le lot du bloc de création Adobe Asset Composer nécessite un redémarrage.

>[!NOTE]
>
>Vous devrez peut-être vider la mémoire cache du navigateur.

1. Accédez à `https://[host]:[port]/system/console/bundles`. Le cas échéant, connectez-vous en tant qu’administrateur.

1. Recherchez le lot du bloc de création Adobe Asset Composer. Redémarrez le lot : cliquez sur Arrêter, puis sur Démarrer.

   ![Bloc de création Adobe Asset Composer](assets/6_assetcomposerbuildingblockbundle.png)

Après le redémarrage du lot du bloc de création Adobe Asset Composer, le bouton personnalisé s’affiche dans l’interface utilisateur de création de correspondance. Vous pouvez ouvrir une lettre dans l’interface utilisateur de création de correspondance afin de prévisualiser le bouton personnalisé.

### Ajouter un traitement d’action au bouton {#add-action-handling-to-the-button}

Par défaut, la classe ActionHandler est intégrée dans le fichier cm.domain.js de l’interface utilisateur de création de correspondance à l’emplacement suivant :

/libs/fd/cm/ccr/gui/components/admin/clientlibs/ccr/js/cm.domain.js

Concernant le traitement de l’action personnalisée, créez un recouvrement du fichier cm.domain.js dans la branche /apps de CRX.

Le traitement de l’action/du bouton lors d’un clic sur l’action/le bouton comprend la logique pour :

* Rendre l’action ajoutée visible/invisible : via le remplacement de la fonction actionVisible().
* Activer/désactiver l’action ajoutée : via le remplacement de la fonction actionEnabled().
* Traiter réellement l’action lorsque l’utilisateur clique sur le bouton : via le remplacement de l’implémentation de la fonction handleAction().

1. Accédez à `https://[server]:[port]/[ContextPath]/crx/de`. Le cas échéant, connectez-vous en tant qu’administrateur.

1. Dans le dossier d’applications, créez un dossier nommé `js` dans la branche /apps de CRX, dont la structure est semblable au dossier suivant :

   `/libs/fd/cm/ccr/gui/components/admin/clientlibs/ccrui/js`

   Procédez comme suit pour créer le dossier :

   1. Cliquez avec le bouton droit sur le dossier **[!UICONTROL js]** à l’emplacement suivant et sélectionnez **[!UICONTROL Nœud de recouvrement]** :

      `/libs/fd/cm/ccr/gui/components/admin/clientlibs/ccrui/js`

   1. Assurez-vous que la boîte de dialogue du nœud de recouvrement possède les valeurs suivantes :

      **[!UICONTROL Chemin :]** /libs/fd/cm/ccr/gui/components/admin/clientlibs/ccrui/js

      **[!UICONTROL Emplacement du recouvrement :]** /apps/

      **[!UICONTROL Respect des types de nœud :]** activé

   1. Cliquez sur **[!UICONTROL OK]**.
   1. Cliquez sur **[!UICONTROL Enregistrer tout]**.

1. Dans le dossier js, procédez comme suit pour créer un fichier nommé ccrcustomization.js avec le code de traitement d’action du bouton :

   1. Cliquez avec le bouton droit sur le dossier **[!UICONTROL js]** au chemin suivant, puis sélectionnez **[!UICONTROL Créer > Créer un fichier]** :

      `/apps/fd/cm/ccr/gui/components/admin/clientlibs/ccrui/js`

      Nommez le fichier ccrcustomization.js.

   1. Double-cliquez sur le fichier ccrcustomization.js pour l’ouvrir dans CRX.
   1. Dans le fichier, collez le code suivant puis cliquez sur **[!UICONTROL Enregistrer tout]** :

      ```
      /* for adding and handling custom actions in Extensible Toolbar.
        * One instance of handler will be created for each action.
        * CM.domain.CCRCustomActionHandler is actionHandler class.
        */
      var CCRCustomActionHandler;
          CCRCustomActionHandler = CM.domain.CCRCustomActionHandler = new Class({
              className: 'CCRCustomActionHandler',
              extend: CCRDefaultActionHandler,
              construct : function(action,model){
              }
          });
          /**
           * Called when user user click an action
           * @param extraParams additional arguments that may be passed to handler (For future use)
           */
          CCRCustomActionHandler.prototype.handleAction = function(extraParams){
              if (this.action.name == CCRCustomActionHandler.SEND_FOR_REVIEW) {
                  var sendForReview = function(){
                      var serviceName = this.action.actionConfig["serviceName"];
                      var inputParams = {};
                      inputParams["dataXML"] = this.model.iccData.data;
                      inputParams["letterId"] = this.letterVO.id;
                      inputParams["letterName"] = this.letterVO.name;
                      inputParams["mailId"] = $('#email').val();
                      /*function to invoke the LivecyleService */
                      ServiceDelegate.callJSONService(this,"lc.icc.renderlib.serviceInvoker.json","invokeProcess",[serviceName,inputParams],this.onProcessInvokeComplete,this.onProcessInvokeFail);
                      $('#ccraction').modal("hide");
                  }
                  if($('#ccraction').length == 0){
                      /*For first click adding popup & setting letterName.*/
                      $("body").append(popUp);
                      $("input[id*='letterName']").val(this.letterVO.name);   
                      $(document).on('click',"#submitLetter",$.proxy( sendForReview, this ));
                  }
                  $('#ccraction').modal("show");
              }
          };
          /**
           * Should the action be enabled in toolbar
           * @param extraParams additional arguements that may be passed to handler (For future use)
           * @return flag indicating whether the action should be enabled
           */
         CCRCustomActionHandler.prototype.actionEnabled = function(extraParams){
                  /*can be customized as per user requirement*/
                  return true;
          };
          /**
           * Should the action be visible in toolbar
           * @param extraParams additional arguments that may be passed to handler (For future use)
           * @return flag indicating whether the action should be enabled
           */
          CCRCustomActionHandler.prototype.actionVisible = function(extraParams){
              /*Check can be enabled for Non-Preview Mode.*/
              return true;
          };
          /*SuccessHandler*/
          CCRCustomActionHandler.prototype.onProcessInvokeComplete = function(response) {
              ErrorHandler.showSuccess("Letter Sent for Review");
          };
          /*FaultHandler*/
          CCRCustomActionHandler.prototype.onProcessInvokeFail = function(event) {
              ErrorHandler.showError(event.message);
          };
          CCRCustomActionHandler.SEND_FOR_REVIEW  = "Letter Review";
      /*For PopUp*/
          var popUp = '<div class="modal fade" id="ccraction" tabindex="-1" role="dialog" aria-hidden="true">'+
          '<div class="modal-dialog modal-sm">'+
              '<div class="modal-content">' +
                  '<div class="modal-header">'+
                      '<button type="button" class="close" data-dismiss="modal" aria-label="Close"><span aria-hidden="true">&times;</span></button>'+
                      '<h4 class="modal-title"> Send Review </h4>'+
                  '</div>'+
                  '<div class="modal-body">'+
                      '<form>'+
                          '<div class="form-group">'+
                              '<label class="control-label">Email Id</label>'+
                              '<input type="text" class="form-control" id="email">'+
                          '</div>'+
                          '<div class="form-group">'+
                              '<label  class="control-label">Letter Name</label>'+
                              '<input id="letterName" type="text" class="form-control" readonly>'+
                          '</div>'+
                          '<div class="form-group">'+
                              '<input id="letterData" type="text" class="form-control hide" readonly>'+
                          '</div>'+
                      '</form>'+
                  '</div>'+
                  '<div class="modal-footer">'+
                     '<button type="button" class="btn btn-default" data-dismiss="modal"> Cancel </button>'+
                     '<button type="button" class="btn btn-primary" id="submitLetter"> Submit </button>'+
                  '</div>'+
              '</div>'+
          '</div>'+
      '</div>';
      ```

### Ajout d’un processus LiveCycle pour activer le traitement <span class="acrolinxCursorMarker"></span>d’action {#add-the-livecycle-process-to-enable-action-span-class-acrolinxcursormarker-span-handling}

Dans ce scénario, activez les composants suivants, qui font partie du fichier joint components.zip :

* Fichier jar du composant DSC (`DSCSample.jar`)
* Processus LCA d’envoi de la lettre pour révision (`SendLetterForReview.lca`)

Téléchargez et décompressez le fichier `components.zip` fichier à obtenir `DSCSample.jar` et `SendLetterForReview.lca` fichiers . Utilisez ces fichiers comme indiqué dans les procédures suivantes.

[Obtenir le fichier](assets/components.zip)

#### Configuration du serveur LiveCycle pour exécuter le processus LCA {#configure-the-livecycle-server-to-run-the-lca-process}

>[!NOTE]
>
>Cette étape n’est nécessaire que si vous utilisez une &quot;configuration OSGI&quot; et que l’intégration LC est requise pour le type de personnalisation que vous mettez en oeuvre.

Le processus LCA s’exécute sur le serveur LiveCycle et requiert l’adresse du serveur et les informations d’identification.

1. Accédez à `https://[server]:[port]/system/console/configMgr` et connectez-vous en tant qu’administrateur.
1. Localisez la configuration du SDK client d’Adobe LiveCycle et cliquez sur **[!UICONTROL Modifier]** (icône de modification). Le panneau de configuration s’ouvre.

1. Saisissez les informations suivantes, puis cliquez sur **[!UICONTROL Enregistrer]** :

   * **[!UICONTROL URL du serveur]** : URL du serveur LC dont dépend le service Envoi pour révision utilisé par le code du gestionnaire d’action.
   * **[!UICONTROL Nom d’utilisateur]** : nom d’utilisateur de l’administrateur du serveur LC.
   * **[!UICONTROL Mot de passe]** : mot de passe du nom d’utilisateur de l’administrateur.

   ![Configuration du SDK client d’Adobe LiveCycle](assets/3_clientsdkconfiguration.png)

#### Installation de LiveCycle Archive (LCA) {#install-livecycle-archive-lca}

Processus LiveCycle requis permettant l’exécution du processus de service de courrier électronique.

>[!NOTE]
>
>Workbench est requis pour connaître le fonctionnement de ce processus ou créer un processus similaire.

1. Connectez-vous en tant qu’administrateur à l’interface administrateur du serveur LiveCycle à l’adresse `https:/[lc server]/:[lc port]/adminui`.

1. Accédez à **[!UICONTROL Accueil > Services > Applications et services > Gestion des applications]**.

1. Si l’application SendLetterForReview est déjà présente, ignorez les étapes restantes de cette procédure. Dans le cas contraire, effectuez les étapes suivantes.

   ![Application SendLetterForReview dans l’interface utilisateur](assets/12_applicationmanagementlc.png)

1. Cliquez sur **[!UICONTROL Importer]**.

1. Cliquez sur **[!UICONTROL Choisir un fichier]****[!UICONTROL et sélectionnez SendLetterForReview.lca]**.

   ![Sélection du fichier SendLetterForReview.lca](assets/14_sendletterforreview_lca.png)

1. Cliquez sur **[!UICONTROL Aperçu]**. 

1. Sélectionnez **[!UICONTROL Déployer les ressources à l’exécution à la fin de l’importation]**.

1. Cliquez sur **[!UICONTROL Importer]**.

#### Ajout de ServiceName à la liste de services Placés sur la liste autorisée {#adding-servicename-to-the-allowlisted-service-list}

Indiquez dans le serveur AEM les services LiveCycle auxquels vous souhaitez qu’il accède.

1. Connectez-vous en tant qu’administrateur à `https:/[host]/:[port]/system/console/configMgr`.

1. Recherchez et cliquez sur **[!UICONTROL Configuration du SDK client d’Adobe LiveCycle]**. Le panneau Configuration du SDK client d’Adobe LiveCycle s’affiche.
1. Dans la liste Nom du service, cliquez sur l’icône + et ajoutez un nom de service **[!UICONTROL SendLetterForReview/SendLetterForReviewProcess]**.

1. Cliquez sur **[!UICONTROL Enregistrer]**.

#### Configuration du service de courrier électronique {#configure-the-email-service}

Dans ce scénario, configurez le service de messagerie dans le serveur LiveCycle afin que Correspondence Management puisse envoyer un courrier électronique.

1. Connectez-vous avec les informations d’identification d’administrateur à l’interface utilisateur du serveur LiveCycle à l’adresse `https:/[lc server]:[lc port]/adminui`.

1. Accédez à **[!UICONTROL Accueil > Services > Applications et services > Gestion des services]**.

1. Recherchez et cliquez sur **[!UICONTROL EmailService]**.

1. Dans **[!UICONTROL Hôte SMTP]**, configurez le service de messagerie.

1. Cliquez sur **[!UICONTROL Enregistrer]**.

#### Configuration du service DSC {#configure-the-dsc-service}

Pour utiliser l’API Correspondence Management, téléchargez la `DSCSample.jar` (joint à ce document en tant que partie intégrante de `components.zip`) et chargez-le sur le serveur LiveCycle. Après la `DSCSample.jar` est chargé sur le serveur LiveCycle, le serveur AEM utilise la variable `DSCSample.jar` pour accéder à l’API renderLetter.

Pour plus d’informations, voir [Connexion d’AEM Forms à Adobe LiveCycle](/help/forms/using/aem-livecycle-connector.md).

1. Mettez à jour l’URL du serveur AEM dans cmsa.properties dans `DSCSample.jar`, qui se trouve à l’emplacement suivant :

   DSCSample.jar\com\adobe\livecycle\cmsa.properties

1. Indiquez les paramètres suivants dans le fichier de configuration :

   * **crx.serverUrl**=https:/[hôte]/:[port]/[chemin du contexte]/[URL AEM]
   * **crx.username**= nom d’utilisateur AEM
   * **crx.password**= AEM mot de passe
   * **crx.appRoot**=/content/apps/cm

   >[!NOTE]
   >
   >À chaque modification apportée au côté serveur, redémarrez le serveur 

   Le `DSCSample.jar` utilise la variable `renderLetter` API. Pour plus d’informations sur l’API renderLetter, voir [Interface LetterRenderService](https://helpx.adobe.com/aem-forms/6-1/javadocs/com/adobe/icc/ddg/api/LetterRenderService.html).

#### Importation de DSC dans AEM Forms on JEE {#import-dsc-to-livecyle}

`DSCSample.jar``renderLetter`Le fichier utilise l’API pour effectuer le rendu d’une lettre sous forme d’octets PDF à partir des données XML fournies par C en tant qu’entrée. Pour plus d’informations sur l’API renderLetter et les autres API, voir [Service de rendu de lettre](https://helpx.adobe.com/aem-forms/6-2/javadocs/com/adobe/icc/ddg/api/LetterRenderService.html).

1. Démarrer Workbench et connectez-vous.
1. Sélectionnez **[!UICONTROL Fenêtre > Afficher les vues > Composants]**. La vue Composants est ajoutée à Workbench ES2.

1. Faites un clic droit sur **[!UICONTROL Composants]** et sélectionnez **[!UICONTROL Installer un composant]**.

1. Sélectionnez le fichier `DSCSample.jar` via l’explorateur de fichiers et cliquez sur **[!UICONTROL Ouvrir]**.
1. Faites un clic droit sur **[!UICONTROL RenderWrapper]** et sélectionnez **[!UICONTROL Démarrer le composant]**. Si le composant démarre, une flèche verte apparaît en regard du nom du composant.

## Envoi de la lettre pour révision {#send-letter-for-review}

Après avoir configuré l’action et le bouton d’envoi de la lettre pour révision :

1. Videz la mémoire cache du navigateur.

1. Dans l’interface utilisateur de création de correspondance, cliquez sur **[!UICONTROL Révision de lettre]** et indiquez l’ID de messagerie du réviseur.

1. Cliquez sur **[!UICONTROL Envoyer]**.

![sendreview](assets/sendreview.png)

Le réviseur reçoit un courrier électronique du système contenant la lettre en tant que pièce jointe.
