---
title: Définir les options de configuration XCI
seo-title: Specify XCI configuration options
description: Découvrez comment spécifier des options de configuration XCI.
seo-description: Learn how to specify XCI configuration options.
uuid: cf9e544d-63cd-4fad-8f89-bdb46eeef409
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_output
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: f38ebd69-8d1c-49b6-824f-4bf0ec8a8953
exl-id: 5156bb1c-8ad6-498c-aaf7-6474ffa8c83c
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '165'
ht-degree: 14%

---

# Définir les options de configuration XCI {#specify-xci-configuration-options}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Output vous permet de spécifier un fichier XCI personnalisé qu’il utilise pour le rendu. (Voir [Définition des emplacements de fichiers pour Output](/help/forms/using/admin-help/specify-file-locations-output.md#specify-file-locations-for-output).) Par défaut, Output remplace certaines des options spécifiées dans le fichier XCI, notamment :

* `config/present/xdp/packets`
* `config/present/pdf/creator`
* `config/present/pdf/producer`
* `config/present/pdf/compression/compressObjectStream`

Vous pouvez sélectionner des options qui annulent le remplacement des options répertoriées ci-dessus. Dans ce cas, Output utilise les valeurs spécifiées dans le fichier XCI personnalisé.

1. Dans Administration Console, cliquez sur Services > Output.
1. Cochez ou désélectionnez la case Utiliser les options XCI par défaut du système . Lorsque cette option est sélectionnée, Output utilise ses valeurs par défaut pour les paramètres paquets, créateur, producteur et compressObjectStream. Si cette option est désélectionnée, Output utilise les valeurs spécifiées dans le fichier XCI personnalisé.
1. Cliquez sur Enregistrer.
