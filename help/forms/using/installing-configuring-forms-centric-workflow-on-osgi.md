---
title: Installation et configuration d’un workflow basé sur l’utilisation de Forms sur OSGi
seo-title: Installing and Configuring Forms-centric workflow on OSGi
description: Installez et configurez les communications interactives AEM Forms pour créer les correspondances commerciales, les documents, les déclarations, les avis, les courriers marketing, les factures et les kits de bienvenue.
seo-description: Install and configure AEM Forms Interactive Communications to create business correspondences, documents, statements, benefit notices, marketing mails, bills, and welcome kits.
uuid: 847c3351-dc46-4e60-a023-0f4e9e057c7c
topic-tags: installing
discoiquuid: 7333641e-8c8c-4b52-a7da-a2976c88592c
role: Admin
exl-id: 308b106f-4c5a-49d6-a7f6-c1e8a0bf62e9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1645'
ht-degree: 69%

---

# Installation et configuration d’un workflow basé sur l’utilisation de Forms sur OSGi {#installing-and-configuring-forms-centric-workflow-on-osgi}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

## Présentation {#introduction}

Les entreprises collectent et traitent des données à partir de plusieurs formulaires, systèmes d’arrière-plan et autres sources de données. Le traitement des données implique des procédures de révision et d’approbation, des tâches répétitives et l’archivage données. Par exemple, lʼexamen d’un formulaire et sa conversion en document PDF. Lorsquʼelles sont effectuées manuellement, les tâches répétitives peuvent prendre beaucoup de temps et de ressources.

Vous pouvez utiliser le [Workflow basé sur lʼutilisation de Forms sur OSGi](/help/forms/using/aem-forms-workflow.md) pour créer rapidement des workflows basés sur des formulaires adaptatifs. Ces workflows peuvent vous aider à automatiser les workflows de révision et d’approbation, les workflows de gestion commerciale et d’autres tâches répétitives. Ces processus permettent également de traiter des documents (créer, assembler, distribuer et archiver des documents de PDF, ajouter des signatures numériques pour limiter l’accès aux documents, décoder des formulaires à code-barres, etc.) et utiliser le processus de signature Acrobat Sign avec des formulaires et des documents.

Une fois configurés, ces workflows peuvent être déclenchés manuellement pour terminer un processus ou une exécution défini par programmation lorsque les utilisateurs envoient un formulaire ou une communication interactive. Cette fonctionnalité est incluse dans le package du module complémentaire AEM Forms.

AEM Forms est une plateforme d’entreprise performante. Le workflow basé sur lʼutilisation de Forms sur OSGi n’est qu’une des fonctionnalités d’AEM Forms. Pour obtenir la liste complète des fonctionnalités, voir [Présentation d’AEM Forms](/help/forms/using/introduction-aem-forms.md).

>[!NOTE]
>
>Avec le processus basé sur l’utilisation de Forms sur OSGi, vous pouvez rapidement créer et déployer des processus pour différentes tâches sur la pile OSGi, sans avoir à installer la fonctionnalité Process Management complète sur la pile JEE. Regardez une [comparaison](/help/forms/using/capabilities-osgi-jee-workflows.md) des workflows AEM basés sur lʼutilisation de Forms sur OSGi et la gestion des processus sur JEE pour découvrir les différences et les similitudes entre les fonctionnalités.
>
>Après la comparaison, si vous choisissez d’installer la fonctionnalité de gestion des processus sur la pile JEE, consultez la section [Installation ou mise à niveau d’AEM Forms sur JEE](/help/forms/home.md) pour obtenir des informations détaillées sur l’installation et la configuration de la pile JEE et des fonctionnalités de gestion des processus.

## Topologie de déploiement {#deployment-topology}

Le module complémentaire AEM Forms est une application déployée sur AEM. Une instance dʼauteur ou de traitement AEM (auteur de production) suffit pour exécuter le workflow basé sur lʼutilisation de Forms sur OSGi. Une instance de traitement est une instance dʼ[auteur AEM sécurisée de manière renforcée](/help/forms/using/hardening-securing-aem-forms-environment.md). Nʼeffectuez pas de création réelle, comme la création de workflows ou de formulaires adaptatifs, sur lʼauteur de production.

