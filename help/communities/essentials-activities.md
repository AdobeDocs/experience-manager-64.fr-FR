---
title: Activité Stream Essentials
seo-title: Activité Stream Essentials
description: Liste des activités récentes effectuées par un membre ou une liste d'activités récentes sur un seul thread de contenu
seo-description: Liste des activités récentes effectuées par un membre ou une liste d'activités récentes sur un seul thread de contenu
uuid: 6e4734bb-52a8-4670-b665-e640108b036e
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 8cc04993-4021-4cb7-b973-5afc4da1ed11
translation-type: tm+mt
source-git-commit: 4d64494dff34108d32e060a96209df697b2ce11f
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 2%

---


# Activité Stream Essentials {#activity-stream-essentials}

Les activités d&#39;un membre de la communauté connecté, comme la publication sur un forum ou un blog, sont collectées dans un flux qui peut être filtré et affiché de différentes manières via la configuration du composant de flux d&#39;activité.

La capacité de suivre ajoute un autre ensemble d&#39;activités lorsque les membres de la communauté suivent des messages d&#39;intérêt ou d&#39;autres membres de la communauté.

Tous les sites [de la](overview.md#communitiessites) communauté incluent une page de profil d’utilisateur pour le membre connecté qui affiche les activités du membre de la même manière.

## Concepts {#concepts}

Un flux *d’* activité est la liste des activités récentes effectuées par un membre ou une liste d’activités récentes sur un seul fil de contenu, tel qu’un sujet de forum ou un blog.

Un membre peut suivre un flux d&#39;activités, soit en suivant un autre individu, soit en suivant un autre contenu.

Un flux *d&#39;* information est une fusion des flux d&#39;activités suivis par un membre dans un flux unique.

Un graphique [](essentials-socialgraph.md) social capture les relations suivantes d’un membre à un autre.

## Essentials for Client-Side {#essentials-for-client-side}

<table> 
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td> 
   <td>flux sociaux/d’activités/composants/hbs/flux d’activités</td> 
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>inclus</strong></a></td> 
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
   <td>Voir Fonction Flux <a href="activities.md">d’Activité</a></td> 
  </tr>
 </tbody>
</table>

* [Personnalisations côté client](client-customize.md)

## Essentials for Server-Side {#essentials-for-server-side}

* [API Activités Streams](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/activitystreams/api/package-frame.html)

* [API du module d&#39;écoute des flux d&#39;Activité](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/activitystreams/listener/api/package-frame.html)

* [Personnalisations côté serveur](server-customize.md)

### Fonction Flux d&#39;activités {#activity-stream-function}

Une structure de site communautaire qui comprend la fonction [de flux d’](functions.md#activity-stream-function)Activité, comprend un `activity streams` composant configuré.
