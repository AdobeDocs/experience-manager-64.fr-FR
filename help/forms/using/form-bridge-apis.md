---
title: API Form Bridge pour les formulaires HTML5
seo-title: Form Bridge APIs for HTML5 forms
description: Les applications externes utilisent l’API FormBridge pour se connecter au formulaire pour périphériques mobiles XFA. L’API distribue un événement FormBridgeInitialized sur la fenêtre parent.
seo-description: External applications use the FormBridge API to connect to the XFA Mobile Form. The API dispatches a FormBridgeInitialized event on the parent window.
uuid: 0db22649-522b-4857-9ffd-826c52381d15
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: developer-reference
discoiquuid: c05c9911-7c49-4342-89de-61b8b9953c83
exl-id: ad669f3b-2bda-4c41-8032-cf25a192ce12
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '939'
ht-degree: 40%

---

# API Form Bridge pour les formulaires HTML5 {#form-bridge-apis-for-html-forms}

Vous pouvez utiliser les API Form Bridge pour ouvrir un canal de communication entre des formulaires HTML5 basés sur XFA et vos applications. Les API Form Bridge fournissent une **connect** API pour créer la connexion.

L’API de **connexion** accepte un gestionnaire en tant qu’argument. Une fois la connexion créée entre le formulaire HTML5 basé sur XFA et Form Bridge, la poignée est appelée.

Vous pouvez utiliser l’exemple de code suivant pour créer la connexion.

```
// Example showing how to connect to FormBridge
window.addEventListener("FormBridgeInitialized",
                                function(event) {
                                    var fb = event.detail.formBridge;
                                    fb.connect(function() {
                                           //use form bridge functions 
                         })
                            })
```

>[!NOTE]
>
>Assurez-vous d’avoir créé la connexion avant d’ajouter le fichier formruntime.jsp.

## API Form Bridge disponible  {#available-form-bridge-api-nbsp}

**getBridgeVersion()**

Renvoie le numéro de version de la bibliothèque de script.

* **Input** : aucune
* **Sortie**: Numéro de version de la bibliothèque de script
* **Errors** : aucune

**isConnected()** Vérifie si l’état du formulaire a été initialisé.

* **Input** : aucune
* **Sortie**: **True** si l’état du formulaire XFA a été initialisé ;

* **Errors** : aucune

**connect(handler, context)** établit une connexion à FormBridge et exécute la fonction une fois la connexion établie et l’état du formulaire initialisé.

* **Entrée**:

   * **handler** : fonction à exécuter après la connexion de Form Bridge
   * **contexte**: Objet auquel le contexte (ceci) de la fonction *handler* est défini.

* **Output** : aucune
* **Error** : aucune

**getDataXML(options)** Renvoie les données actuelles du formulaire au format XML

* **Entrée:**

   * **options :** objet JavaScript contenant les propriétés suivantes :

      * **Error**: Error Handler Function
      * **success** : fonction du gestionnaire de réussite. Cette fonction transmet un objet contenant du code XML à la propriété *data*.
      * **context** : objet pour lequel le contexte (valeur « this ») de la fonction *success* est défini.
      * **validationChecker**: Fonction à appeler pour vérifier les erreurs de validation reçues du serveur. La fonction de validation transmet un tableau de chaînes d’erreur.
      * **formState**: L’état JSON du formulaire XFA pour lequel les données XML doivent être renvoyées. Si cette fonction n’est pas spécifiée, elle renvoie les données XML du formulaire actuellement généré.

* **Output :** aucune
* **Error :** aucune

**registerConfig(configName, config)** Enregistre les configurations spécifiques à l’utilisateur/au portail avec FormBridge. Ces configurations remplacent les configurations par défaut. Les configurations prises en charge sont spécifiées dans la section config.

* **Entrée:**

   * **configName :** Nom de la configuration à remplacer

      * **widgetConfig :** Permet à l’utilisateur de remplacer les widgets par défaut du formulaire par des widgets personnalisés. La configuration est remplacée comme suit :

         formBridge.registerConfig(&quot;widgetConfig&quot;:{/&amp;ast;configuration&amp;ast;/})

      * **pagingConfig :** Permet à l’utilisateur de remplacer le comportement par défaut du rendu de la première page uniquement. La configuration est remplacée comme suit :

         window.formBridge.registerConfig(&quot;pagingConfig&quot;:{pagingDisabled: &lt;true | false>, shrinkPageDisabled: &lt;true | false> }).

      * **LoggingConfig:** Permet à l’utilisateur de remplacer le niveau de journalisation, de désactiver la journalisation d’une catégorie ou d’afficher la console des journaux ou de l’envoyer au serveur. La configuration peut être remplacée comme suit :

      ```css
      formBridge.registerConfig{  
        "LoggerConfig" : {  
      {  
      "on":`<true *| *false>`,  
      "category":`<array of categories>`,  
      "level":`<level of categories>`, "  
      type":`<"console"/"server"/"both">`  
          }  
        }
      ```

      * **SubmitServiceProxyConfig :** Permet aux utilisateurs d’enregistrer les envois et les services proxy de journalisation.

         ```css
         window.formBridge.registerConfig("submitServiceProxyConfig",  
         {  
         "submitServiceProxy" : "`<submitServiceProxy>`",  
         "logServiceProxy": "`<logServiceProxy>`",  
         "submitUrl" : "`<submitUrl>`"  
         });
         ```
   * **config :** valeur de la configuration



