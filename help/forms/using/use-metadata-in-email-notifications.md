---
title: Utilisation de métadonnées dans une notification électronique
seo-title: Use metadata in an email notification
description: Utilisation de métadonnées pour renseigner des informations dans une notification électronique de processus de formulaires
seo-description: Use metadata to populate information in a forms workflow email notification
uuid: 17e018c9-6bf8-4042-bba9-4ebe449304ac
topic-tags: publish
discoiquuid: bdf13893-630a-43cd-aaeb-c7c16bf4f8a6
exl-id: 248c5adf-23e9-463f-9f29-869ae2426c22
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '938'
ht-degree: 17%

---

# Utilisation de métadonnées dans une notification électronique  {#use-metadata-in-an-email-notification}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Utilisation de métadonnées pour renseigner des informations dans une notification électronique de processus de formulaires

Vous pouvez utiliser l’étape Affecter une tâche pour créer et affecter des tâches à un utilisateur ou à un groupe. Lorsqu’une tâche est assignée à un utilisateur ou à un groupe, une notification est envoyée par e-mail à l’utilisateur défini ou à chaque membre du groupe défini. Un [notification électronique](/help/forms/using/use-custom-email-template-assign-task-step.md) contient le lien de la tâche affectée et des informations relatives à la tâche.

Vous pouvez utiliser des métadonnées dans un modèle de courrier électronique pour remplir de manière dynamique les informations d’une notification électronique. Par exemple, la valeur du titre, de la description, de l’échéance, de la priorité, du workflow et de la dernière date dans la notification électronique suivante est sélectionnée dynamiquement au moment de l’exécution (lorsqu’une notification électronique est générée).

![default-email-template](assets/default-email-template.png)

Les métadonnées sont stockées dans des paires clé-valeur. Vous pouvez spécifier la clé dans le modèle de courrier électronique et la clé est remplacée par une valeur au moment de l’exécution (lorsqu’une notification électronique est générée). Par exemple, dans l’exemple de code ci-dessous, la clé est « $ {workitem_title} ». Il est remplacé par la valeur &quot;Demande de prêt&quot; au moment de l’exécution.

```xml
subject=Task Assigned - ${workitem_title}

message=<html><body>\n\
 <table>\n\
  <tbody>\n\
   <tr>\n\
    <td>\n\
      Sample Company\n\
    </td>\n\
   </tr>\n\
   <tr>\n\
    <td>\n\
     <pre style="font-size: 13px; font-family: Helvetica, Arial, sans-serif;  font-weight: normal; color: #323232;"> Hello ${workitem_assignee},\n\
 The following task has been assigned to you:</pre>\n\
    </td>\n\
   </tr>\n\
   <tr>\n\
    <td>\n\
     <table>\n\
      <tbody>\n\
       <tr style="border-bottom: solid 2px #FFFCF9;">\n\
        <td> TITLE</td>\n\
        <td>\n\
         <p>${workitem_title}</p>\n\
        </td>\n\
       </tr>\n\
                            <tr style="border-bottom: solid 2px #FFFCF9;">\n\
        <td> DESCRIPTION</td>\n\
        <td>\n\
         <p>${workitem_description}</p>\n\
        </td>\n\
       </tr>\n\
       <tr style="border-bottom: solid 2px #FFFCF9;">\n\
        <td> DUE DATE</td>\n\
        <td>\n\
         <p>${workitem_due_date}</p>\n\
        </td>\n\
       </tr>\n\
       <tr style="border-bottom: solid 2px #FFFCF9;">\n\
        <td> PRIORITY</td>\n\
        <td>\n\
         <p>${workitem_priority}</p>\n\
        </td>\n\
       </tr>\n\
       <tr>\n\
        <td> WORKFLOW</td>\n\
        <td>\n\
         <p>${workitem_workflow}</p>\n\
        </td>\n\
       </tr>\n\
      </tbody>\n\
     </table>\n\
    </td>\n\
   </tr>\n\
   <tr style = "text-align: center; vertical-align: middle;">\n\
    <td> \n\
     <a href="${workitem_url}" target="_blank" style="background-color: #1EBBBB; font-size: 18px; line-height: 25px; font-weight: bold; color: #FFFFFF; text-decoration: none; padding: 15px 15px 15px 15px;">Open Task</a>\n\
    </td>\n\
   </tr>\n\
   <tr>\n\
    <td>\n\
     <p><span style="font-size: 12px; font-weight: normal; font-style: italic; color: #919191;">This is an automatically generated email. Please do not reply to this email.</span></p>\n\
    </td>\n\
   </tr>\n\
  </tbody>\n\
 </table>\n\
</body>\n\
</html>\n\
```

