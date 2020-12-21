---
title: Présentation des rapports sur les transactions
seo-title: Présentation des rapports sur les transactions
description: Conserver le décompte de tous les formulaires envoyés, les communications interactives rendues, les Documents convertis en un autre format, etc.
seo-description: Conserver le décompte de tous les formulaires envoyés, les communications interactives rendues, les Documents convertis en un autre format, etc.
uuid: b40220e6-88c8-4507-b228-6c57d9b54422
contentOwner: khsingh
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: forms-manager
discoiquuid: 1fb11e02-d8f1-41a0-8e23-cb890b4e2244
translation-type: tm+mt
source-git-commit: 0797eeae57ac5a9676c6d308eaf2aaffab999d18
workflow-type: tm+mt
source-wordcount: '593'
ht-degree: 0%

---


# Aperçu des rapports de transactions {#transaction-reports-overview}

Conserver le décompte de tous les formulaires envoyés, les communications interactives rendues, les Documents convertis en un autre format, etc.

## Présentation {#introduction}

Les rapports de transactions à AEM Forms vous permettent de conserver le décompte de toutes les transactions effectuées depuis une date spécifiée dans votre déploiement AEM Forms. L&#39;objectif est de fournir des informations sur l&#39;utilisation des produits et d&#39;aider les parties prenantes à comprendre leurs volumes de traitement numérique. Voici quelques exemples d’une transaction :

* Envoi d’un formulaire adaptatif, d’un formulaire HTML5 ou d’un jeu de formulaires
* Rendu d&#39;une version imprimée ou Web d&#39;une communication interactive
* Conversion d’un document d’un format de fichier à un autre

Pour plus d&#39;informations sur ce qui est considéré comme une transaction, voir [API facturables](/help/forms/using/transaction-reports-billable-apis.md).

L’enregistrement de transaction est désactivé par défaut. Vous pouvez [activer l&#39;enregistrement des transactions](/help/forms/using/viewing-and-understanding-transaction-reports.md#setting-up-transaction-reports) à partir de AEM Web Console. Vous pouvez vue des rapports de transactions sur les instances d’auteur, de traitement ou de publication. Vue des rapports de transactions sur les instances d&#39;auteur ou de traitement pour une somme agrégée de toutes les transactions. Les transactions de vue génèrent des rapports sur les instances de publication pour comptabiliser toutes les transactions qui ont lieu uniquement sur cette instance de publication à partir de laquelle l&#39;état est exécuté.

Ne créez pas de contenu (créez des formulaires adaptatifs, des communications interactives, des thèmes et d’autres activités de création) et de documents de processus (utilisez des workflows, des services de document et d’autres activités de traitement) sur la même instance AEM. Conservez l’enregistrement de transaction désactivé pour les serveurs AEM Forms utilisés pour créer du contenu. Activez l’enregistrement des transactions pour les serveurs AEM Forms utilisés pour traiter les documents.

![sample-transaction-report-author-1](assets/sample-transaction-report-author-1.png)

Une transaction reste dans la mémoire tampon pendant une période spécifiée (durée de la mémoire tampon de vidage + temps de réplication inverse). Par défaut, il faut environ 90 secondes pour que le nombre de transactions se reflète dans l&#39;état de la transaction.

Les actions telles que l’envoi d’un formulaire PDF, l’utilisation de l’interface utilisateur de l’agent pour prévisualisation une communication interactive ou l’utilisation de méthodes d’envoi de formulaire non standard ne sont pas comptabilisées comme des transactions. AEM Forms fournit une API pour enregistrer ces transactions. Appelez l’API depuis vos implémentations personnalisées pour enregistrer une transaction.

## Topologie prise en charge {#supported-topology}

Les rapports de transactions sont disponibles uniquement sur AEM Forms sur l’environnement OSGi. Il prend en charge les topologies auteur-publication, auteur-traitement-publication et de traitement uniquement. Par exemple, les topologies, voir [Topologies d’architecture et de déploiement pour AEM Forms](/help/forms/using/transaction-reports-overview.md).

Le nombre de transactions est répliqué inversement d’instances de publication à des instances d’auteur ou de traitement. Une topologie indicative auteur-publication s’affiche ci-dessous :

![simple-auteur-publication-topologie](assets/simple-author-publish-topology.png)

>[!NOTE]
>
>Les rapports de transactions AEM Forms ne prennent pas en charge les topologies qui contiennent uniquement des instances de publication.

### Directives pour l&#39;utilisation des rapports de transactions {#guidelines-for-using-transaction-reports}

* Désactiver les rapports de transactions sur toutes les instances d’auteur en tant que rapports sur les instances d’auteur inclut les transactions enregistrées lors de la création d’activités.
* Activez l&#39;option **Afficher les transactions de publication uniquement** sur l&#39;instance d&#39;auteur pour vue les transactions cumulatives de toutes les instances de publication. Vous pouvez également vue des rapports de transactions sur chaque instance de publication pour les transactions réelles sur cette instance de publication uniquement.
* N’utilisez pas les instances d’auteur pour exécuter des workflows et traiter des documents.
* Avant d’utiliser le rapports de transaction, si vous disposez d’une stratégie avec les serveurs de publication, assurez-vous que la réplication inversée est activée pour toutes les instances de publication.
* Les données de transaction sont répliquées de manière inversée d’une instance de publication à une instance d’auteur ou de traitement correspondante uniquement. L’auteur ou l’instance de traitement ne peut pas répliquer davantage les données vers une autre instance. Par exemple, si vous disposez de la topologie author-processing-publish, les données de transaction agrégées sont répliquées uniquement sur l’instance de traitement.

## Articles connexes {#related-articles}

* [Affichage et compréhension des rapports sur les transactions](/help/forms/using/viewing-and-understanding-transaction-reports.md)
* [API facturables des rapports de transaction](/help/forms/using/transaction-reports-billable-apis.md)
* [Enregistrer une transaction pour les implémentations personnalisées](/help/forms/using/record-transaction-custom-implementation.md)

