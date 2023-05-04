---
title: Notions fondamentales sur le contenu proposé
seo-title: Featured Content Essentials
description: Utilisation du contenu des fonctionnalités
seo-description: Working with feature content
uuid: b376828a-1431-4d16-ad6b-b23a3ea62a75
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 781625f1-39a0-4e34-948c-d4eab35dd5c1
exl-id: 4805db0f-18d2-4bbc-a4d6-eaafa7a4c152
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 9%

---

# Notions fondamentales sur le contenu proposé {#featured-content-essentials}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Cette page fournit les informations essentielles pour utiliser le contenu présenté.

Contrairement à l’épinglage d’une publication en haut d’un forum, cette fonctionnalité permet de mettre en évidence le contenu n’importe où sur le site de la communauté.

## Principes élémentaires pour le côté client {#essentials-for-client-side}

<table> 
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td> 
   <td>social/commons/components/hbs/featuredcontent</td> 
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>incluable</strong></a></td> 
   <td>Non</td> 
  </tr>
  <tr>
   <td> <a href="clientlibs.md"><strong>clientllibs</strong></a></td> 
   <td> <i>default</i></td> 
  </tr>
  <tr>
   <td> <strong>templates</strong></td> 
   <td> /libs/social/commons/components/hbs/featuredcontent/featuredcontent.hbs<br /> /libs/social/commons/components/hbs/featuredtopic/featuredtopic.hbs</td> 
  </tr>
  <tr>
   <td> <strong>css</strong></td> 
   <td> /libs/social/commons/components/hbs/featuredcontent/clientlibs/featuredcontent.css</td> 
  </tr>
  <tr>
   <td><strong> properties</strong></td> 
   <td>Voir <a href="featured.md">Contenu en vedette</a></td> 
  </tr>
 </tbody>
</table>

* [Personnalisations côté client](client-customize.md)

### Fonction Bibliothèque de fichiers {#file-library-function}

Une structure de site de communauté qui inclut [Fonction Contenu en vedette](functions.md#featured-content-function), inclut une `featured content` composant.
