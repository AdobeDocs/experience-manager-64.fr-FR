---
title: Référence sur les étapes de workflow
seo-title: Référence sur les étapes de workflow
description: 'null'
seo-description: 'null'
uuid: 72a64495-d1b1-49e7-8257-d6b2ed36961c
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: extending-aem
content-type: reference
discoiquuid: 25f0e0f7-9570-4748-81cb-ccec6492c0b4
translation-type: tm+mt
source-git-commit: b698a1348df3ec2ab455c236422784d10cbcf7c2
workflow-type: tm+mt
source-wordcount: '2831'
ht-degree: 70%

---


# Référence sur les étapes de workflow{#workflow-step-reference}

Les modèles de workflow se composent d’une série d’étapes de différents types. En fonction de leur type, ces étapes peuvent être configurées et étendues avec des paramètres et des scripts pour fournir les fonctionnalités et le contrôle dont vous avez besoin.

>[!NOTE]
>
>Cette section présente les étapes de workflow standard.
>
>Pour les étapes spécifiques aux modules, voir également :
>
>* [Référence sur les étapes de workflow d’AEM Forms](/help/forms/using/aem-forms-workflow-step-reference.md)
>* [Traitement des ressources à l’aide des workflows et des gestionnaires de médias](/help/assets/media-handlers.md)

>



## Propriétés des étapes  {#step-properties}

Chaque composant d’étape comporte une boîte de dialogue **[!UICONTROL Propriétés d’étape]** qui vous permet de définir et de modifier les propriétés requises.

### Propriétés des étapes – onglet Commun {#step-properties-common-tab}

Une combinaison des propriétés suivantes est disponible pour la plupart des composants d’étape de workflow, sous l’onglet **[!UICONTROL Commun]** de la boîte de dialogue Propriétés :

* **[!UICONTROL Titre]**

   Titre de l’étape.

* **[!UICONTROL Description]**

   Description de l’étape.

