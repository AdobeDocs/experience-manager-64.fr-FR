---
title: eCommerce
seo-title: eCommerce
description: AEM eCommerce aide les spécialistes du marketing à offrir des expériences d’achat personnalisées sur le web, les appareils mobiles et les médias sociaux.
seo-description: AEM eCommerce helps marketers deliver branded, personalized shopping experiences across web, mobile, and social touchpoints.
uuid: 14af7a3a-7211-4a56-aeef-1603128d5d8a
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: e-commerce
content-type: reference
discoiquuid: 68799110-8183-40fe-be4f-2a7c7a7b3018
feature: Commerce Integration Framework
exl-id: 3c046e16-5f54-4a16-aa5b-256b679808fa
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '792'
ht-degree: 53%

---

# eCommerce{#ecommerce}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

* [Concepts](/help/sites-administering/concepts.md)
* [Administration (générique)](/help/sites-administering/generic.md)
* [SAP Commerce Cloud](/help/sites-administering/sap-commerce-cloud.md)
* [Commerce Cloud Salesforce](https://github.com/adobe/commerce-salesforce)
* [Magento](https://www.adobe.io/apis/experiencecloud/commerce-integration-framework/integrations.html#!AdobeDocs/commerce-cif-documentation/master/integrations/02-AEM-Magento.md)

Adobe propose deux versions de framework d’intégration de Commerce :

|  | CIF sur site | CIF Cloud |
|-------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------|
| Versions d’AEM prises en charge | AEM on-premise ou AMS 6.x | AEM AMS 6.4 et 6.5 |
| back-end | - AEM, Java <br> - Intégration monolithique, mappage de prégénération (modèle)<br> - Référentiel JCR | - Magento <br>- Java et JavaScript <br>- Aucune donnée Commerce stockée dans le référentiel JCR |
| Front-end | AEM pages générées côté serveur | Application de page mixte (rendu hybride) |
| Catalogue de produits | - Importateur de produits, éditeur, mise en cache dans AEM <br>- Catalogues réguliers avec des pages AEM ou proxy | - Pas d’importation de produit <br>- Modèles génériques <br>- Données à la demande via le connecteur |
| Évolutivité | - Peut prendre en charge jusqu’à quelques millions de produits (selon le cas d’utilisation) <br> - Mise en cache sur Dispatcher | - Aucune limitation de volume <br>- Mise en cache sur Dispatcher ou CDN |
| Modèle de données normalisé | Non | Oui, schéma GraphQL Magento |
| Disponibilité | Oui :<br> - Commerce Cloud SAP (extension mise à jour pour prendre en charge AEM 6.4 et Hybris 5 (par défaut) et maintenir la compatibilité avec Hybris 4) <br>- Commerce Cloud Salesforce (connecteur open-source pour prendre en charge AEM 6.4) | Oui, en open source via GitHub. <br> Magento Commerce (prend en charge Magento 2.3.2 (par défaut) et compatible avec Magento 2.3.1). |
| Quand l’utiliser | Cas d’utilisation limités : dans le cas de scénarios dans lesquels de petits catalogues statiques doivent être importés | Solution préférée dans la plupart des cas d’utilisation |

eCommerce, avec la gestion de l’information sur les produits (PIM), gère les activités d’un site web axé sur la vente de produits par le biais d’une boutique en ligne :

* Création, durée de vie et obsolescence d’un produit
* Gestion des prix
* Gestion des transactions
* Gestion de catalogues entiers
* Enregistrements de stockage en direct et centralisés
* Interfaces web

AEM eCommerce aide les spécialistes du marketing à offrir des expériences d’achat personnalisées sur le web, les appareils mobiles et les médias sociaux. L’environnement de création AEM vous permet de personnaliser les pages et les composants en fonction du contexte du visiteur cible et des stratégies de marchandisage. par exemple :

* Pages de produits
* Composants du panier
* Composants de passage en caisse

La mise en œuvre d’eCommerce permet d’accéder en temps réel à des informations sur le produit. Cela peut être utilisé pour appliquer :

* Intégrité des informations sur les produits
* Tarifs
* Inventaire de la gestion des stocks
* Variations du statut d’un panier

>[!NOTE]
>
>Pour utiliser le framework d’intégration avec les prestataires eCommerce externes, vous devez tout d’abord installer les packages nécessaires. Pour plus d’informations, reportez-vous à [Déploiement d’e-commerce](/help/sites-deploying/ecommerce.md).
>
>Pour plus d’informations sur les possibilités d’extension d’eCommerce, consultez [Développement du e-commerce](/help/sites-developing/ecommerce.md).

## Principales fonctionnalités {#main-features}

AEM eCommerce fournit :

* Différents **composants AEM prêts à l’emploi** illustrent ce qu’il est possible d’obtenir pour votre projet :

   * Affichage des produits
   * Panier
   * Extraction
   * Produits récemment consultés
   * Bons
   * et autres

   ![chlimage_1-150](assets/chlimage_1-150.png)

   >[!NOTE]
   >
   >La structure d’intégration fournie par AEM vous permet également de créer des composants AEM supplémentaires pour les fonctionnalités commerciales, indépendamment de votre moteur eCommerce spécifique.

* **Rechercher** - à l’aide de :

   * la recherche AEM
   * Recherche du système eCommerce
   * Une recherche tierce
   * Ou une combinaison de ces trois fonctions

   ![chlimage_1-151](assets/chlimage_1-151.png)

* Utilise les capacités d’AEM de **présenter du contenu sur plusieurs canaux**, qu’il s’agisse d’une fenêtre de navigateur ou d’un appareil mobile. Ainsi, vous proposez votre contenu au format adapté pour vos visiteurs.

   ![chlimage_1-152](assets/chlimage_1-152.png)

* La possibilité de **développer votre propre mise en œuvre de l’intégration en fonction du [framework d’AEM eCommerce](#the-framework)**.

   Les deux mises en œuvre actuellement disponibles reposent sur la même base et complètent l’API générale (la structure). La mise en œuvre d’une nouvelle intégration implique seulement de mettre en œuvre les fonctionnalités dont votre intégration a besoin. Les composants frontaux peuvent être utilisés par les nouvelles mises en œuvre puisqu’ils utilisent des interfaces (et sont donc indépendants de la mise en œuvre).

* Possibilité de développer un **commerce axé sur l’expérience en fonction des données et de l’activité des acheteurs**, Vous pouvez ainsi réaliser de nombreux scénarios :

   * Par exemple, une réduction des frais de livraison proposée lorsque le montant total d’une commande dépasse un montant spécifique.
   * Autre exemple : la possibilité de proposer des offres à certaines occasions à partir des informations de profil (tel le lieu). Elles peuvent ensuite être mises en évidence, selon d’autres facteurs, le cas échéant.

   Dans l’exemple ci-dessous, un teaser est affiché, car le contenu du panier est inférieur à 75 € :

   ![chlimage_1-153](assets/chlimage_1-153.png)

   Cela peut être modifié lorsque le contenu du panier dépasse 75 $ :

   ![chlimage_1-154](assets/chlimage_1-154.png)

* Et d’autres fonctionnalités, notamment :

   * Contenu du panier conservé d’une session à l’autre
   * Historique des commandes exhaustif
   * Mise à jour du catalogue express

## Le cadre {#the-framework}

Le [Concepts](/help/sites-administering/concepts.md) couvre la structure de manière plus détaillée, mais ce qui suit fournit une vue à grande vitesse de la structure :

### Quoi ? {#what}

* La structure d’intégration fournit l’API, une gamme de composants pour illustrer les fonctionnalités et plusieurs extensions pour fournir des exemples de méthodes de connexion.
* La structure fournit la structure de base nécessaire à la mise en oeuvre d’un projet.
* Le framework est extensible.
* Le framework ne fournit pas de site prêt à l’emploi. Un certain travail de développement reste nécessaire pour adapter le framework à vos spécifications.

### Pourquoi ? {#why}

* Fournir les mécanismes de base nécessaires pour réaliser rapidement un site de commerce électronique personnalisé.
* Tp offre la flexibilité nécessaire au développement d’un site d’e-commerce réel.
* Illustrer les bonnes pratiques.
