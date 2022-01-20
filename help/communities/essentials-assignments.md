---
title: Notions fondamentales sur les affectations
seo-title: Assignments Essentials
description: Présentation de la fonction Affectations pour les communautés d’activation
seo-description: Assignments feature overview for enablement communities
uuid: 8310decf-174d-4e93-8c92-4a9583077b7a
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 796781e6-5cab-4ea1-b484-0945bc8febbf
exl-id: 310d9086-36b6-42ea-835f-c77d75e880cb
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '213'
ht-degree: 13%

---

# Notions fondamentales sur les affectations {#assignments-essentials}

Cette page fournit les informations essentielles pour utiliser la fonctionnalité d’affectations de [communauté d&#39;activation](overview.md#enablement-community) sites.

La fonction Affectations permet d’affecter des ressources d’activation et des parcours d’apprentissage aux membres des communautés d’activation.

## Principes élémentaires pour le côté client {#essentials-for-client-side}

<table> 
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td> 
   <td>social/enablement/components/hbs/myassigned</td> 
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>incluable</strong></a></td> 
   <td>Non</td> 
  </tr>
  <tr>
   <td> <a href="clientlibs.md"><strong>clientllibs</strong></a></td> 
   <td>cq.social.enablement.hbs.breadcrumbs<br /> cq.social.enablement.hbs.myassigned<br /> cq.social.enablement.hbs.resource<br /> cq.social.enablement.hbs.learningpath</td> 
  </tr>
  <tr>
   <td> <strong>templates</strong></td> 
   <td> /libs/social/enablement/components/hbs/myassigned/myassigned.hbs</td> 
  </tr>
  <tr>
   <td> <strong>css</strong></td> 
   <td> /libs/social/enablement/components/hbs/myassigned/clientlibs/myassigned.css</td> 
  </tr>
  <tr>
   <td><strong> properties</strong></td> 
   <td>Voir <a href="assignments.md">Fonctionnalité Affectations</a></td> 
  </tr>
 </tbody>
</table>

### État d’achèvement et de réussite {#completion-and-success-status}

Les états de fin et de réussite sont utilisés dans les rapports, ainsi que dans les bannières d’état sur les affectations.

État d’achèvement :

* Non attribué
* Non démarré (nouveau)
* En cours
* Terminé

État de réussite:

* Inconnu
* Réussite
* Échec

Les seules combinaisons possibles d’achèvement et d’état de réussite sont les suivantes :

| **Fin** | **Réussite** |
|---|---|
| Non démarré | Inconnu |
| En cours | Inconnu |
| Terminé | Réussite |
| Terminé | Échec |

## Principes élémentaires pour le côté serveur {#essentials-for-server-side}

### Fonction Affectations {#assignments-function}

Une structure de site de communauté qui inclut [Fonction Affectations](functions.md#assignments-function), inclut une ` [assignments](assignments.md)` composant.

### API de référence {#reference-apis}

* [API d’activation](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/enablement/reporting/model/api/package-summary.html)

* [API de création de rapports](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/reporting/dv/api/package-summary.html)

* [API Reporting Analytics](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/reporting/analytics/api/package-summary.html)
