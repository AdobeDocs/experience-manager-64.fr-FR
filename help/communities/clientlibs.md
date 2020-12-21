---
title: Clientlibs pour les composants Communities
seo-title: Clientlibs pour les composants Communities
description: Bibliothèques côté client pour les communautés
seo-description: Bibliothèques côté client pour les communautés
uuid: 0a62f629-e6af-4269-862e-0595824c329f
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 7d423dff-8710-4f43-ad55-8863169946e2
translation-type: tm+mt
source-git-commit: 59d40b5bddc42a4ac057ef600243f396aefc926b
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 2%

---


# Clientlibs pour les composants de communautés {#clientlibs-for-communities-components}

## Présentation {#introduction}

Cette section de la documentation décrit comment ajouter des bibliothèques côté client (clientlibs) à une page pour les composants Communities.

Pour obtenir des informations de base, consultez :

* [Utilisation de ](../../help/sites-developing/clientlibs.md) bibliothèques côté client qui fournit des détails d’utilisation ainsi que des outils de débogage
* [Clientlibs for ](client-customize.md#clientlibs) SCFqui fournit des informations utiles lors de la personnalisation des composants SCF
* [Blog : aem bibliothèques clientes expliquées par l’exemple](https://blogs.adobe.com/experiencedelivers/experience-management/clientlibs-explained-example/)

## Raisons pour lesquelles les bibliothèques clientes sont requises {#why-clientlibs-are-required}

Les bibliothèques clientes sont requises pour le bon fonctionnement (JavaScript) et le style (CSS) d’un composant.

Lorsqu&#39;il existe une [fonction communautaire](functions.md) pour une fonction, tous les composants et configurations nécessaires, y compris les clientlibs requis, seront présents sur le site communautaire. Ce n&#39;est que si d&#39;autres composants doivent être disponibles pour les auteurs que des clientlibs supplémentaires doivent être ajoutés.

Lorsque les clientlibs requis sont manquants, [l&#39;ajout d&#39;un composant Communities à une page](author-communities.md) peut entraîner des erreurs javascript ainsi qu&#39;un aspect inattendu.

### Exemple : Révisions placées sans bibliothèques clientes {#example-placed-reviews-without-clientlibs}

![chlimage_1-244](assets/chlimage_1-244.png)

### Exemple : Révisions placées avec des bibliothèques clientes {#example-placed-reviews-with-clientlibs}

![chlimage_1-245](assets/chlimage_1-245.png)

## Identification des bibliothèques clientes requises {#identifying-required-clientlibs}

Les informations essentielles pour les développeurs identifient les clients requis.

De plus, à partir d&#39;une instance AEM, l&#39;accès au [Guide des composants de la communauté](components-guide.md) permet d&#39;accéder à une liste des catégories clientlib requises pour un composant.

Par exemple, en haut de la page [Révisions](http://localhost:4502/content/community-components/en/reviews.html), les clientlibs requis répertoriés sont

* cq.ckeditor
* cq.social.hbs.reviews

![chlimage_1-246](assets/chlimage_1-246.png)

## Ajouter les bibliothèques clientes requises {#adding-required-clientlibs}

Si vous souhaitez ajouter un composant Communautés à une page, vous devez ajouter les clientlibs requis pour le composant si celui-ci n’est pas déjà présent.

Utilisez [CRXDE|Lite](#using-crxde-lite) pour modifier une liste de clients existante pour une page de site communautaire.

Pour ajouter une bibliothèque cliente pour un site communautaire à l&#39;aide de [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md) :

* Accédez à [https://&lt;serveur>:&lt;port>/crx/de](http://localhost:4502/crx/de).
* Localisez le noeud `clientlibslist` pour la page sur laquelle vous souhaitez ajouter le composant.

   * `/content/sites/sample/en/page/jcr:content/clientlibslist`

* Avec le noeud `clientlibslist` sélectionné

   * Localisez la propriété String[] `scg:requiredClientLibs`.
   * Sélectionnez `Value` pour accéder à la boîte de dialogue de tableau de chaînes.

      * Faire défiler vers le bas si nécessaire
      * Sélectionnez `+` pour entrer une nouvelle bibliothèque cliente.

         * Répéter pour ajouter d’autres bibliothèques clientes
      * **[!UICONTROL Cliquez sur OK]**
   * Sélectionner **[!UICONTROL Enregistrer tout]**



>[!NOTE]
>
>Si le site n&#39;est pas un site communautaire, il faudrait découvrir l&#39;existence ou l&#39;emplacement des bibliothèques clientes utilisées pour le site.

À l&#39;aide de l&#39;exemple [Prise en main d&#39;AEM Communities](getting-started.md), où `site-name` est *engager*, voici comment la liste cliente s&#39;affichera si vous ajoutez le composant de révision :

![chlimage_1-247](assets/chlimage_1-247.png)

