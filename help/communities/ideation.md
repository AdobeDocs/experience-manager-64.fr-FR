---
title: Notions fondamentales relatives aux idées
seo-title: Ideation Essentials
description: Présentation de la fonctionnalité d’orientation
seo-description: Ideation feature overview
uuid: abaf03ee-8bf4-4241-96c3-474c95a30a88
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: a9e4f2f0-d1ff-40c0-abcf-645e40586a84
exl-id: 7fb68293-c6e3-4793-b433-205bcfc23e20
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 8%

---

# Notions fondamentales relatives aux idées {#ideation-essentials}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Cette page fournit les informations essentielles pour travailler avec la fonction d’idéation, qui est similaire à un forum, mais qui permet d’enregistrer en tant que brouillon et d’avoir un aspect plus collaboratif.

## Principes élémentaires pour le côté client {#essentials-for-client-side}

<table> 
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td> 
   <td>social/ideation/components/hbs/ideation</td> 
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>incluable</strong></a></td> 
   <td>Non</td> 
  </tr>
  <tr>
   <td> <a href="clientlibs.md"><strong>clientllibs</strong></a></td> 
   <td>cq.social.hbs.votes<br /> cq.social.hbs.liking<br /> cq.social.hbs.ideation</td> 
  </tr>
  <tr>
   <td> <strong>templates</strong></td> 
   <td> /libs/social/ideation/components/hbs/ideation/ideation.hbs<br /> /libs/social/ideation/components/hbs/ideation/ideationlists.hbs<br /> /libs/social/ideation/components/hbs/ideation/composer.hbs</td> 
  </tr>
  <tr>
   <td> <strong>css</strong></td> 
   <td> /libs/social/ideation/components/hbs/ideation/clientlibs/ideation.css</td> 
  </tr>
  <tr>
   <td><strong> properties</strong></td> 
   <td>Voir <a href="ideation-feature.md">Fonctionnalité d’orientation</a></td> 
  </tr>
 </tbody>
</table>

* [Personnalisations côté client](client-customize.md)

### Fonction de conceptualisation {#ideation-function}

Une structure de site de communauté qui inclut [Fonction d’information](functions.md#ideation-function), inclut une `ideation` composant.
