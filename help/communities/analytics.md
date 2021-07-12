---
title: Configuration d’Analytics pour les fonctionnalités des communautés
seo-title: Configuration d’Analytics pour les fonctionnalités des communautés
description: Configuration d’Analytics pour Communities
seo-description: Configuration d’Analytics pour Communities
uuid: 625a253f-b198-40e8-b34c-dff337fb0eff
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 36ea97a4-4e13-4e89-866b-495f3c30cb94
role: Admin
exl-id: cb2f61df-73bb-47f7-86ce-feda4772c8d0
source-git-commit: 3c050c33a384d586d74bd641f7622989dc1d6b22
workflow-type: tm+mt
source-wordcount: '2787'
ht-degree: 5%

---

# Configuration d’Analytics pour les fonctionnalités des communautés {#analytics-configuration-for-communities-features}

## Présentation {#overview}

Adobe Analytics et Adobe Experience Manager (AEM) sont les deux solutions de Adobe Marketing Cloud.

Adobe Analytics peut être configuré pour AEM Communities afin que, lorsqu’un membre interagit avec les fonctionnalités de communauté prises en charge, des événements soient envoyés à Adobe Analytics à partir duquel des rapports sont générés.

Par exemple, lorsqu’un membre d’un site de communauté d’activation affiche une ressource vidéo qui lui est attribuée, le lecteur de ressources envoie des événements à Analytics, y compris des données de pulsation vidéo. Sur le site de la communauté, les administrateurs peuvent consulter divers rapports concernant la lecture de la vidéo.

En outre, les analyses sont nécessaires pour :

* Dans l’environnement de publication :

   * Reporting sur la communauté [tendances](trends.md)
   * Autoriser les visiteurs du site à trier par &quot;le plus consulté&quot;, &quot;le plus principal&quot;, &quot;le plus apprécié&quot;
   * Affichage du nombre de listes UGC

* Dans l’environnement de création :

   * Affichage des données de participation dans la [console de gestion des membres](members.md) (vues, publications, mentions &quot;J’aime&quot;)
   * Synthèse des tendances, pulsation vidéo et périphérique vidéo pour la ressource d’activation [rapports](reports.md)

Fonctionnalités de communautés prises en charge :

* [Ressources d’activation](resources.md)
* [Forum](forum.md)
* [Q&amp;R](working-with-qna.md)
* [Blog](blog-feature.md)
* [Bibliothèque de fichiers](file-library.md)
* [Calendrier](calendar.md)

Cette section de la documentation décrit comment connecter une suite de rapports Analytics aux fonctionnalités de Communities. Les étapes de base sont les suivantes :

