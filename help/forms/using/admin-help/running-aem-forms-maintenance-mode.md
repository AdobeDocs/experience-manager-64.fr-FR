---
title: Exécuter AEM Forms en mode de maintenance
seo-title: Running AEM forms in maintenance mode
description: Le mode de maintenance est utile lorsque vous réalisez des tâches telles que l’application d’un correctif à un DSC, la mise à niveau d’AEM forms ou l’application d’un pack de services. En savoir plus sur l’exécution d’AEM forms en mode de maintenance.
seo-description: Maintenance mode is useful when performing tasks such as patching a DSC, upgrading AEM forms, or applying a service pack. Learn more about running AEM forms in maintenance mode.
uuid: 9aa3be20-f17e-4384-b4ce-daaee2898c96
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_aem_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 94047c12-ba3d-457a-954f-e035c7cc3ecd
exl-id: 2f56bbc7-5e23-4c84-ac0a-03f0b01150b3
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '310'
ht-degree: 22%

---

# Exécuter AEM Forms en mode de maintenance {#running-aem-forms-in-maintenance-mode}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Le mode de maintenance est utile lorsque vous réalisez des tâches telles que l’application d’un correctif à un DSC, la mise à niveau d’AEM forms ou l’application d’un Service Pack.

Évitez d’appeler des processus lorsque le serveur est en mode de maintenance. Voici ce qui se passe si un processus est appelé alors que le serveur est en mode de maintenance :

* Si le processus est de longue durée, il est ajouté à la base de données de tâches, mais n’est pas démarré. Lorsque vous quittez le mode de maintenance, AEM forms traite les tâches de longue durée dans sa file d’attente, même si le serveur a été redémarré en mode de maintenance.
* Si le processus est de courte durée, il est traité immédiatement.

**Activation des AEM forms en mode de maintenance**

1. Dans un navigateur web, saisissez :

   `https://`*[hostname ]*`:`*[port]* `/dsc/servlet/DSCStartupServlet?maintenanceMode=pause&user=`*[nom d’utilisateur administrateur ]*`&password=`*[password]*

   Un message &quot;maintenant en pause&quot; s’affiche dans la fenêtre du navigateur.

   >[!NOTE]
   >
   >Si vous arrêtez le serveur alors qu’il est en mode de maintenance, il sera toujours en mode de maintenance au redémarrage. Vous devez désactiver le mode de maintenance lorsque vous avez terminé vos tâches de maintenance.

**Vérifiez si AEM forms s’exécute en mode de maintenance**

1. Dans un navigateur web, saisissez :

   `https://`*[hostname]:[port ]*`/dsc/servlet/DSCStartupServlet?maintenanceMode=isPaused&user=`*[nom d’utilisateur administrateur]* `&password=`*[password ]*

   L’état s’affiche dans la fenêtre du navigateur. L’état &quot;true&quot; indique que le serveur s’exécute en mode de maintenance et &quot;false&quot; que le serveur n’est pas en mode de maintenance.

**Désactivation du mode de maintenance**

1. Dans un navigateur web, saisissez :

   `https://`*[hostname]:[port ]*`/dsc/servlet/DSCStartupServlet?maintenanceMode=resume&user=`*[nom d’utilisateur administrateur]* `&password=`*[password ]*

   Un message d’exécution s’affiche dans la fenêtre du navigateur.
