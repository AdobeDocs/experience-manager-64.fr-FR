---
title: Clientlibs des composants Communities
seo-title: Clientlibs for Communities Components
description: Bibliothèques côté client pour les communautés
seo-description: Client-side libraries for Communities
uuid: 0a62f629-e6af-4269-862e-0595824c329f
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 7d423dff-8710-4f43-ad55-8863169946e2
exl-id: 9b4ed16f-3c7c-478a-a897-9b4be086988b
source-git-commit: 9178c3a01e7f450d3794f41605fb3788231c88c0
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 3%

---

# Clientlibs des composants Communities {#clientlibs-for-communities-components}

## Présentation {#introduction}

Cette section de la documentation décrit comment ajouter des bibliothèques côté client (clientlibs) à une page pour les composants Communities.

Pour obtenir des informations de base, consultez :

* [Utilisation de bibliothèques côté client](../../help/sites-developing/clientlibs.md) qui fournit des détails d’utilisation ainsi que des outils de débogage
* [Clientlibs pour SCF](client-customize.md#clientlibs) qui fournit des informations utiles lors de la personnalisation des composants SCF

## Pourquoi les bibliothèques côté client sont nécessaires {#why-clientlibs-are-required}

Les bibliothèques côté client sont nécessaires au bon fonctionnement (JavaScript) et au style (CSS) d’un composant.

Lorsqu’il existe une [fonction communautaire](functions.md) pour une fonctionnalité, tous les composants et configurations nécessaires, y compris les bibliothèques clientes requises, seront présents sur le site de la communauté. Il est nécessaire d’ajouter des clientlibs supplémentaires uniquement si des composants supplémentaires doivent être disponibles pour les auteurs.

Lorsque les clientlibs requises sont manquantes, [ajout d’un composant Communautés à une page](author-communities.md) peut entraîner des erreurs JavaScript et un aspect inattendu.

### Exemple : Révisions placées sans clientlibs {#example-placed-reviews-without-clientlibs}

![chlimage_1-244](assets/chlimage_1-244.png)

### Exemple : Révisions placées avec Clientlibs {#example-placed-reviews-with-clientlibs}

![chlimage_1-245](assets/chlimage_1-245.png)

## Identification des bibliothèques clientes requises {#identifying-required-clientlibs}

Les informations de fonction essentielles pour les développeurs identifient les clientlibs requises.

En outre, à partir d’une instance AEM, accédez au [Guide des composants de communauté](components-guide.md) permet d’accéder à la liste des catégories clientlib requises pour un composant.

Par exemple, tout en haut de la page [Page des révisions](http://localhost:4502/content/community-components/en/reviews.html) les clientlibs requises répertoriées sont

* cq.ckeditor
* cq.social.hbs.reviews

![chlimage_1-246](assets/chlimage_1-246.png)

## Ajout de bibliothèques clientes requises {#adding-required-clientlibs}

Si vous souhaitez ajouter un composant Communities à une page, vous devez ajouter les bibliothèques clientes requises pour le composant s’il n’est pas déjà présent.

Utilisation [CRXDE|Lite](#using-crxde-lite) pour modifier une liste de bibliothèques clientes existante pour une page de site communautaire.

Pour ajouter une bibliothèque cliente à un site de la communauté à l’aide d’ [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md):

* Accédez à [https://&lt;server>:&lt;port>/crx/de](http://localhost:4502/crx/de)
* Recherchez la variable `clientlibslist` noeud de la page sur laquelle vous souhaitez ajouter le composant.

   * `/content/sites/sample/en/page/jcr:content/clientlibslist`

* Avec `clientlibslist` noeud sélectionné

   * Localisation de la chaîne[] property `scg:requiredClientLibs`
   * Sélectionnez `Value` pour accéder à la boîte de dialogue Tableau de chaînes

      * Faites défiler la page vers le bas si nécessaire
      * Sélectionner `+` pour entrer une nouvelle bibliothèque cliente

         * Répétez l’opération pour ajouter d’autres bibliothèques clientes.
      * Sélectionnez **[!UICONTROL OK]**
   * Sélectionnez **[!UICONTROL Enregistrer tout]**



>[!NOTE]
>
>Si le site n’est pas un site communautaire, l’existence ou l’emplacement des bibliothèques clientes utilisées pour le site doivent être découverts.

En utilisant la variable [Prise en main d’AEM Communities](getting-started.md) exemple, où `site-name` is *engager*, voici comment clientliblist s’affiche lors de l’ajout du composant de révisions :

![chlimage_1-247](assets/chlimage_1-247.png)
