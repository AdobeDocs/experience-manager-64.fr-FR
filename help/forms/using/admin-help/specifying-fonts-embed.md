---
title: Spécifier les polices à incorporer
seo-title: Specifying fonts to embed
description: Découvrez comment spécifier les polices à incorporer.
seo-description: Learn how to specify fonts to embed.
uuid: 97de6f98-ed3b-4a93-854a-193a967b4672
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 4c83694c-b00f-40be-9ac4-f5785cd60741
exl-id: 0bde7192-9d21-40b4-9164-314c9a30153b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '286'
ht-degree: 24%

---

# Spécifier les polices à incorporer {#specifying-fonts-to-embed}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Vous pouvez spécifier les polices qui sont toujours ou jamais incorporées avec les formulaires générés par le service Forms. L’incorporation de polices augmente la taille de fichier des formulaires. Incorporez des polices inhabituelles que les utilisateurs ont rarement sur leurs systèmes. N’incorporez pas les polices courantes généralement installées.

>[!NOTE]
>
>Si vous avez spécifié un fichier XCI personnalisé pour Forms, l’option d’incorporation de polices dans le fichier XCI remplace ces paramètres. (Voir [Configuration des emplacements pour Forms](/help/forms/using/admin-help/configuring-locations-forms.md#configuring-locations-for-forms).)

1. Dans la console d’administration, cliquez sur **[!UICONTROL Services > Forms]**.
1. Sous **[!UICONTROL Paramètres d’incorporation des polices]**, dans le champ **[!UICONTROL Toujours incorporer les polices]**, saisissez les noms des polices à incorporer aux formulaires (en les séparant par des virgules). Les polices que vous spécifiez ne sont incorporées dans le formulaire généré que si elles sont utilisées dans le formulaire. Ce paramètre est ignoré si l’option d’incorporation des polices a été activée dans le fichier XCI transmis au service, car dans ce cas, toutes les polices utilisées dans le PDF sont toujours incorporées.
1. Dans le champ **[!UICONTROL Ne jamais incorporer les polices]**, saisissez les noms des polices à ne pas incorporer avec les formulaires (en les séparant par des virgules). Les polices que vous spécifiez ne sont pas incorporées dans le PDF, même si elles sont utilisées dans le PDF généré. Ce paramètre est ignoré si l’option d’incorporation des polices a été désactivée dans le fichier XCI transmis au service, car dans ce cas, aucune des polices utilisées dans le PDF n’est incorporée.
1. Cliquez sur **[!UICONTROL Enregistrer]**.