## Utilisation de métadonnées générées par le système dans une notification électronique {#using-system-generated-metadata-in-an-email-notification}

Une application AEM Forms fournit plusieurs variables de métadonnées (paires clé-valeur) prêtes à l’emploi. Vous pouvez utiliser ces variables dans un modèle de courrier électronique. La valeur de la variable est basée sur l’application de formulaires associée. Le tableau suivant répertorie toutes les variables de métadonnées prêtes à l’emploi :

<table> 
 <tbody> 
  <tr> 
   <td>Clé</td> 
   <td>Description</td> 
  </tr> 
  <tr> 
   <td>workitem_title</td> 
   <td>Titre de l’application de formulaires associée.</td> 
  </tr> 
  <tr> 
   <td>workitem_url</td> 
   <td>URL d’accès à l’application de formulaires associée.</td> 
  </tr> 
  <tr> 
   <td>workitem_description</td> 
   <td>Description de l’application de formulaires associée.</td> 
  </tr> 
  <tr> 
   <td>workitem_priority</td> 
   <td>Priorité spécifiée pour l’application de formulaires associée.</td> 
  </tr> 
  <tr> 
   <td>workitem_due_date</td> 
   <td>Date de dernière action sur l’application de formulaires associée.</td> 
  </tr> 
  <tr> 
   <td>workitem_workflow</td> 
   <td>Nom du processus associé à l’application de formulaires.</td> 
  </tr> 
  <tr> 
   <td>workitem_assign_timestamp</td> 
   <td>Date et heure auxquelles l’élément de workflow a été affecté à la personne désignée actuelle.</td> 
  </tr> 
  <tr> 
   <td>workitem_assignee</td> 
   <td>Nom de la personne désignée actuelle.</td> 
  </tr> 
  <tr> 
   <td>host_prefix</td> 
   <td>URL du serveur de création. Par exemple, https://10.41.42.66:4502<br />. </td> 
  </tr> 
  <tr> 
   <td>publish_prefix</td> 
   <td>URL du serveur de publication. Par exemple, https://10.41.42.66:4503.</td> 
  </tr> 
 </tbody> 
</table>

## Utilisation de métadonnées personnalisées dans une notification électronique {#using-custom-metadata-in-an-email-notification}

Vous pouvez également utiliser des métadonnées personnalisées dans une notification électronique. Les métadonnées personnalisées contiennent des informations en plus des métadonnées générées par le système. Par exemple, les détails de la stratégie récupérés à partir d’une base de données. Vous pouvez utiliser une offre groupée ECMAScript ou OSGi pour ajouter des métadonnées personnalisées dans le référentiel crx :

### Utilisation de ECMAScript pour ajouter des métadonnées personnalisées  {#use-ecmascript-to-add-custom-metadata}

