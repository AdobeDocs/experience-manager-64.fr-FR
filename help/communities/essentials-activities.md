---
title: Essentials du flux d’activités
seo-title: Essentials du flux d’activités
description: Liste des activités récentes effectuées par un membre ou liste des activités récentes sur un seul thread de contenu
seo-description: Liste des activités récentes effectuées par un membre ou liste des activités récentes sur un seul thread de contenu
uuid: 6e4734bb-52a8-4670-b665-e640108b036e
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 8cc04993-4021-4cb7-b973-5afc4da1ed11
translation-type: tm+mt
source-git-commit: 4d64494dff34108d32e060a96209df697b2ce11f

---


# Essentials du flux d’activités {#activity-stream-essentials}

Les activités d’un membre de la communauté connecté, comme les publications sur un forum ou un blog, sont collectées dans un flux qui peut être filtré et affiché de différentes manières via la configuration du composant de flux d’activité.

La capacité de suivre ajoute un autre ensemble d&#39;activités lorsque les membres de la communauté suivent des messages d&#39;intérêt ou d&#39;autres membres de la communauté.

Tous les sites [de](overview.md#communitiessites) la communauté incluent une page de profil utilisateur pour le membre connecté qui affichera les activités des membres de la même manière.

## Concepts {#concepts}

Un flux *d’* activité est la liste des activités récentes exécutées par un membre ou la liste des activités récentes sur un seul fil de contenu, tel qu’un sujet de forum ou un blog.

Un membre peut suivre un flux d’activité, soit en suivant un autre individu, soit en suivant un autre contenu.

Un flux d’ *actualités* est une fusion des flux d’activités suivis par un membre dans un seul flux.

Un graphique [](essentials-socialgraph.md) social capture les relations suivantes entre un membre et un autre.

## Essentials for Client-Side {#essentials-for-client-side}

<table> 
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td> 
   <td>social/activitystream/components/hbs/activitystream</td> 
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>inclus</strong></a></td> 
   <td>Non</td> 
  </tr>
  <tr>
   <td> <a href="clientlibs.md"><strong>clientllibs</strong></a></td> 
   <td>cq.social.hbs.activitystream</td> 
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
   <td>Voir Fonctionnalité <a href="activities.md">des flux d’activité</a></td> 
  </tr>
 </tbody>
</table>

* [Personnalisations côté client](client-customize.md)

## Essentials for Server-Side {#essentials-for-server-side}

* [API Flux d’activités](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/activitystreams/api/package-frame.html)

* [API d’écouteur de flux d’activité](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/activitystreams/listener/api/package-frame.html)

* [Personnalisations côté serveur](server-customize.md)

### Fonction Flux d&#39;activités {#activity-stream-function}

Une structure de site de la communauté qui comprend la fonction [Flux d’](functions.md#activity-stream-function)activité, comprend un `activity streams` composant configuré.
