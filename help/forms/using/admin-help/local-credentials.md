---
title: Gérer les informations d’identification locales
seo-title: Managing local credentials
description: Découvrez comment gérer les informations d’identification locales.
seo-description: Learn how to manage local credentials.
uuid: 3c4358e0-aaff-4e94-a6b2-04b463fca260
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_certificates_and_credentials
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 598a9a03-3773-4620-8867-1f754d8ca031
exl-id: f8c6f4e3-4c2d-4843-8f29-6d3297e57c89
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '537'
ht-degree: 21%

---

# Gérer les informations d’identification locales {#managing-local-credentials}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Les informations d’identification locales sont des informations d’identification de clé privée hébergées dans Trust Store Management. A *informations d’identification locales* identifie l’emplacement de stockage des informations d’identification DES d’un utilisateur. Trust Store Management vous permet d’importer et de gérer vos informations d’identification locales à l’aide, par exemple, de fichiers PFX existants, afin que vous puissiez importer, modifier et supprimer des informations d’identification locales.

AEM forms prend en charge les informations d’identification RSA et DSA jusqu’à 4 096 bits au format PKCS12 standard (fichiers .pfx et .p12).

Vous pouvez importer et exporter un nombre indéfini d’informations d’identification. Si vous souhaitez remplacer des informations d’identification expirées par le même alias, supprimez-les, puis importez les nouvelles informations d’identification avec le même alias.

Pour obtenir des informations et des instructions relatives aux extensions Acrobat Reader DC, voir [Configuration des informations d’identification à utiliser avec les extensions Acrobat Reader DC](/help/forms/using/admin-help/configuring-credentials-acrobat-reader-dc.md#configuring-credentials-for-use-with-acrobat-reader-dc-extensions).

## Importation d’informations d’identification {#import-a-credential}

1. Dans Administration Console, cliquez sur Paramètres > Trust Store Management > Informations d’identification locales.
1. Cliquez sur Importer. Sous Type de Trust Store, sélectionnez l’une des options suivantes :

   * **Informations d’identification de signature de document :** informations d’identification utilisées pour émettre une signature numérique sur un document.
   * **Informations d’identification des extensions d’Acrobat Reader DC :** certificat numérique spécifique des extensions d’Acrobat Reader DC qui permet l’activation de droits Adobe Reader dans les documents PDF générés.
   * **Par défaut :** indique qu’il s’agit des informations d’identification par défaut à utiliser avec les extensions d’Acrobat Reader DC.

   Pour plus d’informations sur l’obtention d’informations d’identification, voir [Préparation à l’installation d’AEM forms](https://www.adobe.com/go/learn_aemforms_prepareInstallsingle_63_fr).

1. Dans la zone Alias, saisissez un identifiant pour les informations d’identification. Cet identifiant est utilisé comme nom d’affichage des informations d’identification dans les extensions Acrobat Reader DC et le service Signature. Cet alias est également utilisé pour accéder aux informations d’identification par programmation à l’aide du SDK d’AEM forms.

   >[!NOTE]
   >
   >Le nom d’alias est automatiquement converti en majuscules à des fins d’affichage. Le nom d’alias n’est pas sensible à la casse lorsque vous y faites référence dans un processus.

1. Cliquez sur Parcourir pour localiser les informations d’identification, saisissez le mot de passe de ces informations, puis cliquez sur OK.

   Si le message d’erreur &quot;Échec de l’importation des informations d’identification en raison d’un format de fichier incorrect ou d’un mot de passe incorrect&quot; s’affiche, vérifiez que le mot de passe est valide.

## Exportation d’informations d’identification {#export-a-credential}

Les informations d’identification sont exportées sous la forme de fichiers P12 au format PKCS#12.

1. Dans Administration Console, cliquez sur Paramètres > Trust Store Management > Informations d’identification locales.
1. Cliquez sur le nom d’alias des informations d’identification à exporter, puis sur Exporter.
1. Dans la zone Mot de passe, saisissez le mot de passe. Ce mot de passe est nouveau et est utilisé pour chiffrer les informations d’identification exportées.
1. Cliquez sur Exporter, suivez les instructions pour exporter les informations d’identification, puis cliquez sur OK.

## Modification de l’alias ou du type de Trust Store d’une information d’identification {#edit-a-credential-s-alias-or-trust-store-type}

Une fois les informations d’identification importées, vous pouvez modifier leur nom d’alias et leur type de Trust Store.

1. Dans Administration Console, cliquez sur Paramètres > Trust Store Management > Informations d’identification locales.
1. Cliquez sur le nom d’alias des informations d’identification à modifier.
1. Cliquez sur Mettre à jour les informations d’identification.
1. Modifiez le nom d’alias et le type de Trust Store selon les besoins, puis cliquez sur OK.

## Suppression d’informations d’identification {#delete-a-credential}

1. Dans Administration Console, cliquez sur Paramètres > Trust Store Management > Informations d’identification locales.
1. Cochez les cases correspondant aux informations d’identification à supprimer.
1. Cliquez sur Supprimer, puis sur OK.
