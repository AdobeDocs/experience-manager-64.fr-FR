---
title: Résolution des problèmes d’intégration
seo-title: Troubleshooting Integration Issues
description: Découvrez comment résoudre les problèmes d’intégration.
seo-description: Learn how to troubleshoot integration issues.
uuid: fe080e58-a855-4308-a611-f72eb47ba82d
contentOwner: raiman
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: integration
content-type: reference
discoiquuid: 422ee332-23ae-46bd-8394-a4e0915beaa2
exl-id: 81b8f8c0-7f9d-4748-af07-c550826c19b4
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1094'
ht-degree: 69%

---

# Résolution des problèmes d’intégration{#troubleshooting-integration-issues}

## Conseils pratiques de dépannage {#general-troubleshooting-tips}

### Vérification de l’absence d’erreur JavaScript {#ensure-there-are-no-javascript-errors}

Vérifiez si des erreurs s’affichent sur la console JavaScript du navigateur. Les erreurs non prises en charge peuvent empêcher le code suivant de s’exécuter correctement. S’il y a des erreurs, vérifiez le script à l’origine de chaque erreur et dans quelle zone celle-ci s’est produite. Le chemin d’accès au script peut donner une indication de la fonctionnalité à laquelle le script est associé.

### Connexion au niveau du composant {#logging-on-component-level}

Dans certains cas, il peut s’avérer utile d’ajouter des instructions au niveau du composant. Puisque le composant est rendu, vous pouvez ajouter un balisage temporaire pour afficher les valeurs de variable qui pourraient vous aider à identifier les problèmes potentiels. Par exemple :

```
<%
log.info("myVariable={}", myVariable);
%>
  
<!--
<%= myJspVariable %>
-->

<!--
${ myHtlVariable }
-->
```

