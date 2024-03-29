---
title: Personnalisation côté serveur
seo-title: Server-side Customization
description: Personnalisation côté serveur dans AEM Communities
seo-description: Customizing server-side in AEM Communities
uuid: 5e9bc6bf-69dc-414c-a4bd-74a104d7bd8f
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: df5416ec-5c63-481b-99ed-9e5a91df2432
exl-id: fbe2a617-e926-4842-a3bc-8d193bd367dc
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '927'
ht-degree: 1%

---

# Personnalisation côté serveur {#server-side-customization}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

| **[⇐ Notions fondamentales sur les fonctionnalités](essentials.md)** | **[⇒ de personnalisation côté client](client-customize.md)** |
|---|---|
|  | **[Aide-mémoire SCF ⇒](handlebars-helpers.md)** |

## API Java {#java-apis}

>[!NOTE]
>
>L’emplacement du package des API Communities peut être modifié lors de la mise à niveau d’une version majeure vers une version suivante.

### Interface du composant Social {#socialcomponent-interface}

Les composants sociaux sont des POJO qui représentent une ressource pour une fonction AEM Communities. Idéalement, chaque composant Social représente un type de ressource spécifique avec des GETters exposés qui fournissent des données au client afin que la ressource soit correctement représentée. Toute la logique commerciale et la logique d’affichage sont encapsulées dans le composant Social, y compris les informations de session du visiteur du site, si nécessaire.

L’interface définit un ensemble de base de GETters nécessaires pour représenter une ressource. L&#39;interface stipule : Map&lt;string object=&quot;&quot;> Méthodes getAsMap() et String toJSONString() nécessaires pour effectuer le rendu des modèles Handlebars et exposer les points de terminaison JSON GET pour les ressources.

Toutes les classes SocialComponent doivent mettre en oeuvre l’interface `com.adobe.cq.social.scf.SocialComponent`

### Interface du composant SocialCollection {#socialcollectioncomponent-interface}

L’interface SocialCollectionComponent étend l’interface SocialComponent pour mieux représenter les ressources qui sont des collections d’autres ressources.

Toutes les classes SocialCollectionComponent doivent implémenter l’interface com.adobe.cq.social.scf.SocialCollectionComponent

### Interface SocialComponentFactory {#socialcomponentfactory-interface}

Une SocialComponentFactory (factory) enregistre un composant Social avec la structure. La fabrique permet à la structure de savoir quels composants sociaux sont disponibles pour un type de ressource donné et leur rang de priorité. lorsque plusieurs composants sociaux sont identifiés.

SocialComponentFactory est responsable de la création d’une instance du composant Social sélectionné, ce qui permet d’injecter toutes les dépendances dont le composant Social a besoin à partir de la fabrique à l’aide des pratiques d’ID.

Un SocialComponentFactory est un service OSGi qui a accès à d’autres services OSGi qui peuvent être transmis à SocialComponent par l’intermédiaire d’un constructeur.

Toutes les classes SocialComponentFactory doivent mettre en oeuvre l’interface `com.adobe.cq.social.scf.SocialComponentFactory`

Une implémentation de la méthode SocialComponentFactory.getPriority() doit renvoyer la valeur la plus élevée afin que la fabrique soit utilisée pour le resourceType donné comme renvoyé par getResourceType().

### Interface de SocialComponentFactoryManager {#socialcomponentfactorymanager-interface}

SocialComponentFactoryManager (responsable) gère tous les composants sociaux enregistrés dans la structure et est responsable de la sélection de SocialComponentFactory à utiliser pour une ressource donnée (resourceType). Si aucune usine n’est enregistrée pour un type de ressource spécifique, le responsable renvoie une usine avec le super type le plus proche pour la ressource donnée.

Un SocialComponentFactoryManager est un service OSGi qui a accès à d’autres services OSGi qui peuvent être transmis à SocialComponent par l’intermédiaire d’un constructeur.

Un gestionnaire du service OSGi est obtenu en appelant `com.adobe.cq.social.scf.SocialComponentFactoryManager`

### API HTTP - Demandes de POST {#http-api-post-requests}

#### Classe PostOperation {#postoperation-class}

Les points d’entrée du POST d’API HTTP sont des classes PostOperation définies par l’implémentation de la variable `SlingPostOperation`interface (module `org.apache.sling.servlets.post`).

Le `PostOperation`ensembles d’implémentations de point de terminaison `sling.post.operation`à une valeur à laquelle l’opération répondra. Toutes les demandes de POST avec un paramètre:operation défini sur cette valeur seront déléguées à cette classe d’implémentation.

