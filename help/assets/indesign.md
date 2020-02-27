---
title: Intégration d’AEM Assets à Adobe InDesign Server
description: Découvrez comment intégrer AEM Assets à InDesign Server.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 0d70a672a2944e2c03b54beb3b5f734136792ab1

---


# Intégration d’AEM Assets à Adobe InDesign Server {#integrating-aem-assets-with-indesign-server}

Adobe Experience Manager (AEM) Assets utilise :

* Un proxy pour distribuer la charge de certaines tâches de traitement. Un proxy est une instance AEM qui communique avec un programme de traitement du proxy afin d’accomplir une tâche spécifique, et avec d’autres instances AEM pour diffuser les résultats. 
* Le programme de traitement du proxy définit et gère une tâche spécifique.

Elles peuvent couvrir une grande variété de tâches; par exemple, l’utilisation d’Adobe InDesign Server pour traiter des fichiers.

Pour transférer intégralement des fichiers créés avec Adobe InDesign vers AEM Assets, un proxy est utilisé. Cette méthode utilise un programme de traitement du proxy pour communiquer avec Adobe InDesign Server, qui exécute des [scripts](https://www.adobe.com/devnet/indesign/documentation.html#idscripting) afin d’extraire des métadonnées et de générer divers rendus pour AEM Assets. Le programme de traitement du proxy permet une communication bidirectionnelle entre InDesign Server et les instances AEM dans une configuration cloud.

>[!NOTE]
>
>Adobe InDesign se compose de deux produits :
>
>* [InDesign](https://www.adobe.com/products/indesign.html)\
   >  Vous permet de concevoir des mises en page pour l’impression ou la diffusion numérique.
   >
   >
* [InDesign Server](https://www.adobe.com/products/indesignserver.html)\
   >  Vous permet de créer des documents de façon automatisée et programmatique sur la base de vos mises en pages créées avec InDesign. Il s’exécute en tant qu’un service offrant une interface pour son moteur [ExtendScript](https://www.adobe.com/devnet/scripting.html).\
   >  Les scripts sont écrits dans ExtendScript, ce qui est similaire à JavaScript. For information about Indesign scripts see [https://www.adobe.com/devnet/indesign/documentation.html#idscripting](https://www.adobe.com/devnet/indesign/documentation.html#idscripting).
>



## Fonctionnement de l’extraction {#how-the-extraction-works}

The InDesign Server can be integrated with AEM Assets so that files created with InDesign ( `.indd`) can be uploaded, renditions generated, *all* media extracted (for example, video) and stored as assets:

>[!NOTE]
>
>Les versions précédentes d’AEM permettaient seulement d’extraire le XMP et la miniature. Désormais, tous les médias peuvent être extraits. 

1. Upload your `.indd` file to AEM Assets.
1. Une infrastructure envoie des scripts de commande vers InDesign Server via SOAP (Simple Object Access Protocol).

    Ce script de commande permet de :

   * Retrieve the `.indd` file.
   * Exécuter des commandes InDesign Server :

      * La structure, le texte et tous les fichiers multimédias sont extraits.
      * Des rendus PDF et JPG sont générés.
      * Des rendus HTML et IDML sont générés.
   * Republier les fichiers résultants dans AEM Assets.
   >[!NOTE]
   >
   >IDML est un format XML qui permet de générer un rendu de *l’intégralité* du contenu d’un fichier InDesign. Il est stocké sous forme d’une archive compressée au format [Zip](https://www.techterms.com/definition/zip).
   >
   >See [Adobe InDesign Interchange Formats INX and IDML](http://www.peachpit.com/articles/article.aspx?p=1381880&seqNum=8) for further information.

   >[!CAUTION]
   >
   >If the InDesign Server is not installed or not configured, then you can still upload an `.indd` file into AEM. However the renditions generated will be limited to `png` and `jpeg`, you will not be able to generate `html`, `idml` or the page renditions.

1. Après l’extraction et la génération de rendu : 

   * La structure est identique à `cq:Page` (type de rendu).
   * Le texte et les fichiers extraits sont stockés dans AEM Assets. 
   * Tous les rendus sont stockés dans des AEM Assets, dans la ressource même.

## Intégration d’InDesign Server avec AEM {#integrating-the-indesign-server-with-aem}

Pour intégrer le serveur InDesign en vue de son utilisation avec AEM Assets et après avoir configuré votre proxy, vous devez effectuer les opérations suivantes :

1. [Installer InDesign Server](#installing-the-indesign-server).
1. Si nécessaire, [configurer le processus AEM Assets](#configuring-the-aem-assets-workflow).

   Cette opération n’est nécessaire que si les valeurs par défaut ne sont pas adaptées à votre instance.

1. Configurer un [programme de traitement du proxy pour InDesign Server](#configuring-the-proxy-worker-for-indesign-server).

### Configuration de InDesign Server {#installing-the-indesign-server}

Pour installer et démarrer InDesign Server afin de l’utiliser avec AEM : 

1. Téléchargez et installez Adobe InDesign Server.

   >[!NOTE]
   >
   >InDesign Server (CS6 et version ultérieure).

1. Si nécessaire, vous pouvez personnaliser la configuration de votre instance de InDesign Server. 

1. À partir de la ligne de commande, démarrez le serveur :

   `<*ids-installation-dir*>/InDesignServer.com -port 8080`

   Cela démarre le serveur avec le module complémentaire SOAP en écoute sur le port 8080. Tous les messages de journal et les résultats sont écrits directement dans la fenêtre de commande.

   >[!NOTE]
   >
   >Si vous souhaitez enregistrer les messages de sortie vers un fichier, puis utiliser une redirection, par exemple, sous Windows :
   >
   >`<ids-installation-dir>/InDesignServer.com -port 8080 > ~/temp/INDD-logfile.txt 2>&1`

### Configuration du processus AEM Assets {#configuring-the-aem-assets-workflow}

AEM Assets has a pre-configured workflow **DAM Update Asset**, that has several process steps specifically for InDesign:

* [Extraction de médias](#media-extraction)
* [Extraction de page](#page-extraction)

Ce processus est configuré avec les valeurs par défaut qui peuvent être adaptées à votre configuration pour diverses instances d’auteur (il s’agit d’un processus standard, aussi des informations supplémentaires sont disponibles sous [Modifier un processus](/help/sites-developing/workflows-models.md#configuring-a-workflow-step)). Si vous utilisez les valeurs par défaut (y compris le port SOAP), aucune configuration n’est nécessaire.

Après la configuration, le transfert de fichiers InDesign dans AEM Assets (via les méthodes habituelles) déclenche le processus requis pour le traitement de la ressource et la préparation des différents rendus. Test your configuration by uploading an `.indd` file into AEM Assets to confirm that you see the different renditions created by IDS under `<*your_asset*>.indd/Renditions`

#### Extraction de médias {#media-extraction}

This step controls the extraction of media from the `.indd` file.

Pour personnaliser, vous pouvez modifier l’onglet **[!UICONTROL Arguments]** de l’étape **[!UICONTROL Extraction]** de médias.

![Arguments d’extraction de médias et chemins de scripts](assets/media_extraction_arguments_scripts.png)

Arguments d’extraction de médias et chemins de scripts

* **Bibliothèque** ExtendScript : Il s’agit d’une simple bibliothèque de méthodes http get/post, requise par les autres scripts.

* **Etendre les scripts**: Vous pouvez spécifier différentes combinaisons de scripts ici. If you want your own scripts to be executed on the InDesign Server, save the scripts at `/apps/settings/dam/indesign/scripts`.

   For information about Indesign scripts see [https://www.adobe.com/devnet/indesign/documentation.html#idscripting](https://www.adobe.com/devnet/indesign/documentation.html#idscripting).

>[!CAUTION]
>
>Ne modifiez pas la bibliothèque ExtendScript. La bibliothèque fournit la fonctionnalité HTTP requise pour communiquer avec Sling. Ce paramètre spécifie la bibliothèque à envoyer au serveur Adobe InDesign pour y être utilisée.

Le script `ThumbnailExport.jsx` exécuté par l’étape de processus Extraction des médias génère un rendu miniature au format .jpg. Ce rendu est utilisé par l’étape du processus de miniatures afin de générer les rendus statiques requis par AEM.

Vous pouvez configurer l’étape du processus de miniatures de manière à générer des rendus statiques de différentes tailles. Assurez-vous de ne pas supprimer les valeurs par défaut, car elles sont requises par l’interface utilisateur d’AEM Assets. Enfin, l’étape Processus de suppression du rendu d’aperçus d’image efface le rendu miniature .jpg, car il n’est plus nécessaire.

#### Extraction de page {#page-extraction}

Cette opération crée une page AEM à partir des éléments extraits. Un gestionnaire d’extraction est utilisé pour extraire les données d’un rendu (actuellement HTML ou IDML). Ces données sont ensuite utilisées pour créer une page avec PageBuilder. 

Pour personnaliser, vous pouvez modifier l’onglet **[!UICONTROL Arguments]** de l’étape d’**extraction de page**.

![chlimage_1-289](assets/chlimage_1-289.png)

* **Gestionnaire** d&#39;extraction de page : Dans la liste déroulante, sélectionnez le gestionnaire à utiliser. Un gestionnaire d’extraction opère sur un rendu spécifique, choisi par un autre `RenditionPicker` (voir l’API `ExtractionHandler`). Par défaut, le gestionnaire d’extraction d’exportation IDML est disponible. Il fonctionne sur le `IDML` rendu généré dans l’étape MediaExtract.

* **Nom** de page : Indiquez le nom que vous souhaitez affecter à la page résultante. Si vous laissez le champ vide, le nom est « page » (ou une variante si « page » existe déjà).

* **Titre** de la page : Indiquez le titre que vous souhaitez affecter à la page résultante.

* **Chemin** racine de la page : Chemin d’accès à l’emplacement racine de la page résultante. Si rien n’est indiqué, le noeud contenant les rendus de la ressource est utilisé.

* **Modèle** de page : Modèle à utiliser lors de la génération de la page résultante.

* **Conception** de page : Conception de page à utiliser lors de la génération de la page résultante.

### Configuration du traitement du proxy pour InDesign Server {#configuring-the-proxy-worker-for-indesign-server}

>[!NOTE]
>
>Le programme de traitement réside sur une instance de proxy.

1. Dans la console Outils, développez **[!UICONTROL Configurations de services Cloud]** dans le volet de gauche. Développez ensuite **[!UICONTROL Configuration de proxy Cloud]**. 

1. Cliquez deux fois sur le **[!UICONTROL programme de travail IDS]** pour ouvrir la configuration.

1. Cliquez sur **[!UICONTROL Modifier]** pour ouvrir la boîte de dialogue de configuration et définir les paramètres requis : 

   ![proxy_idsworkerconfig](assets/proxy_idsworkerconfig.png)

   * **Pool** IDS : Point(s) de fin SOAP à utiliser pour communiquer avec le serveur InDesign. Vous pouvez ajouter, supprimer ou trier les éléments au besoin.

1. Cliquez sur **[!UICONTROL OK]** pour enregistrer.

### Configuration de l’externaliseur de lien DAY CQ  {#configuring-day-cq-link-externalizer}

Si InDesign Server et AEM sont exécutés sur des hôtes différents ou si ces deux applications ne fonctionnent pas sur les ports par défaut, configurez **l’externaliseur de lien Day CQ** afin de définir le nom d’hôte, le port et le chemin d’accès au contenu pour InDesign Server.

1. Accédez à Configuration Manager à l’adresse URL `https://[AEM_server]:[port]/system/console/configMgr`.
1. Localisez l’**[!UICONTROL Externalisateur de liens Day CQ]** de configuration, puis cliquez sur l’icône **[!UICONTROL Modifier]** pour l’ouvrir.
1. Spécifiez le nom d’hôte et le chemin d’accès contextuel de InDesign Server, puis cliquez sur **[!UICONTROL Enregistrer]**.

   ![chlimage_1-290](assets/chlimage_1-290.png)

### Enabling Parallel Job Processing for InDesign Server(s) {#enabling-parallel-job-processing-for-indesign-server-s}

Vous pouvez désormais activer le traitement parallèle des tâches pour IDS.

Vous devez d’abord déterminer le nombre maximal de tâches parallèles (`x`) que InDesign Server peut traiter :

* Sur une machine unique à processeur multi-cœurs, le nombre maximum de tâches parallèles (x) qu’InDesign Server peut traiter est égal au nombre de processeurs qui exécutent IDS, moins un.
* Lorsque vous exécutez IDS sur plusieurs machines, vous devez compter le nombre total de processeurs disponibles (sur chaque ordinateur) et soustraire le nombre total d’ordinateurs.

Pour configurer le nombre de tâches parallèles d’IDS :

1. Ouvrez l’onglet **[!UICONTROL Configurations]** de la console Felix ; par exemple :

   `http://localhost:4502/system/console/configMgr`

1. Sélectionnez la file d’attente du traitement d’IDS sous :

   `Apache Sling Job Queue Configuration`

1. Définir:

   * **[!UICONTROL Type]** - `Parallel`
   * **[!UICONTROL Tâches]** parallèles maximales - `<*x*>` (comme calculé ci-dessus)

1. Enregistrez ces modifications.
1. Pour activer la prise en charge de plusieurs sessions pour Adobe CS6 et versions ultérieures, cochez la `enable.multisession.name` case sous `com.day.cq.dam.ids.impl.IDSJobProcessor.name configuration`.
1. Create a [pool of &lt; `*x*>` IDS workers by adding SOAP endpoints to the IDS Worker configuration](#configuring-the-proxy-worker-for-indesign-server).

   S’il existe plusieurs machines exécutant InDesign Server, ajoutez les points d’extrémité SOAP (nombre de processeurs par ordinateur -1) pour chaque ordinateur.

   >[!NOTE]
   >
   >Vous pouvez activer la mise sur liste noire du traitement IDS lorsque vous travaillez avec un groupe de programmes de traitement.
   >
   >To do so, enable the &quot;enable.retry.name&quot; checkbox, under the `com.day.cq.dam.ids.impl.IDSJobProcessor.name` configuration, which enables IDS job retrials.
   >
   >En outre, sous la configuration `com.day.cq.dam.ids.impl.IDSPoolImpl.name`, définissez une valeur positive pour le paramètre max.errors.to.blacklist, qui détermine le nombre de tentatives pour une tâche avant qu’un IDS ne soit exclu de la liste des gestionnaires de tâches.
   >
   >Par défaut, le traitement IDS est revalidé après une durée en minutes configurable (retry.interval.to.whitelist.name). Si le programme de traitement est en ligne, il est retiré de la liste noire.

## Activation de la prise en charge d’Adobe InDesign Server 10.0 ou version ultérieure {#enabling-support-for-indesign-server-or-higher}

Pour InDesign Server 10.0 ou version ultérieure, réalisez les étapes suivantes pour activer la prise en charge multisession.

1. Ouvrez Configuration Manager à partir de votre instance AEM Assets `https://[AEM_server]:[port]/system/console/configMgr`.
1. Edit the configuration `com.day.cq.dam.ids.impl.IDSJobProcessor.name`.
1. Select the **[!UICONTROL ids.cc.enable]** option, and click **[!UICONTROL Save]**.

>[!NOTE]
>
>Pour l’intégration de InDesign Server dans AEM Assets, utilisez un processeur multicœur, car la fonction Prise en charge de sessions nécessaire pour l’intégration n’est pas prise en charge sur les systèmes à un seul cœur.

## Configuration des informations d’identification AEM {#configure-aem-credentials}

Vous pouvez modifier les informations d’identification d’administrateur par défaut (nom d’utilisateur et mot de passe) pour accéder au serveur InDesign à partir de votre instance AEM sans rompre l’intégration au serveur Adobe InDesign.

1. Aller à `/etc/cloudservices/proxy.html`.
1. Dans la boîte de dialogue, indiquez le nouveau nom d’utilisateur et le nouveau mot de passe.
1. Enregistrez les identifiants.
