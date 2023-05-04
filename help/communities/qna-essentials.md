---
title: Notions fondamentales sur la qualité de vie
seo-title: QnA Essentials
description: Fonctionnalité de forum Questions et réponses
seo-description: Questions and answers forum feature
uuid: c718a8e3-b3bd-4db9-8c0f-6dd973d40583
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: ceace3aa-78a5-485e-b519-630479e087d8
exl-id: 99f8afda-1771-471b-bd0c-99960a453bc9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '284'
ht-degree: 4%

---

# Notions fondamentales sur la qualité de vie {#qna-essentials}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Cette page fournit les informations essentielles pour utiliser la fonction de forum de questions et réponses (Q&amp;R).

## Principes élémentaires pour le côté client {#essentials-for-client-side}

<table> 
 <tbody>
  <tr>
   <td> resourceType</td> 
   <td>social/qna/components/hbs/qnaforum</td> 
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component">incluable</a></td> 
   <td>Non</td> 
  </tr>
  <tr>
   <td> <a href="clientlibs.md">clientllibs</a></td> 
   <td>cq.ckeditor<br /> cq.social.hbs.votes<br /> cq.social.hbs.qna</td> 
  </tr>
  <tr>
   <td> templates</td> 
   <td> /libs/social/qna/components/hbs/qnaforum/qnaforum.hbs<br /> /libs/social/qna/components/hbs/qnaforum/activity-title.hbs</td> 
  </tr>
  <tr>
   <td> css</td> 
   <td> /libs/social/qna/components/hbs/qnaforum/clientlibs/qnaforum.css</td> 
  </tr>
  <tr>
   <td> properties</td> 
   <td>Voir <a href="working-with-qna.md">Fonctionnalité du forum Q&amp;R</a></td> 
  </tr>
 </tbody>
</table>

* [Personnalisations côté client](client-customize.md)

## Principes élémentaires pour le côté serveur {#essentials-for-server-side}

* [API Q&amp;R](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/qna/client/api/package-summary.html)

* [Points de fin Q&amp;R](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/qna/client/endpoints/package-summary.html)

* [Personnalisations côté serveur](server-customize.md)

### Fonction Q&amp;R {#qna-function}

Une structure de site de communauté qui inclut [Fonction Q&amp;R](functions.md#qna-function) dispose d’un `QnA` , ainsi que les paramètres affectant la modération et le balisage. La fonction Q&amp;R prend en charge l’identification d’une [groupe d’utilisateurs de membres privilégiés](users.md#privileged-members-group).

### Accès aux publications du forum Q&amp;R (UGC) {#accessing-qna-forum-posts-ugc}

Le contenu généré par l’utilisateur doit être modéré à l’aide de l’une des méthodes standard de modération.\
Voir [Modération de contenu généré par l’utilisateur](moderate-ugc.md).

À partir de AEM 6.1 Communities, utilisez un [magasin commun](working-with-srp.md) pour le contenu généré par l’utilisateur inclut l’accès programmatique au contenu généré par l’utilisateur, quelle que soit l’option de stockage choisie (comme ASRP, MSRP ou JSRP).

**L’emplacement et le format du contenu créé par l’utilisateur dans le référentiel peuvent être modifiés sans avertissement.**.

Voir :

* [Présentation du fournisseur de ressources de stockage](srp.md) - présentation et utilisation du référentiel
* [Principes de base de la SRP et du contenu généré par l’utilisateur](srp-and-ugc.md) - Méthodes d’utilitaire SRP et exemples
* [Accès au contenu généré par l’utilisateur avec SRP](accessing-ugc-with-srp.md) - Instructions de codage
* [Refactorisation de SocialUtils](socialutils.md) - mappage de méthodes d’utilitaire obsolètes aux méthodes d’utilitaire SRP actuelles
