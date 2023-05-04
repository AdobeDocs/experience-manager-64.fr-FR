---
title: Création de projets AEM à l’aide d’Apache Maven
description: Ce document décrit comment configurer un projet AEM basé sur Apache Maven
exl-id: 6ae0e387-468b-4cea-9e3f-0816d67b7621
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 72%

---

# Création de projets AEM à l’aide d’Apache Maven {#how-to-build-aem-projects-using-apache-maven}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

AEM 6.4 respecte les bonnes pratiques de gestion des packages et de structure des projets, telles qu’elles sont mises en œuvre par le dernier archétype de projet AEM pour les implémentations On-Premise et AMS.

>[!TIP]
>
>Pour plus d’informations, consultez les ressources suivantes :
>
>* L’article sur la [structure de projet AEM](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html?lang=fr) dans la documentation AEM as a Cloud Service pour savoir comment structurer des projets AEM modernes
>* La documentation sur l’[Archétype de projet AEM](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=fr) pour savoir comment démarrer un nouveau projet AEM à l’aide de l’archétype
>* L’article [Plug-in Maven de package de contenu Adobe](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developer-tools/maven-plugin.html#developer-tools) dans la documentation d’AEM as a Cloud Service pour savoir comment déployer des applications AEM.
>
>Les trois documents s’appliquent à AEM 6.4.
