---
title: Notions fondamentales sur le vote
seo-title: Voting Essentials
description: Composant Vote - Aperçu
seo-description: Voting component overview
uuid: ed0a771d-1c14-4fbf-ab6a-a028e5ee2e2a
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 1a947a06-6a5c-4be9-b2fa-e5fa809ff3b8
exl-id: f2ecd59c-a311-4e4a-b1a8-2bc3afe0599d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 3%

---

# Notions fondamentales sur le vote {#voting-essentials}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Le composant Vote, une [tally](tally.md) subclass est un outil utile qui permet aux membres d’évaluer un élément de contenu particulier en sélectionnant simplement les flèches haut ou bas pour indiquer leur opinion.

Le placement de plusieurs instances d’un composant Vote sur la même page est autorisé ; chaque instance doit être configurée avec une `tally name` .

La publication anonyme d&#39;un vote n&#39;est pas prise en charge. Les visiteurs du site ne doivent s’inscrire et se connecter qu’une seule fois pour participer au vote. Le visiteur (membre) connecté peut changer son vote à tout moment.

## Principes élémentaires pour le côté client {#essentials-for-client-side}

<table> 
 <tbody> 
  <tr> 
   <td> <strong>resourceType</strong></td> 
   <td>social/tally/components/hbs/votes</td> 
  </tr> 
  <tr> 
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>incluable</strong></a></td> 
   <td>Oui - les propriétés peuvent être modifiées dans <i>design </i>mode</td> 
  </tr> 
  <tr> 
   <td> <a href="client-customize.md#clientlibs-for-scf"><strong>clientlibs</strong></a></td> 
   <td> cq.social.hbs.voting</td> 
  </tr> 
  <tr> 
   <td> <strong>templates</strong></td> 
   <td><p> /libs/social/tally/components/hbs/voting/voting.hbs<br /> /libs/social/tally/components/hbs/voting/activity-title.hbs</p> </td> 
  </tr> 
  <tr> 
   <td><strong>CSS</strong></td> 
   <td> /libs/social/tally/components/hbs/voting/clientlibs/votingcomponent.css</td> 
  </tr> 
  <tr> 
   <td><strong>properties</strong></td> 
   <td><p>Voir <a href="voting.md">Utilisation du vote</a></p> </td> 
  </tr> 
 </tbody> 
</table>

* [Personnalisations côté client](client-customize.md)

## Principes élémentaires pour le côté serveur {#essentials-for-server-side}

* [API Tally](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/tally/client/api/package-summary.html)

* [Points de terminaison Tally](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/tally/client/endpoints/package-summary.html)

* [Personnalisations côté serveur](server-customize.md)

### Accès au vote publié (UGC) {#accessing-posted-voting-ugc}

Le contenu généré par l’utilisateur doit être modéré à l’aide de l’une des méthodes standard de modération.\
Voir [Modération de contenu généré par l’utilisateur](moderate-ugc.md).

À partir de AEM 6.1 Communities, utilisez un [magasin commun](working-with-srp.md) pour le contenu généré par l’utilisateur inclut l’accès programmatique au contenu généré par l’utilisateur, quelle que soit l’option de stockage choisie (comme ASRP, MSRP ou JSRP).

**L’emplacement et le format du contenu créé par l’utilisateur dans le référentiel peuvent être modifiés sans avertissement.**.

Voir :

* [Présentation du fournisseur de ressources de stockage](srp.md) - présentation et utilisation du référentiel
* [Principes de base de la SRP et du contenu généré par l’utilisateur](srp-and-ugc.md) - Méthodes d’utilitaire SRP et exemples
* [Accès au contenu généré par l’utilisateur avec SRP](accessing-ugc-with-srp.md) - Instructions de codage
* [Refactorisation de SocialUtils](socialutils.md) - mappage de méthodes d’utilitaire obsolètes aux méthodes d’utilitaire SRP actuelles
