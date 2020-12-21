---
title: Référence sur les étapes du processus basé sur l’utilisation de Forms on OSGi
seo-title: Référence sur les étapes du processus basé sur l’utilisation de Forms on OSGi
description: Les étapes du processus basé sur l’utilisation de Forms on OSGi vous permettent de créer rapidement des formulaires adaptatifs basés sur des processus.
seo-description: Les étapes du processus basé sur l’utilisation de Forms on OSGi vous permettent de créer rapidement des formulaires adaptatifs basés sur des processus.
uuid: 57c872d6-c6ca-4f78-a98c-f9487f1d673c
contentOwner: aheimoz
discoiquuid: f2bd4d96-55a5-4fbd-bede-1747c2ec63c8
translation-type: tm+mt
source-git-commit: 36baba4ee20dd3d7d23bc50bfa91129588f55d32
workflow-type: tm+mt
source-wordcount: '4561'
ht-degree: 88%

---


# Référence sur les étapes du processus basé sur l’utilisation de Forms on OSGi {#forms-centric-workflow-on-osgi-step-reference}

## Étapes de processus Forms {#forms-workflow-steps}

Les étapes de processus Forms effectuent des opérations spécifiques à AEM Forms dans un processus AEM. Ces étapes vous permettent de créer rapidement des formulaires adaptatifs à partir de processus basés sur l’utilisation de Forms on OSGi. Ces processus peuvent être utilisés pour développer des processus de révision et d’approbation de base, des processus métier internes et sur le pare-feu. Vous pouvez également utiliser les étapes de processus Forms pour lancer les services de document, les intégrer au processus de signature Adobe Sign et effectuer d’autres opérations AEM Forms. Un [module complémentaire AEM Forms](https://www.adobe.com/go/learn_aemforms_documentation_63) est nécessaire pour utiliser ces étapes dans un processus.

## Étape Affecter une tâche  {#assign-task-step}

L’étape Affecter une tâche crée une tâche et l’affecte à un utilisateur ou un groupe. Lors de l’affectation de la tâche, le composant spécifie également le formulaire adaptatif ou le fichier PDF non interactif de la tâche. Le formulaire adaptatif est requis pour accepter une saisie des utilisateurs et un fichier PDF non interactif ou un formulaire adaptatif en lecture seule est utilisé pour les processus de révision uniquement.

Vous pouvez également utiliser le composant pour contrôler le comportement de la tâche. Par exemple : lors de la création d’un document d’enregistrement automatique, lors de l’affectation de la tâche à un utilisateur ou un groupe spécifique, lors de l’indication du chemin d’accès des données envoyées, lors de l’indication du chemin d’accès des données pré-renseignées et des actions par défaut. L’étape Affecter une tâche possède les propriétés suivantes :

* **Titre :** titre de la tâche. Le titre s’affiche dans la boîte de réception AEM.
* **Description :** description des opérations en cours dans la tâche. Ces informations sont utiles pour d’autres développeurs de processus lorsque vous travaillez dans un environnement de développement partagé.

* **Chemin d’accès de la miniature :** chemin d’accès de la miniature de la tâche. Si aucun chemin n’est spécifié, une miniature par défaut s’affiche pour un formulaire adaptatif et une icône par défaut s’affiche pour un document d’enregistrement.
* **Phase de processus :** un processus peut se composer de plusieurs phases. Ces phases sont affichées dans la boîte de réception AEM. Vous pouvez définir ces phases dans les propriétés du modèle (Sidekick > Page > Propriétés de la page > Phases).
* **Priorité :** la priorité sélectionnée s’affiche dans la boîte de réception AEM. Les options disponibles sont les suivantes : Elevée, Moyenne et Faible. La valeur par défaut est Moyenne.
* **Date d’expiration :** spécifiez le nombre de jours ou d’heures restant avant que la tâche soit affichée comme En retard. Si vous sélectionnez **Désactivé**, la tâche n’est jamais marquée comme En retard. Vous pouvez également spécifier un gestionnaire de dépassement de délai pour effectuer des tâches spécifiées dès que la tâche est marquée comme En retard.

* **Jours :** le nombre de jours restants pour terminer la tâche. Le nombre de jours est calculé à partir du jour de l’affectation de la tâche à un utilisateur. Si cette option est sélectionnée, si une tâche n’est pas terminée et dépasse le nombre de jours spécifié dans le champ Jours, un gestionnaire de dépassement de délai est déclenché après la date d’expiration.
* **Heures :** le nombre d’heures restantes pour terminer la tâche. Le nombre d’heure est calculé à partir de l’heure de l’affectation de la tâche à un utilisateur. Si cette option est sélectionnée, si une tâche n’est pas terminée et dépasse pas le nombre d’heures spécifié dans le champ Heures, un gestionnaire de dépassement de délai est déclenché après l’heure de l’expiration.
* **Expiration après l’échéance :** sélectionnez cette option pour activer le champ Sélection du gestionnaire de dépassement de délai.
* **Gestionnaire de dépassement de délai :** sélectionnez le script à exécuter lorsque l’étape Affecter une tâche dépasse l’échéance. Les scripts placés dans le référentiel CRX à l’adresse [apps]/fd/tableau de bord/scripts/timeoutHandler peuvent être sélectionnés. Le chemin spécifié n’existe pas dans le référentiel CRX. Un administrateur crée le chemin d’accès avant de l’utiliser.
* **Sélectionner l’action et ajouter un commentaire depuis la dernière tâche dans Détails de la tâche :** sélectionnez cette option pour afficher la dernière action qui a été effectuée et le dernier commentaire reçu dans la section Détails de la tâche.
* **Type :** sélectionnez le type de document à remplir lors du lancement du processus. Vous pouvez sélectionner un formulaire adaptatif, un formulaire adaptatif en lecture seule ou un document PDF non interactif.
* **Utiliser un formulaire adaptatif :** indiquez la méthode pour localiser le formulaire adaptatif d’entrée. Vous pouvez utiliser le formulaire adaptatif disponible à un chemin absolu, envoyé en tant que charge utile au flux de travail, ou disponible à un chemin calculé à l’aide d’une variable. Vous pouvez utiliser une variable de type String pour spécifier le chemin d’accès.
* **Chemin d’accès du formulaire adaptatif** : indiquez le chemin d’accès du formulaire adaptatif. Ce champ est disponible lorsque vous utilisez un formulaire adaptatif ou un formulaire adaptatif en lecture seule dans le champ Type en association avec l’option de chemin absolu dans le champ Utiliser un formulaire adaptatif.
* **Chemin d’accès du fichier PDF :** indiquez le chemin d’accès d’un document PDF non interactif. Le champ apparaît lorsque vous sélectionnez un document PDF non interactif dans le champ Type. Le chemin d’accès est toujours relatif à la charge. Par exemple, [Payload_Directory]/Workflow/PDF/credit-card.pdf. Le chemin n’existe pas dans le référentiel CRX. Un administrateur crée le chemin d’accès avant de l’utiliser. Vous devez activer l’option Document d’enregistrement ou posséder des formulaires adaptatifs basés sur un modèle de formulaire pour utiliser l’option Chemin d’accès du fichier PDF.
* **Une fois la tâche terminée, effectuer le rendu du formulaire adaptatif en tant que** : lorsqu’une tâche est marquée comme terminée, vous pouvez effectuer le rendu du formulaire adaptatif en tant que formulaire adaptatif en lecture seule ou document PDF. Vous devez activer l’option Document d’enregistrement ou posséder des formulaires adaptatifs basés sur un modèle de formulaire pour effectuer le rendu du formulaire adaptatif en tant que Document d’enregistrement.
* **Informations à pré-renseigner :** les champs répertoriés ci-dessous servent de données d’entrées pour la tâche :

   * **Chemin d’accès au fichier de données :** chemin d’accès au fichier de données d’entrée (.json ou.xml). Le chemin d’accès est toujours relatif à la charge. Par exemple, le fichier contient les données envoyées pour le formulaire via une application de boîte de réception AEM. Un exemple de chemin d’accès est [Payload_Directory]/workflow/data.
   * **Chemin d’accès de la pièce jointe :** les pièces jointes disponibles à l’emplacement sont jointes au formulaire associé à la tâche. Le chemin d’accès est toujours relatif à la charge. Un exemple de chemin est [Payload_Directory]/attachments/

* **Informations envoyées :** les champs répertoriés ci-dessous servent d’emplacement de sortie pour la tâche :

   * **Chemin d’accès au fichier de données :** chemin d’accès au fichier de données (.json ou .xml). Le fichier de données contient des informations envoyées via le formulaire associé. Le chemin d’accès est toujours relatif à la charge. Par exemple, [Payload_Directory]/Workflow/data, où les données sont un fichier.
   * **Chemin d’accès de la pièce jointe :** chemin d’accès pour enregistrer les pièces jointes de formulaire fournies dans une tâche.
   * **Chemin d’accès du document d’enregistrement :** chemin d’accès pour enregistrer un fichier de document d’enregistrement. Par exemple, [Payload_Directory]/DocumentofRecord/credit-card.pdf. Le document d’enregistrement n’est pas généré si le champ du chemin d’accès est vide. Le chemin d’accès est toujours relatif à la charge.

* **Options d’affectation :** indiquez la méthode à utiliser pour affecter la tâche à un utilisateur. Vous pouvez affecter la tâche de manière dynamique à un utilisateur ou un groupe à l’aide du script Programme de sélection des participants ou affecter la tâche à un utilisateur ou à un groupe AEM spécifique.
* **Programme de sélection des participants :** cette option est disponible lorsque l’option **Sélectionner de manière dynamique un utilisateur ou un groupe** est activée dans le champ Options d’affectation. Vous pouvez utiliser un script ECMAScript ou un service pour sélectionner de manière dynamique un utilisateur ou un groupe. Pour plus d’informations, voir [Affecter de manière dynamique un processus à des utilisateurs](https://helpx.adobe.com/experience-manager/kb/HowToAssignAWorkflowDynamicallyToParticipants.html) et [Création d’une étape Participant dynamique Adobe Experience Manager personnalisé.](https://helpx.adobe.com/experience-manager/using/dynamic-steps.html)

* **Participants :** le champ est disponible lorsque l’option **[!UICONTROL com.adobe.granite.workflow.core.process.RandomParticipantChooser]** est sélectionnée dans le champ Programme de sélection des participants. Le champ vous permet de sélectionner des utilisateurs ou des groupes pour l’option RandomParticipantChooser.

* **Arguments :** le champ est disponible lorsqu’un script autre que le script RandomParticipantChoose est sélectionné dans le champ Programme de sélection des participants. Le champ vous permet de fournir une liste d’arguments séparés par des virgules pour le script sélectionné dans le champ Programme de sélection des participants.

* **Utilisateur ou groupe :** la tâche est affectée à l’utilisateur ou au groupe sélectionné. Cette option est disponible lorsque l’option **À un utilisateur ou un groupe spécifique** est activée dans le champ Options d’affectation. Le champ répertorie tous les utilisateurs et groupes du groupe d’utilisateurs du processus.

* **Avertir la personne désignée par courrier électronique :** sélectionnez cette option pour envoyer des notifications électroniques à la personne désignée. Ces notifications sont envoyées lorsqu’une tâche est affectée à un utilisateur. Avant d’utiliser cette option, activez les notifications de la console Web AEM. Pour obtenir des instructions détaillées, consultez [Configuration des notifications électroniques à l’étape Affecter une tâche](/help/forms/using/aem-forms-workflow.md)

* **Modèle de courrier électronique HTML** : sélectionnez un modèle de courrier électronique pour la notification électronique. Pour modifier un modèle, modifiez le fichier situé à l’emplacement /libs/fd/dashboard/templates/email/htmlEmailTemplate.txt dans le référentiel CRX.
* **Autoriser la délégation à :** la boîte de réception AEM permet à l’utilisateur connecté de déléguer le processus affecté à un autre utilisateur. Vous pouvez déléguer la tâche au sein du même groupe ou à l’utilisateur du processus d’un autre groupe. Si la tâche est affectée à un utilisateur unique et que l’option **Autoriser la délégation aux membres du groupe désigné** est sélectionnée, vous ne pouvez pas déléguer la tâche à un utilisateur ou à un autre groupe.

* **Actions par défaut :** les actions Prêt à l’emploi, Envoyer, Enregistrer et Réinitialiser sont disponibles. Par défaut, toutes les actions par défaut sont activées.
* **Variable d’itinéraire :** nom de la variable d’itinéraire. La variable d’itinéraire capture les actions personnalisées qu’un utilisateur sélectionne dans la boîte de réception AEM.
* **Itinéraires :** une tâche peut se composer de plusieurs itinéraires. Lorsque cette option est sélectionnée dans la boîte de réception AEM, l’itinéraire renvoie une valeur et les branches du processus en fonction de l’itinéraire sélectionné.
* **Titre** : Indiquez le titre de l&#39;itinéraire. Il s’affiche dans la boîte de réception AEM.
* **Icône Corail** : indiquez l’attribut HTML d’une icône corail. La bibliothèque Adobe CorelUI fournit un vaste ensemble d’icônes tactiles. Vous pouvez sélectionner et utiliser une icône pour l’itinéraire. Elle s’affiche avec le titre dans la boîte de réception AEM.
* **Autoriser la personne désignée à ajouter des commentaires** : sélectionnez cette option pour activer les commentaires pour la tâche. Une personne désignée peut ajouter des commentaires à partir de la boîte de réception AEM au moment de l’envoi de la tâche.
* **Autoriser la personne désignée à ajouter des pièces jointes à la tâche** : sélectionnez cette option pour activer les pièces jointes pour la tâche. Une personne désignée peut ajouter des pièces jointes à partir de la boîte de réception AEM au moment de l’envoi de la tâche.
* **Chemin d’accès de sortie des pièces jointes de la tâche** : indiquez l’emplacement de la pièce jointe. L’emplacement est relatif à la charge.
* **Utiliser des métadonnées personnalisées :** sélectionnez cette option pour activer le champ de métadonnées personnalisées. Les métadonnées personnalisées sont utilisées dans les modèles de courrier électronique.
* **Métadonnées personnalisées :** sélectionnez une métadonnée personnalisée pour les modèles de courrier électronique. La métadonnée personnalisée est disponible dans le référentiel CRX à l’emplacement apps/fd/dashboard/scripts/metadataScripts. Le chemin spécifié n’existe pas dans le référentiel CRX. Un administrateur crée le chemin d’accès avant de l’utiliser. Vous pouvez également utiliser un service pour les métadonnées personnalisées. Vous pouvez également étendre l&#39;interface `WorkitemUserMetadataService` pour fournir des métadonnées personnalisées.

* **Afficher les données des étapes précédentes** : sélectionnez cette option pour permettre aux personnes désignées d’afficher les personnes désignées précédentes, les actions déjà effectuées sur la tâche, les commentaires ajoutés à la tâche et le document d’enregistrement de la tâche terminée, le cas échéant.
* **Afficher les données des étapes suivantes :** sélectionnez cette option pour permettre à la personne actuellement désignée d’afficher l’action effectuée et les commentaires ajoutés à la tâche par les personnes désignées suivantes. Cette option permet également à la personne actuellement désignée d’afficher un document d’enregistrement de la tâche terminée, le cas échéant.
* **Visibilité du type de données :** par défaut, une personne désignée peut afficher un document d’enregistrement, des personnes désignées, une action effectuée et les commentaires des personnes désignées précédentes et suivantes qui ont été ajoutés. Utilisez l’option de visibilité du type de données pour limiter le type de données visibles pour les personnes désignées.

## Etape Envoyer un courrier électronique {#send-email-step}

Utilisez l’étape Envoyer un courrier électronique pour, par exemple, envoyer un courrier électronique avec un document d’enregistrement, un lien d’un formulaire adaptatif, un lien d’une communication interactive ou avec un document PDF joint. L’étape Envoyer un courrier électronique prend en charge [le courrier électronique HTML](https://en.wikipedia.org/wiki/HTML_email). Les courriers électroniques HTML sont réactifs et s’adaptent à différents clients de messagerie et tailles d’écran. Vous pouvez utiliser un modèle de courrier électronique HTML pour définir l’aspect, le modèle de couleurs et le comportement du courrier électronique.

L’étape Envoyer un courrier électronique utilise le service de messagerie Day CQ pour envoyer des messages. Avant d’utiliser l’étape Envoyer un courrier électronique, assurez-vous que [le service de messagerie](/help/forms/using/aem-forms-workflow.md) est configuré. L’étape Envoyer un courrier électronique possède les propriétés suivantes :

**Titre :** le titre de l’étape permet d’identifier l’étape dans l’éditeur du processus.

**Description :** la description est utile pour d’autres développeurs de processus lorsque vous travaillez dans un environnement de développement partagé.

**Objet du message :** l’objet peut être récupéré à partir d’une métadonnée de processus ou être spécifié manuellement. Sélectionnez l’option **Littéral** pour saisir un objet manuellement ou sélectionnez l’option **Récupérer à partir des métadonnées de processus** pour récupérer l’objet d’une propriété de métadonnées.

**Modèle de courrier électronique HTML** : modèle HTML pour le courrier électronique. Vous pouvez spécifier des variables dans un modèle de courrier électronique. L’étape Envoyer un courrier électronique extrait et affiche toutes les variables incluses dans un modèle pour les entrées.

**Métadonnées du modèle de courrier électronique :** la valeur des variables de modèle de courrier électronique peut être une valeur spécifiée par l’utilisateur, le chemin d’accès d’un fichier sur l’auteur ou sur le serveur de publication, l’image ou une propriété de métadonnées de processus.

* **Littéral :** utilisez cette option lorsque vous connaissez la valeur exacte à spécifier. Par exemple, [example@example.com](mailto:example@example.com).

* **Métadonnées de processus :** utilisez cette option lorsque la valeur à utiliser est enregistrée dans une propriété de métadonnées de processus. Après avoir sélectionné cette option, saisissez le nom de la propriété des métadonnées dans la zone de texte vide en dessous de l’option Métadonnées de processus. Par exemple, emailAddress.
* **URL du fichier :** utilisez l’option pour incorporer un lien Web d’une communication interactive avec le courrier électronique. Après avoir sélectionné l’option, recherchez et choisissez la communication interactive à incorporer. Un actif peut résider sur le serveur de création ou de publication.
* **Image :** utilisez cette option pour inclure une image au courrier électronique. Après avoir sélectionné cette option, recherchez et sélectionnez l’image. L’option d’image est disponible uniquement pour les balises d’image (&lt;img src=&quot;&amp;ast;&quot;/>) disponibles dans le modèle de courrier électronique.

**Adresse électronique de l’expéditeur/du Destinataire :** sélectionnez l’option  **** Littéral pour spécifier manuellement une adresse électronique ou sélectionnez l’option  **Récupérer à partir des** métadonnées du flux de travail pour récupérer l’adresse électronique à partir d’une propriété de métadonnées. Vous pouvez également spécifier une liste de tableaux de propriété de métadonnées pour l’option **Récupérer à partir des métadonnées de processus**.

**Chemin d’accès de la pièce jointe de fichier :** l’actif disponible à l’emplacement spécifié est joint au courrier électronique. Le chemin d’accès de l’actif peut être lié à la charge utile ou au chemin d’accès absolu. Un exemple de chemin est [Payload_Directory]/attachments/

**Nom de fichier :** nom du fichier de la pièce jointe au courrier électronique. L’étape de courrier électronique modifie le nom de fichier d’origine de la pièce jointe en le remplaçant par le nom de fichier spécifié. Le nom peut être spécifié manuellement ou récupéré à partir d’une propriété de métadonnées de processus. Utilisez l’option **Littéral** lorsque vous connaissez la valeur exacte à spécifier. Utilisez l’option **Récupérer à partir des métadonnées de processus** lorsque la valeur à utiliser est enregistrée dans une propriété de métadonnées de processus.

## Etape Générer un document d’enregistrement  {#generate-document-of-record-step}

Lorsqu’un formulaire est rempli ou envoyé, vous pouvez conserver un enregistrement du formulaire, au format imprimé ou au format de document. On parle ici de document d’enregistrement (DOR). Vous pouvez utiliser l’étape Générer un document d’enregistrement pour créer une version PDF interactive ou en lecture seule d’un formulaire adaptatif. La version PDF contient des informations remplies dans le formulaire avec la mise en page du formulaire adaptatif.

L’étape Document d’enregistrement possède les propriétés suivantes :

**Utiliser un formulaire** adaptatif : Spécifiez la méthode pour localiser le formulaire adaptatif d’entrée. Vous pouvez utiliser le formulaire adaptatif disponible à un chemin absolu, envoyé en tant que charge utile au flux de travail, ou disponible à un chemin calculé à l’aide d’une variable. Vous pouvez utiliser une variable de type String pour spécifier le chemin d’accès.

**Chemin d’accès du formulaire adaptatif** : indiquez le chemin d’accès du formulaire adaptatif. Ce champ est disponible lorsque vous utilisez un formulaire adaptatif ou un formulaire adaptatif en lecture seule dans le champ Type en association avec l’option de chemin absolu dans le champ Utiliser un formulaire adaptatif.

**Chemin d’accès des données d’entrée :** chemin d’accès des données d’entrée pour le formulaire adaptatif. Vous pouvez conserver les données à un emplacement lié à une charge utile ou spécifier un chemin d’accès absolu des données. Les données d’entrée sont fusionnées avec le formulaire adaptatif pour créer un document d’enregistrement.

**Chemin d’accès de la pièce jointe d’entrée :** chemin d’accès des pièces jointes. Ces pièces jointes sont incluses dans le document d’enregistrement. Vous pouvez conserver les pièces jointes à un emplacement lié à une charge utile ou spécifier un chemin d’accès absolu aux pièces jointes.

Si vous spécifiez le chemin d’accès d’un dossier (des pièces jointes, par exemple), tous les fichiers directement disponibles dans le dossier sont joints au document d’enregistrement. Si des fichiers sont présents dans les dossiers directement disponibles dans le chemin d’accès de la pièce jointe spécifiée, les fichiers sont inclus dans le document d’enregistrement en tant que pièces jointes. Les dossiers présents dans les dossiers directement disponibles sont ignorés.

**Chemin d’accès du document d’enregistrement généré :** spécifiez l’emplacement pour conserver un fichier de document d’enregistrement. Vous pouvez choisir de remplacer le dossier de charge utile ou de placer un document d’enregistrement à un emplacement dans le répertoire de charge utile.

**Paramètre régional** : spécifiez la langue du document d’enregistrement.

## Etape Invoquer le service de modèle de données de formulaire  {#invoke-form-data-model-service-step}

Vous pouvez utiliser l’[intégration de données AEM Forms](/help/forms/using/data-integration.md) pour configurer des sources de données disparates et vous y connecter. Ces sources de données peuvent être une base de données, un service Web, un service REST, un service OData et une solution CRM. L’intégration de données AEM Forms vous permet de créer un modèle de données de formulaire regroupant plusieurs services afin d’effectuer des opérations de récupération, d’ajout et de mise à jour de données sur la base de données configurée. Vous pouvez utiliser **l’étape Invoquer le service de modèle de données de formulaire** pour sélectionner un modèle de données de formulaire (FDM) et utiliser les services du FDM pour récupérer, mettre à jour ou ajouter des données aux sources de données disparates.

Pour mieux comprendre les entrées des champs de l’étape, la table de base de données et le fichier JSON suivants sont utilisés à titre d’exemple :

**Exemple de table CustomerDetails**

<table> 
 <tbody> 
  <tr> 
   <td>Propriétés</td> 
   <td>Valeur<br /> </td> 
  </tr> 
  <tr> 
   <td>Prénom<br /> </td> 
   <td>Sarah<br /> </td> 
  </tr> 
  <tr> 
   <td>Nom de famille</td> 
   <td>Rose</td> 
  </tr> 
  <tr> 
   <td>ID de client</td> 
   <td>1</td> 
  </tr> 
  <tr> 
   <td>Adresse électronique<br /> </td> 
   <td>srose@we.info</td> 
  </tr> 
 </tbody> 
</table>

**Exemple de fichier JSON**

```
{ 
  customer: { 
   firstName: "Sarah", 
   lastName:"Rose", 
   customerId: "1", 
   emailAddress:"srose@we.info" 
 }, 
  insurance: {
   customerId: "1", 
  policyType: "Premium,
  policyNumber: "Premium-521499",
  customerDetails: { 
   firstName: "Sarah",
   lastName: "Rose",
   customerId: "1",
   emailAddress: "srose@we.info" 
  }
 }
}
```

L’étape Invoquer le service de modèle de données de formulaire contient les champs suivants pour faciliter les opérations du modèle de données de formulaire :

* **Titre :** titre de l’étape. Il permet d’identifier l’étape dans l’éditeur du processus.
* **Description :** la description est utile pour d’autres développeurs de processus lorsque vous travaillez dans un environnement de développement partagé.

* **Chemin d’accès du modèle de données de formulaire** : recherchez et sélectionnez un modèle de données de formulaire présent sur le serveur.

* **Service** : liste des services fournit par le modèle de données de formulaire sélectionné.
* **Entrée des services > Fournir des données d’entrée à l’aide d’un fichier JSON, de l’option Littéral, de métadonnées de processus** : un service peut avoir plusieurs arguments. Sélectionnez cette option pour obtenir la valeur des arguments de service à partir d’une propriété de métadonnées de processus, d’un objet JSON, ou saisissez directement la valeur dans la zone prévue à cet effet :

   * **Littéral :** utilisez cette option lorsque vous connaissez la valeur exacte à spécifier. Par exemple, srose@we.info.
   * **Récupérer à partir des métadonnées de processus :** utilisez cette option lorsque la valeur à utiliser est enregistrée dans une propriété de métadonnées de processus. Par exemple, emailAddress.
   * **JSON Dot Notation :** utilisez cette option lorsque la valeur à utiliser figure dans un fichier JSON. Par exemple, insurance.customerDetails.emailAddress. L’option JSON Dot Notation est uniquement disponible si l’option Mapper les champs de saisie depuis le fichier JSON d’entrée est sélectionnée.
   * **Mapper les champs de saisie depuis le fichier JSON d’entrée :** spécifiez le chemin d’accès d’un fichier JSON pour obtenir la valeur d’entrée des arguments de service à partir du fichier JSON. Le chemin d’accès du fichier JSON peut être relatif à la charge utile ou à un chemin d’accès absolu.

* **Entrée des services > Fournir des données d’entrée à l’aide d’un fichier JSON :** sélectionnez cette option pour obtenir les valeurs de tous les arguments à partir d’un fichier JSON.
* **Chemin d’accès du fichier JSON d’entrée** : chemin d’accès du fichier JSON contenant les valeurs de tous les arguments de service. Le chemin d’accès du fichier JSON peut être **relatif à la charge utile** ou à un **chemin d’accès absolu**.

* **JSON Dot Notation :** laissez le champ vide pour utiliser tous les objets du fichier JSON spécifié en tant qu’entrée pour les arguments de service. Pour lire un objet JSON spécifique à partir du fichier JSON spécifié en tant qu’entrée pour des arguments de service, spécifiez la notation par point pour l’objet JSON. Par exemple, si vous avez un fichier JSON identique à l’un des fichiers indiqué au début de la section, spécifiez insurance.customerDetails pour fournir tous les détails d’un client en tant qu’entrée du service.
* **Sortie de service > Mapper et écrire les valeurs de sortie dans les métadonnées :** sélectionnez cette option pour enregistrer les valeurs de sortie en tant que propriétés du nœud de métadonnées de l’instance de processus dans le référentiel CRX. Spécifiez le nom de la propriété de métadonnées et sélectionnez l’attribut de sortie de service correspondant à mapper avec la propriété de métadonnées, par exemple, mappez la valeur numéro_de_téléphone renvoyé par le service de sortie avec la propriété numéro_de_téléphone des métadonnées du processus.
* **Output of service > Save output as JSON :** sélectionnez l’option permettant d’enregistrer les valeurs de sortie dans un fichier JSON.
* **Chemin d’accès au fichier JSON de sortie :** chemin d’accès pour enregistrer le fichier JSON de sortie. Le chemin d’accès du fichier JSON peut être relatif à la charge utile ou à un chemin d’accès absolu.

## Etape Signer le document  {#sign-document-step}

L’étape Signer le document vous permet d’utiliser Adobe Sign pour signer des documents. L’étape du Document de signature possède les propriétés suivantes :

* **Nom du contrat :** indiquez le titre du contrat. Le nom du contrat devient une partie de l’objet et du corps du courrier électronique envoyé aux signataires.
* **Paramètre régional :** spécifiez la langue pour les options de messagerie et de vérification.
* **Configuration cloud Adobe Sign** : sélectionnez une configuration cloud Adobe Sign. Si vous n’avez pas configuré Adobe Sign pour AEM Forms, voir [Intégrer Adobe Sign à AEM Forms](/help/forms/using/adobe-sign-integration-adaptive-forms.md).

* **Document à signer :** vous pouvez sélectionner un document à partir d’un emplacement relatif à la charge utile, utiliser la charge utile en tant que document ou spécifier le chemin d’accès absolu du document.
* **Jours avant l’échéance :** un document est marqué comme dû (délai expiré) lorsqu’il n’y a plus aucune activité sur la tâche pour le nombre de jours spécifié dans le champ **Jours avant l’échéance.** Le nombre de jours est calculé à partir du jour de l’affectation du document à un utilisateur pour signature.

* **Fréquence des messages de rappel :** vous pouvez envoyer un message de rappel à intervalle quotidien ou hebdomadaire. La semaine est calculée à compter du jour de l’affectation du document à un utilisateur pour signature.
* **Processus de signature :** vous pouvez signer un document dans un ordre séquentiel ou parallèle. Dans un ordre séquentiel, un signataire à la fois reçoit le document à signer. Une fois que le premier signataire a terminé la signature du document, il est envoyé au signataire suivant, et ainsi de suite. Dans l’ordre parallèle, plusieurs signataires signent un document en même temps.

* **URL de redirection :** spécifiez une URL de redirection. Une fois le document signé, vous pouvez rediriger la personne désignée vers une URL. En général, cette URL contient un message de remerciement ou des instructions supplémentaires.
* **Phase de processus :** un processus peut se composer de plusieurs phases. Ces phases sont affichées dans la boîte de réception AEM. Vous pouvez définir ces phases dans les propriétés du modèle (Sidekick > Page > Propriétés de la page > Phases).
* **Sélectionner les signataires :** indiquez la méthode utilisée pour sélectionner des signataires pour le document. Vous pouvez affecter de manière dynamique le processus à un utilisateur ou à un groupe ou ajouter manuellement les informations d’un signataire.
* **Script ou service pour sélectionner les signataires :** cette option est disponible uniquement si l’option De manière dynamique est sélectionnée dans le champ Sélectionner les signataires. Vous pouvez spécifier un ECMAScript ou un service pour choisir les signataires et les options de vérification pour un document.

* **Détails du signataire :** cette option est disponible uniquement si l’option Manuellement est sélectionnée dans le champ Sélectionner les signataires. Indiquez l’adresse électronique et choisissez une méthode de vérification facultative. Avant de sélectionner une méthode de vérification en 2 étapes, assurez-vous que l’option de vérification correspondante est activée pour le compte Adobe Sign configuré.
* **Variable d’état :** l’état de signature d’un document activé par Adobe Sign est stocké dans une variable. Spécifiez le nom de la variable d’état (adobeSignStatus). Une variable d’état d’une instance est disponible dans CRXDE à l’adresse /etc/workflow/instances/&lt;serveur>/&lt;date-time>/&lt;instance du modèle de flux de travail>/workItems/&lt;noeud>/metaData contient l’état d’une variable.
* **Chemin d’accès du document signé :** spécifiez l’emplacement pour conserver les documents signés. Vous pouvez choisir de remplacer le fichier de charge utile ou de placer le document signé à un emplacement dans le répertoire de charge utile.

## Etapes Services de document {#document-services-steps}

Les services de document AEM sont un ensemble de services permettant de créer, d’assembler et de sécuriser des documents PDF. AEM Forms fournit une étape de processus AEM distincte pour chaque service de document :

### Étape Appliquer l’horodatage du document {#apply-document-time-stamp-step}

Ajoute un horodatage à un document. Indiquez les détails du document, tels que le chemin d’accès du document d’entrée, le nom du document d’entrée, l’emplacement de stockage des données exportées. Vous pouvez remplacer le fichier de charge utile existant ou choisir un autre nom de fichier pour stocker des données dans un autre fichier sous le dossier de charge utile.

### Etape Convertir en image  {#convert-to-image-step}

Convertit un document PDF en fichier image. Les formats d’image pris en charge sont JPEG, JPEG2000, PNG et TIFF. Les informations suivantes s’appliquent aux conversions en images TIFF :

* Un fichier TIFF de plusieurs pages est généré.
* Certaines annotations ne sont pas incluses dans les images TIFF. Les annotations requises par Acrobat pour générer leur aspect ne sont pas incluses.

### Etape Convertir en PDF/A  {#convert-to-pdf-a-step}

Convertit un document PDF au format PDF/A à l’aide des options fournies. La version PDF/A du format PDF (Portable Document Format) est réservée à l’archivage et la conservation des documents à long terme.

### Etape Convertir en PS {#convert-to-ps-step}

Convertir des documents PDF en PostScript. Lors d’une conversion au format PostScript, vous pouvez indiquer le document source et choisir entre une conversion vers PostScript niveau 2 ou 3. Le document PDF à convertir en fichier PostScript ne doit pas être interactif.

### Etape Créer le PDF depuis le type spécifié  {#create-pdf-from-specified-type-step}

Génère un document PDF à partir d’un fichier d’entrée. Le document d’entrée peut être relatif à la charge utile ou posséder un chemin d’accès absolu ou encore être une charge utile.

### Etape Créer un fichier PDF depuis l’URL/HTML/ZIP {#create-pdf-from-url-html-zip-step}

Génère un document PDF à partir de l’URL fournie ou du fichier HTML et ZIP.

### Etape Exporter des données  {#export-data-step}

Exporte des données à partir d’un formulaire PDF ou d’un XDP. Vous devez saisir le chemin d’accès du document d’entrée et le format d’exportation des données. Les options Exporter le format de données sont Auto, XDP et XmlData.

### Etape Exporter un PDF vers le type spécifié  {#export-pdf-to-specified-type-step}

Convertit un document PDF au format sélectionné.

### Etape Générer un PDF non interactif  {#generate-non-interactive-pdf-step}

Génère un PDF non interactif. Cette étape comprend différentes options de personnalisation.

### Etape Importer des données {#import-data-step}

Fusionne les données de formulaire dans un formulaire PDF. Vous pouvez importer les données de formulaire dans un formulaire au format PDF.

### Etape Invoquer DDX  {#invoke-ddx-step}

Exécute le fichier DDX sur la carte spécifiée des documents d’entrée et renvoie les documents PDF ayant fait l’objet d’une manipulation.

### Etape Optimiser un PDF  {#optimize-pdf-step}

Optimise les fichiers PDF en réduisant leur taille. Cette conversion a pour effet de réduire la taille des fichiers PDF par rapport à leur version d’origine. Cette opération permet également de convertir des documents PDF vers la version PDF spécifiée dans les paramètres d’optimisation.

Les paramètres d’optimisation spécifient comment les fichiers sont optimisés. Voici des exemples de paramètres :

* Version PDF cible
* Ignorer les objets tels que les actions JavaScript et les vignettes incorporées
* Ignorer les données utilisateur telles que les commentaires et les pièces jointes
* Ignorer les paramètres incorrects ou inutilisés
* Compression de données non compressées ou utilisation d’algorithmes de compression plus efficaces
* Suppression de polices incorporées
* Définition des valeurs de transparence

### Etape Effectuer un rendu de formulaire PDF  {#render-pdf-form-step}

Enregistre un formulaire créé dans Form Designer (XDP) dans un formulaire PDF.

### Etape Protéger un document  {#secure-document-step}

Chiffre, signe et certifie un document. AEM Forms prend en charge le chiffrement par mot de passe et au moyen d’un certificat. Vous pouvez également choisir entre plusieurs algorithmes pour signer des documents. SHA-256 et SH-512, par exemple. Vous pouvez également utiliser l’étape de processus pour étendre Reader aux documents PDF. L’étape de processus propose une option qui permet d’activer le décodage de code-barres, les signatures numériques, l’importation et l’exportation de données au format PDF et d’autres options.

### Etape Envoyer à l’imprimante {#send-to-printer-step}

Envoie un document directement à une imprimante. Cette étape prend en charge les systèmes d’accès aux imprimantes suivants :

* **Imprimante accessible directement** : une imprimante installée sur l’ordinateur utilisé est appelée imprimante accessible directement et l’ordinateur est appelé hôte de l’imprimante. Il peut s’agir d’une imprimante locale directement reliée à l’ordinateur.
* **Imprimante accessible indirectement** : l’imprimante installée sur un serveur d’impression est accessible depuis d’autres ordinateurs. Les technologies de type CUPS (Common Unix® Printing System) et le protocole LPD (Line Printer Daemon) permettent de se connecter à une imprimante réseau. Pour accéder à une imprimante accessible indirectement, spécifiez l’adresse IP ou le nom d’hôte du serveur d’impression. Ainsi, vous pouvez envoyer un document vers un URI LPD lorsqu’un protocole LDP s’exécute sur le réseau. Ce système vous permet d’acheminer le document vers n’importe quelle imprimante connectée au réseau qui exécute un protocole LDP.

