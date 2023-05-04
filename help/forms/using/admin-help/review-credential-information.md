---
title: Vérifier les informations d’identification de l’utilisateur
seo-title: Review credential use information
description: Découvrez comment consulter les informations d’utilisation des informations d’identification.
seo-description: Learn how to review credential use information.
uuid: 02af75f9-c235-470d-a98b-a2102aa31381
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_acrobat_reader_dc_extensions
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: cdf61cff-768b-49f7-9926-400bc96b0708
exl-id: abd62cca-edf0-4b44-94c3-7af3116b0c54
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 8%

---

# Vérifier les informations d’identification de l’utilisateur {#review-credential-use-information}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Les informations d’identification contiennent des informations décrivant son utilisation prévue, accessibles par le biais de l’application web pour utilisateurs finaux d’Acrobat Reader DC extensions. Vous pouvez utiliser ces informations pour déterminer le type d’informations d’identification installées (évaluation ou production) et ses dates de validité.

1. Ouvrez un navigateur web et saisissez l’URL suivante :

   http://localhost:*[port]*/ReaderExtensions (où *[port]* est le numéro de port de votre serveur d’applications)

1. Connectez-vous à l’aide du nom d’utilisateur et du mot de passe par défaut :

   Nom d’utilisateur : administrator

   Mot de passe : password

   >[!NOTE]
   >
   >Vous devez disposer de droits d’administrateur ou de super utilisateur pour vous connecter à l’aide du nom d’utilisateur et du mot de passe par défaut. Pour permettre à d’autres utilisateurs d’accéder aux extensions Acrobat Reader DC, créez les comptes d’utilisateurs dans User Management et attribuez aux utilisateurs le rôle Application Web des extensions Acrobat Reader DC.

1. Sélectionnez l’alias des informations d’identification dans la liste Sélectionner les informations d’identification et passez en revue les informations incluses dans les sections Date d’expiration et Avis d’utilisation prévue.

>[!NOTE]
>
>La date d’expiration des informations d’identification est également disponible sur la page Paramètres > Trust Store Management > Informations d’identification locales d’Administration Console, sous Date d’expiration.
