---
title: Installation et configuration des sites de référence d’AEM Forms
seo-title: Installation et configuration des sites de référence d’AEM Forms
description: Les sites de référence AEM Forms décrivent comment utiliser AEM Forms pour implémenter un flux de bout en bout dans une entreprise.
seo-description: Les sites de référence AEM Forms décrivent comment utiliser AEM Forms pour implémenter un flux de bout en bout dans une entreprise.
uuid: 087d58a1-d84e-49ac-a82d-4e7fc708f00f
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: introduction
discoiquuid: 2feb4a9c-57ad-4c6b-a572-0047bc409bbb
translation-type: tm+mt
source-git-commit: 6a8fa45ec61014acebe09048066972ecb1284641
workflow-type: tm+mt
source-wordcount: '2922'
ht-degree: 48%

---


# Installé et configuré les sites de référence d’AEM Forms {#set-up-and-configure-aem-forms-reference-sites}

AEM Forms fournit une implémentation de site de référence pour démontrer la manière dont AEM Forms permet à des organisations gouvernementales et du secteur des services financiers de transformer leurs transactions complexes en expériences numériques simples et attrayantes, n’importe où, n’importe quand et sur n’importe quel périphérique.

Les sites de référence We.Finance et We.Gov utilisent des exemples de cas réels pour collaborer avec leurs clients existants et potentiels depuis leur tout premier contact, à la gestion des correspondances et transactions, de manière personnalisée et économique.

Les sites de référence vous permettent d’explorer et de voir en action les principales fonctionnalités suivantes d’AEM Forms.

* Simplification de la création de formulaires adaptatifs attrayants et réactifs et de communications interactives.
* Communications interactives pour créer des communications client interactives, personnalisées et réactives qui s’adaptent au paramètre et à la mise en page du périphérique.
* Intégration des données permettant de se connecter à des sources de données disparates afin de préremplir et d’envoyer des données de formulaire par le biais d’un modèle de données de formulaire.
* Processus des formulaires pour automatiser les processus d’entreprise.
* Fonctionnalités de traitement et de gestion des données utilisateur.
* Intégration avec Adobe Sign garantissant une signature et un envoi sécurisé des formulaires adaptatifs.
* Intégration avec Adobe Target pour fournir des recommandations ciblées et effectuer les tests A/B, pour augmenter le retour sur investissement d’un formulaire.
* Intégration à Adobe Analytics pour mesurer les performances d’un formulaire ou d’une campagne et prendre des décisions éclairées.
* Amélioration de l’expérience de remplissage des formulaires.

Les sites de référence offrent des ressources réutilisables que vous pouvez utiliser comme modèles pour créer vos propres ressources.

* Intégration avec Adobe Sign garantissant une signature et un envoi sécurisé des formulaires adaptatifs.

* Intégration avec Adobe Sign garantissant une signature et un envoi sécurisé des formulaires adaptatifs.

## Conditions préalables et étapes et de la configuration des sites de référence {#prerequisites-and-steps-to-set-up-reference-sites}

Avant de configurer le site de référence, assurez-vous que vous disposez des éléments suivants :

