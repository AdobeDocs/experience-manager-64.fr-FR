---
title: Activer AEM pour rechercher des documents PDF protégés par la sécurité documentaire et des documents Microsoft Office
seo-title: Enable AEM to search document security protected PDF and Microsoft Office documents
description: 'Découvrez comment permettre à la recherche AEM native d’effectuer une recherche de texte intégral sur des documents PDF protégés par DRM.  '
seo-description: Learn how to enable native AEM search to perform full-text search on DRM protected PDF documents.
uuid: dba882f8-bad4-4122-a0df-03cf087afb23
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_document_security
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 7eebef08-83b9-4b56-90ec-35ab3b0c27e8
noindex: true
feature: Document Security
exl-id: dbf97dc1-cf05-4d45-859e-60ff01186e51
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '643'
ht-degree: 100%

---

# Activer AEM pour rechercher des documents PDF protégés par la sécurité documentaire et des documents Microsoft Office{#enable-aem-to-search-document-security-protected-pdf-and-microsoft-office-documents}

Adobe Experience Manager fournit une interface utilisateur permettant de rechercher différents actifs stockés dans AEM. La recherche native peut effectuer une recherche de texte intégral recherchez du texte dans les formats de document couramment utilisés tels que les fichiers texte brut, les documents Microsoft Office et les fichiers PDF. Vous pouvez également étendre la recherche native de sorte à ce qu’elle effectue une recherche de texte intégral dans des documents PDF protégés DRM et des documents Microsoft Office.

Effectuez les étapes suivantes pour permettre à AEM de rechercher des documents PDF protégés par sécurité documentaire et des documents Microsoft Office :

## Avant de commencer {#before-you-start}

* Installez et configurez la sécurité documentaire AEM Forms.
* Ajoutez le package sun.util.calendar à la liste blanche de la **Configuration du pare-feu de désérialisation.** La configuration est répertoriée à l’adresse `https://[server]:[port]/system/console/configMgr`.
* Vérifiez que tous les bundles AEM sont en cours d’utilisation. Les lots sont répertoriés à l’adresse `https://[server]:[port]/system/console/bundles`. Si tous les lots ne sont pas actifs, patientez, puis vérifiez leur statut après quelques minutes.

## Établir une connexion sécurisée dans le flux de production AEM Forms (AEM Forms on JEE) {#establish-a-secure-connection-within-aem-forms-workflow-aem-forms-on-jee}

Une connexion sécurisée permet un flux d’informations harmonieux entre AEM Forms sur JEE et les services OSGi s’exécutant sur le même serveur. Utilisez l’une des méthodes suivantes pour établir une connexion sécurisée :

* Configurer le bundle de SDK client AEM Forms avec les informations d’identification d’administrateur d’AEM Forms on JEE
* Configurer le bundle de SDK client AEM Forms à l’aide de l’authentification mutuelle

### Configurer le bundle de SDK client AEM Forms avec les informations d’identification d’administrateur d’AEM Forms on JEE {#configure-aem-forms-client-sdk-bundle-with-aem-forms-on-jee-admin-credentials}

1. Accédez au gestionnaire de configuration et connectez-vous à AEM en tant qu’administrateur. L’URL par défaut est https://&lt;Nomserveur>:&lt;port>/lc/system/console/configMgr.
1. Recherchez et ouvrez le bundle de SDK client AEM Forms. Spécifiez la valeur des propriétés suivantes :

   * **URL du serveur :** spécifiez l’URL HTTP d’AEM Forms on JEE. Pour activer la communication via https, redémarrez le serveur AEM Forms sur JEE avec le paramètre -Djavax.net.ssl.trustStore=&lt;chemin dʼaccès du fichier de stockage de clés AEM Forms sur JEE>.
   * **Nom du service** : ajoutez RightsManagementService à la liste des services spécifiés.
   * **Nom d’utilisateur :** indiquez le nom d’utilisateur du compte AEM Forms on JEE à utiliser pour lancer des appels à partir du serveur AEM Forms on JEE. Le compte spécifié doit disposer des autorisations pour appeler Document services sur le serveur AEM Forms on JEE.
   * **Mot de passe** : indiquez le mot de passe du compte AEM Forms on JEE mentionné dans le champ Nom d’utilisateur.

   Cliquez sur **Enregistrer**. AEM est activé pour rechercher des documents PDF protégés par la sécurité documentaire et des documents Microsoft Office.

### Configurer le bundle de SDK client AEM Forms à l’aide de l’authentification mutuelle {#configure-aem-forms-client-sdk-bundle-using-mutual-authentication}

1. Activez l’authentification mutuelle pour AEM Forms on JEE. Pour plus d’informations, voir [CAC et authentification mutuelle](https://helpx.adobe.com/fr/livecycle/kb/cac-mutual-authentication.html).
1. Accédez au gestionnaire de configuration et connectez-vous à AEM en tant qu’administrateur. L’URL par défaut est https://&lt;Nomserveur>:&lt;port>/lc/system/console/configMgr.
1. Recherchez et ouvrez le bundle de SDK client AEM Forms. Spécifiez la valeur des propriétés suivantes :

   * **URL du serveur** : spécifiez l’URL HTTPS d’AEM Forms on JEE. Pour activer la communication via https, redémarrez le serveur AEM Forms sur JEE avec le paramètre -Djavax.net.ssl.trustStore=&lt;chemin dʼaccès du fichier de stockage de clés AEM Forms sur JEE>.
   * **Activer SSL bidirectionnel** : activez l’option Activer SSL bidirectionnel.
   * **URL du fichier KeyStore** : indiquez l’URL du fichier de stockage de clés.
   * **URL du fichier TrustStore** : indiquez l’URL du fichier de magasin approuvé.
   * **Mot de passe du KeyStore** : indiquez le mot de passe du fichier de stockage des clés.
   * **Mot de passe TrustStore** : indiquez le mot de passe du fichier de magasin approuvé.
   * **Nom du service** : ajoutez RightsManagementService à la liste des services spécifiés.

   Cliquez sur **Enregistrer**. AEM est activé pour rechercher des documents PDF protégés par la sécurité documentaire et des documents Microsoft Office

## Indexer un document PDF ou Microsoft Office protégé par un exemple de stratégie {#index-a-sample-policy-protected-pdf-or-microsoft-office-document}

1. Connectez-vous à AEM Assets en tant qu’administrateur.
1. Créez un dossier dans AEM Digital Asset Manager et téléchargez un document PDF ou Microsoft Office protégé par une stratégie vers le dossier que vous venez de créer. Désormais, vous pouvez rechercher le contenu des documents protégés par une stratégie à l’aide de la recherche AEM. Il doit renvoyer le document contenant le texte recherché.
