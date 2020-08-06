---
title: Fonctionnalités de configuration d’Analytics pour les communautés
seo-title: Fonctionnalités de configuration d’Analytics pour les communautés
description: Configuration des analyses pour les communautés
seo-description: Configuration des analyses pour les communautés
uuid: 625a253f-b198-40e8-b34c-dff337fb0eff
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 36ea97a4-4e13-4e89-866b-495f3c30cb94
translation-type: tm+mt
source-git-commit: 501a6c470113d249646f4424a19ee215a82b032d
workflow-type: tm+mt
source-wordcount: '2787'
ht-degree: 5%

---


# Fonctionnalités de configuration d’Analytics pour les communautés {#analytics-configuration-for-communities-features}

## Présentation {#overview}

Adobe Analytics et Adobe Experience Manager (AEM) sont deux solutions de Adobe Marketing Cloud.

Adobe Analytics peut être configuré pour AEM Communities de sorte que, lorsqu&#39;un membre interagit avec les fonctions de communautés prises en charge, des événements soient envoyés à Adobe Analytics à partir desquels les rapports sont générés.

Par exemple, lorsqu’un membre d’un site de communauté d’activation vue une ressource vidéo qui lui est affectée, le lecteur de ressources envoie des événements à Analytics, y compris des données de pulsation vidéo. Depuis le site communautaire, les administrateurs peuvent consulter divers rapports sur la lecture de la vidéo.

En outre, les analyses sont nécessaires pour :

* Dans l’environnement de publication :

   * Rapports sur les [tendances communautaires](trends.md)
   * Autoriser les visiteurs du site à trier en fonction des critères &quot;le plus vu&quot;, &quot;le plus principal&quot;, &quot;le plus aimé&quot;
   * Nombre de Vues sur les listes UGC

* Dans l&#39;environnement de l&#39;auteur :

   * Affichage des données de participation dans la console [de gestion des](members.md) membres (vues, publications, mentions J’aime, etc.)
   * Résumé des tendances, pulsation vidéo et périphérique vidéo pour les [rapports de ressources d’activation](reports.md)

Les fonctionnalités des communautés prises en charge sont les suivantes :