[ECMAScript](https://fr.wikipedia.org/wiki/ECMAScript) est un langage de script. Il est utilisé pour les applications de script et de serveur côté client. Pour utiliser ECMAScript afin d’ajouter des métadonnées personnalisées pour un modèle de courrier électronique, procédez comme suit :

1. Connectez-vous à CRX DE avec un compte d’administration. L’URL est `https://[server]:[port]/crx/de/index.jsp`

1. Accédez à /apps/fd/dashboard/scripts/metadataScripts. Créez un fichier avec l’extension .ecma. Par exemple, usermetadata.ecma

   Si le chemin d’accès mentionné ci-dessus n’existe pas, créez-le.

1. Ajoutez du code au fichier .ecma qui possède la logique pour générer des métadonnées personnalisées dans des paires clé-valeur. Par exemple, le code ECMAScript suivant génère des métadonnées personnalisées pour une police d’assurance :

   ```
   function getUserMetaData()  {
       //Commented lines below provide an overview on how to set user metadata in map and return it.
       var HashMap = Packages.java.util.HashMap;
       var valuesMap = new HashMap();
       valuesMap.put("policyNumber", "2017568972695");
       valuesMap.put("policyHolder", "Adobe Systems");
   
       return valuesMap;
   }
   ```

1. Cliquez sur Enregistrer tout. Désormais, le script peut être sélectionné dans AEM modèle de workflow.

   ![assigntask-metadata](assets/assigntask-metadata.png)

1. (Facultatif) Spécifiez le titre du script :

   Si vous ne spécifiez pas le titre, le champ Métadonnées personnalisées affiche le chemin d’accès complet au fichier ECMAScript. Pour définir un titre significatif pour le script, procédez comme suit :

   1. Développez le nœud du script, cliquez avec le bouton droit de la souris sur **[!UICONTROL jcr:content]**, puis cliquez sur **[!UICONTROL Mixins]**.
   1. Type mix:title dans la boîte de dialogue Modifier les mixins, puis cliquez sur **+**.
   1. Ajoutez une propriété avec les valeurs suivantes.

      | Nom | jcr:title |
      |---|---|
      | Type | Chaîne |
      | Valeur | Indiquez le titre du script. Par exemple, des métadonnées personnalisées pour le détenteur de la stratégie. La valeur spécifiée s’affiche à l’étape Affecter une tâche. |

### Utilisation d’un lot OSGi et d’une interface Java pour ajouter des métadonnées personnalisées {#use-an-osgi-bundle-and-java-interface-to-add-custom-metadata}

Vous pouvez utiliser l’interface Java WorkitemUserMetadataService pour ajouter des métadonnées personnalisées pour les modèles de courrier électronique. Vous pouvez créer un lot OSGi qui utilise l’interface Java WorkitemUserMetadataService et le déployer sur le serveur AEM Forms. Les métadonnées peuvent être sélectionnées à l’étape Affecter une tâche .

Pour créer un lot OSGi avec une interface Java, ajoutez [SDK client AEM Forms](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=fr) jar et [jar granite](https://repo.adobe.com/nexus/content/groups/public/com/adobe/granite/com.adobe.granite.workflow.api/1.0.2/) comme dépendances externes au projet de bundle OSGi. Vous pouvez utiliser n’importe quel IDE Java pour créer un bundle OSGi. La procédure suivante décrit l’utilisation d’Eclipse pour créer un lot OSGi :

1. Ouvrez Eclipse IDE. Accédez à Fichier > Nouveau projet.

1. Sur l’écran de sélection de l’assistant, sélectionnez Projet Maven puis cliquez sur Suivant.

1. Sur le projet New Maven, conservez les valeurs par défaut, puis cliquez sur Suivant. Sélectionnez un archétype et cliquez sur Suivant. Par exemple, maven-archetype-quickstart. Indiquez l’ID de groupe, l’ID d’artefact, la version et le package du projet, puis cliquez sur Terminer. Le projet est créé.

1. Ouvrez le fichier pom.xml pour modifier et remplacer tout le contenu du fichier par ce qui suit :

   ```
   
   ```

1. Ajoutez le code source qui utilise l’interface Java WorkitemUserMetadataService pour ajouter des métadonnées personnalisées aux modèles de courrier électronique. Voici un exemple de code :

   ```java
   package com.aem.impl;
   
   import com.adobe.fd.workspace.service.external.WorkitemUserMetadataService;
   import org.apache.felix.scr.annotations.Component;
   import org.apache.felix.scr.annotations.Properties;
   import org.apache.felix.scr.annotations.Property;
   import org.apache.felix.scr.annotations.Service;
   import org.osgi.framework.Constants;
   
   import java.util.HashMap;
   import java.util.Map;
   
   @Component
   @Service
   @Properties({
           @Property(name = Constants.SERVICE_DESCRIPTION, value = "A sample implementation of a user metadata service."),
           @Property(name = WorkitemUserMetadataService.SERVICE_PROPERTY_LABEL, value = "Default User Metadata Service")})
   
   public class WorkitemUserMetadataServiceImpl
     implements WorkitemUserMetadataService
   {
     public WorkitemUserMetadataServiceImpl() {}
   
     public Map<String, String> getUserMetadataMap()
     {
       HashMap<String, String> metadataMap = null;
       metadataMap = new HashMap();
       metadataMap.put("test_metadata", "tested-interface implementation");
       return metadataMap;
     }
   }
   ```

1. Ouvrez une invite de commande et accédez au répertoire contenant le projet de bundle OSGi. Utilisez la commande suivante pour créer le lot OSGi :

   `mvn clean install`

1. Chargez le lot sur un serveur AEM Forms. Vous pouvez utiliser AEM Package Manager pour importer le lot vers le serveur AEM Forms.

Une fois le bundle importé, vous pouvez sélectionner les métadonnées dans l’étape Affecter une tâche et les utiliser dans un modèle de courrier électronique.
