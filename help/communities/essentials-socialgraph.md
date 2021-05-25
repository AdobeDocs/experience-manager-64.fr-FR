---
title: Notions fondamentales sur les graphiques sociaux
seo-title: Notions fondamentales sur les graphiques sociaux
description: suivi du composant et présentation des composants suivants
seo-description: suivi du composant et présentation des composants suivants
uuid: 8ea33760-62b1-4de2-b07f-bc2417ade156
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: f8d85d72-0215-4680-a334-e37a530fba58
exl-id: 55aa015e-e0e4-411e-8e28-75006ae3090b
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '278'
ht-degree: 12%

---

# Notions fondamentales sur les graphiques sociaux {#social-graph-essentials}

La possibilité pour un membre de la communauté de suivre les [activités](essentials-activities.md) et d’être suivi est établie par deux composants :

Le composant `follow`doit être associé à une autre ressource. Cette association est déjà établie pour les membres et fonctionnalités de communautés existants dans un [site communautaire](overview.md#communitiessites).

Le composant `following`répertorie les membres qui suivent le membre actuel ou qui sont suivis par le membre actuel. Ce graphique social des relations entre les membres est inclus dans le profil d’utilisateur établi pour un site de communauté.

## Principes élémentaires pour le côté client {#essentials-for-client-side}

### Abonnement {#following}

<table> 
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td> 
   <td>social/socialgraph/components/hbs/relations</td> 
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>incluable</strong></a></td> 
   <td>Non</td> 
  </tr>
  <tr>
   <td> <a href="clientlibs.md"><strong>clientllibs</strong></a></td> 
   <td>cq.social.hbs.socialgraph</td> 
  </tr>
  <tr>
   <td> <strong>templates</strong></td> 
   <td> /libs/social/socialgraph/components/hbs/relationships/relationships.hbs</td> 
  </tr>
  <tr>
   <td> <strong>css</strong></td> 
   <td> /libs/social/socialgraph/components/hbs/relationships/clientlibs/relationships.css</td> 
  </tr>
  <tr>
   <td><strong> properties</strong></td> 
   <td>Voir <a href="socialgraph.md">Utilisation de Social Graph</a></td> 
  </tr>
  <tr>
   <td><strong> propriété facultative<br /></strong></td> 
   <td>
    <ul> 
     <li>Nom: <strong><code>outgoing</code></strong></li> 
     <li>Type : booléen</li> 
     <li>Valeur : <br /> 
      <ul> 
       <li><i>true  </i>- le  <code>following</code> composant répertorie les membres qui sont actuellement membres connectés <code>follows</code></li> 
       <li><i>false  </i>- le  <code>following</code> composant répertorie les membres qui  <code>follow </code>le membre actuellement connecté</li> 
      </ul> </li> 
    </ul> <p>La valeur par défaut est <i>true</i> si la propriété est manquante. Actuellement, il n’est pas possible de définir cette propriété à l’aide de la boîte de dialogue de modification en mode création. La propriété doit être ajoutée à une instance du noeud <code>following </code>à l’aide de <a href="../../help/sites-developing/developing-with-crxde-lite.md">CRXDE|Lite</a>.</p> </td> 
  </tr>
 </tbody>
</table>

### S’abonner {#follow}

| **resourceType** | social/socialgraph/components/hbs/following |
|---|---|
| [**incluable**](scf.md#add-or-include-a-communities-component) | Non |
| **templates** | /libs/social/socialgraph/components/hbs/following/following.hbs |
| **css** | /libs/social/socialgraph/components/hbs/following/clientlibs/following.css |

* [Personnalisations côté client](client-customize.md)

## Principes élémentaires côté serveur {#essentials-for-server-side}

* [API Social Graph](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/graph/client/api/package-frame.html)

* [Points de terminaison du graphique des réseaux sociaux](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/graph/client/endpoint/package-frame.html)

* [Personnalisations côté serveur](server-customize.md)
