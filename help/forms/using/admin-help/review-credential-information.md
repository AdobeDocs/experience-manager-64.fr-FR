---
title: Vérification de l’utilisation des informations d’identification
seo-title: Review credential use information
description: Découvrez comment vérifier les informations d’identification de l’utilisateur.
seo-description: Learn how to review credential use information.
uuid: 02af75f9-c235-470d-a98b-a2102aa31381
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_acrobat_reader_dc_extensions
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: cdf61cff-768b-49f7-9926-400bc96b0708
exl-id: abd62cca-edf0-4b44-94c3-7af3116b0c54
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 93%

---

# Vérification de l’utilisation des informations d’identification {#review-credential-use-information}

Les informations d’identification contiennent des données décrivant leur utilisation prévue grâce à l’application Web d’utilisateur final des extensions d’Acrobat Reader DC. Vous pouvez utiliser ces données pour déterminer le type d’informations d’identification installées (évaluation ou production), de même que leurs dates de validité.

1. Ouvrez un navigateur Web, puis saisissez l’URL suivante :

   http://localhost:*[port]*/ReaderExtensions (où *[port]* est le numéro de port de votre serveur d’applications)

1. Connectez-vous à l’aide du nom d’utilisateur et du mot de passe par défaut :

   Nom d’utilisateur : administrator

   Mot de passe : password

   >[!NOTE]
   >
   >pour pouvoir vous connecter au moyen du nom d’utilisateur et du mot de passe par défaut, vous devez disposer de droits d’administrateur ou de superutilisateur. Pour permettre à d’autres utilisateurs d’accéder aux extensions d’Acrobat Reader DC, vous devez créer les comptes d’utilisateurs dans Gestion des utilisateurs et leur octroyer le rôle Application Web des extensions d’Acrobat Reader DC.

1. Sélectionnez l’alias d’informations d’identification dans la liste Sélectionner informations d’identification, puis vérifiez les données des sections Date d’expiration et Avis d’utilisation prévue.

>[!NOTE]
>
>La date d’expiration des informations d’identification est également disponible à la page Paramètres > Trust Store Management > Informations d’identification locales dans Administration Console, sous Date d’expiration.
