---
title: Structure des composants sociaux
seo-title: Social Component Framework
description: La structure de composants sociaux (SCF) simplifie le processus de configuration, de personnalisation et d’extension des composants de communautés.
seo-description: The social component framework (SCF) simplifies the process of configuring, customizing, and extending Communities components
uuid: 23b4418d-b91c-46fc-bf42-1154ef79fe5a
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: d7b5b5e3-2d84-4a6b-bcc2-d490882ff3ed
exl-id: 9264c888-a583-40eb-9178-273146f8a12b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1524'
ht-degree: 2%

---

# Structure des composants sociaux {#social-component-framework}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

La structure de composants sociaux (SCF) simplifie le processus de configuration, de personnalisation et d’extension des composants Communities côté serveur et côté client.

Les avantages du cadre :

* **Fonctionnel**: Facilité d’intégration prête à l’emploi avec peu ou pas de personnalisation pour 80 % des cas d’utilisation
* **Skinable**: Utilisation cohérente des attributs de HTML pour la mise en forme CSS
* **Extensible**: La mise en oeuvre des composants est orientée objet et s’appuie sur la logique métier : il est facile d’ajouter une connexion métier incrémentielle sur le serveur.
* **Flexible**: Modèles JavaScript simples sans logique, facilement recouverts et personnalisés
* **Accessible**: L’API HTTP prend en charge la publication depuis n’importe quel client, y compris les applications mobiles.
* **Portable**: Intégrer/incorporer dans n’importe quelle page web reposant sur n’importe quelle technologie

Explorez une instance de création ou de publication à l’aide de l’option interactive [Guide des composants de communauté](components-guide.md).

## Présentation {#overview}

Dans SCF, un composant est constitué d’un POJO SocialComponent, d’un modèle JS Handlebars (pour effectuer le rendu du composant) et de CSS (pour appliquer un style au composant).

Un modèle JS Handlebars peut étendre les composants JS de modèle/vue pour gérer l’interaction de l’utilisateur avec le composant sur le client.

Si un composant doit prendre en charge la modification des données, l’implémentation de l’API SocialComponent peut être écrite pour prendre en charge la modification/enregistrement de données similaires aux objets de modèle/données dans les applications web traditionnelles. En outre, les opérations (contrôleurs) et un service d’opération peuvent être ajoutés pour gérer les demandes d’opération, exécuter une logique métier et appeler les API sur les objets de modèle/données.

L’API SocialComponent peut être étendue afin de fournir les données requises par un client pour une couche d’affichage ou un client HTTP.

### Rendu des pages pour le client {#how-pages-are-rendered-for-client}

![chlimage_1-25](assets/chlimage_1-25.png)

### Personnalisation et extension des composants {#component-customization-and-extension}

Pour personnaliser ou étendre les composants, vous écrivez uniquement les incrustations et les extensions dans votre répertoire /apps, ce qui simplifie le processus de mise à niveau vers les prochaines versions.

