---
title: Résumé des nouvelles fonctionnalités | AEM 6.4 Forms
seo-title: Résumé des nouvelles fonctionnalités | AEM 6.4 Forms
description: Résumé des nouvelles fonctionnalités et améliorations de la version 6.4 d’AEM Forms.
seo-description: Résumé des nouvelles fonctionnalités et améliorations de la version 6.4 d’AEM Forms.
uuid: 152068ec-47a8-43f4-b9c8-3a17d1f085fe
contentOwner: vishgupt
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: introduction
discoiquuid: 436aa424-d05e-4f3d-90ac-5ff3b05ddba8
translation-type: tm+mt
source-git-commit: f2b0d37a0666f2a0be9e7034da12dddf0c56fb25
workflow-type: tm+mt
source-wordcount: '2016'
ht-degree: 80%

---


# Résumé des nouvelles fonctionnalités | AEM 6.4 Forms {#new-features-summary-aem-forms}

Résumé des nouvelles fonctionnalités et améliorations de la version 6.4 d’AEM Forms.

AEM Forms comporte plusieurs nouvelles fonctionnalités et améliorations qui optimisent la création, la gestion et les expériences utilisateur avec des formulaires adaptatifs et des communications interactives.

Lisez ci-après la présentation rapide des nouvelles fonctionnalités et améliorations. Consultez la documentation pour de plus amples informations. Vous pouvez également consulter les [notes de mise à jour](/help/release-notes/forms.md) d’AEM 6.4 Forms. Pour obtenir la documentation complète de la version 6.4 de Forms, consultez le [AEM 6.4 Forms Guide](/help/forms/home.md).

## Communications interactives {#interactive-communications}

![gestion de la correspondance](assets/correspondence-management.png)

Interactive Communications centralise et gère la création, l&#39;assemblage et la diffusion de correspondances sécurisées, personnalisées et interactives telles que la correspondance d&#39;affaires, les lettres, les documents, les déclarations, les avis de prestations, les prospectus de gestion de patrimoine, les courriels marketing, les factures et les kits de bienvenue.

Les communications interactives utilisent la même technologie, les mêmes processus et les mêmes composants sous-jacents que les formulaires adaptatifs pour créer des communications multicanaux réactives, tout comme les formulaires adaptatifs réactifs.

La communication interactive offre des avantages significatifs :

* Fournit l’intégration en standard avec le modèle de données de formulaire pour permettre un accès facile et rapide aux bases de données back end et à d’autres systèmes CRM tels que MS Dynamics
* Fournit une interface de création intégrée pour les canaux d’impression et web
* Fournit une interface de création basée sur un glisser-déposer, similaire à la création de formulaires adaptatifs, pour les canaux d’impression et web.

La communication interactive est l’approche par défaut et recommandée pour créer des communications client. Pour continuer à utiliser les lettres dans AEM 6.3 Forms et AEM 6.2 Forms, vous devez installer un package de compatibilité.

### Création d’une communication interactive multicanaux  {#multi-channel-interactive-communication-authoring}

Grâce à la communication interactive, vous pouvez créer et modifier des documents d’impression et web à partir d’un seul éditeur de document. En utilisant les mêmes fragments de document pour créer des rendus des deux canaux, vous évitez de fournir de multiples efforts.
![printweb_2](assets/printweb_2.png)

Pour plus d&#39;informations, voir [Présentation des communications interactives](/help/forms/using/interactive-communications-overview.md).

### Éditeur de document WYSIWYG {#wysiwyg-document-editor}

L’éditeur de document glisser-déposer WYSIWYGM est adapté aux entreprises. L’interface intuitive, la fonction de glisser-déposer, les composants standard, les modèles de données et le référentiel intégré des actifs permettent la création facile et rapide d’une communication interactive.

Pour créer une communication interactive ou en modifier une existante, les utilisateurs professionnels peuvent utiliser les blocs de construction suivants : Canaux, contenu, propriétés, ressources, composants et sources de données.

![glisser-n-déposer-lf](assets/drag-n-drop-lf.png)

Pour plus d’informations, voir [Introduction à la création de communications interactives](/help/forms/using/introduction-interactive-communication-authoring.md).

### Générer automatiquement la version web à partir du contenu imprimé dans la communication interactive {#auto-generate-web-version-from-print-content-in-interactive-communication}

