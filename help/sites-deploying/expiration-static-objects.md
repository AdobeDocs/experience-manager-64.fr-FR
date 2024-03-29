---
title: Expiration des objets statiques
seo-title: Expiration of Static Objects
description: Découvrez comment configurer AEM afin que les objets statiques n’expirent pas (pendant une période raisonnable).
seo-description: Learn how to configure AEM so that static objects do not expire (for a reasonable period of time).
uuid: ee019a3d-4133-4d40-98ec-e0914b751fb3
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: configuring
content-type: reference
discoiquuid: 73f37b3c-5dbe-4132-bb60-daa8de871884
feature: Configuring
exl-id: 3551d25c-c852-4f59-84fe-5e62f57ae63f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 57%

---

# Expiration des objets statiques{#expiration-of-static-objects}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Les objets statiques (par exemple, les icônes) ne changent pas. Par conséquent, le système doit être configuré de sorte qu’il n’expire pas (pendant une période raisonnable) et ainsi réduire le trafic inutile.

Cela a l’impact suivant :

* Décharge les requêtes de l’infrastructure du serveur.
* Augmente les performances de chargement des pages, car le navigateur met en cache les objets dans le cache du navigateur.

Les expirations sont spécifiées par la norme HTTP concernant « l’expiration » des fichiers (voir, par exemple, Chapitre 14.21 de [RFC 2616](https://www.ietf.org/rfc/rfc2616.txt) « Hypertext Transfer Protocol - HTTP 1.1 »). Cette norme utilise l’en-tête pour permettre aux clients de mettre en cache des objets jusqu’à ce qu’ils soient considérés comme périmés ; ces objets sont mis en cache pendant la durée spécifiée sans qu’aucun contrôle de statut ne soit effectué sur le serveur d’origine.

>[!NOTE]
>
>Cette configuration est complètement distincte du Dispatcher (et ne fonctionnera pas pour lui).
>
>Le Dispatcher a pour objectif de mettre les données en mémoire cache en amont d’AEM.

Tous les fichiers, qui ne sont pas dynamiques et qui ne changent pas au fil du temps, peuvent et doivent être mis en cache. La configuration du serveur Apache HTTPD pourrait ressembler à l’un des suivants, selon l’environnement :

>[!CAUTION]
>
>Soyez prudent lorsque vous définissez la période pendant laquelle un objet est considéré comme étant à jour. Comme il y a *pas de vérification tant que la période spécifiée n’a pas expiré*, le client peut finir par présenter de l’ancien contenu à partir du cache.

1. **Pour une instance d’auteur :**

   ```xml
   LoadModule expires_module modules/mod_expires.so
   <Location /libs>
     ExpiresByType text/css "access plus 1 month"
     ExpiresByType text/javascript "access plus 1 month"
     ExpiresByType image/png "access plus 1 month"
     ExpiresByType image/gif "access plus 1 month"
   </Location>
   ```

   Cela permet au cache intermédiaire (par exemple le cache du navigateur) de stocker des fichiers CSS, Javascript, PNG et GIF pendant un mois au maximum, jusqu’à leur expiration. Cela signifie qu’ils n’ont pas besoin d’être demandés à AEM ou au serveur web, mais peuvent rester dans le cache du navigateur.

   Les autres sections du site ne doivent pas être mises en cache sur une instance d’auteur, car elles peuvent être modifiées à tout moment.

1. **Pour une instance de publication :**

   ```xml
   LoadModule expires_module modules/mod_expires.so
   <Location /content>
     ExpiresByType text/css "access plus 1 day"
     ExpiresByType text/javascript "access plus 1 day"
     ExpiresByType image/png "access plus 1 day"
     ExpiresByType image/gif "access plus 1 day"
   </Location>
   <Location /etc/designs>
     ExpiresByType text/css "access plus 1 day"
     ExpiresByType text/javascript "access plus 1 day"
     ExpiresByType image/png "access plus 1 day"
     ExpiresByType image/gif "access plus 1 day"
   </Location>
   ```

   Cela permet au cache intermédiaire (par exemple le cache du navigateur) de stocker des fichiers CSS, Javascript, PNG et GIF pendant un jour au maximum dans les caches clients. Bien que cet exemple illustre les paramètres globaux pour tout ce qui se situe sous `/content` et `/etc/designs`, vous devriez les rendre plus granulaires.

   Selon la fréquence de mise à jour de votre site, vous pouvez également envisager de mettre en cache les pages HTML. Un délai raisonnable serait d’une heure :

   ```xml
   <Location /content>
     ExpiresByType text/html "access plus 1 hour"
   </Location>
   ```

Après avoir configuré les objets statiques, parcourez `request.log`, tout en sélectionnant les pages qui contiennent de tels objets, pour confirmer qu’aucune demande (inutile) n’est faite pour les objets statiques.
