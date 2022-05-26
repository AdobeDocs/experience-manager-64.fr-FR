---
title: Appel d’AEM Forms à l’aide d’API
seo-title: Invoking AEM Forms using APIs
description: 'Adobe Experience Manager Forms est un logiciel d’entreprise basé sur J2EE qui se compose de services fonctionnant dans une infrastructure partagée. Découvrez comment utiliser des applications client pour appeler AEM Forms par programmation à l’aide d’une API Java, de services web, d’Remoting et d’une API REST. '
seo-description: Adobe Experience Manager Forms is J2EE-based enterprise software that consists of services that operate within a shared infrastructure. Learn how to use client applications to invoke AEM Forms programmatically using a Java API, web services, Remoting, and REST API.
uuid: d100e106-e508-4d3c-ba8c-b5fe13c9e2d6
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: development-tools, coding
discoiquuid: 1825e12c-0306-4e0a-9643-47ce1ce82132
role: Developer
exl-id: 6b60209f-aced-4698-97f1-b1a7782eef46
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 93%

---

# Appel d’AEM Forms à l’aide d’API {#invoking-aem-forms-using-apis}

Adobe Experience Manager Forms est un logiciel d’entreprise basé sur J2EE qui se compose de services fonctionnant dans une infrastructure partagée. Les opérations de service consomment ou produisent généralement des documents. En utilisant AEM Forms, vous pouvez combiner le workflow des formulaires avec les formulaires électroniques, la sécurité des documents et la génération de documents dans un ensemble intégré et cohérent de services. Ces services sont accessibles depuis l’intérieur et l’extérieur du pare-feu.

Les applications clientes peuvent appeler par programmation les services AEM Forms en utilisant une API Java, de services web, de Remoting et de REST. À l’aide de la console d’administration, vous pouvez configurer un service pour exposer un point d’entrée qui permet aux services AEM Forms d’être appelés par programmation. Par défaut, la plupart des services sont préconfigurés pour exposer des points d’entrée de service Remoting, Java et Web.

Les exigences de votre entreprise déterminent la méthode d’appel à utiliser. Par exemple, à l’aide de l’API Java, vous pouvez intégrer la fonctionnalité AEM Forms à vos applications d’entreprise Java, telles que Java Entity et Message Beans. De même, vous pouvez intégrer la fonctionnalité AEM Forms dans des projets .NET (ou d’autres projets développés avec des environnements de développement qui prennent en charge les normes de services web) à l’aide de services web.

Les services nécessitent un conteneur de services pour s’exécuter, de la même manière que Enterprise JavaBeans™ (EJB) nécessite un conteneur J2EE. AEM Forms ne comprend qu’une seule implémentation d’un conteneur de services. Le conteneur de service est chargé de la gestion de la durée de vie d’un service, y compris son déploiement et l’assurance que toutes les demandes sont envoyées au service approprié. Il gère également les documents qu’un service consomme ou produit.

>[!NOTE]
>
>La programmation avec AEM Forms ne comprend pas d’informations sur la manière d’appeler AEM Forms en utilisant des dossiers de contrôle ou des e-mails.