Les auteurs peuvent générer automatiquement du contenu de document Web à partir des documents d’impression pour créer, prévisualisation et modifier des documents Web et d’impression dans le même éditeur. Les auteurs de communications interactives peuvent créer une fois et publier sur tous les canaux. Les auteurs de communications interactives peuvent utiliser les mêmes fragments de document dans le canal papier et le  Web pour éviter la duplication des efforts.

Pour plus d’informations, voir [canal d’impression et canal Web](/help/forms/using/web-channel-print-channel.md).

### Utiliser des thèmes pour définir l’aspect du canal web de la communication interactive {#use-themes-to-style-web-channel-of-interactive-communication}

La communication interactive prend en charge des thèmes. Vous pouvez créer des thèmes et les appliquer à votre communication interactive. Un thème contient des détails de style pour les composants et les panneaux. Vous pouvez réutiliser un thème sur différentes communications interactives pour leur donner une apparence et une identité graphique cohérentes et communes.

AEM Forms comprend un thème prêt à l&#39;emploi pour Interactive Communications. À l’aide d’un thème, vous pouvez également personnaliser l’apparence d’une communication interactive sur un périphérique.

Pour plus d’informations, voir [Thèmes dans AEM Forms](/help/forms/using/themes.md).

### Interface améliorée de l’agent {#enhanced-agent-interface}

L’interface utilisateur de l’agent prend désormais en charge l’impression et l’aperçu web de la communication interactive. Dans la même interface utilisateur de l&#39;agent, vous pouvez choisir de modifier le canal Web du canal d&#39;impression et de la prévisualisation de votre communication interactive multicanal. Les champs, les variables, les éléments FDM et les fragments de document dans le canal d’impression peuvent être configurés pour être modifiés par l’agent dans l’interface utilisateur de l’agent. La prise en charge du modèle de données de formulaire vous permet de générer des aperçus avec des exemples de données pré-remplies.

Pour plus d&#39;informations, voir [Préparation et envoi de communications interactives à l&#39;aide de l&#39;interface utilisateur de l&#39;agent](/help/forms/using/prepare-send-interactive-communication.md).

### Présenter des informations dans les graphiques {#present-information-in-charts}

La communication interactive prend en charge les graphiques dans le canal d’impression et le canal web pour des communications plus riches. À l’aide de graphiques (circulaire, anneau, barre et colonne), vous pouvez condenser et présenter une large quantité d’informations pour faciliter l’interprétation et l’analyse.

![graphique-2](assets/chart-2.png) ![graphique](assets/chart.png)

Pour plus d&#39;informations, voir [Utilisation de graphiques dans les communications interactives](/help/forms/using/chart-component-interactive-communications.md).

### Des connecteurs de données prêts à l’emploi pour pré-remplir des documents {#out-of-the-box-data-connectors-to-prefill-documents}

La communication interactive fournit l’intégration des données avec des outils d’entreprise permettant de se connecter à plusieurs systèmes d’entreprise, notamment les systèmes CRM, et de personnaliser les données dans des documents.

![fdm_ad](assets/fdm_ad.png)

Pour plus d’informations, reportez-vous à la section [Utilisation d’un modèle de données de formulaire](/help/forms/using/using-form-data-model.md).

### Éditeur de fragment de document amélioré {#enhanced-document-fragment-editor}

Vous pouvez maintenant utiliser des éléments et des règles FDM dans des fragments de documents de communication interactive.

* Prise en charge des éléments de modèle de données de formulaire
* Afficher ou masquer un fragment d’actif/texte utilisant des règles
* Valider la valeur d’un élément/d’une variable
* Exécuter des fonctions pour calculer la valeur d&#39;une expression mathématique

Pour en savoir plus, voir:

* [Textes dans les communications interactives](/help/forms/using/texts-interactive-communications.md)
* [Conditions dans les communications interactives](/help/forms/using/conditions-interactive-communications.md)

### Package de compatibilité pour les actifs existants  {#compatibility-package-for-existing-assets}

Par défaut, les actifs de lettres des versions précédentes d’AEM Forms ne sont pas pris en charge dans cette version. Pour continuer à utiliser les lettres dans AEM 6.3 Forms et AEM 6.2 Forms, vous devez installer un package de compatibilité.

## Intégration de données  {#data-integration}

