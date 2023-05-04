---
title: Paramètres de configuration OSGi
seo-title: OSGi Configuration Settings
description: Cet article décrit les paramètres de configuration OSGi (répertoriés en fonction du lot) pertinents pour la mise en oeuvre du projet. La liste sert de ligne directrice et n’est pas exhaustive.
seo-description: This article details the OSGi configuration settings (listed according to bundle) that are relevant to project implementation. The list acts as a guideline and it is not exhaustive.
uuid: 817de76e-7ba6-4502-94f5-09046b878cfb
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: configuring
content-type: reference
discoiquuid: ccddb2cd-8e67-43aa-a495-8996ad349761
feature: Configuring
exl-id: 5c07c773-53a3-41fd-860a-da0cb14f8bc6
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '3496'
ht-degree: 72%

---

# Paramètres de configuration OSGi{#osgi-configuration-settings}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

L’[OSGi](https://www.osgi.org/) est un élément fondamental de la pile technologique d’AEM. Il est utilisé pour contrôler les lots composites d’AEM et leur configuration.

OSGi &quot;*fournit les primitives normalisées qui permettent de construire des applications à partir de petits composants réutilisables et collaboratifs. Ces composants peuvent être créés dans une application et déployés* ».

Cela permet une gestion conviviale des lots car ils peuvent être arrêtés, installés et démarrés individuellement. Les interdépendances sont gérées automatiquement. Chaque composant OSGi (voir [Spécifications OSGi](https://docs.osgi.org/specification/)) se trouve dans l’un des lots. Lorsque vous utilisez AEM, plusieurs méthodes permettent de gérer les paramètres de configuration de ces lots. see [Configuration d’OSGi](/help/sites-deploying/configuring-osgi.md) pour plus d’informations et pour connaître les pratiques recommandées.

Les paramètres de configuration OSGi suivants (répertoriés en fonction du lot) sont pertinents pour la mise en oeuvre du projet. Les paramètres répertoriés ne doivent pas tous être ajustés, certains sont mentionnés pour vous aider à comprendre comment fonctionne AEM.

>[!CAUTION]
>
>La liste est destinée à servir de ligne directrice et n’est pas exhaustive. Tous les lots ne sont pas répertoriés, pas plus que tous les paramètres de certains des lots qui le sont.
>
>La configuration nécessaire varie d’un projet à l’autre.
>
>Consultez la console Web pour connaître les valeurs utilisées et des informations détaillées sur les paramètres.

>[!NOTE]
>
>L’outil de comparaison des configurations OSGi, faisant partie des [Outils AEM](https://helpx.adobe.com/experience-manager/kb/tools/aem-tools.html), peut être utilisé pour répertorier les configurations OSGi par défaut.

>[!NOTE]
>
>D’autres lots peuvent être nécessaires pour des zones spécifiques de fonctionnalité dans AEM. Dans ce cas, les informations de configuration figurent sur la page liée à la fonctionnalité en question.

Le **Listener d’événement de réplication AEM** configure les éléments suivants :

* Les **Modes d’exécution** dans lesquels les événements de réplication seront distribués aux listeners. Par exemple, s’il est défini comme auteur, il s’agit du système qui « lance » la réplication.

* Le mode d’exécution **publier** doit être ajouté si le code du projet traite les événements de réplication (réplication inverse) dans un environnement de publication. Par exemple, lorsque le Dispatcher est utilisé pour vider le contenu de l’environnement de publication ou lorsque la réplication standard vers d’autres instances de publication se produit.

Le **Listener de modification du référentiel AEM** configure les éléments suivants :

* Les **Chemins**, les emplacements à écouter pour maintenir les événements de référentiel prêts à être distribuer.

Le **Référentiel client CRX Sling** configure l’accès au référentiel de contenu sous-jacent.

* Le **Mot de passe administrateur** doit être modifié après installation afin de garantir la [sécurité](/help/sites-administering/security-checklist.md) de votre instance.

* Aucune autre modification n’est nécessaire et vous devez procéder avec précaution pour toute modification car elles peuvent affecter l’accès au référentiel.

La **Console de gestion OSGi Apache Felix** configure :

* les **modules complémentaires**, les éléments de navigation principale (modules complémentaires de la console) disponibles dans la **Console de gestion web Apache Felix** en tant qu’éléments de menu de niveau supérieur. Désactivez tous les éléments dont vous n’avez pas besoin, car chacun d’entre eux requiert de l’espace et des ressources. 

>[!CAUTION]
>
>Veillez à configurer les éléments suivants :
>
>**Nom d’utilisateur** et **Mot de passe**, les informations d’identification pour accéder à la console de gestion web Apache Felix.\
>Le mot de passe doit être modifié après l’installation initiale pour garantir [la sécurité](/help/sites-administering/security-checklist.md) de votre instance. 

>[!NOTE]
>
>Cette configuration doit être effectuée par le biais de la console Felix, car elle est nécessaire au démarrage (avant que le référentiel ne soit disponible).

L’**Enregistreur de données de demandes personnalisables Apache Sling** configure :

* le **Nom de l’enregistreur** et le **Format de journal** pour configurer l’emplacement et le format de la demande et de la journalisation des accès (valeur par défaut : `request.log`). Ce fichier journal est essentiel pour analyser la performance ou déboguer les fonctionnalités liées à la chaîne web. 

   Celle-ci est associée à l’enregistreur de demandes Apache Sling.

Pour plus d’informations, reportez-vous aux sections [Journalisation AEM](/help/sites-deploying/configure-logging.md) et [Journalisation Sling](https://sling.apache.org/site/logging.html).

Le **Pool de threads d’événement Apache Sling** configure les éléments suivants :

* La **Taille minimale du pool** et la **Taille max. du pool**, les taille du pool utilisées pour contenir les threads d’événement.

* La **Taille de la file d’attente**, taille maximale de la file d’attente de thread si le pool est épuisé.

   La valeur recommandée est `-1` car cela définit la file d’attente sur illimitée ; si une limite est définie, les pertes peuvent survenir lorsqu’elle est dépassée.

* La modification de ces paramètres peut améliorer les performances dans des scénarios comportant un grand nombre d’événements ; par exemple, une utilisation importante de la gestion des ressources numériques ou des workflows AEM.
* Les valeurs spécifiques à votre scénario doivent être établies à l’aide de tests.
* Ces paramètres peuvent avoir une incidence sur les performances de votre instance. Par conséquent, ne les modifiez pas sans raison et sans précautions.

Le **Servlet GET Apache Sling** configure certains aspects du rendu :

* L’**Index automatique** pour activer ou désactiver le rendu du répertoire pour la navigation. 
* **Activer** (ou désactiver) les rendus par défaut, tels que **HMTL**, **Texte brut**, **JSON** ou **XML**.

   Ne désactivez pas le JSON.

>[!NOTE]
>
>Ce paramètre est automatiquement configuré pour les instances d’exploitation si vous exécutez AEM en [mode Prêt pour l’exploitation](/help/sites-administering/production-ready.md).

Le **Gestionnaire de script Java Apache Sling** configure les paramètres de compilation des fichiers .java en tant que scripts (servlets).

Certains paramètres peuvent nuire aux performances et doivent être désactivés dans la mesure du possible, en particulier pour une instance d’exploitation. 

* s **Source VM** et **Target VM**, définissez la version du JDK comme celle utilisée comme JVM d’exécution.

* pour les instances de production :

   * Désactivez l’option **Générer les informations de débogage**.

**Programme d’installation de JCR Apache Sling** Ces paramètres n’ont pas besoin d’être configurés, mais peuvent être utiles pour savoir quand développer ou déboguer. Par exemple, le dossier d’installation peut être utile pour archiver/extraire ou créer un package.

* **regexp du nom des dossiers d&#39;installation** et **Profondeur de hiérarchie maximale des dossiers d’installation** - indiquez où et dans quelle profondeur les dossiers de référentiel sont recherchés pour les ressources à installer. Lorsqu’un caractère générique est utilisé (comme dans .&amp;ast;/install) toutes les correspondances appropriées seront recherchées, par exemple : `/libs/sling/install` et `/libs/cq/core/install`.

* **Chemin de recherche** : la liste des chemins d’accès recherchés par jcrinstall pour l’installation des ressources, ainsi qu’un nombre indiquant le facteur de pondération pour ce chemin. 

Le **Gestionnaire d’événements de tâche Apache Sling** configure les paramètres qui gèrent la planification des tâches :

* **Intervalle de reprise**, **Nombre maximal de reprises**, **Nombre maximal de tâches en parallèle**, **Accepter le temps d’attente**, entre autres.

* La modification de ces paramètres peut améliorer les performances dans des scénarios comportant un grand nombre de tâches ; par exemple, une utilisation intensive de la gestion des ressources numériques et des workflows AEM.
* Les valeurs spécifiques à votre scénario doivent être établies à l’aide de tests.
* Ne modifiez pas ces paramètres sans raison, mais uniquement après mûre réflexion.

Le **Gestionnaire de script JSP Apache Sling** configure les paramètres relatifs aux performances pour le gestionnaire de script JSP. Pour améliorer les performances, désactivez autant que possible.

En particulier pour les instances de production :

* Désactivez l’option **Générer les informations de débogage**.
* disable **Conserver le code Java généré**
* Désactivez l’option **Contenu mappé**.
* disable **Afficher les fragments source**

>[!NOTE]
>
>Ce paramètre est automatiquement configuré pour les instances d’exploitation si vous exécutez AEM en [mode Prêt pour l’exploitation](/help/sites-administering/production-ready.md).

La **Configuration de journalisation Apache Sling** configure les éléments suivants :

* Le **Niveau de journal** et le **fichier journal**, pour définir l’emplacement et le niveau de journal de la configuration de journalisation centrale (error.log). Le niveau peut être défini sur `DEBUG`, `INFO`, `WARN`, `ERROR` et `FATAL`.

* **Nombre de fichiers journaux** et **Seuil du fichier journal** pour définir la taille et la rotation de version du fichier journal.

* **Modèle de message** définit le format des messages du journal.

Pour plus d’informations, reportez-vous aux sections [Journalisation AEM](/help/sites-deploying/configure-logging.md#global-logging) et [Journalisation Sling](https://sling.apache.org/site/logging.html).

La **Configuration de l’enregistreur de journaux Apache Sling (configuration d’usine)** configure :

* Le **Niveau de journal**, le **Fichier journal** et le **Format de message** pour définir les détails du fichier journal et des messages. 

*  L’**Enregistreur** pour définir la catégorie ; par exemple, uniquement le journal pour com.day.cq.

* En utilisant **Configurations d’usine**, un certain nombre de configurations supplémentaires peuvent être ajoutées pour répondre aux différents niveaux de journal et catégories nécessaires.
* Ces configurations sont utiles lors du développement. par exemple, pour consigner des messages de TRACE pour un service spécifique dans un fichier journal spécifique.
* De telles configurations s’avèrent utiles dans un environnement de production. par exemple, pour que les messages relatifs à un service spécifique soient consignés dans un fichier journal individuel afin de faciliter la surveillance.

Pour plus d’informations, reportez-vous aux sections [Journalisation AEM](/help/sites-deploying/configure-logging.md) et [Journalisation Sling](https://sling.apache.org/site/logging.html).

La **Configuration de rédacteur de journalisation Apache Sling (configuration d’usine)** configure les éléments suivants :

* Le **Fichier journal** pour définir l’existence d’un fichier journal
* Le **nombre de fichiers journaux** pour définir la rotation des versions

* Le rédacteur peut être utilisé par une **configuration d’enregistreur de journaux Apache Sling**.

* Ces configurations sont utiles lors du développement. par exemple, pour consigner des messages de TRACE pour un service spécifique dans un fichier journal spécifique.
* De telles configurations s’avèrent utiles dans un environnement de production. par exemple, pour que les messages relatifs à un service spécifique soient consignés dans un fichier journal individuel afin de faciliter la surveillance.

Pour plus d’informations, reportez-vous aux sections [Journalisation AEM](/help/sites-deploying/configure-logging.md) et [Journalisation Sling](https://sling.apache.org/site/logging.html).

Le **Servlet principal Apache Sling** configure :

* le **Nombre d’appels par demande** et la **Profondeur de récursion** pour protéger votre système contre la récursivité infinie et les appels excessifs de script.

Le **Service de type MIME Apache Sling** configure :

* **les types MIME** pour ajouter ceux requis par votre projet dans le système. Cela permet d’effectuer une demande `GET` sur un fichier pour définir l’en-tête du type de contenu approprié pour lier le type de fichier et l’application. 

**Filtre de référent Apache Sling** Pour résoudre les problèmes de sécurité connus avec Cross-Site Request Forgery (CSRF) dans CRX WebDAV et Apache Sling, vous devez configurer le filtre de référent.

Le service de filtrage des référents est un service OSGi qui vous permet de configurer :

* les méthodes HTTP à filtrer ;
* si un en-tête de référent vide est permis ;
* et une liste des serveurs autorisés, en plus de l’hôte de serveur.

Reportez-vous à la section [Liste de contrôle de sécurité - Problèmes de falsification des demandes cross-site](/help/sites-administering/security-checklist.md#protect-against-cross-site-request-forgery) pour plus de détails.

>[!NOTE]
>
>Le filtre de référent Apache Sling dépend de l’installation d’un package de correctif rapide.

L’**Enregistreur de requêtes Apache Sling** configure les éléments suivants :

* Divers paramètres pour définir comment les requêtes sont consignées
* L’option **Activer le journal de requête**, pour l’activer ou le désactiver

* **Activer le journal d’accès**, pour activer ou désactiver .

Ceci est associé à l’enregistreur de données de requête personnalisable Apache Sling.

Pour plus d’informations, reportez-vous aux sections [Journalisation AEM](/help/sites-deploying/configure-logging.md) et [Journalisation Sling](https://sling.apache.org/site/logging.html).

La **Fabrique de résolveur de ressource Apache Sling** configure les aspects centraux de la résolution des ressources Sling :

* **Le chemin de recherche de la ressource**, ajoute tous les chemins d’accès spécifiques au projet (mais ne supprime pas `/libs` ni `/apps`).

* Les **URL virtuelles** pour définir vos mappages aux URL de redirection

* Les **Mappages d’URL** pour définir tous les alias ; par exemple, de `/content` à `/`

* L’**Emplacement du mappage**, la configuration du mappeur extériorisée dans `/etc/map`

* Utilisez votre installation locale (par exemple, utilisez `http://localhost:4502/system/console/jcrresolver`) pour déterminer quel résolveur de ressources est actif.

Pour plus d’informations, voir : [https://cwiki.apache.org/confluence/display/SLING/Flexible+Resource+Resolution](https://cwiki.apache.org/confluence/display/SLING/Flexible+Resource+Resolution).

>[!CAUTION]
>
>En particulier, ces options doivent être configurées dans le référentiel.
>
>Sinon, les modifications apportées à **Mappages d’URL** l’utilisation de la console Felix peut être écrasée par AEM au prochain démarrage.

Le **Gestionnaire d’erreur et résolveur de script et le servlet Apache Sling** Le servlet Sling et le résolveur de script ont plusieurs tâches :

1. Ils sont utilisés comme `ServletResolver` pour sélectionner le servlet ou le script à appeler pour traiter la demande.

1. Ils servent de `SlingScriptResolver`.

1. Ils assurent la gestion des erreurs en implémentant l’interface `ErrorHandler` à l’aide du même algorithme pour sélectionner les servlets et les scripts assurant la gestion des erreurs, comme ceux utilisés pour résoudre les servlets et scripts assurant le traitement des demandes.

Plusieurs paramètres peuvent être définis, notamment :

* **Chemins d’exécution** répertorie les chemins d’accès à la recherche de scripts exécutables ; en configurant des chemins spécifiques, vous pouvez limiter les scripts pouvant être exécutés. Si aucun chemin n’est configuré, la valeur par défaut est utilisée (`/`= root). Cela permet l’exécution de tous les scripts.

   Si une valeur de chemin configuré se termine par une barre oblique, l’arborescence entière est recherchée. En l’absence d’une telle barre oblique, le script n’est exécuté que s’il s’agit d’une correspondance exacte.

* **Utilisateur du script** - cette propriété facultative peut spécifier le compte utilisateur du référentiel utilisé pour lire les scripts. Si aucun nombre n’est spécifié, l’utilisateur `admin` est utilisé par défaut.

* **Extensions par défaut** La liste des extensions pour lesquelles le comportement par défaut est utilisé. Cela signifie que le dernier segment de chemin du type de ressource peut être utilisé comme nom du script.

* Définissez le **Chemin de la police** pour rechercher des polices spécifiques au projet.

   Par exemple, `/apps/myapp/fonts`.

**Configuration du proxy de composants HTTP Apache** Configuration de proxy pour tout le code utilisant le client HTTP Apache, utilisée lorsque du code HTTP est créé ; par exemple lors de la réplication.

Lors de la création d’une configuration, n’apportez pas de modifications à la configuration d’usine, mais créez plutôt une configuration d’usine pour ce composant à l’aide du gestionnaire de configuration disponible ici : **http://localhost:4502/system/console/configMgr/**. La configuration du proxy est disponible à l’adresse **org.apache.http.proxyconfigurator.**

>[!NOTE]
>
>Dans AEM version 6.0 et antérieure, le proxy était configuré dans le client HTTP Day Commons. Depuis AEM 6.1 et versions ultérieures, la configuration proxy a été déplacée vers « Configuration proxy des composants HTTP Apache » au lieu de la configuration « Client HTTP Day Commons ».

L’**Antispam Day CQ** configure le service anti-spam (Akismet) utilisé. Pour ce faire, vous devez enregistrer les éléments suivants :

* **Fournisseur**
* **Clé API**
* **URL enregistrée**

**Gestionnaire de bibliothèques HTML Adobe Granite** Configurez ce dernier pour contrôler la gestion des bibliothèques client (CSS ou js) ; notamment la manière dont la structure sous-jacente est vue.

* Pour les instances de production :

   * Activez **Minifier** (pour supprimer les caractères CRLF et les espaces blancs).
   * Activez **Gzip** (pour permettre l’extraction et l’accès aux fichiers avec une seule requête).
   * Désactivez **Déboguer**
   * Désactivez **Minutage**

* Pour le développement JS (en particulier lors du débogage/du bogage de feu) :

   * disable **Minify**
   * enable **Déboguer** pour séparer les fichiers à des fins de débogage et à utiliser avec firebug.
   * enable **Minutage** dans le cas de l’intérêt pour le timing.
   * enable **Déboguer** pour afficher les messages du journal de la console JS.

>[!CAUTION]
>
>Lorsque vous changez le paramètre sur **Minimisation** ou **Gzip**, vous devez également supprimer le contenu du cache clientlibs. Reportez-vous à l’[article de la base de connaissances](https://experienceleague.adobe.com/docs/experience-cloud-kcs/kbarticles/KA-16543.html?lang=fr) pour plus d’informations.

>[!NOTE]
>
>Ce paramètre est automatiquement configuré pour les instances d’exploitation si vous exécutez AEM en [mode Prêt pour l’exploitation](/help/sites-administering/production-ready.md).

**Gestionnaire d’authentification de l’en-tête HTTP Day CQ** Paramètres à l’échelle du système pour la méthode d’authentification de base de la requête HTTP.

Lors de l’utilisation de [groupes d’utilisateurs fermés](/help/sites-administering/cug.md) vous pouvez configurer (entre autres) :

* **Domaine HTTP**
* La **page de connexion par défaut**

Le **Service de vérificateur de lien Day CQ** vérifie et, si nécessaire, configure les éléments suivants :

* La **période du planificateur** pour définir l’intervalle selon lequel les liens externes doivent être automatiquement vérifiés

* Vérifier **Intervalle de tolérance des liens incorrecte** pour la période au-delà de laquelle un lien externe infructueux est considéré comme mauvais.
* **Modèles de remplacement de la vérification de lien**, pour définir les chemins à exclure de la vérification des liens.

La **Tâche du vérificateur de lien Day CQ** configure les paramètres d’une seule tâche de vérification de lien (une tâche qui vérifie un lien externe) :

* Vérifiez les intervalles définis dans les options **Intervalle de test de lien valide** et **Intervalle de test d’un lien invalide**.

* Les différents paramètres liés aux proxys pour l’accès Internet et les NTLM nécessaires pour les accès externes lors de la vérification d’un lien.

Le **Service de messagerie Day CQ** Configurez le nom d’hôte et les informations d’accès au serveur de messagerie. Reportez-vous à la section Configuration du service de messagerie.

La **Newsletter MCM Day CQ** Configurez les différents paramètres utilisés avec la newsletter.

Le **Mappage racine Day CQ** configure :

* le **chemin cible** pour définir où une demande de « `/` » sera redirigée.

Il y a [deux interfaces utilisateur](/help/sites-authoring/select-ui.md) disponible dans AEM :

* l’interface utilisateur optimisée pour les écrans tactiles a été introduite.
* et l’IU classique est toujours pleinement opérationnelle.

En utilisant le mappage racine d’AEM, vous pouvez configurer l’IU que vous souhaitez utiliser en tant que valeur par défaut pour votre instance :

* Pour que l’IU optimisée pour les écrans tactiles soit l’IU par défaut, **Chemin cible** doit pointer vers :

   ```
      /projects.html
   ```

* Pour utiliser l’IU classique en tant qu’IU par défaut, le **chemin cible** doit pointer vers :

   ```
      /welcome.html
   ```

>[!NOTE]
>
>Pour une installation standard, l’IU optimisée pour les écrans tactiles est l’UI par défaut.

**Gestionnaire d’authentification SSO Adobe Granite** Configurez les détails de connexion unique (SSO) ; ils sont souvent nécessaires dans les configurations d’auteur d’entreprise, souvent en conjonction avec le protocole LDAP.

Différentes propriétés de configuration sont disponibles :

* **Chemin**
Chemin pour lequel ce gestionnaire d’authentification est actif. Si ce paramètre n’est pas renseigné, le gestionnaire d’authentification est désactivé. Par exemple, si vous utilisez le chemin /, le gestionnaire d’authentification est utilisé pour l’ensemble du référentiel.

* **Classement de service**
La valeur de classement du service OSGi Framework est utilisée pour indiquer l’ordre d’appel de ce service. Il s’agit d’une valeur 
`int`, pour laquelle des valeurs plus élevées désignent une priorité plus élevée.


   La valeur par défaut est `0`.

* **Noms des en-têtes**
Les noms des en-têtes qui peuvent contenir un identifiant utilisateur.

* **Noms de cookies**
Les noms des cookies pouvant contenir un identifiant utilisateur.

* **Nom des paramètres**
Les noms des paramètres de requête pouvant fournir l’identifiant utilisateur.

* **La carte utilisateur**
Pour les utilisateurs sélectionnés, le nom d’utilisateur extrait de la requête HTTP peut être remplacé par un nom différent dans l’objet des informations d’authentification. Le mappage est défini ici. Si le nom d’utilisateur 
`admin` apparaît d’un côté ou de l’autre de la carte, le mappage est ignoré. N’oubliez pas que le caractère « = » doit être précédé de « \ ».

* **Format**
Indique le format dans lequel l’identifiant utilisateur est fourni. Utilisez :

   * `Basic` si l’identifiant utilisateur est codé au format d’authentification HTTP de base ;
   * `AsIs` si l’identifiant utilisateur est fourni en texte brut ou si une valeur appliquée d’expression régulière doit être utilisée telle quelle.

**Filtre de débogage de la gestion de contenu web Day CQ**
Utile lors du développement car il permet d’utiliser des suffixes comme ?debug=layout lors de l’accès à une page. Par exemple, http://localhost:4502/cf#/content/geometrixx/en/support.html?debug=layout fournira des informations de mise en page qui peuvent intéresser le développeur.

* Désactivez cette option sur les instances d’exploitation pour en garantir la performance et la sécurité.

Le **Filtre de gestion de contenu web Day CQ** configure les éléments suivants :

* **Mode WCM** pour définir le mode par défaut.
* Sur une instance d’auteur, cela peut être `edit`, `disable,preview` ou `analytics`.

   Les autres modes sont accessibles depuis le sidekick. Vous pouvez également utiliser le suffixe `?wcmmode=disabled` pour simuler un environnement d’exploitation.

* Sur une instance de publication, cela doit être défini sur `disabled` afin de vous assurer qu’aucun autre mode n’est accessible.

>[!NOTE]
>
>Ce paramètre est automatiquement configuré pour les instances d’exploitation si vous exécutez AEM en [mode Prêt pour l’exploitation](/help/sites-administering/production-ready.md).

Le **Configurateur de vérification de lien de gestion de contenu web Day CQ** configure les éléments suivants :

* **Liste des configurations de réécriture** pour spécifier une liste d’emplacements pour les configurations linkchecker basées sur le contenu. Les configurations peuvent être basées sur le mode d’exécution ; il est important de faire la distinction entre les environnements de création et de publication, car les paramètres de linkchecker peuvent différer.

Le **Processeur de page de gestion de contenu web Day CQ** configure :

* les **chemins d’accès**, une liste d’emplacements où le système détecte des modifications de page avant de déclencher `jcr:Event`.

L’**Outil de suivi des impressions de page Adobe**, pour une instance d’auteur, configure :

* **sling.auth.requirements** : définissez la valeur de cette propriété sur `-/libs/wcm/stats/tracker`.

>[!CAUTION]
>
>Ce paramétrage permettra l&#39;envoi de requêtes anonymes au service de tracking.

>[!NOTE]
>
>Consultez la section [Impressions de page](/help/sites-deploying/configuring.md#enabling-page-impressions) pour plus d’informations.

Les **Statistiques de page de la gestion de contenu web Day CQ**, pour une instance de publication, configure les éléments suivants :

* L’**URL pour envoyer des données** pour configurer l’URL utilisée pour suivre les statistiques de page (essentiel si la demande d’un outil de suivi passe par le Dispatcher) ; par exemple, l’URL par défaut est `http://localhost:4502/libs/wcm/stats/tracker`.

* Le **Script de suivi activé** pour activer (`true`) ou désactiver (`false`) l’intégration du script de suivi sur les pages. La valeur par défaut est `false`.

>[!NOTE]
>
>Consultez la section [Impressions de page](/help/sites-deploying/configuring.md#enabling-page-impressions) pour plus d’informations.

Le **Gestionnaire de versions de la gestion de contenu web Day CQ** contrôlez si et comment les versions sont gérées dans votre système :

* **Créer une version lors de l’activation**, activé dans une installation standard
* **Activer la purge**

* **Purger les chemins d’accès**, les chemins d’accès qui seront recherchés suite à une action de recherche
* **Chemins de version implicites**, les chemins d’accès pour lesquels la création de version implicite est active

* **Âge de version maximal**, l’âge maximale (en jours) d’une version

* **Nombre maximal de versions**, le nombre maximal de versions à conserver

Consultez la section [Purge des version](/help/sites-deploying/version-purging.md) pour plus d’informations.

Le **Service de notification par e-mail des workflows Day CQ** configure les paramètres d’e-mail pour les notifications envoyées par un workflow.

**Fabrique d’analyseur de HTMLS de réécriture CQ**

Contrôle l’analyseur de HTML pour le module de réécriture CQ.

* **Balises supplémentaires à traiter** - Vous pouvez ajouter ou supprimer des balises de HTML à traiter par l’analyseur. Par défaut, les balises suivantes sont traitées : A,IMG,AREA,FORM,BASE,LINK,SCRIPT,BODY,HEAD
* **Conserver les majuscules** - Par défaut, l’analyseur HTML convertit les attributs contenant une majuscule (par exemple eBay) en minuscules (par exemple ebay). Vous pouvez désactiver cette option pour conserver les attributs de casse des chameaux. Cela s’avère utile lors de l’utilisation de structures front-end telles que Angular 2.

Le **Pool de connexions JDBC Day Commons** configure l’accès à une base de données externe utilisée comme source de contenu.

Comme c’est une configuration d’usine, plusieurs instances peuvent être configurées.

**CDN Rewriter** La communication entre AEM et le CDN doit être assurée pour que les ressources et fichiers binaires soient diffusés à l’utilisateur final de manière sécurisée. Cela implique deux tâches :

* Accédez à la ressource à partir d’AEM via le réseau de diffusion de contenu la toute première fois (ou après son expiration dans le cache).
* L’accès à la ressource mise en cache dans le réseau de diffusion de contenu est sécurisé, car une fois la ressource mise en cache dans le réseau de diffusion de contenu, la demande n’est pas envoyée à AEM et tous les utilisateurs ayant accès à cette ressource sur doivent être diffusés à partir du réseau de diffusion de contenu.

AEM fournit un module de réécriture permettant de réécrire les URL de ressources internes en URL CDN externes. Il réécrit les liens à transmettre au réseau de diffusion de contenu, y compris une signature JWS et un délai d’expiration pour permettre l’accès sécurisé à la ressource. Cette fonctionnalité doit être utilisée sur les instances d’auteur.

Le flux global est le suivant :

1. L’utilisateur s’authentifie avec AEM et demande une page contenant des ressources.
1. La page demandée contient une ressource similaire à `/content/dam/geometrixx-media/articles/paladin_trailer.jpg/jcr:content/renditions/cq5dam.thumbnail.319.319.png`.
1. Le module de réécriture transforme le lien en URL CDN contenant une signature JWS :

   `CDN_domain/content/dam/geometrixx-media/articles/paladin_trailer.jpg/_jcr_content/renditions/cq5dam.thumbnail.319.319.png?cdn_sign=JWS_SIGNATURE`

1. Le navigateur de l’utilisateur, puis transfère la demande de ressource au serveur CDN.
1. Le CDN doit être configuré pour charger la demande à AEM avec le paramètre `cdn_sign`.
1. Un gestionnaire d’authentification valide le paramètre `cdn_sign`, puis renvoie la ressource au CDN, qui est ensuite renvoyée à l’utilisateur.

Le flux entre le navigateur de l’utilisateur, le CDN et AEM peut être visualisée comme suit. 

![chlimage_1-118](assets/chlimage_1-118.png)

>[!NOTE]
>
>Cette fonctionnalité est actuellement disponible uniquement pour les instances d’auteur AEM. 

**CDNConfigServiceImpl** Fournit des configurations CDN.

La fonction de réécriture CDN peut être activée en indiquant le **nom de domaine de distribution CDN** dans la configuration pour com.adobe.cq.cd n.rewriter.impl.CDNConfigServiceImpl.

Le service contient également d’autres options de configuration comme activer/désactiver la réécriture du CDN, les préfixes de chemin pour lesquels la réécriture CDN est exécutée, les valeurs TTL et le protocole (HTTP ou HTTPS).

**CDN Rewriter** Un module de réécriture pour réécrire les URL des images internes en URL CDN

La valeur **Attributs de balise** dans com.adobe.cq.cdn.rewriter.impl.CDNRewriter peut être définie de sorte que seuls les liens d’une sélection d’images soient réécrits.
