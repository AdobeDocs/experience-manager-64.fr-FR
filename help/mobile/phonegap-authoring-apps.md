---
title: Création d’applications mobiles
seo-title: Authoring Mobile Applications
description: Le tableau de bord AEM Mobile vous permet de créer, de créer et de déployer votre application mobile, de créer, de supprimer et de modifier les métadonnées de l’application. Consultez cette page pour en savoir plus.
seo-description: he AEM Mobile Dashboard allows you to create, build and deploy your mobile application, create, delete and edit application metadata. Follow this page to learn more.
uuid: 293b5d29-df7e-42dd-ae64-8c677317e7a5
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/MOBILE
topic-tags: authoring-adobe-phonegap-enterprise
discoiquuid: abfeea65-102d-4800-abeb-304d61afcc13
exl-id: dbaa5221-4011-49cf-8123-5f8daa7fae76
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1060'
ht-degree: 3%

---

# Création d’applications mobiles{#authoring-mobile-applications}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

>[!NOTE]
>
>Adobe recommande d’utiliser l’éditeur d’application d’une seule page (SPA) pour les projets nécessitant un rendu côté client basé sur la structure SPA (par exemple, React). [En savoir plus](/help/sites-developing/spa-overview.md).

Le tableau de bord AEM Mobile vous permet de créer, de créer et de déployer votre application mobile, de créer, de supprimer et de modifier les métadonnées de l’application. Une fois votre application activée, vous pouvez analyser les analyses de l’application, y compris les mesures de cycle de vie et d’utilisation, afin d’améliorer la conversion des clients et la fidélité à la marque.

Pour créer votre application AEM Mobile, reportez-vous à la section [Création d’applications mobiles](/help/mobile/building-app-mobile-phonegap.md) page.

Pour configurer votre environnement et commencer, voir [Administration d’AEM pour utiliser AEM PhoneGap Enterprise](/help/mobile/administer-phonegap.md).

## Catalogue des applications AEM Mobile {#the-aem-mobile-apps-catalog}