![](do-not-localize/data-integeration-1.png)

[L’intégration de données AEM Forms](/help/forms/using/data-integration.md) vous permet de configurer des sources de données variées, telles que des bases de données, des services web RESTful ou SOAP et des services OData, pour créer un modèle de données de formulaire que vous pouvez utiliser pour lier des données, pré-remplir et invoquer des services dans des formulaires et des documents adaptatifs.

Plusieurs nouvelles fonctionnalités et améliorations sont disponibles dans l’intégration de données de cette version.

### Créer un modèle de données de formulaire sans source de données {#create-form-data-model-without-data-source}

Les utilisateurs professionnels et les auteurs de formulaire peuvent désormais créer un modèle de données de formulaire, y compris ses entités et propriétés, sans configurer de source de données, et peuvent être utilisés pour la création de formulaires et de documents adaptatifs. Vous pouvez lier le modèle de données de formulaire aux sources de données ultérieurement. Il élimine les dépendances des sources de données pour créer des formulaires et des documents à l’aide du modèle de données de formulaire.

De même, vous pouvez créer des entités et des propriétés enfant dans un modèle de données de formulaire existant et les lier ultérieurement aux entités et propriétés correspondantes dans une source de données.

Pour plus d’informations, voir [Création d’un modèle de données de formulaire](/help/forms/using/create-form-data-models.md).

### Créer des propriétés calculées {#create-computed-properties}

Les auteurs et les développeurs de formulaires peuvent créer des propriétés calculées dans un modèle de données de formulaire. Ils vous permettent de calculer une valeur pour la propriété en créant des règles ou une logique sur les données disponibles dans les sources de données configurées. Une règle est une expression qui est évaluée lorsque les données sont chargées dans le modèle de données de formulaire ou lorsque les valeurs des propriétés dans l’expression changent. Par exemple, une propriété calculée appelée Versements calcule le montant mensuel à payer pour un prêt en fonction du taux d’intérêt spécifié dans la source de données et du montant du prêt et de la durée spécifiés par l’utilisateur dans le formulaire.

Une propriété calculée réside localement dans un modèle de données de formulaire et n’existe pas dans une source de données. Vous pouvez utiliser des propriétés calculées dans des formulaires adaptatifs et des communications interactives.

Pour plus d’informations, voir [Utilisation du modèle de données de formulaire](/help/forms/using/work-with-form-data-model.md).

### Prévisualiser les formulaires et les documents avec des exemples de données {#preview-forms-and-documents-with-sample-data}

Le modèle de données de formulaire permet de générer des exemples de données pour les propriétés de toutes les entités d’un modèle de données de formulaire. Les données générées correspondent aux types de données configurés pour les propriétés. Lorsque vous prévisualisez un formulaire adaptatif ou un document associé au modèle de données de formulaire, celui-ci est restitué avec des exemples de données pré-remplies.

L’exemple de données est un ensemble de valeurs aléatoires qui change chaque fois que vous le générez. Cependant, vous pouvez modifier et enregistrer les exemples de données qui persistent même si vous les régénérez. Par exemple, si vous modifiez et enregistrez les exemples de données pour les propriétés Prénom et Nom et si vous ajoutez ultérieurement une autre propriété ou entité dans le modèle de données de formulaire et régénérez les exemples de données, les propriétés Prénom et Nom afficheront les valeurs enregistrées tandis que les valeurs des autres propriétés seront régénérées.

Pour plus d’informations, voir [Utiliser le modèle de données de formulaire](/help/forms/using/using-form-data-model.md).

### Actualiser les définitions de source de données {#refresh-data-source-definitions}

Toute mise à jour dans les propriétés ou les entités de source de données ne se reflète pas automatiquement dans les modèles de données de formulaire associés. L’éditeur de modèles de données de formulaire contient désormais ![refresh_forms_di](assets/refresh_forms_di.png) (Actualiser les définitions de source de données) qui invalide le cache du serveur et récupère le schéma mis à jour de la source de données pour qu’il se reflète immédiatement dans le modèle de données de formulaire.

### Configurer les sources de données à l’aide de l’interface utilisateur tactile {#configure-data-sources-using-touch-user-interface}

