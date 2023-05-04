---
title: Activation de CRXDE Lite dans AEM
seo-title: Enabling CRXDE Lite in AEM
description: Découvrez comment activer CRXDE Lite dans AEM.
seo-description: Learn how to enable CRXDE Lite in AEM.
uuid: d7a3db67-6384-463b-9aa9-f08ecc6c99c6
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: Security
content-type: reference
discoiquuid: 72df3ece-badf-466b-8f9a-0ec985d87741
exl-id: 3d8dc987-2ff9-4f71-bc07-48018caa3af4
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 80%

---

# Activation de CRXDE Lite dans AEM {#enabling-crxde-lite-in-aem}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Pour garantir que les installations AEM sont aussi sécurisées que possible, la liste de contrôle de sécurité recommande [désactivation de WebDAV](/help/sites-administering/security-checklist.md#disable-webdav) dans les environnements de production.

Toutefois, comme CRXDE Lite dépend du lot `org.apache.sling.jcr.davex` pour fonctionner correctement, désactiver WebDAV aura pour effet de désactiver CRXDE Lite également.

Lorsque ceci se produit, accéder à `https://serveraddress:4502/crx/de/index.jsp` affiche un nœud racine vide et toutes les requêtes HTTP aux ressources CRXDE Lite échouent :

```xml
404 Resource at '/crx/server/crx.default/jcr:root/.1.json' not found: No resource found
```

Bien que cette recommandation vise à réduire les surfaces d’attaque autant que possible, les administrateurs système peuvent parfois avoir besoin d’accéder à CRXDE Lite pour parcourir le contenu ou corriger des problèmes affectant les instances de production.

Si cette option est désactivée, vous pouvez activer CRXDE Lite en suivant la procédure ci-dessous :

1. Accédez à la console des composants OSGi sur `http://localhost:4502/system/console/components`.
1. Recherchez le composant suivant :

   * `org.apache.sling.jcr.davex.impl.servlets.SlingDavExServlet`

1. Cliquez sur l’icône de clé à molette située à côté pour afficher les options de configuration du composant :

   ![chlimage_1-80](assets/chlimage_1-80.png)

1. Créez la configuration suivante :

   * **Chemin racine :** `/crx/server`
   * Cochez la case **Utiliser des URI absolus**.

1. Une fois que vous avez terminé d’utiliser CRXDE Lite, assurez-vous de désactiver à nouveau WebDAV.

Vous pouvez également activer CRXDE Lite via cURL, en exécutant la commande suivante :

```shell
curl -u admin:admin -F "jcr:primaryType=sling:OsgiConfig" -F "alias=/crx/server" -F "dav.create-absolute-uri=true" -F "dav.create-absolute-uri@TypeHint=Boolean" http://localhost:4502/apps/system/config/org.apache.sling.jcr.davex.impl.servlets.SlingDavExServlet
```

## Autres ressources {#other-resources}

Pour plus d’informations sur les fonctions de sécurité d’AEM 6, consultez les pages suivantes :

* [Liste de contrôle de sécurité AEM](/help/sites-administering/security-checklist.md)
* [Exécution d’AEM en mode Prêt pour la production](/help/sites-administering/production-ready.md)
