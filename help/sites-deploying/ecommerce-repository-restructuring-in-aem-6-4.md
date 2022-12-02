---
title: Restructuration des référentiels e-Commerce dans AEM 6.4
seo-title: E-Commerce Repository Restructuring in AEM 6.4
description: Découvrez comment apporter les modifications nécessaires pour migrer vers la nouvelle structure de référentiel dans AEM 6.4 pour e-Commerce.
seo-description: Learn how to make the necessary changes in order to migrate to the new repository structure in AEM 6.4 for E-Commerce.
uuid: 1fff1a4b-c8d0-4016-92fb-e2ea26e3a302
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: repo_restructuring
discoiquuid: 28c92e7d-2106-4333-afa6-c5528a00d7b4
feature: Upgrading
exl-id: 6adcc1a4-eb0f-4410-8219-dbd7e6bbe469
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '201'
ht-degree: 100%

---

# Restructuration des référentiels e-Commerce dans AEM 6.4{#e-commerce-repository-restructuring-in-aem}

Comme indiqué dans la page parent [Restructuration des référentiels dans AEM 6.4](/help/sites-deploying/repository-restructuring.md), les clients effectuant une mise à niveau vers AEM 6.4 doivent utiliser cette page pour évaluer le travail associé aux modifications des référentiels ayant un impact sur la solution de e-Commerce d’AEM. Certaines modifications demandent du travail lors du processus de mise à niveau vers AEM 6.4, tandis que d’autres peuvent être différées jusqu’à une mise à niveau vers la version 6.5.

## Avec la mise à niveau vers la version 6.4 {#with-upgrade}

### Données sur les produits, les commandes, les collections, les classifications, les méthodes d’expédition et les modes de paiement {#product-order-collections-classifications-shipping-methods-and-payment-methods-data}

<table> 
 <tbody>
  <tr>
   <td><strong>Emplacement précédent</strong></td> 
   <td><p><code>/etc/commerce/products</code></p> <p><code>/etc/commerce/orders</code></p> <p><code>/etc/commerce/collections</code></p> <p><code>/etc/commerce/classifications</code></p> <p><code>/etc/commerce/shipping-methods</code></p> <p><code>/etc/commerce/payment-methods</code></p> </td> 
  </tr>
  <tr>
   <td><strong>Nouveaux emplacements</strong></td> 
   <td><p><code>/var/commerce/products</code></p> <p><code>/var/commerce/orders</code></p> <p><code>/var/commerce/collections</code></p> <p><code>/var/commerce/classifications</code></p> <p><code>/var/commerce/shipping-methods</code></p> <p><code>/var/commerce/payment-methods</code></p> </td> 
  </tr>
  <tr>
   <td><strong>Conseil de restructuration</strong></td> 
   <td><p>Vous pouvez utiliser une tâche de <a href="/help/sites-deploying/lazy-content-migration.md" target="_blank">migration différée</a> pour migrer les données e-Commerce.</p> <p>La procédure effectue les étapes suivantes :</p> 
    <ul> 
     <li>ajuste les références à l’ancien emplacement pour pointer vers le nouvel emplacement</li> 
     <li>transfère le contenu de l’ancien emplacement vers le nouvel emplacement</li> 
     <li>supprime l’ancien emplacement pour éventuellement activer l’utilisation du nouvel emplacement dans l’ensemble du système</li> 
    </ul> <p>Les emplacements couverts par la tâche sont les suivants :</p> 
    <ul> 
     <li>/etc/commerce/products</li> 
     <li>/etc/commerce/collections<br /> </li> 
     <li>/etc/commerce/orders<br /> </li> 
     <li>/etc/commerce/payment-methods<br /> </li> 
     <li>/etc/commerce/shipping-methods<br /> </li> 
    </ul> <p>Pour les catalogues plus volumineux, il est recommandé d’exécuter la tâche de migration de commerce individuellement en transmettant la propriété système Java suivante à AEM :</p> <p><code>propertyname: com.adobe.upgrade.forcemigration</code></p> <p><code>property value: com.day.cq.compat.codeupgrade.impl.cq64.CQ64CommerceMigrationTask</code></p> <p>Après la migration, AEM doit être redémarré.</p> </td> 
  </tr>
  <tr>
   <td><strong>Remarques</strong></td> 
   <td>N/A<br /> </td> 
  </tr>
 </tbody>
</table>
