---
title: Principes de base de la configuration des formulaires
seo-title: Basics of configuring forms
description: Découvrez les différents services de formulaires qui vous aident à créer des applications de capture de données interactives.
seo-description: Learn about the various forms services that help you create interactive data capture applications.
uuid: f495c170-2d17-45b0-b09d-22cce101131e
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: e87c7379-28ed-4fda-aef1-970d2b54f30d
exl-id: 616cd550-c3bd-4daf-887d-0470f1b08389
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 9%

---

# Principes de base de la configuration des formulaires {#basics-of-configuring-forms}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Le service Forms vous permet de créer des applications clientes interactives de capture de données qui valident, traitent, transforment et diffusent des formulaires généralement créés dans Designer. Les auteurs de formulaires développent une conception de formulaire unique que le service Forms effectue dans différents formats :

* comme PDF dans Adobe Reader ou dans un navigateur
* comme HTML dans divers environnements de navigateur, y compris le rendu conforme XHTML 1.0
* comme guides de formulaire dans divers environnements de navigateur qui prennent en charge le Flash Player des Adobes.

Pour plus d’informations sur le service Forms, voir [Référence des services](https://help.adobe.com/fr_FR/livecycle/11.0/Services/index.html).

La page Forms d’Administration Console vous permet de configurer le comportement du service Forms. Ces paramètres s’appliquent à tous les appels du service. Tous les paramètres envoyés par le biais du SDK d’AEM forms remplacent les paramètres définis dans la console d’administration ; cependant, elles n’affectent que cet appel particulier.

Après avoir modifié les paramètres Forms dans Administration Console, cliquez sur Enregistrer. Vous n’avez pas besoin de redémarrer le serveur pour que les modifications soient prises en compte. Cependant, vous devrez peut-être arrêter et redémarrer le service Forms lors de la configuration des paramètres du mode de mise en cache. (Voir [Démarrage et arrêt des services](/help/forms/using/admin-help/starting-stopping-services.md#starting-and-stopping-services).)
