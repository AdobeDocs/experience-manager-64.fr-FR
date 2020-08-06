---
title: Affectations Essentials
seo-title: Affectations Essentials
description: Présentation de la fonction Affectations pour les communautés d’activation
seo-description: Présentation de la fonction Affectations pour les communautés d’activation
uuid: 8310decf-174d-4e93-8c92-4a9583077b7a
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 796781e6-5cab-4ea1-b484-0945bc8febbf
translation-type: tm+mt
source-git-commit: 4d64494dff34108d32e060a96209df697b2ce11f
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 13%

---


# Affectations Essentials {#assignments-essentials}

Cette page fournit les informations essentielles pour travailler sur les fonctions d&#39;attribution des sites de la communauté [d&#39;](overview.md#enablement-community) activation.

La fonction des affectations permet d’affecter des ressources d’activation et des chemins d’apprentissage aux membres des communautés d’activation.

## Essentials for Client-Side {#essentials-for-client-side}

<table> 
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td> 
   <td>social/activation/composants/hbs/myassigné</td> 
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>inclus</strong></a></td> 
   <td>Non</td> 
  </tr>
  <tr>
   <td> <a href="clientlibs.md"><strong>clientllibs</strong></a></td> 
   <td>cq.social.enablement.hbs.breadcrumbs<br /> cq.social.enablement.hbs.myassigné<br /><br /> cq.social.enablement.hbs.resource cq.social.enablement.hbs.learnpath</td> 
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
   <td>Voir Fonction <a href="assignments.md">Affectations</a></td> 
  </tr>
 </tbody>
</table>

### État d’achèvement et de réussite {#completion-and-success-status}

Les états d’achèvement et de réussite sont utilisés dans les rapports ainsi que dans les bannières d’état sur les affectations.

État d’achèvement :

* Non attribué
* Non démarré (nouveau)
* En cours
* Terminer

État de réussite:

* Inconnu
* Réussite
* Échec

Les seules combinaisons possibles d’achèvement et d’état de réussite sont les suivantes :

| **Fin** | **Réussite** |
|---|---|
| Non démarré | Inconnu |
| En cours | Inconnu |
| Terminer | Réussite |
| Terminer | Échec |

## Essentials for Server-Side {#essentials-for-server-side}

### Fonction Affectations {#assignments-function}

Une structure de site communautaire qui comprend la fonction [](functions.md#assignments-function)Affectations, comprend un ` [assignments](assignments.md)` composant configuré.

### API de référence {#reference-apis}

* [API d&#39;activation](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/enablement/reporting/model/api/package-summary.html)

* [API Rapports](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/reporting/dv/api/package-summary.html)

* [API d&#39;analyse de Rapports](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/reporting/analytics/api/package-summary.html)