---
title: Présentation du site de référence We.Finance
seo-title: We.Finance reference site walkthrough
description: Explorez le site de référence We.Finance et comprenez comment il a été mis en oeuvre. We.Finance est un exemple de mise en oeuvre qui présente les fonctionnalités clés d’AEM Forms.
seo-description: Explore the We.Finance reference site and understand how it has been implemented. We.Finance is a sample implementation to showcase key features and functionalities of AEM Forms.
uuid: cbcedba4-6151-475d-b6c2-9859e0382768
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: introduction
discoiquuid: 0c1b6ad7-9d25-41dc-b1fe-a4cb9366c259
exl-id: 17e8c644-ee17-496c-a781-a295a4796cb9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '9237'
ht-degree: 5%

---

# Présentation du site de référence We.Finance {#we-finance-reference-site-walkthrough}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

## Prérequis {#pre-requisites}

Configurez les sites de référence comme décrit dans la section [Installation et configuration des sites de référence AEM Forms](/help/forms/using/setup-reference-sites.md).

## Scénarios du site de référence We.Finance {#we-finance-reference-site-scenarios}

We.Finance est une organisation de pointe dans le domaine des services financiers qui propose des solutions financières complètes et personnalisées pour répondre aux besoins de divers profils clients. Ils proposent des cartes de crédit, des prêts immobiliers et des services d&#39;assurance habitation.

Leur objectif est d’atteindre les clients existants et potentiels sur leur appareil préféré, d’expliquer les avantages de leurs services et de les aider à s’inscrire à leurs services. En outre, ils cherchent à lancer plus de produits financiers comme des cartes complémentaires que les clients peuvent trouver intéressants.

Lisez la suite pour obtenir des instructions détaillées sur les cas d’utilisation de We.Finance et comprendre comment AEM Forms aide les organisations financières à atteindre leurs objectifs. Les étapes suivantes sont décrites :

