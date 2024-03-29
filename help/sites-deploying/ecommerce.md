---
title: Présentation du commerce électronique
seo-title: eCommerce Overview
description: AEM eCommerce générique est disponible dans le cadre de l’installation standard et vous fournit toutes les fonctionnalités de la structure eCommerce.
seo-description: AEM generic eCommerce is available as part of the standard installation and provides you with the full functionality of the eCommerce framework.
uuid: 7be42b1e-f1d6-4891-96f8-0133b3a299a1
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: e-commerce
content-type: reference
discoiquuid: cb043066-aefc-4b68-b302-2b5dd710a786
feature: Commerce Integration Framework
exl-id: d84cd0ec-4586-45c1-a07a-a4d50fcbb629
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 59%

---

# Présentation du commerce électronique{#ecommerce-overview}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Le commerce électronique générique AEM est disponible dans le cadre de l’installation standard et vous offre toutes les fonctionnalités de la structure de commerce électronique.

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


## Déploiement d’autres mises en oeuvre {#deploying-other-implementations}

* [SAP Commerce Cloud](/help/sites-deploying/sap-commerce-cloud.md)
* [Commerce Cloud Salesforce](https://github.com/adobe/commerce-salesforce)
* [Magento](https://www.adobe.io/apis/experiencecloud/commerce-integration-framework/integrations.html#!AdobeDocs/commerce-cif-documentation/master/integrations/02-AEM-Magento.md)

>[!NOTE]
>
>Pour plus d’informations sur les concepts et l’administration des implémentations eCommerce, consultez [Administration d’eCommerce](/help/sites-administering/ecommerce.md).
>
>Pour plus d’informations sur les possibilités d’extension d’eCommerce, consultez [Développement du e-commerce](/help/sites-developing/ecommerce.md).