Le [Catalogue d’applications AEM Mobile](http://localhost:4502/aem/apps.html/content/phonegap) affiche l’ensemble de votre application mobile gérée dans AEM.

Considérez ce catalogue comme la &quot;page d’entrée&quot; d’AEM Mobile, où les administrateurs peuvent démarrer une nouvelle application AEM Mobile en créant une application à partir d’un modèle ou en chargeant une application existante déjà lancée par un développeur mobile.

Pour accéder à la page d’entrée du catalogue d’applications, procédez comme suit :

1. Accédez à **Navigation** puis choisissez **Mobile**.

1. Choisir **Applications** pour ouvrir le catalogue d’applications.

![Catalogue d’applications AEM Mobile](assets/chlimage_1-135.png)

## Tableau de bord de l’application AEM Mobile {#the-aem-mobile-app-dashboard}

La sélection d’une application AEM Mobile dans le catalogue affiche son tableau de bord. Vous pouvez y gérer votre application, afficher des statistiques, créer, déployer et gérer le contenu de votre application mobile.

Vous pouvez développer chaque mosaïque du tableau de bord AEM Mobile pour afficher ou modifier les détails en cliquant sur &quot;...&quot;. dans le coin inférieur droit.

![Centre de commandes des applications AEM Mobile](assets/chlimage_1-136.png)

### Mosaïque Gérer l’application {#the-manage-app-tile}

La mosaïque Gérer l’application affiche l’icône, le nom, la description de votre application, les plateformes prises en charge, appelle la page d’accueil pour les mises à jour, l’URL et les informations de version. Vous pouvez accéder à cette mosaïque pour modifier et gérer la configuration de l’application PhoneGap (config.xml), puis préparer votre application pour l’envoi aux différentes boutiques d’applications en vue de sa distribution.

Cliquez sur [here](/help/mobile/phonegap-app-details-tile.md) pour plus d’informations.

![chlimage_1-137](assets/chlimage_1-137.png)

### Mosaïque Gérer le contenu de la page {#the-manage-page-content-tile}

Le contenu peut être créé, mis à jour et supprimé dans AEM Mobile de la même manière que vous le faites dans AEM Sites. Le **Mosaïque Gestion du contenu de la page** affiche le nombre de pages de contenu géré et de la dernière modification. Vous pouvez analyser le contenu pour créer, copier, déplacer, supprimer et mettre à jour des pages en cliquant sur chaque enregistrement de la mosaïque. Une fois que le contenu a été mis à jour, vous pouvez envoyer une mise à jour de contenu à vos clients via le **Mosaïque Gestion des packages de contenu .**

![Mosaïque Contenu](assets/chlimage_1-138.png)

### Mosaïque Gestion des packages de contenu {#the-manage-content-packages-tile}

Une fois que vous avez ajouté ou modifié votre contenu par le biais de la mosaïque Gérer le contenu de la page , vous pouvez envoyer ces modifications à vos clients avec une mise à jour de la version du contenu.

Le module de contenu permet à AEM’auteur d’applications de gérer le contenu des pages dans AEM et de demander à votre équipe de développement d’apporter des modifications à votre application Shell PhoneGap (c’est-à-dire la structure ou l’infrastructure de l’application), puis d’envoyer ces modifications rapidement à vos clients, sans avoir à enrôler un développeur pour qu’il les soumette à nouveau aux différentes boutiques pour distribution.

Le module de contenu crée un fichier ZIP, considéré comme un module de version de contenu, pour chaque mise à jour. Ces modules contiennent des ressources HTML et des pages HTML générées lors du rendu de l’application. Ils sont suffisamment intelligents pour ne compresser que les fichiers qui ont été modifiés depuis la dernière mise à jour.

Mosaïque Gérer le module de contenu **Type** La colonne affiche &quot;Application&quot; pour indiquer le contenu du shell d’application, par exemple la structure ou l’infrastructure de l’application gérée par un développeur, ou &quot;Contenu&quot; pour représenter le contenu de la page géré par l’auteur du contenu.

Le contenu peut être représenté sous la forme d’une langue ou d’une partie particulière de l’application où plusieurs modules de publication de contenu sont utilisés par l’application. Le choix du mode de regroupement de votre contenu est conçu pour être flexible et entièrement à la hauteur de la manière dont vous souhaitez gérer le contenu de votre application.

Le **Modifié** indique le moment où les pages ont été modifiées le plus récemment.

Le **Intermédiaire** affiche la date de la dernière mise à jour du contenu. Pour créer une mise à jour de contenu et préparer vos modifications, ouvrez n’importe quel enregistrement dans la mosaïque et créez une nouvelle mise à jour.

Le **Publié** indique le moment où la dernière mise à jour du contenu a été publiée et mise à disposition de vos clients pour utilisation. Pour publier du contenu, vous devez d’abord en faire l’étape, puis publier la mise à jour en parcourant cette mosaïque et en la publiant à partir de la console Détails de la version de contenu .

![Mosaïque Version du contenu](assets/chlimage_1-139.png) ![Package ContentSync pour l’interpréteur d’application](do-not-localize/chlimage_1-5.png)

Cette icône représente un package Content Release pour le shell d’application.

![](do-not-localize/chlimage_1-6.png)

Ces icônes représentent un module de version de contenu pour le contenu de l’application.

### Mosaïque PhoneGap Build {#the-phonegap-build-tile}

Le **Mosaïque PhoneGap Build** se connecte à [https://build.phonegap.com](https://build.phonegap.com) pour créer et héberger des builds distants. Une fois créée, la version est disponible en téléchargement ou directement sur votre appareil via un code QR.

Vous pouvez également télécharger la source du périphérique à créer localement via le [Interface de ligne de commande de PhoneGap](https://docs.phonegap.com/en/3.5.0/guide_cli_index.md.html).

![Mosaïque PhoneGap Build](assets/chlimage_1-140.png)

### Mosaïque Mesures {#the-metrics-tile}

>[!CAUTION]
>
>La mosaïque Mesures s’affiche uniquement une fois que vous avez configuré le service cloud.
>
>Voir [Configuration de votre Cloud Service Mobile Services Adobe](/help/mobile/configure-adobe-mobile-cloud-service.md) pour plus d’informations.

AEM Mobile s’intègre à Adobe Analytics via [SDK Adobe Mobile Services](https://www.adobe.com/ca/solutions/digital-marketing/mobile-services/app-sdk.html) (AMS).

Le Centre de contrôle **Mosaïque Mesures** affiche les analyses récapitulatives extraites d’AMS pour votre application. Vous pouvez accéder au tableau de bord des analyses en cliquant sur &quot;...&quot;. en bas à droite.

![Mosaïque Mesures](assets/chlimage_1-141.png)

### Mosaïque Gérer le contenu de l’entité {#the-manage-entity-content-tile}

La mosaïque Gérer le contenu des entités vous permet d’ajouter et de gérer des définitions d’application. Les définitions d’application permettent d’identifier les espaces (et autres configurations) appropriés à l’application. De cette manière, un nouvel espace peut être ajouté, sans avoir à recompiler l’application. La définition de l’application est mise à jour et inclut les informations de tous les nouveaux espaces.

Cliquez sur [here](/help/mobile/phonegap-app-definitions.md) pour créer et gérer les définitions de votre application.

Vous pouvez accéder au tableau de bord de gestion du contenu des entités en cliquant sur &quot;...&quot;. en bas à droite.

![chlimage_1-142](assets/chlimage_1-142.png)

#### Ressources supplémentaires {#additional-resources}

Pour en savoir plus sur les rôles et les responsabilités d’un administrateur et d’un développeur, consultez les ressources ci-dessous :

* [Développement pour Adobe PhoneGap Enterprise avec AEM](/help/mobile/developing-in-phonegap.md)
* [Administration de contenu pour Adobe PhoneGap Enterprise avec AEM](/help/mobile/administer-phonegap.md)
