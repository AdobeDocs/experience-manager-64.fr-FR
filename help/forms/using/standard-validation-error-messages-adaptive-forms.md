---
title: Messages d’erreur de validation standard pour les formulaires adaptatifs
seo-title: Standard validation error messages for adaptive forms
description: Transformer les messages d’erreur de validation des formulaires adaptatifs au format standard à l’aide de gestionnaires d’erreurs personnalisés
seo-description: Transform the validation error messages for adaptive forms into standard format using custom error handlers
uuid: 0d1f9835-3e28-41d3-a3b1-e36d95384328
contentOwner: anujkapo
content-type: reference
geptopics: SG_AEMFORMS/categories/setting_up_and_managing_domains
discoiquuid: ec062567-1c6b-497b-a1e7-1dbac2d60852
feature: Adaptive Forms
exl-id: 864e6b0d-178b-4b91-85d3-34b90e999ee3
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1108'
ht-degree: 10%

---

# Messages d’erreur de validation standard pour les formulaires adaptatifs {#standard-validation-error-messages}

Les formulaires adaptatifs valident les entrées que vous fournissez dans les champs en fonction de critères de validation prédéfinis. Les critères de validation font référence aux valeurs d’entrée acceptables pour les champs d’un formulaire adaptatif. Vous pouvez définir les critères de validation en fonction de la source de données que vous utilisez avec le formulaire adaptatif. Par exemple, si vous utilisez des services web RESTful comme source de données, vous pouvez définir les critères de validation dans un fichier de définition Swagger.

Si les valeurs d’entrée répondent aux critères de validation, elles sont envoyées à la source de données. Sinon, le formulaire adaptatif affiche un message d’erreur.

De la même manière que cette approche, les formulaires adaptatifs peuvent désormais s’intégrer aux services personnalisés pour effectuer des validations de données. Si les valeurs d’entrée ne répondent pas aux critères de validation et que le message d’erreur de validation renvoyé par le serveur est au format standard du message, les messages d’erreur s’affichent au niveau du champ dans le formulaire.

Si les valeurs d’entrée ne répondent pas aux critères de validation et que le message d’erreur de validation du serveur n’est pas au format standard du message, les formulaires adaptatifs fournissent un mécanisme pour transformer les messages d’erreur de validation en un format standard afin qu’ils s’affichent au niveau du champ dans le formulaire. Vous pouvez transformer le message d&#39;erreur au format standard à l&#39;aide de l&#39;une des deux méthodes suivantes :

* Ajout d’un gestionnaire d’erreur personnalisé lors de l’envoi du formulaire adaptatif
* Ajout d’un gestionnaire personnalisé à l’action Invoke Service à l’aide de l’éditeur de règles

Cet article décrit le format standard des messages d’erreur de validation et les instructions pour transformer les messages d’erreur d’un format personnalisé en un format standard.

## Format du message d’erreur de validation standard {#standard-validation-message-format}

Les formulaires adaptatifs affichent les erreurs au niveau du champ si les messages d’erreur de validation du serveur sont au format standard suivant :

```javascript
   {
    errorCausedBy : "SERVER_SIDE_VALIDATION/SERVICE_INVOCATION_FAILURE"
    errors : [
        {
             somExpression  : <somexpr>
             errorMessage / errorMessages : <validationMsg> / [<validationMsg>, <validationMsg>]

        }
    ]
    originCode : <target error Code>
    originMessage : <unstructured error message returned by service>
}
```

Où :

* `errorCausedBy` décrit la raison de l’échec
* `errors` mentionnez l’expression SOM des champs qui ont échoué aux critères de validation avec le message d’erreur de validation.
* `originCode` contient le code d’erreur renvoyé par le service externe
* `originMessage` contient les données d’erreur brutes renvoyées par le service externe ;

## Configuration de l’envoi de formulaire adaptatif pour ajouter des gestionnaires personnalisés {#configure-adaptive-form-submission}

Si le message d’erreur de validation du serveur ne s’affiche pas dans le format standard, vous pouvez activer l’envoi asynchrone et ajouter un gestionnaire d’erreur personnalisé lors de l’envoi du formulaire adaptatif pour convertir le message dans un format standard.

### Configuration de l’envoi de formulaire adaptatif asynchrone {#configure-asynchronous-adaptive-form-submission}

Avant d’ajouter un gestionnaire personnalisé, vous devez configurer le formulaire adaptatif pour l’envoi asynchrone. Procédez comme suit :