La topologie suivante est une topologie indicatif pour exécuter les fonctionnalités AEM Forms Interactive Communications, Correspondence Management, AEM Forms Data Capture et Forms-Centric Workflow on OSGi. Pour plus d’informations sur la topologie, voir [Topologies d’architecture et de déploiement pour AEM Forms](/help/forms/using/aem-forms-architecture-deployment.md).

![topologie-recommandée](assets/recommended-topology.png)

Le workflow basé sur lʼutilisation de Forms AEM Forms sur OSGi exécute la boîte de réception AEM et l’interface utilisateur de création de modèle de workflow AEM sur les instances d’auteur d’AEM Forms.

## Configuration requise {#system-requirements}

>[!NOTE]
>
>Passez à la section [Étapes suivantes](#next-steps) du document si vous avez déjà installé AEM Forms sur OSGi, comme détaillé dans lʼarticle [Installation et configuration des fonctionnalités de capture de données](/help/forms/using/installing-configuring-aem-forms-osgi.md).

Avant dʼinstaller et de configurer le workflow basé sur lʼutilisation de Forms sur OSGi, assurez-vous de disposer des éléments suivants :

* Le matériel et l’infrastructure logicielle sont en place. Pour obtenir une liste détaillée des matériels et logiciels pris en charge, voir [Conditions techniques applicables](/help/sites-deploying/technical-requirements.md).

* Le chemin d’installation de l’instance AEM ne contient pas d’espaces.
* Une instance AEM est en cours d’exécution. Dans la terminologie AEM, une « instance » est une copie d’AEM s’exécutant sur un serveur en mode de création ou de publication. Vous avez besoin d’au moins une instance AEM (auteur ou traitement) pour exécuter un workflow basé sur lʼutilisation de Forms sur OSGi :

   * **Auteur**: Instance d’AEM utilisée pour créer, télécharger et modifier du contenu et administrer le site web. Une fois que le contenu est publié, il est répliqué sur l’instance de publication.
   * **Traitement :** Une instance de traitement est une [Auteur AEM sécurisé](/help/forms/using/hardening-securing-aem-forms-environment.md) instance. Vous pouvez configurer une instance de création et renforcer sa sécurité après avoir effectué l’installation.
   * **Publier**: Une instance AEM qui diffuse le contenu publié au public sur Internet ou sur un réseau interne.

* Les exigences de mémoire sont respectées. Le package complémentaire AEM Forms nécessite :

   * 15 Go d’espace temporaire pour les installations basées sur Microsoft Windows.
   * 6 Go d’espace temporaire pour les installations Unix.

* Configuration requise supplémentaire pour les systèmes UNIX : Si vous utilisez un système d’exploitation UNIX, installez les packages suivants à partir du support d’installation du système d’exploitation correspondant.

<table> 
 <tbody>
  <tr>
   <td>expat</td> 
   <td>libxcb</td> 
   <td>freetype</td> 
   <td>libXau</td> 
  </tr>
  <tr>
   <td>libSM</td> 
   <td>zlib</td> 
   <td>libICE</td> 
   <td>libuuid</td> 
  </tr>
  <tr>
   <td>glibc</td> 
   <td>libXext</td> 
   <td><p>nss-softokn-freebl</p> </td> 
   <td>fontconfig</td> 
  </tr>
  <tr>
   <td>libX11</td> 
   <td>libXrender</td> 
   <td>libXrandr</td> 
   <td>libXinerama</td> 
  </tr>
 </tbody>
</table>

## Installation du package complémentaire AEM Forms {#install-aem-forms-add-on-package}

Le module complémentaire AEM Forms est une application déployée sur AEM. Le package contient un workflow basé sur l’utilisation de Forms sur OSGi ainsi que d’autres fonctionnalités. Suivez les étapes ci-après pour installer le package du module complémentaire :

1. Ouvrez la [Distribution de logiciels](https://experience.adobe.com/downloads). Vous avez besoin d’un Adobe ID pour vous connecter à la Distribution de logiciels.
1. Appuyez sur **[!UICONTROL Adobe Experience Manager]** disponible dans le menu d’en-tête.
1. Dans le **[!UICONTROL Filtres]** section :
   1. Sélectionner **[!UICONTROL Forms]** de la **[!UICONTROL Solution]** liste déroulante.
   2. Sélectionnez la version et le type du package. Vous pouvez également utiliser l’option **[!UICONTROL Rechercher des téléchargements]** pour filtrer les résultats.
1. Appuyez sur le nom de package applicable à votre système d’exploitation, sélectionnez **[!UICONTROL Accepter les conditions du CLUF]**, puis appuyez sur **[!UICONTROL Télécharger]**.
1. Ouvrez [Package Manager](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html?lang=fr) et cliquez sur **[!UICONTROL Télécharger le package]** pour télécharger le package.
1. Sélectionnez le package et cliquez sur **[!UICONTROL Installer]**.

   Vous pouvez également télécharger le package via le lien direct répertorié dans l’article [Version d’AEM Forms](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=fr).

1. Une fois le package installé, vous êtes invité à redémarrer l’instance AEM. **Ne redémarrez pas immédiatement le serveur.** Avant d’arrêter le serveur AEM Forms, attendez que les messages ServiceEvent REGISTERED et ServiceEvent UNREGISTERED cessent d’apparaître dans le fichier [repertoire-installation-AEM]/crx-quickstart/logs/error.log et que le journal soit stable.
1. Répétez les étapes 1 à 7 sur toutes les instances de création et de publication.

## Configurations post-installation {#post-installation-configurations}

AEM Forms comporte quelques configurations obligatoires et facultatives. Les configurations obligatoires incluent la configuration des bibliothèques BouncyCastle et de l’agent de sérialisation. Les configurations facultatives incluent la configuration du répartiteur et d’Adobe Target.

### Configurations post-installation obligatoires {#mandatory-post-installation-configurations}

#### Configuration des bibliothèques RSA et BouncyCastle  {#configure-rsa-and-bouncycastle-libraries}

Pour déléguer le démarrage des bibliothèques, procédez comme suit sur toutes les instances dʼauteur et de publication :

1. Arrêtez l’instance AEM sous-jacente.
1. Ouvrez le fichier [répertoire d’installation AEM]\crx-quickstart\conf\sling.properties pour le modifier.

   Si vous utilisiez [répertoire d’installation AEM]\crx-quickstart\bin\start.bat pour démarrer AEM, modifiez le fichier sling.properties dans [racine_AEM]\crx-quickstart\.

1. Ajoutez les propriétés suivantes au fichier sling.properties :

   ```
   sling.bootdelegation.class.com.rsa.jsafe.provider.JsafeJCE=com.rsa.*
   sling.bootdelegation.class.org.bouncycastle.jce.provider.BouncyCastleProvider=org.bouncycastle.*
   ```

1. (AIX uniquement) Ajoutez les propriétés suivantes au fichier sling.properties :

   ```
   sling.bootdelegation.xerces=org.apache.xerces.*
   ```

1. Enregistrez et fermez le fichier, puis démarrez l’instance AEM.
1. Répétez les étapes 1 à 4 sur toutes les instances de création et de publication.

#### Configurer l’agent de sérialisation {#configure-the-serialization-agent}

Pour autoriser le package, procédez comme suit sur toutes les instances dʼauteur et de publication :

1. Ouvrez AEM Configuration Manager dans une fenêtre de navigateur. L’URL par défaut est `https://[server]:[port]/system/console/configMgr`.
1. Recherchez et ouvrez la **configuration du pare-feu de désérialisation**.
1. Ajoutez le package **sun.util.calendar** au champ **Placer sur la liste autorisée**. Cliquez sur Enregistrer.
1. Répétez les étapes 1 à 3 sur toutes les instances de création et de publication.

### Configurations optionnelles de post-installation {#optional-post-installation-configurations}

#### La configuration de Dispatcher {#configure-dispatcher}

Dispatcher est un outil de mise en cache et d’équilibrage de charge pour AEM. Le répartiteur AEM aide également à protéger le serveur AEM des attaques. Vous pouvez augmenter la sécurité de votre instance AEM en utilisant le répartiteur conjointement avec un serveur Web de niveau élevé. Si vous utilisez [Dispatcher](https://helpx.adobe.com/fr/experience-manager/dispatcher/using/dispatcher-configuration.html), effectuez les configurations suivantes pour AEM Forms :

1. Configurez l’accès à AEM Forms:

   Ouvrez le fichier dispatcher.any pour le modifier. Accédez à la section filter et ajoutez le filtre suivant à la section filter :

   `/0025 { /type "allow" /glob "* /bin/xfaforms/submitaction*" } # to enable AEM Forms submission`

   Enregistrez et fermez le fichier. Pour plus d’informations sur les filtres, voir [Documentation de Dispatcher](https://helpx.adobe.com/fr/experience-manager/dispatcher/using/dispatcher-configuration.html).

1. Configurez le service de filtrage des référents :

   Connectez-vous au gestionnaire de configuration Apache Felix en tant qu’administrateur. L’URL par défaut du gestionnaire de configuration est `https://[server]:[port_number]/system/console/configMgr`. Dans le menu **Configurations**, sélectionnez l’option **Apache Sling Referrer Filter.** Dans le champ Allow Hosts, saisissez le nom d’hôte du répartiteur afin de l’activer comme référent et cliquez sur **Enregistrer**. Le format de l’entrée est `https://[server]:[port]`.

#### Configuration du cache {#configure-cache}

La mise en cache est un mécanisme qui permet de raccourcir les temps d’accès aux données, de réduire la latence et d’améliorer les vitesses d’entrée/sortie (E/S). Le cache de formulaires adaptatifs stocke uniquement le contenu de HTML et la structure JSON d’un formulaire adaptatif sans enregistrer de données préremplies. Cela permet de réduire le temps nécessaire au rendu d’un formulaire adaptatif.

* Lors de l’utilisation du cache de formulaires adaptatifs, utilisez la variable [AEM Dispatcher](https://helpx.adobe.com/fr/experience-manager/dispatcher/using/dispatcher-configuration.html) pour mettre en cache les bibliothèques clientes (CSS et JavaScript) d’un formulaire adaptatif.
* Lors du développement de composants personnalisés, gardez le cache de formulaires adaptatifs désactivé sur le serveur utilisé pour le développement.

Pour configurer la mise en cache des formulaires adaptatifs, procédez comme suit :

1. Accédez à la page de configuration de la console web AEM à l’adresse `https://[server]:[port]/system/console/configMgr`.
1. Cliquez sur la **[!UICONTROL configuration de canal web de communication interactive de formulaire adaptatif]** pour éditer ses valeurs de configuration. Dans la boîte de dialogue Modifier les valeurs de configuration, spécifiez le nombre maximal de formulaires ou de documents qu’une instance du serveur AEM Forms peut mettre en cache le champ **Nombre de formulaires adaptatifs**. La valeur par défaut est 100. Cliquez sur **Enregistrer**.

   >[!NOTE]
   >
   >Pour désactiver le cache, définissez la valeur du champ Nombre de Forms adaptatives sur **0**. Le cache est réinitialisé, et tous les formulaires et documents sont supprimés du cache lorsque vous désactivez ou modifiez la configuration du cache.

#### Configuration d’Acrobat Sign {#configure-adobe-sign}

Acrobat Sign active les processus de signature électronique pour les formulaires adaptatifs. Les signatures électroniques améliorent les processus de traitement des documents pour les services juridiques, commercial, des ressources humaines, et bien d’autres domaines.

Dans un scénario standard de processus Acrobat Sign et Forms centré sur OSGi, un utilisateur remplit un formulaire adaptatif pour demander un service. Par exemple, un formulaire de demande de carte de paiement et d’allocation. Lorsqu’un utilisateur remplit, envoie et signe le formulaire de demande, un workflow d’approbation / de rejet est lancé. Le fournisseur de services examine la demande dans AEM boîte de réception et utilise Acrobat Sign pour la signer électroniquement. Pour activer des processus de signature électronique similaires, vous pouvez intégrer Acrobat Sign à AEM Forms.

Pour utiliser Acrobat Sign avec AEM Forms, [Intégration d’Acrobat Sign à AEM Forms](/help/forms/using/adobe-sign-integration-adaptive-forms.md).

## Étapes suivantes {#next-steps}

Un environnement a été configuré pour utiliser le workflow centré sur l’utilisation de Forms en fonction des fonctionnalités OSGi. Maintenant, les prochaines étapes pour utiliser cette fonctionnalité sont les suivantes :

* [Utiliser un workflow centré sur les formulaires sur OSGi](/help/forms/using/aem-forms-workflow.md)
* [Référence sur les étapes de workflow](/help/sites-developing/workflows-step-ref.md)
* [Post-traitement des lettres et communications interactives](/help/forms/using/submit-letter-topostprocess.md)