1. [Répliquez la ](#replicate-the-crypto-key) clé de chiffrement pour vous assurer que le cryptage/décryptage se produit correctement sur toutes les instances AEM
1. Préparation d’une [suite de rapports Adobe Analytics](#adobe-analytics-report-suite-for-video-reporting)
1. Créez un [service cloud d’AEM ](#aem-analytics-cloud-service-configuration) et [framework](#aem-analytics-framework-configuration)
1. [Activation ](#enable-analytics-for-a-community-site) d’Analytics pour un site de communauté
1. [](#verify-analytics-to-aem-variable-mapping) Vérifier Analytics pour AEM mappage des variables
1. Identifier [l’éditeur Principal](#primary-publisher)
1. [](#publish-community-site-and-analytics-cloud-service) Publier le site de la communauté
1. Configurer [l’importation des données de rapport](#obtaining-reports-from-analytics) d’Adobe Analytics vers le site de la communauté

## Prérequis {#prerequisites}

Pour configurer les fonctionnalités Analytics for Communities, il est nécessaire de travailler avec le gestionnaire de compte pour configurer un compte Adobe Analytics et une [suite de rapports](#adobe-analytics-report-suite-for-video-reporting). Une fois établies, les informations suivantes doivent être disponibles :

* Nom de l’entreprise

   Société associée au compte Adobe Analytics
* Nom d’utilisateur

   Nom d’utilisateur de connexion de l’utilisateur autorisé à gérer le compte Analytics.

   (Doit inclure des privilèges d’accès aux services web)

* Mot de passe

   Mot de passe de connexion de l’utilisateur autorisé

* Centre de données Analytics

   URL du centre de données Analytics pour le compte

* Suite de rapports

   Nom de la suite de rapports Analytics à utiliser

## Suite de rapports Adobe Analytics pour les rapports vidéo {#adobe-analytics-report-suite-for-video-reporting}

À l’aide du [Gestionnaire de suites de rapports d’Adobe Marketing Cloud](https://docs.adobe.com/content/help/en/analytics/admin/manage-report-suites/new-report-suite/new-report-suite.html), les suites de rapports Analytics peuvent être configurées de sorte qu’un site de communauté puisse être activé afin de fournir des rapports pour les fonctionnalités de communauté.

En se connectant à [Adobe Marketing Cloud](https://docs.adobe.com/content/help/en/analytics/analyze/analysis-workspace/home.html) avec [Nom de société et Nom d’utilisateur](analytics.md#prerequisites), il est possible de configurer une suite de rapports nouvelle ou existante pour que :

* [11 variables de conversion](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/conversion-variables/conversion-var-admin.html)  (evars)

   * **`evar1`** par  **`evar11`** activation
   * Peut réutiliser (renommer) des eVars existantes ou en créer de nouvelles à utiliser pour les fonctionnalités de communauté

* [7 événements de succès](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/success-events/success-event.html)  (événements)

   * **`event1`** par  **`event7`** activation
   * Type **`Counter`**

      * not **`Counter (no subrelations)`**
   * Peut réutiliser (renommer) des événements existants ou en créer de nouveaux à utiliser pour les fonctionnalités de communauté


* [Gestion des vidéos](https://docs.adobe.com/content/help/en/media-analytics/using/media-overview.html)

   * Console Rapports vidéo

      * Activer `Video Core`
      * Sélectionnez Enregistrer
   * Console de mesures coeur de la vidéo

      * Sélectionner `Use Solution Variables`
      * Sélectionnez Enregistrer


Si vous utilisez une **nouvelle suite de rapports**, sachez qu’une nouvelle suite de rapports ne peut comporter que 4 eVars et 6 variables d’événements, tandis que 11 eVar et 7 variables d’événements sont requises pour Communities.

Si vous utilisez une **suite de rapports** existante, il peut être nécessaire de [modifier le mappage de variables](#modifying-analytics-variable-mapping) avant d’activer la structure Analytics pour un site de communauté. Contactez le représentant de votre compte pour toute question concernant les variables dédiées aux communautés.

>[!CAUTION]
>
>**Si vous utilisez une suite de rapports existante qui utilise déjà des variables dans**
>
>* **`evar1`** à **`evar11`**
>* **`event1`** à **`event7`**

>
>
**Ensuite, avant que le site de la communauté ne soit publié,** il est important de restaurer le mappage préexistant en déplaçant les variables AEM automatiquement mises en correspondance avec les variables Analytics lorsque Analytics a été activé pour un site de la communauté.
>
>Pour restaurer le mappage préexistant et déplacer AEM variables vers d’autres variables Analytics, reportez-vous à la section [Modification du mappage de variables Analytics](#modifying-analytics-variable-mapping).
>
>Si vous ne le faites pas, il se peut qu’il y ait une perte de données irrécupérable.

### Video Heartbeat Analytics {#video-heartbeat-analytics}

Lorsque Video Heartbeat Analytics est sous licence, une `Marketing Cloud Org Id` est affectée.

Pour activer la création de rapports Video Heartbeat après avoir [configuré la suite de rapports Analytics pour la création de rapports vidéo](#adobe-analytics-report-suite-for-video-reporting) :

* Créer un [service cloud Analytics](#aem-analytics-cloud-service-configuration)
* Activez [Analytics pour un site communautaire](#enable-analytics-for-a-community-site)
* Associez le `Marketing Cloud Org Id` au site de la communauté.

La balise `Marketing Cloud Org Id` peut être saisie au moment de la [création du site de la communauté](sites-console.md#enablement) ou ultérieurement par [modification](sites-console.md#modifying-site-properties) des propriétés du site de la communauté. [](#aem-analytics-cloud-service-configuration)

![chlimage_1-264](assets/chlimage_1-264.png)

Lorsque l’analyse de pulsation vidéo est activée, le code JavaScript (JS) du lecteur vidéo instancie le code de bibliothèque de pulsation vidéo (également dans JS) qui gère toute la logique d’envoi de mises à jour d’état vidéo aux serveurs de suivi vidéo Analytics toutes les 10 secondes (non configurables) et éventuellement l’envoi d’un rapport cumulatif de la session vidéo aux serveurs Analytics principaux.

Si cette option n’est pas activée, le code de pulsation vidéo n’est jamais instancié et seul le suivi de progression et de reprise de la vidéo est conservé à la SRP pour la création de rapports.

## Configuration du service Analytics Cloud AEM {#aem-analytics-cloud-service-configuration}

Pour créer une intégration Analytics, qui intègre Adobe Analytics au site de la communauté AEM, à l’aide de l’interface utilisateur standard sur l’instance de création :

* À partir de la navigation globale : **[!UICONTROL Outils > Déploiement > Cloud Services]**
* Faites défiler l’écran jusqu’à **[!UICONTROL Adobe Analytics]**
* Sélectionnez **[!UICONTROL Configurer maintenant]** ou **[!UICONTROL Afficher les configurations]** .

![chlimage_1-265](assets/chlimage_1-265.png)

### Boîte de dialogue Créer une configuration {#create-configuration-dialog}

* Cliquez sur `[+]` icône en regard de **[!UICONTROL Configurations disponibles]** pour créer une configuration.

Dans la boîte de dialogue Créer une configuration , les valeurs à renseigner identifient la configuration.

![chlimage_1-266](assets/chlimage_1-266.png)

* **[!UICONTROL Titre]**

   (Obligatoire) Titre affiché de la configuration.

   Par exemple, saisissez *Activation Community Analytics*

* **[!UICONTROL Name]** (Nom)

   (Facultatif) S’il n’est pas spécifié, le nom est défini par défaut sur un nom de noeud valide dérivé du titre.

   Par exemple, saisissez *communities*


* **[!UICONTROL Modèle]**

   Sélectionner `Adobe Analytics Configuration`

* Sélectionnez **[!UICONTROL Créer]**
   * Lance la page de configuration et ouvre la boîte de dialogue `Analytics Settings`

### Boîte de dialogue de paramètres Analytics {#analytics-settings-dialog}

La création initiale d’une nouvelle configuration Analytics entraîne l’affichage de la configuration et une nouvelle boîte de dialogue pour l’entrée des paramètres Analytics. Cette boîte de dialogue nécessite les [informations de compte prérequises](#prerequisites) obtenues auprès du représentant du compte.

![chlimage_1-267](assets/chlimage_1-267.png)

* **[!UICONTROL Société]**

   Société associée au compte Adobe Analytics

* **[!UICONTROL Nom d’utilisateur]**

   Nom d’utilisateur de connexion de l’utilisateur autorisé à gérer le compte Analytics.

* **[!UICONTROL Mot de passe]**

   Mot de passe de connexion de l’utilisateur autorisé

* **[!UICONTROL Centre de données]**

   Sélectionnez le centre de données Analytics hébergeant la suite de rapports.

* **[!UICONTROL Ne pas ajouter la balise de suivi sur la page]**

   Laissez comme valeur par défaut (non coché)

* **[!UICONTROL Utiliser AppMeasurement]**

   Laissez comme valeur par défaut (non coché)

* **[!UICONTROL Ne pas importer des impressions de page de nuit (auteur)]**

   Laissez comme valeur par défaut (non coché)

* **[!UICONTROL Ne pas importer des impressions de page de nuit (publication)]**

   Laissez comme valeur par défaut (coché)

Pour enregistrer les paramètres :


* Sélectionnez **[!UICONTROL Connexion à Analytics]**

   * En cas d’échec,

      * Vérifier que les entrées ne contiennent pas d’espaces
      * Tester un autre centre de données
      * Contacter le représentant de votre compte

* **[!UICONTROL Cliquez sur OK]**


![chlimage_1-268](assets/chlimage_1-268.png)

### Créer une structure {#create-framework}

Après une configuration réussie de la connexion de base à Adobe Analytics, il est nécessaire de créer ou de modifier une structure pour le site de la communauté. L’objectif de la structure est de mapper les variables de fonctionnalités (AEM) de communautés aux variables Analytics (suite de rapports).

* Cliquez sur `[+]` icône en regard de **[!UICONTROL Structures disponibles]** pour créer une nouvelle structure.

![chlimage_1-269](assets/chlimage_1-269.png)

* **[!UICONTROL Titre]**

   (Obligatoire) Titre affiché de la structure.

   Par exemple, saisissez *Enablement Community Framework*

* **[!UICONTROL Name]** (Nom)

   (Facultatif) S’il n’est pas spécifié, le nom est défini par défaut sur un nom de noeud valide dérivé du titre.

   Par exemple, saisissez *communities*

* **[!UICONTROL Modèle]**

   Sélectionner `Adobe Analytics Framework`

* Sélectionnez **[!UICONTROL Créer]**

La création de la structure Analytics ouvre la structure pour la configuration.

## Configuration de la structure d’AEM Analytics {#aem-analytics-framework-configuration}

L’objectif de la structure est de mapper AEM variables aux variables Analytics (evars et événements). Les variables Analytics disponibles pour le mappage sont [définies dans la suite de rapports](#adobe-analytics-report-suite-for-video-reporting).

![chlimage_1-270](assets/chlimage_1-270.png)

### Sélectionner une suite de rapports {#select-report-suite}

Sélectionnez la suite de rapports qui a été configurée pour la création de rapports vidéo.

Si une suite de rapports n’a pas encore été créée ou n’a pas été correctement configurée, reportez-vous à la section précédente :\
[Suite de rapports Adobe Analytics pour les rapports vidéo](#adobe-analytics-report-suite-for-video-reporting)

Le sidekick n’est pas nécessaire et peut être réduit afin de ne pas entraver l’accès aux paramètres des suites de rapports.

#### Boîte de dialogue Suites de rapports avant et après la sélection de l’option &quot;Ajouter un élément&quot; {#report-suites-dialog-before-and-after-selecting-add-item}

![chlimage_1-271](assets/chlimage_1-271.png)

1. Sélectionnez **[!UICONTROL Ajouter un élément +]** deux listes déroulantes s’affichent.
1. Choisissez une `Report suite` , les suites de rapports associées au compte de la société doivent pouvoir être sélectionnées.
1. Sélectionnez **[!UICONTROL Oui]** dans la boîte de dialogue qui s’ouvre : ```Load default server settings? Do you want to load the default server settings and overwrite current values in the Server section?```
1. Choisissez une balise `Run Mode`\
   Sélectionnez **[!UICONTROL publish]**

![chlimage_1-272](assets/chlimage_1-272.png)

Le service et la structure cloud Analytics sont désormais terminés. Les mappages seront définis une fois qu’un site de communauté a été créé avec ce service Analytics activé.

## Activation d’Analytics pour un site de la communauté {#enable-analytics-for-a-community-site}

### Activation pour le nouveau site de la communauté {#enable-for-new-community-site}

Pour ajouter le service cloud Analytics lors de la [création d’un site de communauté](sites-console.md) :


* À l’étape 3
* Sous l’onglet [ANALYTICS](sites-console.md#analytics) :

   * Cochez la case **[!UICONTROL Activer Analytics]** .
   * Choisissez la structure dans la liste déroulante

* Si vous le souhaitez, revenez à la configuration de la structure Analytics pour ajuster les mappages des variables.

### Activer pour le site de la communauté existant {#enable-for-existing-community-site}

Pour ajouter le service cloud Analytics à un [site communautaire existant](sites-console.md#modifying-site-properties) :


* Accédez à la console **[!UICONTROL Communautés > Sites]**
* Sélectionner l’icône Modifier le site du site de la communauté
* Sélection des PARAMÈTRES
* Dans la section Analytics :

   * Cochez la case **[!UICONTROL Activer Analytics]** .
   * Choisissez la structure dans la liste déroulante


* Si vous le souhaitez, revenez à la configuration de la structure Analytics pour ajuster les mappages des variables.

### Activation pour les sites personnalisés {#enable-for-customized-sites}

Pour que le suivi et l’importation Analytics fonctionnent correctement pour un site de communauté, un élément de page avec les attributs `scf-js-site-title` et  doit être présent. Un seul élément de ce type doit exister sur la page, comme c’est le cas dans un script `sitepage.hbs` non modifié pour un site communautaire. La valeur de `siteUrl` est extraite et envoyée à Adobe Analytics en tant que *chemin du site*.

```xml
# present in default sitepage.hbs
# only one scf-js-site-title class should be included
# this example sets it to be hidden as it serves no visual purpose
<div
    class="navbar-brand scf-js-site-title"
    href="{{siteUrl}}.html"
    style="visibility: hidden;"
>
</div>
```

Pour un **site de communauté personnalisé** qui chevauche le script `sitepage.hbs`, assurez-vous que l’élément est présent. La variable `siteUrl`est définie lors du rendu sur le serveur avant de servir au client.

Pour un **site d’AEM générique** qui comprend des composants Communities, mais qui n’est pas créé avec l’[assistant de création de site](sites-console.md), il est nécessaire d’ajouter l’élément . La valeur de href doit être le chemin d’accès au site. Par exemple, si le chemin du site est `/content/my/company/en`, utilisez :

```xml
<div
    class="navbar-brand scf-js-site-title"
    href="/content/my/company/en.html"
    style="visibility: hidden;"
>
</div>
```

## Fonctionnalités d’Analytics for Communities {#analytics-for-communities-features}

Analytics est automatiquement utilisé pour plusieurs fonctions de communauté.

La [configuration OSGi de l’environnement de création](../../help/sites-deploying/configuring-osgi.md), `AEM Communities Analytics Component Configuration`, fournit une liste des composants créés pour Analytics. Le mappage automatique des variables est déterminé par les composants répertoriés.

Si de nouveaux composants personnalisés créés sont créés et créés pour Analytics, ils doivent être ajoutés à cette liste de composants configurés.

### Configuration des composants {#component-configuration}

![chlimage_1-273](assets/chlimage_1-273.png)

Remarque : les composants `journal` sont utilisés pour mettre en oeuvre la fonction de blog.

### Analytics mappé sur AEM variables {#mapped-analytics-to-aem-variables}

Une fois le site de la communauté enregistré avec Analytics activé et la structure de configuration cloud sélectionnée, les variables AEM sont automatiquement mises en correspondance avec les evar et les événements Analytics, en commençant par evar1 et event1, respectivement, et en étant incrémentées de 1.

Si vous utilisez une suite de rapports existante qui a mappé l’une des variables d’evar1 à evar11 et event1 à event7, il sera nécessaire de [supprimer les variables AEM](#modifying-analytics-variable-mapping) et restaurer le mappage d’origine.

Voici un exemple de mappages par défaut après avoir suivi le [tutoriel de prise en main](getting-started-enablement.md) :

![chlimage_1-274](assets/chlimage_1-274.png)

#### Carte des eVars envoyées avec chaque événement {#map-of-evars-sent-with-each-event}

|  | Type de ressource d’activation | Titre du site | Type de fonction | Titre du groupe | Chemin d’accès du groupe | Type UGC | Titre UGC | Utilisateur (membre) | Chemin d’accès UGC | Chemin du site |
|------------------------|------------------------|-----------|--------------|------------|-----------|---------|----------|--------------|---------|----------|
|  | **eVar1** | **eVar2** | **eVar3** | **eVar4** | **eVar5** | **eVar6** | **eVar7** | **eVar8** | **eVar9** | **eVar10** |
| event1Resource Play | (une) | - | - | - | - | - | - | - | (i) | - |
| event2SCFView | (une) | (b) | (c) | (d) | (e) | (f) | (g) | (h) | (i) | (j) |
| event3SCFCreate (Post) | - | (b) | (c) | (d) | (e) | (f) | (g) | (h) | (i) | (j) |
| event4SCFFollow | - | (b) | (c) | (d) | (e) | (f) | (g) | (h) | (i) | (j) |
| event5SCFVoteUp | - | (b) | (c) | (d) | (e) | (f) | (g) | (h) | (i) | (j) |
| event6SCFVoteDown | - | (b) | (c) | (d) | (e) | (f) | (g) | (h) | (i) | (j) |
| event7SCFRate | - | (b) | (c) | (d) | (e) | (f) | (g) | (h) | (i) | (j) |

**Exemples de valeurs d’eVar :**

* [Type](https://www.iana.org/assignments/media-types) MIME : video/mp4
* [Titre](sites-console.md#step13asitetemplate) du site de la communauté : Communautés de Geometrixx
* [Nom](functions.md) de la fonction de communauté : Forum
* [Nom](creating-groups.md#creating-a-new-group) du groupe de la communauté : La randonnée
* Chemin d’accès au contenu du groupe de communautés : /content/sites/communities/en/groups/hiking
* [Type de ressource](essentials.md) du composant UGC : social/forum/components/hbs/topic
* Titre du composant UGC : Rubriques de randonnée
* Login (Authorizable Id) : aaron.mcdonald@mailinator.com
* Chemin SRP vers UGC : /content/usergenerated/asi/../forum/jmtz-topic3 ou *chemin du composant à suivre* : /content/sites/communities/en/jcr:content/content/Principal/forum
* Chemin d’accès au contenu du site de la communauté : /content/sites/community/en

### Modification du mappage des variables Analytics {#modifying-analytics-variable-mapping}

La mise en correspondance des eVars et événements Analytics avec les variables AEM est visible à partir de la configuration de la structure une fois Analytics activé pour un site de communauté.

Une fois Analytics activé et avant la publication du site de la communauté, le mappage peut être modifié dans la structure en faisant glisser l’eVar ou l’événement Analytics de votre choix depuis le rail de gauche et en le déposant sur la ligne correspondante dans le tableau de mappage.

Pour éviter les mappages en double, veillez à supprimer l’eVar ou l’événement Analytics remplacé de la ligne en la survolant et en sélectionnant le &quot;X&quot; qui apparaît à droite de l’élément de variable Analytics.

Si les eVars et événements de Communities remplacent les mappages qui existaient auparavant dans la suite de rapports, puis, pour éviter toute perte de données, affectez les variables d’AEM des fonctionnalités de Communities à d’autres eVars et/ou événements Analytics et restaurez les mappages d’origine.

>[!CAUTION]
>
>Il est important de procéder à une recodification avant que le site de la communauté soit [publié](#publishing-the-community-site) avec Analytics activé, faute de quoi il existe un risque de perte de données.

#### Exemple d’étape 1 : Déplacement d’Analytics evar14 dans la table de mappage {#example-step-dragging-analytics-evar-into-mapping-table}

![chlimage_1-275](assets/chlimage_1-275.png)

#### Exemple d’étape 2 : Sélectionner &quot;x&quot; pour supprimer evar11 remplacé {#example-step-selecting-x-to-remove-replaced-evar}

![chlimage_1-276](assets/chlimage_1-276.png)

#### Exemple d’étape 3 : AEM var eventdata.siteId mappé sur Analytics evar14 {#example-step-aem-var-eventdata-siteid-remapped-to-analytics-evar}

![chlimage_1-277](assets/chlimage_1-277.png)

## Publication du site de la communauté {#publishing-the-community-site}

### Vérification d’Analytics pour AEM mappage des variables {#verify-analytics-to-aem-variable-mapping}

Il est conseillé de vérifier le mappage des variables avant de publier le site de la communauté, qui publie également le service et la structure cloud Analytics.

Voir les sections :

* [Analytics mappé sur AEM variables](#mapped-analytics-to-aem-variables)
* [Modification du mappage des variables Analytics](#modifying-analytics-variable-mapping)

>[!CAUTION]
>
>**Si vous utilisez une suite de rapports existante qui utilise déjà des variables dans**
>
>* **`evar1`** à **`evar11`**
>* **`event1`** à **`event7`**

>
>
**Ensuite, avant que le site de la communauté ne soit publié,** il est important de restaurer le mappage préexistant et de déplacer les variables d’AEM des communautés qui ont été automatiquement mappées (lorsque Analytics a été activé pour le site de la communauté) vers d’autres variables Analytics. Ce remappage doit être cohérent dans tous les composants de Communities.
>
>Si vous ne le faites pas, il se peut qu’il y ait une perte de données irrécupérable.

### Éditeur Principal {#primary-publisher}

Lorsque le déploiement choisi est une [ferme de publication](topologies.md#tarmk-publish-farm), une instance de publication AEM doit être identifiée comme l’éditeur Principal pour interroger Adobe Analytics pour que les données de rapport puissent être écrites dans [SRP](working-with-srp.md).

Par défaut, la configuration OSGi `AEM Communities Publisher Configuration` identifie son instance de publication comme l’éditeur Principal, de sorte que toutes les instances de publication dans une batterie de publication s’identifient elles-mêmes comme l’instance Principale.

Par conséquent, il est nécessaire de modifier la configuration sur toutes les instances de publication secondaires pour décocher la case **Éditeur Principal** .

Pour obtenir des instructions spécifiques, reportez-vous à la section Principale de l’éditeur de [Déploiement de communautés](deploy-communities.md#primary-publisher).

>[!CAUTION]
>
>Il est important que l’éditeur Principal soit configuré pour empêcher l’interrogation de plusieurs instances de publication.

### Réplication de la clé de chiffrement {#replicate-the-crypto-key}

Les informations d’identification Adobe Analytics sont chiffrées. Pour faciliter la réplication ou la transmission des informations d’identification d’analyse chiffrées entre l’auteur et les éditeurs, toutes les instances AEM doivent partager la même clé de chiffrement Principale.

Pour ce faire, suivez les instructions de la section [Répliquer la clé de chiffrement](deploy-communities.md#replicate-the-crypto-key).

### Publier le site de la communauté et le service Analytics Cloud {#publish-community-site-and-analytics-cloud-service}

Une fois que le service cloud Analytics a été activé pour un site de communauté et que, si nécessaire, le [mappage d’Analytics sur AEM variables a été adapté](#mapped-analytics-to-aem-variables), il est nécessaire de répliquer la configuration sur l’environnement de publication en [(re)publiant le site de la communauté](sites-console.md#publishing-the-site).

## Obtention de rapports à partir d’Analytics {#obtaining-reports-from-analytics}

### Gestion des rapports {#report-management}

La [configuration OSGi de l’auteur et Principal éditeur](../../help/sites-deploying/configuring-osgi.md), `AEM Communities Analytics Report Management`, est utilisée pour interroger Analytics.

Sur l’auteur, les requêtes concernent les rapports en temps réel.

Sur l’éditeur Principal, les requêtes sont utilisées pour fournir des informations en vue de l’importation des données Analytics de l’importateur de rapports.

L’intervalle de requête est défini par défaut sur 10 secondes.

### Importateur de rapports {#report-importer}

Une fois qu’un site de communauté activé Analytics a été publié, la [configuration OSGi ](../../help/sites-deploying/configuring-osgi.md) de l’éditeur Principal, `AEM Communities Analytics Report Importer`, peut être configurée pour définir l’intervalle d’interrogation par défaut pour les configurations qui ne sont pas configurées individuellement dans CRXDE.

L’intervalle d’interrogation contrôle la fréquence des demandes à Adobe Analytics pour que les données soient extraites et enregistrées dans [SRP](working-with-srp.md).

Lorsque les données peuvent être classées comme &quot;données massives&quot;, des sondages plus fréquents peuvent imposer une charge importante sur le site de la communauté.

L’interrogation par défaut **Intervalle d’importation** est définie sur 12 heures.

![chlimage_1-278](assets/chlimage_1-278.png)

### Personnalisation des rapports de composants {#component-report-customization}

Actuellement, pour personnaliser les mesures à suivre, les noeuds sont créés dans le référentiel qui définit des périodes pour lesquelles générer un rapport sur cette mesure.

Le sujet du forum est actuellement le seul exemple de cette personnalisation :

* Sur l’éditeur Principal
* Connexion avec droits d’administrateur
* Accédez à [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md)

   * Par exemple, [http://localhost:4503/crx/de](http://localhost:4503/crx/de)

* Sous le noeud `jcr:content` de la racine de langue

   * Par exemple, `/content/sites/engage/en/jcr:content`

* Accédez au composant configuré pour la création de rapports Analytics.

   * Par exemple, `analytics/reportConfigs/social_forum_components_hbs_topic`

* Remarquez les périodes créées.

   * `last30Days`
   * `last90Days`
   * `thisYear`

* Remarquez le noeud `total`.

   * La modification de la propriété `interval` remplace l’intervalle de l’importateur de rapports.
   * La valeur est en secondes et est définie sur 4 heures (1 400 secondes).

![chlimage_1-279](assets/chlimage_1-279.png)

## Gestion des données utilisateur dans Analytics {#manage-user-data-in-analytics}

Adobe Analytics fournit des API qui vous permettent d’accéder, d’exporter et de supprimer des données utilisateur. Pour plus d’informations, voir [Soumettre les demandes d’accès et de suppression](https://docs.adobe.com/content/help/en/analytics/admin/data-governance/gdpr-submit-access-delete.html).

## Ressources {#resources}

* Adobe Marketing Cloud : [Aide et référence d’Analytics](https://docs.adobe.com/content/help/en/analytics/landing/home.html)
* AEM : [Intégration à Adobe Analytics](../../help/sites-administering/adobeanalytics.md)
* AEM : [Analyses avec fournisseurs externes](../../help/sites-administering/external-providers.md)
