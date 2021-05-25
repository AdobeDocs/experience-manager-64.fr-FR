---
title: Définition de votre filtre de référent sur Autoriser vide
seo-title: Définition de votre filtre de référent sur Autoriser vide
description: Consultez cette page pour en savoir plus sur le filtre de référent. Pour permettre à la visionneuse d’applications AEM Mobile d’afficher les applications sur votre instance d’auteur, vous devez définir le filtre de référent HTML sur "autoriser vide".
seo-description: Consultez cette page pour en savoir plus sur le filtre de référent. Pour permettre à la visionneuse d’applications AEM Mobile d’afficher les applications sur votre instance d’auteur, vous devez définir le filtre de référent HTML sur "autoriser vide".
uuid: 4fb0f95c-ac8f-4a14-8c46-6616d9d4f380
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/MOBILE
topic-tags: administering-adobe-phonegap-enterprise
discoiquuid: 8fb7d088-94bf-4799-98b3-8fa58eef83df
exl-id: 81828b4c-cf0f-4722-8ae3-2e24be91a09b
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '223'
ht-degree: 47%

---

# Définition de votre filtre de référent sur Autoriser vide{#setting-your-referrer-filter-to-allow-empty}

>[!NOTE]
>
>Adobe recommande d’utiliser l’éditeur d’application d’une seule page (SPA) pour les projets nécessitant un rendu côté client basé sur la structure SPA (par exemple, React). [En savoir plus](/help/sites-developing/spa-overview.md).

Pour permettre à la visionneuse d’applications AEM Mobile d’afficher les applications sur votre instance d’auteur, vous devez définir le filtre de référent HTML sur &quot;autoriser vide&quot;.

Si vous n’avez pas l’intention d’utiliser la visionneuse d’application pour passer en revue les applications se trouvant aux stades de développement et intermédiaire, il n’est pas nécessaire de modifier le paramètre par défaut du filtre de référent.

Dans votre instance d’auteur en cours d’exécution d’AEM, accédez à : [http://localhost:4502/system/console/configMgr](http://localhost:4502/system/console/configMgr) et recherchez &quot;Apache Sling Referrer Filter&quot;. Cliquez pour modifier le filtre de référent et cochez la case « autoriser vide » (voir l’image ci-dessous). Cliquez ensuite sur le bouton Enregistrer et fermez la page du navigateur.

![Paramètres du filtre de référent](assets/chlimage_1-106.png)