Pour plus d’informations sur la journalisation, voir [Journalisation](/help/sites-deploying/configure-logging.md) et [Utilisation des enregistrements d’audit et des fichiers journaux](/help/sites-deploying/monitoring-and-maintaining.md#working-with-audit-records-and-log-files) pages.

## Problèmes d’intégration d’Analytics {#analytics-integration-issues}

### L’importateur de rapports mobilise fortement le processeur/la mémoire {#the-report-importer-causes-high-cpu-memory-usage}

L’importateur de rapports mobilise fortement le processeur/la mémoire ou entraîne des exceptions de type `OutOfMemoryError`.

#### Solution {#solution}

Pour résoudre ce problème, vous pouvez essayer la méthode suivante :

* Vérifiez l’absence d’enregistrement d’une quantité importante d’importateurs d’interrogations (voir la section « L’arrêt prend un certain temps à cause de l’importateur d’interrogations » ci-dessous).
* Exécutez les importateurs de rapports à un moment précis à l’aide des expressions CRON pour les configurations `ManagedPollingImporter` dans la [console OSGi](/help/sites-deploying/configuring-osgi.md).

Pour plus d’informations sur la création de services d’importateur de données personnalisés dans AEM, lisez l’article suivant. [https://helpx.adobe.com/experience-manager/using/polling.html](https://helpx.adobe.com/experience-manager/using/polling.html).

### L’arrêt prend un certain temps à cause de l’importateur d’interrogations {#shutdown-takes-a-long-time-due-to-the-pollingimporter}

Analytics a été conçu avec un mécanisme d’héritage. L’utilisateur active généralement Analytics pour un site en ajoutant une référence à une configuration Analytics dans l’onglet des propriétés de la page des [Services cloud](/help/sites-developing/extending-cloud-config.md). Toutes les sous-pages héritent alors automatiquement de la configuration sans qu’il soit nécessaire d’ajouter à nouveau la référence, sauf si une page nécessite une configuration différente. L’ajout d’une référence à un site crée également automatiquement plusieurs noeuds (12 pour AEM 6.3 et versions antérieures ou 6 pour AEM 6.4) de type `cq;PollConfig` qui instancie les importateurs d’interrogations utilisés pour importer des données Analytics dans AEM. Par conséquent :

* Le fait d’avoir un grand nombre de pages référençant Analytics génère de nombreux importateurs d’interrogations.
* De plus, la copie et le collage de pages avec une référence dans une configuration Analytics entraînent la duplication de ses importateurs d’interrogations.

#### Solution {#solution-1}

Tout d’abord, l’analyse de la [error.log](/help/sites-deploying/configure-logging.md) peut vous donner des informations sur la quantité de importateurs d’interrogations principaux ou enregistrés. Par exemple :

```
# Count PollingImporter entries
$ sed -n "s/.*(aem-analytics-integration-.*).*target=\(.*\),interval.*/\1/p" error.log | wc -l
86415
# Count PollingImporter entries for last30days
$ sed -n "s/.*(aem-analytics-integration-last30Days).*target=\(.*\),interval.*/\1/p" error.log | wc -l
14531
# Count unique paths of PollingImporter registrations
sed -n "s/.*(aem-analytics-integration-.*).*target=\(.*\)\/jcr:content.*/\1/p" error.log | sort | uniq -c
28115
```

Ensuite, vérifiez que seules les pages principales (en haut dans la hiérarchie) ont une configuration d’Analytics référencée.

Pour plus d’informations sur la création de services d’importateur de données personnalisés dans AEM, lisez l’article suivant. [https://helpx.adobe.com/experience-manager/using/polling.html](https://helpx.adobe.com/experience-manager/using/polling.html).

## Problèmes de gestion dynamique des balises (hérités) {#dtm-legacy-issues}

### La balise de script de gestion dynamique des balises n’est pas rendue dans la source de la page {#the-dtm-script-tag-is-not-rendered-in-the-page-source}

La balise de script de [gestion dynamique des balises](/help/sites-administering/dtm.md) n’est pas correctement incluse dans la page, même si la configuration a été référencée dans l’onglet des propriétés de la page des [Services cloud](/help/sites-developing/extending-cloud-config.md).

#### Solution {#solution-2}

Pour résoudre ce problème, vous pouvez essayer les méthodes suivantes :

* Assurez-vous que les propriétés chiffrées peuvent être déchiffrées (notez que le chiffrement peut utiliser une clé générée automatiquement différente pour chaque instance AEM). Pour plus d’informations, voir aussi la section [Prise en charge du chiffrement des propriétés de configuration](/help/sites-administering/encryption-support-for-configuration-properties.md).
* Republier les configurations trouvées dans `/etc/cloudservices/dynamictagmanagement`
* Vérifier les listes de contrôle d’accès sur `/etc/cloudservices`. Les listes de contrôle d’accès doivent être les suivantes :

   * allow; jcr:read; webservice-support-servicelibfinder
   * allow; jcr:read; tout le monde; rep:glob:&amp;ast;/defaul/&amp;ast;
   * allow; jcr:read; tout le monde; rep:glob:&amp;ast;/default
   * allow; jcr:read; tout le monde; rep:glob:&amp;ast;/public/&amp;ast;
   * allow; jcr:read; tout le monde; rep:glob:&amp;ast;/public

Pour plus d’informations sur la gestion des listes de contrôle d’accès, consultez la page [Administration et sécurité des utilisateurs](/help/sites-administering/security.md#permissions-in-aem).

## Problèmes d’intégration dans Target {#target-integration-issues}

### Le contenu cible n’est pas visible en mode Aperçu lors de l’utilisation de composants de page personnalisés {#targeted-content-not-visible-in-preview-mode-when-using-custom-page-components}

Ce problème se produit parce que les composants de page personnalisés n’incluent pas le bon JSP ou les bibliothèques clientes qui gèrent les intégrations de gestion dynamique des balises dans Target.

#### Solution {#solution-3}

Vous pouvez essayer les solutions suivantes :

* Assurez-vous que la variable `headlibs.jsp` (le cas échéant) `/apps/<CUSTOM-COMPONENTS-PATH>/headlibs.jsp`) comprend les éléments suivants :

```
<%@include file="/libs/cq/cloudserviceconfigs/components/servicelibs/servicelibs.jsp" %>
<sly data-sly-resource="${'contexthub' @ resourceType='granite/contexthub/components/contexthub'}"/>
```

* Assurez-vous que la variable `head.html` (le cas échéant) `/apps/<CUSTOM-COMPONENTS-PATH>/head.html`) **ne fait pas** incluez de manière sélective des headlibs d’intégration spécifiques comme dans l’exemple ci-dessous :

```
<!-- DO NOT MANUALLY INCLUDE SPECIFIC CLOUD SERVICE HEADLIBS LIKE THIS -->
<meta data-sly-include="/libs/cq/dtm/components/dynamictagmanagement/headlibs.jsp" data-sly-unwrap/>
```

Le fichier `servicelibs.jsp` ajoute les objets d’analyse JavaScript requis et charge les bibliothèques de service cloud associées au site web. Pour le service Target, les bibliothèques sont chargées via l’événement `/libs/cq/analytics/components/testandtarget/headlibs.jsp`

Le jeu de bibliothèques chargé dépend du type de bibliothèque cliente cible (`mbox.js` ou`at.js` ) ) utilisé dans la configuration de Target.

Lorsque vous utilisez la gestion dynamique des balises pour fournir `mbox.js` ou `at.js`, assurez-vous que les bibliothèques sont chargées avant que le contenu soit rendu. L’utilisation de systèmes de gestion des balises qui chargent ces bibliothèques de manière asynchrone risque d’entraîner des problèmes lors de l’exécution du code JavaScript spécifique à la cible.

Pour plus d’informations, consultez la page [Développement pour le contenu ciblé](/help/sites-developing/target.md#understanding-the-target-component).

### L’erreur « Identifiant de suite de rapports manquant dans l’initialisation d’AppMeasurement » s’affiche dans la console du navigateur. {#the-error-missing-report-suite-id-in-appmeasurement-initialization-is-displayed-in-the-browser-console}

Ce problème peut apparaître lorsque Adobe Analytics est implémenté sur le site web à l’aide de la gestion dynamique des balises et utilise le code personnalisé. La cause utilise la variable `s = new AppMeasurement()` pour instancier la variable `s` .

#### Solution {#solution-4}

Utilisation `s_gi` au lieu de `new AppMeasurement` méthode d’instanciation. Par exemple :

```
var s_account="INSERT-RSID-HERE"
var s=s_gi(s_account)
```

### Une offre par défaut s’affiche de manière aléatoire au lieu de l’offre correcte {#a-default-offer-is-randomly-displayed-instead-of-the-correct-offer}

Ce problème peut avoir plusieurs causes :

* Chargement des bibliothèques clientes Target ( `mbox.js` ou `at.js`) en utilisant de manière asynchrone des systèmes de gestion des balises tiers peut rompre le ciblage de manière aléatoire. Les bibliothèques cibles doivent être chargées de manière synchrone dans l’en-tête de la page. C’est toujours le cas lorsque les bibliothèques sont diffusées à partir d’AEM.

* Chargement de deux bibliothèques clientes Target ( `at.js`) simultanément, par exemple, l’un utilisant la gestion dynamique des balises et l’autre utilisant la configuration Target dans AEM. Cela peut entraîner des conflits pour la définition d’`adobe.target` si les versions d’`at.js` diffèrent.

#### Solution {#solution-5}

Vous pouvez essayer les solutions suivantes :

* Assurez-vous que le code client utilisé pour charger les bibliothèques de gestion dynamique des balises (qui, à leur tour, chargent les bibliothèques cible) est exécuté de manière synchrone dans l’[en-tête de la page](/help/sites-developing/target.md#enabling-targeting-with-adobe-target-on-your-pages).
* si le site est configuré pour utiliser la gestion dynamique des balises pour fournir les bibliothèques Target, assurez-vous que la variable **Bibliothèque cliente fournie par DTM** est cochée dans la variable [Configuration de Target](https://helpx.adobe.com/experience-manager/6-3/sites/administering/using/target-configuring.html) pour le site.

### Une offre par défaut s’affiche toujours à la place de l’offre correcte lors de l’utilisation d’AT.js 1.3+ {#a-default-offer-is-always-displayed-instead-of-correct-offer-when-using-at-js}

Les versions prêtes à l’emploi AEM 6.2 et 6.3 ne sont pas compatibles avec AT.js version 1.3.0+. Avec la version 1.3.0 d’AT.js qui introduit la validation des paramètres pour ses API, `adobe.target.applyOffer()` nécessite un paramètre &quot;mbox&quot; qui n’est pas fourni par la variable `atjs-itegration.js` code.

#### Solution {#solution-6}

Pour résoudre ce problème, modifiez `atjs-itegration.js` et ajoutez le `"mbox": mboxName` dans l’objet de paramètre pour `adobe.target.applyOffer()` comme suit :

```
adobe.target.getOffer({
    "mbox": mboxName,
    "params": params,
    "success": function (response) {
        adobe.target.applyOffer({
            "mbox": mboxName, //<--- ADDED PARAM
            "selector": "#" + mboxName,
            "offer": response
        })
    },
```

### La page Objectifs et paramètres n’affiche pas la section Sources de création {#the-goals-settings-page-does-not-show-the-reporting-sources-section}

Ce problème est probablement un problème qui [Configuration d’Analytics Cloud A4T](/help/sites-administering/target-configuring.md) problème de configuration.

#### Solution {#solution-7}

Vous devez vérifier qu’A4T est correctement activé pour votre compte Target en envoyant la demande de vérification suivante à AEM :

```
http://localhost:4502/etc/cloudservices/testandtarget/<YOUR-CONFIG>/jcr:content.a4t.json
 
{
    "a4tEnabled": true,
    "sharedsecret": "SECRET",
    "proxyUrl": "/libs/cq/contentinsight/content/proxy.reportingservices.json",
    "active": "true",
    "pageName": "",
    "url": "https://api5.omniture.com/rs/0.5/",
    "username": "USER@DOMAIN"
}
```

Si la réponse contient la ligne `a4tEnabled:false`, contactez l’[Assistance clientèle Adobe](https://helpx.adobe.com/fr/contact.html) pour que votre compte soit correctement configuré.

### API Target utiles {#helpful-target-apis}

Vous trouverez ci-dessous deux API Target qui peuvent s’avérer utiles lors du dépannage des problèmes dans Target :

* Pour récupérer le point de terminaison Target pour un code client spécifique

```
https://admin.testandtarget.omniture.com/rest/v1/endpoint/<CLIENTCODE>.json
 
{"api":"https://admin<N>.testandtarget.omniture.com/admin/rest/v1"}
```

* Pour récupérer le profil d’un client

```
https://admin<N>.testandtarget.omniture.com/admin/rest/v1/clients/<CLIENT>?email=<EMAIL>&password=<PASSWORD>
 
Response for N=4, CLIENT-dayintegrationintern
{
    "clientCode": "dayintegrationintern",
    "companyName": "Day Integration - Internal",
    "omnitureCompanyId": "Day Integration Internal",
    "softTraxId": -1,
    "address1": "XYZ",
    "city": "San Francisco",
    "state": "ca",
    "zip": "94107",
    "country": "UNITED STATES",
    "locale": "de_DE",
    "timeZone": "Europe/Berlin",
    "phone": "XX-XX-XXXX",
    "serviceLevel": "Up to 100,000",
    "privileges": [
        "a4t",
        "hosts",
        "TnT-SC-integration",
        "mvt",
        "steps",
        "testing-campaigns",
        "view-snapshot",
        "on-site-editor",
        "optimizing-campaign",
        "third-party-id-support",
        "landing-page-campaigns",
        "segment",
        "rest-create-user",
        "advanced-targeting",
        "mobile-device-targeting",
        "beta",
        "geolocation"
    ]
}
```
