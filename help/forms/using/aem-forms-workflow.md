---
title: Processus basé sur l’utilisation de Forms sur OSGi
seo-title: Rapidly build adaptive forms-based processes, automate document services operations, and use Acrobat Sign with AEM workflows
description: Utiliser un processus AEM Forms pour automatiser et créer rapidement des révisions et des approbations pour les services de document de début (par exemple, pour convertir un document de PDF dans un autre format), intégrez le processus de signature Acrobat Sign, etc.
seo-description: Use AEM Forms Workflow to automate and rapidly build review and approvals, to start document services (For example, to convert a PDF document to another format), integrate with Acrobat Sign signature workflow, and more.
uuid: 46be7ec6-d5cc-498a-9484-e66a29527064
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: document_services, publish
discoiquuid: f8df5fa3-3843-4110-a46d-9a524d2657cd
noindex: true
exl-id: fa39a4e8-ae22-4356-8935-44fdf1f4f609
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2902'
ht-degree: 41%

---

# Processus basé sur l’utilisation de Forms sur OSGi {#forms-centric-workflow-on-osgi}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

![](do-not-localize/header.png)

Les entreprises collectent des données à partir de centaines, de milliers de formulaires, de divers systèmes principaux et de sources de données en ligne ou hors ligne. Ils disposent également d’un ensemble dynamique d’utilisateurs pour prendre des décisions sur les données, ce qui implique des processus itératifs de révision et d’approbation.

Outre les workflows de révision et d’approbation pour les audiences internes et externes, les grandes entreprises et entreprises ont des tâches répétitives. Par exemple, la conversion d’un document de PDF dans un autre format. Lorsque ces tâches sont effectuées manuellement, elles nécessitent beaucoup de temps et de ressources. Les entreprises ont également des exigences légales pour signer numériquement un document et archiver les données de formulaire en vue d’une utilisation ultérieure dans des formats prédéfinis.

## Présentation du processus basé sur l’utilisation de Forms sur OSGi {#introduction-to-forms-centric-workflow-on-osgi}

Vous pouvez utiliser des processus AEM pour créer rapidement des processus basés sur des formulaires adaptatifs. Ces processus peuvent être utilisés pour la révision et l’approbation, les flux de processus d’entreprise, pour démarrer les services de document, pour intégrer le processus de signature Acrobat Sign et d’autres opérations similaires. Par exemple, le traitement d’une demande de carte de crédit, les processus d’approbation de congés des employés et l’enregistrement d’un formulaire en tant que document de PDF. De plus, ces workflows peuvent être utilisés au sein d’une organisation ou par un pare-feu réseau.

Avec le processus basé sur l’utilisation de Forms on OSGi, vous pouvez rapidement créer et déployer des processus pour différentes tâches sur la pile OSGi, sans avoir à installer la fonctionnalité Process Management complète sur la pile JEE. Le développement et la gestion des workflows utilisent les fonctionnalités familières de workflow AEM et de boîte de réception AEM. Les processus forment la base de l’automatisation des processus réels d’entreprise, qui s’étendent sur plusieurs systèmes logiciels, réseaux, services et même organisations.

Une fois configurés, ces processus peuvent être déclenchés manuellement pour terminer un processus défini ou s’exécuter par programmation lorsque les utilisateurs envoient un formulaire ou [gestion des correspondances](/help/forms/using/cm-overview.md) lettre. Grâce à ces nouvelles fonctionnalités de workflow d’AEM, AEM Forms offre deux fonctionnalités distinctes, mais similaires. Dans le cadre de votre stratégie de déploiement, vous devez décider laquelle vous convient. Référez-vous à la [comparaison](/help/forms/using/capabilities-osgi-jee-workflows.md) des workflows centrés sur les formulaires AEM sur OSGi et de la gestion des processus sur JEE. De plus, pour la topologie de déploiement, voir [Topologies d’architecture et de déploiement pour AEM Forms](/help/forms/using/aem-forms-architecture-deployment.md).

