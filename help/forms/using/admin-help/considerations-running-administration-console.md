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
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '130'
ht-degree: 100%

---

# Remarques concernant l’exécution d’Administration Console {#considerations-when-running-administrationconsole}

Il existe plusieurs éléments à prendre en compte lors de l’exécution d’Administration Console :

* Si vous accédez à la console d’administration en utilisant l’URL `https://*[hostname]*:*[port]*/adminui`, le nom d’hôte spécifié ne peut pas contenir de caractères de soulignement. Dans le cas contraire, les liens vers certaines zones d’Administration Console risquent de ne pas fonctionner correctement.
* Si vous exécutez Administration Console dans Windows Explorer sur un système d’exploitation japonais, il se peut que vous rencontriez les problèmes suivants :

   * Un clic sur un lien vous renvoie à la page d’ouverture de session au lieu du lien prévu.
   * Un clic sur un lien entraîne l’affichage d’une erreur d’autorisation.

   Il est conseillé d’exécuter Administration Console depuis un autre navigateur, tel que Mozilla Firefox, pour éviter que des liens n’échouent.

* N’utilisez pas de barres obliques inverses (\) lorsque vous exécutez des recherches dans Administration Console.
