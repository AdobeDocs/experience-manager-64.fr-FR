---
title: Prévenir les attaques CSRF
seo-title: Preventing CSRF attacks
description: Découvrez comment empêcher les attaques CSRF (Cross-site request forgery) et protéger les données utilisateur contre les compromis.
seo-description: Learn how to prevent Cross-site request forgery (CSRF) attacks and safeguard user data from being compromised.
uuid: f3553826-f5eb-40ea-aeb7-90e4ad30598c
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_user_management
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: a3cbffb7-c1d1-47c2-bcfd-70f1e2d81ac9
exl-id: 89286798-e02a-45d8-a91d-c50ef4dc7f25
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1007'
ht-degree: 33%

---

# Prévenir les attaques CSRF {#preventing-csrf-attacks}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

## Fonctionnement des attaques CSRF {#how-csrf-attacks-work}

Une attaque multisite par usurpation de requête ou CSRF (Cross-site request forgery) consiste à utiliser le navigateur d’un utilisateur valide pour envoyer une requête malveillante via un élément iframe, par exemple. Étant donné que le navigateur envoie les cookies sur une base de domaine, si l’utilisateur est actuellement connecté à une application, les données de l’utilisateur peuvent être compromises.

Supposons, par exemple, que vous soyez connecté à Administration Console dans un navigateur. Vous recevez un message électronique contenant un lien. Cliquez sur le lien pour ouvrir un nouvel onglet dans votre navigateur. La page que vous avez ouverte contient un iFrame masqué qui émet une requête malveillante au serveur Forms à l’aide du cookie de votre session d’AEM authentifiée. Comme User Management reçoit un cookie valide, il transmet la demande.

## Termes liés aux CSRF {#csrf-related-terms}

**Référent :** adresse de la page source à partir de laquelle la requête est envoyée. Par exemple, une page web sur site1.com contient un lien vers site2.com. Un clic sur le lien envoie une requête à site2.com. Le référent de cette requête est site1.com, car la requête provient d’une page dont la source est site1.com.

**URI Placés sur la liste autorisée :** Les URI identifient les ressources sur le serveur Forms qui sont demandées, par exemple /adminui ou /contentspace. Certaines ressources peuvent autoriser des requêtes à entrer dans l’application à partir de sites Web externes. Ces ressources sont considérées comme des URI placés sur la liste autorisée. Le serveur Forms ne vérifie jamais le référent des URI placés sur la liste autorisée.

**Référent de valeur NULL :** lorsque vous ouvrez une nouvelle fenêtre ou un nouvel onglet de navigation et saisissez une adresse puis appuyez sur Entrée, la valeur du référent est NULL. La demande est entièrement nouvelle et ne provient pas d’une page Web parente ; il n’existe donc aucun référent pour la requête. Le serveur Forms peut recevoir un référent null de :

* demandes effectuées sur des points de terminaison SOAP ou REST depuis Acrobat
* lorsqu’un utilisateur final effectue une requête HTTP sur un point d’entrée SOAP ou REST AEM Forms ;
* lorsqu’une nouvelle fenêtre de navigateur est ouverte et que l’URL de toute page de connexion de l’application web d’AEM forms est saisie.

