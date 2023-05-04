---
title: Envoi sécurisé de gros volumes d’information
seo-title: High-volume secure information delivery
description: Document Security prend en charge l’association de licences aux utilisateurs, plutôt qu’aux documents dans les environnements de production de masse.
seo-description: Document security supports the association of licenses to users, rather than to the documents in mass production environments.
uuid: 9747d283-506c-434e-9850-e50b95290cc8
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_document_security
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: b76d7d93-23a5-4c08-81f5-a56267b1556a
feature: Document Security
exl-id: 78fc7c4a-a634-4628-927a-c9622bdc13fc
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 8%

---

# Envoi sécurisé de gros volumes d’information {#high-volume-secure-information-delivery}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Dans un environnement de production de masse, comme celui qui génère des factures mensuelles sécurisées pour une société de télécommunications, la création de licences spécifiques à chaque document peut devenir un processus gourmand en ressources. Dans ce cas, Document Security prend en charge l’association de licences aux utilisateurs plutôt qu’aux documents. La licence générée pour un utilisateur est utilisée pour tous les documents protégés pour cet utilisateur.

L’un des avantages de cette approche est que la taille de la base de données Document Security ne s’accroît pas de manière linéaire avec les documents, mais avec le nombre d’utilisateurs. En outre, puisque vous n’avez besoin de créer la licence qu’une seule fois pour un utilisateur, la protection ultérieure des documents par le biais de ces stratégies devient plus rapide. Des fonctionnalités telles que l’accès hors ligne, l’expiration du document et la révocation sont prises en charge pour tous ces documents.

Document Security prend également en charge les stratégies abstraites. Les stratégies abstraites sont des modèles de stratégie qui contiennent tous les attributs de stratégie, tels que les paramètres de Document Security et les droits d’utilisation, mais ne contiennent pas de liste d’entités. Les administrateurs peuvent créer un nombre illimité de stratégies à partir de la stratégie abstraite avec différentes entités qui doivent avoir accès aux documents. Les modifications apportées à la stratégie abstraite n’affectent pas les stratégies réelles générées à partir des stratégies abstraites.

Dans le cas de la génération mensuelle de factures pour une société de télécommunications, vous créez une stratégie abstraite, des utilisateurs, puis générez des licences uniques pour chaque utilisateur. Les licences sont ensuite appliquées aux documents pour chaque utilisateur.

La création d’une stratégie abstraite est prise en charge uniquement par le biais du SDK Java de Document Security. Vous pouvez toutefois administrer les stratégies que vous créez à partir de la stratégie abstraite des pages Web de Document Security. Les stratégies créées à l’aide de cette méthode ont un comportement identique à celles créées à partir des pages Web de Document Security.

Pour plus d’informations, consultez [Programmation avec AEM Forms](https://www.adobe.com/go/learn_aemforms_programming_63_fr).
