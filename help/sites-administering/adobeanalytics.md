---
title: Intégration à Adobe Analytics
seo-title: Integrating with Adobe Analytics
description: Découvrez comment intégrer AEM à Adobe Analytics.
seo-description: Learn how to integrate AEM with Adobe Analytics.
uuid: 8329d891-1897-46f6-80ee-40244b079c0e
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: integration
content-type: reference
discoiquuid: 0089394f-0107-49eb-ad73-52e9cabe71b1
exl-id: ca11bfcd-06d1-4ca9-9069-afa91d8a6610
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 94%

---

# Intégration à Adobe Analytics{#integrating-with-adobe-analytics}

L’intégration d’Adobe Analytics et d’AEM vous permet de suivre votre activité de pages Web :

* Une configuration Adobe Analytics permet à AEM de s’authentifier avec Adobe Analytics.
* Une structure identifie les données envoyées à votre suite de rapports Adobe Analytics.

Les données incluent la page et les données sur l’utilisateur, par exemple :

* Données collectées par les composants AEM
* Clics sur les liens
* Informations sur l’utilisation des vidéos
* Nombre de visites de pages provenant d’Adobe Analytics

Les pages suivantes vous aident à configurer l’intégration :

* [Connexion à Adobe Analytics et création de frameworks](/help/sites-administering/adobeanalytics-connect.md)
* [Configuration du suivi des liens Adobe Analytics](/help/sites-administering/adobeanalytics-link.md)
* [Mappage des données de composant aux propriétés Adobe Analytics](/help/sites-administering/adobeanalytics-mapping.md)
* [Configuration du suivi vidéo pour Adobe Analytics](/help/sites-administering/adobeanalytics-video.md)

Vous pouvez également utiliser l’[assistant de souscription](/help/sites-administering/opt-in.md) pour exécuter facilement l’intégration.

>[!NOTE]
>
>Voir également l’article de procédures : [Intégration d’AEM avec Adobe Target et Analytics à l’aide de la gestion dynamique des balises](https://helpx.adobe.com/fr/experience-manager/using/integrate-digital-marketing-solutions.html).

## Informations supplémentaires {#further-information}

Voir :

* [Extension de l’intégration à Adobe Analytics](/help/sites-developing/extending-analytics.md) pour plus d’informations sur le développement de composants qui collectent des données utilisateur et la personnalisation de la structure d’Adobe Analytics.
* L’article de la base de connaissances, [Intégration Adobe Analytics : résolution des incidents](https://helpx.adobe.com/fr/experience-manager/kb/sitecatalystintegrationtroubleshooting.html) pour plus d’informations concernant le dépannage de votre intégration Adobe Analytics.

>[!NOTE]
>
>Si vous utilisez Adobe Analytics avec une configuration de proxy personnalisée, vous devez [configurer deux lots OSGi](/help/sites-deploying/configuring-osgi.md) (par exemple, avec la console web) requis pour les configurations de proxy **Apache HTTP Client**. Les deux lots sont requis, car certaines fonctionnalités d’AEM utilisent les API 3.x, tandis que d’autres utilisent les API 4.x. Configurer :
>
>* **Day Commons HTTP Client 3.1** pour configurer l’API 3.x ;\
   >  par exemple, [http://localhost:4502/system/console/configMgr/com.day.commons.httpclient](http://localhost:4502/system/console/configMgr/com.day.commons.httpclient)
>
>* **Apache HTTP Components Proxy Configuration** pour configurer l’API 4.x ;
>
>  par exemple, [http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator](http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator)
