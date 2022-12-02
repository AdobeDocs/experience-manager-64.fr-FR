---
title: Intégrer [!DNL Experience Manager] Ressources avec Adobe InDesign Server
description: Découvrez comment intégrer [!DNL Experience Manager] Ressources avec InDesign Server.
contentOwner: AG
feature: Publishing
role: Admin
exl-id: d80562f7-071c-460a-9c68-65f48d36fbd9
source-git-commit: cc9b6d147a93688e5f96620d50f8fc8b002e2d0d
workflow-type: tm+mt
source-wordcount: '1674'
ht-degree: 66%

---

# Intégration de ressources à Adobe InDesign Server {#integrating-aem-assets-with-indesign-server}

Adobe Experience Manager Assets utilise :

* un proxy pour distribuer la charge de certaines tâches de traitement. Un proxy est une instance [!DNL Experience Manager] qui communique avec un programme de traitement du proxy afin d’accomplir une tâche spécifique, et avec d’autres instances [!DNL Experience Manager] pour diffuser les résultats.
* Le programme de traitement du proxy définit et gère une tâche spécifique.

Il peut s&#39;agir de diverses tâches; par exemple, l’utilisation d’Adobe InDesign Server pour traiter des fichiers.

Pour charger complètement des fichiers dans [!DNL Experience Manager] Les ressources que vous avez créées avec Adobe InDesign sont utilisées par proxy. Cette méthode utilise un programme de traitement du proxy pour communiquer avec Adobe InDesign Server, qui exécute des [scripts](https://www.adobe.com/devnet/indesign/documentation.html#idscripting) afin d’extraire des métadonnées et de générer divers rendus pour  Assets. [!DNL Experience Manager] Le worker de proxy active la communication bidirectionnelle entre l’InDesign Server et la variable [!DNL Experience Manager] instances dans une configuration cloud.

>[!NOTE]
>
>Adobe InDesign se compose de deux produits :
>
>* [InDesign](https://www.adobe.com/fr/products/indesign.html)\
   >  Vous permet de concevoir des mises en page pour l’impression ou la diffusion numérique.
>
>* [InDesign Server](https://www.adobe.com/fr/products/indesignserver.html)\
   >  Vous permet de créer des documents de façon automatisée, et par programmation, sur la base de vos mises en pages créées avec InDesign. Il s’exécute en tant que service offrant une interface pour son moteur [ExtendScript](https://www.adobe.com/devnet/scripting.html).\
   >  Les scripts sont écrits dans ExtendScript et sont similaires à JavaScript. Pour plus d’informations sur les scripts Adobe InDesign, voir [https://www.adobe.com/devnet/indesign/documentation.html#idscripting](https://www.adobe.com/devnet/indesign/documentation.html#idscripting).
>


## Fonctionnement de l’extraction {#how-the-extraction-works}

L’InDesign Server peut être intégré à [!DNL Experience Manager] Ressources afin que les fichiers créés avec InDesign ( `.indd`) peut être chargé, des rendus générés, *all* fichier multimédia extrait (vidéo, par exemple) et stocké en tant que ressources :

>[!NOTE]
>
>Les versions précédentes d’[!DNL Experience Manager] permettaient seulement d’extraire le XMP et la miniature. Désormais, tous les médias peuvent être extraits.

1. Téléchargez votre `.indd` vers [!DNL Experience Manager] Ressources.
1. Une infrastructure envoie des scripts de commande vers InDesign Server via SOAP (Simple Object Access Protocol).

   Ce script de commande permet d’effectuer les opérations suivantes :

   * Récupération de la variable `.indd` fichier .
   * Exécuter des commandes InDesign Server :

      * La structure, le texte et tous les fichiers multimédias sont extraits.
      * Des rendus PDF et JPG sont générés.
      * Des rendus HTML et IDML sont générés.
   * Republiez les fichiers obtenus dans [!DNL Experience Manager] Ressources.

   >[!NOTE]
   >
   >IDML est un format XML qui permet de générer un rendu de *l’intégralité* du contenu d’un fichier InDesign. Il est stocké sous forme d’une archive compressée au format [Zip](https://www.techterms.com/definition/zip).
   >
   >Voir [Formats d’échange Adobe InDesign INX et IDML](https://www.peachpit.com/articles/article.aspx?p=1381880&amp;seqNum=8) pour plus d’informations.

   >[!CAUTION]
   >
   >Si l’InDesign Server n’est pas installé ou configuré, vous pouvez tout de même télécharger un `.indd` dans [!DNL Experience Manager]. Toutefois, les rendus générés seront limités à `png` et `jpeg`, vous ne pourrez pas générer `html`, `idml` ou les rendus de page.

1. Après l’extraction et la génération du rendu :

   * La structure est identique à `cq:Page` (type de rendu).
   * Le texte et les fichiers extraits sont stockés dans [!DNL Experience Manager] Ressources.
   * Tous les rendus sont stockés dans [!DNL Experience Manager] Ressources, dans la ressource elle-même.

## Intégration d’InDesign Server à [!DNL Experience Manager] {#integrating-the-indesign-server-with-aem}

Pour intégrer l’InDesign Server à utiliser avec [!DNL Experience Manager] Ressources et après avoir configuré votre proxy, vous devez :

1. [installer InDesign Server](#installing-the-indesign-server) ;
1. Si nécessaire, [ [!DNL Experience Manager] configurer le workflow  Assets](#configuring-the-aem-assets-workflow).

   Cette opération n’est nécessaire que si les valeurs par défaut ne sont pas adaptées à votre instance.

1. Configurer un [programme de traitement du proxy pour InDesign Server](#configuring-the-proxy-worker-for-indesign-server).

### Configuration de InDesign Server   {#installing-the-indesign-server}

Pour installer et démarrer InDesign Server afin de l’utiliser avec [!DNL Experience Manager]:

1. Téléchargez et installez Adobe InDesign Server.

   >[!NOTE]
   >
   >InDesign Server (CS6 ou version ultérieure).

1. Si nécessaire, vous pouvez personnaliser la configuration de votre instance InDesign Server.

1. À partir de la ligne de commande, démarrez le serveur :

   `<*ids-installation-dir*>/InDesignServer.com -port 8080`

   Cela démarre le serveur avec le module complémentaire SOAP en écoute sur le port 8080. Tous les messages de journal et les résultats sont écrits directement dans la fenêtre de commande.

   >[!NOTE]
   >
   >Si vous souhaitez enregistrer les messages de sortie vers un fichier, puis utiliser une redirection ; par exemple, sous Windows :
   >
   >`<ids-installation-dir>/InDesignServer.com -port 8080 > ~/temp/INDD-logfile.txt 2>&1`

### Configuration de la variable [!DNL Experience Manager] Processus des ressources {#configuring-the-aem-assets-workflow}

[!DNL Experience Manager] Ressources dispose d’un workflow préconfiguré. **Ressources de mise à jour de gestion des actifs numériques**, qui comprend plusieurs étapes de processus spécifiques à InDesign :

* [Extraction de médias](#media-extraction)
* [Extraction de page](#page-extraction)

Ce workflow est configuré avec les valeurs par défaut qui peuvent être adaptées à votre configuration pour diverses instances d’auteur (il s’agit d’un workflow standard, aussi des informations supplémentaires sont disponibles sous [Modifier un workflow](/help/sites-developing/workflows-models.md#configuring-a-workflow-step)). Si vous utilisez les valeurs par défaut (port SOAP compris), aucune configuration n’est nécessaire.

Après la configuration, chargez les fichiers d’InDesign dans [!DNL Experience Manager] Les ressources (par l’une des méthodes habituelles) déclenchent le workflow requis pour traiter la ressource et préparer les différents rendus. Testez votre configuration en transférant un fichier `.indd`[!DNL Experience Manager] dans  Assets afin de confirmer que vous voyez les différents rendus créés par IDS sous . `<*your_asset*>.indd/Renditions`

#### Extraction de médias {#media-extraction}

Cette étape contrôle l’extraction de médias à partir de la `.indd` fichier .

Pour la personnaliser, vous pouvez modifier l’onglet **[!UICONTROL Arguments]** dans l’étape **[!UICONTROL Extraction de médias]**.

![Arguments d’extraction de médias et chemins de scripts](assets/media_extraction_arguments_scripts.png)

Arguments d’extraction de médias et chemins de scripts

* **Bibliothèque ExtendScript** : il s’agit d’une simple bibliothèque de méthodes HTTP GET/POST, requise par les autres scripts.

* **Développer les scripts** : vous pouvez indiquer ici différentes combinaisons de script. Si vous souhaitez que vos propres scripts soient exécutés sur le serveur InDesign, enregistrez-les sous `/apps/settings/dam/indesign/scripts`.

   Pour plus d’informations sur les scripts d’InDesign, voir [https://www.adobe.com/devnet/indesign/documentation.html#idscripting](https://www.adobe.com/devnet/indesign/documentation.html#idscripting).

>[!CAUTION]
>
>Ne modifiez pas la bibliothèque ExtendScript. La bibliothèque fournit la fonctionnalité HTTP requise pour communiquer avec Sling. Ce paramètre spécifie la bibliothèque à envoyer à Adobe InDesign Server pour y être utilisée.

Le script `ThumbnailExport.jsx` exécuté par l’étape de workflow Extraction des médias génère un rendu miniature au format .jpg. Ce rendu est utilisé par l’étape du workflow Traiter les miniatures afin de générer les rendus statiques requis par [!DNL Experience Manager].

Vous pouvez configurer l’étape du workflow Traiter les miniatures de manière à générer des rendus statiques de différentes tailles. Veillez à ne pas supprimer les valeurs par défaut, car elles sont requises par la variable [!DNL Experience Manager] Interface utilisateur des ressources. Enfin, l’étape Processus de suppression du rendu d’aperçus d’image efface le rendu miniature .jpg, car il n’est plus nécessaire.

#### Extraction de page   {#page-extraction}

Cette opération crée une page [!DNL Experience Manager] à partir des éléments extraits. Un gestionnaire d’extraction est utilisé pour extraire les données d’un rendu (actuellement HTML ou IDML). Ces données sont ensuite utilisées pour créer une page avec PageBuilder.

Pour la personnaliser, vous pouvez modifier l’onglet **[!UICONTROL Arguments]** dans l’étape **Extraction de page**.

![chlimage_1-289](assets/chlimage_1-289.png)

* **Gestionnaire d’extraction de page**: Dans la liste déroulante, sélectionnez le gestionnaire à utiliser. Un gestionnaire d’extraction fonctionne sur un rendu spécifique, sélectionné par un `RenditionPicker` associé (voir l’API `ExtractionHandler`). Par défaut, le gestionnaire d’extraction d’exportation IDML est disponible. Il fonctionne sur la variable `IDML` rendu généré lors de l’étape MediaExtract .

* **Nom de la page** : indique le nom que vous souhaitez attribuer à la page résultante. Si vous laissez le champ vide, le nom est « page » (ou une variante si « page » existe déjà).

* **Titre de la page** : indique le titre que vous souhaitez attribuer à la page résultante.

* **Racine de la page** : chemin d’accès à la racine de la page résultante. Si rien n’est indiqué, le noeud contenant les rendus de la ressource est utilisé.

* **Modèle de page** : modèle à utiliser lors de la génération de la page résultante.

* **Conception de page** : conception de page à utiliser lors de la génération de la page résultante.

### Configuration du traitement du proxy pour InDesign Server {#configuring-the-proxy-worker-for-indesign-server}

>[!NOTE]
>
>Le programme de traitement réside sur une instance de proxy.

1. Dans la console Outils, développez **[!UICONTROL Configurations Cloud Services]** dans le volet de gauche. Développez ensuite **[!UICONTROL Configuration de proxy Cloud]**.

1. Double-cliquez sur **[!UICONTROL IDS Worker]** pour ouvrir la configuration.

1. Cliquez sur **[!UICONTROL Modifier]** pour ouvrir la boîte de dialogue de configuration et définir les paramètres requis :

   ![proxy_idsworkerconfig](assets/proxy_idsworkerconfig.png)

   * **Pool IDS**: Points d’entrée SOAP à utiliser pour communiquer avec l’InDesign Server. Vous pouvez ajouter, supprimer ou trier les éléments au besoin.

1. Cliquez sur **[!UICONTROL OK]** pour enregistrer.

### Configuration de l’externaliseur de liens DAY CQ  {#configuring-day-cq-link-externalizer}

Si l’InDesign Server et [!DNL Experience Manager] sont sur des hôtes différents ou l’une de ces applications ou les deux ne fonctionnent pas sur les ports par défaut, configurez **Externalisateur de lien Day CQ** pour définir le nom d’hôte, le port et le chemin d’accès au contenu de l’InDesign Server.

1. Accédez à Configuration Manager à l’adresse suivante : `https://[AEM_server]:[port]/system/console/configMgr`.
1. Localisez la configuration **[!UICONTROL Externalisateur de lien Day CQ]**. Cliquez sur **[!UICONTROL Modifier]** pour ouvrir.
1. Les paramètres de l’externaliseur de liens permettent de créer des URL absolues pour le [!DNL Experience Manager] et pour le déploiement [!DNL InDesign Server]. Utilisation **[!UICONTROL Domaines]** pour spécifier le nom d’hôte et le chemin d’accès au contexte pour la variable [!DNL Adobe InDesign Server]. Suivez les instructions qui s’affichent. Cliquez sur **[!UICONTROL Enregistrer]**.

   ![Paramètres de l’externaliseur de lien](assets/link-externalizer-config.png)

### Activation du traitement parallèle des tâches pour InDesign Server {#enabling-parallel-job-processing-for-indesign-server}

Vous pouvez désormais activer le traitement parallèle des tâches pour IDS.

Vous devez d’abord déterminer le nombre maximal de tâches parallèles (`x`) qu’InDesign Server peut traiter :

* Sur une machine unique à processeur multi-cœurs, le nombre maximum de tâches parallèles (x) qu’InDesign Server peut traiter est égal au nombre de processeurs qui exécutent IDS, moins un.
* Lorsque vous exécutez IDS sur plusieurs machines, vous devez compter le nombre total de processeurs disponibles (sur chaque ordinateur) et soustraire le nombre total d’ordinateurs.

Pour configurer le nombre de tâches parallèles d’IDS :

1. Ouvrez l’onglet **[!UICONTROL Configurations]** de la console Felix ; par exemple :    

   `http://localhost:4502/system/console/configMgr`

1. Sélectionnez la file d’attente du traitement d’IDS sous :

   `Apache Sling Job Queue Configuration`

1. Définissez :

   * **[!UICONTROL Type]** - `Parallel`
   * **[!UICONTROL Nombre max. de tâches parallèles]** - `<*x*>` (conformément au calcul ci-dessus)

1. Enregistrez ces modifications.
1. Pour activer la prise en charge multi-session pour Adobe CS6 et versions ultérieures, cochez la case `enable.multisession.name` case à cocher sous `com.day.cq.dam.ids.impl.IDSJobProcessor.name configuration`.
1. Créez un [pool de &lt; `*x*>` Travailleurs IDS en ajoutant des points de fin SOAP à la configuration du traitement IDS](#configuring-the-proxy-worker-for-indesign-server).

   S’il existe plusieurs machines exécutant InDesign Server, ajoutez les points d’extrémité SOAP (nombre de processeurs par ordinateur -1) pour chaque ordinateur.

   >[!NOTE]
   >
   >Lorsque vous travaillez avec un groupe de programmes de traitement, vous pouvez activer la liste bloquée des programmes de traitement IDS.
   >
   >Pour ce faire, cochez la case « enable.retry.name » sous la configuration de `com.day.cq.dam.ids.impl.IDSJobProcessor.name`, ce qui déclenche de nouvelles tentatives pour les tâches IDS.
   >
   >En outre, sous la configuration `com.day.cq.dam.ids.impl.IDSPoolImpl.name`, définissez une valeur positive pour le paramètre `max.errors.to.blacklist`, qui détermine le nombre de tentatives pour une tâche avant qu’un IDS ne soit exclu de la liste des gestionnaires de tâches.
   >
   >Par défaut, le traitement IDS est revalidé après une durée en minutes configurable (`retry.interval.to.whitelist.name`). Si le programme de traitement est en ligne, il est retiré de la liste bloquée.

<!-- TBD: Make updates to configurations for allow and block list after product updates are done. See CQ-4298427.
-->

## Activation de la prise en charge du serveur Adobe InDesign 10.0 ou version ultérieure {#enabling-support-for-indesign-server-or-higher}

Pour InDesign Server 10.0 ou version ultérieure, réalisez les étapes suivantes pour activer la prise en charge multisession.

1. Ouvrez Configuration Manager à partir de votre [!DNL Assets] instance `https://[aem_server]:[port]/system/console/configMgr`.
1. Modifiez la configuration de `com.day.cq.dam.ids.impl.IDSJobProcessor.name`.
1. Sélectionner **[!UICONTROL ids.cc.enable]** puis cliquez sur **[!UICONTROL Enregistrer]**.

>[!NOTE]
>
>Pour l’intégration de [!DNL InDesign Server] à [!DNL Assets], utilisez un processeur multicœur, car la fonction de prise en charge de sessions nécessaire pour l’intégration n’est pas prise en charge sur les systèmes à un seul cœur.

## Configuration des informations d’identification du Experience Manager {#configure-aem-credentials}

Vous pouvez modifier les informations d’identification d’administrateur par défaut (nom d’utilisateur et mot de passe) pour accéder au serveur InDesign à partir de votre [!DNL Experience Manager] sans interrompre l’intégration avec le serveur Adobe InDesign.

1. Accédez à `/etc/cloudservices/proxy.html`.
1. Dans la boîte de dialogue, indiquez le nouveau nom d’utilisateur et le nouveau mot de passe.
1. Enregistrez les identifiants.
