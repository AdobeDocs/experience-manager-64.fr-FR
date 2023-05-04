---
title: Référence sur les étapes du workflow basé sur l’utilisation de Forms on OSGi
seo-title: Forms-centric workflow on OSGi - Step Reference
description: Les processus basés sur Forms sur les étapes OSGi vous permettent de créer rapidement des processus basés sur des formulaires adaptatifs.
seo-description: Forms-centric workflow on OSGi steps allow you rapidly build adaptive forms based workflows.
uuid: 57c872d6-c6ca-4f78-a98c-f9487f1d673c
contentOwner: AEM Docs
discoiquuid: f2bd4d96-55a5-4fbd-bede-1747c2ec63c8
exl-id: f8e25989-6ed3-4b35-95e5-fbfd7c51d622
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '4673'
ht-degree: 44%

---

# Référence sur les étapes du processus basé sur l’utilisation de Forms on OSGi {#forms-centric-workflow-on-osgi-step-reference}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

## Étapes de processus Forms {#forms-workflow-steps}

Les étapes du workflow Forms effectuent des opérations spécifiques à AEM Forms dans un workflow AEM. Ces étapes vous permettent de créer rapidement un processus Forms basé sur des formulaires adaptatifs sur OSGi. Ces workflows peuvent être utilisés pour développer des processus de révision et d’approbation de base, des processus métier internes et entre pare-feu. Vous pouvez également utiliser des étapes Forms Workflow pour démarrer Document Services, intégrer le processus de signature Acrobat Sign et effectuer d’autres opérations AEM Forms. Vous avez besoin de [Module complémentaire AEM Forms](https://www.adobe.com/go/learn_aemforms_documentation_63_fr) pour utiliser ces étapes dans un workflow.

## Étape Affecter une tâche {#assign-task-step}

L’étape Affecter une tâche crée une tâche et l’affecte à un utilisateur ou à un groupe. En plus d’affecter la tâche, le composant spécifie également le formulaire adaptatif ou le PDF non interactif pour la tâche. Le formulaire adaptatif est requis pour accepter les entrées des utilisateurs et des PDF non interactifs ou un formulaire adaptatif en lecture seule est utilisé pour les processus de révision uniquement.

Vous pouvez également utiliser le composant pour contrôler le comportement de la tâche. Par exemple, la création d’un document d’enregistrement automatique, l’affectation de la tâche à un utilisateur ou à un groupe spécifique, la spécification du chemin d’accès des données envoyées, la spécification du chemin d’accès des données à pré-remplir et la spécification des actions par défaut. L’étape Affecter une tâche possède les propriétés suivantes :

* **Titre :** Titre de la tâche. Le titre s’affiche dans la boîte de réception AEM.
* **Description :** Explication des opérations en cours dans la tâche. Ces informations sont utiles pour d’autres développeurs de processus lorsque vous travaillez dans un environnement de développement partagé.

* **Chemin de la miniature :** Chemin d’accès de la miniature de la tâche. Si aucun chemin n’est spécifié, une miniature par défaut de formulaire adaptatif s’affiche et une icône par défaut s’affiche pour le document d’enregistrement.
* **Phase de processus :** un processus peut se composer de plusieurs phases. Ces phases sont affichées dans la boîte de réception AEM. Vous pouvez définir ces phases dans les propriétés du modèle (Sidekick > Page > Propriétés de la page > Phases).
* **Priorité :** la priorité sélectionnée s’affiche dans la boîte de réception AEM. Les options disponibles sont les suivantes : Élevée, Moyenne et Faible. La valeur par défaut est Moyenne.
* **Date d’échéance :** Indiquez le nombre de jours ou d’heures après lesquels la tâche est marquée comme en retard. Si vous sélectionnez **Désactivé**, la tâche n’est jamais marquée comme En retard. Vous pouvez également spécifier un gestionnaire de dépassement de délai pour effectuer des tâches spécifiées dès que la tâche est marquée comme En retard.

* **Jours :** le nombre de jours restants pour terminer la tâche. Le nombre de jours est calculé à partir du jour de l’affectation de la tâche à un utilisateur. Si cette option est sélectionnée, si une tâche n’est pas terminée et dépasse le nombre de jours spécifié dans le champ Jours, un gestionnaire de dépassement de délai est déclenché après la date d’expiration.
* **Heures :** Nombre d’heures avant que la tâche ne soit terminée. Le nombre d’heures est calculé à partir de l’heure de l’affectation de la tâche à un utilisateur. Si cette option est sélectionnée, si une tâche n’est pas terminée et dépasse le nombre d’heures spécifié dans le champ Heures, un gestionnaire de dépassement de délai est déclenché après l’heure de l’expiration.
* **Expiration après l’échéance :** sélectionnez cette option pour activer le champ Sélection du gestionnaire de dépassement de délai.
* **Gestionnaire de dépassement de délai :** sélectionnez le script à exécuter lorsque l’étape Affecter une tâche dépasse l’échéance. Les scripts placés dans le référentiel CRX à l’emplacement [apps]/fd/dashboard/scripts/timeoutHandler peuvent être sélectionnés. Le chemin d’accès spécifié n’existe pas dans le référentiel crx. Un administrateur crée le chemin d’accès avant de l’utiliser.
* **Sélectionner l’action et ajouter un commentaire depuis la dernière tâche dans Détails de la tâche :** sélectionnez cette option pour afficher la dernière action qui a été effectuée et le dernier commentaire reçu dans la section Détails de la tâche.
* **Type :** sélectionnez le type de document à remplir lors du lancement du processus. Vous pouvez choisir un formulaire adaptatif, un formulaire adaptatif en lecture seule ou un document de PDF non interactif.
* **Utiliser le formulaire adaptatif :** spécifiez la méthode pour localiser le formulaire adaptatif d’entrée. Vous pouvez utiliser le formulaire adaptatif disponible à un chemin absolu, envoyé en tant que charge utile au workflow, ou disponible à un chemin calculé à l’aide d’une variable. Vous pouvez utiliser une variable de type chaîne pour spécifier le chemin d’accès.
* **Chemin d’accès du formulaire adaptatif** : indiquez le chemin d’accès du formulaire adaptatif. Le champ est disponible lorsque vous utilisez l’option de formulaire adaptatif ou de formulaire adaptatif en lecture seule dans le champ Type conjointement avec l’option de chemin d’accès absolu dans le champ Utiliser le formulaire adaptatif .
* **Chemin du PDF :** Spécifiez le chemin d’accès d’un document de PDF non interactif. Le champ apparaît lorsque vous sélectionnez un document PDF non interactif dans le champ Type. Le chemin d’accès est toujours relatif à la charge. Par exemple, [Répertoire_Charge_utile]/Workflow/PDF/credit-card.pdf. Le chemin n’existe pas dans le référentiel CRX. Un administrateur crée le chemin d’accès avant de l’utiliser. Vous avez besoin d’une option Document d’enregistrement activée ou de formulaires adaptatifs basés sur un modèle de formulaire pour utiliser l’option Chemin du PDF .
* **Pour la tâche terminée, effectuez le rendu du formulaire adaptatif comme**: Lorsqu’une tâche est marquée comme terminée, vous pouvez effectuer le rendu du formulaire adaptatif en tant que formulaire adaptatif en lecture seule ou document de PDF. Vous avez besoin d’une option Document d’enregistrement activée ou de formulaires adaptatifs basés sur un modèle de formulaire pour générer le formulaire adaptatif en tant que document d’enregistrement.
* **Informations à préremplir :** Les champs suivants répertoriés ci-dessous servent d’entrées à la tâche :

   * **Chemin du fichier de données :** Chemin du fichier de données d’entrée (.json ou .xml). Le chemin d’accès est toujours relatif à la charge. Par exemple, le fichier contient les données envoyées pour le formulaire via une application de boîte de réception AEM. Voici un exemple de chemin d’accès : [Répertoire_Charge_utile]/workflow/data.
   * **Chemin d’accès de la pièce jointe :** Les pièces jointes disponibles à l’emplacement sont jointes au formulaire associé à la tâche. Le chemin d’accès est toujours relatif à la charge. Voici un exemple de chemin d’accès : [Répertoire_Charge_utile]/attachments/

* **Informations envoyées :** les champs répertoriés ci-dessous servent d’emplacement de sortie pour la tâche :

   * **Chemin du fichier de données :** Chemin du fichier de données (.json ou .xml). Le fichier de données contient des informations envoyées via le formulaire associé. Le chemin d’accès est toujours relatif à la charge. Par exemple, [Répertoire_Charge_utile]/Workflow/data, où les données correspondent à un fichier.
   * **Chemin d’accès de la pièce jointe :** Chemin d’accès pour enregistrer les pièces jointes de formulaire fournies dans une tâche.
   * **Chemin du document d’enregistrement :** Chemin d’accès pour enregistrer un fichier de document d’enregistrement. Par exemple,[ Répertoire_Charge_utile]/DocumentofRecord/credit-card.pdf. Le document d’enregistrement n’est pas généré si le champ de chemin d’accès est vide. Le chemin d’accès est toujours relatif à la charge.

* **Options d’affectation :** Indiquez la méthode d’affectation de la tâche à un utilisateur. Vous pouvez affecter la tâche de manière dynamique à un utilisateur ou un groupe à l’aide du script Programme de sélection des participants ou affecter la tâche à un utilisateur ou à un groupe AEM spécifique.
* **Programme de sélection des participants :** Cette option est disponible lorsque la variable **À un utilisateur ou à un groupe de manière dynamique** est sélectionnée dans le champ Options d’affectation . Vous pouvez utiliser un ECMAScript ou un service pour sélectionner dynamiquement un utilisateur ou un groupe. Pour plus d’informations, voir [Affectation dynamique d’un workflow aux utilisateurs](https://helpx.adobe.com/fr/experience-manager/kb/HowToAssignAWorkflowDynamicallyToParticipants.html) et [Création d’une étape de participant dynamique Adobe Experience Manager personnalisée.](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html?lang=fr&amp;CID=RedirectAEMCommunityKautuk)

* **Participants :** le champ est disponible lorsque l’option **[!UICONTROL com.adobe.granite.workflow.core.process.RandomParticipantChooser]** est sélectionnée dans le champ Programme de sélection des participants. Le champ vous permet de sélectionner des utilisateurs ou des groupes pour l’option RandomParticipantChooser.

* **Arguments :** le champ est disponible lorsqu’un script autre que le script RandomParticipantChoose est sélectionné dans le champ Programme de sélection des participants. Le champ vous permet de fournir une liste d’arguments séparés par des virgules pour le script sélectionné dans le champ Programme de sélection des participants.

* **Utilisateur ou groupe :** la tâche est affectée à l’utilisateur ou au groupe sélectionné. Cette option est disponible lorsque l’option **À un utilisateur ou un groupe spécifique** est activée dans le champ Options d’affectation. Le champ répertorie tous les utilisateurs et groupes du groupe d’utilisateurs du processus.

* **Notifier le cessionnaire par courrier électronique :** Sélectionnez cette option pour envoyer des notifications par courrier électronique à la personne désignée. Ces notifications sont envoyées lorsqu’une tâche est assignée à un utilisateur. Avant d&#39;utiliser cette option, activez les notifications depuis AEM console web. Pour obtenir des instructions détaillées, voir [configurer des notifications électroniques pour l’étape Affecter une tâche](/help/forms/using/aem-forms-workflow.md)

* **Modèle de courrier électronique HTML**: Sélectionnez le modèle d&#39;email de l&#39;email de notification. Pour modifier un modèle, modifiez le fichier situé à l’emplacement /libs/fd/dashboard/templates/email/htmlEmailTemplate.txt dans le référentiel crx-repository.
* **Autoriser la délégation à :** La boîte de réception AEM fournit à l’utilisateur connecté une option lui permettant de déléguer le processus affecté à un autre utilisateur. Vous êtes autorisé à déléguer au sein du même groupe ou à l’utilisateur du workflow d’un autre groupe. Si la tâche est affectée à un seul utilisateur et que la fonction **Autoriser la délégation aux membres du groupe désigné** est sélectionnée, puis il n’est pas possible de déléguer la tâche à un autre utilisateur ou groupe.

* **Actions par défaut :** Les actions Envoyer, Enregistrer et Réinitialiser prêtes à l’emploi sont disponibles. Par défaut, toutes les actions par défaut sont activées.
* **Variable d’itinéraire :** Nom de la variable d’itinéraire. La variable d’itinéraire capture les actions personnalisées qu’un utilisateur sélectionne dans la boîte de réception AEM.
* **Itinéraires :** Une tâche peut se branche à différents itinéraires. Lorsque cette option est sélectionnée dans la boîte de réception AEM, l’itinéraire renvoie une valeur et les branches du processus en fonction de l’itinéraire sélectionné.
* **Titre** : indiquez le titre de l’itinéraire. Il s’affiche dans AEM boîte de réception.
* **Icône Coral**: Spécifiez l’attribut HTML d’une icône de corail. La bibliothèque Adobe CoralUI fournit un vaste ensemble d’icônes tactiles. Vous pouvez choisir et utiliser une icône pour l’itinéraire. Elle s’affiche avec le titre dans la boîte de réception AEM.
* **Autoriser les personnes désignées à ajouter des commentaires**: Sélectionnez cette option pour activer les commentaires pour la tâche. Une personne désignée peut ajouter les commentaires dans AEM boîte de réception au moment de l’envoi de la tâche.
* **Autoriser les personnes désignées à ajouter des pièces jointes à la tâche**: Sélectionnez cette option pour activer les pièces jointes pour la tâche. Une personne désignée peut ajouter des pièces jointes à partir de la boîte de réception AEM au moment de l’envoi de la tâche.
* **Chemin de sortie des pièces jointes de la tâche**: Indiquez l’emplacement du dossier de pièces jointes. L’emplacement est relatif à la charge utile.
* **Utilisation de métadonnées personnalisées :** Sélectionnez cette option pour activer le champ de métadonnées personnalisé. Les métadonnées personnalisées sont utilisées dans les modèles de courrier électronique.
* **Métadonnées personnalisées :** sélectionnez une métadonnée personnalisée pour les modèles de courrier électronique. Les métadonnées personnalisées sont disponibles dans le référentiel crx-repository sous apps/fd/dashboard/scripts/metadataScripts. Le chemin d’accès spécifié n’existe pas dans le référentiel crx. Un administrateur crée le chemin d’accès avant de l’utiliser. Vous pouvez également utiliser un service pour les métadonnées personnalisées. Vous pouvez également étendre l’interface `WorkitemUserMetadataService` afin de fournir des métadonnées personnalisées.

* **Afficher les données des étapes précédentes** : sélectionnez cette option pour permettre aux personnes désignées d’afficher les personnes désignées précédentes, les actions déjà effectuées sur la tâche, les commentaires ajoutés à la tâche et le document d’enregistrement de la tâche terminée, le cas échéant.
* **Afficher les données des étapes suivantes :** sélectionnez cette option pour permettre à la personne actuellement désignée d’afficher l’action effectuée et les commentaires ajoutés à la tâche par les personnes désignées suivantes. Elle permet également à la personne désignée actuelle d’afficher un document d’enregistrement de la tâche terminée, le cas échéant.
* **Visibilité du type de données :** Par défaut, une personne désignée peut afficher un document d’enregistrement, les personnes désignées, l’action entreprise et les commentaires ajoutés par les personnes désignées précédentes et suivantes. Utilisez l’option de visibilité du type de données pour limiter le type de données visibles pour les personnes désignées.

## Étape Envoyer un e-mail {#send-email-step}

Utilisez l’étape Envoyer un courrier électronique pour envoyer un courrier électronique, par exemple un courrier électronique contenant un document d’enregistrement, un lien d’un formulaire adaptatif, un lien d’une communication interactive ou un document de PDF joint. L’étape Envoyer un courrier électronique prend en charge [Email HTML](https://en.wikipedia.org/wiki/HTML_email). Les emails par HTML sont réactifs et s’adaptent à la taille de l’écran et au client de messagerie du destinataire. Vous pouvez utiliser un modèle de courrier électronique HTML pour définir l’aspect, le modèle de couleurs et le comportement du courrier électronique.

L’étape Envoyer un courrier électronique utilise le service de messagerie Day CQ pour envoyer des messages. Avant d’utiliser l’étape de courrier électronique, assurez-vous que la variable [service de messagerie électronique](/help/forms/using/aem-forms-workflow.md) est configuré. L’étape Envoyer un courrier électronique possède les propriétés suivantes :

**Titre :** Le titre de l’étape permet d’identifier l’étape dans l’éditeur de workflow.

**Description :** la description est utile pour d’autres développeurs de processus lorsque vous travaillez dans un environnement de développement partagé.

**Objet du message :** L’objet peut être récupéré à partir des métadonnées d’un workflow ou spécifié manuellement. Sélectionnez la **Littéral** pour spécifier manuellement un objet ou sélectionner l’option **Récupération à partir des métadonnées de workflow** pour récupérer l’objet à partir d’une propriété de métadonnées.

**Modèle de courrier électronique HTML** : modèle HTML pour le courrier électronique. Vous pouvez spécifier des variables dans un modèle de courrier électronique. L’étape Envoyer un courrier électronique extrait et affiche toutes les variables incluses dans un modèle pour les entrées.

**Métadonnées du modèle d’e-mail :** la valeur des variables du modèle d’e-mail peut être une valeur spécifiée par l’utilisateur, le chemin d’accès d’un actif sur le serveur de création ou de publication, une image ou une propriété de métadonnées de workflow.

* **Littéral** : utilisez cette option lorsque vous connaissez la valeur exacte à spécifier. Par exemple, [example@example.com](mailto:example@example.com).

* **Métadonnées de workflow :** Utilisez l’option lorsque la valeur à utiliser est enregistrée dans une propriété de métadonnées de workflow. Après avoir sélectionné l’option, saisissez le nom de la propriété de métadonnées dans la zone de texte vide sous l’option Métadonnées de processus . Par exemple, emailAddress.
* **URL de la ressource :** utilisez cette option pour inclure un lien web d’une communication interactive à l’e-mail. Après avoir sélectionné cette option, recherchez et sélectionnez la communication interactive à inclure. La ressource peut se trouver sur le serveur de création ou de publication.
* **Image :** Utilisez l’option pour incorporer une image dans le courrier électronique. Après avoir sélectionné cette option, recherchez et sélectionnez l’image. L’option image est disponible uniquement pour les balises d’image (&lt;img src=&quot;&amp;ast;&quot; />) disponibles dans le modèle d’email.

**Adresse électronique de l’expéditeur/du destinataire :** Sélectionnez la **Littéral** pour spécifier manuellement une adresse électronique ou sélectionner l’option **Récupération à partir des métadonnées de workflow** pour récupérer l’adresse électronique à partir d’une propriété de métadonnées. Vous pouvez également spécifier une liste de tableaux de propriété de métadonnées pour l’option **Récupérez à partir des métadonnées de processus.**

**File Attachment Path :** La ressource disponible à l’emplacement spécifié est jointe au courrier électronique. Le chemin d’accès de l’actif peut être lié à la charge utile ou au chemin d’accès absolu. Voici un exemple de chemin d’accès : [Répertoire_Charge_utile]/attachments/

**Nom de fichier :** nom du fichier de la pièce jointe au courrier électronique. L’étape Envoyer un courrier électronique remplace le nom de fichier original de la pièce jointe par le nom de fichier spécifié. Le nom peut être spécifié manuellement ou récupéré à partir d’une propriété de métadonnées de workflow. Utilisez l’option **Littéral** lorsque vous connaissez la valeur exacte à spécifier. Utilisez l’option **Récupérer à partir des métadonnées de processus** lorsque la valeur à utiliser est enregistrée dans une propriété de métadonnées de processus.

## Etape Générer un document d’enregistrement {#generate-document-of-record-step}

Lorsqu’un formulaire est rempli ou envoyé, vous pouvez conserver un enregistrement du formulaire, au format imprimé ou au format de document. On parle alors de document d’enregistrement (DE). Vous pouvez utiliser l’étape Générer un document d’enregistrement pour créer une version de PDF interactive ou en lecture seule d’un formulaire adaptatif. La version du PDF contient des informations remplies dans le formulaire, ainsi que la mise en page du formulaire adaptatif.

L’étape Document d’enregistrement possède les propriétés suivantes :

**Utiliser un formulaire adaptatif** : spécifiez la méthode pour localiser le formulaire adaptatif d’entrée. Vous pouvez utiliser le formulaire adaptatif disponible à un chemin absolu, envoyé en tant que charge utile au workflow, ou disponible à un chemin calculé à l’aide d’une variable. Vous pouvez utiliser une variable de type chaîne pour spécifier le chemin d’accès.

**Chemin d’accès du formulaire adaptatif** : indiquez le chemin d’accès du formulaire adaptatif. Le champ est disponible lorsque vous utilisez l’option de formulaire adaptatif ou de formulaire adaptatif en lecture seule dans le champ Type conjointement avec l’option de chemin d’accès absolu dans le champ Utiliser le formulaire adaptatif .

**Input Data Path :** Chemin d’accès des données d’entrée pour le formulaire adaptatif. Vous pouvez conserver les données à un emplacement relatif à la charge utile ou spécifier un chemin d’accès absolu aux données. Les données d’entrée sont fusionnées avec le formulaire adaptatif pour créer un document d’enregistrement.

**Input Attachment Path :** Input Attachment Path : Chemin des pièces jointes. Ces pièces jointes sont incluses dans le document d’enregistrement. Vous pouvez conserver les pièces jointes à un emplacement relatif à la charge utile ou spécifier un chemin d’accès absolu aux pièces jointes.

Si vous spécifiez le chemin d’accès d’un dossier, par exemple des pièces jointes, tous les fichiers directement disponibles dans le dossier sont joints au document d’enregistrement. Si des fichiers sont disponibles dans les dossiers directement disponibles dans le chemin d’accès de la pièce jointe spécifiée, les fichiers sont inclus dans le document d’enregistrement sous forme de pièces jointes. Les dossiers présents dans les dossiers directement disponibles sont ignorés.

**Chemin d’accès du document d’enregistrement généré :** Indiquez l’emplacement où conserver un fichier de document d’enregistrement. Vous pouvez choisir de remplacer le dossier de charge utile ou de placer le document d’enregistrement à un emplacement dans le répertoire de charge utile.

**Paramètre régional** : spécifiez la langue du document d’enregistrement.

## Étape Invoquer le service de modèle de données de formulaire {#invoke-form-data-model-service-step}

Vous pouvez utiliser l’[intégration de données AEM Forms](/help/forms/using/data-integration.md) pour configurer des sources de données disparates et vous y connecter. Ces sources de données peuvent être une base de données, un service Web, un service REST, un service OData et une solution de gestion de la relation client (CRM). L’intégration de données AEM Forms vous permet de créer un modèle de données de formulaire englobant divers services afin d’effectuer des opérations de récupération, d’ajout et de mise à jour de données sur la base de données configurée. Vous pouvez utiliser **l’étape Invoquer le service de modèle de données de formulaire** pour sélectionner un modèle de données de formulaire (FDM) et utiliser les services du FDM pour récupérer, mettre à jour ou ajouter des données aux sources de données disparates.

Pour expliquer les entrées des champs de l’étape, le tableau de base de données et le fichier JSON suivants sont utilisés comme exemple :

**Exemple de tableau CustomerDetails**

<table> 
 <tbody> 
  <tr> 
   <td>Propriété</td> 
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

* **Titre :** Titre de l’étape. Il permet d’identifier l’étape dans l’éditeur du processus.
* **Description :** la description est utile pour d’autres développeurs de processus lorsque vous travaillez dans un environnement de développement partagé.

* **Chemin d’accès du modèle de données de formulaire** : recherchez et sélectionnez un modèle de données de formulaire présent sur le serveur.

* **Service** : liste des services fournit par le modèle de données de formulaire sélectionné.
* **Entrée pour les services > Fournir des données d’entrée à l’aide de littéraux, de métadonnées de workflow et d’un fichier JSON**: Un service peut avoir plusieurs arguments. Sélectionnez l’option pour obtenir la valeur des arguments de service à partir d’une propriété de métadonnées de workflow, d’un objet JSON ou saisissez directement la valeur dans la zone de texte fournie :

   * **Littéral** : utilisez cette option lorsque vous connaissez la valeur exacte à spécifier. Par exemple, srose@we.info.
   * **Récupération à partir des métadonnées de workflow :** Utilisez l’option lorsque la valeur à utiliser est enregistrée dans une propriété de métadonnées de workflow. Par exemple, emailAddress.
   * **JSON Dot Notation :** utilisez cette option lorsque la valeur à utiliser figure dans un fichier JSON. Par exemple, insurance.customerDetails.emailAddress.L’option JSON Dot Notation n’est disponible que si l’option Mapper les champs de saisie depuis l’entrée JSON est sélectionnée.
   * **Mapper les champs de saisie depuis le fichier JSON d’entrée :** spécifiez le chemin d’accès d’un fichier JSON pour obtenir la valeur d’entrée des arguments de service à partir du fichier JSON. Le chemin d’accès du fichier JSON peut être relatif à la charge utile ou à un chemin d’accès absolu.

* **Entrée pour les services > Fournir des données d’entrée à l’aide d’un fichier JSON :** Sélectionnez l’option pour obtenir des valeurs pour tous les arguments d’un fichier JSON.
* **Chemin du fichier JSON d’entrée**: Chemin du fichier JSON contenant les valeurs de tous les arguments de service. Le chemin d’accès du fichier JSON peut être **relatif à la charge utile** ou à un **chemin d’accès absolu**.

* **Notation de point JSON :** Laissez le champ vide pour utiliser tous les objets du fichier JSON spécifié comme entrée pour les arguments de service. Pour lire un objet JSON spécifique à partir du fichier JSON spécifié en tant qu’entrée pour des arguments de service, spécifiez la notation par point pour l’objet JSON. Par exemple, si vous avez un fichier JSON identique à l’un des fichiers indiqué au début de la section, spécifiez insurance.customerDetails pour fournir tous les détails d’un client en tant qu’entrée du service.
* **Sortie de service > Mapper et écrire les valeurs de sortie sur les métadonnées :** Sélectionnez l’option pour enregistrer les valeurs de sortie en tant que propriétés du noeud de métadonnées de l’instance de workflow dans le référentiel crx-repository. Spécifiez le nom de la propriété de métadonnées et sélectionnez l’attribut de sortie de service correspondant à mapper avec la propriété de métadonnées, par exemple, mappez la valeur numéro_de_téléphone renvoyé par le service de sortie avec la propriété numéro_de_téléphone des métadonnées du processus.
* **Sortie de service > Enregistrer la sortie au format JSON :** Sélectionnez l’option pour enregistrer les valeurs de sortie dans un fichier JSON.
* **Chemin du fichier JSON de sortie :** Chemin d’accès pour enregistrer le fichier JSON de sortie. Le chemin d’accès du fichier JSON peut être relatif à la charge utile ou à un chemin d’accès absolu.

## Étape Signer le document {#sign-document-step}

L’étape Signer le document vous permet d’utiliser Acrobat Sign pour signer des documents. L’étape Signer le document possède les propriétés suivantes :

* **Nom du contrat :** indiquez le titre du contrat. Le nom du contrat devient une partie de l’objet et du corps du courrier électronique envoyé aux signataires.
* **Paramètre régional :** spécifiez la langue pour les options de messagerie et de vérification.
* **Configuration du cloud Acrobat Sign**: Sélectionnez une configuration de cloud Acrobat Sign. Si vous n’avez pas configuré Acrobat Sign pour AEM Forms, reportez-vous à la section [Intégration d’Acrobat Sign à AEM Forms](/help/forms/using/adobe-sign-integration-adaptive-forms.md).

* **Document à signer :** Vous pouvez choisir un document à partir d’un emplacement relatif à la charge utile, utiliser la charge utile comme document ou spécifier un chemin d’accès absolu au document.
* **Input Attachment Path :** Sélectionnez une pièce jointe. Ces pièces jointes sont incluses dans le document de signature. Vous pouvez conserver les pièces jointes à un emplacement relatif à la charge utile ou spécifier un chemin d’accès absolu aux pièces jointes.

   Si vous spécifiez le chemin d’accès d’un dossier, par exemple des pièces jointes, tous les fichiers directement disponibles dans le dossier sont joints au document d’enregistrement. Si des fichiers sont présents dans les dossiers directement disponibles dans le chemin d’accès de la pièce jointe spécifiée, les fichiers sont inclus dans le document de signature en tant que pièces jointes. Les dossiers présents dans les dossiers directement disponibles sont ignorés.
* **Jours avant l’échéance :** un document est marqué comme dû (délai expiré) lorsqu’il n’y a plus aucune activité sur la tâche pour le nombre de jours spécifié dans le champ **Jours avant l’échéance.** Le nombre de jours est calculé à partir du jour de l’affectation du document à un utilisateur pour signature.

* **Fréquence des messages de rappel :** vous pouvez envoyer un message de rappel à intervalle quotidien ou hebdomadaire. La semaine est calculée à compter du jour de l’affectation du document à un utilisateur pour signature.
* **Processus de signature :** Vous pouvez choisir de signer un document dans un ordre séquentiel ou parallèle. Dans l’ordre séquentiel, un signataire reçoit le document à la fois pour signature. Une fois que le premier signataire a terminé la signature du document, le document est envoyé au second signataire, etc. Dans l’ordre parallèle, plusieurs signataires signent un document en même temps.

* **URL de redirection :** Spécifiez une URL de redirection. Une fois le document signé, vous pouvez rediriger la personne désignée vers une URL. En règle générale, cette URL contient un message de remerciement ou d’autres instructions.
* **Phase de processus :** un processus peut se composer de plusieurs phases. Ces phases sont affichées dans la boîte de réception AEM. Vous pouvez définir ces phases dans les propriétés du modèle (Sidekick > Page > Propriétés de la page > Phases).
* **Sélectionner les signataires :** indiquez la méthode utilisée pour sélectionner des signataires pour le document. Vous pouvez affecter de manière dynamique le processus à un utilisateur ou à un groupe ou ajouter manuellement les informations d’un signataire.
* **Script ou service pour sélectionner les signataires :** Cette option n’est disponible que si l’option Dynamiquement est sélectionnée dans le champ Sélectionner les signataires . Vous pouvez spécifier un script ECMAScript ou un service pour sélectionner des signataires et des options de vérification pour un document.

* **Détails du signataire :** cette option est disponible uniquement si l’option Manuellement est sélectionnée dans le champ Sélectionner les signataires. Indiquez l’adresse électronique et choisissez une méthode de vérification facultative. Avant de sélectionner un mécanisme de vérification en 2 étapes, assurez-vous que l’option de vérification correspondante est activée pour le compte Acrobat Sign configuré.
* **Variable d’état :** Un document activé par Acrobat Sign stocke l’état de signature du document dans une variable. Spécifiez le nom de la variable d’état (adobeSignStatus). Une variable de statut d’une instance est disponible dans CRXDE à l’emplacement /etc/workflow/instances/&lt;server>/&lt;date-heure>/&lt;instance de modèle de processus>/workItems/&lt;node>/metaData. Elle contient le statut d’une variable.
* **Chemin du document signé :** Indiquez l’emplacement où conserver les documents signés. Vous pouvez choisir de remplacer le fichier de charge utile ou de placer le document signé à un emplacement dans le répertoire de charge utile.

## Étapes de Document Services {#document-services-steps}

AEM Services de document est un ensemble de services permettant de créer, d’assembler et de sécuriser des documents PDF. AEM Forms fournit une étape AEM processus distincte pour chaque service de document :

### Étape Appliquer l’horodatage du document {#apply-document-time-stamp-step}

Ajoutez un horodatage à un document. Vous fournissez des détails sur le document, tels que le chemin du document d’entrée, le nom du document d’entrée, l’emplacement de stockage des données exportées. Vous pouvez choisir de remplacer un fichier de charge utile existant ou choisir un autre nom de fichier pour stocker les données dans un autre fichier sous le dossier de charge utile.

### Etape Convertir en image {#convert-to-image-step}

Convertit un document PDF en fichier image. Les formats d’image pris en charge sont JPEG, JPEG2000, PNG et TIFF. Les informations suivantes s’appliquent aux conversions en images de TIFF :

* Un fichier de TIFF de plusieurs pages est généré.
* Certaines annotations ne sont pas incluses dans les images de TIFF. Les annotations qui nécessitent qu’Acrobat génère leur apparence ne sont pas incluses.

### Étape Convertir en PDF/A {#convert-to-pdf-a-step}

Convertit un document de PDF au format PDF/A à l’aide des options fournies. La version PDF/A du format PDF (Portable Document Format) est réservée à l’archivage et la conservation des documents à long terme.

### Étape Convertir en PS {#convert-to-ps-step}

Convertir des documents PDF en PostScript. Lors de la conversion au format PostScript, vous pouvez utiliser l’opération de conversion pour spécifier le document source et indiquer si vous souhaitez effectuer une conversion au format PostScript 2 ou 3. Le document du PDF que vous convertissez en fichier PostScript doit être non interactif.

### Création d’un PDF à partir d’une étape de type spécifiée {#create-pdf-from-specified-type-step}

Générer un document de PDF à partir d’un fichier d’entrée. Le document d’entrée peut être relatif à la charge utile, avoir un chemin d’accès absolu ou être la charge utile elle-même.

### Créer un PDF à partir de l’étape URL/HTML/ZIP {#create-pdf-from-url-html-zip-step}

Génère un document de PDF à partir de l’URL, du HTML et du fichier ZIP fournis.

### Étape Exporter les données {#export-data-step}

Exporte les données d’un fichier PDF forms ou XDP. Vous devez saisir le chemin d’accès au fichier du document d’entrée et du format d’exportation des données. Les options pour l’option Export Data Format sont Auto, XDP et XmlData.

### Export PDF à l’étape de type spécifiée {#export-pdf-to-specified-type-step}

Convertit un document PDF au format sélectionné.

### Étape Générer un PDF non interactif {#generate-non-interactive-pdf-step}

Générez un PDF non interactif. Cette étape comprend différentes options de personnalisation.

### Étape Importer des données {#import-data-step}

Fusionne les données de formulaire dans un formulaire de PDF. Vous pouvez importer des données de formulaire dans un formulaire de PDF.

### Étape Invoquer DDX {#invoke-ddx-step}

Exécute le fichier DDX sur la carte spécifiée des documents d’entrée et renvoie les documents de PDF manipulés.

### Étape Optimize PDF {#optimize-pdf-step}

Optimise les fichiers de PDF en réduisant leur taille. Le résultat de cette conversion est un fichier PDF moins volumineux que sa version d’origine. Cette opération convertit également les documents du PDF vers la version du PDF spécifiée dans les paramètres d’optimisation.

Les paramètres d’optimisation spécifient le mode d’optimisation des fichiers. Voici des exemples de paramètres :

* Version PDF cible :
* Ignorer les objets tels que les actions JavaScript et les miniatures de page incorporées
* Ignorer les données utilisateur telles que les commentaires et les pièces jointes
* Ignorer les paramètres non valides ou inutilisés
* Compresser les données non compressées ou utiliser des algorithmes de compression plus efficaces
* Supprimer les polices incorporées
* Définir les valeurs de transparence

### Étape Render PDF Form {#render-pdf-form-step}

Rend un formulaire créé dans Form Designer (XDP) dans un formulaire PDF.

### Étape Protéger le document {#secure-document-step}

Chiffrez, signez et certifiez un document. AEM Forms prend en charge le chiffrement avec mot de passe et base de certificats. Vous pouvez également choisir entre différents algorithmes pour signer des documents. Par exemple, SHA-256 et SH-512. Vous pouvez également utiliser l’étape de workflow pour étendre Reader aux documents PDF. L’étape de processus propose une option qui permet d’activer le décodage de code-barres, les signatures numériques, l’importation et l’exportation de données au format PDF et d’autres options.

### Étape Envoyer à l’imprimante {#send-to-printer-step}

Envoyez directement un document à une imprimante. Il prend en charge les mécanismes d’accès à l’impression suivants :

* **Imprimante accessible directement**: Une imprimante installée sur le même ordinateur s’appelle une imprimante accessible directement, et l’ordinateur s’appelle hôte de l’imprimante. Ce type d’imprimante peut être une imprimante locale directement reliée à l’ordinateur.
* **Imprimante accessible indirectement**: L’imprimante installée sur un serveur d’impression est accessible à partir d’autres ordinateurs. Les technologies de type CUPS (Common Unix® Printing System) et le protocole LPD (Line Printer Daemon) permettent de se connecter à une imprimante réseau. Pour accéder à une imprimante accessible indirectement, indiquez l’adresse IP ou le nom d’hôte du serveur d’impression. Grâce à ce mécanisme, vous pouvez envoyer un document à un URI LPD lorsque le réseau dispose d’un LPD en cours d’exécution. Le mécanisme permet d’acheminer le document vers n’importe quelle imprimante connectée au réseau sur lequel un protocole LPD est en cours d’exécution.
