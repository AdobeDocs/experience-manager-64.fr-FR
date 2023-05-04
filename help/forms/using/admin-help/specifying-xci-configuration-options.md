---
title: Définir les options de configuration XCI
seo-title: Specifying XCI configuration options
description: Découvrez comment spécifier des options de configuration XCI.
seo-description: Learn how to specify XCI configuration options.
uuid: 5d3c10c1-4a93-4336-b311-20faaf835b9f
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 162c9fda-f4d4-4ad5-a9ab-7554828e821c
exl-id: 7a13b13f-3eee-4fc0-8957-bd42f43119e9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 14%

---

# Définir les options de configuration XCI {#specifying-xci-configuration-options}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Forms vous permet de spécifier un fichier XCI personnalisé à utiliser pour le rendu. (Voir [Configuration des emplacements pour Forms](/help/forms/using/admin-help/configuring-locations-forms.md#configuring-locations-for-forms).) Par défaut, Forms remplace certaines des options spécifiées dans le fichier XCI, notamment :

* `config/present/xdp/packets`
* `config/present/pdf/creator`
* `config/present/pdf/producer`
* `config/present/pdf/compression/compressObjectStream`

Vous pouvez sélectionner des options qui annulent le remplacement des options répertoriées ci-dessus. Dans ce cas, Forms utilisera les valeurs spécifiées dans le fichier XCI personnalisé.

1. Dans Administration Console, cliquez sur Services > Forms.
1. Cochez ou désélectionnez la case Utiliser les options XCI par défaut du système . Lorsque cette option est sélectionnée, Forms utilise ses valeurs par défaut pour les paramètres paquets, créateur, producteur et compressObjectStream . Si cette option est désélectionnée, Forms utilise les valeurs spécifiées dans le fichier XCI personnalisé.
1. Cliquez sur Enregistrer.
