---
title: Spécifier les polices à incorporer
seo-title: Specify fonts to embed
description: Découvrez comment spécifier les polices à incorporer.
seo-description: Learn how to specify fonts to embed.
uuid: 02da5c00-0467-4633-a076-c36725cbfbad
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_output
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 180f0448-d507-4b6d-bb8a-d12a434e1250
exl-id: e24f4123-bed3-4096-b3fb-22deb1c1e9b9
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 24%

---

# Spécifier les polices à incorporer{#specify-fonts-to-embed}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Vous pouvez spécifier les polices qui sont toujours ou jamais incorporées avec les formulaires utilisés par Output. L’incorporation de polices augmente la taille de fichier des formulaires. Incorporez les polices inhabituelles que les utilisateurs ne sont pas susceptibles de posséder sur leurs systèmes et n’incorporez pas les polices courantes qu’ils auront installées.

>[!NOTE]
>
>Si vous avez spécifié un fichier XCI personnalisé pour Output, l’option d’incorporation de polices dans le fichier XCI remplace ces paramètres. (Voir [Définition des emplacements de fichiers pour Output](/help/forms/using/admin-help/specify-file-locations-output.md#specify-file-locations-for-output).)

1. Dans Administration Console, cliquez sur Services > Output.
1. Sous Paramètres d’incorporation des polices, dans le champ Toujours incorporer les polices, saisissez les noms des polices à incorporer aux formulaires (en les séparant par des virgules). Les polices que vous spécifiez ne sont incorporées dans le formulaire généré que si elles sont utilisées dans le formulaire. Ce paramètre est ignoré si l’option d’incorporation des polices a été activée dans le fichier XCI transmis au service. Dans ce cas, toutes les polices utilisées dans le PDF sont toujours incorporées.
1. Dans le champ Ne jamais incorporer les polices, saisissez les noms des polices à ne pas incorporer avec les formulaires (en les séparant par des virgules). Les polices que vous spécifiez ne sont pas incorporées dans le PDF, même si elles sont utilisées dans le PDF généré. Ce paramètre est ignoré si l’option d’incorporation des polices a été désactivée dans le fichier XCI transmis au service. Dans ce cas, aucune des polices utilisées dans le PDF n’est incorporée.
1. Cliquez sur Enregistrer.