Avec cette version, la configuration des services cloud pour les sources de données est disponible dans l’interface utilisateur tactile. En outre, l’emplacement de configuration des services cloud a été remplacé par **[!UICONTROL Outils > Cloud Services > Sources de données]**. Voir [Configurer les sources de données](/help/forms/using/configure-data-sources.md).

## Formulaires adaptatifs {#adaptive-forms}

![simplification-of-authoring-forms-and-documents_hero-image_2](assets/simplification-of-authoring-forms-and-documents_hero-image_2.png)

### Améliorer les performances des formulaires adaptatifs avec le chargement différé amélioré {#improve-performance-of-adaptive-forms-with-enhanced-lazy-loading}

La fonctionnalité de chargement différé dans les formulaires adaptatifs retarde l’initialisation des fragments de formulaire jusqu’à ce qu’ils soient nécessaires. Elle améliore les performances des formulaires volumineux en réduisant le temps requis pour générer un formulaire, ce qui améliore l’expérience utilisateur.

Plusieurs améliorations ont été apportées à la fonctionnalité de chargement différé au sein de cette version :

* Les composants Pièce jointe et Conditions générales sont pris en charge dans les fragments de formulaire avec la fonctionnalité chargement différé activée.
* Les fragments de formulaire adaptatif avec activation du chargement différé sont pris en charge dans des panneaux répétables.
* Les formulaires adaptatifs avec fragments à chargement différé sont pris en charge dans l’application AEM Forms.

## Processus AEM basés sur l’utilisation de Forms  {#forms-centric-aem-workflows}

![aem-forms-workflow-on-osgi-](assets/aem-forms-workflow-on-osgi-.png)

La fonctionnalité Processus AEM basés sur l’utilisation de Forms permet une création et un déploiement rapides des processus pour diverses tâches de la pile OSGi. Vous n’avez plus besoin d’installer la fonctionnalité de gestion des processus disponible sur la pile JEE, ce qui simplifie le déploiement et l’élimination des coûts de serveur d’applications et d’infrastructure. Pour plus d’informations, voir [Flux de travail basé sur l’utilisation de Forms sur OSGi](/help/forms/using/aem-forms-workflow.md).

Les améliorations suivantes ont été apportées aux Workflows d&#39;AEM orientés Forms : ・

* L’éditeur de modèle de processus est disponible dans l’interface utilisateur tactile. Il vous aide à réduire le temps requis pour la création de processus AEM basés sur l’utilisation de Forms.
* Étape de processus pour l’envoi de courriers électroniques. Par exemple, vous pouvez utiliser l’étape Envoyer un courrier électronique pour envoyer un document d’enregistrement à la fin d’un processus.
* Étape de processus pour l’utilisation de services de modèle de données de formulaire dans un modèle de processus. Cette étape vous permet d’invoquer des services d’intégration de données sans écrire de code personnalisé. Par exemple, vous pouvez appeler un service GET pour obtenir des informations sur les employés à partir des archives d’une base de données sans écrire de code personnalisé.

## Application AEM Forms {#aem-forms-app}

![aem-forms-app](assets/aem-forms-app.png)

L’application AEM Forms permet aux agents de terrain de synchroniser leurs périphériques mobiles avec un serveur AEM Forms, puis de travailler sur leurs formulaires. L’application est exécutée sans accroc lorsque le périphérique est hors connexion et que les données y sont enregistrées en local et synchronisées avec le serveur lorsque le périphérique est de nouveau en ligne. Pour plus d’informations, voir [Application AEM Forms](/help/forms/using/aem-forms-app.md).

Voici les améliorations apportées à l’application AEM Forms :

* Les formulaires adaptatifs avec fragments à chargement différé sont pris en charge dans l’application AEM Forms.
* Les formulaires adaptatifs avec modèle de données de formulaire sont pris en charge dans l’application AEM Forms.

## Document Security {#document-security}

![aem-forms-document-sécurité-](assets/aem-forms-document-security-.png)

Document Security vous permet de distribuer en toute sécurité toute information enregistrée sous un format pris en charge. Grâce à Document Security, seuls les utilisateurs autorisés peuvent utiliser vos documents. Les principaux changements apportés à la sécurité des documents sont les suivants :

