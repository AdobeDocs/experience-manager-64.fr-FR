---
title: Configurer les paramètres de verrouillage des comptes
seo-title: Configure account-locking settings
description: Utilisez l’option Activer le verrouillage de compte pour verrouiller les comptes utilisateur après un nombre spécifié d’échecs d’authentification consécutifs.
seo-description: Use the Enable Account Locking option to lock user accounts after a specified number of consecutive authentication failures.
uuid: 5ff3fb76-8b11-4818-9a75-40ed8e121da5
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/setting_up_and_managing_domains
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: d4409c6b-f4ef-499c-8daa-e93a163ff8ab
exl-id: e407c643-5753-447e-ad4e-deb7b9eb2b55
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '230'
ht-degree: 14%

---

# Configurer les paramètres de verrouillage des comptes {#configure-account-locking-settings}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Lorsque vous ajoutez un domaine, indiquez s’il faut activer le verrouillage des comptes. Lorsque l’option Activer le verrouillage de compte est sélectionnée, les comptes utilisateur sont verrouillés après un nombre spécifié d’échecs d’authentification consécutifs. Après une durée spécifiée, l’utilisateur peut à nouveau tenter de s’authentifier. Cette fonctionnalité empêche les utilisateurs d’essayer différentes combinaisons d’informations d’identification pour accéder au système.

Utilisez les paramètres de la page Gestion des domaines pour spécifier le nombre maximal d’échecs d’authentification et la durée pendant laquelle les comptes sont verrouillés. Ces paramètres s’appliquent à tous les domaines pour lesquels le verrouillage de compte est activé.

1. Dans la console dʼadministration, cliquez sur **[!UICONTROL Paramètres > Gestion des utilisateurs > Gestion des domaines]**.
1. Dans la zone Echecs d’authentification consécutifs maximum, saisissez le nombre de tentatives consécutives d’ouverture de session d’un utilisateur avant que son compte ne soit verrouillé. La valeur par défaut est 20.
1. Dans la zone Déverrouiller le compte après (minutes) , saisissez le nombre de minutes pendant lesquelles le compte utilisateur est verrouillé. Après le nombre de minutes spécifié, l’utilisateur peut tenter de se reconnecter. La valeur par défaut est 30.
1. Cliquez sur **[!UICONTROL Enregistrer]**.
