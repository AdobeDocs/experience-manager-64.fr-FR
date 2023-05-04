---
title: Remarques concernant l’exécution d’Administration Console
seo-title: Considerations when running AdministrationConsole
description: Ce document répertorie quelques points à prendre en compte lors de l’exécution d’Administration Console.
seo-description: This document lists a few points to consider when running Administration Console.
uuid: e260f187-4728-44f3-a5c1-7388ff3965c4
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_application_server
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 525c4afc-e109-4546-b78c-1efee63edc43
exl-id: 991418fd-5ff8-491e-834e-2324e029e499
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 24%

---

# Remarques concernant l’exécution d’Administration Console {#considerations-when-running-administrationconsole}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Voici quelques éléments à prendre en compte lors de l’exécution d’Administration Console :

* Si vous accédez à la console d’administration en utilisant l’URL `https://*[hostname]*:*[port]*/adminui`, le nom d’hôte spécifié ne peut pas contenir de caractères de soulignement. Dans le cas contraire, les liens vers certaines zones d’Administration Console risquent de ne pas fonctionner correctement.
* Si vous exécutez Administration Console dans Windows Explorer sur un système d’exploitation japonais, vous pouvez rencontrer les problèmes suivants :

   * Cliquer sur un lien vous renvoie à la page de connexion au lieu du lien attendu.
   * Cliquez sur un lien pour afficher une erreur d’autorisation.

   Il est recommandé d’exécuter Administration Console à partir d’un autre navigateur, tel que Mozilla Firefox, pour vous assurer qu’aucun lien n’échouera.

* N’utilisez pas de barre oblique inverse () lorsque vous effectuez des recherches dans Administration Console.
