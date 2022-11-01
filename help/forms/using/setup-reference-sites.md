---
title: Installation et configuration des sites de référence d’AEM Forms
seo-title: Set up and configure AEM Forms reference sites
description: Les sites de référence AEM Forms décrivent comment utiliser AEM Forms pour implémenter un flux de bout en bout dans une entreprise.
seo-description: AEM Forms reference sites showcase how you can use AEM Forms to implement end-to-end workflow in an organization.
uuid: 087d58a1-d84e-49ac-a82d-4e7fc708f00f
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: introduction
discoiquuid: 2feb4a9c-57ad-4c6b-a572-0047bc409bbb
exl-id: 9c5d956c-06bc-4428-afcd-02b4f81b802f
source-git-commit: f8b19b6723d333e76fed111b9fde376b3bb13a1d
workflow-type: tm+mt
source-wordcount: '2911'
ht-degree: 44%

---

# Installation et configuration des sites de référence d’AEM Forms {#set-up-and-configure-aem-forms-reference-sites}

AEM Forms fournit une implémentation de site de référence pour démontrer la manière dont AEM Forms permet à des organisations gouvernementales et du secteur des services financiers de transformer leurs transactions complexes en expériences numériques simples et attrayantes, n’importe où, n’importe quand et sur n’importe quel périphérique.

Les sites de référence We.Finance et We.Gov utilisent des exemples de cas réels pour collaborer avec leurs clients existants et potentiels depuis leur tout premier contact, à la gestion des correspondances et transactions, de manière personnalisée et économique.

Les sites de référence vous permettent d’explorer et de voir en action les principales fonctionnalités suivantes d’AEM Forms.

* Expérience de création simplifiée : formulaires adaptatifs attrayants et réactifs et communications interactives.
* Communications interactives pour créer des communications client interactives, personnalisées et réactives qui s’adaptent au paramètre et à la mise en page de l’appareil.
* Intégration des données permettant de se connecter à des sources de données disparates afin de préremplir et d’envoyer des données de formulaire par le biais d’un modèle de données de formulaire.
* Processus des formulaires pour automatiser les processus d’entreprise.
* Fonctionnalités de traitement et de gestion des données utilisateur.
* Intégration à Acrobat Sign pour signer et envoyer en toute sécurité des formulaires adaptatifs.
* Intégration avec Adobe Target pour fournir des recommandations ciblées et effectuer les tests A/B, pour augmenter le retour sur investissement d’un formulaire.
* Intégration à Adobe Analytics pour mesurer les performances d’un formulaire ou d’une campagne et prendre des décisions éclairées.
* Amélioration de l’expérience de remplissage des formulaires.

Les sites de référence offrent des ressources réutilisables que vous pouvez utiliser comme modèles pour créer vos propres ressources.

* Intégration à Acrobat Sign pour signer et envoyer en toute sécurité des formulaires adaptatifs.

* Intégration à Acrobat Sign pour signer et envoyer en toute sécurité des formulaires adaptatifs.

## Conditions préalables et étapes et de la configuration des sites de référence {#prerequisites-and-steps-to-set-up-reference-sites}

Avant de configurer le site de référence, assurez-vous que vous disposez des éléments suivants :

* **AEM essentiels**

   AEM QuickStart, package de module complémentaire AEM Forms et packages de site de référence. Voir [Versions d’AEM Forms](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=fr) pour les détails des modules complémentaires et des sites de référence.

* **Un service SMTP** Vous pouvez utiliser n’importe quel service SMTP.

