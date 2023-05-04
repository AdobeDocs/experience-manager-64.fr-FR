---
title: Personnaliser les pages affichées par le gestionnaire d’erreurs
seo-title: Customizing Pages shown by the Error Handler
description: AEM est fourni avec un gestionnaire d’erreurs standard pour gérer les erreurs HTTP.
seo-description: AEM comes with a standard error handler for handling HTTP errors
uuid: aaf940fd-e428-4c7c-af7f-88b1d02c17c6
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: platform
content-type: reference
discoiquuid: 63c94c82-ed96-4d10-b645-227fa3c09f4b
exl-id: f71b16a9-a233-4129-bbf2-257ded88be25
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '554'
ht-degree: 72%

---

# Personnaliser les pages affichées par le gestionnaire d’erreurs{#customizing-pages-shown-by-the-error-handler}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

AEM s’accompagne d’un outil standard destiné à la gestion des erreurs HTTP, en affichant, par exemple :

![chlimage_1-67](assets/chlimage_1-67.png)

Les scripts fournis par le système existent (sous `/libs/sling/servlet/errorhandler`) pour répondre aux codes d’erreur. Par défaut, les fichiers suivants sont disponibles avec une instance CQ standard :

* 403.jsp
* 404.jsp

>[!NOTE]
>
>AEM est basé sur Apache Sling. Vous êtes donc invité à vous rendre sur la page [https://sling.apache.org/site/errorhandling.html](https://sling.apache.org/site/errorhandling.html) pour plus d’informations sur le traitement des erreurs Sling.

>[!NOTE]
>
>Sur une instance de création, le [filtre de débogage de la gestion du contenu web CQ](/help/sites-deploying/osgi-configuration-settings.md) est activé par défaut. Le code de réponse est toujours 200. Le gestionnaire d’erreur par défaut répond en écrivant la trace de pile complète à la réponse.
>
>Sur une instance de publication, le filtre de débogage de la gestion du contenu web CQ est *toujours* désactivé (même s’il est configuré comme étant activé).

## Comment personnaliser les pages affichées par le gestionnaire d’erreurs {#how-to-customize-pages-shown-by-the-error-handler}

Vous pouvez développer vos propres scripts afin de personnaliser les pages affichées par le gestionnaire d’erreurs lors de la détection d’une erreur. Vos pages personnalisées sont créées sous `/apps` et se superposent aux pages par défaut (qui se trouvent sous `/libs`).

>[!NOTE]
>
>Voir [Utilisation des recouvrements](/help/sites-developing/overlays.md) pour plus d’informations.

1. Dans le référentiel, copiez le ou les scripts par défaut :

   * de `/libs/sling/servlet/errorhandler/`
   * vers `/apps/sling/servlet/errorhandler/`

   Puisque le chemin de destination n’existe pas par défaut, vous devez le créer lorsque vous effectuez cette opération pour la première fois.

1. Accédez à `/apps/sling/servlet/errorhandler`. Ici, vous pouvez effectuer l’une des opérations suivantes :

   * Modifier le script existant approprié pour fournir les informations requises
   * Créer un script, et le modifier, pour le code requis

1. Enregistrez les modifications et effectuez un test.

>[!CAUTION]
>
>Les gestionnaires 404.jsp et 403.jsp ont été spécialement conçus pour prendre en charge l’authentification CQ5 ; notamment pour permettre la connexion au système en cas d&#39;erreur.
>
>Par conséquent, le remplacement de ces deux gestionnaires devrait être effectué avec grand soin.

### Personnalisation de la réponse aux erreurs HTTP 500 {#customizing-the-response-to-http-errors}

Les erreurs HTTP 500 sont dues à des exceptions côté serveur.

* **[500 : Erreur de serveur interne](https://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html)**
Le serveur a rencontré une condition inattendue qui l’a empêché de satisfaire la demande.

Lorsque le traitement des demandes provoque une exception, le framework Apache Sling (sur laquelle CQ est basé) :

* consigne l’exception
* renvoie :

   * le code de réponse HTTP 500
   * trace de la pile d’exceptions

   dans le corps de la réponse.

La [personnalisation des pages affichées par le gestionnaire d’erreurs](#how-to-customize-pages-shown-by-the-error-handler) permet de créer un script `500.jsp`. Cependant, il n’est utilisé que si `HttpServletResponse.sendError(500)` est exécuté de manière explicite ; c’est-à-dire à partir d’un détecteur d’exceptions.

Dans le cas contraire, le code de réponse est défini sur 500, mais le script `500.jsp` n’est pas exécuté.

Pour gérer les erreurs de type 500, le nom de fichier du script de gestionnaire d’erreurs doit être identique à la classe d’exception (ou superclasse). Pour gérer toutes ces exceptions, vous pouvez créer un script `/apps/sling/servlet/errorhandler/Throwable.js` ou `/apps/sling/servlet/errorhandler/Exception.jsp`.

>[!CAUTION]
>
>Sur une instance de création, le [filtre de débogage de la gestion du contenu web CQ](/help/sites-deploying/osgi-configuration-settings.md) est activé par défaut. Le code de réponse est toujours 200. Le gestionnaire d’erreur par défaut répond en écrivant la trace de pile complète à la réponse.
>
>Des réponses avec le code 500 sont nécessaires pour un gestionnaire d’erreurs personnalisé. Par conséquent, le [filtre de débogage de la gestion du contenu Web CQ doit être désactivé](/help/sites-deploying/osgi-configuration-settings.md). Cela garantit le renvoi du code de réponse 500 qui, à son tour, déclenche le gestionnaire d’erreurs Sling approprié.
>
>Sur une instance de publication, le filtre de débogage de la gestion du contenu Web CQ est *toujours* désactivé (même s’il est configuré comme étant activé).
