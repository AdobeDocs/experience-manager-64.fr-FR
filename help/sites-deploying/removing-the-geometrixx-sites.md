---
title: Suppression des sites de Geometrixx
seo-title: Removing the Geometrixx Sites
description: Découvrez comment supprimer l’exemple de contenu de Geometrixx.
seo-description: Learn how to remove the sample Geometrixx content.
uuid: 07d20837-3375-4e64-bb07-3e4d10452335
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
discoiquuid: 56761a36-ce21-46e1-856f-75a7e94acae9
exl-id: 495031fb-b559-4071-abc4-93d238ce136d
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 38%

---

# Suppression des sites de Geometrixx{#removing-the-geometrixx-sites}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

AEM s’accompagne d’un ensemble de sites web Geometrixx donnés à titre d’exemple. Vous pouvez supprimer cet exemple de contenu via la fonction **Gestionnaire de modules**.

Les packages individuels liés à geometrixx sont les suivants :

* `cq-geometrixx-outdoors-ugc-pkg-*<version>*.zip`
* `cq-geometrixx-pkg-*<version>*.zip`
* `cq-content-mac-*<version>*.zip`
* `cq-geometrixx-login-pkg-*<version>*.zip`
* `cq-geometrixx-users-pkg-*<version>*.zip`
* `cq-geometrixx-workflow-pkg-*<version>*.zip`
* `cq-geometrixx-outdoors-pkg-*<version>*.zip`
* `cq-geometrixx-commons-pkg-*<version>*.zip`
* `cq-geometrixx-media-pkg-*<version>*.zip`

Pour supprimer un module individuel, cliquez simplement sur **Désinstaller** sur ce paquet.

Il existe également un super package :

* `cq-geometrixx-all-pkg-5.6.12.zip`

Ce package comprend tous les packages individuels ci-dessus. Pour supprimer tout le contenu associé à geometrixx à la fois, cliquez sur **Désinstaller** sur ce paquet. Le super package passe alors dans le statut désinstallé et tous les packages qui le composent disparaissent de la vue du gestionnaire de packages.

Vous disposez à présent d’une instance AEM « vide », sans aucun site de démonstration.

>[!NOTE]
>
>Lors de la mise à niveau, les sites geometrixx sont automatiquement réinstallés. Si vous n’avez pas besoin de ces exemples, vous pourrez supprimer les sites web geometrixx après la mise à niveau.