* **Compte de développeur Acrobat Sign et application API Acrobat Sign**

   Pour utiliser les fonctionnalités de signature numérique, un compte de développeur Acrobat Sign est requis. Voir [Acrobat Sign](https://acrobat.adobe.com/fr/fr/why-adobe/developer-form.html).

* Une instance en cours d’exécution de Microsoft Dynamics 365 à intégrer à AEM Forms. Pour exécuter le site de référence, vous importez les exemples de données dans l’instance Microsoft Dynamics afin de préremplir la communication interactive utilisée dans le site de référence.
* Une instance en cours d’exécution d’AEM 6.4 avec le module complémentaire Forms. Pour plus d’informations, reportez-vous à la section [Installation et configuration d’AEM Forms](installing-configuring-aem-forms-osgi.md).

Effectuez les étapes suivantes dans l’ordre recommandé pour installer et configurer les sites de référence.

<table> 
 <tbody> 
  <tr> 
   <th><strong>Étape</strong></th> 
   <th><strong>Configuration de</strong></th> 
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
   <td>Activez HTTP over SSL pour les communications sécurisées avec Acrobat Sign.</td> 
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
   <td>Utilisé pour remplacer les caractères $, { et } qui sont bloqués par la sécurité xss.</td> 
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
   <td>Présentation de la demande de carte de crédit, de la demande de prêt immobilier et de la demande d’assurance habitation</td> 
  </tr> 
  <tr> 
   <td><a href="/help/forms/using/setup-reference-sites.md#configure-oauth-cloud-service-for-microsoft-dynamics">Configurer le service cloud OAuth pour Microsoft Dynamics</a></td> 
   <td>Auteur et publication</td> 
   <td>Configurez le service cloud OAuth dans AEM Forms pour activer la communication entre AEM Forms et Microsoft Dynamics. </td> 
  </tr> 
  <tr> 
   <td><a href="#scheduler">Configuration du planificateur Acrobat Sign</a></td> 
   <td>Auteur et publication<br /> </td> 
   <td>Modifiez la configuration du planificateur pour vérifier l’état toutes les deux minutes.</td> 
  </tr> 
  <tr> 
   <td><a href="#sign-service">Configuration du Cloud Service Acrobat Sign du site de référence</a></td> 
   <td>Auteur et publication<br /> </td> 
   <td>Une configuration qui comprend des packages de sites de référence et qui doit être reconfigurée avec des informations d’identification valides.</td> 
  </tr> 
  <tr> 
   <td><a href="#anonymous">Configurer le service de configuration commun aux formulaires pour les utilisateurs anonymes</a></td> 
   <td>Publication</td> 
   <td>La configuration permet l’envoi, la signature et la génération du document d’enregistrement pour les utilisateurs anonymes.</td> 
  </tr> 
  <tr> 
   <td><a href="#fdm">Modifier le fichier Swagger du service Rest pour le modèle de données du formulaire</a></td> 
   <td>Auteur et publication<br /> </td> 
   <td>Modifiez le service pour votre environnement.</td> 
  </tr> 
 </tbody> 
</table>

## Installer et configurer AEM Forms {#install-and-configure-aem-forms}

Installez et déployez AEM Forms comme décrit dans la section [Installation et configuration d’AEM Forms sur OSGi](/help/forms/using/installing-configuring-aem-forms-osgi.md).

>[!NOTE]
>
>Configurez les agents de réplication et d’inversion de la réplication s’il existe plusieurs instances de publication ou si les instances d’auteur et de publication se trouvent sur des ordinateurs différents.

## Configurer SSL {#ssl}

La configuration SSL est requise pour communiquer avec les serveurs Acrobat Sign. Pour obtenir des instructions détaillées, voir [Activation de HTTP Over SSL](/help/sites-administering/ssl-by-default.md).

>[!CAUTION]
>
>Ne configurez pas l’activation forcée du protocole SSL `/etc/map` dossier.

## Configuration de Day CQ Link Externalizer (Externalisateur du lien vers Day CQ) {#externalizer}

Dans AEM, la variable **Externalizer** est un service OSGI qui vous permet de transformer par programmation un chemin d’accès à une ressource (par exemple, /path/to/my/page) en URL externe et absolue (par exemple, https://www.mycompany.com/path/to/my/page) en ajoutant un chemin d’accès en préfixe avec un DNS préconfiguré. Voir [Externalisation des URL](/help/sites-developing/externalizer.md).

>[!CAUTION]
>
>N’externalisez pas vers l’URL HTTPS si vous utilisez certificat autosigné pour SSL.
>
>En outre, vous devez utiliser localhost plutôt que hostname pour le serveur local.

Effectuez les étapes suivantes sur les instances d’auteur et de publication :

1. Accédez à Configuration OSGi à l’adresse https://&lt;*hostname>*:&lt;*port>*/system/console/configMgr
1. Rechercher et appuyer sur **[!UICONTROL Externalisateur de lien Day CQ]** configuration.

   La boîte de dialogue Day CQ Link Externalizer s’ouvre à des fins d’édition de la configuration.

1. Dans la boîte de dialogue Day CQ Link Externalizer, dans le champ Domaines :

   * Sur l’instance de rédaction, spécifiez une URL de publication accessible depuis n’importe quel système externe. Par exemple, un nom d’hôte ou un serveur Web de publication.
   * Sur l’instance de publication, indiquez les URL de rédaction et de publication.

1. Sur les instances d’auteur et de publication, assurez-vous que l’URL du serveur local est indiquée dans le champ des domaines.
1. Appuyez sur **[!UICONTROL Enregistrer]**. Patientez un moment le temps que tous les services redémarrent.

## Configuration du service de messagerie Day CQ {#cqmail}

Une mise en œuvre de site de référence nécessite que les courriers électroniques soient envoyés aux exemples d’utilisateurs lorsqu’ils remplissent les formulaires et les envoient. La configuration du service de messagerie Day CQ vous permet de fournir des détails de serveur SMTP pour envoyer des courriers électroniques automatisés aux clients. Voir [Configuration des notifications par courrier électronique](/help/sites-administering/notification.md).

Procédez comme suit pour configurer le service de messagerie sur l’instance de publication :

1. Accédez à Configuration OSGi à l’adresse https://&lt;*hostname>*:&lt;*port>*/system/console/configMgr
1. Rechercher et appuyer sur **[!UICONTROL Service de messagerie Day CQ]** pour l’ouvrir en vue de la configuration.
1. Indiquez les valeurs hostname et de port du serveur SMTP.
1. Appuyez sur **[!UICONTROL Enregistrer]**.

>[!NOTE]
>
>Vous pouvez utiliser votre service SMTP d’entreprise ou des services publics comme Gmail. Pour la configuration du service SMTP, voir la documentation correspondante.

## Remplacement de la configuration XSS par défaut {#xss}

Les modèles de courrier électronique pour le site de référence We.Finance contiennent des liens personnalisés dans les courriers électroniques. Ces liens possèdent un espace réservé tel que `${placeholder}`. Ces espaces réservés sont remplacés par des valeurs réelles avant l’envoi des courriers électroniques. La configuration de protection XSS par défaut pour AEM n’autorise pas les accolades (**{ }**) dans l’URL d’un contenu HTML. Cependant, vous pouvez remplacer la configuration par défaut en procédant comme suit sur l’instance de publication :

1. Copiez `/libs/cq/xssprotection/config.xml` dans `/apps/cq/xssprotection/config.xml`.
1. Ouvrez `/apps/cq/xssprotection/config.xml`.
1. Dans le `common-regexps` , modifiez la variable `onsiteURL` et enregistrez le fichier.

   `<regexp name="onsiteURL" value="([\p{L}\p{N}\\\.\#@\$\{\}%\+&;\-_~,\?=/!\*\(\)]*|\#(\w)+)"/>`

>[!NOTE]
>
>Les accolades (**{}**) sont incluses en tant que caractères acceptés dans l’URL du contenu HTML.

Après la configuration du serveur SMTP, essayez de remplir un formulaire à l’aide de Sarah Rose et de l’enregistrer en tant que brouillon. Lorsque vous enregistrez en tant que brouillon, vous obtenez une option permettant de recevoir le brouillon par courrier électronique. Lorsque vous appuyez sur le bouton **Envoyer un courrier électronique**, si vous recevez un courrier électronique contenant un lien vers le brouillon de la demande, votre configuration de courrier électronique est correcte. Assurez-vous que vous vous connectez en utilisant les identifiants de Sarah pour afficher le brouillon.

## Configurer les paramètres AEM DS {#aemds}

AEM les paramètres du service DS sont requis sur l’instance de publication pour les communications par e-mail dans les cas d’utilisation du site de référence. Pour obtenir des instructions détaillées sur la configuration du service DS AEM sur l’instance de publication, voir [Configuration des paramètres AEM DS](/help/forms/using/configuring-the-processing-server-url-.md).

Pour les sites de référence AEM Forms, dans le service de paramètres d’AEM, spécifiez l’URL du serveur de publication au lieu de l’URL du serveur de traitement.

>[!CAUTION]
>
>Ne pas placer `/lc` dans l’URL du serveur de traitement si vous la configurez pour AEM Forms OSGi.

## Déployer les packages des sites de référence {#refsite}

Installez les packages de sites de référence suivants à l’aide de la Distribution de logiciels.

* [AEM-FORMS-6.4-FSI-REF-SITE](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/fd/AEM-FORMS-6.4-FSI-REF-SITE)
* [AEM-FORMS-6.4-GOV-REF-SITE](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/fd/AEM-FORMS-6.4-GOV-REF-SITE)

Pour en savoir plus sur l’utilisation des packages, voir [Utilisation de modules](/help/sites-administering/package-manager.md).

Une fois que vous avez installé les packages et avez lancé les instances de rédaction et de publication, consultez les URL suivantes dans votre navigateur :

* `https://[server]:[port]/wegov`
* `https://[server]:[port]/wefinance`

Si votre installation est terminée, vous pouvez accéder aux pages d’accueil des sites de référence We.Gov et We.Finance.

## (Facultatif) Importation de données d’exemple dans Microsoft Dynamics {#optional-import-sample-data-into-microsoft-dynamics}

Les sites de référence de la demande de prêt immobilier et de l’assurance automobile sont configurés pour utiliser les enregistrements de Microsoft Dynamics. Le package de site de référence installe une entité personnalisée et des exemples d’enregistrements que vous pouvez importer dans Microsoft Dynamics pour exécuter le site de référence. Effectuez les étapes suivantes pour migrer et configurer les exemples de données :

Pour importer l’entité personnalisée d’une demande d’assurance automobile :

1. Téléchargez la **WeFinanceAutoInsurance_1_0.zip** package de solution à partir de `https://[server]:[port]/content/aemforms-refsite-collaterals/we-finance/auto-insurance/ms-dynamics/WeFinanceAutoInsurance_1_0.zip` sur votre instance d’auteur AEM.
1. Dans votre instance Microsoft Dynamics, accédez à **[!UICONTROL Solutions]** dans le **[!UICONTROL Paramètres]** et cliquez sur **[!UICONTROL Importer]**. Sélectionnez le package et importez-le.

Pour importer l’entité personnalisée d’une demande d’assurance automobile :

1. Téléchargez la **AEMFormsFSIRefsite_1_0.zip** package à partir de https://[author]:[port]/content/aemforms-refsite-collaterals/we-finance/home-mortgage/ms-dynamics/AEMFormsFSIRefsite_1_0.zip. Sélectionnez le package et importez-le.

1. Dans votre instance Microsoft Dynamics, accédez à **[!UICONTROL Solutions]** dans le **[!UICONTROL Paramètres]** et cliquez sur **[!UICONTROL Importer]**. Sélectionnez le package et importez-le.

Pour importer les enregistrements de client et de police d’assurance :

1. Téléchargez la **We.Finance Customers.csv, We.Finance Auto Insurance Renewals.csv**, et **prêt immobilier** fichiers de données des emplacements suivants sur votre instance d’auteur AEM :

   * `https://[server]:[port/content/aemforms-refsite-collaterals/we-finance/auto-insurance/ms-dynamics/We.Finance Customers.csv`
   * `https://[server]:[port/content/aemforms-refsite-collaterals/we-finance/auto-insurance/ms-dynamics/We.Finance Auto Insurance Renewals.csv`
   * `https://[server]:[port]/content/aemforms-refsite-collaterals/we-finance/home-mortgage/ms-dynamics/Sarah%20Rose%20Contact.csv`

1. Dans votre instance Microsoft Dynamics, procédez comme suit :

   * Accédez à **[!UICONTROL Ventes > Clients We.Finance]** et cliquez sur **[!UICONTROL Importer]**.
   * Accédez à **[!UICONTROL Ventes > Assurance automobile We.Finance]** et cliquez sur **[!UICONTROL Importer]**.
   * Accédez à **[!UICONTROL Ventes > Prêt immobilier We.Finance]**  et cliquez sur **[!UICONTROL Importer]**.

## Configurer le service cloud OAuth pour Microsoft Dynamics {#configure-oauth-cloud-service-for-microsoft-dynamics}

Configurez le service cloud OAuth dans AEM Forms pour activer la communication entre AEM Forms et Microsoft Dynamics. Effectuez les étapes suivantes pour configurer le Cloud Service OAuth sur les instances de création et de publication d’AEM :

1. Sur AEM instance d’auteur, accédez à **[!UICONTROL Outils > Cloud Services > Sources de données > globales]**. Appuyer **[!UICONTROL Intégration de Refsite Dynamics]** icône et appuyez sur **[!UICONTROL Propriétés]**.
1. Accédez au compte Microsoft Azure Active Directory. Ajoutez l’URL de configuration du service cloud copiée dans le paramètre **[!UICONTROL URL de réponse]** pour votre application enregistrée. Enregistrez la configuration.
1. Dans l’onglet Paramètres d’authentification, spécifiez **[!UICONTROL Racine du service]**, **[!UICONTROL ID client]**, **[!UICONTROL Secret du client]**, et **[!UICONTROL URL de ressource]** pour votre instance Microsoft Dynamics. Cliquez sur **[!UICONTROL Connexion à OAuth]** qui redirige vers la page de connexion de Microsoft Dynamics.
1. Entrez vos informations de connexion. Une fois connecté, vous êtes redirigé vers la page de configuration du service cloud AEM Forms. Cliquez sur **[!UICONTROL Enregistrer et fermer]**. La configuration du service cloud est enregistrée.
1. Accédez à **[!UICONTROL Forms > Intégrations de données > We.Finance]**. Sélectionnez Assurance automobile (Dynamics) et cliquez sur Modifier. Les entités Microsoft Dynamics sont répertoriées sous l’onglet Sources de données . Patientez jusqu’à ce que toutes les entités soient récupérées à partir de Microsoft Dynamics et répertoriées sous l’onglet Sources de données .
1. Sélectionnez la **[!UICONTROL Entité AutoInsuranceRenewal]** et cliquez sur **[!UICONTROL Objet de modèle de test]**. Dans la section de demande d’entrée, indiquez la valeur de l’ID de client comme &quot;900001&quot;, puis cliquez sur **[!UICONTROL Test]**. La section Sortie affiche les enregistrements récupérés de Microsoft Dynamics pour l’ID de client 900001.
1. Dans la section de demande d’entrée, indiquez la valeur de l’ID de client comme &quot;900001&quot;, puis cliquez sur **[!UICONTROL Test]**. La section Sortie affiche les enregistrements récupérés de Microsoft Dynamics pour l’ID de client 900001.
1. Répétez les étapes 1 à 6 sur l’instance de publication.

## Configuration du planificateur Acrobat Sign {#scheduler}

Effectuez les étapes suivantes sur les instances d’auteur et de publication :

1. Accédez à AEM console de configuration Web à l’adresse `https://[server]:[host]/system/console/configMgr`.
1. Rechercher et appuyer sur **[!UICONTROL Service de configuration Acrobat Sign]** pour l’ouvrir en vue de la configuration.
1. Configurer **[!UICONTROL Expression du planificateur de mise à jour d’état]** as **0 0/2 &amp;ast; &amp;ast; &amp;ast; ?**.

   >[!NOTE]
   >
   >La configuration du planificateur ci-dessus vérifie l’état du service Acrobat Sign toutes les deux minutes.

1. Appuyez sur **[!UICONTROL Enregistrer]**.

## Configuration du service cloud Acrobat Sign du site de référence {#sign-service}

Effectuez les étapes suivantes sur les instances d’auteur et de publication :

1. Accédez à **[!UICONTROL Outils > Cloud Services > Acrobat Sign > global]**. Sélectionner **[!UICONTROL AEM Forms Reference Site Sign]** et appuyez sur **[!UICONTROL Propriétés]**.

   >[!CAUTION]
   >
   >Assurez-vous que le fichier https://[hôte]:[ssl_port]/mnt/overlay/adobesign/cloudservices/adobesign/properties.html L’URL est ajoutée à la liste des URL de redirection de la configuration OAuth de l’application API Acrobat Sign.

1. Indiquez l’identifiant du client et le secret de la configuration OAuth de l’application Acrobat Sign.
1. (Facultatif) Sélectionnez le **[!UICONTROL Activation d’Acrobat Sign pour les pièces jointes également]** et appuyez sur **[!UICONTROL Connexion à Acrobat Sign]**. Il ajoute les fichiers joints à un formulaire adaptatif au document Acrobat Sign correspondant envoyé pour signature.
1. Appuyer **[!UICONTROL Connexion à Acrobat Sign]** et connectez-vous avec vos informations d’identification Acrobat Sign.

## Configurer le service de configuration commun aux formulaires {#anonymous}

Effectuez les étapes suivantes sur l’instance de publication pour autoriser l’accès des utilisateurs anonymes :

1. Accédez à AEM console de configuration Web à l’adresse `https://[server]:[port]/system/console/configMgr`.
1. Rechercher et appuyer sur **[!UICONTROL Service de configuration commun à Forms]** pour l’ouvrir en vue de la configuration.
1. Configurez la variable **[!UICONTROL Autoriser]** champ pour **[!UICONTROL Tous les utilisateurs]**.
1. Appuyez sur **[!UICONTROL Enregistrer]**.

## Modifier le service Rest pour le modèle de données de formulaire {#fdm}

Effectuez les étapes suivantes sur les instances d’auteur et de publication :

1. Accédez à CRXDE à l’adresse `https://[server]:[port]/crx/de/index.jsp`.
1. Accédez à **/conf/global/settings/cloudconfigs/fdm/roi-rest/jcr:content/swaggerFile** et ouvrez le fichier swagger.
1. Mettez à jour les paramètres d’hôte et de port en fonction de votre environnement.
1. Enregistrez les paramètres.
1. (**Instance de création uniquement**) Accédez à **[!UICONTROL Outils]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Sources de données]** > **[!UICONTROL global]**. Sélectionner **[!UICONTROL roi-rest]** et appuyez sur **[!UICONTROL Propriétés]**. Appuyer **[!UICONTROL Paramètres d’authentification]** et défini **[!UICONTROL Type d’authentification]** to **[!UICONTROL Authentification de base]**. Spécifier `admin`/ `admin`comme nom d’utilisateur/mot de passe pour accéder au service. Appuyez sur **[!UICONTROL Enregistrer et fermer]**.

## Intégration à Marketing Cloud {#integrate-with-marketing-cloud}

Vous pouvez intégrer AEM Forms à Adobe Analytics et Adobe Target. Bien qu’Adobe Analytics vous aide à générer des rapports et à analyser les performances des formulaires adaptatifs, Adobe Target vous aide à fournir des expériences personnalisées et à effectuer des tests A/B pour les formulaires adaptatifs.

Procédez comme suit pour configurer Adobe Analytics et Adobe Target dans AEM Forms.

### Configuration d’Adobe Analytics {#configure-adobe-analytics}

L’intégration d’Adobe Analytics à AEM Forms vous permet de surveiller et d’analyser la manière dont vos clients interagissent avec vos formulaires et documents. Il vous aide à identifier et à résoudre les zones à problème et à agir pour augmenter le taux de conversion.

Pour tester cette fonctionnalité sur le site de référence, configurez votre compte Analytics tel que décrit dans [Configuration des analyses et des rapports](/help/forms/using/configure-analytics-forms-documents.md).

Pour générer un rapport, les données sources sont regroupées avec les sites de référence. Avant d’utiliser les données sources, procédez comme suit :

1. Assurez-vous que les configurations d’analyse We.Finance et We.Gov sont disponibles dans les services cloud AEM. Vous pouvez trouver les services cloud de l’une des manières suivantes :

   * Accédez à **[!UICONTROL Outils > Cloud Services > Cloud Services hérités]** ou accédez à https://&lt;host>:&lt;port>/libs/cq/core/content/tools/cloudservices.html.
   * Dans le **[!UICONTROL Cloud Services]** page, sous **[!UICONTROL Adobe Analytics]** , cliquez sur `Show Configurations`. Vous pouvez voir les configurations We.Finance et We.Gov disponibles. Cliquez pour ouvrir la configuration. Dans la page de configuration, cliquez sur **[!UICONTROL Modifier]**. Indiquez un nom d’utilisateur, une société valide, un secret partagé (mot de passe) et un centre de données, puis cliquez sur **[!UICONTROL Connexion à Analytics]**. Une fois la boîte de dialogue Connexion réussie, cliquez sur **[!UICONTROL OK]** dans la boîte de dialogue de configuration. Configurez la structure sous la configuration Analytics comme décrit dans la section [Configuration des analyses et des rapports](/help/forms/using/configure-analytics-forms-documents.md).

1. Accédez à https://&lt;*hôte*>:&lt;*port*>/system/console/configMgr et procédez comme suit :

   * Dans le **[!UICONTROL Configuration de la console web]** page, rechercher et cliquer **[!UICONTROL Configuration d’AEM Forms Analytics]**.
   * Dans le **[!UICONTROL Structure de SiteCatalyst]** dans le champ de la boîte de dialogue Configuration d’AEM Forms Analytics, sélectionnez we-finance (we-finance) ou we-gov (we-gov).
   * Cliquez sur **[!UICONTROL Enregistrer]** et laissez la page s’actualiser.

1. Accédez au gestionnaire de formulaires à l’adresse https://&lt;host>:&lt;port>/aem/forms et procédez comme suit :

   * Ouvrez le dossier We.Finance ou We.Gov, puis sélectionnez le formulaire pour lequel vous souhaitez afficher le rapport.
   * Dans la barre d’outils des actions, cliquez sur Rapport d’analyse. Une fois que vous avez activé les analyses pour le formulaire, cliquez sur Rapport d’analyse. Vous constatez qu’un rapport vide a été généré. Une fois qu’un rapport vierge a été généré, vous devez fournir les données sources fournies avec le package refsite pour générer le rapport d’analyse à des fins de démonstration.

   Les sites de référence fournissent des rapports d’analyse avec des données sources pour les cas d’utilisation de cartes de crédit, de prêts hypothécaires et d’allocations familiales. Pour la configuration des données sources, voir [Présentation du site de référence We.Finance](/help/forms/using/finance-reference-site-walkthrough.md) et [Présentation du site de référence We.Gov](/help/forms/using/gov-reference-site-walkthrough.md).

### Configuration de Target {#configure-target}

Le site de référence bénéficie de l’intégration d’Adobe Target à AEM Forms, ce qui vous permet d’incorporer du contenu ciblé et personnalisé dans des documents adaptatifs. Ce module permet également la création de tests A/B pour les formulaires adaptatifs.

Pour tester l’intégration au site de référence, procédez comme suit pour configurer Target dans AEM :

1. Démarrez le démarrage rapide de l’auteur avec l’argument jvm. `-Dabtesting.enabled=true` pour activer les tests A/B sur le serveur.

   **Remarque**: Si l’instance d’AEM est en cours d’exécution sur JBoss, qui est démarré en tant que service à partir de l’installation clé en main, ajoutez le `-Dabtesting.enabled=true` dans l’entrée suivante du `jboss\bin\standalone.conf.bat` fichier, :

   `set "JAVA_OPTS=%JAVA_OPTS% -Dadobeidp.serverName=server1 -Dfile.encoding=utf8 -Djava.net.preferIPv4Stack=true -Dabtesting.enabled=true"`

1. Accédez à https://&lt;*hostname*>:&lt;*port*>/libs/cq/core/content/tools/cloudservices.html.

1. Dans le **[!UICONTROL Adobe Target]** , cliquez sur **[!UICONTROL Afficher les configurations]**. Vous pouvez voir la configuration de Target We.Finance disponible. Cliquez pour ouvrir la configuration. Dans la page de configuration, cliquez sur **[!UICONTROL Modifier]**. Le **[!UICONTROL Modifier le composant]** pour la configuration s’ouvre.

1. Indiquez vos code client, adresse électronique et mot de passe associés à votre compte Target. Sélectionnez le type d’API comme **[!UICONTROL REST]**.
1. Cliquez sur **[!UICONTROL Se connecter à Adobe Target]**. Une fois le compte Target configuré, cliquez sur **[!UICONTROL OK]**. Vous pouvez voir que la configuration empaquetée comporte une structure Target.

1. Rendez-vous sur https://&lt;*nom de lʼhôte*>:&lt;*port*>/system/console/configMgr.

1. Cliquez sur **[!UICONTROL AEM Forms Target Configuration]**.
1. Sélectionnez une structure Target.
1. Dans le champ **[!UICONTROL Target URLs]**, indiquez l’URL vers AEM Forms. Par exemple : https://&lt;*hostname*>:&lt;*port*>.

1. Cliquez sur **[!UICONTROL Enregistrer]**.

Les cas pratiques de demande de carte de crédit et de demande de prêt immobilier montrent comment effectuer des tests A/B et présenter un rapport à des fins de démonstration. Pour des instructions, voir [Présentation du site de référence We.Finance](/help/forms/using/finance-reference-site-walkthrough.md).

## Étape suivante {#next-step}

Vous êtes maintenant prêt à explorer le site de référence Pour en savoir plus sur le processus et les étapes relatifs au site de référence, consultez la section :

* [Présentation du site de référence We.Finance](/help/forms/using/finance-reference-site-walkthrough.md)
* [Présentation du site de référence We.Gov](/help/forms/using/gov-reference-site-walkthrough.md)

* [Présentation du site de référence de libre-service dédié aux employés](/help/forms/using/employee-self-service-reference-site.md)
