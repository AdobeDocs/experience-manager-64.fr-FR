---
title: Configuration des applications AEM
seo-title: Configuring for AEM Apps
description: Découvrez comment configurer AEM applications.
seo-description: Learn how to configure AEM Apps.
uuid: ab9acd93-da7f-4bb7-8d26-224044899068
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
discoiquuid: 34f24837-f5e2-41f0-a359-fdb695e1b8f2
exl-id: 593a588c-02f1-4b48-ac57-9348d6652bcc
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '177'
ht-degree: 61%

---

# Configuration des applications AEM{#configuring-for-aem-apps}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Adobe Experience Manager Apps offre la possibilité de mettre à jour le contenu de votre application par les airs (OTA, Over The Air). Le contenu mis à jour est stocké sur l’instance de publication. Pour permettre à l’application sur votre appareil de se connecter à l’instance de publication et de rechercher les mises à jour, l’instance de publication doit être configurée de manière à autoriser un en-tête de référent vide.

## Configuration de l’en-tête de référent vide {#configuring-empty-referrer-header}

Pour configurer le service de filtrage de référent, procédez comme suit :

* Ouvrez la console Apache Felix (**Configurations**) dans :
* https://&lt;server>:&lt;port_number>/system/console/configMgr
* Connectez-vous en tant qu’administrateur.
* Dans le menu **Configurations**, sélectionnez : *Apache Sling Referrer Filter*
* Cochez le champ Autoriser vide pour autoriser les en-têtes vides/manquants.
* Cliquez sur **Enregistrer** pour enregistrer vos modifications.

![chlimage_1-58](assets/chlimage_1-58.png)

Pour plus de détails, consultez les sections [Paramètres de configuration OSGI](/help/sites-deploying/osgi-configuration-settings.md) et [Liste de contrôle de sécurité - Problèmes de Cross-Site Request Forgery](/help/sites-administering/security-checklist.md#protect-against-cross-site-request-forgery).
