---
title: Importer et exporter le fichier de configuration
seo-title: Importing and exporting the configuration file
description: Découvrez comment importer et exporter le fichier de configuration afin de modifier les préférences du serveur ou de configurer une autre instance de produit AEM forms.
seo-description: Learn how to import and export the configuration file in order to edit server preferences or configure another AEM forms product instance.
uuid: 32e8a709-2d7c-4740-9533-d53aa751bc58
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_user_management
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: c1636537-f7dc-48d8-a3f0-9052bcd28b62
exl-id: dbad776a-60fd-4fcc-ba2a-a2f379f5462c
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 6%

---

# Importer et exporter le fichier de configuration {#importing-and-exporting-the-configuration-file}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Utilisez la page Configuration manuelle pour télécharger une copie des paramètres de configuration au format XML. Les paramètres de ce fichier contrôlent toutes les préférences du serveur. Vous pouvez ensuite modifier le fichier et le charger à nouveau sur le serveur. Vous pouvez également utiliser ce fichier pour configurer une autre instance AEM produit forms.

Pour éviter tout risque de sécurité, la valeur du mot de passe de liaison du serveur d’annuaire n’est pas incluse dans un fichier de configuration exporté. Mettez à jour le mot de passe dans le fichier XML avant d’importer le fichier dans un nouveau système.

>[!NOTE]
>
>L’importation du fichier de configuration reconfigure AEM formulaires en fonction des informations contenues dans le fichier. Seul un administrateur système ou un consultant en services professionnels qui connaît le produit AEM forms et le code XML doit envisager de modifier le fichier de configuration. Il peut être nécessaire de modifier le fichier de configuration, par exemple, pour reconfigurer un paramètre corrompu.

**Exportation des informations de configuration**

1. Dans Administration Console, cliquez sur Paramètres > User Management > Configuration > Importer et exporter des fichiers de configuration.
1. Cliquez sur Exporter. Si vous utilisez Microsoft Internet Explorer, vous êtes invité à spécifier l’emplacement d’enregistrement du fichier. Si vous utilisez Firefox, le fichier est enregistré sur votre bureau.

**Importation des informations de configuration**

1. Dans Administration Console, cliquez sur Paramètres > User Management > Configuration > Importer et exporter des fichiers de configuration.
1. Cliquez sur Parcourir pour rechercher le fichier de configuration, sur Importer, puis sur OK.
