---
title: Notions fondamentales sur les flux d’activités
seo-title: Activity Stream Essentials
description: Liste des activités récentes effectuées par un membre ou liste des activités récentes sur un seul fil de contenu
seo-description: List of recent activites performed by a member or a list of recent activities on a single thread of content
uuid: 6e4734bb-52a8-4670-b665-e640108b036e
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 8cc04993-4021-4cb7-b973-5afc4da1ed11
exl-id: 74dcbefa-e670-419b-af9b-b3d3c593ebaa
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 3%

---

# Notions fondamentales sur les flux d’activités {#activity-stream-essentials}

Les activités d’un membre de la communauté connecté, comme la publication sur un forum ou un blog, sont collectées dans un flux qui peut être filtré et affiché de différentes manières via la configuration du composant Flux d’activités.

La possibilité de suivre ajoute un autre ensemble d’activités lorsque les membres de la communauté suivent des messages d’intérêt ou d’autres membres de la communauté.

Tous [sites communautaires](overview.md#communitiessites) incluez une page de profil utilisateur pour le membre connecté qui affichera les activités du membre de la même manière.

## Concepts {#concepts}

Un *flux d’activités* est la liste des activités récentes effectuées par un membre ou une liste des activités récentes sur un seul fil de contenu, comme un sujet de forum ou un blog.

Un membre peut suivre un flux d’activité en suivant un autre individu ou un autre contenu.

A *fil d&#39;actualités* est une fusion des flux d’activité suivis par un membre dans un seul flux.

A [graphique social](essentials-socialgraph.md) capture les relations suivantes d’un membre à un autre.

## Principes élémentaires pour le côté client {#essentials-for-client-side}

<table> 
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td> 
   <td>social/activitystreams/components/hbs/activitystreams</td> 
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>incluable</strong></a></td> 
   <td>Non</td> 
  </tr>
  <tr>
   <td> <a href="clientlibs.md"><strong>clientllibs</strong></a></td> 
   <td>cq.social.hbs.activitystreams</td> 
  </tr>
  <tr>
   <td> <strong>templates</strong></td> 
   <td> /libs/social/activitystreams/components/hbs/activitystreams/activitystreams.hbs<br /> /libs/social/activitystreams/components/hbs/activitystreams/activity/activity-title.hbs<br /> /libs/social/activitystreams/components/hbs/activitystreams/activity/activity.hbs</td> 
  </tr>
  <tr>
   <td> <strong>css</strong></td> 
   <td> /libs/social/activitystreams/components/hbs/activitystreams/clientlibs/activitystreams.css</td> 
  </tr>
  <tr>
   <td><strong> properties</strong></td> 
   <td>Voir <a href="activities.md">Fonctionnalité Flux d’activités</a></td> 
  </tr>
 </tbody>
</table>

* [Personnalisations côté client](client-customize.md)

## Principes élémentaires pour le côté serveur {#essentials-for-server-side}

* [API Flux d’activités](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/activitystreams/api/package-frame.html)

* [API du récepteur de flux d’activités](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/activitystreams/listener/api/package-frame.html)

* [Personnalisations côté serveur](server-customize.md)

### Fonction Flux d&#39;activités {#activity-stream-function}

Une structure de site de communauté qui inclut [Fonction de flux d’activités](functions.md#activity-stream-function), inclut une `activity streams` composant.