* [Présentation de la demande de carte de crédit](#credit-card-application-walkthrough)
* [Présentation de la demande de prêt immobilier](#home-mortgage-application-walkthrough)
* [Présentation de la demande de prêt immobilier avec Microsoft Dynamics](#home-mortgage-application-walkthrough-with-microsoft-dynamics)
* [Présentation de la demande d’assurance habitation](#home-insurance-application-walkthrough)
* [Présentation de la gestion de la richesse](#wealthmanagementwalkthrough)
* [Présentation de la demande d’assurance automobile](#autoinsuranceapplicationwalkthrough)

## Présentation de la demande de carte de crédit {#credit-card-application-walkthrough}

Le scénario de demande de carte de crédit We.Finance comprend les personnages suivants :

* Sarah Rose, une cliente de We.Finance
* Gloria Rios, chef de la Carte de crédit et des Prêts immobiliers, We.Finance

L’infographie suivante illustre le processus détaillé de la demande de carte de crédit.

![workflow_aem](assets/workflow_aem.png)

Examinons le scénario du site de référence en détail pour comprendre comment AEM Forms aide We.Finance à atteindre ses objectifs.

### Sarah reçoit une newsletter de We.Finance et demande une carte de crédit {#sarah-receives-a-newsletter-from-we-finance-and-applies-for-a-credit-card}

Sarah Rose est déjà cliente de We.Finance. Elle reçoit une newsletter de We.Finance sur les nouvelles cartes de crédit proposées. Elle trouve les offres excitantes et décide de faire une demande de carte de crédit. Elle clique sur le bouton Demander ma carte dans la newsletter, ce qui l’amène à la demande de carte de crédit sur le portail We.Finance.

![marketing-email](assets/marketing-email.png)

#### Fonctionnement {#how-it-works}

La newsletter envoyée à Sarah est une mise en oeuvre personnalisée qui déclenche un courrier électronique vers l’ID de courrier électronique spécifié. Le bouton Demander maintenant dans le courrier électronique est lié à la demande de carte de crédit, qui est un formulaire adaptatif sur une instance de publication.

#### Démonstration {#see-it-yourself}

Ouvrez l’URL suivante sur l’instance de publication pour déclencher un courrier électronique de newsletter. Assurez-vous que vous remplacez `[emailID]` avec un compte de messagerie valide pour recevoir la newsletter. Ouvrez la newsletter, puis cliquez sur **[!UICONTROL Appliquer maintenant]** pour accéder à la demande de carte de crédit.

`https://[publishServer]:[publsihPort]/content/campaigns/we-finance/start.html?app=cc&email=[emailID]&givenName=Sarah&familyName=Rose`

### Sarah trouve l’offre intéressante et choisit de la présenter {#sarah-finds-the-offer-interesting-and-chooses-to-apply}

Sarah décide de demander la carte de crédit et appuie **[!UICONTROL Appliquer maintenant]** sur l’email. Sarah est alors redirigée vers la demande de carte de crédit sur le portail We.Finance. Le formulaire de demande est organisé en sections selon une mise en page Carte.

Sarah sélectionne une carte de crédit parmi les options disponibles et clique **[!UICONTROL Continuer]**.

![cc-application-form-desktop](assets/cc-application-form-desktop.png)

Sur la page Informations personnelles, lorsque Sarah fournit son numéro de sécurité sociale, elle reçoit une invite lui demandant de se connecter à l’aide de ses informations d’identification.

![login-ssn](assets/login-ssn.png)

Sarah est déjà cliente chez We.Finance. Elle se connecte à l’aide de ses informations d’identification de compte We.Finance et ses informations personnelles sont automatiquement renseignées dans le formulaire. Sarah continue à remplir le formulaire de demande et c’est là qu’un rappel apparaît pour une réunion à laquelle elle doit participer. Elle clique **[!UICONTROL Enregistrer ma progression]** sur le formulaire de demande. Elle enregistre toutes les informations que Sarah a déjà fournies et une boîte de dialogue s’affiche pour confirmer si elle souhaite recevoir un courrier électronique contenant un lien vers son brouillon de demande pour la terminer ultérieurement.

Sarah clique **[!UICONTROL Envoyer un courrier]**. Elle reçoit un courrier électronique contenant un lien pour reprendre sa demande de carte de crédit.

![resume](assets/resume.png)


<!--Theses sections used to be an accordion until converted to straight Markdown. When accordions are enabled, revert-->

### Sarah accède à la demande de carte de crédit à partir de son appareil mobile {#a-sarah-access}

Si Sarah accède à la demande de carte de crédit à partir de son appareil mobile, la demande réactive s’ouvre dans une vue optimisée pour les appareils mobiles. Dans cette vue, le formulaire de demande est présenté sous la forme d’une section à la fois. Cela permet à Sarah d’afficher et de fournir des informations progressivement lorsqu’elle navigue dans la demande.

![form-on-mobile](assets/form-on-mobile.png)

### Fonctionnement {#a-how-it-works}

Le **[!UICONTROL Appliquer maintenant]** ce bouton redirige Sarah vers la demande de carte de crédit. La demande est un formulaire adaptatif, que vous pouvez consulter dans les instances de création à l’adresse `https://[host]:[Port]/editor.html/content/forms/af/we-finance/cc-app.html`.

Voici quelques-unes des fonctions clés que vous pouvez examiner dans le formulaire adaptatif :

* Il est basé sur un schéma XSD.
* Il est créé à l’aide du thème A We.Finance pour le style et du modèle We.Finance pour la mise en page. En outre, elle utilise Disposition sans titres de panneau dans la disposition d’en-tête du formulaire pour la navigation mobile. Elle affiche une disposition mobile progressive lorsqu’elle est ouverte à partir d’un appareil mobile. Vous pouvez consulter le modèle à l’adresse `https://[host]:[Port]/libs/wcm/core/content/sites/templates.html/conf/we-finance` et le thème au `https://[host]:[Port]/editor.html/content/dam/formsanddocuments-themes/we-finance/we-finance-theme-a/jcr:content`.
* Il comprend des règles de formulaire adaptatif pour appeler les services de modèle de données de formulaire afin de préremplir les détails de l’utilisateur connecté. Il appelle également les services pour préremplir les informations par numéro de sécurité sociale ou adresse électronique fournie dans le formulaire. Vous pouvez consulter les modèles de données de formulaire et leurs services à l’adresse `https://[host]:[Port]/aem/forms.html/content/dam/formsanddocuments-fdm`.
* Il utilise divers composants de formulaire adaptatif pour capturer des entrées et s’adapte aux réponses des utilisateurs. Il utilise également des composants tels que Email qui prennent en charge les types d’entrée HTML5.
* Il utilise le composant Étape de signature pour afficher le formulaire rempli et permet la signature électronique sur le formulaire.
* Le bouton Enregistrer ma progression génère un identifiant unique pour l’utilisateur et enregistre la demande partiellement remplie en tant que brouillon dans un noeud du référentiel AEM. Il affiche également une autorisation de recherche de boîte de dialogue pour envoyer un courrier électronique contenant un lien vers le noeud contenant le brouillon de la demande. Le bouton Envoyer un courrier de la boîte de dialogue de confirmation déclenche un courrier électronique contenant un lien vers le noeud contenant le brouillon.
* Elle utilise l’action d’envoi Appeler le processus AEM pour déclencher le processus d’approbation de carte de crédit. Vous pouvez consulter le workflow utilisé dans ce formulaire à l’adresse `https://[host]:[Port]/editor.html/conf/global/settings/workflow/models/we-finance-credit-card-workflow.html`

Il est recommandé de consulter le formulaire pour comprendre le schéma, les composants, les règles, les modèles de données de formulaire, le processus des formulaires et l’action d’envoi utilisés pour créer le formulaire.

Consultez également la documentation suivante pour plus d’informations sur les fonctionnalités utilisées dans le formulaire adaptatif de demande de carte de crédit :

* [Présentation de la création de formulaires adaptatifs](/help/forms/using/introduction-forms-authoring.md)
* [Création de formulaires adaptatifs à l’aide d’un schéma XML](/help/forms/using/adaptive-form-xml-schema-form-model.md)
* [Éditeur de règles](/help/forms/using/rule-editor.md)
* [Thèmes](/help/forms/using/themes.md)
* [Intégration de données ](/help/forms/using/data-integration.md)
* [Utilisation d’Acrobat Sign dans les formulaires adaptatifs](/help/forms/using/working-with-adobe-sign.md)
* [Processus basé sur l’utilisation de Forms sur OSGi](/help/forms/using/aem-forms-workflow.md)

### Démonstration {#a-see-it-yourself}

Lorsque vous êtes connecté en tant que Sarah Rose, cliquez sur le **[!UICONTROL Appliquer maintenant]** sur la demande de carte de crédit. Renseignez certains détails, explorez divers composants de formulaire adaptatif, puis cliquez sur **[!UICONTROL Enregistrer ma progression]** pour recevoir un courrier électronique contenant un **[!UICONTROL Reprendre]** qui renvoie au brouillon de la demande. Assurez-vous de spécifier votre ID de courrier électronique dans le formulaire de demande pour recevoir le courrier électronique.

Consultez le thème We.Finance disponible à l’adresse :

`https://<host>:<AuthorPort>/editor.html/content/dam/formsanddocuments-themes/we-Finance/we-Finance-Theme-A/jcr:content`

Vous pouvez consulter le modèle We.Finance à l’adresse :

`https://<host>:<AuthorPort>/editor.html/conf/we-finance/settings/wcm/templates/we-finance-template/structure.html`

### Sarah reprend et envoie la demande {#sarah-resumes-and-submits-the-application}

Sarah revient plus tard et trouve un courriel de We.Finance. Elle clique sur le bouton **[!UICONTROL Reprendre]** dans le courrier électronique qui l’amène à son brouillon de demande de carte de crédit. Les informations qu’elle a renseignées précédemment sont préremplies. Elle remplit le formulaire de demande restant, signe la demande et l’envoie.

![resume-1](assets/resume-1.png)

Elle peut également accéder à son brouillon de demande sous **[!UICONTROL Mon Forms]** sur la page d’accueil de We.Finance.

![portal-brouillons](assets/portal-drafts.png)

#### Fonctionnement {#how-it-works-1}

Le bouton Reprendre du courrier électronique redirige Sarah vers le noeud contenant son brouillon de demande.

#### Démonstration {#see-it-yourself-1}

Vous devez avoir reçu un courrier électronique contenant un lien vers le brouillon de la demande sur votre ID de courrier électronique que vous avez spécifié lors du remplissage du formulaire de demande. Allez-y, renseignez les sections restantes de la demande et envoyez-la.

### We.Finance reçoit et approuve la demande {#approving-the-application}

We.Finance reçoit la demande de carte de crédit envoyée par Sarah. Une tâche est assignée à Gloria Rios. Elle examine la tâche dans sa boîte de réception AEM et l’approuve.

![boîte de réception](assets/inbox.png)

#### Fonctionnement {#how-it-works-2}

Lorsque Sarah remplit et envoie la demande de carte de crédit, un Forms Workflow se déclenche et une tâche est créée dans la boîte de AEM de Gloria.

AEM Forms sur OSGi fournit des processus basés sur l’utilisation de formulaires qui vous permettent de créer des processus basés sur des formulaires adaptatifs. Ces processus peuvent être utilisés pour la révision et l’approbation, les flux de processus d’entreprise, pour démarrer les services de document, pour intégrer le processus de signature Acrobat Sign, etc. Pour plus d’informations, voir [Processus orientés formulaire sur OSGi](/help/forms/using/aem-forms-workflow.md).

L’image suivante illustre le processus d’AEM qui traite la demande de carte de crédit et génère une sortie PDF de la demande.

![flux de travail](assets/workflow.png)

#### Démonstration {#see-it-yourself-2}

Vous pouvez accéder à AEM boîte de réception pour le site we.finance à l’adresse https://&lt;*hostname*>:&lt;*PublishPort*>/content/we-finance/global/en.html. Sur la page, appuyez sur . **[!UICONTROL Se connecter]**, sélectionnez la variable **[!UICONTROL Connexion en tant que représentant]** , connectez-vous à la boîte de réception AEM à l’aide de la case à cocher `grios/password` comme nom d’utilisateur/mot de passe pour Gloria Rios, et approuvez la demande de carte de crédit. Pour plus d’informations sur l’utilisation de la boîte de réception AEM pour les tâches du workflow relatives aux formulaires, voir [Gérer des applications et des tâches Forms dans la boîte de réception AEM](/help/forms/using/manage-applications-inbox.md).

![inbox-1](assets/inbox-1.png)

Lorsque vous approuvez la demande, Sarah reçoit un courrier électronique contenant le kit de bienvenue.

### Sarah reçoit le kit de bienvenue et demande une carte ajoutée {#sarah-receives-the-welcome-kit-and-applies-for-an-add-on-card}

Lorsque la demande de carte de crédit de Sarah est approuvée, elle reçoit un courrier électronique contenant un lien vers le kit de bienvenue. Elle ouvre le kit de bienvenue, qui contient les détails de son compte de carte de crédit. Le kit de bienvenue affiche également des offres promotionnelles personnalisées pour Sarah. Lorsqu’elle fait défiler la page vers le bas, le kit de bienvenue contient un formulaire incorporé pour demander une carte ajoutée. Sarah remplit rapidement les informations requises à partir du kit de bienvenue et demande la carte ajoutée. Une boîte de dialogue de confirmation pour la demande de carte ajoutée s’affiche.

![welcome-kit-for-sara](assets/welcome-kit-for-sara.png)

Le kit de bienvenue est personnalisé pour Sarah et affiche des informations la concernant. Il lui offre la possibilité de télécharger une version PDF du kit de bienvenue.

![carte-avantages-platine](assets/benefits-of-platinum-card.png)

Le kit de bienvenue comprend un autre formulaire de demande que Sarah peut remplir et envoyer pour demander une carte ajoutée depuis le kit de bienvenue sans consulter le portail We.Finance.

![apply-addon-card](assets/apply-addon-card.png)

#### Fonctionnement {#how-it-works-3}

Le kit de bienvenue est une communication interactive incluse dans la variable `cq-we-finance-content-pkg.zip` module. Les cartes interactives de la version pour ordinateur qui présentent les avantages de la carte de crédit dans le kit de bienvenue sont une disposition personnalisée créée à l’aide de la mise en page de carte par défaut d’un fragment de document.

La demande de carte ajoutée est un formulaire adaptatif incorporé dans la communication interactive du kit de bienvenue.

#### Démonstration {#see-it-yourself-3}

Cliquez sur le bouton **[!UICONTROL Reprendre]** dans l’email que vous avez reçu à l’étape précédente. Il ouvre le brouillon de la demande. Renseignez tous les détails et envoyez la demande. Vous recevrez alors un kit de bienvenue. Examinez le kit de bienvenue.

Vous pouvez également afficher le kit de bienvenue à l’adresse URL suivante :

https://&lt;*hôte*>:&lt;*port*>/content/aemforms-refsite/doclink.html?document=/content/forms/af/we-finance/Credit-card/creditcardwelcomekit&amp;customerId=197&amp;channel=web

Vous pouvez y accéder sur les instances de création et de publication.

### Sarah reçoit un relevé de carte de crédit {#sarah-receives-a-credit-card-statement}

Comme Sarah commence à utiliser la carte de crédit, elle reçoit un autre courrier électronique de We.Finance comprenant son relevé de carte de crédit. Les illustrations suivantes montrent le courrier électronique contenant un lien vers le relevé de carte de crédit sur mobile.

![instruction-email](assets/statement-email.png)

Sarah clique sur Afficher le relevé dans le courrier électronique pour afficher le relevé de carte de crédit. Le relevé est une communication interactive. Il possède des versions Web et d’impression (PDF). L’instruction s’intègre au modèle de données Forms pour récupérer des données de la base de données, propres au client. Le relevé interactif se compose de plusieurs éléments :

* Résumé du relevé
* Rapport détaillé des dépenses
* Analyse graphique des dépenses
* Option permettant d’effectuer un paiement pour le montant dû indiqué dans le relevé
* Télécharger le reçu de paiement

![Différentes parties du relevé de carte de crédit](assets/sara-rose-statement.png)

Sarah n’a pas besoin d’accéder au portail ni de rechercher dans ses courriers électroniques la version PDF du relevé de carte de crédit pour l’archivage hors ligne. Elle clique simplement sur Télécharger l’instruction pour télécharger une version PDF de l’instruction.

Le relevé détaillé est présenté dans un tableau réactif. Le relevé offre également la possibilité de payer une partie ou la totalité du montant dû indiqué dans le relevé.

![Relevé détaillé](assets/statement-details.png)

Sarah planifie le paiement à partir du relevé. Sarah peut également utiliser l’option Paiement Flexi pour diviser le paiement en deux parties égales.

#### Fonctionnement {#how-it-works-4}

Le relevé de carte de crédit est une communication interactive. Le tableau détaillé des dépenses du relevé est un tableau réactif. Le graphique de l’analyse des dépenses est un composant graphique qui lit le tableau des dépenses et génère le graphique circulaire.

#### Démonstration {#see-it-yourself-4}

Vous pouvez consulter le relevé de carte de crédit interactif à l’adresse URL suivante :

https://&lt;*hostname*>:&lt;*port*>/content/aemforms-refsite/doclink.html?document=/content/forms/af/we-finance/Credit-card/Credit-card-statement&amp;customerId=197&amp;channel=web

Vous pouvez y accéder sur les instances de création et de publication.

Le relevé de carte de crédit affiche des offres promotionnelles à la fin du relevé. Vous pouvez intégrer Adobe Target à la communication interactive AEM Forms afin de proposer des offres ciblées promotionnelles basées sur des segments de clients spécifiques. Pour configurer votre communication interactive afin d’utiliser Adobe Target pour des offres personnalisées et ciblées, voir [créer des expériences ciblées](/help/forms/using/experience-targeting-forms.md).

![](do-not-localize/offers.png)

### We.Finance analyse les performances de la demande de carte de crédit {#we-finance-analyzes-the-performance-of-the-credit-card-application}

We.Finance, de temps à autre, examine les performances de sa demande de carte de crédit afin de vérifier les problèmes éventuels des clients. Ils utilisent cette analyse pour prendre des décisions éclairées au sujet des modifications requises dans la demande de carte de crédit afin d’améliorer l’expérience utilisateur, de réduire le taux d’abandon des formulaires et ainsi d’améliorer la conversion. Ils tirent parti de l’intégration d’AEM Forms à Adobe Analytics pour leur analyse. L’image suivante illustre le tableau de bord des analyses.

Pour plus d’informations sur l’interprétation du tableau de bord des analyses, voir [Affichage et compréhension des rapports d’analyse AEM Forms](/help/forms/using/view-understand-aem-forms-analytics-reports.md).

![cc-analytics](assets/cc-analytics.png)

#### Fonctionnement {#how-it-works-5}

Les mesures de performances du formulaire de demande de carte de crédit sont suivies à l’aide d’Adobe Analytics. Pour plus d’informations sur la configuration d’Adobe Analytics et l’affichage des rapports, voir [Configuration des analyses pour les formulaires et les documents](/help/forms/using/configure-analytics-forms-documents.md).

#### Démonstration {#see-it-yourself-br}

Pour que vous puissiez afficher et explorer le rapport d’analyse, nous fournissons des données sources pour la demande de carte de crédit sur le site de référence. Avant d’utiliser les données sources, reportez-vous à la section [Configuration d’Analytics](/help/forms/using/setup-reference-sites.md#configureanalytics). Effectuez les étapes suivantes dans l’instance d’auteur pour afficher le rapport avec les données sources :

1. Accédez à **[!UICONTROL Forms et documents]** Interface utilisateur à l’adresse https://&lt;*hostname*>:&lt;*AuthorPort*>/aem/forms.html/content/dam/formsanddocuments.

1. Cliquez pour ouvrir la **[!UICONTROL We.Finance]** Dossier.
1. Sélectionner **[!UICONTROL Demande de carte de crédit]** formulaire adaptatif, puis dans la barre d’outils, cliquez sur **[!UICONTROL Activation d’Analytics]**.

1. Sélectionnez à nouveau le formulaire adaptatif et cliquez sur **[!UICONTROL Rapport Analytics]** dans la barre d’outils pour générer le rapport. Un rapport vierge s’affiche initialement.

Pour générer un rapport d’analyse avec des données sources :

1. Dans le navigateur d’adresse de CRXDE Lite, saisissez : `/apps/we-finance/demo-artifacts/analyticsTestData/Credit card Analytics Test Data`
1. Les données de test sont sélectionnées dans la structure de répertoires du côté gauche.
1. Double-cliquez sur le fichier sélectionné pour ouvrir son contenu dans le panneau de droite.
1. Copiez tout le contenu du fichier de données source.
1. Dans CRXDE, accédez à : `/content/dam/formsanddocuments/we-finance/cc-app/jcr:content/analyticsdatanode/lastsevendays`.
1. Dans le **[!UICONTROL analyticsdata]** champ sous **[!UICONTROL Propriétés]**, collez le contenu copié du fichier de données source.

1. Sélectionner **Demande de carte de crédit** formulaire adaptatif et clic **[!UICONTROL Rapport Analytics]** dans la barre d’outils pour générer le rapport avec les données sources.

**Test A/B de la demande de carte de crédit**

En plus d’analyser les performances de la demande de carte de crédit et de l’améliorer constamment, We.Finance tire parti de l’intégration d’AEM Forms à Target pour créer des tests A/B. Il leur permet de proposer différentes expériences du formulaire de demande de carte de crédit et d’identifier l’expérience qui entraîne un meilleur taux de conversion en termes de remplissage et d’envoi du formulaire.

Pour configurer Target dans le serveur AEM Forms, voir [Configuration et intégration de Target dans AEM Forms](/help/forms/using/ab-testing-adaptive-forms.md#set%20up%20and%20integrate%20target%20in%20aem%20forms).

Effectuez les étapes suivantes pour expérimenter la création d’un test A/B pour le formulaire de demande de carte de crédit We.Finance :

1. Accédez à **[!UICONTROL Forms et documents]** à l’adresse https://&lt;*hostname*>:&lt;*AuthorPort*>/aem/forms.html/content/dam/formsanddocuments.

1. Cliquez pour ouvrir la **[!UICONTROL We.Finance]** dossier.
1. Sélectionner **[!UICONTROL Demande de carte de crédit]** formulaire adaptatif.
1. Cliquez sur **[!UICONTROL Plus]** dans la barre d’outils et sélectionnez **[!UICONTROL Configuration des tests A/B]**. La page Configurer les tests A/B s’ouvre.

1. Spécifiez une **[!UICONTROL Nom de l’activité]**.
1. Dans la liste déroulante Audience , sélectionnez une audience à qui vous souhaitez proposer différentes expériences du formulaire. Par exemple : **Visiteurs utilisant Chrome**.
1. Dans le **[!UICONTROL Distribution de l’expérience]** pour les expériences A et B, spécifiez la répartition, en termes de pourcentage, afin de déterminer la distribution des expériences entre l’audience totale. Par exemple, si vous spécifiez 40, 60 pour les expériences A et B, respectivement, l’expérience A sera transmise à 40 % de l’audience et les 60 % restants verront l’expérience B.
1. Cliquez sur **Configurer**. Une boîte de dialogue s’affiche pour confirmer la création du test A/B.
1. Cliquez sur **Terminé**.
1. Sélectionnez la **Demande de carte de crédit** formulaire et clic **Modifier**. Elle permet d’ouvrir l’une des expériences. Cliquez sur **Expérience B**. Le formulaire s’ouvre en mode d’édition.

1. Modifiez le formulaire selon vos besoins pour créer une expérience différente de l’expérience A par défaut.
1. Accédez à l’interface utilisateur de Forms et documents, sélectionnez le formulaire, puis cliquez sur **Plus**, puis sélectionnez **Démarrer le test A/B**.

1. Ouvrez maintenant le formulaire dans le navigateur Chrome plusieurs fois à l’aide de l’URL suivante :

   `https://[hostname]:[port]/content/dam/formsanddocuments/we-finance/cc-app/jcr:content?wcmmode=disabled`

   >[!NOTE]
   >
   >Supprimez le cookie portant le nom . **mbox** de la persistance des cookies du navigateur avant d’ouvrir le formulaire la prochaine fois. Vous verrez l’expérience A et B du formulaire de manière aléatoire.

1. Sélectionnez le formulaire, puis cliquez sur **Plus**, puis cliquez sur **Rapport de test A/B**. Vous ne trouverez pas beaucoup de données dans le rapport, car vous venez de commencer le test. Ajoutons maintenant quelques données sources pour voir à quoi ressemble le rapport de test A/B.

1. Ouvrez CRXDE Lite et effectuez une sauvegarde du fichier suivant : /libs/fd/fmaddon/gui/components/admin/targetreport/clientlibs/targetreport/js/targetreport.js
1. Remplacer la définition de fonction `onReportLoadSuccess` dans le fichier mentionné ci-dessus avec la définition de fonction dans le fichier suivant : /apps/we-finance/demo-artifacts/targetreport.js

   **Remarque :** Ces modifications sont uniquement à des fins de démonstration. Assurez-vous de restaurer le contenu du fichier après avoir terminé cette procédure.

1. Actualisez le rapport que vous avez généré et vous verrez quelque chose comme ceci. Examinez le tableau de bord des rapports.

![ab-test-report-3](assets/ab-test-report-3.png)

Pour mettre fin au test A/B, cliquez sur **Fin du test A/B** dans le tableau de bord des rapports. Actuellement, une boîte de dialogue vous invite à déclarer une expérience. Sélectionnez l’expérience la plus probante et confirmez la fin du test A/B.

Si vous choisissez l’expérience A comme expérience gagnante, le test A/B sera mis fin et, à partir de ce moment, seule l’expérience A sera transmise à toutes les audiences, y compris celles utilisant Chrome.

## Présentation de la demande de prêt immobilier {#home-mortgage-application-walkthrough}

Le scénario de prêt immobilier We.Finance comprend les personnages suivants :

* Sarah Rose, une cliente de We.Finance
* Gloria Rios, chef de la Carte de crédit et des Prêts immobiliers, We.Finance
* John Doe, représentant de l’assistance clientèle, We.Finance

L’infographie suivante illustre le processus détaillé d’une demande de prêt immobilier.

![home_prêt_application_walkthrough](assets/home_mortgage_application_walkthrough.png)

Examinons maintenant en détail les étapes du scénario du site de référence pour voir comment AEM Forms aide We.Finance à atteindre ses objectifs.

### Sarah se rend sur le site Web de We.Finance et demande un prêt immobilier {#sarah-visits-we-finance-website-and-applies-for-home-mortgage}

Sarah Rose prévoit d’acheter une maison et de rechercher un prêt immobilier. Elle est cliente de We.Finance et se rend donc sur le portail We.Finance pour explorer les offres de prêt immobilier. Elle se rend à la section Prêts et trouve une calculatrice de prêt immobilier sur le portail. Elle remplit les détails et clique sur Calculer mon prêt, ce qui renvoie un plan de prêt immobilier.

![prêts1](assets/loans1.png) ![prêts2](assets/loans2.png)
**Figure :** *Calcul de prêt immobilier*

![prêts3](assets/loans3.png)
**Figure :** *Résultat du calculateur de prêt immobilier*

#### Fonctionnement {#how-it-works-6}

Le calculateur de prêt immobilier sur la page Prêts est un formulaire adaptatif incorporé à la page AEM Sites. Vous pouvez consulter la page Prêts en mode d’édition à l’adresse `https://[authorHost]:[authorPort]/editor.html/content/we-finance/global/en/loan-landing-page.html`.

Le calculateur de prêt immobilier intégré, qui est un formulaire adaptatif, utilise des règles pour calculer le montant de l’IME en fonction des détails du prêt fournis dans les champs du calculateur. Vous pouvez consulter le formulaire adaptatif à l’adresse `https://[authorHost]:[authorPort]/editor.html/content/forms/af/we-finance/hm-calc.html`.

#### Démonstration {#see-it-yourself-5}

Accédez au portail We.Finance à l’adresse `https://<publishHost>:<publishPort>/content/we-finance/global/en.html` et cliquez sur **[!UICONTROL Prêts]**. Fournissez des détails dans le calculateur de prêt immobilier et consultez les résultats.

### Sarah trouve l’offre intéressante et choisit de la présenter {#sarah-finds-the-offer-interesting-and-chooses-to-apply-1}

Sarah choisit de demander un prêt immobilier et clique **[!UICONTROL Appliquer maintenant]** dans les résultats du calculateur de prêt immobilier. Il ouvre la demande de prêt immobilier.

Si Sarah accède à la demande de prêt immobilier à partir de son appareil mobile, le formulaire de demande s’ouvre dans une vue optimisée pour l’affichage sur un appareil mobile. Dans cette vue, le formulaire de demande effectue le rendu d’une section à la fois. Cela permet à Sarah d’afficher et de fournir des informations progressivement lorsqu’elle navigue dans le formulaire de demande.

Les illustrations suivantes montrent le processus lorsque Sarah parcourt la demande de prêt immobilier sur son appareil mobile.

![Remplir la demande de prêt immobilier sur un périphérique mobile](assets/mortgage-form-on-mobile.png)

Si Sarah clique **Appliquer maintenant** depuis son bureau, le formulaire de demande de prêt immobilier s’ouvre comme suit. Les informations que Sarah a fournies dans le calculateur de prêt immobilier sont préremplies dans le formulaire de demande. Sarah remplit les détails et clics restants **Continuer**.

![application de prêt immobilier](assets/mortgage-application.png)

En fonction des informations que Sarah a renseignées dans le calculateur de prêt immobilier, elle reçoit quelques plans de prêt immobilier. Elle choisit le plan qui lui convient et continue à remplir la demande. Elle signe et envoie enfin la demande.

La demande envoyée est envoyée à We.Finance pour approbation.

![Enregistrement d’un brouillon de demande](assets/mortgage-plans.png)

#### Fonctionnement {#how-it-works-7}

Le **Appliquer maintenant** ce bouton redirige Sarah vers la demande de prêt immobilier. La demande est un formulaire adaptatif, que vous pouvez consulter dans les instances de création à l’adresse `https://[host]:[Port]/editor.html/content/forms/af/we-finance/hm-app.html`.

Voici quelques-unes des fonctions clés que vous pouvez examiner dans le formulaire adaptatif :

* Il est basé sur un schéma XSD, `homeMortgageApplication.xsd`.
* Il est créé à l’aide du thème We.Finance B pour le style et du modèle We.Finance pour la mise en page. En outre, elle utilise Disposition sans titres de panneau dans la disposition d’en-tête du formulaire pour la navigation mobile. Elle affiche une disposition mobile progressive lorsqu’elle est ouverte à partir d’un appareil mobile. Vous pouvez consulter le modèle et le thème utilisés dans le formulaire adaptatif aux emplacements suivants sur votre instance d’auteur AEM :

   * `https://[host]:[Port]/libs/wcm/core/content/sites/templates.html/conf/we-finance`
   * `https://[host]:[Port]/editor.html/content/dam/formsanddocuments-themes/we-finance/we-finance-theme-b/jcr:content`

* Le premier onglet, Prise en main, dans la demande est un calculateur de prêt immobilier dynamique qui affiche des options en fonction de la sélection de l’utilisateur. Par exemple, les champs et les valeurs sont différents pour les options Achat et Refinancement . Cette fonctionnalité est réalisée à l’aide de règles d’affichage/masquage. En outre, lorsque vous cliquez sur Continuer et que l’onglet Plans est initialisé, il appelle un service Web configuré dans un modèle de données de formulaire pour récupérer et afficher les plans de prêt immobilier. Vous pouvez consulter les modèles de données de formulaire et les services configurés à l’adresse `https://[host]:[Port]/aem/forms.html/content/dam/formsanddocuments-fdm`.
* Il utilise divers composants de formulaire adaptatif pour capturer des entrées et s’adapte aux réponses des utilisateurs. Il utilise également des composants tels que Email qui prennent en charge les types d’entrée HTML5.
* Il utilise le composant Étape de signature pour afficher le formulaire rempli et permet la signature électronique sur le formulaire.
* Elle utilise l’action d’envoi Appeler le processus d’AEM pour déclencher le processus d’AEM du prêt immobilier We Finance. Vous pouvez consulter le workflow utilisé dans ce formulaire à l’adresse `https://[host]:[Port]/editor.html/conf/global/settings/workflow/models/we-finance-home-mortgage-workflow.html`

Il est recommandé de consulter le formulaire pour comprendre le schéma, les composants, les règles, les modèles de données de formulaire, le processus des formulaires et l’action d’envoi utilisés pour créer le formulaire.

Consultez également la documentation suivante pour plus d’informations sur les fonctionnalités utilisées dans le formulaire adaptatif de demande de prêt immobilier :

* [Présentation de la création de formulaires adaptatifs](/help/forms/using/introduction-forms-authoring.md)
* [Création de formulaires adaptatifs à l’aide d’un schéma XML](/help/forms/using/adaptive-form-xml-schema-form-model.md)
* [Éditeur de règles](/help/forms/using/rule-editor.md)
* [Thèmes](/help/forms/using/themes.md)
* [Intégration de données ](/help/forms/using/data-integration.md)
* [Utilisation d’Acrobat Sign dans les formulaires adaptatifs](/help/forms/using/working-with-adobe-sign.md)
* [Processus basé sur l’utilisation de Forms sur OSGi](/help/forms/using/aem-forms-workflow.md)

#### Démonstration {#see-it-yourself-6}

Accédez à `https://[server]:[port]/content/we-finance/global/en/all-forms.html` et cliquez sur le bouton **Appliquer maintenant** sur la demande de prêt immobilier. Renseignez les détails dans l’onglet Prise en main , essayez différentes options et envoyez la demande.

Assurez-vous de spécifier un ID de courrier électronique valide dans la demande pour recevoir un accusé de réception dans votre boîte de réception.

### We.Finance reçoit la demande {#approving_the_application-1}

We.Finance reçoit la demande de prêt immobilier envoyée par Sarah. La tâche d’approbation ou de rejet de la demande est assignée à Gloria Rios. Elle examine la demande et constate que l’ID du gouvernement de Sarah est absent.

![grios-inbox](assets/grios-inbox.png)

Gloria ouvre la tâche, clique sur Besoin de plus d’informations et envoie un commentaire sur l’ID d’administration manquant.

![need-more-info](assets/need-more-info.png)

La tâche est maintenant assignée à John Doe, un représentant de l’assistance clientèle chez We.Finance. Il ouvre la tâche et examine le commentaire de Gloria. Il contacte Sarah et lui demande d’envoyer une copie de sa carte d’identité. Après avoir reçu une copie de l’ID de Sarah, il l’joint à la tâche et envoie la demande pour réévaluation.

![réévaluation](assets/reevaluation.png)

La tâche est réaffectée à Gloria. Elle consulte la pièce jointe et approuve la demande.

#### Fonctionnement {#how-it-works-8}

Lorsque Sarah remplit et envoie la demande de prêt immobilier, un Forms Workflow se déclenche et une tâche est créée dans la boîte de AEM de Gloria. Lorsque Gloria examine la demande et demande plus d’informations, la tâche est assignée à John Doe. Lorsque John Doe joint l’ID et envoie à nouveau la demande, il est affecté à Gloria. Elle est définie dans le workflow AEM associé à la demande de prêt immobilier.

AEM Forms sur OSGi fournit des processus basés sur l’utilisation de formulaires qui vous permettent de créer des processus basés sur des formulaires adaptatifs. Ces processus peuvent être utilisés pour la révision et l’approbation, les flux de processus d’entreprise, pour démarrer les services de document, pour intégrer le processus de signature Acrobat Sign, etc. Pour plus d’informations, voir [Processus orientés formulaire sur OSGi](/help/forms/using/aem-forms-workflow.md).

L’image suivante illustre le processus d’AEM associé à la demande de prêt immobilier.

![prêt immobilier-workflow-modèle](assets/mortgage-workflow-model.png)

#### Démonstration {#see-it-yourself-7}

Vous pouvez accéder à la boîte de réception AEM à l’adresse https://&lt;***hostname***>:&lt;***AuthorPort***>/content/we-finance/global/en/login.html?resource=/aem/inbox.html. Connectez-vous à la boîte de réception AEM à l’aide de `grios/password` comme nom d’utilisateur/mot de passe pour Gloria Rios et `jdoe/jdoe` pour John Doe, et explorez le processus de demande de prêt immobilier.

Pour plus d’informations sur l’utilisation de la boîte de réception AEM pour les tâches du workflow relatives aux formulaires, voir [Gérer des applications et des tâches Forms dans la boîte de réception AEM](/help/forms/using/manage-applications-inbox.md).

### Sarah reçoit le kit de bienvenue {#sarah-receives-the-welcome-kit}

Lorsque la demande de prêt immobilier de Sarah est approuvée, elle reçoit un courrier électronique contenant un lien vers le kit de bienvenue. Elle ouvre le kit de bienvenue, qui comprend un carrousel présentant des offres promotionnelles personnalisées pour Sarah.

![prêt immobilier-bienvenue-kit](assets/mortgage-welcome-kit.png)

Le kit de bienvenue est personnalisé pour Sarah et affiche des informations la concernant. Il lui offre la possibilité de télécharger une version PDF du kit de bienvenue. Le bouton fléché au bas de l’écran permet à Sarah de faire défiler la page vers le bas et de parcourir d’autres sections du kit de bienvenue.

#### Fonctionnement {#how-it-works-9}

Le kit de bienvenue est une communication interactive incluse dans la variable `cq-we-finance-content-pkg.zip` module. Les offres promotionnelles du kit de bienvenue sont diffusées par le serveur Adobe Target. Les offres sont personnalisées et ciblées pour des segments de clients spécifiques. Le kit de bienvenue récupère les offres d’un serveur Adobe Target préconfiguré pour un segment d’audience de clientes féminines.

Les cartes interactives dans la version pour ordinateur du kit de bienvenue utilisent une disposition personnalisée créée à l’aide de la disposition de carte par défaut d’un fragment de document.

#### Démonstration {#see-it-yourself-8}

Si vous avez fourni votre ID de courrier électronique lors du remplissage de la demande de prêt immobilier, vous avez reçu un courrier électronique contenant un lien vers le kit de bienvenue. Vérifiez votre boîte de réception et examinez le kit de bienvenue.

Vous pouvez l’afficher dans AEM instance de publication à l’adresse URL suivante :

`https://[host]:[port]/content/forms/af/we-finance/mortgage-loan-welcome-kit.html`

### Sarah reçoit un relevé de compte {#sarah-receives-an-account-statement}

Lorsque Sarah se sert du prêt et commence à payer les versements, elle reçoit un autre courrier électronique de We.Finance comprenant son relevé de compte mensuel.

![prêt immobilier-courrier électronique](assets/mortgage-statement-email.png)

Sarah clique sur Afficher le relevé dans le courrier électronique pour afficher le relevé de compte de prêt immobilier. Le relevé interactif se compose de plusieurs éléments :

* Résumé du relevé
* Détails du relevé

L’image suivante montre différentes parties du relevé de compte sur le bureau.

![Relevé de compte de prêt immobilier](assets/mortgage-statement.png)

Le relevé détaillé est présenté dans un tableau réactif et permet de payer une partie ou l’intégralité du montant dû indiqué dans le relevé.

#### Fonctionnement {#how-it-works-10}

Le relevé de prêt immobilier est une communication interactive. Il est généré à l’aide du processus de traitement par lot JSON. Le tableau détaillé des dépenses du relevé est un tableau réactif.

#### Démonstration {#see-it-yourself-9}

Vous pouvez consulter le relevé de compte de prêt immobilier interactif à l’adresse URL suivante :

https://&lt;*hostname*>:&lt;*port*>/content/forms/af/we-finance/mortgage-account-statement.html?wcmmode=disabled

Vous pouvez y accéder sur les instances de création et de publication.

### We.Finance analyse les performances de la demande de prêt immobilier {#we-finance-analyzes-the-performance-of-the-mortgage-application}

We.Finance, de temps à autre, examine les performances de sa demande de prêt immobilier pour vérifier les problèmes éventuels des clients. Il utilise cette analyse pour prendre des décisions éclairées concernant les modifications requises dans la demande de prêt immobilier afin d’améliorer l’expérience utilisateur, de réduire le taux d’abandon des formulaires et ainsi d’améliorer la conversion. Ils tirent parti de l’intégration d’AEM Forms à Adobe Analytics pour leur analyse. L’image suivante illustre le tableau de bord des analyses.

Pour plus d’informations sur l’interprétation du tableau de bord des analyses, voir [Affichage et compréhension des rapports d’analyse AEM Forms](/help/forms/using/view-understand-aem-forms-analytics-reports.md).

![prêt immobilier-analytics](assets/mortgage-analytics.png)

#### Fonctionnement {#how-it-works-11}

Les mesures de performances du formulaire de demande de prêt immobilier sont suivies à l’aide d’Adobe Analytics. Pour plus d’informations sur la configuration d’Adobe Analytics et l’affichage des rapports, voir [Configuration des analyses pour les formulaires et les documents](/help/forms/using/configure-analytics-forms-documents.md).

#### Démonstration {#see-it-yourself-br-1}

Pour que vous puissiez afficher et explorer le rapport d’analyse, nous fournissons des données sources pour la demande de prêt immobilier sur le site de référence. Avant d’utiliser les données sources, reportez-vous à la section [Configuration d’Analytics](/help/forms/using/setup-reference-sites.md#configureanalytics). Effectuez les étapes suivantes dans l’instance d’auteur pour afficher le rapport avec les données sources :

1. Accédez à **Forms et documents** Interface utilisateur à l’adresse https://&lt;*hostname*>:&lt;*AuthorPort*>/aem/forms.html/content/dam/formsanddocuments.

1. Cliquez pour ouvrir la **we-finance** Dossier.
1. Sélectionner **[!UICONTROL Demande de prêt immobilier]** formulaire adaptatif, puis dans la barre d’outils, cliquez sur **[!UICONTROL Activation d’Analytics]**.

1. Sélectionnez à nouveau le formulaire, puis cliquez sur **[!UICONTROL Rapport Analytics]** dans la barre d’outils pour générer le rapport. Un rapport vierge s’affiche initialement.

Pour générer un rapport d’analyse avec des données sources :

1. Dans le navigateur d’adresse de CRXDE Lite, saisissez ce qui suit : `/apps/we-finance/demo-artifacts/analyticsTestData/HomeMortgageAnalyticsTestData`
1. Les données de test sont sélectionnées dans la structure de répertoires du côté gauche.
1. Double-cliquez sur le fichier sélectionné pour ouvrir son contenu dans le panneau de droite.
1. Copiez tout le contenu du fichier de données source.
1. Dans CRXDE, accédez à : `/content/dam/formsanddocuments/we-finance/hm-app/jcr:content/analyticsdatanode/lastsevendays`.
1. Dans le champ analyticsdata sous Propriétés, collez le contenu copié du fichier de données source.
1. Générez à présent le rapport d’analyse pour le formulaire de demande de prêt immobilier. Le rapport contient les données sources.

**Test A/B de la demande de prêt immobilier**

En plus d’analyser les performances de la demande de prêt immobilier et de l’améliorer constamment, We.Finance tire parti de l’intégration d’AEM Forms à Target pour créer des tests A/B. Il leur permet de proposer différentes expériences du formulaire de demande et d’identifier l’expérience qui entraîne un meilleur taux de conversion en termes de remplissage et d’envoi du formulaire.

Pour configurer Target dans le serveur AEM Forms, voir [Configuration et intégration de Target dans AEM Forms](/help/forms/using/ab-testing-adaptive-forms.md#set%20up%20and%20integrate%20target%20in%20aem%20forms).

Effectuez les étapes suivantes dans l’instance d’auteur pour expérimenter la création d’un test A/B pour le formulaire de demande de prêt immobilier We.Finance :

1. Accédez à **Forms et documents** à l’adresse https://&lt;*hostname*>:&lt;*AuthorPort*>/aem/forms.html/content/dam/formsanddocuments.

1. Cliquez pour ouvrir la **We.Finance** dossier.
1. Sélectionner **Demande de prêt immobilier** formulaire adaptatif.
1. Cliquez sur **Plus** dans la barre d’outils et sélectionnez **Configuration des tests A/B**. La page Configurer les tests A/B s’ouvre.

1. Spécifiez une **Nom de l’activité**.
1. Dans la liste déroulante Audience , sélectionnez une audience à qui vous souhaitez proposer différentes expériences du formulaire. Par exemple : **Visiteurs utilisant Chrome**.
1. Dans le **Distribution de l’expérience** pour les expériences A et B, spécifiez la répartition, en termes de pourcentage, afin de déterminer la distribution des expériences entre l’audience totale. Par exemple, si vous spécifiez 40, 60 pour les expériences A et B, respectivement, l’expérience A sera transmise à 40 % de l’audience et les 60 % restants verront l’expérience B.
1. Cliquez sur **Configurer**. Une boîte de dialogue s’affiche pour confirmer la création du test A/B.
1. Cliquez sur **Terminé**.
1. Sélectionnez la **Demande de prêt immobilier** formulaire adaptatif et clic **Modifier**. Elle permet d’ouvrir l’une des expériences. Cliquez sur **Expérience B**. Le formulaire s’ouvre en mode d’édition.

1. Modifiez le formulaire selon vos besoins pour créer une expérience différente de l’expérience A par défaut.
1. Accédez à l’interface utilisateur de Forms et documents, sélectionnez le formulaire, puis cliquez sur **Plus**, puis sélectionnez **Démarrer le test A/B**.

1. Ouvrez maintenant le formulaire dans le navigateur Chrome plusieurs fois à l’aide de l’URL suivante :

   `https://[hostname]:[port]/content/dam/formsanddocuments/we-finance/hm-app/jcr:content?wcmmode=disabled`

   >[!NOTE]
   >
   >Supprimez le cookie portant le nom . **mbox** de la persistance des cookies du navigateur avant d’ouvrir le formulaire la prochaine fois. Vous verrez l’expérience A et B du formulaire de manière aléatoire.

1. Sélectionnez le formulaire, puis cliquez sur **Plus**, puis cliquez sur **Rapport de test A/B**. Vous ne trouverez pas beaucoup de données dans le rapport, car vous venez de commencer le test. Ajoutons maintenant quelques données sources pour voir à quoi ressemble le rapport de test A/B.

1. Ouvrez CRXDE Lite et effectuez une sauvegarde du fichier suivant : /libs/fd/fmaddon/gui/components/admin/targetreport/clientlibs/targetreport/js/targetreport.js
1. Remplacez la définition de la variable `onReportLoadSuccess` dans le fichier mentionné ci-dessus avec la définition de fonction dans le fichier suivant : /apps/we-finance/demo-artifacts/targetreport.js

   >[!NOTE]
   >
   >Ces modifications sont uniquement à des fins de démonstration. Assurez-vous de restaurer le contenu du fichier après avoir terminé cette procédure.

1. Actualisez le rapport que vous avez généré et vous verrez quelque chose comme ceci. Examinez le tableau de bord des rapports.

![ab-test-report-4](assets/ab-test-report-4.png)

Pour mettre fin au test A/B, cliquez sur **Fin du test A/B** dans le tableau de bord des rapports. Actuellement, une boîte de dialogue vous invite à déclarer une expérience. Sélectionnez l’expérience la plus probante et confirmez la fin du test A/B.

Si vous choisissez l’expérience A comme expérience gagnante, le test A/B sera mis fin et, à partir de ce moment, seule l’expérience A sera transmise à toutes les audiences, y compris celles utilisant Chrome.

## Présentation de la demande de prêt immobilier avec Microsoft Dynamics {#home-mortgage-application-walkthrough-with-microsoft-dynamics}

Le scénario de prêt immobilier We.Finance avec Microsoft Dynamics implique les personnages suivants :

* Sarah Rose, une cliente de We.Finance
* L’administrateur de l’instance We.Finance Microsoft Dynamics

La présentation de la demande de prêt immobilier avec Microsoft Dynamics montre comment un client We.Finance peut utiliser le site pour demander un prêt immobilier lorsque le site de référence utilise Microsoft Dynamics pour l’intégration des données. La présentation se termine par les données renseignées par l’utilisateur reçu par Microsoft Dynamics. Avant de procéder à ce scénario, vous devez effectuer les opérations suivantes : [Configuration de Microsoft Dynamics 365 pour le processus de prêt immobilier du site de référence We.Finance](/help/forms/using/ms-dynamics-configuration-home-mortgage.md).

### Sarah se rend sur le site Web de We.Finance et demande un prêt immobilier {#sarah-visits-we-finance-website-and-applies-for-home-mortgage-1}

Sarah Rose prévoit d’acheter une maison et de rechercher un prêt immobilier. Elle est cliente de We.Finance et se rend donc sur le portail We.Finance pour explorer les offres de prêt immobilier. Elle se rend à la section Prêts et trouve une calculatrice de prêt immobilier sur le portail. Elle remplit les détails et clique sur Calculer mon prêt, ce qui renvoie un plan de prêt immobilier.

![prêts1](assets/loans1.png) ![prêts2](assets/loans2.png)
**Figure :** *Calcul de prêt immobilier*

![prêts3](assets/loans3.png)
**Figure :** *Résultat du calculateur de prêt immobilier*

#### Fonctionnement {#how-it-works-12}

Le calculateur de prêt immobilier sur la page Prêts est un formulaire adaptatif incorporé à la page AEM Sites. Vous pouvez consulter la page Prêts en mode d’édition à l’adresse `https://[authorHost]:[authorPort]/editor.html/content/we-finance/global/en/loan-landing-page.html`.

Le calculateur de prêt immobilier intégré, qui est un formulaire adaptatif, utilise des règles pour calculer le montant de l’IME en fonction des détails du prêt fournis dans les champs du calculateur. Vous pouvez consulter le formulaire adaptatif à l’adresse `https://[authorHost]:[authorPort]/editor.html/content/forms/af/we-finance/ms-dynamics/home-mortgage-calculator.html`.

#### Démonstration {#see-it-yourself-10}

Accédez au portail We.Finance à l’adresse `https://<publishHost>:<publishPort>/content/we-finance/global/en.html` et cliquez sur **[!UICONTROL Prêts]**. Fournissez des détails dans le calculateur de prêt immobilier et consultez les résultats.

### Sarah trouve l’offre intéressante et choisit de la présenter {#sarah-finds-the-offer-interesting-and-chooses-to-apply-2}

Sarah choisit de demander un prêt immobilier et clique **[!UICONTROL Appliquer maintenant]** dans les résultats du calculateur de prêt immobilier. Il ouvre la demande de prêt immobilier.

Si Sarah accède à la demande de prêt immobilier à partir de son appareil mobile, le formulaire de demande s’ouvre dans une vue optimisée pour l’affichage sur un appareil mobile. Dans cette vue, le formulaire de demande effectue le rendu d’une section à la fois. Cela permet à Sarah d’afficher et de fournir des informations progressivement lorsqu’elle navigue dans le formulaire de demande.

Les illustrations suivantes montrent le processus lorsque Sarah parcourt la demande de prêt immobilier sur son appareil mobile.

![Remplir la demande de prêt immobilier sur un périphérique mobile](assets/mortgage-form-on-mobile.png)

Si Sarah clique **Appliquer maintenant** depuis son bureau, le formulaire de demande de prêt immobilier s’ouvre comme suit. Les informations que Sarah a fournies dans le calculateur de prêt immobilier sont préremplies dans le formulaire de demande. Sarah remplit les détails et clics restants **Continuer**.

![application de prêt immobilier](assets/mortgage-application.png)

En fonction des informations que Sarah a renseignées dans le calculateur de prêt immobilier, elle reçoit quelques plans de prêt immobilier. Elle choisit le plan qui lui convient et continue à remplir la demande. Elle signe et envoie enfin la demande.

La demande envoyée est envoyée à We.Finance pour approbation.

![Enregistrement d’un brouillon de demande](assets/mortgage-plans.png)

#### Fonctionnement {#how-it-works-13}

Le **Appliquer maintenant** ce bouton redirige Sarah vers la demande de prêt immobilier. La demande est un formulaire adaptatif, que vous pouvez consulter dans les instances de création à l’adresse `https://[host]:[Port]/editor.html/content/forms/af/we-finance/ms-dynamics/application-for-home-mortgage.html`.

Voici quelques-unes des fonctions clés que vous pouvez examiner dans le formulaire adaptatif :

* Il est basé sur un schéma XSD, `homeMortgageApplication.xsd`.
* Il est créé à l’aide du thème We.Finance B pour le style et du modèle We.Finance pour la mise en page. En outre, elle utilise Disposition sans titres de panneau dans la disposition d’en-tête du formulaire pour la navigation mobile. Elle affiche une disposition mobile progressive lorsqu’elle est ouverte à partir d’un appareil mobile. Vous pouvez consulter le modèle et le thème utilisés dans le formulaire adaptatif aux emplacements suivants sur votre instance d’auteur AEM :

   * `https://[host]:[Port]/libs/wcm/core/content/sites/templates.html/conf/we-finance`
   * `https://[host]:[Port]/editor.html/content/dam/formsanddocuments-themes/we-finance/we-finance-theme-b/jcr:content`

* Le premier onglet, Prise en main, dans la demande est un calculateur de prêt immobilier dynamique qui affiche des options en fonction de la sélection de l’utilisateur. Par exemple, les champs et les valeurs sont différents pour les options Achat et Refinancement . Cette fonctionnalité est réalisée à l’aide de règles d’affichage/masquage. En outre, lorsque vous cliquez sur Continuer et que l’onglet Plans est initialisé, il appelle un service Web configuré dans un modèle de données de formulaire pour récupérer et afficher les plans de prêt immobilier. Vous pouvez consulter les modèles de données de formulaire et les services configurés à l’adresse `https://[host]:[Port]/aem/forms.html/content/dam/formsanddocuments-fdm`.
* Il utilise divers composants de formulaire adaptatif pour capturer des entrées et s’adapte aux réponses des utilisateurs. Il utilise également des composants tels que Email qui prennent en charge les types d’entrée HTML5.
* Il utilise le composant Étape de signature pour afficher le formulaire rempli et permet la signature électronique sur le formulaire.

Il est recommandé de consulter le formulaire pour comprendre le schéma, les composants, les règles, les modèles de données de formulaire, le processus des formulaires et l’action d’envoi utilisés pour créer le formulaire.

### L’administrateur affiche les données envoyées dans l’instance Microsoft Dynamics. {#the-administrator-views-the-submitted-data-in-the-microsoft-dynamics-instance}

We.Finance reçoit la demande de prêt immobilier envoyée par Sarah sur l’instance Microsoft Dynamics. L’administrateur appuie sur l’entrée dans la colonne de piste pour accéder à l’enregistrement de piste créé pour Sarah Rose.

![msdynamicsrecord](assets/msdynamicsrecord.png)

## Présentation de la demande d’assurance habitation {#home-insurance-application-walkthrough}

Le scénario d’assurance habitation We.Finance comprend les personnages suivants :

* Sarah Rose, une cliente de We.Finance
* Gloria Rios, chef de la Carte de crédit et des Prêts immobiliers, We.Finance
* Frank De Costa, agent d’assurance, We.Finance

L’infographie suivante illustre le déroulement détaillé d’un scénario de demande d’assurance habitation.

![workflow_insurance](assets/workflow_insurance.png)

Examinons maintenant en détail les étapes du scénario du site de référence pour voir comment AEM Forms aide We.Finance à atteindre ses objectifs.

### Sarah reçoit une newsletter de We.Finance et demande une assurance habitation {#sarah-receives-a-newsletter-from-we-finance-and-applies-for-home-insurance}

Sarah Rose est une cliente de prêt immobilier de We.Finance et recherche une bonne affaire d’assurance habitation. Elle visite le portail We.Finance et explore les plans d’assurance habitation. We.Finance l’a identifiée comme une cliente existante et lui envoie une newsletter ciblée par courrier électronique. La newsletter contient des offres d’assurance habitation.

![newsletter-assurance](assets/insurance-newsletter.png)

#### Fonctionnement {#how-it-works-14}

La newsletter envoyée à Sarah est une mise en oeuvre personnalisée qui déclenche un courrier électronique vers l’ID de courrier électronique spécifié. Le bouton Demander maintenant de la newsletter est lié à la demande d’assurance habitation, qui est un formulaire adaptatif sur une instance de publication.

#### Démonstration {#see-it-yourself-11}

Ouvrez l’URL suivante pour déclencher un courrier électronique de newsletter. Assurez-vous que vous remplacez `[emailID]` avec un compte de messagerie valide pour recevoir la newsletter. Ouvrez la newsletter, puis cliquez sur **[!UICONTROL Appliquer maintenant]** pour accéder à la demande d&#39;assurance habitation.

`https://[authorServer]:[authorPort]/content/campaigns/we-finance/start.html?app=ins&email=[emailID]&givenName=Sarah&familyName=Rose`

### Sarah trouve l’offre d’assurance habitation intéressante et choisit de postuler {#sarah-finds-the-home-insurance-offer-interesting-and-chooses-to-apply}

Sarah apprécie le forfait d’assurance habitation dans la newsletter et décide de le demander. Elle clique sur Demander maintenant dans la newsletter, ce qui ouvre la demande d’assurance habitation sur le portail We.Finance. Le formulaire de demande est organisé en sections selon une mise en page Carte.

Sur la page Informations personnelles, lorsque Sarah fournit son numéro de sécurité sociale, elle reçoit une invite lui demandant de se connecter à l’aide de ses informations d’identification.

![insurance-ssn](assets/insurance-ssn.png)

Sarah est déjà cliente chez We.Finance. Elle se connecte à l’aide de ses informations d’identification de compte We.Finance et ses informations personnelles sont automatiquement renseignées dans le formulaire. Elle continue à remplir et envoyer la demande.

Si Sarah envoie la demande sur un appareil mobile, elle passe en revue les écrans suivants.

![assurance-formulaire-sur-mobile](assets/insurance-form-on-mobile.png)

#### Fonctionnement {#how-it-works-15}

Le **Appliquer maintenant** sur la newsletter, Sarah est redirigée vers la demande d’assurance habitation sur le portail We.Finance. La demande est un formulaire adaptatif, que vous pouvez consulter dans l’instance de création à l’adresse `https://[host]:[Port]/editor.html/content/forms/af/we-finance/insurance/application-for-insurance.html`.

Voici quelques-unes des fonctions clés que vous pouvez examiner dans le formulaire adaptatif :

* Il est basé sur un schéma XSD, `insurance.xsd`.
* Il est créé à l’aide du thème Assurance pour le style et utilise la mise en page sans titres de panneau dans la mise en page de l’en-tête du formulaire pour la navigation mobile. Elle affiche une disposition mobile progressive lorsqu’elle est ouverte à partir d’un appareil mobile. Vous pouvez consulter le modèle à l’adresse `https://[host]:[Port]/libs/wcm/core/content/sites/templates.html/conf/we-finance` et le thème au `https://[host]:[Port]/editor.html/content/dam/formsanddocuments-themes/we-finance/insurance/jcr:content`.

* Il comprend des règles de formulaire adaptatif pour appeler les services de modèle de données de formulaire afin de préremplir les détails de l’utilisateur connecté. Il appelle également les services pour préremplir les informations par numéro de sécurité sociale ou adresse électronique fournie dans le formulaire. Vous pouvez consulter les modèles de données de formulaire et leurs services à l’adresse `https://[host]:[Port]/aem/forms.html/content/dam/formsanddocuments-fdm`.
* Il utilise divers composants de formulaire adaptatif pour capturer des entrées et s’adapte aux réponses des utilisateurs. Il utilise également des composants tels que Email qui prennent en charge les types d’entrée HTML5.
* Le bouton Enregistrer ma progression génère un identifiant unique pour l’utilisateur et enregistre la demande partiellement remplie en tant que brouillon dans un noeud du référentiel AEM. Il affiche également une autorisation de recherche de boîte de dialogue pour envoyer un courrier électronique contenant un lien vers le noeud contenant le brouillon de la demande. Le bouton Envoyer un courrier de la boîte de dialogue de confirmation déclenche un courrier électronique contenant un lien vers le noeud contenant le brouillon.
* Elle utilise l’action d’envoi Appeler le processus d’AEM pour déclencher le processus de validation de l’assurance habitation. Vous pouvez consulter le workflow utilisé dans ce formulaire à l’adresse `https://[host]:[Port]/editor.html/conf/global/settings/workflow/models/we-finance-insurance-workflow.html`

Il est recommandé de consulter le formulaire pour comprendre le schéma, les composants, les règles, les modèles de données de formulaire, le processus des formulaires et l’action d’envoi utilisés pour créer le formulaire.

Consultez également la documentation suivante pour plus d’informations sur les fonctionnalités utilisées dans le formulaire adaptatif de demande d’assurance habitation :

* [Présentation de la création de formulaires adaptatifs](/help/forms/using/introduction-forms-authoring.md)
* [Création de formulaires adaptatifs à l’aide d’un schéma XML](/help/forms/using/adaptive-form-xml-schema-form-model.md)
* [Éditeur de règles](/help/forms/using/rule-editor.md)
* [Thèmes](/help/forms/using/themes.md)
* [Intégration de données ](/help/forms/using/data-integration.md)
* [Utilisation d’Acrobat Sign dans les formulaires adaptatifs](/help/forms/using/working-with-adobe-sign.md)
* [Processus basé sur l’utilisation de Forms sur OSGi](/help/forms/using/aem-forms-workflow.md)

#### Démonstration {#see-it-yourself-12}

Cliquez sur **Appliquer maintenant** dans la newsletter que vous avez reçue par courrier électronique. Vous pouvez également accéder à `https://[publishHost]:[publishPort]/content/we-finance/global/en/all-forms.html` et cliquez sur **[!UICONTROL Appliquer]** sur la demande d’assurance. Spécifier `123456789` dans le champ Numéro de sécurité sociale . Lorsque vous y êtes invité, connectez-vous à l’aide de `srose/srose` comme nom d’utilisateur/mot de passe.

Renseignez les détails, explorez divers composants de formulaire adaptatif et envoyez la demande. Vous pouvez consulter le formulaire adaptatif à l’adresse `https://[authorHost]:[authorPort]/editor.html/content/forms/af/we-finance/insurance/application-for-insurance.html`.

### We.Finance approuve la demande et un contrat est signé {#we-finance-approves-the-application-and-a-contract-is-signed}

We.Finance reçoit la demande d’assurance habitation envoyée par Sarah. Une tâche est assignée à Gloria Rios. Elle examine la demande dans sa boîte de réception AEM et l’approuve.

![insurance-inbox-grios](assets/insurance-inbox-grios.png)

Lorsque Gloria approuve la demande d’assurance habitation de Sarah, une tâche est créée dans la boîte de réception AEM de Frank De Costa. Frank examine la tâche. Il prépare un contrat de police d’assurance habitation pour Sarah, joint le contrat à sa demande et l’envoie à Sarah pour qu’elle signe le contrat. Le contrat, affiché ci-dessous dans l’interface utilisateur de l’agent, est la version d’impression de la communication interactive.

![insurance-contact-letter](assets/insurance-contact-letter.png)

Sarah reçoit un courrier électronique contenant un lien vers le contrat de police d’assurance habitation pour signature. Sarah examine et signe le contrat.

![assurance-contrat-email](assets/insurance-contract-email.png)

#### Fonctionnement {#how-it-works-16}

Lorsque Sarah envoie la demande d’assurance habitation, un Forms Workflow se déclenche et une tâche est créée dans la boîte de AEM de Gloria. Lorsque Gloria examine la demande et l’approuve, la tâche est assignée à Frank De Costa. Le flux des tâches d’une personne à une autre est défini dans le workflow AEM associé à la demande d’assurance. Pour plus d’informations sur les workflows, voir [Processus centré sur Forms sur OSGi](/help/forms/using/aem-forms-workflow.md).

L’image suivante illustre le workflow d’AEM associé à la demande d’assurance.

![we-finance-insurance-workflow-model](assets/we-finance-insurance-workflow-model.png)

Frank utilise Correspondence Management pour préparer un contrat de police d’assurance habitation. Il télécharge le PDF du contrat et le joint à la demande de Sarah, puis clique sur Envoyer le contrat. Le processus déclenche la signature d’un contrat d’assurance habitation pour un courrier électronique envoyé à Sarah.

#### Démonstration {#see-it-yourself-13}

Procédez comme suit :

1. Accédez à AEM boîte de réception, `https://[publishHost]:[publishPort]/content/we-finance/global/en/login.html?resource=/aem/inbox.html`et connectez-vous avec `grios/grios` comme mot de passe du nom d’utilisateur pour le personnage de Gloria. Approuvez la tâche pour la demande d’assurance habitation de Sarah.

1. Ensuite, connectez-vous à AEM boîte de réception avec `fdcosta/password` comme mot de passe du nom d&#39;utilisateur pour le personnage de Frank. Afficher la tâche.
1. Maintenant, accédez à `https://[authorHost]:[authorPort]/aem/forms.html/content/dam/formsanddocuments/we-finance/insurance` et prévisualisez le modèle de lettre pour HomeInsuranceWelcomeKit.
1. Renseignez les informations du panneau Données. Cliquez sur **[!UICONTROL Aperçu]** puis téléchargez le PDF sur votre système de fichiers local. Assurez-vous que le fichier du PDF est enregistré avec le nom de fichier contrat.pdf.
1. Accédez à la boîte de réception d’AEM de Frank, ouvrez la tâche, joignez le PDF de contrat téléchargé, puis cliquez sur **[!UICONTROL Envoyer le contrat]**.
1. Ouvrez l’email avec le contrat et signez le document.

### Sarah reçoit un kit de bienvenue {#sarah-receives-a-welcome-kit}

Lorsque Sarah signe le contrat d’assurance habitation, elle reçoit un courrier électronique contenant les détails de la police.

![insurance-policy-details](assets/insurance-policy-details.png)

Peu de temps après, elle reçoit un autre courrier électronique de We.Finance avec un kit de bienvenue pour sa police d’assurance. À partir du kit de bienvenue, Sarah peut accéder à ses documents de stratégie et afficher ses instructions.

![insurance-welcome-kit](assets/insurance-welcome-kit.png)

#### Démonstration {#see-it-yourself-14}

Si vous avez spécifié votre ID de courrier électronique dans la demande, vous avez reçu un courrier électronique contenant un lien vers le kit de bienvenue. Cliquez sur **[!UICONTROL Mon kit de bienvenue]** pour ouvrir le kit de bienvenue.

![insurance-welcome-kit-email](assets/insurance-welcome-kit-email.png)

## Présentation du prospectus de gestion de la richesse {#wealth-management-prospectus-walkthrough}

Le scénario de gestion de la richesse We.Finance implique le personnage suivant :

* Sarah Rose, une cliente de We.Finance

La présentation de la gestion de la richesse montre comment un client de We.Finance peut utiliser le site pour en savoir plus sur un fonds mutuel, le Blue Chip Growth Fund. Le site de référence utilise une communication interactive pour afficher des informations sur le fonds. Les informations sont disponibles en format web et PDF. La présentation se termine par un message électronique du client à son frère de la version PDF de l’information.

L’image suivante affiche le workflow de la présentation de la gestion de la richesse :

![gestion de patrimoine-prospectus-walkthrough](assets/wealth-management-prospectus-walkthrough.png)

### Sarah visite le site Web de We.Finance et ouvre le prospectus Blue Chip Growth Fund {#sarah-visits-we-finance-website-and-opens-the-blue-chip-growth-fund-prospectus}

Sarah Rose prévoit d’investir dans un fonds mutuel. Elle est déjà cliente de We.Finance et se rend donc sur le portail We.Finance pour explorer les fonds communs de placement disponibles. Elle accède à la section Gestion de la richesse et ouvre la page We.Finance Blue Chip Growth Fund . La page contient des liens vers les prospectus qui contiennent des informations détaillées sur les prix actuels et historiques, les performances mensuelles, la diversification par secteur, les dépenses, les émoluments, la taxe et plus d’informations sur les fonds.

![slide1](assets/slide1.png)

#### Fonctionnement {#how-it-works-17}

Le prospectus Blue Chip Growth Fund est une communication interactive. Il utilise des textes, des images, des graphiques et des composants de tableau (fragments de document) pour afficher la synthèse du produit, le style du stock, les performances du fonds, les détails du fonds et d’autres informations connexes. Vous pouvez consulter la communication interactive en mode d’édition à l’adresse https://[authorHost]:[ authorPort]/editor.html/content/forms/af/we-finance/wealth-management/wealth-management/channels/web.html

Les graphiques et les tableaux récupèrent les données d’un modèle de données de formulaire. Le modèle de données de formulaire se connecte à des sources de données configurées, une base de données dans cette présentation détaillée, pour récupérer des informations spécifiques au fonds. Vous pouvez consulter le modèle de données de formulaire à l’adresse https://[authorHost]:[authorPort]/aem/fdm/editor.html/content/dam/formsanddocuments-fdm/we-finance/rich-management

#### Démonstration  {#see-it-yourself-15}

Accédez au portail We.Finance à l’adresse https://[publishHost]:[publishPort]/wefinance, appuyez sur Gestion de la richesse, développez Fonds par classe d’actifs, puis appuyez sur We.Finance Blue Chip Growth Fund. Le prospectus We.Finance Blue Chip Growth Fund s&#39;ouvre.

### Sarah explore le prospectus du Blue Chip Growth Fund pour en savoir plus sur le fonds {#sarah-explores-the-blue-chip-growth-fund-prospectus-to-learn-about-the-fund}

Sarah explore les onglets Aperçu, Prix et Performance, Gestion des Portfolios, Frais et minimum, Impôts et Paiement du prospectus pour découvrir les prix actuels et historiques, la croissance historique, la comparaison avec l’indice S&amp;P 500, la diversification par secteur, les personnes gérant le fonds et les dépenses liées au fonds. Les informations associées sont réparties dans différents onglets. Le prospectus est une communication interactive. Les communications interactives ont un design réactif. Elle peut ouvrir la communication interactive sur un appareil de n’importe quelle taille d’écran, et la communication interactive la redistribue pour l’adapter à l’appareil sous-jacent.

![diapositive1-1](assets/slide1-1.png)

#### Fonctionnement {#how-it-works-18}

La communication interactive du Blue Chip Growth Fund utilise des panneaux parents et enfants pour séparer les informations associées en différentes sections. Le panneau parent classe tous les panneaux enfants dans des onglets.

La mise en page de l’onglet parent est définie sur Onglets en haut pour convertir tous les panneaux enfants en onglets. Vous pouvez consulter les panneaux de la communication interactive en mode d’édition à l’adresse https://[authorHost]:[ authorPort]/editor.html/content/forms/af/we-finance/wealth-management/wealth-management/channels/web.html.

#### Démonstration  {#see-it-yourself-16}

Accédez à la communication interactive du Blue Chip Growth Fund à l’adresse https://[publishHost]:[ publishPort]/content/forms/af/we-finance/wealth-management/wealth-management/channels/web.html?wcmmode=disabled Explorez tous les onglets.

### Sarah consulte et envoie par courrier électronique la version PDF de la page Blue Chip Growth Fund . {#sarah-views-and-emails-the-pdf-version-of-the-blue-chip-growth-fund-page}

Sarah voyage à la campagne le week-end. Elle prévoit de discuter du Blue Chip Growth Fund avec son frère aîné. Son frère aîné travaille avec une banque et l&#39;aide dans les décisions liées à la finance. Sarah télécharge une copie de la version PDF de la page Blue Chip Growth Fund sur son ordinateur portable pour une lecture hors ligne. Elle envoie également par courrier électronique une copie de la version PDF à son frère.

![blue-chip-pdf](assets/blue-chip-pdf.gif)

#### Fonctionnement {#how-it-works-19}

Le prospectus Blue Chip Growth Fund est une communication interactive. Il dispose d’un canal web et PDF. La communication interactive s’intègre aux processus AEM pour envoyer la version du PDF par courrier électronique. Vous pouvez consulter le modèle de processus à l’adresse https://[authorHost]:[ authorPort]/editor.html/conf/global/settings/workflow/models/wealthmanagement.html.

![gestion de la richesse](assets/wealth-management.png)

#### Démonstration  {#see-it-yourself-17}

Pour télécharger la version PDF, consultez la communication interactive du Blue Chip Growth Fund https://[publishHost]:[ publishPort]/content/forms/af/we-finance/wealth-management/wealth-management/channels/web.html, appuyez sur Télécharger le PDF.

Pour envoyer un PDF par e-mail, consultez la communication interactive du Blue Chip Growth Fund https://[publishHost]:[ publishPort]/content/forms/af/we-finance/wealth-management/wealth-management/channels/web.html, appuyez sur PDF EMAIL. Spécifier **Nom complet** et **Adresse électronique**. Cliquez sur **Envoyer un courrier électronique**.

## Présentation de la demande d’assurance automobile {#auto-insurance-application-walkthrough}

Le scénario de demande d’assurance automobile We.Finance implique le personnage suivant :

* Sarah Rose, une cliente de We.Finance
* Conrad Simms, agent d’assurance, We.Finance

Sarah Rose est déjà cliente chez We.Finance et a acheté une police d’assurance automobile. Elle doit renouveler sa police d’assurance aujourd’hui. Conrad Simms, agent d’assurance, We.Finance envoie un rappel à Sarah au sujet du renouvellement de sa police. L’e-mail de rappel contient un PDF contenant les détails du renouvellement de la stratégie et un lien vers la version web de la communication interactive. Les communications interactives ont une conception adaptée aux mobiles et réactive. Elle peut ouvrir la communication interactive sur n’importe quel appareil et la communication interactive se transforme en taille d’écran de l’appareil sous-jacent. La version PDF de la communication interactive, jointe à un email, est utile pour la lecture hors ligne.

Sarah suit les instructions fournies dans le courrier électronique et réussit à renouveler le processus. L’image suivante affiche le workflow de la présentation de la demande d’assurance automobile :  ![auto-insurance-application-walkthrough](assets/auto-insurance-application-walkthrough.png)

### Conrad envoie une communication de renouvellement de police d’assurance à We.Finance {#conrad-sends-an-insurance-policy-renewal-communication-from-we-finance}

Conrad se connecte à l’instance AEM, ouvre le tableau de bord Assurance automobile et spécifie le de Sarah **ID de client**, et clics **Renouveler la stratégie**. Le **Interface utilisateur de l’agent** s’ouvre avec les informations de stratégie de Sarah Rose déjà renseignées. Conrad Adresse électronique spécifiée de Sarah et clics **Envoyer**. Sarah reçoit un courrier électronique avec l’objet **Votre renouvellement d’assurance automobile**.

![cc-dashboard](assets/cc-dashboard.png)

#### Fonctionnement {#how-it-works-20}

La communication sur le renouvellement des polices d’assurance est une communication interactive. Conrad Simms utilise l’interface utilisateur de l’agent pour envoyer la communication de renouvellement de police d’assurance à Sarah. La communication comprend l’impression (PDF) et le lien vers le canal web de la communication interactive. La communication interactive utilise AEM Workflow pour envoyer l’email. Vous pouvez voir le workflow à l’adresse https://[authorHost]:[ authorPort]/editor.html/conf/global/settings/workflow/models/we-finance-auto-insurance-renewal.html

![auto-assurance-workflow](assets/auto-insurance-workflow.png)

#### Démonstration  {#see-it-yourself-18}

Connectez-vous à **Tableau de bord des assurances automatiques We.Finance** comme Conrad Simms (csimms/password). L’URL est https://[publishhost]:[publishport]/content/we-finance/global/en/login.html?resource=/content/we-finance/ccdashboard.html. Spécifiez la variable **ID de client**. L’ID de client de Sarah Rose est 900001. Cliquez sur **Renouveler la stratégie**. La communication interactive s’ouvre dans l’interface utilisateur de l’agent. Dans l’interface utilisateur de l’agent, saisissez une adresse électronique valide pour envoyer le courrier électronique avec le document de stratégie joint, puis cliquez sur **Envoyer**. Un message, Envoi commencé, s’affiche à l’écran, puis, en quelques secondes, un autre message, Envoyé avec succès, s’affiche. Un email avec l’objet **Votre renouvellement d’assurance automobile** et est envoyé à l’adresse électronique spécifiée. La politique proposée à Sarah Rose est une politique privilégiée.

La présentation de l&#39;assurance automobile contient également un autre client, Alison Jones. L’ID de client d’Alison Jones est 900002. Lorsque vous envoyez la communication interactive à Alison Jones, une stratégie standard est envoyée. La différence entre les stratégies standard et premium est la suivante :

* La stratégie premium comporte une image de bannière et la stratégie standard ne contient que du texte sous le bloc d’adresse.
* La politique standard coûte moins cher que la politique de primes.
* La politique premium comporte une récompense anti-vol et la politique standard une récompense intelligente.

Les deux stratégies utilisent la même communication interactive. Les sections de la stratégie sont modifiées ou masquées en fonction de la condition de type de stratégie. Vous pouvez accéder à la communication interactive de renouvellement d’assurance automobile et la consulter directement à partir de `https://[authorHost]: [authorPort]/aem/formdetails.html/content/dam/formsanddocuments/we-finance/autoinsurance/auto-insurance-renewal`

**Utilisation de Microsoft Dynamics comme source de données**

Le site de référence fournit également une communication interactive qui utilise Microsoft Dynamics comme source de données pour le modèle de données de formulaire. Effectuez les étapes suivantes pour configurer la communication interactive pour la présentation de l’assurance automobile :

1. Connectez-vous à https://[author]:[port]/crx/de en tant qu’administrateur.
1. Ouvrez le fichier `/apps/we-finance/components/ccrui/ccrui.jsp`.
1. Définissez la valeur de `FormFieldRequestParameter`to `/content/dam/formsanddocuments/we-finance/autoinsurance/auto-insurance-renewal-dynamics`
1. Appuyez sur **Enregistrer tout**. Le site de référence est configuré pour utiliser la communication interactive qui utilise MS Dynamics comme source de données.

Maintenant, connectez-vous à **Tableau de bord des assurances automatiques We.Finance** comme Conrad Simms (csimms/password). L’URL est https://[publishhost]:[publishport]/content/we-finance/global/en/login.html?resource=/content/we-finance/ccdashboard.html. Spécifiez la variable **ID de client**. L’ID de client de Sarah Rose est 900001. Cliquez sur **Renouveler la stratégie**. La communication interactive s’ouvre dans l’interface utilisateur de l’agent. Dans l’interface utilisateur de l’agent, saisissez une adresse électronique valide pour envoyer le courrier électronique avec le document de stratégie joint, puis cliquez sur **Envoyer**. Un message, Envoi commencé, s’affiche à l’écran, puis, en quelques secondes, un autre message, Envoyé avec succès, s’affiche. Un email avec l’objet **Votre renouvellement d’assurance automobile** est envoyé à l’adresse électronique spécifiée.

>[!NOTE]
>
>Lorsque vous utilisez la communication interactive qui utilise Microsoft Dynamics comme source de données, les liens contenus dans les courriers électroniques envoyés à Sarah pointent vers la communication interactive qui n’utilise pas Microsoft Dynamics. Pour résoudre ce problème, modifiez manuellement les liens dans les modèles de courrier électronique.

![agent_ui_email-1](assets/agent_ui_email-1.png)

### Sarah reçoit une notification de renouvellement de police d’assurance de We.Finance et décide d’effectuer le renouvellement. {#sarah-receives-an-insurance-policy-renewal-communication-from-we-finance-and-decides-to-renew}

Sarah reçoit un courrier électronique avec une pièce jointe de We.Finance qui lui rappelle que sa police d’assurance automobile est sur le point d’expirer. La pièce jointe est la version imprimée des détails de renouvellement de sa police d’assurance automobile.

Sarah clique **Renouveler maintenant** et est dirigé vers la version web de sa lettre d’assurance automobile. En plus de cette lettre, Sarah trouve un certain nombre de jours restants pour l’expiration de sa politique. La page fournit à Sarah un aperçu des détails de sa police d’assurance, tels que le numéro de la police, le montant dû et d’autres informations, telles que les offres de remise et les récompenses de fidélité. Sarah clique à nouveau sur **Renouveler maintenant** au bas de la police.

![auto-assurance-renouvellement-email](assets/auto-insurance-renewal-email.png)

#### Fonctionnement  {#how-it-works-21}

Les sorties web et imprimée de votre lettre d’assurance automobile sont créées à l’aide des fonctionnalités multicanaux des communications interactives. Le **Renouveler maintenant** dans l’email est lié à la demande de renouvellement d’assurance automobile, qui est une communication interactive sur une instance de publication.

![ic-web-version](assets/ic-web-version.png)

#### Démonstration  {#see-it-yourself-19}

Vous avez dû recevoir un email avec un PDF joint. Le PDF est une version imprimée de votre lettre d’assurance automobile. Cliquez sur **Renouveler maintenant** pour accéder à la version web de la police. Vérifiez vos informations personnelles et vos informations de stratégie, puis cliquez sur **Renouveler maintenant**. Il vous amène à un formulaire adaptatif pour paiement.

Le bouton **Renouveler maintenant** figurant dans l’e-mail redirige Sarah vers la version web de la police. Vous pouvez consulter l’URL suivante :

https://[publishServer]:[publishPort]/content/document.html?schema=fdm&amp;documentId=/content/forms/af/we-finance/autoinsurance/auto-insurance-renewal/channels/web.html&amp;customerId=900001

Vous pouvez vérifier le résumé détaillé de votre renouvellement d’assurance automobile, puis cliquer sur **Renouveler maintenant** au bas de la page.

### Sarah ouvre la page de paiement, effectue le paiement et termine le processus {#sarah-opens-the-payment-page-and-makes-the-payment-and-completes-the-process}

Lorsque Sarah clique **Renouveler maintenant** dans la version web de la communication interactive, la page paiements s’ouvre. Sarah vérifie à nouveau son numéro de police et la date d’expiration dans ses dossiers. Sur le côté droit de la page, elle vérifie le récapitulatif des paiements de son renouvellement avec une réduction de 10 % sur le montant total. Sarah remplit ses informations de carte de crédit et clique sur **Effectuer un paiement**.

![payment-adaptive-form](assets/payment-adaptive-form.png)

#### Fonctionnement  {#how-it-works-22}

Le bouton Renouveler maintenant redirige Sarah vers la page de paiement. La page de paiement est un formulaire adaptatif. Sarah remplit les détails de la carte de crédit et clique **Envoyer**. Son paiement par carte de crédit est traité et un message de remerciement configuré dans le formulaire adaptatif s’affiche à l’écran.

#### Démonstration  {#see-it-yourself-20}

Cliquez sur **Renouveler maintenant** pour accéder à la page de paiement. Saisissez vos informations de carte de crédit, puis cliquez sur **Effectuer un paiement.** Vous pouvez accéder à la page de paiement dans l’instance de création à l’adresse :

https://[authorServer]:[authorPort]/content/document.html?documentId=/content/forms/af/we-finance/credit-card/ccbillpayment.html&amp;schema=fdm&amp;customerId=900001

Le message de remerciement s’affiche une fois que vous avez cliqué sur le bouton Effectuer un paiement .