* Document Security fournit une [bibliothèque portable de protection (PPL)](/help/forms/using/document-security-offerings.md) pour protéger un document localement sans l’envoyer vers le serveur AEM Forms. Seules les informations d’identification de sécurité et les détails de la stratégie transitent sur le réseau vers le serveur AEM Forms. AEM 6.4 Forms inclut la bibliothèque portable de protection (PPL) dans un format de bundle OSGi. Vous pouvez maintenant installer directement la bibliothèque PPL sur un serveur AEM Forms et utiliser conjointement les fonctionnalités AEM et PPL.
* Le SDK Document Security C++ et la bibliothèque PPL C++ peuvent être compilés avec Microsoft Visual Studio 2013. La version précédemment prise en charge était Microsoft Visual Studio 2010.

## Plateformes prises en charge {#supported-platforms}

AEM Forms peut être installé à l’aide de n’importe quelle combinaison de systèmes d’exploitation, serveurs d’applications, bases de données, pilotes de base de données, JDK, serveurs LDAP et serveurs de messagerie électronique pris en charge. Voici les principales modifications apportées aux plateformes prises en charge :

<table> 
 <tbody> 
  <tr> 
   <td>Composant</td> 
   <td>Prise en charge ajoutée</td> 
   <td>Prise en charge supprimée</td> 
  </tr> 
  <tr> 
   <td>Systèmes d’exploitation</td> 
   <td> 
    <ul> 
     <li>Microsoft Windows Server 2016</li> 
     <li>Oracle Linux® 7 Update 3</li> 
    </ul> </td> 
   <td> 
    <ul> 
     <li>IBM AIX 7.2 <sup>[1]</sup><br /> </li> 
     <li>Solaris 11 <sup>[1]</sup></li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Serveurs d’applications<br /> </td> 
   <td> 
    <ul> 
     <li>Red Hat JBoss EAP 7</li> 
    </ul> </td> 
   <td> 
    <ul> 
     <li>IBM Weblogic 12.1.3</li> 
     <li>IBM WebSphere 8.5.5</li> 
     <li>Red Hat JBoss EAP 6</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Bases de données</td> 
   <td> 
    <ul> 
     <li>Microsoft SQL Server 2016</li> 
     <li>MySQL 5.7.19 et versions ultérieures</li> 
     <li>IBM DB2 11.1</li> 
     <li>Architecture Oracle Multitenant</li> 
    </ul> </td> 
   <td> 
    <ul> 
     <li>Microsoft SQL Server 2012<br /> </li> 
     <li>Microsoft SQL Server 2014</li> 
     <li>MySQL 5.5</li> 
     <li>IBM DB2 10.5<br /> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Serveurs LDAP</td> 
   <td> 
    <ul> 
     <li>Microsoft Active Directory 2016</li> 
     <li>IBM Tivoli Directory Server 6.4</li> 
    </ul> </td> 
   <td> 
    <ul> 
     <li>Microsoft Active Directory 2008</li> 
     <li>IBM Tivoli Directory Server 6.3</li> 
     <li>Oracle Directory Server Enterprise Édition 7.0</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Serveurs de messagerie</td> 
   <td> 
    <ul> 
     <li>Microsoft Office 365</li> 
    </ul> </td> 
   <td> 
    <ul> 
     <li>Novell GroupWise 7</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Connecteurs</td> 
   <td> 
    <ul> 
     <li>Connector for Microsoft Sharepoint 2016</li> 
     <li>Connector for EMC Documentum 7.3</li> 
    </ul> </td> 
   <td> 
    <ul> 
     <li>Connector for Microsoft Sharepoint 2007</li> 
     <li>Connector for Microsoft Sharepoint 2010</li> 
     <li>Connector for IBM FileNet 5.0</li> 
     <li>Connector for EMC Documentum 6.7</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Navigateurs</td> 
   <td> 
    <ul> 
     <li>Apple Safari 11.x sur macOS</li> 
     <li>Apple Safari 11.x sous iOS</li> 
    </ul> </td> 
   <td> 
    <ul> 
     <li>Navigateur Blackberry sur les appareils Blackberry Z30 et Q10</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td>Application AEM Forms<br /> </td> 
   <td> 
    <ul> 
     <li>Android 4.4 ou ultérieure</li> 
     <li>Apple iOS 10 ou ultérieure</li> 
    </ul> </td> 
   <td> </td> 
  </tr> 
 </tbody> 
</table>

1. Les systèmes d’exploitation AIX et Solaris sont disponibles uniquement pour les clients de mise à niveau.