* **Output :** objet contenant la valeur d’origine de la configuration dans la propriété *data*.

* **Error :** aucune

**hideFields(fieldArray)** Masque les champs dont les expressions Som sont fournies dans le tableau fieldArray. Définit la propriété presence des champs spécifiés sur invisible

* **Entrée:**

   * **fieldArray :** Tableau des expressions Som pour les champs à masquer

* **Output :** aucune
* **Error :** aucune

**showFields(fieldArray)** Affiche les champs dont les expressions Som sont fournies dans le tableau fieldArray. Définit la propriété presence des champs fournis sur visible

* **Entrée:**

   * **fieldArray :** Tableau des expressions Som des champs à afficher

* **Output :** aucune
* **Error :** aucune

**hideSubmitButtons()** Masque tous les boutons d’envoi dans le formulaire.

* **Input** : aucune
* **Output** : aucune
* **Error** : renvoie l’exception si l’état du formulaire n’est pas initialisé

**getFormState()** Renvoie le JSON représentant l’état du formulaire

* **Input :** aucune
* **Sortie :** Objet contenant JSON représentant l’état actuel du formulaire dans *data* .

* **Error :** aucune

**restoreFormState(options)** Restaure l’état du formulaire à partir de l’état JSON fourni dans l’objet options. L’état est appliqué et les gestionnaires de réussite ou d’erreur sont appelés après que l’opération soit terminée

* **Entrée:**

   * **Options :** Objet JavaScript contenant les propriétés suivantes :

      * **Erreur**: Fonction de gestionnaire d’erreurs
      * **success** : fonction du gestionnaire de réussite
      * **contexte**: Objet auquel le contexte (ceci) de la propriété *success* sont définies
      * **formState** : état JSON du formulaire. Le formulaire est restauré à l’état JSON.

* **Output :** aucune
* **Error :** aucune

**setFocus (som)** Définit la cible d’action sur le champ spécifié dans l’expression Som

* **Entrée :** Expression du champ sur lequel définir la cible d’action
* **Output :** aucune
* **Error :** renvoie une exception si l’expression Som est incorrecte

**setFieldValue (som, value)** Définit la valeur des champs pour les expressions Som données

* **Entrée:**

   * **som :** tableau contenant les expressions Som du champ. L’expression om pour définir la valeur des champs.
   * **value:** Tableau contenant des valeurs correspondant aux expressions Som fournies dans un **som** tableau. Si le type de données de la valeur n’est pas le même que fieldType, la valeur n’est pas modifiée.

* **Output :** aucune
* **Erreur :** Lance une exception dans le cas d’une expression Som incorrecte

**getFieldValue (som)** Renvoie la valeur des champs des expressions Som données

* **Entrée :** Tableau contenant les expressions Som des champs dont la valeur doit être récupérée
* **Sortie :** Objet contenant le résultat sous forme de tableau dans **data** .

* **Error :** aucune

### Exemple d’API getFieldValue() {#example-of-nbsp-getfieldvalue-api}

```JavaScript
var a =  formBridge.getFieldValue(“xfa.form.form1.Subform1.TextField”);
if(a.errors) {
    var err;
     while((err = a.getNextMessage()) != null)
               alert(a.message)
} else {
   alert(a.data[0]) 
}
```

**getFieldProperties(som, property)** Récupérer la liste des valeurs pour la propriété donnée des champs spécifiés par les expressions Som

* **Entrée:**

   * **som :** tableau contenant les expressions Som des champs
   * **property** : nom de la propriété dont la valeur est requise

* **Sortie :** Objet contenant le résultat sous forme de tableau dans *data *property

* **Error :** aucune

**setFieldProperties(som, property, values)** Définit la valeur de la propriété donnée pour tous les champs spécifiés par les expressions Som

* **Entrée:**

   * **som :** Tableau contenant les expressions Som des champs dont la valeur doit être définie
   * **property **: propriété dont la valeur doit être définie
   * **value:** Tableau contenant les valeurs de la propriété donnée pour les champs spécifiés par les expressions Som

* **Output :** aucune
* **Error :** aucune

## Exemple d’utilisation de l’API Form Bridge {#sample-usage-of-form-bridge-api}

```JavaScript
// Example 1: FormBridge.restoreFormState
  function loadFormState() {
    var suc = function(obj) {
             //success
            }
    var err = function(obj) {
           while(var t = obj.getNextMessage()) {
         $("#errorDiv").append("<div>"+t.message+"</div>");
           }
           }
        var _formState = // load form state from storage
    formBridge.restoreFormState({success:suc,error:err,formState:_formState}); // not passing a context means that this will be formBridge itself. Validation errors will be checked.
  }

//--------------------------------------------------------------------------------------------------

//Example 2: FormBridge.submitForm
  function SubmitForm() {
    var suc = function(obj) {
             var data = obj.data;
         // submit the data to a url;
            }
    var err = function(obj) {
           while(var t = obj.getNextMessage()) {
         $("#errorDiv").append("<div>"+t.message+"</div>");
           }
           }
    formBridge.submitForm({success:suc,error:err}); // not passing a context means that this will be formBridge itself. Validation errors will be checked.
  }
```
