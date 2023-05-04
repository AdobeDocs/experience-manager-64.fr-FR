---
title: Configuration des informations d’identification à utiliser avec les extensions d’Acrobat Reader DC
seo-title: Configuring credentials for use with Acrobat Reader DC extensions
description: Découvrez comment configurer les informations d’identification à utiliser avec les extensions Acrobat Reader DC.
seo-description: Learn how to configure credentials for use with Acrobat Reader DC extensions.
uuid: 9210e6c9-6f5c-402d-b355-b104cdffd5eb
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_acrobat_reader_dc_extensions
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 5bb32fb1-4b6e-412f-aa16-f60db9dcaba1
exl-id: 40c2e205-0115-4ebe-ab24-66c8ee0663fa
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '591'
ht-degree: 20%

---

# Configuration des informations d’identification à utiliser avec les extensions d’Acrobat Reader DC{#configuring-credentials-for-use-with-acrobat-reader-dc-extensions}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Pour appliquer des droits d’utilisation aux documents PDF, configurez AEM forms avec des informations d’identification valides pour les extensions d’Acrobat Reader DC. Des informations d’identification peuvent avoir été configurées lors de l’installation d’AEM forms. Si vous n’avez pas configuré vos informations d’identification des extensions Acrobat Reader DC lors de l’exécution de Configuration Manager ou si vous devez importer des informations d’identification nouvelles ou de remplacement, vous pouvez le faire à l’aide des pages Trust Store Management.

Si vous utilisez des informations d’identification d’évaluation, remplacez-les par des informations d’identification de production lors du passage à votre environnement de production. Pour mettre à jour des informations d’identification d’évaluation ou expirées, commencez par supprimer les anciennes informations d’identification des extensions d’Acrobat Reader DC.

Pour plus d’informations sur l’obtention d’informations d’identification, voir [Préparation à l’installation d’AEM forms (serveur unique)](https://www.adobe.com/go/learn_aemforms_prepareInstallsingle_63_fr).

Le Trust Store peut contenir plusieurs informations d’identification d’extensions Acrobat Reader DC. Vous devez désigner l’une de ces informations d’identification comme informations d’identification Reader Extensions par défaut. Les informations d’identification par défaut sont utilisées lorsqu’un utilisateur de Workbench ne parvient pas à déterminer les informations d’identification à utiliser lors de la création du processus. Ces règles s’appliquent aux informations d’identification par défaut :

* Si vous importez des informations d’identification des extensions Acrobat Reader DC et que le Trust Store ne contient aucune autre information d’identification des extensions Acrobat Reader DC, cette valeur est définie comme valeur par défaut.
* Si vous importez des informations d’identification des extensions Acrobat Reader DC avec l’option Par défaut sélectionnée, le type par défaut est supprimé des informations d’identification par défaut existantes. Le jeu d’informations d’identification importé devient la valeur par défaut.
* Vous ne pouvez pas supprimer d’informations d’identification des extensions Acrobat Reader DC par défaut. Pour supprimer les informations d’identification par défaut, définissez d’abord une autre information d’identification comme valeur par défaut. Une exception à cette règle est que s’il n’existe qu’un seul identifiant, vous pouvez le supprimer, même s’il s’agit de la valeur par défaut.
* Vous ne pouvez pas mettre à jour un jeu d’informations d’identification des extensions d’Acrobat Reader DC par défaut.

>[!NOTE]
>
>Vous pouvez également importer et supprimer des informations d’identification par programmation. (Voir [Programmation avec les AEM forms](https://www.adobe.com/go/learn_aemforms_programming_63_fr).)

## Importation des informations d’identification des extensions Acrobat Reader DC {#import-a-acrobat-reader-dc-extensions-credential}

1. Dans Administration Console, cliquez sur Paramètres > Trust Store Management > Informations d’identification locales.
1. Cliquez sur Importer, puis, sous Type de Trust Store, sélectionnez Informations d’identification des extensions Acrobat Reader DC.
1. (Facultatif) Pour indiquer que ces informations d’identification sont les informations d’identification par défaut à utiliser avec les extensions Acrobat Reader DC, sélectionnez Par défaut.
1. Dans la zone Alias, saisissez un identifiant pour les informations d’identification. Cet identifiant est utilisé comme nom d’affichage des informations d’identification dans les extensions Acrobat Reader DC. Cet alias est également utilisé pour accéder aux informations d’identification par programmation à l’aide du SDK d’AEM forms.

   >[!NOTE]
   >
   >Le nom d’alias est automatiquement converti en majuscules à des fins d’affichage. Le nom d’alias n’est pas sensible à la casse lorsque vous y faites référence dans un processus.

1. Cliquez sur Choisir un fichier pour accéder aux informations d’identification, saisissez le mot de passe correspondant, puis cliquez sur OK.

   Si le message d’erreur &quot;Échec de l’importation des informations d’identification en raison d’un format de fichier incorrect ou d’un mot de passe incorrect&quot; s’affiche, vérifiez que le mot de passe est valide.

## Suppression d’informations d’identification des extensions Acrobat Reader DC {#remove-a-acrobat-reader-dc-extensions-credential}

1. Dans Administration Console, cliquez sur Paramètres > Trust Store Management > Informations d’identification locales.
1. Sélectionnez les informations d’identification, puis cliquez sur Supprimer.

## Remplacement des informations d’identification des extensions Acrobat Reader DC {#replace-a-acrobat-reader-dc-extensions-credential}

1. Dans Administration Console, cliquez sur Paramètres > Trust Store Management > Informations d’identification locales.
1. Notez l’alias des informations d’identification existantes, sélectionnez-le, puis cliquez sur Supprimer.
1. Importez les nouvelles informations d’identification en utilisant exactement le même nom d’alias.