* **aem essentiels**

   aem QuickStart, module complémentaire AEM Forms et packages de site de référence. Voir [Versions d’AEM Forms](https://helpx.adobe.com/fr/aem-forms/kb/aem-forms-releases.html) pour plus d’informations sur les packages de modules complémentaires et de sites de référence.

* **Un service SMTP** Vous pouvez utiliser n’importe quel service SMTP.

* **Compte de développeur Adobe Sign et application API Adobe Sign**

   Pour utiliser les fonctions de signature numérique, un compte de développeur Adobe Sign est requis. Voir [Adobe Sign](https://acrobat.adobe.com/fr/fr/why-adobe/developer-form.html).

* Instance en cours d&#39;exécution de Microsoft Dynamics 365 à intégrer à AEM Forms. Pour exécuter le site de référence, vous importez les données d&#39;exemple dans l&#39;instance Microsoft Dynamics afin de préremplir la communication interactive utilisée dans le site de référence.
* Instance en cours d’exécution d’AEM 6.4 avec le module complémentaire Forms. Pour plus d’informations, reportez-vous à la section [Installation et configuration d’AEM Forms](installing-configuring-aem-forms-osgi.md).

Effectuez les étapes suivantes dans l’ordre recommandé pour installer et configurer les sites de référence.

<table> 
 <tbody> 
  <tr> 
   <th><strong>Étape</strong></th> 
   <th><strong>Configuration</strong></th> 
   <th><strong>Remarques</strong></th> 
  </tr> 
  <tr> 
   <td><a href="#installaemforms">Installer et configurer AEM Forms</a></td> 
   <td>Auteur et publication</td> 
   <td>Installez et configurez des instances d’auteur et de publication AEM Forms.</td> 
  </tr> 
  <tr> 
   <td><a href="#ssl">Configurer SSL</a></td> 
   <td>Auteur et publication<br /> </td> 
   <td>Activez HTTP via SSL pour sécuriser les communications avec Adobe Sign.</td> 
  </tr> 
  <tr> 
   <td><p><a href="#externalizer">Configuration de Day CQ Link Externalizer (Externalisateur du lien vers Day CQ)</a></p> </td> 
   <td>Auteur et publication<br /> </td> 
   <td><p>Les cas d’utilisation de site de référence fournissent des messages électroniques pour diverses transactions. Ce paramètre est requis pour la diffusion de la newsletter par courrier électronique. Cela permet d’assurer que les URL et les images pointent vers une instance de publication. </p> </td> 
  </tr> 
  <tr> 
   <td><a href="#cqmail">Configuration du service de messagerie Day CQ</a></td> 
   <td>Auteur et publication</td> 
   <td>Requis pour les communications par courrier électronique.</td> 
  </tr> 
  <tr> 
   <td><a href="#xss">Remplacement de la configuration XSS par défaut</a></td> 
   <td>Publication</td> 
   <td>Utilisé pour remplacer les caractères $, { et } bloqués par la sécurité xss.</td> 
  </tr> 
  <tr> 
   <td><a href="#aemds">Configurer les paramètres AEM DS</a></td> 
   <td>Création</td> 
   <td>Configurez AEM DS pour l’envoi de formulaire sur l’instance de publication et les processus de traitement sur l’instance d’auteur.</td> 
  </tr> 
  <tr> 
   <td><a href="#refsite">Déployer les packages des sites de référence</a></td> 
   <td>Création</td> 
   <td>Déployez les packages des sites de référence sur l’instance d’auteur AEM Forms.</td> 
  </tr> 
  <tr> 
   <td><a href="/help/forms/using/setup-reference-sites.md#optional-import-sample-data-into-microsoft-dynamics">Importation d’exemples de données dans Microsoft Dynamics</a></td> 
   <td>Auteur et publication</td> 
   <td>Importer les données d’exemple pour la demande de carte de crédit, la demande de prêt immobilier et la présentation de la demande d’assurance habitation</td> 
  </tr> 
  <tr> 
   <td><a href="/help/forms/using/setup-reference-sites.md#configure-oauth-cloud-service-for-microsoft-dynamics">Configurer le service cloud OAuth pour Microsoft Dynamics</a></td> 
   <td>Auteur et publication</td> 
   <td>Configurez le service cloud OAuth en AEM Forms pour activer la communication entre AEM Forms et Microsoft Dynamics. </td> 
  </tr> 
  <tr> 
   <td><a href="#scheduler">Configurer le planificateur Adobe Sign</a></td> 
   <td>Auteur et publication<br /> </td> 
   <td>Modifiez la configuration du planificateur pour vérifier l’état toutes les deux minutes.</td> 
  </tr> 
  <tr> 
   <td><a href="#sign-service">Configurer le service cloud Adobe Sign de site de référence</a></td> 
   <td>Auteur et publication<br /> </td> 
   <td>Une configuration qui comprend des packages de sites de référence et qui doit être reconfigurée avec des informations d’identification valides.</td> 
  </tr> 
  <tr> 
   <td><a href="#anonymous">Configurer le service de configuration commun aux formulaires pour les utilisateurs anonymes</a></td> 
   <td>Publication</td> 
   <td>La configuration permet l’envoi, la signature et le Document de génération d’enregistrements pour les utilisateurs anonymes.</td> 
  </tr> 
  <tr> 
   <td><a href="#fdm">Modifier le fichier Swagger du service Rest pour le modèle de données du formulaire</a></td> 
   <td>Auteur et publication<br /> </td> 
   <td>Modifiez le service pour votre environnement.</td> 
  </tr> 
 </tbody> 
</table>

## Installer et configurer AEM Forms  {#install-and-configure-aem-forms}

Installez et déployez AEM Forms comme décrit dans [Installation et configuration d’AEM Forms sur OSGi](/help/forms/using/installing-configuring-aem-forms-osgi.md).

>[!NOTE]
>
>Configurez les agents de réplication et d’inversion de la réplication s’il existe plusieurs instances de publication ou si les instances d’auteur et de publication se trouvent sur des ordinateurs différents.

## Configurer SSL  {#ssl}

La configuration SSL est requise pour communiquer avec les serveurs Adobe Sign. Pour obtenir des instructions détaillées, voir [Activation du protocole HTTP sur SSL](/help/sites-administering/ssl-by-default.md).

>[!CAUTION]
>
>Ne configurez pas l’option forcer SSL sur le dossier `/etc/map`.

## Configuration de Day CQ Link Externalizer (Externalisateur du lien vers Day CQ){#externalizer}

En AEM, le **Externalizer** est un service OSGI qui vous permet de transformer par programmation un chemin de ressources (ex. /path/to/my/page) dans une URL externe et absolue (par exemple, https://www.mycompany.com/path/to/my/page) en préfixant le chemin d’accès avec un DNS préconfiguré. Voir [Externalisation des URL](/help/sites-developing/externalizer.md).

>[!CAUTION]
>
>N’externalisez pas vers l’URL HTTPS si vous utilisez certificat autosigné pour SSL.
>
>En outre, vous devez utiliser localhost plutôt que hostname pour le serveur local.

Effectuez les étapes suivantes sur les instances d’auteur et de publication :

1. Accédez à Configuration OSGi à l’adresse https://*nom_hôte>*:*port>*/system/console/configMgr.
1. Recherchez et appuyez sur **[!UICONTROL Day CQ Link Externalizer]** configuration.

   La boîte de dialogue Day CQ Link Externalizer s’ouvre à des fins d’édition de la configuration.

1. Dans la boîte de dialogue Day CQ Link Externalizer, dans le champ Domaines :

   * Sur l’instance de rédaction, spécifiez une URL de publication accessible depuis n’importe quel système externe. Par exemple, un nom d’hôte ou un serveur Web de publication.
   * Sur l’instance de publication, indiquez les URL de rédaction et de publication.

1. Sur les instances d’auteur et de publication, assurez-vous que l’URL du serveur local est indiquée dans le champ des domaines.
1. Appuyez sur **[!UICONTROL Enregistrer]**. Patientez un moment le temps que tous les services redémarrent.

## Configuration du service de messagerie Day CQ  {#cqmail}

Une mise en œuvre de site de référence nécessite que les courriers électroniques soient envoyés aux exemples d’utilisateurs lorsqu’ils remplissent les formulaires et les envoient. La configuration du service de messagerie Day CQ vous permet de fournir des détails de serveur SMTP pour envoyer des courriers électroniques automatisés aux clients. Voir [Configuration des notifications par courrier électronique](/help/sites-administering/notification.md).

Procédez comme suit pour configurer le service de messagerie sur l’instance de publication :

1. Accédez à Configuration OSGi à l’adresse https://*nom_hôte>*:*port>*/system/console/configMgr.
1. Recherchez **[!UICONTROL Day CQ Mail Service]** et appuyez dessus pour l’ouvrir en vue de sa configuration.
1. Indiquez les valeurs hostname et de port du serveur SMTP.
1. Appuyez sur **[!UICONTROL Save]** (Enregistrer).

>[!NOTE]
>
>Vous pouvez utiliser votre service SMTP d’entreprise ou des services publics comme Gmail. Pour la configuration du service SMTP, voir la documentation correspondante.

## Remplacement de la configuration XSS par défaut  {#xss}

Les modèles de courrier électronique pour le site de référence We.Finance contiennent des liens personnalisés dans les courriers électroniques. Ces liens possèdent un espace réservé tel que `${placeholder}`. Ces espaces réservés sont remplacés par des valeurs réelles avant l’envoi des courriers électroniques. La configuration de protection XSS par défaut pour AEM n’autorise pas les accolades (**{ }**) dans l’URL d’un contenu HTML. Cependant, vous pouvez remplacer la configuration par défaut en procédant comme suit sur l’instance de publication :

1. Copiez `/libs/cq/xssprotection/config.xml` dans `/apps/cq/xssprotection/config.xml`.
1. Ouvrez `/apps/cq/xssprotection/config.xml`.
1. Dans la section `common-regexps`, modifiez l&#39;entrée `onsiteURL` comme suit et enregistrez le fichier.

   `<regexp name="onsiteURL" value="([\p{L}\p{N}\\\.\#@\$\{\}%\+&;\-_~,\?=/!\*\(\)]*|\#(\w)+)"/>`

>[!NOTE]
>
>Les accolades (**{}**) sont incluses en tant que caractères acceptés dans l’URL du contenu HTML.

Après la configuration du serveur SMTP, essayez de remplir un formulaire à l’aide de Sarah Rose et de l’enregistrer en tant que brouillon. Lorsque vous enregistrez en tant que brouillon, vous obtenez une option permettant de recevoir le brouillon par courrier électronique. Lorsque vous appuyez sur le bouton **Envoyer un courrier électronique**, si vous recevez un courrier électronique contenant un lien vers le brouillon de la demande, votre configuration de courrier électronique est correcte. Assurez-vous que vous vous connectez en utilisant les identifiants de Sarah pour afficher le brouillon.

## Configurer les paramètres AEM DS  {#aemds}

aem paramètres du service DS sont requis sur l’instance de publication pour les communications par courrier électronique dans les cas d’utilisation du site de référence. Pour obtenir des instructions détaillées sur la configuration du service DS AEM sur l’instance de publication, voir [Configuration des paramètres DS AEM](/help/forms/using/configuring-the-processing-server-url-.md).

Pour les sites de référence AEM Forms, dans le service des paramètres AEM DS, spécifiez l’URL du serveur de publication au lieu de celle du serveur de traitement.

>[!CAUTION]
>
>Ne placez pas `/lc` dans l’URL du serveur de traitement si vous la configurez pour AEM Forms OSGi.

## Déployer les packages des sites de référence {#refsite}

Installez les packages de sites de référence suivants à l’aide de la Distribution de logiciels.

* [AEM-FORMS-6.4-FSI-REF-SITE](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/fd/AEM-FORMS-6.4-FSI-REF-SITE)
* [AEM-FORMS-6.4-GOV-REF-SITE](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/fd/AEM-FORMS-6.4-GOV-REF-SITE)

Pour en savoir plus sur l’utilisation des packages, voir [Comment utiliser les packages](/help/sites-administering/package-manager.md).

Une fois que vous avez installé les packages et avez lancé les instances de rédaction et de publication, consultez les URL suivantes dans votre navigateur :

* `https://[server]:[port]/wegov`
* `https://[server]:[port]/wefinance`

Si votre installation est terminée, vous pouvez accéder aux pages d’accueil des sites de référence We.Gov et We.Finance.

## (Facultatif) Importez des exemples de données dans Microsoft Dynamics {#optional-import-sample-data-into-microsoft-dynamics}

Les sites de référence des demandes de prêt immobilier et d&#39;assurance automobile sont configurés pour utiliser les enregistrements de Microsoft Dynamics. Le package de site de référence installe une entité personnalisée et des exemples d&#39;enregistrements que vous pouvez importer dans Microsoft Dynamics pour exécuter le site de référence. Effectuez les étapes suivantes pour migrer et configurer les données d’exemple :

Pour importer l&#39;entité personnalisée pour la demande d&#39;assurance automatique :

1. Téléchargez le package de solution **WeFinanceAutoInsurance_1_0.zip** à partir de `https://[server]:[port]/content/aemforms-refsite-collaterals/we-finance/auto-insurance/ms-dynamics/WeFinanceAutoInsurance_1_0.zip` sur votre instance d’auteur AEM.
1. Dans votre instance Microsoft Dynamics, accédez à **[!UICONTROL Solutions]** dans le menu **[!UICONTROL Paramètres]** et cliquez sur **[!UICONTROL Importer]**. Sélectionnez et importez le package.

Pour importer l&#39;entité personnalisée pour la demande d&#39;assurance automatique :

1. Téléchargez le package **AEMFormsFSIRefsite_1_0.zip** à l’adresse https://[author]:[port]/content/aemforms-refsite-collaterals/we-finance/home-mortgage/ms-dynamics/AEMFormsFSIRefsite_1_0.zip. Sélectionnez et importez le package.

1. Dans votre instance Microsoft Dynamics, accédez à **[!UICONTROL Solutions]** dans le menu **[!UICONTROL Paramètres]** et cliquez sur **[!UICONTROL Importer]**. Sélectionnez et importez le package.

Pour importer les enregistrements de contrat d&#39;assurance et de client :

1. Téléchargez les fichiers de données **We.Finance Customers.csv, We.Finance Auto Insurance Renewals.csv** et **home loan** à partir des emplacements suivants sur l&#39;instance d&#39;auteur de votre AEM :

   * `https://[server]:[port/content/aemforms-refsite-collaterals/we-finance/auto-insurance/ms-dynamics/We.Finance Customers.csv`
   * `https://[server]:[port/content/aemforms-refsite-collaterals/we-finance/auto-insurance/ms-dynamics/We.Finance Auto Insurance Renewals.csv`
   * `https://[server]:[port]/content/aemforms-refsite-collaterals/we-finance/home-mortgage/ms-dynamics/Sarah%20Rose%20Contact.csv`

1. Dans votre instance Microsoft Dynamics, procédez comme suit :

   * Accédez à **[!UICONTROL Ventes > Clients We.Finance]** et cliquez sur **[!UICONTROL Importer]**.
   * Accédez à **[!UICONTROL Ventes > Nous.Finance Auto Insurance]** et cliquez sur **[!UICONTROL Importer]**.
   * Accédez à **[!UICONTROL Ventes > We.Finance Home Mortgage]** et cliquez sur **[!UICONTROL Importer]**.

## Configurer le service cloud OAuth pour Microsoft Dynamics {#configure-oauth-cloud-service-for-microsoft-dynamics}

Configurez le service cloud OAuth en AEM Forms pour activer la communication entre AEM Forms et Microsoft Dynamics. Effectuez les étapes suivantes pour configurer l’Cloud Service OAuth sur les instances d’auteur et de publication d’AEM :

1. Sur AEM instance d’auteur, accédez à **[!UICONTROL Outils > Cloud Services > Sources de données > global]**. Appuyez sur l&#39;icône **[!UICONTROL Refsite Dynamics Integration]** et sur **[!UICONTROL Properties]**.
1. Accédez au compte Microsoft Azure Active Directory. Ajoutez l’URL de configuration du service cloud copiée dans le paramètre **[!UICONTROL URL de réponse]** pour votre application enregistrée. Enregistrez la configuration.
1. Dans l&#39;onglet Paramètres d&#39;authentification, spécifiez **[!UICONTROL Racine du service]**, **[!UICONTROL ID client]**, **[!UICONTROL Secret client]** et **[!UICONTROL URL de ressource]** pour votre instance Microsoft Dynamics. Cliquez sur **[!UICONTROL Se connecter à OAuth]** qui redirige vers la page de connexion Microsoft Dynamics.
1. Entrez vos informations de connexion. Une fois connecté, vous êtes redirigé vers la page de configuration du service cloud AEM Forms. Cliquez sur **[!UICONTROL Enregistrer et fermer]**. La configuration du service cloud est enregistrée.
1. Accédez à **[!UICONTROL Forms > Data Integrations > We.Finance]**. Sélectionnez Assurance automatique (Dynamics) et cliquez sur Modifier. Les entités Microsoft Dynamics sont répertoriées sous l&#39;onglet Sources de données. Attendez que toutes les entités soient récupérées de Microsoft Dynamics et répertoriées sous l&#39;onglet Sources de données.
1. Sélectionnez l&#39;**[!UICONTROL entité AutoInsuranceRenewal]** et cliquez sur **[!UICONTROL Objet de modèle de test]**. Dans la section de demande d’entrée, spécifiez la valeur de l’ID de client &quot;900001&quot; et cliquez sur **[!UICONTROL Test]**. La section Output affiche les enregistrements extraits de Microsoft Dynamics pour l&#39;ID de client 900001.
1. Dans la section de demande d’entrée, spécifiez la valeur de l’ID de client &quot;900001&quot; et cliquez sur **[!UICONTROL Test]**. La section Output affiche les enregistrements extraits de Microsoft Dynamics pour l&#39;ID de client 900001.
1. Répétez les étapes 1 à 6 sur l’instance de publication.

## Configurer le planificateur Adobe Sign {#scheduler}

Effectuez les étapes suivantes sur les instances d’auteur et de publication :

1. Accédez à AEM Web Configuration Console à l’adresse `https://[server]:[host]/system/console/configMgr`.
1. Recherchez **[!UICONTROL Adobe Sign Configuration Service]** et appuyez dessus pour l’ouvrir en vue de sa configuration.
1. Configurez **[!UICONTROL l&#39;Expression de l&#39;Planificateur de mise à jour d&#39;état]** comme **0 0/2 &amp;ast; &amp;ast; &amp;ast; ?**.

   >[!NOTE]
   >
   >La configuration du planificateur ci-dessus vérifie l’état du service Adobe Sign toutes les deux minutes.

1. Appuyez sur **[!UICONTROL Enregistrer]**.

## Configurer le service cloud Adobe Sign de site de référence  {#sign-service}

Effectuez les étapes suivantes sur les instances d’auteur et de publication :

1. Accédez à **[!UICONTROL Outils > Cloud Services > Adobe Sign > global]**. Sélectionnez **[!UICONTROL Signal du site de référence AEM Forms]** et appuyez sur **[!UICONTROL Propriétés]**.

   >[!CAUTION]
   >
   >Assurez-vous que l’URL https://[host]:[ssl_port]/mnt/overlay/adobesign/cloudservices/adobesign/properties.html est ajoutée à la liste d’URL de redirection de la configuration OAuth de l’application API Adobe Sign.

1. Indiquez l’ID client et le secret de la configuration OAuth d’application Adobe Sign.
1. (Facultatif) Sélectionnez l’option **[!UICONTROL Activer Adobe Sign pour les pièces jointes]** et appuyez sur **[!UICONTROL Se connecter à Adobe Sign]**. Cela permet d’ajouter les fichiers joints à un formulaire adaptatif au document Adobe Sign envoyé à des fins de signature.
1. Appuyez sur **[!UICONTROL Connectez-vous à Adobe Sign]** et connectez-vous avec vos informations d’identification Adobe Sign.

## Configurer le service de configuration commun aux formulaires {#anonymous}

Effectuez les étapes suivantes sur l’instance de publication pour autoriser l’accès des utilisateurs anonymes :

1. Accédez à AEM Web Configuration Console à l’adresse `https://[server]:[port]/system/console/configMgr`.
1. Recherchez **[!UICONTROL Forms Common Configuration Service]** et appuyez dessus pour l’ouvrir en vue de sa configuration.
1. Configurez le champ **[!UICONTROL Autoriser]** pour **[!UICONTROL Tous les utilisateurs]**.
1. Appuyez sur **[!UICONTROL Enregistrer]**.

## Modifier le service Rest pour le modèle de données de formulaire  {#fdm}

Effectuez les étapes suivantes sur les instances d’auteur et de publication :

1. Accédez à CRXDE à `https://[server]:[port]/crx/de/index.jsp`.
1. Accédez à **/conf/global/settings/cloudconfigs/fdm/roi-rest/jcr:content/swaggerFile** et ouvrez le fichier swagger.
1. Mettez à jour les paramètres d’hôte et de port en fonction de votre environnement.
1. Enregistrez les paramètres.
1. (**Instance Auteur uniquement**) Accédez à **[!UICONTROL Outils]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Sources de données]** > **[!UICONTROL global]**. Sélectionnez **[!UICONTROL roi-rest]** et appuyez sur **[!UICONTROL Propriétés]**. Appuyez sur **[!UICONTROL Paramètres d&#39;authentification]** et définissez **[!UICONTROL Type d&#39;authentification]** sur **[!UICONTROL Authentification de base]**. Indiquez `admin`/ `admin`comme nom d’utilisateur/mot de passe pour accéder au service. Appuyez sur **[!UICONTROL Save &amp; Close]** (Enregistrer et fermer). 

## Intégrer au Marketing Cloud {#integrate-with-marketing-cloud}

Vous pouvez intégrer l&#39;AEM Forms à Adobe Analytics et à Adobe Target. Adobe Analytics vous aide à générer des rapports et à analyser les performances des formulaires adaptatifs, mais Adobe Target vous aide à fournir des expériences personnalisées et à effectuer des tests A/B pour les formulaires adaptatifs.

Procédez comme suit pour configurer Adobe Analytics et Adobe Target dans AEM Forms.

### Configuration d’Adobe Analytics {#configure-adobe-analytics}

L’intégration d’Adobe Analytics à AEM Forms vous permet de surveiller et d’analyser la manière dont vos clients interagissent avec vos formulaires et documents. Il vous aide à identifier et à résoudre les problèmes et à agir pour augmenter le taux de conversion.

Pour tester cette fonctionnalité sur le site de référence, configurez votre compte Analytics tel que décrit dans [Configuration des analyses et des rapports](/help/forms/using/configure-analytics-forms-documents.md).

Pour générer un rapport, les données sources sont regroupées avec les sites de référence. Avant d’utiliser les données de base, procédez comme suit :

1. Assurez-vous que les configurations d’analyse We.Finance et We.Gov sont disponibles dans les services AEM Cloud. Vous pouvez trouver les services cloud de l’une des manières suivantes :

   * Accédez à **[!UICONTROL Outils>Cloud Services>Cloud Services hérités]** ou accédez à https://&lt;hôte>:&lt;port>/libs/cq/core/content/tools/cloudservices.html.
   * Dans la page **[!UICONTROL Cloud Services]**, sous **[!UICONTROL Adobe Analytics]**, cliquez sur `Show Configurations`. Vous pouvez voir les configurations We.Finance et We.Gov disponibles. Cliquez pour ouvrir la configuration. Dans la page de configuration, cliquez sur **[!UICONTROL Modifier]**. Fournissez une Société valide, un nom d’utilisateur, un secret partagé (mot de passe) et un centre de données, puis cliquez sur **[!UICONTROL Se connecter à Analytics]**. Une fois que la boîte de dialogue Connexion s’affiche, cliquez sur **[!UICONTROL OK]** dans la boîte de dialogue de configuration. Configurez la structure sous la configuration Analytics comme décrit dans la section [Configuration d’Analytics et de rapports](/help/forms/using/configure-analytics-forms-documents.md).

1. Accédez à https://&quot;a0/>host *:&quot;a2/>port&lt;a3/&quot;/system/console/configMgr et procédez comme suit :***

   * Dans la page **[!UICONTROL Configuration de la console Web]**, recherchez **[!UICONTROL Configuration AEM Forms Analytics]** et cliquez dessus.
   * Dans le champ **[!UICONTROL SiteCatalyst Framework]** de la boîte de dialogue Configuration de AEM Forms Analytics, sélectionnez we-finance(we-finance) ou we-gov(we-gov).
   * Cliquez sur **[!UICONTROL Enregistrer]** et laissez la page s’actualiser.

1. Accédez au gestionnaire de formulaires à l’adresse https://&lt;hôte>:&lt;port>/aem/forms et procédez comme suit :

   * Ouvrez le dossier We.Finance ou We.Gov, puis sélectionnez le formulaire pour lequel vous souhaitez afficher le rapport.
   * Dans la barre d’outils des actions, cliquez sur Rapport d’analyse. Une fois que vous avez activé les analyses pour le formulaire, cliquez sur Rapport d’analyse. Vous constatez qu’un rapport vide a été généré. Après la génération d’un rapport vierge, vous devez fournir les données d’origine fournies avec le module de site de référence pour générer le rapport d’analyse à des fins de démonstration.

   Les sites de référence fournissent au rapports d’analyse des données de base sur les cas d’utilisation des cartes de crédit, des prêts hypothécaires et des allocations familiales. Pour la configuration des données de base, voir les sections [Présentation du site de référence We.Finance](/help/forms/using/finance-reference-site-walkthrough.md) et [Présentation du site de référence We.Gov](/help/forms/using/gov-reference-site-walkthrough.md).

### Configuration de Target {#configure-target}

Le site de référence bénéficie de l’intégration d’Adobe Target à AEM Forms, ce qui vous permet d’incorporer du contenu ciblé et personnalisé dans des documents adaptatifs. Ce module permet également la création de tests A/B pour les formulaires adaptatifs.

Pour tester l’intégration au site de référence, procédez comme suit pour configurer Target dans AEM :

1. Début à l’auteur de démarrer rapidement avec l’argument jvm `-Dabtesting.enabled=true` pour activer les tests A/B sur le serveur.

   **Remarque** : Si l’instance AEM s’exécute sur JBoss, qui est démarré en tant que service à partir de l’installation clé en main, ajoutez le  `-Dabtesting.enabled=true` paramètre dans l’entrée suivante du  `jboss\bin\standalone.conf.bat` fichier :

   `set "JAVA_OPTS=%JAVA_OPTS% -Dadobeidp.serverName=server1 -Dfile.encoding=utf8 -Djava.net.preferIPv4Stack=true -Dabtesting.enabled=true"`

1. Accédez à https://&quot;a0/>hostname *:&quot;a2/>port&lt;a3/&quot;/libs/cq/core/content/tools/cloudservices.html.***

1. Dans la section **[!UICONTROL Adobe Target]**, cliquez sur **[!UICONTROL Afficher les configurations]**. Vous pouvez voir la configuration de la Cible We.Finance disponible. Cliquez pour ouvrir la configuration. Dans la page de configuration, cliquez sur **[!UICONTROL Modifier]**. La boîte de dialogue **[!UICONTROL Modifier le composant]** pour la configuration s&#39;ouvre.

1. Indiquez vos code client, adresse électronique et mot de passe associés à votre compte Target. Sélectionnez le type d’API **[!UICONTROL REST]**.
1. Cliquez sur **[!UICONTROL Se connecter à Adobe Target]**. Une fois le compte de Cible configuré, cliquez sur **[!UICONTROL OK]**. Vous pouvez voir que la configuration empaquetée comporte une structure de Cible.

1. Accédez à https://&quot;a0/>hostname *:&quot;a2/>port&lt;a3/&quot;/system/console/configMgr.***

1. Cliquez sur **[!UICONTROL AEM Forms Target Configuration]**.
1. Sélectionnez une structure de Cible.
1. Dans le champ **[!UICONTROL Target URLs]**, indiquez l’URL vers AEM Forms. Par exemple : https://&quot;a0/>nom_hôte *:&quot;a2/>port&lt;a3/&quot;.***

1. Cliquez sur **[!UICONTROL Enregistrer]**.

Les cas d’utilisation de demandes de carte de crédit et de demandes de prêt immobilier montrent comment effectuer des tests A/B et comment présenter un rapport à des fins de démonstration. Pour les procédures pas à pas, voir [Présentation du site de référence We.Finance](/help/forms/using/finance-reference-site-walkthrough.md).

## Étape suivante {#next-step}

Vous êtes maintenant prêt à explorer le site de référence. Pour en savoir plus sur le processus et les étapes relatifs au site de référence, consultez la section :

* [Présentation du site de référence We.Finance](/help/forms/using/finance-reference-site-walkthrough.md) 
* [Présentation du site de référence We.Gov](/help/forms/using/gov-reference-site-walkthrough.md)

* [Présentation du site de référence de libre-service dédié aux employés](/help/forms/using/employee-self-service-reference-site.md)

