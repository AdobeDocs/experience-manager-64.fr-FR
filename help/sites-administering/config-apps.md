---
title: Configuration d’Applications AEM
seo-title: Configuring for AEM Apps
description: Apprenez à configurer Applications AEM.
seo-description: Learn how to configure AEM Apps.
uuid: ab9acd93-da7f-4bb7-8d26-224044899068
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
discoiquuid: 34f24837-f5e2-41f0-a359-fdb695e1b8f2
exl-id: 593a588c-02f1-4b48-ac57-9348d6652bcc
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '141'
ht-degree: 58%

---

# Configuration d’Applications AEM{#configuring-for-aem-apps}

Adobe Experience Manager Apps offre la possibilité de mettre à jour le contenu de votre application par les airs (OTA, Over The Air). Le contenu mis à jour est stocké sur l’instance de publication. Pour permettre à l’application sur votre appareil de se connecter à l’instance de publication et de rechercher les mises à jour, l’instance de publication doit être configurée pour autoriser un en-tête de référent vide.

## Configuration d’un en-tête de référent vide {#configuring-empty-referrer-header}

Pour configurer le service de filtrage de référent :

* Ouvrez la console Apache Felix (**Configurations**) à :
* https://&lt;server>:&lt;port_number>/system/console/configMgr
* Connectez-vous en tant qu’administrateur.
* Dans le **Configurations** , sélectionnez : *Filtre de référent Apache Sling*
* Cochez le champ Autoriser vide pour autoriser les en-têtes de référent vides/manquants.
* Cliquez sur **Enregistrer** pour enregistrer vos modifications.

![chlimage_1-58](assets/chlimage_1-58.png)

Voir [Paramètres de configuration OSGI](/help/sites-deploying/osgi-configuration-settings.md) et [Liste de contrôle de sécurité - Problèmes de falsification de requête intersites](/help/sites-administering/security-checklist.md#protect-against-cross-site-request-forgery) pour plus de détails.
