---
title: Content Services
seo-title: Content Services
description: Content Services
seo-description: null
uuid: 7bd09c91-3931-400b-bdfc-b064b9ca9668
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/MOBILE
discoiquuid: 6a7e5472-cb57-4c78-b183-7c6dcac11a4e
exl-id: e900d93e-f7cd-4a0d-a866-7fc6c7882797
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 13%

---

# Content Services{#content-services}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

>[!NOTE]
>
>Adobe recommande d’utiliser l’éditeur d’application d’une seule page (SPA) pour les projets nécessitant un rendu côté client basé sur la structure SPA (par exemple, React). [En savoir plus](/help/sites-developing/spa-overview.md).

>[!CAUTION]
>
>La fonctionnalité Content Services est documentée à des fins d’aperçu uniquement.
>
>Il peut être modifié avec la version 6.3 GA Service Pack 1.

AEM Mobile Content Services est une fonctionnalité légère qui permet de demander du contenu géré par AEM. Cela permet à tous les développeurs d’applications d’obtenir du contenu de manière très performante sans avoir à posséder une connaissance approfondie du référentiel de contenu AEM (JCR) et de la structure web (Sling). Il permet de découpler les applications qui le demandent du référentiel de contenu.

Content Services introduit plusieurs nouveaux éléments d’AEM qui permettent à un développeur d’accéder AEM contenu géré sans connaître la structure de référentiel de ce contenu.

Ces éléments sont nécessaires pour préserver la flexibilité et permettre une extension future en fournissant une couche d’abstraction entre le contenu géré AEM et les applications mobiles qui consomment le contenu. Cela permet à AEM Content Services de fonctionner comme une couche d’abstraction entre les exigences de contenu de l’application native et le référentiel de contenu AEM.

Content Services peut diffuser le contenu sous la forme de ressources, de HTML empaqueté (HTML/CSS/JS) ou de contenu indépendant du canal.

>[!CAUTION]
>
>**Conditions préalables:**
>
>Avant de commencer à utiliser Content Services, assurez-vous d’activer l’indicateur Content Services. Pour activer la création et la gestion des modèles dans votre application, vous devez activer les modèles de données dans le navigateur de configuration.
>
>Voir **[Administration de Content Services](/help/mobile/developing-content-services.md)** pour plus d’informations.
>
>Pour plus d’informations, consultez la [documentation relative au Navigateur de configurations](/help/sites-administering/configurations.md).

![chlimage_1-143](assets/chlimage_1-143.png)

Une fois que vous avez défini l’indicateur Content Services et activé les modèles de données dans le navigateur de configuration, consultez les ressources ci-dessous pour commencer à utiliser AEM Mobile Content Services, familiarisez-vous avec les concepts de Content Services, tels que la gestion des modèles, la gestion des entités, suivie de la diffusion/du rendu de contenu pour AEM Mobile Content Services.

* Modèles dans le référentiel
* Rendu et diffusion