* [Ressources d&#39;activation](resources.md)
* [Forum](forum.md)
* [Q&amp;R](working-with-qna.md)
* [Blog](blog-feature.md)
* [Bibliothèque de fichiers](file-library.md)
* [Calendrier](calendar.md)

Cette section de la documentation décrit la connexion d’une suite de rapports Analytics aux fonctionnalités des communautés. Les étapes de base sont les suivantes :

1. [Répliquer la clé](#replicate-the-crypto-key) de chiffrement pour vérifier que le chiffrement/déchiffrement se produit correctement sur toutes les instances AEM
1. Préparation d’une suite de [rapports Adobe Analytics](#adobe-analytics-report-suite-for-video-reporting)
1. Création d’un service [et d’une](#aem-analytics-cloud-service-configuration) structure AEM Analytics [Cloud](#aem-analytics-framework-configuration)
1. [Activation d’Analytics](#enable-analytics-for-a-community-site) pour un site communautaire
1. [Vérifier](#verify-analytics-to-aem-variable-mapping) Analytics pour AEM mappage des variables
1. Identifier l&#39;éditeur [Principal](#primary-publisher)
1. [Publication](#publish-community-site-and-analytics-cloud-service) du site de la communauté
1. Configurer l&#39; [importation des données](#obtaining-reports-from-analytics) de rapport d&#39;Adobe Analytics vers le site de la communauté

## Conditions préalables {#prerequisites}

Pour configurer les fonctionnalités d’Analytics pour les communautés, vous devez travailler avec votre gestionnaire de compte pour configurer un compte Adobe Analytics et une suite [de](#adobe-analytics-report-suite-for-video-reporting)rapports. Une fois établies, les informations suivantes devraient être disponibles :

* Nom de la Société

   société associée au compte Adobe Analytics
* Nom d’utilisateur

   Nom d’utilisateur de connexion de l’utilisateur autorisé à gérer le compte Analytics.

   (Doit inclure les privilèges d’accès aux services Web)

* Mot de passe

   Mot de passe de connexion de l’utilisateur autorisé

* Centre de données Analytics

   URL du centre de données Analytics pour le compte

* Suite de rapports

   Nom de la suite de rapports Analytics à utiliser

## Report Suite Adobe Analytics pour le Rapports vidéo {#adobe-analytics-report-suite-for-video-reporting}

A l’aide du Gestionnaire [](https://docs.adobe.com/content/help/en/analytics/admin/manage-report-suites/new-report-suite/new-report-suite.html)de Report Suites d’Adobe Marketing Cloud, les suites de rapports Analytics peuvent être configurées de sorte qu’un site communautaire puisse être activé pour fournir des rapports pour les fonctionnalités des communautés.

En vous connectant à [Adobe Marketing Cloud](https://docs.adobe.com/content/help/en/analytics/analyze/analysis-workspace/home.html) avec le nom de [Société et le nom d’utilisateur](analytics.md#prerequisites), il est possible de configurer une suite de rapports nouvelle ou existante pour qu’elle dispose des éléments suivants :

* [11 Variables](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/conversion-variables/conversion-var-admin.html) de conversion (evars)

   * **`evar1`** par **`evar11`** activé
   * Peut réutiliser (renommer) des eVars existantes ou en créer de nouvelles à utiliser pour les fonctionnalités des communautés

* [7 Événements](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/success-events/success-event.html) de réussite (événements)

   * **`event1`** par **`event7`** activé
   * Type **`Counter`**

      * not **`Counter (no subrelations)`**
   * Peut réutiliser (renommer) des événements existants ou en créer de nouveaux à utiliser pour les fonctionnalités des communautés


* [Gestion des vidéos](https://docs.adobe.com/content/help/en/media-analytics/using/media-overview.html)

   * Console Rapports vidéo

      * Activer `Video Core`
      * Sélectionnez Enregistrer
   * Console de mesure coeur de la vidéo

      * Sélectionner `Use Solution Variables`
      * Sélectionnez Enregistrer


Si vous utilisez une **nouvelle suite** de rapports, sachez qu’une nouvelle suite de rapports ne peut comporter que 4 eVars et 6 variables de événement, tandis que 11 eVar et 7 variables de événement sont requises pour les communautés.

Si vous utilisez une suite **de rapports** existante, il peut être nécessaire de [modifier le mappage](#modifying-analytics-variable-mapping) des variables avant d’activer la structure Analytics pour un site communautaire. Contactez votre gestionnaire de compte pour toute question concernant les variables dédiées aux communautés.

>[!CAUTION]
>
>**Si vous utilisez une suite de rapports existante qui utilise déjà des variables dans**
>
>* **`evar1`** à **`evar11`**
>* **`event1`** à **`event7`**

>
>
**Avant la publication du site de la communauté,** il est important de restaurer la mise en correspondance existante en déplaçant les variables AEM qui étaient automatiquement mises en correspondance avec les variables Analytics lorsque Analytics était activé pour un site de la communauté.
>
>Pour restaurer le mappage préexistant et déplacer les variables AEM vers d’autres variables Analytics, voir la section sur la [modification du mappage](#modifying-analytics-variable-mapping)des variables Analytics.
>
>Si vous ne le faites pas, vous risquez de perdre des données irrécupérables.

### Analyses de pulsation vidéo {#video-heartbeat-analytics}

Lorsque la licence Video Heartbeat Analytics est concédée, une licence `Marketing Cloud Org Id` est attribuée.

Pour activer le rapports de pulsation vidéo après [la configuration de la suite de rapports Analytics pour le rapports](#adobe-analytics-report-suite-for-video-reporting)vidéo :

* Création d’un service [Analytics Cloud](#aem-analytics-cloud-service-configuration)
* Activation d’ [Analytics pour un site communautaire](#enable-analytics-for-a-community-site)
* Associer le site `Marketing Cloud Org Id` à la communauté

La `Marketing Cloud Org Id` valeur peut être saisie au moment de la création [d&#39;un site](sites-console.md#enablement) communautaire ou ultérieurement en [modifiant](sites-console.md#modifying-site-properties) les propriétés du site communautaire. [](#aem-analytics-cloud-service-configuration)

![chlimage_1-264](assets/chlimage_1-264.png)

Lorsque Video Heartbeat Analytics est activé, le code JavaScript (JS) du lecteur vidéo instancie le code de bibliothèque Video Heartbeat (également dans JS) qui gère toute la logique d’envoi de mises à jour d’état vidéo aux serveurs de suivi vidéo Analytics toutes les 10 secondes (non configurables) et, en fin de compte, envoie un rapport cumulatif de la session vidéo aux serveurs Analytics principaux.

Si elle n’est pas activée, le code de pulsation vidéo n’est jamais instancié et seul le suivi de la progression vidéo et de la reprise de la position est conservé à SRP pour rapports.

## Configuration du service Analytics Cloud AEM {#aem-analytics-cloud-service-configuration}

Pour créer une intégration Analytics, qui intègre Adobe Analytics au site de la communauté AEM, à l’aide de l’interface utilisateur standard de l’instance d’auteur :

* A partir de la navigation globale : **[!UICONTROL Outils > Déploiement > Cloud Services]**
* Scroll down to **[!UICONTROL Adobe Analytics]**
* Sélectionnez **[!UICONTROL Configurer maintenant]** ou **[!UICONTROL Afficher les configurations]**

![chlimage_1-265](assets/chlimage_1-265.png)

### Boîte de dialogue Créer une configuration {#create-configuration-dialog}

* Sélectionner `[+]` l&#39;icône en regard de Configurations **** disponibles pour créer une nouvelle configuration

Dans la boîte de dialogue Créer une configuration, les valeurs à saisir identifient la configuration.

![chlimage_1-266](assets/chlimage_1-266.png)

* **[!UICONTROL Titre]**

   (Obligatoire) Titre d’affichage de la configuration.

   Par exemple, saisissez *Activation Community Analytics.*

* **[!UICONTROL Nom]**

   (Facultatif) S’il n’est pas spécifié, le nom est défini par défaut sur un nom de noeud valide dérivé du titre.

   For example, enter *communities*


* **[!UICONTROL Template (Modèle)]**

   Sélectionner `Adobe Analytics Configuration`

* Sélectionnez **[!UICONTROL Créer]**
   * Lance la page de configuration et ouvre `Analytics Settings` la boîte de dialogue.

### Boîte de dialogue Paramètres Analytics {#analytics-settings-dialog}

La création initiale d’une nouvelle configuration Analytics entraîne l’affichage de la configuration et une nouvelle boîte de dialogue d’entrée des paramètres Analytics. Cette boîte de dialogue nécessite les informations [de compte](#prerequisites) prérequises obtenues auprès du représentant du compte.

![chlimage_1-267](assets/chlimage_1-267.png)

* **[!UICONTROL Société]**

   société associée au compte Adobe Analytics

* **[!UICONTROL Nom d’utilisateur]**

   Nom d’utilisateur de connexion de l’utilisateur autorisé à gérer le compte Analytics.

* **[!UICONTROL Mot de passe]**

   Mot de passe de connexion de l’utilisateur autorisé

* **[!UICONTROL Centre de données]**

   Sélectionnez le centre de données Analytics qui héberge la suite de rapports.

* **[!UICONTROL Ne pas ajouter la balise de suivi sur la page]**

   Ne pas utiliser comme valeur par défaut (non cochée)

* **[!UICONTROL Utiliser AppMeasurement]**

   Ne pas utiliser comme valeur par défaut (non cochée)

* **[!UICONTROL Ne pas importer des impressions de page de nuit (auteur)]**

   Ne pas utiliser comme valeur par défaut (non cochée)

* **[!UICONTROL Ne pas importer des impressions de page de nuit (publication)]**

   Quitter comme valeur par défaut (cochée)

Pour enregistrer les paramètres :


* Select **[!UICONTROL Connect to Analytics]**

   * En cas d’échec,

      * Vérifier que les entrées ne contiennent pas d&#39;espace de début
      * Essayer un autre centre de données
      * Contactez votre représentant de compte

* **[!UICONTROL Cliquez sur OK]**


![chlimage_1-268](assets/chlimage_1-268.png)

### Créer une structure {#create-framework}

Après avoir configuré correctement la connexion de base à Adobe Analytics, il est nécessaire de créer ou de modifier une structure pour le site communautaire. L’objectif de cette structure est de mettre en correspondance les variables de fonction (AEM) Communautés avec les variables Analytics (suite de rapports).

* Sélectionner `[+]` l&#39;icône en regard de Cadres **** disponibles pour créer une nouvelle structure

![chlimage_1-269](assets/chlimage_1-269.png)

* **[!UICONTROL Titre]**

   (Obligatoire) Titre d’affichage de la structure

   Par exemple, saisissez *Enablement Community Framework.*

* **[!UICONTROL Nom]**

   (Facultatif) S’il n’est pas spécifié, le nom est défini par défaut sur un nom de noeud valide dérivé du titre.

   For example, enter *communities*

* **[!UICONTROL Template (Modèle)]**

   Sélectionner `Adobe Analytics Framework`

* Sélectionnez **[!UICONTROL Créer]**

La création d’Analytics Framework ouvre la structure de configuration.

## Configuration du cadre d’AEM Analytics {#aem-analytics-framework-configuration}

L’objectif de la structure est de mapper AEM variables à des variables Analytics (evars et événements). Les variables Analytics disponibles pour le mappage sont [définies dans la suite](#adobe-analytics-report-suite-for-video-reporting)de rapports.

![chlimage_1-270](assets/chlimage_1-270.png)

### Sélectionner une Report Suite {#select-report-suite}

Sélectionnez la suite de rapports configurée pour le rapports vidéo.

Si une suite de rapports n’a pas encore été créée ou n’a pas été correctement configurée, reportez-vous à la section précédente :\
[Report Suite Adobe Analytics pour le Rapports vidéo](#adobe-analytics-report-suite-for-video-reporting)

Le sidekick n’est pas nécessaire et peut être réduit afin de ne pas entraver l’accès aux paramètres Report Suites.

#### Boîte de dialogue Report Suites avant et après avoir sélectionné &#39;Ajouter l&#39;élément&#39; {#report-suites-dialog-before-and-after-selecting-add-item}

![chlimage_1-271](assets/chlimage_1-271.png)

1. Sélectionner un élément **[!UICONTROL Ajouté +]** deux listes déroulantes s&#39;affichent
1. Sélectionnez `Report suite` les suites de rapports associées au compte de Société qui peuvent être sélectionnées.
1. Sélectionnez **[!UICONTROL Oui]** dans la boîte de dialogue qui s’ouvre : ```Load default server settings? Do you want to load the default server settings and overwrite current values in the Server section?```
1. Choose a `Run Mode`\
   Choisir la **[!UICONTROL publication]**

![chlimage_1-272](assets/chlimage_1-272.png)

Le service et la structure de cloud Analytics sont maintenant terminés. Les mappages seront définis une fois qu’un site communautaire a été créé avec ce service Analytics activé.

## Activation d’Analytics pour un site de la communauté {#enable-analytics-for-a-community-site}

### Activer pour le nouveau site de la communauté {#enable-for-new-community-site}

Pour ajouter le service cloud Analytics lors de la [création d’un site](sites-console.md)communautaire :


* À l’étape 3
* Sous l’onglet [](sites-console.md#analytics)ANALYTICS :

   * Cochez la case **[!UICONTROL Activer Analytics]** .
   * Sélectionnez le cadre dans la liste déroulante.

* Vous pouvez éventuellement revenir à la configuration de la structure d’Analytics pour ajuster les mappages de variables.

### Activer pour le site de la communauté existante {#enable-for-existing-community-site}

Pour ajouter le service cloud Analytics à un site [communautaire](sites-console.md#modifying-site-properties)existant :


* Accédez à la console **[!UICONTROL Communautés > Sites]** .
* Sélectionnez l&#39;icône Modifier le site du site de la communauté
* Sélectionner les paramètres
* Dans la section Analytics :

   * Cochez la case **[!UICONTROL Activer Analytics]** .
   * Sélectionnez le cadre dans la liste déroulante.


* Vous pouvez éventuellement revenir à la configuration de la structure d’Analytics pour ajuster les mappages de variables.

### Activer pour les sites personnalisés {#enable-for-customized-sites}

Pour que le suivi et l’importation Analytics fonctionnent correctement pour un site communautaire, un élément de page avec les attributs `scf-js-site-title` class et href doit être présent. Un seul élément de ce type doit exister sur la page, par exemple dans un `sitepage.hbs` script non modifié pour un site communautaire. La valeur de `siteUrl` est extraite et envoyée à Adobe Analytics en tant que chemin d’accès *au* site.

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

Pour un site **communautaire** personnalisé qui chevauche le `sitepage.hbs` script, assurez-vous que l’élément est présent. La `siteUrl`variable sera définie une fois rendue sur le serveur avant de servir au client.

Pour un site **AEM** générique qui comprend des composants Communautés, mais qui n&#39;est pas créé avec l&#39;Assistant [de création de](sites-console.md)site, il est nécessaire d&#39;ajouter l&#39;élément. La valeur de href doit être le chemin d&#39;accès au site. Par exemple, si le chemin d’accès au site est `/content/my/company/en`, utilisez :

```xml
<div
    class="navbar-brand scf-js-site-title"
    href="/content/my/company/en.html"
    style="visibility: hidden;"
>
</div>
```

## Fonctionnalités d’Analytics pour les communautés {#analytics-for-communities-features}

Analytics est automatiquement utilisé pour plusieurs fonctions de communautés.

La configuration [](../../help/sites-deploying/configuring-osgi.md)OSGi de l’environnement auteur `AEM Communities Analytics Component Configuration`fournit une liste des composants créés pour Analytics. Le mappage automatique des variables est déterminé par les composants répertoriés.

Si de nouveaux composants personnalisés créés pour Analytics sont créés, ils doivent être ajoutés à cette liste de composants configurés.

### Configuration des composants {#component-configuration}

![chlimage_1-273](assets/chlimage_1-273.png)

Remarque : les `journal` composants sont utilisés pour implémenter la fonction de blog.

### Analyses mises en correspondance avec AEM variables {#mapped-analytics-to-aem-variables}

Une fois le site de la communauté enregistré avec Analytics activé et la structure de configuration du cloud sélectionnée, les variables AEM sont automatiquement mises en correspondance avec les variables eVar et les événements Analytics en commençant par evar1 et événement1, respectivement, et en augmentant par 1.

Si vous utilisez une suite de rapports existante qui a mappé l’une des variables d’evar1 à evar11 et événement1 à événement7, il sera nécessaire de [remapper les variables](#modifying-analytics-variable-mapping) AEM et de restaurer le mappage d’origine.

Voici un exemple de mappages par défaut après avoir suivi le didacticiel [de](getting-started-enablement.md)prise en main :

![chlimage_1-274](assets/chlimage_1-274.png)

#### Carte des eVars envoyées avec chaque événement {#map-of-evars-sent-with-each-event}

|  | Type de ressource d&#39;activation | Titre du site | Type de fonction | Titre du groupe | Chemin d’accès du groupe | Type UGC | Titre UGC | Utilisateur (membre) | Chemin UGC | Chemin du site |
|------------------------|------------------------|-----------|--------------|------------|-----------|---------|----------|--------------|---------|----------|
|  | **eVar1** | **eVar2** | **eVar3** | **eVar4** | **eVar5** | **eVar6** | **eVar7** | **eVar8** | **eVar9** | **eVar10** |
| événement1Lecture des ressources | (une) | - | - | - | - | - | - | - | (i) | - |
| event2SCFView | (une) | (b) | (c) | (d) | (e) | (f) | (g) | (h) | (i) | j) |
| événement3SCFCreate (Post) | - | (b) | (c) | (d) | (e) | (f) | (g) | (h) | (i) | j) |
| event4SCFFollow | - | (b) | (c) | (d) | (e) | (f) | (g) | (h) | (i) | j) |
| event5SCFVoteUp | - | (b) | (c) | (d) | (e) | (f) | (g) | (h) | (i) | j) |
| event6SCFVoteDown | - | (b) | (c) | (d) | (e) | (f) | (g) | (h) | (i) | j) |
| event7SCFRate | - | (b) | (c) | (d) | (e) | (f) | (g) | (h) | (i) | j) |

**Exemples de valeurs d’eVar :**

* [Type](https://www.iana.org/assignments/media-types)MIME : vidéo/mp4
* [Titre](sites-console.md#step13asitetemplate)du site communautaire : Communautés de Geometrixx
* [Nom](functions.md)de la fonction communautaire : Forum
* [Nom](creating-groups.md#creating-a-new-group)du groupe de la communauté : Randonnée
* Chemin d’accès au contenu du groupe de la communauté : /content/sites/communautés/fr/groups/hiking
* [UGC component resourceType](essentials.md): social/forum/composants/hbs/rubrique
* Titre du composant UGC : Rubriques de randonnée
* Identifiant de connexion (identifiant autorisé) : aaron.mcdonald@mailinator.com
* Chemin SRP vers UGC : /content/usergenerate/asi/.../forum/jmtz-topic3 ou *chemin du composant à suivre*: /content/sites/communautés/fr/jcr:content/content/Principal/forum
* Chemin d’accès au contenu du site de la communauté : /content/sites/community/fr

### Modification du mappage des variables Analytics {#modifying-analytics-variable-mapping}

Le mappage des variables evar et événement Analytics sur les variables AEM est visible à partir de la configuration de la structure après l’activation d’Analytics pour un site de la communauté.

Une fois Analytics activé et avant la publication du site de la communauté, le mappage peut être modifié dans la structure en faisant glisser la variable eVar ou le événement Analytics de votre choix depuis le rail de gauche et en la déposant dans la ligne correspondante de la table de mappage.

Pour éviter les mappages de duplicata, veillez à supprimer la variable eVar ou le événement Analytics remplacé de la ligne en la survolant et en sélectionnant le X qui s’affiche à droite de l’élément de variable Analytics.

Si les eVars et événements des communautés remplacent les mappages qui existaient avant dans la suite de rapports, pour éviter la perte de données, affectez les variables AEM des fonctionnalités des communautés à d’autres eVars et/ou événements Analytics et restaurez les mappages d’origine.

>[!CAUTION]
>
>Il est important de procéder à une mise en mémoire avant la [publication](#publishing-the-community-site) du site de la communauté avec Analytics activé, faute de quoi il existe un risque de perte de données.

#### Exemple d’étape 1 : Faire glisser Analytics evar14 dans la table de mappage {#example-step-dragging-analytics-evar-into-mapping-table}

![chlimage_1-275](assets/chlimage_1-275.png)

#### Exemple d’étape 2 : Sélection de &#39;x&#39; pour supprimer evar11 remplacée {#example-step-selecting-x-to-remove-replaced-evar}

![chlimage_1-276](assets/chlimage_1-276.png)

#### Exemple d’étape 3 : AEM var eventdata.siteId a été remappé sur Analytics evar14 {#example-step-aem-var-eventdata-siteid-remapped-to-analytics-evar}

![chlimage_1-277](assets/chlimage_1-277.png)

## Publication du site de la communauté {#publishing-the-community-site}

### Vérification du mappage des variables Analytics sur AEM {#verify-analytics-to-aem-variable-mapping}

Il est judicieux de vérifier le mappage des variables avant de publier le site de la communauté, qui publie également le service et la structure de cloud Analytics.

Voir sections :

* [Analyses mises en correspondance avec AEM variables](#mapped-analytics-to-aem-variables)
* [Modification du mappage des variables Analytics](#modifying-analytics-variable-mapping)

>[!CAUTION]
>
>**Si vous utilisez une suite de rapports existante qui utilise déjà des variables dans**
>
>* **`evar1`** à **`evar11`**
>* **`event1`** à **`event7`**

>
>
**Ensuite, avant la publication du site de la communauté,** il est important de restaurer la mise en correspondance préexistante et de déplacer les variables AEM communautés qui étaient automatiquement mises en correspondance (lorsque Analytics était activé pour le site de la communauté) vers d’autres variables Analytics. Ce réacheminement doit être cohérent pour tous les composants des communautés.
>
>Si vous ne le faites pas, vous risquez de perdre des données irrécupérables.

### Éditeur Principal {#primary-publisher}

Lorsque le déploiement choisi est une batterie [de](topologies.md#tarmk-publish-farm)publication, une instance de publication AEM doit être identifiée comme l’éditeur Principal pour l’interrogation du Adobe Analytics pour que les données de rapport soient écrites à [SRP](working-with-srp.md).

Par défaut, la configuration `AEM Communities Publisher Configuration` OSGi identifie son instance de publication comme étant l’éditeur Principal, de sorte que toutes les instances de publication d’une batterie de publication s’identifient elles-mêmes comme étant la Principale.

Par conséquent, il est nécessaire de modifier la configuration sur toutes les instances de publication secondaires pour décocher la case Editeur **** Principal.

Pour obtenir des instructions spécifiques, reportez-vous à la section Principale de l’éditeur de [Déploiement de communautés](deploy-communities.md#primary-publisher).

>[!CAUTION]
>
>Il est important que l’éditeur Principal soit configuré pour empêcher l’interrogation de plusieurs instances de publication.

### Réplication de la clé Crypto {#replicate-the-crypto-key}

Les informations d’identification Adobe Analytics sont chiffrées. Pour faciliter la réplication ou la transmission des informations d’identification d’analyse chiffrées entre l’auteur et les éditeurs, toutes les instances AEM doivent partager la même clé de chiffrement Principale.

Pour ce faire, suivez les instructions de la section [Répliquer la clé](deploy-communities.md#replicate-the-crypto-key)Crypto.

### Publier le site de la communauté et le service Analytics Cloud {#publish-community-site-and-analytics-cloud-service}

Une fois que le service de cloud Analytics a été activé pour un site communautaire et que, si nécessaire, le [mappage d’Analytics sur AEM variables a été ajusté](#mapped-analytics-to-aem-variables), il est nécessaire de répliquer la configuration sur l’environnement de publication en [(re)publiant le site](sites-console.md#publishing-the-site)communautaire.

## Obtention de rapports à partir d’Analytics {#obtaining-reports-from-analytics}

### Gestion des rapports {#report-management}

La configuration [OSGi de l’auteur et de l’éditeur Principal](../../help/sites-deploying/configuring-osgi.md)`AEM Communities Analytics Report Management`est utilisée pour requête Analytics.

En ce qui concerne l’auteur, les requêtes concernent les rapports en temps réel.

Sur l’éditeur Principal, les requêtes sont utilisées pour fournir des informations en vue de l’importation des données Analytics de l’importateur de rapports.

L’intervalle de requête est défini par défaut sur 10 secondes.

### Importateur de rapports {#report-importer}

Une fois qu’un site communautaire compatible Analytics a été publié, la configuration [OSGi de l’éditeur Principal](../../help/sites-deploying/configuring-osgi.md)`AEM Communities Analytics Report Importer`peut être configurée pour définir l’intervalle d’interrogation par défaut pour les configurations qui ne sont pas configurées individuellement dans CRXDE.

L’intervalle d’interrogation contrôle la fréquence des demandes à Adobe Analytics pour que les données soient extraites et enregistrées dans [SRP](working-with-srp.md).

Lorsque les données peuvent être classées comme &quot;données massives&quot;, des sondages plus fréquents peuvent placer une charge importante sur le site communautaire.

L’intervalle **d’** importation d’interrogation par défaut est défini sur 12 heures.

![chlimage_1-278](assets/chlimage_1-278.png)

### Personnalisation des rapports de composants {#component-report-customization}

Actuellement, pour personnaliser les mesures à suivre, des noeuds sont créés dans le référentiel qui définissent les périodes pour lesquelles générer un rapport sur cette mesure.

Le thème du forum est actuellement le seul exemple de cette personnalisation :

* Sur l’éditeur Principal
* Connexion avec des droits d’administrateur
* Navigate to [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md)

   * For example, [http://localhost:4503/crx/de](http://localhost:4503/crx/de)

* Sous le `jcr:content` noeud de la racine de langue

   * Par exemple, `/content/sites/engage/en/jcr:content`

* Accédez au composant configuré pour le rapports Analytics

   * Par exemple, `analytics/reportConfigs/social_forum_components_hbs_topic`

* Notez les périodes créées

   * `last30Days`
   * `last90Days`
   * `thisYear`

* Remarquez le `total`noeud

   * La modification de la `interval` propriété remplace l&#39;intervalle d&#39;importation des rapports.
   * La valeur est exprimée en secondes et est définie sur 4 heures (1 400 secondes).

![chlimage_1-279](assets/chlimage_1-279.png)

## Gestion des données utilisateur dans Analytics {#manage-user-data-in-analytics}

Adobe Analytics fournit des API qui vous permettent d’accéder, d’exporter et de supprimer des données utilisateur. Pour plus d’informations, voir [Envoyer des demandes d’accès et de suppression](https://docs.adobe.com/content/help/en/analytics/admin/data-governance/gdpr-submit-access-delete.html).

## Ressources {#resources}

* Adobe Marketing Cloud : [Aide et référence d’Analytics](https://docs.adobe.com/content/help/en/analytics/landing/home.html)
* AEM: [Integrating with Adobe Analytics](../../help/sites-administering/adobeanalytics.md)
* AEM: [Analytics with External Providers](../../help/sites-administering/external-providers.md)

