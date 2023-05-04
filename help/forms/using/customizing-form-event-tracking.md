---
title: Personnalisation du suivi des événements de formulaire
seo-title: Customizing form event tracking
description: Si un utilisateur passe plus de 60 secondes sur un champ, un événement fieldvisit est déclenché et les détails du champ sont envoyés à Adobe SiteCatalyst.
seo-description: If a user spends more than 60 seconds on a field, a fieldvisit event is triggered and the details of the field are sent to Adobe SiteCatalyst.
uuid: 2f790085-2f1a-45be-9a69-6100c76dcae0
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: customization
discoiquuid: 60d67c6b-5994-42ef-b159-ed6edf5cf9d4
exl-id: e07adddb-e904-4a80-9b1c-8028b12c0e37
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '482'
ht-degree: 41%

---

# Personnalisation du suivi des événements de formulaire {#customizing-form-event-tracking}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Les événements suivants sont immédiatement suivis dans un formulaire adaptatif activé par analyse :

<table> 
 <tbody> 
  <tr> 
   <th>Événement</th> 
   <th>Variables disponibles</th> 
  </tr> 
  <tr> 
   <td>render</td> 
   <td>formName, formTitle, formInstance, source</td> 
  </tr> 
  <tr> 
   <td>abandon</td> 
   <td>formName, formTitle, formInstance, panelName, panelTitle</td> 
  </tr> 
  <tr> 
   <td>save</td> 
   <td>formName, formTitle, formInstance, panelName, source</td> 
  </tr> 
  <tr> 
   <td>envoyer</td> 
   <td>formName, formTitle, formInstance, source</td> 
  </tr> 
  <tr> 
   <td>erreur</td> 
   <td>formName, formTitle, fieldName, fieldTitle, panelTitle</td> 
  </tr> 
  <tr> 
   <td>help</td> 
   <td>formName, formTitle, fieldName, fieldTitle, panelTitle</td> 
  </tr> 
  <tr> 
   <td>fieldVisit</td> 
   <td>formName, formTitle, fieldName, fieldTitle, panelTitle<br /> </td> 
  </tr> 
  <tr> 
   <td>panelVisit</td> 
   <td>formName, formTitle, panelName, panelTitle</td> 
  </tr> 
 </tbody> 
</table>

## Personnalisation du délai d’événement de visite de champ {#customizing-the-field-visit-event-timeout}

Dans la configuration par défaut des formulaires AEM, si un utilisateur passe plus de 60 secondes sur un champ, un événement `fieldvisit` est déclenché et les détails du champ sont envoyés à Adobe Analytics. Vous pouvez personnaliser la ligne de base du suivi temporel des champs sous Configuration d’AEM Forms Analytics dans AEM console de configuration (/system/console/configMgr) afin d’augmenter ou de diminuer le délai d’expiration.

## Personnalisation des événements de suivi {#customizing-the-tracking-events}

Vous pouvez modifier la fonction `trackEvent` disponible dans le fichier `/libs/afanalytics/js/custom.js` afin de personnaliser le suivi des événements. Lorsqu’un événement en cours de suivi se produit dans un formulaire adaptatif, la fonction `trackEvent` est appelée. La fonction `trackEvent` accepte deux paramètres : `eventName` et `variableValueMap`.

Vous pouvez évaluer la valeur de *eventName *et *variableValueMap* pour modifier le comportement de suivi des événements. Par exemple, vous pouvez choisir d’envoyer les informations au serveur d’analyse après un certain nombre d’événements d’erreur. Vous pouvez également choisir d’effectuer l’une des personnalisations suivantes :

* Vous pouvez définir un temps limite avant l’envoi de l’événement.
* Vous pouvez conserver un état afin de déterminer l’action à entreprendre, par exemple *fieldVisit* diffuse un événement factice en fonction de la date et de l’heure du dernier événement.
* Vous pouvez utiliser la fonction `pushEvent` pour envoyer l’événement au serveur d’analyse *.*

* Vous pouvez choisir de ne pas diffuser l’événement au serveur d’analyse.

### Échantillon {#sample}

Dans l’exemple suivant, indiquez comme *error* de chaque *fieldName *est conservé.*. *L’événement n’est envoyé au serveur d’analyse que si une erreur se produit.

```
case 'error':
        if(errorOccurred[variableValueMap.fieldName] == true) {
            pushEvent(eventName, variableValueMap)
        }
        errorOccurred[variableValueMap.fieldName] = true;
        break;
```

## Personnalisation de l’événement panelvisit {#customizing-the-panelvisit-event}

Dans la configuration par défaut d’AEM Forms, toutes les 60 secondes, elle est vérifiée si la fenêtre contenant le formulaire adaptatif est principale. Si la fenêtre est active, un événement `panelVisit` est déclenché dans Adobe Analytics. Cela permet de s’assurer que le document ou le formulaire est principal et de calculer la durée de consultation du formulaire ou du document correspondant.

>[!NOTE]
>
>Le nom d’événement utilisé pour contrôler l’activité et calculer la durée de la visite est &quot;panelVisit&quot;. Cet événement est différent de l’événement de visite de panneau répertorié dans le tableau ci-dessus.

Vous pouvez modifier la fonction scheduleHeartBeatCheck disponible dans le fichier `/libs/afanalytics/js/custom.js` pour modifier ou arrêter cet événement envoyé à Adobe Analytics à intervalles réguliers.
