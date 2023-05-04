---
title: Notions fondamentales sur les blogs
seo-title: Blog Essentials
description: Présentation des blogs
seo-description: Blog overview
uuid: ce0885de-6276-47a2-8f6c-358f0beb2b89
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: de8d0e6d-827b-45fe-a538-d3fe1dec8427
exl-id: 8cff0b7b-c120-462f-8fce-13822073eabb
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 3%

---

# Notions fondamentales sur les blogs {#blog-essentials}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Depuis AEM 6.1 Communities, un blog est une activité communautaire. Les articles de blog sont maintenant publiés à partir de l’environnement de publication, où auparavant les articles de blog ne pouvaient être créés que dans l’environnement de création et publiés .

Les articles de blog peuvent maintenant être créés par n&#39;importe quel membre de la communauté, sauf si cela est limité aux membres privilégiés.

Cette page fournit les informations essentielles pour utiliser la fonction de blog.

>[!NOTE]
>
>L&#39;infrastructure sous-jacente de la fonction de blog est la fonction de journal.

## Principes élémentaires pour le côté client {#essentials-for-client-side}

La fonction de blog est composée de deux composants principaux disponibles en ajoutant la fonction [Fonction de blog](functions.md#blog-function) ou en ajoutant les composants à une page en mode d’édition de création.

### Blog {#blog}

<table> 
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td> 
   <td>social/journal/components/hbs/journal</td> 
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>incluable</strong></a></td> 
   <td>Non</td> 
  </tr>
  <tr>
   <td> <a href="clientlibs.md"><strong>clientllibs</strong></a></td> 
   <td>cq.ckeditor<br /> cq.social.hbs.votes<br /> cq.social.hbs.journal</td> 
  </tr>
  <tr>
   <td> <strong>templates</strong></td> 
   <td> /libs/social/journal/components/hbs/journal/journal.hbs<br /> /libs/social/journal/components/hbs/entry_topic/list-item.hbs</td> 
  </tr>
  <tr>
   <td> <strong>css</strong></td> 
   <td> /libs/social/journal/components/hbs/journal/clientlibs/journal.css</td> 
  </tr>
  <tr>
   <td><strong> properties</strong></td> 
   <td>see <a href="blog-feature.md">Fonctionnalité de blog</a></td> 
  </tr>
 </tbody>
</table>

### Barre latérale de blog {#blog-sidebar}

| **resourceType** | social/journal/components/hbs/sidebar |
|---|---|
| [**incluable**](scf.md#add-or-include-a-communities-component) | Non |
| [**clientllibs**](clientlibs.md) | cq.social.hbs.journal_sidebar |
| **templates** | /libs/social/journal/components/hbs/sidebar/sidebar.hbs |
| **css** | /libs/social/journal/components/hbs/sidebar/clientlibs/sidebar.css |
| **propriétés** | see [Fonctionnalité de blog](blog-feature.md) |

* [Personnalisations côté client](client-customize.md)

## Principes élémentaires pour le côté serveur {#essentials-for-server-side}

* [API de blog](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/journal/client/api/package-summary.html)

* [Points de fin de blog](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/journal/client/endpoints/package-summary.html)

* [Personnalisations côté serveur](server-customize.md)

### Fonction Blog {#blog-function}

Une structure de site de communauté qui inclut [Fonction de blog](functions.md#blog-function) sera configuré `Blog` et `Blog Sidebar` composants. La fonction Blog prend en charge l’identification d’une [groupe d’utilisateurs de membres privilégiés](users.md#privileged-members-group).

### Accès aux entrées de blog (UGC) {#accessing-blog-entries-ugc}

Le contenu généré par l’utilisateur doit être modéré à l’aide de l’une des méthodes standard de modération.\
Voir [Modération de contenu généré par l’utilisateur](moderate-ugc.md).

À partir de AEM 6.1 Communities, utilisez un [magasin commun](working-with-srp.md) pour le contenu généré par l’utilisateur inclut l’accès programmatique au contenu généré par l’utilisateur, quelle que soit l’option de stockage choisie (comme ASRP, MSRP ou JSRP).

**L’emplacement et le format du contenu créé par l’utilisateur dans le référentiel peuvent être modifiés sans avertissement.**.

Voir :

* [Présentation du fournisseur de ressources de stockage](srp.md) - présentation et utilisation du référentiel
* [Principes de base de la SRP et du contenu généré par l’utilisateur](srp-and-ugc.md) - Méthodes d’utilitaire SRP et exemples
* [Accès au contenu généré par l’utilisateur avec SRP](accessing-ugc-with-srp.md) - Instructions de codage
* [Refactorisation de SocialUtils](socialutils.md) - mappage de méthodes d’utilitaire obsolètes aux méthodes d’utilitaire SRP actuelles

## Éditeur Principal {#primary-publisher}

Lorsque le déploiement est une ferme de publication, il est nécessaire d’identifier un éditeur Principal qui interroge les articles planifiés pour publication.

Voir [Éditeur Principal](deploy-communities.md#primary-publisher) pour plus d’informations.

## Autoriser les médias riches {#allowing-rich-media}

La plateforme AEM bloque les liens d’autres sites Web afin d’éviter les attaques XSS, comme décrit dans la section

* [Protect contre les scripts intersites (XSS)](../../help/sites-developing/security.md#protect-against-cross-site-scripting-xss)

À compter de la version AEM 6.2, les modifications qui devaient auparavant être effectuées manuellement sont incluses dans le fichier de configuration AntiSamy par défaut.

Les médias riches sont incorporés dans un article de blog en sélectionnant l’option `Embed Media from External Sites` icon :  ![chlimage_1-471](assets/chlimage_1-471.png)