Le processus basé sur l’utilisation de Forms sur OSGi étend la [boîte de messagerie AEM](/help/sites-authoring/inbox.md) et fournit des composants supplémentaires (étapes) pour que l’éditeur du processus AEM ajoute la prise en charge des processus AEM basés sur l’utilisation d’AEM Forms. La boîte de réception d’AEM étendue présente des fonctionnalités similaires à [Espace de travail AEM Forms](/help/forms/using/introduction-html-workspace.md). Outre la gestion des workflows pour intervenants humains (approbation, révision, etc.), vous pouvez utiliser des workflows AEM pour automatiser [Services de document](/help/sites-developing/workflows-step-ref.md)les opérations liées (par exemple, Générer un PDF) et la signature électronique de documents (Acrobat Sign).

Le diagramme suivant illustre le processus complet de création, d’exécution et contrôle d’un processus basé sur l’utilisation de Forms sur OSGi.

![introduction-à-aem-forms-workflow](assets/introduction-to-aem-forms-workflow.jpg)

## Avant de commencer {#before-you-start}

* Un workflow est une représentation d’un processus d’entreprise réel. Préparez votre processus d’entreprise réel et la liste des participants au processus d’entreprise. Par ailleurs, préparez le document (formulaires adaptatifs, documents de PDF, etc.) avant de commencer à créer un processus.
* Un workflow peut comporter plusieurs étapes. Ces étapes sont affichées dans la boîte de réception AEM et permettent de signaler la progression du workflow. Divisez votre processus d’entreprise en étapes logiques.
* Vous pouvez configurer l’étape Affecter une tâche de AEM Workflows pour envoyer des notifications par e-mail aux utilisateurs ou aux personnes désignées. Donc, [activer les notifications par e-mail ;](#configure-email-service).
* Un workflow peut également utiliser Acrobat Sign pour les signatures numériques. Si vous prévoyez d’utiliser Acrobat Sign dans un workflow, la variable [configuration d’Acrobat Sign pour AEM Forms](/help/forms/using/adobe-sign-integration-adaptive-forms.md) avant de l’utiliser dans un workflow.

## Créer un modèle de processus {#create-a-workflow-model}

Un modèle de workflow est constitué de la logique et du flux d’un processus d’entreprise. Il est composé d&#39;une série d&#39;étapes. Ces étapes sont des composants AEM. Vous pouvez étendre les étapes de workflow avec des paramètres et des scripts pour proposer davantage de fonctionnalités et de contrôle, selon les besoins. AEM Forms fournit quelques étapes en plus de AEM étapes prêtes à l’emploi. Pour obtenir la liste détaillée des étapes AEM et AEM Forms, voir [Référence AEM étape de processus](/help/sites-developing/workflows-step-ref.md) et [Processus basé sur l’utilisation de Forms sur OSGi - Référence des étapes](/help/forms/using/aem-forms-workflow.md).

AEM fournit une interface utilisateur intuitive pour créer un modèle de workflow à l’aide des étapes de workflow fournies. Pour obtenir des instructions détaillées sur la création d’un modèle de processus, voir [Création de modèles de processus](/help/sites-developing/workflows-models.md). L’exemple suivant fournit des instructions étape par étape pour créer un modèle de processus pour un processus d’approbation et de révision :

>[!NOTE]
>
>Vous devez être membre du groupe d’éditeurs de processus pour créer ou modifier un modèle de processus.

### Création d’un modèle pour un processus d’approbation et de révision {#create-a-model-for-an-approval-and-review-workflow}

Les processus d’approbation et de révision concernent les tâches qui nécessitent une intervention humaine pour prendre des décisions. L’exemple suivant crée un modèle de processus pour une demande de prêt immobilier à remplir par un agent bancaire du bureau principal. Une fois la demande remplie, elle est envoyée pour approbation. Par la suite, la demande approuvée est envoyée au demandeur pour signature électronique à l’aide d’Acrobat Sign.

L’exemple est disponible en tant que package joint ci-dessous. Importez et installez l’exemple à l’aide du gestionnaire de packages. Vous pouvez également effectuer les étapes suivantes pour créer manuellement le modèle de workflow de l’application :

L’exemple crée un modèle de workflow dans lequel une demande de prêt immobilier doit être remplie par un agent bancaire de première ligne. Une fois remplie, la demande est envoyée pour approbation. Par la suite, la demande approuvée est envoyée au client pour signature électronique à l’aide d’Acrobat Sign. Vous pouvez importer et installer l’exemple à l’aide du gestionnaire de packages.

[Obtenir le fichier](assets/example-mortgage-loan-application.zip)

1. Ouvrez la console Modèles de processus. L’URL par défaut est `https://[Server]:[port]/libs/cq/workflow/admin/console/content/models.html/etc/workflow/models`
1. Sélectionnez **[!UICONTROL Créer]**, puis **[!UICONTROL Créer un modèle]**. La boîte de dialogue Ajouter un modèle de processus s’ouvre.
1. Saisissez **[!UICONTROL Titre]** et **[!UICONTROL Nom]** (facultatif). par exemple, une demande de prêt immobilier. Appuyez sur **[!UICONTROL Terminé]**.
1. Sélectionnez le processus nouvellement créé et appuyez sur **Modifier.** Désormais, vous pouvez ajouter des étapes de processus pour créer une logique d’entreprise. Lorsque vous créez un modèle de processus pour la première fois, il contient :

   * Les étapes : Début de flux et Fin de flux. Ces étapes représentent le début et la fin du workflow. Ces étapes sont requises et ne peuvent pas être modifiées ni supprimées.
   * Un exemple d’étape Participant, dont le nom est Étape 1. Cette étape est configurée pour affecter un élément de travail à l’utilisateur administrateur. Supprimez cette étape.

1. Activez les notifications électroniques. Vous pouvez configurer le processus basé sur l’utilisation de Forms sur OSGi pour qu’il envoie des notifications électroniques aux utilisateurs ou personnes désignées. Effectuez les configurations suivantes pour activer les notifications électroniques :

   1. Accédez au gestionnaire de configuration AEM à l’adresse `https://[server]:[port]/system/console/configMgr`.
   1. Ouvrez la configuration du **[!UICONTROL Service de messagerie Day CQ]**. Spécifiez une valeur pour les champs **[!UICONTROL Nom d’hôte du serveur SMTP]**, **[!UICONTROL Port du serveur SMTP]** et **[!UICONTROL Adresse de l’expéditeur]**. Cliquez sur **[!UICONTROL Enregistrer]**.
   1. Ouvrez la configuration de **[!UICONTROL Day CQ Link Externalizer]**. Dans le champ **[!UICONTROL Domaines]**, spécifiez le nom de hôte /l’adresse IP et le numéro de port réels pour les instances locale, de l’auteur et de publication. Cliquez sur **[!UICONTROL Enregistrer]**.

1. Créez des étapes de workflow. Un workflow peut comporter plusieurs étapes. Ces étapes sont affichées dans la boîte de réception AEM et signalent la progression du workflow.

   Pour définir une étape, appuyez sur l’icône ![info-circle](assets/info-circle.png) pour ouvrir les propriétés de modèle de processus, ouvrez l’onglet **[!UICONTROL Étapes]**, ajoutez des étapes au modèle de processus et appuyez sur **[!UICONTROL Enregistrer et fermer]**. Pour l’exemple de demande de prêt immobilier, créez des étapes : demande de prêt, état de la demande de prêt, documents à signer et document de prêt signé.

1. Glissez-déposez l’explorateur d’étapes **[!UICONTROL Affecter une tâche]** dans le modèle de processus. Faites-en la première étape du modèle.

   Le composant Affecter une tâche affecte la tâche, créée par le workflow, à un utilisateur ou à un groupe. En plus d’affecter la tâche, vous pouvez utiliser le composant pour spécifier un formulaire adaptatif ou un PDF non interactif pour la tâche. Le formulaire adaptatif est requis pour accepter les entrées des utilisateurs et des PDF non interactifs ou un formulaire adaptatif en lecture seule est utilisé pour les processus de révision uniquement.

   Vous pouvez également utiliser l’étape pour contrôler le comportement de la tâche. Par exemple, la création d’un document d’enregistrement automatique, l’affectation de la tâche à un utilisateur ou à un groupe spécifique, le chemin des données envoyées, le chemin des données à pré-remplir et les actions par défaut. Pour obtenir des informations détaillées sur les options de l’étape d’affectation de tâche, consultez le document [Référence sur les étapes du processus basé sur l’utilisation de Forms sur OSGi](/help/forms/using/aem-forms-workflow.md).

   ![workflow-editor](assets/workflow-editor.png)

   Pour l’exemple de demande de prêt immobilier, configurez l’étape Affecter une tâche pour utiliser un formulaire adaptatif en lecture seule et afficher le document PDF une fois la tâche terminée. Par ailleurs, sélectionnez le groupe d’utilisateurs autorisé à approuver la demande de prêt. Dans l’onglet **[!UICONTROL Actions]**, désactivez l’option **[!UICONTROL Envoyer]**. Spécifiez un **[!UICONTROL Variable d’itinéraire]**. Par exemple, actionTaken. Ajoutez également les itinéraires Approuver et Rejeter . Les itinéraires sont affichés sous forme d’actions distinctes (boutons) dans AEM boîte de réception. Le workflow sélectionne une branche en fonction de l’action (bouton) sur laquelle appuie l’utilisateur.

   Vous pouvez importer l’exemple de package, disponible pour téléchargement au début de la section, pour l’ensemble complet des valeurs de tous les champs de l’étape Affecter une tâche configurée, par exemple la demande de prêt immobilier.

1. Faites glisser et déposez le composant Division OU de l’explorateur d’étapes vers le modèle de workflow. L’étape de division OU divise le processus et une seule branche est active par la suite. Cette étape permet d’ajouter des chemins de traitement conditionnels dans le processus. Vous ajoutez des étapes de processus à chaque branche selon vos besoins.

   Ouvrez les propriétés de la Division OU et ajoutez les fragments de code suivants à Branch1 et Branch2. Ces fragments de code permettent de choisir une branche en fonction de l’action de l’utilisateur dans AEM boîte de réception.

   **Fragment de code pour la Branche 1**

   Lorsqu’un utilisateur clique sur le bouton **[!UICONTROL Approuver]** dans la boîte de réception AEM, la Branche 1 est activée.

   ```
   function check(){
      var action = workflowData.getMetaDataMap().get("actionTaken","");
   log.info("action " + action);
      return action=="Approve";
   }
   ```

   **Fragment de code pour la Branche 2**

   Lorsqu’un utilisateur clique sur **[!UICONTROL Refuser]** dans la boîte de réception AEM, la Branche 2 est activée.

   ```
   function check(){
      var action = workflowData.getMetaDataMap().get("actionTaken","");
   log.info("action " + action);
      return action=="Reject";
   }
   ```

1. Ajoutez d’autres étapes de processus pour créer une logique d’entreprise.

   Pour l’exemple de prêt immobilier, ajoutez un document d’enregistrement généré, deux étapes d’affectation de tâche et une étape de document de signe à la Branche 1 du modèle, comme illustré ci-dessous. Une étape Affecter une tâche consiste à afficher et envoyer des **documents de prêt à signer au demandeur** et un autre composant de tâche consiste à **afficher les documents signés**. Ajoutez également un composant Affecter une tâche à la branche 2. Il est activé lorsqu’un utilisateur clique sur Refuser dans la boîte de réception AEM.

   Pour obtenir l’ensemble complet des valeurs de tous les champs des étapes d’affectation de tâche, de l’étape de document d’enregistrement et de l’étape de signature de document configurée par exemple de demande de prêt immobilier, importez l’exemple de package, disponible au téléchargement au début de cette section.

   Le modèle de workflow est prêt. Vous pouvez lancer le workflow de différentes manières. Pour plus d’informations, voir [Lancement d’un processus Forms sur OSGi](#launch).

   ![workflow-editor-mortgage](assets/workflow-editor-mortgage.png)

## Créer une demande de processus basée sur l’utilisation de Forms {#create-a-forms-centric-workflow-application}

L’application est le formulaire adaptatif associé au processus. Lorsqu’une demande est envoyée via la boîte de réception, elle lance le processus associé. Pour rendre un processus Forms disponible en tant qu’application dans AEM boîte de réception et l’application AEM Forms, procédez comme suit pour créer une application de processus :

>[!NOTE]
>
>Vous devez être membre du groupe administrateur-fd pour être en mesure de créer et de gérer les demandes de processus.

1. Sur votre instance d’auteur AEM, accédez à ![outils](assets/tools.png) > **[!UICONTROL Forms]** > **[!UICONTROL Gestion de l’application de workflow]** et taps **[!UICONTROL Créer]**.
1. Dans la fenêtre Créer une application de processus, saisissez des entrées pour les champs suivants, puis appuyez sur **[!UICONTROL Créer]**. Une nouvelle demande est créée et est répertoriée dans l’écran Demandes de processus.

<table> 
 <tbody> 
  <tr> 
   <td>Champ</td> 
   <td>Description</td> 
  </tr> 
  <tr> 
   <td>Titre</td> 
   <td>Le titre est visible dans AEM boîte de réception et permet aux utilisateurs de choisir une application. Soyez descriptif. Par exemple, Demande d’ouverture de compte d’épargne.<br /> </td> 
  </tr> 
  <tr> 
   <td>Nom </td> 
   <td>Indiquez le nom de la demande. Tous les caractères autres que les lettres, chiffres, tirets et traits de soulignement ont été remplacés par des tirets. </td> 
  </tr> 
  <tr> 
   <td>Description</td> 
   <td>La description est visible dans AEM boîte de réception. Indiquez des informations détaillées sur l’application dans les champs de description. Par exemple, Objectif de la demande.<br /> </td> 
  </tr> 
  <tr> 
   <td>Formulaire adaptatif</td> 
   <td><p>Spécifiez le chemin d’un formulaire adaptatif. Lorsqu’un utilisateur démarre une application, le formulaire adaptatif spécifié s’affiche.</p> <p><strong>Remarque :</strong> Les demandes de processus ne prennent pas en charge les formulaires et documents PDF de plus d’une page ou qui nécessitent un défilement sur l’iPad d’Apple. Lorsqu’une demande est ouverte sur un iPad d’Apple et que la longueur du formulaire adaptatif ou du document PDF dépasse une page, les champs de formulaire et le contenu de la deuxième page sont perdus.</p> </td> 
  </tr> 
  <tr> 
   <td>Groupes d’accès</td> 
   <td><p>Sélectionnez un groupe. L’application est visible dans AEM boîte de réception uniquement pour les membres du groupe sélectionné. L’option Accès au groupe permet de sélectionner tous les groupes du groupe d’utilisateurs du processus. </p> <br /> </td> 
  </tr> 
  <tr> 
   <td>Service de préremplissage</td> 
   <td>Sélectionnez une <a href="/help/forms/using/prepopulate-adaptive-form-fields.md#aem-forms-custom-prefill-service" target="_blank">service prefill</a> pour le formulaire adaptatif.<br /> </td> 
  </tr> 
  <tr> 
   <td>Modèle de workflow</td> 
   <td>Sélectionnez une <a href="/help/forms/using/aem-forms-workflow.md#create-a-workflow-model">modèle de workflow</a> pour l’application. Un modèle de processus se compose de la logique et du flux de processus d’entreprise. </td> 
  </tr> 
  <tr> 
   <td>Chemin d'accès au fichier de données</td> 
   <td>Spécifiez le chemin d’accès du fichier de données dans le référentiel crx-repository. Le chemin d’accès est relatif à la charge utile du formulaire adaptatif et contient le nom du fichier de données. Intégrez toujours le nom complet du fichier, y compris son extension, le cas échéant. Par exemple, [charge utile]/data.xml. </td> 
  </tr> 
  <tr> 
   <td>Chemin d’accès de la pièce jointe</td> 
   <td>Spécifiez le chemin d’accès du dossier de pièces jointes dans le référentiel crx-repository. Le chemin d’accès de la pièce jointe est relatif à l’emplacement de la charge utile. Par exemple, [charge utile]/data.xml. </td> 
  </tr> 
  <tr> 
   <td>Chemin d’accès du document d’enregistrement</td> 
   <td>Spécifiez le chemin du fichier Document d’enregistrement dans le référentiel crx. Le chemin est relatif à l’emplacement de la charge utile du formulaire adaptatif. Intégrez toujours le nom complet du fichier, y compris son extension, le cas échéant. Par exemple, [charge utile]/DOR/creditcard.pdf.</td> 
  </tr> 
 </tbody> 
</table>

## Lancement d’un processus basé sur l’utilisation de Forms sur OSGi {#launch}

Vous pouvez lancer ou déclencher un workflow centré sur Forms en procédant comme suit :

* [Envoyer une demande depuis la boîte de réception AEM](#inbox)
* [Envoyant une demande depuis l’application AEM Forms](#afa)

* [Envoi d’un formulaire adaptatif](#af)
* [Utilisant le dossier de contrôle](#watched)

* [Envoyer une communication interactive ou une lettre](#letter)

### Envoyer une demande depuis la boîte de réception AEM {#inbox}

La demande de processus que vous avez créée est disponible en tant qu’application dans la boîte de réception. Les utilisateurs membres du groupe d’utilisateurs de processus peuvent remplir et envoyer l’application qui déclenche le processus associé. Pour plus d’informations sur l’utilisation de la boîte de réception AEM pour envoyer des demandes et gérer des tâches, voir [Gestion des applications et des tâches Forms dans la boîte de réception AEM](/help/forms/using/manage-applications-inbox.md).

### Envoyant une demande depuis l’application AEM Forms {#afa}

L’application AEM Forms se synchronise avec un serveur AEM Forms et vous permet de modifier les données de formulaire, les tâches, les demandes de processus et les informations enregistrées (brouillons/modèles) dans votre compte. Pour plus d’informations, consultez [Application AEM Forms](/help/forms/using/aem-forms-app.md) et les articles connexes.

### Envoi d’un formulaire adaptatif {#af}

Vous pouvez configurer les actions d’envoi d’un formulaire adaptatif pour démarrer un processus lors de l’envoi du formulaire adaptatif. Les formulaires adaptatifs fournissent la variable **[!UICONTROL Appeler un workflow d’AEM]** Action d’envoi pour démarrer un processus lors de l’envoi d’un formulaire adaptatif. Pour plus d’informations sur l’action d’envoi, voir [Configuration de l’action Envoyer](/help/forms/using/configuring-submit-actions.md). Pour envoyer un formulaire adaptatif via l’application AEM Forms, activez l’option Synchroniser avec l’application AEM Forms dans les propriétés du formulaire adaptatif.

Vous pouvez configurer un formulaire adaptatif pour synchroniser, envoyer et déclencher un processus à partir de l’application AEM Forms. Pour plus d’informations, voir [utilisation d’un formulaire](/help/forms/using/working-with-form.md).

### Utilisation d’un dossier de contrôle {#watched}

Un administrateur (membre du groupe fd-administrateurs) peut configurer un dossier réseau pour exécuter un workflow préconfiguré lorsqu’un utilisateur y place un fichier (tel qu’un fichier de PDF). Une fois le workflow terminé, il peut enregistrer le fichier de résultat dans un dossier de sortie spécifié. Ce dossier est connu sous le nom de [Watched Folder](/help/forms/using/watched-folder-in-aem-forms.md). Procédez comme suit pour configurer un dossier de contrôle afin de lancer un workflow :

1. Sur votre instance d’auteur AEM, accédez à ![outils](assets/tools.png) **[!UICONTROL Forms > Configurer le dossier de contrôle]**.  Une liste de dossiers de contrôle déjà configurés s’affiche.
1. Appuyez sur **[!UICONTROL Nouveau]**. Une liste de champs s’affiche. Spécifiez une valeur pour les champs suivants afin de configurer un dossier de contrôle pour un workflow :

<table> 
 <tbody> 
  <tr> 
   <td>Champ</td> 
   <td>Description</td> 
  </tr> 
  <tr> 
   <td><span class="uicontrol">Nom</span></td> 
   <td>Indiquez le nom du dossier de contrôle. Ce champ ne prend en charge que les caractères alphanumériques.</td> 
  </tr> 
  <tr> 
   <td><span class="uicontrol">Chemin </span></td> 
   <td>Spécifiez l’emplacement physique du dossier de contrôle. Dans un environnement organisé en grappes, utilisez un dossier réseau partagé accessible à partir du noeud de la grappe AEM.</td> 
  </tr> 
  <tr> 
   <td><span class="uicontrol">Traiter les fichiers avec</span></td> 
   <td>Sélectionnez l’option <span class="uicontrol">Workflow</span>.  </td> 
  </tr> 
  <tr> 
   <td><span class="uicontrol">Modèle de processus</span></td> 
   <td>Sélectionnez un modèle de processus.<br /> </td> 
  </tr> 
  <tr> 
   <td><span class="uicontrol">Modèle de fichier de sortie</span></td> 
   <td>Spécifiez la structure de répertoires pour les fichiers et répertoires de sortie. Vous pouvez également spécifier une <a href="/help/forms/using/admin-help/configuring-watched-folder-endpoints.md" target="_blank">modèle pour les fichiers de sortie et les répertoires</a>.</td> 
  </tr> 
 </tbody> 
</table>

1. Appuyer **[!UICONTROL Avancé]**. Spécifiez une valeur pour le champ suivant et appuyez sur **[!UICONTROL Créer]**. Le dossier de contrôle est configuré pour lancer un processus. Désormais, chaque fois qu’un fichier est placé dans le répertoire d’entrée du dossier de contrôle, le processus spécifié est déclenché.

   | Champ | Description |
   |---|---|
   | Filtre de mappeur de charge | Lorsque vous créez un dossier de contrôle, il crée une structure de dossiers dans le référentiel crx-repository. La structure de dossiers peut servir de charge utile au workflow. Vous pouvez écrire un script pour mapper un workflow d’AEM afin d’accepter les entrées de la structure de dossiers de contrôle. Une implémentation prête à l’emploi est disponible et répertoriée dans le filtre du mappeur de charge. Si vous ne disposez pas d’une implémentation personnalisée, sélectionnez l’implémentation par défaut. |

   L&#39;onglet Avancé contient d&#39;autres champs. La plupart de ces champs contiennent une valeur par défaut. Pour en savoir plus sur tous les champs, voir [Création ou configuration d’un dossier de contrôle](/help/forms/using/creating-configure-watched-folder.md) article.

### Envoi d’une communication interactive ou d’une lettre {#letter}

Vous pouvez associer et exécuter un workflow basé sur l’utilisation de Forms sur OSGi lors de l’envoi d’une communication interactive ou d’une lettre. Dans le système de gestion de contenu, les workflows sont utilisés pour le post-traitement de communications interactives et de lettres. Par exemple, l’envoi par courrier électronique, l’impression, le fax ou l’archivage des lettres finales. Pour obtenir des instructions détaillées, voir [Post-traitement des communications interactives et des lettres](/help/forms/using/submit-letter-topostprocess.md).

## Configurations supplémentaires {#additional-configurations}

### Configuration du service de messagerie {#configure-email-service}

Vous pouvez utiliser les étapes Affecter une tâche et Envoyer un courrier électronique des processus AEM pour envoyer un courrier électronique. Effectuez les étapes suivantes pour spécifier les serveurs de messagerie et d’autres configurations nécessaires pour envoyer un courrier électronique :

1. Accédez au gestionnaire de configuration AEM à l’adresse `https://[server]:[port]/system/console/configMgr`.
1. Ouvrez la configuration du **[!UICONTROL Service de messagerie Day CQ]**. Spécifiez une valeur pour les champs **[!UICONTROL Nom d’hôte du serveur SMTP]**, **[!UICONTROL Port du serveur SMTP]** et **[!UICONTROL Adresse de l’expéditeur]**. Cliquez sur **[!UICONTROL Enregistrer]**.
1. Ouvrez la configuration de **[!UICONTROL Day CQ Link Externalizer]**. Dans le champ **[!UICONTROL Domaines]**, spécifiez le nom de hôte /l’adresse IP et le numéro de port réels pour les instances locale, de l’auteur et de publication. Cliquez sur **[!UICONTROL Enregistrer]**.

### Purge des instances de processus {#purge-workflow-instances}

Réduire le nombre d’instances de processus améliore les performances du moteur de processus. Vous pouvez donc purger régulièrement les instances de processus terminées ou en cours d’exécution du référentiel. Pour plus d’informations, voir [Purge régulière des instances de workflow](/help/sites-administering/workflows-administering.md#regular-purging-of-workflow-instances).