1. En mode de création de formulaire adaptatif, sélectionnez l’objet Conteneur de formulaires et appuyez sur ![propriétés de formulaire adaptatif](assets/configure_icon.png) pour ouvrir ses propriétés.
1. Dans la section des propriétés **[!UICONTROL Envoi]**, activez **[!UICONTROL Utiliser l’envoi asynchrone]**.
1. Sélectionner **[!UICONTROL Revalider sur le serveur]** pour valider les valeurs des champs d’entrée sur le serveur avant envoi.
1. Sélectionnez l’action Envoyer :

   * Sélectionner **[!UICONTROL Envoyer à l’aide du modèle de données de formulaire]** et sélectionnez le modèle de données approprié, si vous utilisez le service Web RESTful basé sur [modèle de données de formulaire](work-with-form-data-model.md) comme source de données.
   * Sélectionner **[!UICONTROL Envoyer vers le point de fin REST]** et spécifiez la variable **[!UICONTROL URL/chemin de redirection]**, si vous utilisez des services Web RESTful comme source de données.

   ![propriétés d’envoi de formulaire adaptatif](assets/af_submission_properties.png)

1. Appuyez sur ![Enregistrer](assets/save_icon.png) pour enregistrer les propriétés.

### Ajout d’un gestionnaire d’erreur personnalisé lors de l’envoi du formulaire adaptatif {#add-custom-error-handler-af-submission}

AEM Forms fournit des gestionnaires de réussite et d’erreur prêts à l’emploi pour les envois de formulaires. Les gestionnaires sont des fonctions côté client qui s’exécutent en fonction de la réponse du serveur. Lorsqu’un formulaire est envoyé, les données sont transmises au serveur pour validation, ce qui renvoie une réponse au client avec des informations sur l’événement de succès ou d’erreur pour l’envoi. Les informations sont transmises en tant que paramètres au gestionnaire approprié pour exécuter la fonction.

Exécutez les étapes suivantes pour ajouter un gestionnaire d’erreur personnalisé lors de l’envoi du formulaire adaptatif :

1. Ouvrez le formulaire adaptatif en mode création, sélectionnez un objet de formulaire, puis appuyez sur <!--![Rule Editor](assets/af_edit_rules.png)--> pour ouvrir l’éditeur de règles.
1. Sélectionnez **[!UICONTROL Formulaire]** dans l’arborescence des objets de formulaire et appuyez sur **[!UICONTROL Créer]**.
1. Sélectionner **[!UICONTROL Erreur dans l’envoi]** dans la liste déroulante Événement .
1. Créez une règle pour convertir la structure d’erreur personnalisée en structure d’erreur standard, puis appuyez sur **[!UICONTROL Terminé]** pour enregistrer la règle.

Voici un exemple de code pour convertir une structure d’erreur personnalisée en structure d’erreur standard :

```javascript
var data = $event.data;
var som_map = {
    "id": "guide[0].guide1[0].guideRootPanel[0].Pet[0].id_1[0]",
    "name": "guide[0].guide1[0].guideRootPanel[0].Pet[0].name_2[0]",
    "status": "guide[0].guide1[0].guideRootPanel[0].Pet[0].status[0]"
};

var errorJson = {};
errorJson.errors = [];

if (data) {
    if (data.originMessage) {
        var errorData;
        try {
            errorData = JSON.parse(data.originMessage);
        } catch (err) {
            // not in json format
        }

        if (errorData) {
            Object.keys(errorData).forEach(function(key) {
                var som_key = som_map[key];
                if (som_key) {
                    var error = {};
                    error.somExpression = som_key;
                    error.errorMessage = errorData[key];
                    errorJson.errors.push(error);
                }
            });
        }
        window.guideBridge.handleServerValidationError(errorJson);
    } else {
        window.guideBridge.handleServerValidationError(data);
    }
}
```

Le `var som_map` répertorie l’expression SOM des champs de formulaire adaptatif que vous souhaitez transformer au format standard. Vous pouvez afficher l’expression SOM de n’importe quel champ d’un formulaire adaptatif en appuyant sur le champ et en sélectionnant **[!UICONTROL Afficher l’expression SOM]**.

À l’aide de ce gestionnaire d’erreurs personnalisé, le formulaire adaptatif convertit les champs répertoriés dans `var som_map` au format standard du message d’erreur. Par conséquent, les messages d’erreur de validation s’affichent au niveau du champ dans le formulaire adaptatif.

## Ajout d’un gestionnaire personnalisé à l’aide de l’action Invoke Service