* Pour la mise en page
   * Seule la variable [Modification requise pour CSS](client-customize.md#skinning-css)
* Pour la recherche et le ressenti
   * Modification du modèle JS et du CSS
* Pour Look, Feed et UX
   * Modifier le modèle JS, CSS et [extension/remplacement de JavaScript](client-customize.md#extending-javascript)
* Modification des informations disponibles pour le modèle JS ou le point de terminaison du GET
   * Étendre le [SocialComponent](server-customize.md#socialcomponent-interface)
* Pour ajouter un traitement personnalisé pendant les opérations
   * Écrire une [OperationExtension](server-customize.md#operationextension-class)
* Pour ajouter une nouvelle opération personnalisée
   * Créer [Opération de publication Sling](server-customize.md#postoperation-class)
   * Utiliser existant [OperationServices](server-customize.md#operationservice-class) si nécessaire
   * Ajoutez du code JavaScript pour appeler votre opération du côté client selon les besoins.

## Structure côté serveur {#server-side-framework}

La structure fournit des API pour accéder aux fonctionnalités du serveur et prendre en charge l’interaction entre le client et le serveur.

### API Java {#java-apis}

Les API Java fournissent des classes et des interfaces abstraites qui sont facilement héritées ou sous-classées.

Les principales classes sont décrites dans la section [Personnalisation côté serveur](server-customize.md) page.

Visite [Présentation du fournisseur de ressources de stockage](srp.md) pour en savoir plus sur l’utilisation du contenu créé par l’utilisateur.

### API HTTP  {#http-api}

L’API HTTP prend en charge la facilité de personnalisation et de choix des plateformes clientes pour les applications PhoneGap, les applications natives, ainsi que d’autres intégrations et applications monopages. De plus, l’API HTTP permet à un site communautaire de s’exécuter en tant que service sans client, de sorte que les composants de structure puissent être intégrés à n’importe quelle page web créée sur n’importe quelle technologie.

### API HTTP - Demandes de GET {#http-api-get-requests}

Pour chaque composant Social, la structure fournit un point de terminaison d’API HTTP. Le point de terminaison est accessible en envoyant une requête de GET à la ressource avec un sélecteur + extension &#39;.social.json&#39;. Avec Sling, la requête est transmise à la fonction `DefaultSocialGetServlet`.

La `DefaultSocialGetServlet`

1. Transmet la ressource (resourceType) à la variable `SocialComponentFactoryManager`et reçoit une SocialComponentFactory capable de sélectionner une `SocialComponent`représentant la ressource.

1. Appelle la fabrique et reçoit un `SocialComponent`capable de gérer la ressource et la requête.
1. Appelle le `SocialComponent`, qui traite la requête et renvoie une représentation JSON des résultats.
1. Renvoie la réponse JSON au client.

**`GET Request`**

Un servlet de GET par défaut écoute les demandes .social.json auxquelles le SocialComponent répond avec un JSON personnalisable.

![chlimage_1-26](assets/chlimage_1-26.png)

### API HTTP - Demandes de POST {#http-api-post-requests}

En plus des opérations de GET (lecture), la structure définit un modèle de point de terminaison pour activer d’autres opérations sur un composant, notamment Créer, Mettre à jour et Supprimer. Ces points de terminaison sont des API HTTP qui acceptent les entrées et répondent avec des codes d’état HTTP ou avec un objet de réponse JSON.

Ce modèle de point de terminaison de structure rend les opérations CUD extensibles, réutilisables et testables.

**`POST Request`**

Il existe une opération Sling POST:operation pour chaque opération SocialComponent . La logique commerciale et le code de maintenance pour chaque opération sont encapsulés dans un OperationService accessible via l’API HTTP ou ailleurs en tant que service OSGi. Les hooks prennent en charge les extensions d’opération enfichables pour les actions avant/après.

![chlimage_1-27](assets/chlimage_1-27.png)

### Fournisseur de ressources de stockage (SRP) {#storage-resource-provider-srp}

Pour en savoir plus sur la gestion du contenu généré par l’utilisateur stocké dans la variable [magasin de contenu communautaire](working-with-srp.md), voir

* [Présentation du fournisseur de ressources de stockage](srp.md) - Présentation et utilisation du référentiel
* [Principes de base de la SRP et du contenu généré par l’utilisateur](srp-and-ugc.md) - Méthodes et exemples de l’utilitaire SRP
* [Accès au contenu généré par l’utilisateur avec SRP](accessing-ugc-with-srp.md) - Consignes de codage

### Personnalisations côté serveur {#server-side-customizations}

Visite [Personnalisations côté serveur](server-customize.md) pour plus d’informations sur la personnalisation de la logique commerciale et du comportement d’un composant Communities côté serveur.

## Langage de modèle JS Handlebars {#handlebars-js-templating-language}

L’utilisation de la fonction [Handlebars JS](https://handlebarsjs.com/) langage de modèle (HBS), une technologie Open Source populaire pour le rendu client-serveur.

Les scripts HBS sont simples, sans logique, compilés à la fois sur le serveur et le client, faciles à superposer et à personnaliser, et sont naturellement liés à l’UX du client, car HBS prend en charge le rendu côté client.

La structure fournit plusieurs [Handlebars Helpers](handlebars-helpers.md) qui sont utiles lors du développement de composants sociaux.

Sur le serveur, lorsque Sling résout une demande de GET, il identifie le script qui sera utilisé pour répondre à la demande. Si le script est un modèle HBS (.hbs), Sling déléguera la requête au moteur Handlebars. Le moteur Handlebars récupère ensuite le composant Social à partir de la SocialComponentFactory appropriée, crée un contexte et effectue le rendu du HTML.

### Aucune restriction d’accès {#no-access-restriction}

Les fichiers de modèle Handlebars (HBS) (.hbs) sont similaires aux fichiers de modèle .jsp et .html , sauf qu’ils peuvent être utilisés pour le rendu à la fois dans le navigateur client et sur le serveur. Par conséquent, un navigateur client demandant un modèle côté client recevra un fichier .hbs du serveur.

Pour ce faire, tous les modèles HBS dans le chemin de recherche Sling (tous les fichiers .hbs sous /libs/ ou /apps) peuvent être récupérés par n’importe quel utilisateur à partir de l’auteur ou de la publication.

L’accès HTTP aux fichiers .hbs peut ne pas être interdit.

### Ajout ou inclusion d’un composant Communautés {#add-or-include-a-communities-component}

La plupart des composants Communities doivent être *ajouté* en tant que ressource adressable Sling. Quelques-uns des composants de communauté peuvent être *included* dans un modèle en tant que ressource non existante pour permettre l’inclusion et la personnalisation dynamiques de l’emplacement où écrire le contenu généré par l’utilisateur.

Dans les deux cas, la variable [bibliothèques clientes requises](clientlibs.md) doit également être présent.

**Ajout d’un composant**

L’ajout d’un composant fait référence au processus d’ajout d’une instance d’une ressource (composant), par exemple lorsque vous faites glisser du navigateur de composants (sidekick) vers une page en mode d’édition de création.

Le résultat est un noeud enfant JCR sous un noeud par, qui est adressable à Sling.

**Inclure un composant**

L’inclusion d’un composant fait référence au processus d’ajout d’une référence à une [ressource &quot;non existante&quot;](srp.md#for-non-existing-resources-ners) (pas de noeud JCR) dans le modèle, par exemple en utilisant un langage de script.

À compter de la version 6.1 d’AEM, lorsqu’un composant est inclus dynamiquement au lieu d’être ajouté, il est possible de modifier les propriétés du composant en mode création *conception*.

Seuls quelques-uns des composants AEM Communities peuvent être inclus dynamiquement. Ils sont :

* [Commentaires](essentials-comments.md)
* [Évaluation](rating-basics.md)
* [Révisions](reviews-basics.md)
* [Votant](essentials-voting.md)

Le [Guide des composants de communauté](components-guide.md) permet d’empêcher l’ajout à des composants inclusibles.

**Lors de l’utilisation de Guidons** langue de modèle, la ressource non existante est incluse à l’aide du [assistant d’inclusion](handlebars-helpers.md#include) en spécifiant son resourceType :

`{{include this.id path="comments" resourceType="social/commons/components/hbs/comments"}}`

**Lors de l’utilisation de JSP**, une ressource est incluse à l’aide de la balise . [cq:include](../../help/sites-developing/taglib.md#lt-cq-include):

```
<cq:include path="votes" 
 resourceType="social/tally/components/voting" />
```

>[!NOTE]
>
>Pour ajouter dynamiquement un composant à une page, au lieu de l’ajouter ou de l’inclure dans un modèle, reportez-vous à la section [Chargement partiel des composants](sideloading.md).

### Handlebars Helpers {#handlebars-helpers}

Voir [Assistant de Handlebars SCF](handlebars-helpers.md) pour obtenir une liste et une description des assistants personnalisés disponibles dans SCF.

## Structure côté client {#client-side-framework}

### Structure JavaScript de l’affichage du modèle {#model-view-javascript-framework}

La structure comprend une extension de [Backbone.js](https://www.backbonejs.org/), une structure JavaScript d’affichage de modèle, pour faciliter le développement de composants interactifs riches. La nature orientée objet prend en charge une structure extensible/réutilisable. La communication entre le client et le serveur est simplifiée au moyen de l’API HTTP.

La structure utilise les modèles Handlebars côté serveur pour effectuer le rendu des composants pour le client. Les modèles sont basés sur les réponses JSON générées par l’API HTTP. Les vues se lient au HTML généré par les modèles Handlebars et offrent une interactivité.

### Conventions CSS {#css-conventions}

Les conventions suivantes sont recommandées pour définir et utiliser des classes CSS :

* Utilisez des noms de classe CSS clairement espacés dans l’espace de noms et évitez les noms génériques tels que &#39;titre&#39;, &#39;image&#39;, etc.
* Définissez des styles de sélecteur de classe spécifiques afin que les feuilles de style CSS fonctionnent correctement avec d’autres éléments et styles de la page. Par exemple : `.social-forum .topic-list .li { color: blue; }`
* Conserver les classes CSS pour le style distinctes des classes CSS pour les UX pilotés par JavaScript

### Personnalisations côté client {#client-side-customizations}

Pour personnaliser l’aspect et le comportement d’un composant Communities côté client, reportez-vous à la section [Personnalisations côté client](client-customize.md), qui comprend des informations sur :

* [Recouvrements](client-customize.md#overlays)
* [Extensions](client-customize.md#extensions)
* [Balisage de HTML](client-customize.md#htmlmarkup)
* [Esquisse de CSS](client-customize.md#skinning-css)
* [Extension de JavaScript](client-customize.md#extending-javascript)
* [Clientlibs pour SCF](client-customize.md#clientlibs-for-scf)

## Fonctionnalités et composants essentiels {#feature-and-component-essentials}

Les informations essentielles pour les développeurs sont décrites dans la section [Fonctionnalités et composants essentiels](essentials.md) .

Vous trouverez des informations supplémentaires sur les développeurs dans la section [Consignes de codage](code-guide.md) .

## Résolution des problèmes {#troubleshooting}

Les préoccupations courantes et les problèmes connus sont décrits dans la section [Dépannage](troubleshooting.md) .