Le `PostOperation`invoque la variable `SocialOperation`qui effectue les actions nécessaires à l’opération.

Le `PostOperation`reçoit le résultat de la fonction `SocialOperation`et renvoie la réponse appropriée au client.

#### Classe SocialOperation {#socialoperation-class}

Chaque `SocialOperation`endpoint étend la classe AbstractSocialOperation et remplace la méthode `performOperation().`Cette méthode effectue toutes les actions nécessaires pour terminer l’opération et renvoyer une `SocialOperationResult`ou sinon, lancez une `OperationException`, auquel cas un état d’erreur HTTP avec un message, s’il est disponible, est renvoyé à la place de la réponse JSON normale ou du code d’état HTTP de succès.

Extension `AbstractSocialOperation`rend possible la réutilisation de `SocialComponents`pour envoyer des réponses JSON.

#### Classe SocialOperationResult {#socialoperationresult-class}

Le `SocialOperationResult`est renvoyée en raison de la variable `SocialOperation`et est composé d’un `SocialComponent`, code d’état HTTP et message d’état HTTP.

Le `SocialComponent`représente la ressource qui a été affectée par l’opération.

Pour une opération de création, la variable `SocialComponent`inclus dans la variable `SocialOperationResult`représente la ressource qui vient d&#39;être créée et, pour une opération de mise à jour, elle représente la ressource qui a été modifiée par l&#39;opération. Non `SocialComponent`est renvoyée pour une opération de suppression.

Les codes d’état HTTP de succès utilisés sont les suivants :

* 201 pour les opérations de création
* 200 pour les opérations de mise à jour
* 204 pour les opérations de suppression

#### Classe OperationException {#operationexception-class}

Un `OperationExcepton`peut être généré lors de l’exécution d’une opération si la requête n’est pas valide ou si une autre erreur se produit, telle que des erreurs internes, des valeurs de paramètre incorrectes, des autorisations incorrectes, etc. Un `OperationException`est composé d’un code d’état HTTP et d’un message d’erreur, qui sont renvoyés au client en tant que réponse à la variable `PostOperatoin`.

#### Classe OperationService {#operationservice-class}

La structure de composants sociaux recommande que la logique commerciale responsable de l’exécution de l’opération ne soit pas implémentée dans la variable `SocialOperation`, mais à la place déléguée à un service OSGi. L’utilisation d’un service OSGi pour une logique commerciale permet d’utiliser une `SocialComponent`, suite à `SocialOperation`point d’entrée, à intégrer à d’autres codes et pour lesquels une logique métier différente est appliquée.

Tous `OperationService`étendez les classes `AbstractOperationService`, permettant des extensions supplémentaires pouvant se connecter à l’opération en cours d’exécution. Chaque opération du service est représentée par une `SocialOperation`classe . Le `OperationExtensions`peut être appelée pendant l’exécution de l’opération en appelant les méthodes .

* `performBeforeActions()`
Permet les prévérifications/prétraitements et validations
* `performAfterActions()`
Permet de modifier davantage les ressources ou d’appeler des événements personnalisés, des workflows, etc.

#### Classe OperationExtension {#operationextension-class}

`OperationExtension`Les classes sont des éléments de code personnalisés qui peuvent être injectés dans une opération permettant de personnaliser les opérations pour répondre aux besoins de l’entreprise. Les utilisateurs du composant peuvent ajouter des fonctionnalités de manière dynamique et incrémentielle au composant. Le modèle d’extension/crochet permet aux développeurs de se concentrer exclusivement sur les extensions elles-mêmes et élimine la nécessité de copier et de remplacer des opérations et des composants entiers.

## Exemple de code {#sample-code}

Un exemple de code est disponible dans la [Adobe Marketing Cloud GitHub](https://github.com/Adobe-Marketing-Cloud) référentiel. Recherchez des projets dont le préfixe est `aem-communities` ou `aem-scf`.

## Bonnes pratiques {#best-practices}

Afficher la variable [Consignes de codage](code-guide.md) pour consulter les instructions relatives au codage et les bonnes pratiques à l’intention des développeurs AEM Communities.

Voir aussi [Fournisseur de ressources de stockage (SRP) pour le contenu généré par l’utilisateur](srp.md) pour en savoir plus sur l’accès au contenu généré par l’utilisateur.

| **[⇐ Notions fondamentales sur les fonctionnalités](essentials.md)** | **[⇒ de personnalisation côté client](client-customize.md)** |
|---|---|
|  | **[Aide-mémoire SCF ⇒](handlebars-helpers.md)** |