Exécutez les étapes suivantes pour ajouter un gestionnaire d’erreur afin de convertir une structure d’erreur personnalisée en structure d’erreur standard à l’aide de [Éditeur de règles](rule-editor.md) Action Appeler le service :

1. Ouvrez le formulaire adaptatif en mode création, sélectionnez un objet de formulaire, puis appuyez sur ![Éditeur de règles](assets/rule_editor_icon.png) pour ouvrir l’éditeur de règles.
1. Appuyez sur **[!UICONTROL Créer]**.
1. Créez une condition dans le **[!UICONTROL When]** de la règle. Par exemple, Lorsque[Nom du champ] est modifiée. Sélectionner **[!UICONTROL est modifié]** de la **[!UICONTROL Sélectionner un état]** Liste déroulante pour atteindre cette condition.
1. Dans la section **[!UICONTROL Then]** (Alors), sélectionnez **[!UICONTROL Invoke Service]** (Appeler un service) dans la liste déroulante **[!UICONTROL Select Action]** (Sélectionner une action). 
1. Sélectionnez un service Post et ses liaisons de données correspondantes dans la **[!UICONTROL Entrée]** . Par exemple, si vous souhaitez valider **Nom**, **ID**, et **État** dans le formulaire adaptatif, sélectionnez un service Post (animal de compagnie) et sélectionnez pet.name, pet.id et pet.status dans le champ **[!UICONTROL Entrée]** .

Par conséquent, les valeurs que vous saisissez pour **Nom**, **ID**, et **État** sont validés, dès que le champ défini à l’étape 2 est modifié et que vous désélectionnez le champ du formulaire.

1. Sélectionner **[!UICONTROL Éditeur de code]** dans la liste déroulante sélection de mode .
1. Appuyer **[!UICONTROL Modifier le code]**.
1. Supprimez la ligne suivante du code existant :

   ```javascript
   guidelib.dataIntegrationUtils.executeOperation(operationInfo, inputs, outputs);
   ```

1. Créez une règle pour convertir la structure d’erreur personnalisée en structure d’erreur standard, puis appuyez sur **[!UICONTROL Terminé]** pour enregistrer la règle.
Par exemple, ajoutez l’exemple de code suivant à la fin pour convertir une structure d’erreur personnalisée en structure d’erreur standard :

   ```javascript
   var errorHandler = function(jqXHR, data) {
   var som_map = {
       "id": "guide[0].guide1[0].guideRootPanel[0].Pet[0].id_1[0]",
       "name": "guide[0].guide1[0].guideRootPanel[0].Pet[0].name_2[0]",
       "status": "guide[0].guide1[0].guideRootPanel[0].Pet[0].status[0]"
   };
   
   
   var errorJson = {};
   errorJson.errors = [];
   
   if (data) {
       if (data.originMessage) {
           var errorData;
           try {
               errorData = JSON.parse(data.originMessage);
           } catch (err) {
               // not in json format
           }
   
           if (errorData) {
               Object.keys(errorData).forEach(function(key) {
                   var som_key = som_map[key];
                   if (som_key) {
                       var error = {};
                       error.somExpression = som_key;
                       error.errorMessage = errorData[key];
                       errorJson.errors.push(error);
                   }
               });
           }
           window.guideBridge.handleServerValidationError(errorJson);
       } else {
           window.guideBridge.handleServerValidationError(data);
       }
     }
   };
   
   guidelib.dataIntegrationUtils.executeOperation(operationInfo, inputs, outputs, null, errorHandler);
   ```

   Le `var som_map` répertorie l’expression SOM des champs de formulaire adaptatif que vous souhaitez transformer au format standard. Vous pouvez afficher l’expression SOM de n’importe quel champ d’un formulaire adaptatif en appuyant sur le champ et en sélectionnant **[!UICONTROL Afficher l’expression SOM]** de **[!UICONTROL Autres options]** (...) .

   Assurez-vous de copier la ligne suivante de l’exemple de code dans le gestionnaire d’erreurs personnalisé :

   ```javascript
   guidelib.dataIntegrationUtils.executeOperation(operationInfo, inputs, outputs, null, errorHandler);
   ```

   L’API executeOperation comprend la variable `null` et `errorHandler` en fonction du nouveau gestionnaire d’erreurs personnalisé.

   À l’aide de ce gestionnaire d’erreurs personnalisé, le formulaire adaptatif convertit les champs répertoriés dans `var som_map` au format standard du message d’erreur. Par conséquent, les messages d’erreur de validation s’affichent au niveau du champ dans le formulaire adaptatif.