Autoriser un référent null sur les points de terminaison SOAP et REST. Autorisez également un référent null sur toutes les pages de connexion URI telles que /adminui et /contentspace et leurs ressources mappées correspondantes. Par exemple, le servlet mappé pour /contentspace est /contentspace/faces/jsp/login.jsp, qui doit être une exception référent nulle. Cette exception n’est requise que si vous activez le filtrage par GET pour votre application web. Vos applications peuvent indiquer s’il faut autoriser des référents nuls. Consultez la section « Se protéger des attaques Cross-Site Request Forgery » dans [Renforcement et sécurité dʼAEM Forms](https://help.adobe.com/fr_FR/livecycle/11.0/HardeningSecurity/index.html).

**Exceptions aux référents autorisés :** les exceptions aux référents autorisés constituent une sous-liste de la liste de référents autorisés, dont les requêtes sont bloquées. Les exceptions aux référents autorisés sont spécifiques à une application Web. Si vous souhaitez que certains référents de vos référents autorisés ne soient pas en mesure d’appeler une application web spécifique, vous pouvez les placer sur la liste bloquée à l’aide des exceptions aux référents autorisés. Les exceptions aux référents autorisés peuvent être spécifiées dans le fichier web.xml de votre application (consultez la section Protection contre les attaques multisite par usurpation de requête dans Renforcement et sécurité d’AEM Forms sur la page Aide et didacticiels).

## Fonctionnement des référents autorisés {#how-allowed-referers-work}

AEM forms fournit un filtrage des référents, ce qui peut aider à empêcher les attaques CSRF. Le filtrage des référents fonctionne comme suit :

1. Le serveur Forms vérifie la méthode HTTP utilisée pour l’appel :

   * S’il est POST, le serveur Forms vérifie l’en-tête du référent.
   * S’il s’agit d’une méthode GET, le serveur Forms ignore la vérification du référent, à moins que la variable CSRF_CHECK_GETS ne soit définie sur true. Dans ce cas, il vérifie l’en-tête du référent. La variable CSRF_CHECK_GETS est spécifiée dans le fichier web.xml pour votre application. (Voir &quot;Protection contre les attaques multisites par usurpation de requête&quot; dans [Guide de renforcement et de sécurité](https://help.adobe.com/fr_FR/livecycle/11.0/HardeningSecurity/index.html).)

1. Le serveur Forms vérifie si l’URI requis est placé sur la liste autorisée :

   * Si cʼest le cas, le serveur transmet la requête.
   * Dans le cas contraire, le serveur récupère le référent de la requête.

1. S’il existe un référent dans la requête, le serveur vérifie s’il s’agit d’un référent autorisé. S’il est autorisé, le serveur recherche une exception de référent :

   * S’il s’agit d’une exception, la requête est bloquée.
   * S’il ne s’agit pas d’une exception, la requête est transmise.

1. S’il n’y a aucun référent dans la requête, le serveur vérifie si un référent de valeur NULL est autorisé.

   * Si un référent null est autorisé, la requête est transmise.
   * Si un référent null n’est pas autorisé, le serveur vérifie si l’URI requis est une exception pour un référent null et traite la demande en conséquence.

## Configuration des référents autorisés {#configure-allowed-referers}

Lorsque vous exécutez Configuration Manager, l’hôte par défaut et l’adresse IP ou le serveur Forms sont ajoutés à la liste de référents autorisés. Vous pouvez modifier cette liste dans Administration Console.

1. Dans Administration Console, cliquez sur Paramètres > User Management > Configuration > Configurer les URL de référent autorisées. La liste de référents autorisés s’affiche au bas de la page.
1. Pour ajouter un référent autorisé :

   * Saisissez un nom d’hôte ou une adresse IP dans la zone Référents autorisés . Pour ajouter plusieurs référents autorisés à la fois, saisissez chaque nom d’hôte ou adresse IP sur une nouvelle ligne.
   * Dans les zones Port HTTP et Port HTTPS, spécifiez les ports à autoriser pour le protocole HTTP, HTTPS ou les deux. Si vous laissez ces zones vides, les ports par défaut (port 80 pour HTTP et port 443 pour HTTPS) sont utilisés. Si vous saisissez `0` (zéro) dans les champs, tous les ports sont activés sur ce serveur. Vous pouvez également saisir un numéro de port spécifique pour activer uniquement ce port.
   * Cliquez sur Ajouter.

1. Pour supprimer l’entrée de la liste de référents autorisés, sélectionnez l’élément dans la liste, puis cliquez sur Supprimer.

   Si la liste de référents autorisés est vide, la fonction CSRF cesse de fonctionner et le système n’est plus sécurisé.

1. Après avoir modifié la liste de référents autorisés, redémarrez le serveur d’AEM forms.
