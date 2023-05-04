---
title: Nombre maximal de curseurs ouverts dans une base de données Oracle
seo-title: Oracle database maximum open cursors threshold
description: Découvrez comment configurer une valeur maximale pour les curseurs ouverts dans Oracle.
seo-description: Learn about configuring a maximum value for open cursors in Oracle.
uuid: c1d20997-f853-4772-b1c6-8cea73221d0a
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_aem_forms_database
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: d3565776-1b7d-498c-9840-b17f80170d9b
exl-id: ad14ff27-964f-481f-a8ef-052d9cfb7734
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '120'
ht-degree: 25%

---

# Nombre maximal de curseurs ouverts dans une base de données Oracle {#oracle-database-maximum-open-cursors-threshold}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Pour configurer une valeur maximale pour les curseurs ouverts dans Oracle, vous devrez peut-être ajuster cette valeur à un nombre approprié pour votre application. Il est évident que sous une charge modérée, le nombre moyen de curseurs ouverts était de 2 700. Il est recommandé de commencer par une limite supérieure de 3 000. Pour plus d’informations, rendez-vous sur [https://www.orafaq.com/node/758](https://www.orafaq.com/node/758).
