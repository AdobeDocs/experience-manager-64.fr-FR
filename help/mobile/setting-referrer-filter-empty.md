---
title: Définition du filtre de référent sur Autoriser vide
seo-title: Setting Your Referrer Filter to Allow Empty
description: Consultez cette page pour en savoir plus sur le filtre de référent. Pour permettre à la visionneuse d’applications AEM Mobile d’afficher les applications sur votre instance d’auteur, vous devez définir le filtre de référent de HTML sur "autoriser vide".
seo-description: Follow this page to learn about Referrer Filter. In order to allow the AEM Mobile Application Viewer to view apps on your Author instance, you'll need to set your HTML referrer filter to 'allow empty'.
uuid: 4fb0f95c-ac8f-4a14-8c46-6616d9d4f380
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/MOBILE
topic-tags: administering-adobe-phonegap-enterprise
discoiquuid: 8fb7d088-94bf-4799-98b3-8fa58eef83df
exl-id: 81828b4c-cf0f-4722-8ae3-2e24be91a09b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 15%

---

# Définition du filtre de référent sur Autoriser vide{#setting-your-referrer-filter-to-allow-empty}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

>[!NOTE]
>
>Adobe recommande d’utiliser l’éditeur d’application d’une seule page (SPA) pour les projets nécessitant un rendu côté client basé sur la structure SPA (par exemple, React). [En savoir plus](/help/sites-developing/spa-overview.md).

Pour permettre à la visionneuse d’applications AEM Mobile d’afficher les applications sur votre instance d’auteur, vous devez définir le filtre de référent de HTML sur &quot;autoriser vide&quot;.

Si vous n’avez pas l’intention d’utiliser la visionneuse d’applications pour passer en revue les applications dans les états de développement et d’évaluation, il n’est pas nécessaire de modifier le paramètre par défaut du filtre de référent.

Dans votre instance d’auteur en cours d’exécution d’AEM, accédez à : [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr) et recherchez &quot;Apache Sling Referrer Filter&quot;. Cliquez pour modifier le filtre de référent et cochez la case &quot;autoriser vide&quot; (voir l’image ci-dessous). Appuyez ensuite sur le bouton d’enregistrement et fermez la page du navigateur.

![Paramètres du filtre de référent](assets/chlimage_1-106.png)