* **[!UICONTROL Étape du processus]**

   Sélecteur déroulant auquel appliquer une [étape](/help/sites-developing/workflows.md#workflow-stages) à l’étape.

* **[!UICONTROL Délai dépassé]**

   Période au terme de laquelle l’étape sera &quot;dépassée de délai&quot;.

   Vous pouvez choisir entre : **[!UICONTROL Désactivé]**, **[!UICONTROL Immédiat]**, **[!UICONTROL 1h]**, **[!UICONTROL 6h]**, **[!UICONTROL 12h]**, **[!UICONTROL 24h]**.

* **[!UICONTROL Gestionnaire de dépassement de délai]**

   Gestionnaire qui contrôlera le flux de travail lorsque l&#39;étape expire ; par exemple :

   `Auto Advancer`

* **[!UICONTROL Avance du gestionnaire]**

   Sélectionnez cette option pour avancer automatiquement le flux de travail à l’étape suivante après l’exécution. Si cette option n’est pas sélectionnée, le script de mise en œuvre doit gérer l’avancement du workflow.

#### Propriétés des étapes – onglet Utilisateur/Groupe {#step-properties-user-group-tab}

Les propriétés suivantes sont disponibles pour de nombreux composants d’étape de workflow, sous l’onglet **[!UICONTROL Utilisateur/Groupe]** de la boîte de dialogue Propriétés :

* **[!UICONTROL Avertir l’utilisateur par courrier électronique]**

   * Vous pouvez avertir le ou les participants en leur envoyant un courrier électronique lorsque le workflow atteint l’étape.
   * Si cette option est activée, un courrier électronique est envoyé à l’utilisateur défini par la propriété **[!UICONTROL Utilisateur/Groupe]** ou à chaque membre du groupe si un groupe est défini.

* **[!UICONTROL Utilisateur/Groupe]**

   * Une boîte de sélection déroulante vous permet de localiser et de sélectionner un utilisateur ou un groupe.
   * Si vous attribuez l’étape à un utilisateur spécifique, seul cet utilisateur peut agir sur l’étape.
   * Si vous affectez l&#39;étape à un groupe entier, lorsque le processus atteint cette étape, tous les utilisateurs de ce groupe auront l&#39;action dans leur **[!UICONTROL boîte de réception de flux de travail]**.
   * Voir [Participation à des workflows](/help/sites-authoring/workflows-participating.md) pour plus d’informations.

## Division ET  {#and-split}

Le **[!UICONTROL ET fractionné]** crée une division dans le flux de travaux, après laquelle les deux branches seront principales. Vous ajoutez des étapes de workflow à chaque branche selon vos besoins. Cette étape vous permet d’ajouter plusieurs chemins de traitement dans le workflow. Par exemple, vous pouvez autoriser l’exécution de certaines étapes de révision en parallèle, ce qui représente un réel gain de temps.

![wf-26](assets/wf-26.png)

### Division ET – configuration {#and-split-configuration}

* Modifiez les propriétés **[!UICONTROL AND Split]** :

   * **[!UICONTROL Nom]** fractionné : attribuez un nom à des fins explicatives.
   * Sélectionnez le nombre de branches requis : 2, 3, 4 ou 5.

* Ajoutez des étapes de workflow aux branches selon vos besoins.

   ![wf-27](assets/wf-27.png)

## Étape du conteneur {#container-step}

Une étape **[!UICONTROL Conteneur]** début un autre modèle de processus qui s’exécute en tant que processus enfant.

Ce **[!UICONTROL Conteneur]** vous permet de réutiliser des modèles de processus pour implémenter des séquences d&#39;étapes courantes. Par exemple, un modèle de workflow de traduction peut être utilisé dans plusieurs workflows de modification.

![wf-28](assets/wf-28.png)

### Étape du conteneur – configuration {#container-step-configuration}

Pour configurer l’étape, modifiez et utilisez les onglets suivants :

* [**[!UICONTROL Courant]**](#step-properties-common-tab)
* **[!UICONTROL Conteneur]**

   * **[!UICONTROL Processus secondaire]** : sélectionnez le workflow à démarrer.

## Atteindre l’étape  {#goto-step}

**[!UICONTROL Atteindre l’étape]** permet de spécifier la prochaine étape du modèle de workflow à exécuter, selon le résultat d’un ECMAScript :

* `true` : **[!UICONTROL Atteindre l’étape]** se termine et le moteur de workflow exécute l’étape spécifiée.

* `false` : **[!UICONTROL Atteindre l’étape]** se termine et la logique de routage normale détermine la prochaine étape à exécuter.

**[!UICONTROL Atteindre l’étape]** vous permet de mettre en œuvre des structures de routage avancées dans vos modèles de workflow. Par exemple, pour implémenter une boucle, l&#39;**[!UICONTROL étape d&#39;accès]** peut être définie pour exécuter une étape précédente du flux de travaux, le script évaluant une condition de boucle.

### Atteindre l’étape – configuration {#goto-step-configuration}

Pour configurer l’étape, modifiez et utilisez les onglets suivants :

* [**[!UICONTROL Courant]**](#step-properties-common-tab)
* **[!UICONTROL Processus]**

   * **[!UICONTROL Étape à suivre]** : Sélectionnez l’étape à exécuter.
   * **[!UICONTROL Chemin]** du script : Chemin d’accès à ECMAScript qui détermine si l’étape **** Goto doit être exécutée.
   * **[!UICONTROL Script]** : ECMAScript qui détermine si l’étape **** Goto doit être exécutée.

>[!CAUTION]
>
>Spécifiez le **[!UICONTROL chemin du script]** ou le **[!UICONTROL script]**. Les deux options ne peuvent pas être utilisées simultanément. Si vous spécifiez des valeurs dans les deux propriétés, l’étape utilise le **[!UICONTROL chemin du script]**.

#### Simulation d’une boucle for {#simulating-a-for-loop}

La simulation d’une boucle for requiert que vous comptiez le nombre d’itérations de boucle qui se sont produites :

* Le compte représente généralement un index des éléments qui ont été suivis d’actions dans le workflow.
* Le nombre est évalué comme critère de sortie de la boucle.

Par exemple, pour mettre en œuvre un workflow qui effectue une action sur plusieurs nœuds JCR, vous pouvez utiliser un compteur de boucles en tant qu’index pour les nœuds. Pour conserver le nombre, stockez une valeur `integer` dans la carte de données de l’instance de flux de travaux. Utilisez le script de l’étape définie dans **[!UICONTROL Atteindre l’étape]** pour incrémenter le nombre, ainsi que pour comparer le nombre au critère de sortie.

```
function check(){
   var count=0;
   var keyname="loopcount"
   try{
      if (workflowData.getMetaDataMap().containsKey(keyname)){ 
        log.info("goto script: found loopcount key");
        count= parseInt(workflowData.getMetaDataMap().get(keyname))+1;
      } 
 
     workflowData.getMetaDataMap().put(keyname,count);
 
     }catch(err) {
         log.info(err.message);
         return false;
    }
   if (parseInt(count) <7){
       return true;
   } else {
      return false;
   }
}
```

## Division OU  {#or-split}

La **[!UICONTROL division OU]** crée une division dans le workflow, après quoi seule une branche est active. Cette étape vous permet d’ajouter des chemins de traitement conditionnels dans le workflow. Vous ajoutez des étapes de workflow à chaque branche selon vos besoins.

>[!NOTE]
>
>Pour plus d’informations sur la création d’un fractionnement OU, voir : [https://helpx.adobe.com/experience-manager/using/aem64_workflow_servlet.html](https://helpx.adobe.com/experience-manager/using/aem64_workflow_servlet.html)

![wf-29](assets/wf-29.png)

### Division OU – configuration {#or-split-configuration}

* Modifiez les propriétés **[!UICONTROL OR Split]** :

   * **[!UICONTROL Courant]**

      * Sélectionnez le nombre de branches requis : 2, 3, 4 ou 5.
   * **[!UICONTROL Branche :  *x*>]**

      * **[!UICONTROL Chemin du script]** : chemin d’accès au fichier contenant le script.
      * **[!UICONTROL Script]** : ajoutez le script dans la boîte de dialogue.
      * **[!UICONTROL Chemin par défaut]** : la branche par défaut est suivie lorsque plusieurs branches renvoient la valeur true. Vous pouvez spécifier uniquement une branche par défaut.

   >[!NOTE]
   >
   >Il existe un onglet distinct pour chaque branche :
   >
   >* Les scripts de chaque branche sont évalués un par un.
   >* Les branches sont évaluées de gauche à droite.
   >* Le premier script dont la valeur est true est exécuté.
   >* Si aucune branche n’est évaluée sur true, le flux de travaux n’avance pas.


   >[!CAUTION]
   >
   >Spécifiez le **[!UICONTROL chemin du script]** ou le **[!UICONTROL script]**. Les deux options ne peuvent pas être utilisées simultanément. Si vous spécifiez des valeurs dans les deux propriétés, l’étape utilise le **[!UICONTROL chemin du script]**.

   >[!NOTE]
   >
   >Voir [Définition d’une règle pour une division OUI](/help/sites-developing/workflows-models.md#example-defining-a-rule-for-an-or-split).

* Ajoutez des étapes de workflow aux branches selon vos besoins.

## Étapes et programmes de sélection des participants  {#participant-steps-and-choosers}

### Étape du participant {#participant-step}

Une **[!UICONTROL étape du participant]** vous permet d’attribuer la possession d’une action particulière. Le workflow s’exécute uniquement lorsque l’utilisateur a manuellement reconnu l’étape. Cela est utile lorsque vous souhaitez que quelqu’un d’autre agisse sur le workflow, par exemple, lors d’une étape de révision.

Bien que ceci ne soit pas directement associé, l’autorisation de l’utilisateur doit être prise en compte lors de l’attribution d’une action ; l’utilisateur doit avoir accès à la page qui est la charge utile du workflow.

#### Étape du participant – configuration  {#participant-step-configuration}

Pour configurer l’étape, modifiez et utilisez les onglets suivants :

* [**[!UICONTROL Courant]**](#step-properties-common-tab)
* [**[!UICONTROL Utilisateur/Groupe]**](#step-properties-user-group-tab)

>[!NOTE]
>
>L’initiateur du workflow est toujours averti lorsque :
>
>* le workflow est terminé ;
>* le workflow est interrompu.

>



>[!NOTE]
>
>Certaines propriétés doivent être configurées pour activer les notifications électroniques. Vous pouvez également personnaliser le modèle de courrier électronique ou en ajouter un pour une nouvelle langue. Voir [Configuration de la notification par courrier électronique](/help/sites-administering/notification.md) pour configurer les notifications par courrier électronique dans AEM.

### Étape de participant de la boîte de dialogue {#dialog-participant-step}

Utilisez une **[!UICONTROL étape de participant de boîte de dialogue]** pour collecter des informations provenant de l’utilisateur qui se voit attribuer l’élément de travail. Cette étape est utile pour collecter de petites quantités de données utilisées ultérieurement dans le workflow.

Lors de chaque étape, la boîte de dialogue **[!UICONTROL Terminer l’élément de travail]** contient des champs que vous définissez dans la boîte de dialogue. Les données collectées dans les champs sont stockées dans les nœuds de la charge utile du workflow. Les étapes de workflow suivantes peuvent ensuite lire la valeur à partir du référentiel.

Pour configurer l’étape, vous spécifiez le groupe ou l’utilisateur auquel attribuer l’élément de travail et le chemin de la boîte de dialogue.

#### Étape de participant de boîte de dialogue – configuration  {#dialog-participant-step-configuration}

Pour configurer l’étape, modifiez et utilisez les onglets suivants :

* [**[!UICONTROL Courant]**](#step-properties-common-tab)
* [**[!UICONTROL Utilisateur/Groupe]**](#step-properties-user-group-tab)
* **[!UICONTROL Boîte de dialogue]**

   * **[!UICONTROL Chemin de la boîte de dialogue**] : Chemin d’accès au noeud dialog de la boîte de dialogue [que vous créez](#dialog-participant-step-creating-a-dialog).

#### Étape du participant à la boîte de dialogue - Création d’une boîte de dialogue {#dialog-participant-step-creating-a-dialog}

Pour créer une boîte de dialogue :

* choisir l’endroit où les données résultantes seront [stockées dans la charge utile](#dialog-participant-step-storing-data-in-the-payload) ;
* [définir la boîte de dialogue ; notamment les champs utilisés pour collecter (et enregistrer) les données](#dialog-participant-step-dialog-definition).

#### Étape de participant de boîte de dialogue – stockage des données dans la charge utile {#dialog-participant-step-storing-data-in-the-payload}

Vous pouvez stocker des données de widget dans la charge utile de workflow ou dans les métadonnées d’élément de travail. Le format de la propriété `name` du nœud de widget détermine l’endroit où les données sont stockées.

* **[!UICONTROL Stockage des données avec la charge utile]**

   * Pour stocker les données de widget en tant que propriété de la charge utile du flux de travail, utilisez le format suivant pour la valeur de la propriété name du noeud de widget :

      `./jcr:content/nodename`

   * Les données sont stockées dans la propriété `nodename` du nœud de charge utile. Si le nœud ne contient pas cette propriété, elle est créée.
   * Une fois les données stockées avec la charge utile, les utilisations suivantes de la boîte de dialogue avec la même charge utile remplacent la valeur de la propriété.

* **[!UICONTROL Stockage des données avec l’élément de travail]**

   * Pour stocker les données du widget en tant que propriété des métadonnées de l’élément de travail, utilisez le format suivant pour la valeur de la propriété name :

      `nodename`

   * Les données sont stockées dans la propriété `nodename` de l&#39;élément de travail `metadata`. Les données sont conservées si la boîte de dialogue utilisée ultérieurement présente la même charge utile.

#### Étape de participant de la boîte de dialogue – définition de boîte de dialogue  {#dialog-participant-step-dialog-definition}

1. **[!UICONTROL Structure de boîte de dialogue]**

   Les boîtes de dialogue des étapes de participant de boîte de dialogue sont similaires aux boîtes de dialogue que vous créez pour les composants de création. Elles sont stockées sous :

   `/apps/myapp/workflow/dialogs`

   Les boîtes de dialogue de l’IU standard compatible avec les écrans tactiles présentent la structure de nœud suivante :

   ```xml
   newComponent (cq:Component)
     |- cq:dialog (nt:unstructured)
       |- content 
         |- layout 
           |- items 
             |- column 
               |- items 
                 |- component0
                 |- component1
                 |- ...
   ```

   >[!NOTE]
   >
   >Pour plus d’informations, voir [Création et configuration d’une boîte de dialogue](/help/sites-developing/developing-components.md#creating-and-configuring-a-dialog).

1. **[!UICONTROL Propriété Chemin de la boîte de dialogue]**

   L&#39;**[!UICONTROL étape du participant de la boîte de dialogue]** possède la propriété **[!UICONTROL Chemin de la boîte de dialogue]** (ainsi que les propriétés d&#39;une [étape du participant](#participant-step)). La valeur de la propriété **[!UICONTROL Chemin de la boîte de dialogue]** est le chemin du nœud `dialog` de la boîte de dialogue.

   Par exemple, la boîte de dialogue se trouve dans un composant nommé `EmailWatch` qui est stocké dans le nœud :

   `/apps/myapp/workflows/dialogs`

   Pour l’IU compatible avec les écrans tactiles, la valeur suivante est utilisée pour la propriété **[!UICONTROL Chemin de la boîte de dialogue]** :

   `/apps/myapp/workflow/dialogs/EmailWatch/cq:dialog`

   ![wf-30](assets/wf-30.png)

1. **Exemple de définition de boîte de dialogue**

   Le fragment de code XML suivant représente une boîte de dialogue qui stocke une valeur `String` dans le noeud `watchEmail` du contenu de charge utile. Le nœud de titre représente le composant [textfield](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/components/coral/foundation/form/textfield/index.html) :

   ```xml
   jcr:primaryType="nt:unstructured" 
       jcr:title="Watcher Email Address Dialog" 
       sling:resourceType="cq/gui/components/authoring/dialog">
       <content jcr:primaryType="nt:unstructured"
           sling:resourceType="granite/ui/components/foundation/container">
           <layout jcr:primaryType="nt:unstructured" 
               margin="false" 
               sling:resourceType="granite/ui/components/foundation/layouts/fixedcolumns"
           />
           <items jcr:primaryType="nt:unstructured">
               <column jcr:primaryType="nt:unstructured"
                   sling:resourceType="granite/ui/components/foundation/container">
                   <items jcr:primaryType="nt:unstructured">
                       <title jcr:primaryType="nt:unstructured" 
                           fieldLabel="Notification Email Address" 
                           name="./jcr:content/watchEmails"
                           sling:resourceType="granite/ui/components/foundation/form/textfield"
                       />
                   </items>
               </column>
           </items>
       </content>
   </cq:dialog>
   ```

   Dans le cas de l’IU compatible avec les écrans tactiles, cet exemple produit une boîte de dialogue similaire à la suivante :

   ![chlimage_1-177](assets/chlimage_1-177.png)

### Étape choix dynamique de participant {#dynamic-participant-step}

Le composant **[!UICONTROL Étape choix dynamique de participant]** est semblable à l’**[!UICONTROL étape du participant]** à la différence que le participant est choisi automatiquement à l’exécution.

Pour configurer l’étape, vous sélectionnez un **[!UICONTROL programme de sélection des participants]** qui identifie le participant auquel attribuer l’élément de travail, ainsi qu’une boîte de dialogue.

#### Étape choix dynamique de participant – configuration  {#dynamic-participant-step-configuration}

Pour configurer l’étape, modifiez et utilisez les onglets suivants :

* [**[!UICONTROL Courant]**](#step-properties-common-tab)
* **[!UICONTROL Programme de sélection des participants]**

   * **[!UICONTROL Programme de sélection des participants]** : nom du [programme de sélection des participants que vous créez](#dynamic-participant-step-developing-the-participant-chooser).
   * **[!UICONTROL Arguments]** : tous les arguments requis.
   * **[!UICONTROL E-mail]** : si une notification électronique doit être envoyée à l’utilisateur.

* **[!UICONTROL Boîte de dialogue]**

   * **[!UICONTROL Chemin de la boîte de dialogue]** : chemin du nœud de la [boîte de dialogue que vous créez (avec l’**étape de participant de la boîte de dialogue**)](#dialog-participant-step-creating-a-dialog).

#### Étape choix dynamique de participant – développement du programme de sélection des participants  {#dynamic-participant-step-developing-the-participant-chooser}

Vous créez le programme de sélection des participants. Par conséquent, vous pouvez utiliser toute logique ou tout critère de sélection. Par exemple, le programme de sélection des participants peut sélectionner l’utilisateur (dans un groupe) qui a le moins d’éléments de travail. Vous pouvez créer un nombre illimité de programmes de sélection des participants à utiliser avec des instances différentes du composant **Étape choix dynamique de participant** dans vos modèles de workflow.

Créez un service OSGi ou un ECMAScript qui sélectionne un utilisateur auquel attribuer l’élément de travail.

* **[!UICONTROL ECMAscript]**

   Les scripts doivent inclure une fonction appelée getParticipant qui renvoie un ID utilisateur sous forme de valeur `String`. Stockez vos scripts personnalisés dans, par exemple, le dossier `/apps/myapp/workflow/scripts` ou un sous-dossier.

   Un exemple de script est inclus dans une instance AEM standard :

   `/libs/workflow/scripts/initiator-participant-chooser.ecma`

   >[!CAUTION]
   >
   >Vous ne devez *rien* modifier dans le chemin `/libs`.
   >
   >
   >En effet, le contenu de `/libs` est remplacé lors de la prochaine mise à niveau de votre instance (et peut être remplacé lorsque vous appliquez un correctif logiciel ou un pack de fonctionnalités).

   Ce script choisit l’initiateur de workflow en tant que participant :

   ```
   function getParticipant() {
       return workItem.getWorkflow().getInitiator();
   }
   ```

   >[!NOTE]
   >
   >Le composant **[!UICONTROL Sélecteur de participant de l&#39;initiateur de flux de travail]** étend l&#39;**[!UICONTROL étape du participant dynamique]** et utilise ce script comme implémentation de l&#39;étape.

* **[!UICONTROL Service OSGi]**

   Les services doivent implémenter l&#39;interface [com.day.cq.workflow.exec.ParticipantStepChooser](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/day/cq/workflow/exec/ParticipantStepChooser.html). L’interface définit les membres suivants :

   * `SERVICE_PROPERTY_LABEL` field : Utilisez ce champ pour spécifier le nom du sélecteur de participants. Le nom s’affiche dans la liste des programmes de sélection des participants disponibles dans les propriétés **[!UICONTROL Étape choix dynamique de participant]**.
   * `getParticipant` méthode : Renvoie l’identifiant principal résolu de manière dynamique sous la forme d’une  `String` valeur.

   >[!CAUTION]
   >
   >La méthode `getParticipant` renvoie l&#39;identifiant principal résolu de manière dynamique. Il peut s’agir d’un ID de groupe ou d’utilisateur.
   >
   >
   >Toutefois, un ID de groupe ne peut être utilisé pour une **[!UICONTROL étape de participant]**, lorsqu’une liste de participants est renvoyée. Pour une **[!UICONTROL étape du participant dynamique]**, une liste vide est renvoyée et ne peut pas être utilisée pour la délégation.

   Pour rendre votre mise en œuvre disponible aux composants **[!UICONTROL Étape choix dynamique de participant]**, ajoutez votre classe Java à un lot OSGi qui exporte le service et déployez le lot vers le serveur AEM.

   >[!NOTE]
   >
   >Le **[!UICONTROL programme de sélection aléatoire des participants]** est un exemple de service qui sélectionne un utilisateur aléatoire ( `com.day.cq.workflow.impl.process.RandomParticipantChooser`). L’exemple de composant d’étape **[!UICONTROL Sélection aléatoire de participants]** étend l’**[!UICONTROL étape de participant dynamique]** et utilise ce service comme implémentation de l’étape.

#### Étape choix dynamique de participant – exemple de service Programme de sélection des participants {#dynamic-participant-step-example-participant-chooser-service}

La classe Java suivante met en œuvre l’interface `ParticipantStepChooser`. La classe renvoie le nom du participant qui a initié le workflow. Le code utilise la même logique que celle utilisée par l’exemple de script ( `initator-participant-chooser.ecma`).

L&#39;annotation `@Property` définit la valeur du champ `SERVICE_PROPERTY_LABEL` sur `Workflow Initiator Participant Chooser`.

```java
package com.adobe.example;

import org.apache.felix.scr.annotations.Component;
import org.apache.felix.scr.annotations.Properties;
import org.apache.felix.scr.annotations.Property;
import org.apache.felix.scr.annotations.Service;
import org.osgi.framework.Constants;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;

import com.adobe.granite.workflow.WorkflowException;
import com.adobe.granite.workflow.WorkflowSession;
import com.adobe.granite.workflow.exec.ParticipantStepChooser;
import com.adobe.granite.workflow.exec.WorkItem;
import com.adobe.granite.workflow.metadata.MetaDataMap;

@Component
@Service
@Properties({
        @Property(name = Constants.SERVICE_DESCRIPTION, value = "An example implementation of a dynamic participant chooser."),
        @Property(name = ParticipantStepChooser.SERVICE_PROPERTY_LABEL, value = "Workflow Initiator Participant Chooser (service)") })
public class InitiatorParticipantChooser implements ParticipantStepChooser {

 private Logger logger = LoggerFactory.getLogger(this.getClass());

 public String getParticipant(WorkItem arg0, WorkflowSession arg1,
   MetaDataMap arg2) throws WorkflowException {

  String initiator = arg0.getWorkflow().getInitiator();
  logger.info("Assigning Dynamic Participant Step work item to {}",initiator);

  return initiator;
 }
}
```

Dans la boîte de dialogue des propriétés **[!UICONTROL Étape du participant dynamique]**, la liste **[!UICONTROL Sélecteur de participant]** contient l&#39;élément `Workflow Initiator Participant Chooser (script)`, qui représente ce service.

&quot;Lorsque le modèle de flux de travail est démarré, le journal indique l&#39;identifiant de l&#39;utilisateur qui a lancé le flux de travail et qui est affecté à la tâche. Dans cet exemple, l’utilisateur `admin` a commencé le workflow.

`13.09.2015 15:48:53.037 *INFO* [10.176.129.223 [1347565733037] POST /etc/workflow/instances HTTP/1.1] com.adobe.example.InitiatorParticipantChooser Assigning Dynamic Participant Step work item to admin`

### Étape de participant du formulaire {#form-participant-step}

L’**[!UICONTROL étape de participant du formulaire]** présente un formulaire lorsque l’élément de travail est ouvert. Lorsque l’utilisateur remplit et envoie le formulaire, les données de champs sont stockées dans les nœuds de la charge utile du workflow.

Pour configurer l’étape, vous spécifiez le groupe ou l’utilisateur auquel attribuer l’élément de travail et le chemin du formulaire.

>[!CAUTION]
>
>Cette section traite de la [section Formulaires des composants de base pour la création de pages](/help/sites-authoring/default-components-foundation.md#form).

#### Étape de participant du formulaire – configuration {#form-participant-step-configuration}

Pour configurer l’étape, modifiez et utilisez les onglets suivants :

* [**[!UICONTROL Courant]**](#step-properties-common-tab)
* [**[!UICONTROL Utilisateur/Groupe]**](#step-properties-user-group-tab)
* **[!UICONTROL Formulaire]**

   * **[!UICONTROL Chemin]** du formulaire : Chemin d’accès au  [formulaire que vous créez](#form-participant-step-creating-the-form).

#### Étape de participant du formulaire – création de formulaire {#form-participant-step-creating-the-form}

Créez un formulaire à utiliser avec une **[!UICONTROL étape de participant du formulaire]** de façon normale. Toutefois, les formulaires d’une étape de participant du formulaire doivent avoir les configurations suivantes :

* Le composant **[!UICONTROL Début de formulaire]** doit avoir la propriété **[!UICONTROL Type d&#39;action]** définie sur `Edit Workflow Controlled Resource(s)`.

* Le composant **[!UICONTROL Début de formulaire]** doit avoir une valeur pour la propriété `Form Identifier`.

* Les composants de formulaire doivent présenter la propriété **Nom de l’élément** définie sur le chemin du nœud dans lequel les données de champs sont stockées. Le chemin d’accès doit localiser un noeud dans le contenu de la charge utile du flux de travail. La valeur utilise le format suivant :

   `./jcr:content/path_to_node`

* Le formulaire doit inclure un composant **[!UICONTROL Bouton(s) d’envoi de flux de travail]**. Vous ne configurez pas de propriétés du composant.

Les exigences de votre workflow indiquent où vous devez stocker les données de champs. Par exemple, les données de champs peuvent être utilisées pour configurer les propriétés du contenu de la page. La valeur suivante d’une propriété **[!UICONTROL Nom d’élément]** stocke les données de champ en tant que valeur de la propriété `redirectTarget` du noeud `jcr:content` :

`./jcr:content/redirectTarget`

Dans l’exemple suivant, les données de champ sont utilisées comme contenu d’un composant **[!UICONTROL Texte]** sur la page de charge utile :

`./jcr:content/par/text_3/text`

&quot;Le premier exemple peut être utilisé pour toute page rendue par le composant `cq:Page`. Le second exemple peut uniquement être utilisé lorsque la page de la charge utile inclut un composant **Texte** possédant l’ID `text_3`.

Le formulaire peut se trouver n’importe où dans le référentiel, toutefois les utilisateurs du workflow doivent être autorisés à lire le formulaire.

### Programme de sélection aléatoire des participants  {#random-participant-chooser}

L’étape **[!UICONTROL Programme de sélection aléatoire des participants]** est un programme de sélection des participants qui attribue l’élément de travail généré à un utilisateur qui est choisi de manière aléatoire à partir d’une liste.

![wf-31](assets/wf-31.png)

#### Programme de sélection aléatoire des participants – configuration {#random-participant-chooser-configuration}

Pour configurer l’étape, modifiez et utilisez les onglets suivants :

* [**[!UICONTROL Courant]**](#step-properties-common-tab)
* **[!UICONTROL Arguments]**

   * **[!UICONTROL Participants]** : spécifie la liste des utilisateurs disponibles pour la sélection. Pour ajouter un utilisateur à la liste, cliquez sur **[!UICONTROL Ajouter un élément]**, puis saisissez le chemin du répertoire de base du nœud de l’utilisateur ou l’ID de l’utilisateur. L’ordre des utilisateurs n’affecte pas la probabilité de se voir attribuer un élément de travail.

### Programme de sélection des participants de l’initiateur de workflow  {#workflow-initiator-participant-chooser}

L’étape **[!UICONTROL Programme de sélection des participants de l’initiateur de workflow]** est un programme de sélection des participants qui attribue l’élément de travail généré à l’utilisateur qui a démarré le workflow. Il n’y a aucune propriété à configurer à part les propriétés de l’onglet **[!UICONTROL Courant]**.

#### Programme de sélection des participants de l’initiateur de workflow – configuration  {#workflow-initiator-participant-chooser-configuration}

Pour configurer l’étape, modifiez-la à l’aide des onglets suivants :

* [**[!UICONTROL Courant]**](#step-properties-common-tab)

## Étape du processus  {#process-step}

Une **[!UICONTROL étape du processus]** exécute un ECMAScript ou appelle un service OSGi pour effectuer un traitement automatique.

![wf-32](assets/wf-32.png)

### Étape du processus – configuration {#process-step-configuration}

Pour configurer l’étape, modifiez et utilisez les onglets suivants :

* [**[!UICONTROL Courant]**](#step-properties-common-tab)
* **[!UICONTROL Processus]**

   * **[!UICONTROL Processus]** : mise en œuvre de processus à exécuter. Utilisez le menu déroulant pour sélectionner le service ECMAScript ou OSGi. Pour obtenir des informations sur :

      * les ECMAScripts et les services OSGi standard, voir [Processus intégrés pour les étapes du processus](/help/sites-developing/workflows-process-ref.md) ;
      * Création d’ECMAScripts pour une étape **[!UICONTROL Processus]**, voir [Implémentation d’une étape de processus avec un ECMAScript](/help/sites-developing/workflows-customizing-extending.md#using-ecmascript).
      * Création de services OSGi pour une étape **[!UICONTROL Processus]**, voir [Implémentation d&#39;une étape de processus avec une classe Java](/help/sites-developing/workflows-customizing-extending.md#implementing-a-process-step-with-a-java-class).
   * **[!UICONTROL Avance du gestionnaire]** : sélectionnez cette option pour avancer automatiquement le workflow à l’étape suivante après l’exécution. Si cette option n’est pas sélectionnée, le script de mise en œuvre doit gérer l’avancement du workflow.
   * **[!UICONTROL Arguments]** : arguments à transmettre au processus.


