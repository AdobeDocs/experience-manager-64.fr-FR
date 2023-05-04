---
title: Restructuration des référentiels dans AEM 6.4
seo-title: Repository Restructuring in AEM 6.4
description: Découvrez les principes de base et la logique sur laquelle repose le reformatage des référentiels dans AEM 6.4.
seo-description: Learn about the basics and reasoning behind the repository restructuring in AEM 6.4
uuid: e9cd3e88-e352-44a8-9b97-69488d3267cb
contentOwner: chaikels
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: repo_restructuring
discoiquuid: fc879b0b-823b-4bdc-aaa6-36f53a33fb22
feature: Upgrading
exl-id: 6ff5a23a-c9b5-49ca-87b2-ba01eaf48a9f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '573'
ht-degree: 74%

---

# Restructuration des référentiels dans AEM 6.4{#repository-restructuring-in-aem}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

## Présentation {#introduction}

Dans les versions antérieures à AEM 6.4, le code client était déployé dans des zones imprévisibles du référentiel JCR, lesquelles pouvaient donc varier lors des mises à niveau. Pour cette raison, il était courant que les versions AEM officielles écrasent le code, la configuration ou le contenu personnalisé. En outre, les modifications des clients ont parfois remplacé AEM code ou contenu du produit, rompant ainsi la fonctionnalité du produit.

Il est possible d’éviter ces conflits en définissant clairement les hiérarchies applicables au code du produit AEM et au code client.

À cette fin, à compter de la version AEM 6.4 et pour les versions à venir, le contenu est restructuré à partir de /etc vers d’autres dossiers du référentiel, avec des instructions sur le contenu du répertoire, en respectant les règles de haut niveau suivantes :

* Le code de produit AEM sera toujours placé dans /libs, qui ne peut pas être écrasé par du code personnalisé.
* Le code personnalisé doit être placé dans /apps, /content et /conf.

## Impact sur les mises à niveau vers la version 6.4 {#impact-on-upgrades}

Lors de la mise à niveau vers AEM 6.4, un sous-ensemble important du contenu sous /etc sera dupliqué dans d’autres dossiers du référentiel. Ces nouveaux emplacements sont les emplacements favoris dans lesquels le contenu est référencé. Cependant, tout a été mis en œuvre pour que la mise à niveau d’AEM 6.4 soit rétrocompatible avec les emplacements précédents du dossier /etc. Ainsi, dans la plupart des cas, les anciens emplacements continueront à être référencés par le code AEM jusqu’à ce que les modifications soient activement - et dans de nombreux cas manuellement - créées dans l’application d’un client. Du point de vue de la chronologie, il existe deux catégories de modifications :

* Avec la mise à niveau vers la version 6.4 : quelques modifications de restructuration /etc ne sont pas compatibles avec les versions antérieures. Par conséquent, les modifications doivent être planifiées et implémentées dans le cadre de la mise à niveau d’AEM 6.4.
* Avant la mise à niveau vers la version 6.5 : la grande majorité des modifications de restructuration /etc peuvent être différées jusqu’à un certain temps après la mise à niveau. Comme mentionné précédemment, le code AEM 6.4 continuera à faire référence aux anciens emplacements jusqu’à ce que les modifications soient implémentées dans le cadre d’une version client. Bien qu’il n’existe pas de calendrier forcé pour lequel les modifications doivent être apportées, il est recommandé de les effectuer avant la mise à niveau vers la version 6.5, car les fonctionnalités futures pourront dépendre des nouveaux emplacements référencés. De plus, par convention, la documentation relative à une fonctionnalité donnée référencera les nouveaux emplacements. Cela pourrait donc prêter à confusion si les anciens emplacements sont toujours utilisés.

### Conseils de restructuration {#restructuring-guidance}

Lors de la planification d’une mise à niveau vers AEM 6.4, les pages suivantes par solution doivent être référencées afin d’évaluer le travail :

* [Restructuration du référentiel commun à toutes les solutions AEM](/help/sites-deploying/all-repository-restructuring-in-aem-6-4.md)
* [Restructuration du référentiel d’AEM Sites](/help/sites-deploying/sites-repository-restructuring-in-aem-6-4.md)
* [Restructuration du référentiel d’AEM Assets](https://experienceleague.adobe.com/docs/experience-manager-64/deploying/restructuring/repository-restructuring.html?lang=fr)
* [Restructuration du référentiel d’AEM Assets Dynamic Media](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-4.md)
* [Restructuration du référentiel d’AEM Forms](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md)
* [Restructuration du référentiel d’AEM Communities](/help/sites-deploying/communities-repository-restructuring-in-aem-6-4.md)
* [Restructuration du référentiel d’AEM Commerce](/help/sites-deploying/ecommerce-repository-restructuring-in-aem-6-4.md)

Chaque page contient deux sections correspondant à l’urgence des modifications nécessaires. Tout élément de la section « Avec la mise à niveau vers la version 6.4 » doit être traité dans le cadre du projet de mise à niveau d’AEM 6.4. Tout ce qui se trouve sous &quot;Avant la mise à niveau vers la version 6.5&quot; peut éventuellement être différé avant la mise à niveau.

Chaque entrée de la page comprend un champ &quot;Conseil de restructuration&quot;, qui détaille la stratégie technique recommandée pour l’alignement avec le nouveau modèle de référentiel 6.4 afin que les nouveaux emplacements soient référencés pour le contenu situé précédemment sous le dossier /etc. Un champ supplémentaire « Remarques » fournit un contexte utile.
