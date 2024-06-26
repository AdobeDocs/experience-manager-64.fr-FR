---
title: Votre application hybride est-elle prête pour AEM Mobile ?
seo-title: Is your hybrid app ready for AEM Mobile?
description: Consultez cette page pour en savoir plus sur les applications hrybrid. Une application dans AEM est généralement divisée en deux parties. Le "shell" et le "contenu" et cette page fournissent des informations supplémentaires sur ces sujets.
seo-description: Follow this page to learn about hrybrid apps. An app in AEM is commonly divided into two parts. The 'shell' and 'content' and this page provides more insight on these topics.
uuid: cbcce3fa-9100-46ea-9f24-931b42666709
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/MOBILE
topic-tags: developing-adobe-phonegap-enterprise
discoiquuid: b7fd7954-f2a5-402d-b259-e18b5a618be9
pagetitle: Is your hybrid app ready for AEM Mobile?
exl-id: 79eafdb5-8b83-466a-8d06-da1a655a0619
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '777'
ht-degree: 4%

---

# Votre application hybride est-elle prête pour AEM Mobile ?{#is-your-hybrid-app-ready-for-aem-mobile}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

>[!NOTE]
>
>Adobe recommande d’utiliser l’éditeur d’application d’une seule page (SPA) pour les projets nécessitant un rendu côté client basé sur la structure SPA (par exemple, React). [En savoir plus](/help/sites-developing/spa-overview.md).

Vous avez importé votre application PhoneGap hybride ou Cordova dans AEM, et maintenant ? Il est probable que vous souhaitiez ajouter du contenu modifiable à votre application. Pour accomplir cette tâche, vous aurez besoin d’une compréhension générale de la structure d’une application AEM. Une application dans AEM est généralement divisée en deux parties. &quot;shell&quot; et &quot;contenu&quot;. Le &quot;shell&quot; comprend les parties statiques de votre application ; tels que les fichiers de configuration PhoneGap, la structure de l’application et les commandes de navigation. Le contenu de l’archive que vous avez importée est stocké dans le shell. Dans le contexte de ce document, le shell est tout le contenu créé non AEM de votre application PhoneGap hybride créée par le développeur de l’application.

Le contenu fait référence aux composants, modèles et pages créés dans AEM générés par le développeur AEM. Le contenu est classé comme contenu de développement ou comme contenu créé. Les composants, conceptions et modèles de page sont considérés comme du contenu de développement puisqu’ils sont créés par un développeur. author-content sont des pages qui ont été créées à l’aide des composants et des modèles. Elles sont généralement effectuées par un concepteur ou un spécialiste du marketing.

L’ajout de pages d’AEM créées à votre application hybride nécessite une coordination entre le développeur de l’application et le développeur AEM. Partout dans l’application où vous souhaitez ajouter du contenu créé, le développeur de l’application doit organiser ces pages dans une structure qui peut être superposée dans AEM. Le développeur de l’application doit être en mesure de fournir au développeur de l’AEM les chemins d’accès vers lesquels le contenu créé AEM doit être ajouté, puis fournir une page d’espace réservé dans l’application hybride qui sera remplacée après que le développeur de l’AEM a créé le contenu de la page.

Pour faciliter le suivi de l’explication, nous utiliserons le Marketing Cloud AEM : Référence hybride AEM Mobile pour expliquer les concepts. L’application de référence hybride est composée d’une page de bienvenue avec un menu latéral.

![chlimage_1-76](assets/chlimage_1-76.png)

Dans cet exemple, nous allons créer la page de bienvenue de l’application. Jetez un coup d&#39;oeil à la source [https://github.com/Adobe-Marketing-Cloud-Apps/aem-mobile-hybrid-reference/blob/master/hybrid-app/www/js/app.js#L75](https://github.com/Adobe-Marketing-Cloud-Apps/aem-mobile-hybrid-reference/blob/master/hybrid-app/www/js/app.js#L75). Nous constatons que le développeur de l’application a défini une page de bienvenue et fourni un modèle pour la page rendue par l’application. C’est là que le développeur de l’application et le développeur AEM doivent se coordonner. Le chemin d’accès au modèle de page de bienvenue dans l’application de référence hybride est défini sur &quot;content/mobileapps/hybrid-reference-app/en/welcome.template.html&quot;. Ce chemin d’accès est extrêmement important, car le développeur AEM va créer sa page de bienvenue dans le référentiel AEM en utilisant le même chemin d’accès.

![chlimage_1-77](assets/chlimage_1-77.png)

Il est important que l’application hybride et le contenu créé AEM utilisent le même chemin d’accès car nous comptons sur la possibilité de superposer du contenu à l’aide de la synchronisation de contenu pour ajouter de nouvelles pages à l’application hybride. Lorsque l’application hybride est importée dans AEM dans le cadre du processus d’importation, les configurations de synchronisation du contenu sont configurées.

![chlimage_1-78](assets/chlimage_1-78.png)

Lorsque vous &quot;Téléchargez la source&quot; depuis le tableau de bord de l’application, ces scripts ContentSync sont exécutés pour assembler une archive de votre application hybride.

![chlimage_1-79](assets/chlimage_1-79.png)

ContentSync extrait d’abord &quot;shell&quot; de l’application, où est stocké tout le contenu développé par l’application Hybrid, puis extrait le &quot;contenu&quot; de l’application. Désormais, si des pages de l’interpréteur de commandes ont le même chemin que dans &quot;contenu&quot;, les pages situées sous &quot;contenu&quot; seront (remplacées) par les pages situées sous &quot;contenu&quot;. En d’autres termes, dans l’exemple d’application de référence hybride, si nous créons une page dans AEM qui a le même chemin que &quot;content/mobileapps/hybrid-reference-app/en/welcome.template.html&quot; lorsque ContentSync s’exécute, elle recouvrera la page qui faisait partie de l’application de référence hybride avec tout ce qui se trouve dans AEM à cet emplacement. La superposition est prise en charge par ContentSync. Pour les utilisateurs de l’application, les mises à jour apportées à l’application avec AEM contenu créé apparaissent de manière transparente et ne nécessitent pas de reconstruction de l’application. Par conséquent, lorsque vous exécutez l’application, la page de bienvenue s’affiche comme suit :

![chlimage_1-80](assets/chlimage_1-80.png)
