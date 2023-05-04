---
title: Configurer des points d’entrée Remoting
seo-title: Configuring Remoting endpoints
description: Découvrez comment configurer des points de fin distants.
seo-description: Learn how to configure remoting endpoints.
uuid: 4d4f9274-dcae-4b9f-975a-575376c2f89c
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_endpoints
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: aab9d622-d76b-4100-9ca6-e5b86f543381
exl-id: d8e31f99-0558-4634-ae35-f4a09f34ad6d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '156'
ht-degree: 37%

---

# Configurer des points d’entrée Remoting {#configuring-remoting-endpoints}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Un point de fin Remoting permet à une application créée avec Flex d’appeler le service en utilisant (obsolète pour les AEM forms) AEM forms Remoting. Un point de fin Remoting est automatiquement créé pour chaque service activé. Une destination Flex qui porte le même nom que le point de terminaison est créée et les clients Flex peuvent créer des objets distants qui pointent vers cette destination pour appeler des opérations sur le service approprié.

## Paramètres des points d’entrée Remoting {#remoting-endpoint-settings}

**Méthode d’authentification du client Flex :** indique le type de réponse que le serveur renvoie au client lorsque la sécurité du service appelé est activée, l’opération appelée ne prend pas en charge les appels anonymes et le client parvient à se connecter sans informations d’identification ou avec des informations d’identification non valides.
