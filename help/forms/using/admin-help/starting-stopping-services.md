---
title: Démarrer et arrêter des services
seo-title: Starting and stopping services
description: Découvrez comment démarrer et arrêter les services associés aux modules AEM Forms et au serveur applicatif et à la base de données.
seo-description: Learn how to start and stop services associated with AEM Forms modules and the application server and database.
uuid: 8c831cb2-4165-4118-8a09-764cec4e5e05
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_services
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: b93060bd-c6e1-40d2-8acd-ccafb8ed56da
exl-id: 6e0607d6-171c-4119-95a1-373b30fb63c1
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 25%

---

# Démarrer et arrêter des services {#starting-and-stopping-services}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Il existe deux types de services faisant partie d’AEM Forms :

* Services qui contrôlent le serveur d’applications et la base de données d’AEM forms.
* Services qui contrôlent les modules d’AEM forms

## Démarrage ou arrêt des services associés aux modules d’AEM forms {#start-or-stop-the-services-associated-with-aem-forms-modules}

Les modules de formulaires AEM (par exemple, Forms, Rights Management, Output) fonctionnent comme des services. Parfois, vous devrez peut-être arrêter ou démarrer les services pour ces modules d’AEM forms. Par exemple, vous devez arrêter, puis redémarrer un service d’AEM forms après avoir modifié un paramètre du service.

1. Dans Console d’administration, cliquez sur **Services** > **Applications et services** > **Gestion des services**.
1. Sur la page Gestion des services, cochez la case en regard du service à arrêter ou à démarrer, puis cliquez sur Arrêter ou Démarrer.

## Démarrage ou arrêt des services pour le serveur d’applications et la base de données {#start-or-stop-services-for-the-application-server-and-database}

Une mise en oeuvre complète d’AEM forms comprend un serveur d’applications et des services de base de données :

* *`[application server]`* pour AEM Forms
* *`[database]`* pour AEM Forms

Sous Windows, ces services sont accessibles dans **Outils d’administration** > **Panneau de services**. Par exemple, si vous avez installé AEM forms on JBoss à l’aide de la méthode clé en main, les services suivants sont disponibles sur votre système :

* JBoss pour Adobe Experience Manager forms
* MySQL pour Adobe Experience Manager forms

Démarrez ou arrêtez ces services en les sélectionnant dans la liste du panneau Services , puis en cliquant sur le bouton d’action approprié dans le panneau.

Sous UNIX® ou Linux, saisissez le texte suivant à partir d’une ligne de commande, dans laquelle *`[service name]`* correspond au nom du service à vérifier :

```as3
     ps -A | grep [service name]
```
