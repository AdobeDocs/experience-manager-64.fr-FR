---
title: Blog Essentials
seo-title: Blog Essentials
description: Présentation du blog
seo-description: Présentation du blog
uuid: ce0885de-6276-47a2-8f6c-358f0beb2b89
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: de8d0e6d-827b-45fe-a538-d3fe1dec8427
translation-type: tm+mt
source-git-commit: 4d64494dff34108d32e060a96209df697b2ce11f

---


# Blog Essentials {#blog-essentials}

Depuis AEM 6.1 Communities, un blog est une activité communautaire. Les articles de blog sont maintenant publiés à partir de l&#39;environnement de publication, où auparavant, les articles de blog ne pouvaient être créés que dans l&#39;environnement d&#39;auteur et publiés.

Les articles de blog peuvent désormais être créés par n&#39;importe quel membre de la communauté, sauf s&#39;ils sont réservés aux membres privilégiés.

Cette page fournit les informations essentielles pour travailler avec la fonction de blog.

>[!NOTE]
>
>L&#39;infrastructure sous-jacente de la fonction de blog est la fonction de journal.

## Essentials for Client-Side {#essentials-for-client-side}

La fonction de blog est composée de deux composants principaux disponibles en ajoutant la fonction [de](functions.md#blog-function) blog ou en ajoutant les composants à une page en mode d&#39;édition de l&#39;auteur.

### Blog {#blog}

<table> 
 <tbody>
  <tr>
   <td> <strong>resourceType</strong></td> 
   <td>social/journal/composants/hbs/journal</td> 
  </tr>
  <tr>
   <td> <a href="scf.md#add-or-include-a-communities-component"><strong>inclus</strong></a></td> 
   <td>Non</td> 
  </tr>
  <tr>
   <td> <a href="clientlibs.md"><strong>clientllibs</strong></a></td> 
   <td>cq.ckeditor<br /> cq.social.hbs.vote<br /> cq.social.hbs.journal</td> 
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
   <td>voir Fonctionnalité <a href="blog-feature.md">du blog</a></td> 
  </tr>
 </tbody>
</table>

### Barre latérale de blog {#blog-sidebar}

| **resourceType** | social/journal/composants/hbs/barre latérale |
|---|---|
| [**inclus **](scf.md#add-or-include-a-communities-component) | Non |
| [**clientllibs **](clientlibs.md) | cq.social.hbs.journal_sidebar |
| **templates** | /libs/social/journal/components/hbs/sidebar/sidebar.hbs |
| **css** | /libs/social/journal/components/hbs/sidebar/clientlibs/sidebar.css |
| **propriétés** | voir Fonctionnalité [du blog](blog-feature.md) |

* [Personnalisations côté client](client-customize.md)

## Essentials for Server-Side {#essentials-for-server-side}

* [API de blog](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/journal/client/api/package-summary.html)

* [Points de fin du blog](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/cq/social/journal/client/endpoints/package-summary.html)

* [Personnalisations côté serveur](server-customize.md)

### Fonction Blog {#blog-function}

Une structure de site communautaire qui inclut la fonction [](functions.md#blog-function) Bog aura configuré `Blog` et `Blog Sidebar` les composants. La fonction Blog prend en charge l&#39;identification d&#39;un groupe [d&#39;utilisateurs membres](users.md#privileged-members-group)privilégiés.

### Accès aux entrées de blog (UGC) {#accessing-blog-entries-ugc}

L’UGC doit être modérée à l’aide de l’une des méthodes standard de modération.\
Voir [Modération du contenu](moderate-ugc.md)généré par l’utilisateur.

Depuis les communautés AEM 6.1, l’utilisation d’un magasin [](working-with-srp.md) commun pour l’UGC inclut l’accès par programmation à l’UGC, quelle que soit l’option de stockage choisie (par exemple, ASRP, MSRP ou JSRP).

**L’emplacement et le format de l’UGC dans le référentiel peuvent être modifiés sans avertissement**.

Voir :

* [Présentation](srp.md) du fournisseur de ressources de stockage - présentation et présentation de l&#39;utilisation du référentiel
* [SRP et UGC Essentials](srp-and-ugc.md) - Méthodes et exemples d&#39;utilitaires SRP
* [Accès UGC avec SRP](accessing-ugc-with-srp.md) - directives de codage
* [SocialUtils Refactoring](socialutils.md) - mappage des méthodes d’utilitaire obsolètes aux méthodes d’utilitaire SRP actuelles

## Éditeur principal {#primary-publisher}

Lorsque le déploiement est une batterie de publication, il est nécessaire d’identifier un éditeur principal qui interrogera les articles dont la publication est planifiée.

Voir Editeur [](deploy-communities.md#primary-publisher) principal pour plus d’informations.

## Autoriser les médias enrichis {#allowing-rich-media}

La plate-forme AEM bloque les liens d’autres sites Web pour empêcher les attaques XSS, comme décrit dans la section

* [Protection contre les scripts de site à site (XSS)](../../help/sites-developing/security.md#protect-against-cross-site-scripting-xss)

Depuis AEM 6.2, les modifications qui devaient être apportées manuellement sont incluses dans le fichier de configuration par défaut d’AntiSamy.

Le contenu multimédia enrichi est incorporé dans un article de blog en sélectionnant l’ `Embed Media from External Sites` icône :  ![chlimage_1-471](assets/chlimage_1-471.png)

