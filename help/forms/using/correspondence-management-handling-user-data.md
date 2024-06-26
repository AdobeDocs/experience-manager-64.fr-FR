---
title: Correspondence Management | Gestion des données utilisateur
seo-title: Correspondence Management | Handling user data
description: AEM Forms Correspondence Management vous permet de créer, gérer et rationaliser des correspondances client sécurisées et personnalisées. Découvrez comment configurer le stockage des données pour les brouillons et les lettres envoyées dans AEM référentiel, accéder aux données stockées et supprimer les données stockées.
seo-description: AEM Forms Correspondence Management enables you to create, manage, and streamline secure and personalized customer correspondences. Learn how to configure storing data for draft and submitted letters in AEM repository, access stored data, and delete stored data.
uuid: d5bb190b-d668-4da3-95da-b7705ad302d9
topic-tags: grdp
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 764d8e0d-604d-4c7b-89cd-7686ce5f03ff
role: Admin
exl-id: 4a6b3403-2941-4098-bb30-769281adedc2
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '608'
ht-degree: 42%

---

# Correspondence Management | Gestion des données utilisateur {#correspondence-management-handling-user-data}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

AEM Forms Correspondence Management vous permet de créer, gérer et rationaliser des correspondances client sécurisées et personnalisées. Il fournit une interface utilisateur intuitive permettant aux utilisateurs professionnels de créer des correspondances à l’aide de blocs de contenu et d’éléments multimédias prévalidés. Pour obtenir plus d’informations sur la création de correspondances, reportez-vous à la section [Créer une correspondance](/help/forms/using/create-correspondence.md).

Lorsqu’un utilisateur ou un agent de l’entreprise enregistre une correspondance en tant que brouillon ou l’envoie, une instance de lettre est enregistrée dans le référentiel AEM. L’instance de lettre comprend des données et des métadonnées de correspondance.

>[!NOTE]
>
>Dans AEM 6.4 Forms, la gestion des correspondances n’est pas disponible hors champ. Si vous effectuez une mise à niveau à partir d’une version précédente d’AEM Forms, installez le package de compatibilité et migrez vos actifs Correspondence Management pour continuer à les utiliser dans AEM 6.4 Forms. Pour plus d’informations, voir [Package de compatibilité](/help/forms/using/compatibility-package.md).

## Données utilisateur et stockage de données {#data}

Correspondence Management stocke les données des brouillons et des lettres envoyées dans le référentiel d’AEM uniquement si l’instance de publication est configurée pour gérer les instances de lettre. Pour plus d’informations sur la configuration, voir [Propriétés de configuration de Correspondence Management](/help/forms/using/cm-configuration-properties.md).

Selon la persistance de l’entrepôt de données configuré pour votre déploiement AEM, les données de correspondance envoyées et de brouillons sont stockées aux emplacements suivants.

<table> 
 <tbody>
  <tr>
   <td><p><strong>Type de persistance</strong></p> </td> 
   <td><p><strong>Stockage de données</strong></p> </td> 
   <td><p><strong>Emplacement</strong></p> </td> 
  </tr>
  <tr>
   <td><p>Valeur par défaut</p> </td> 
   <td><p>Référentiel AEM de l’instance de publication et des instances d’auteur spécifiées dans la configuration de réplication inverse</p> </td> 
   <td><p><code>/content/apps/cm/letterInstances/[yyyy]/[mm]/[dd]/[node-id]/[letter-instance-name]/</code> </p> </td> 
  </tr>
  <tr>
   <td><p>Distant</p> </td> 
   <td><p>Référentiel AEM de l’instance d’auteur de traitement à distance</p> </td> 
   <td><p><code>/content/apps/cm/letterInstances/[yyyy]/[mm]/[dd]/[node-id]/[letter-instance-name]/</code></p> </td> 
  </tr>
 </tbody>
</table>

À l’emplacement du référentiel AEM spécifié ci-dessus :

* `[yyyy]/[mm]/[dd]` correspond à la structure du nœud en fonction de la date à laquelle l’instance de lettre a été créée
* `[node-id]` correspond à l’ID attribué au dossier contenant la lettre
* `[letter-instance-name]` correspond au nom spécifié lors de l’enregistrement ou de l’envoi d’une lettre

Sous le nœud [letter-instance-name], la structure de nœud suivante est créée et les données de chaque instance de lettre sont stockées dans le référentiel AEM :

| Nœud | Description |
|---|---|
| `extendedProperties` | Stocke les propriétés de métadonnées de l’instance de lettre. |
| `dataXML` | Stocke un fichier dataXML téléchargeable contenant les données de correspondance au format binaire. |
| `processedXDP` | Inclut les détails du modèle XDP utilisé pour créer la lettre envoyée. Ce nœud est créé uniquement pour les correspondances envoyées. |
| `submittedLetter` | Stocke les données de lettres envoyées dans un format binaire téléchargeable. Ce nœud est créé uniquement pour les correspondances envoyées. |

## Accès et suppression des données utilisateur {#access-and-delete-user-data}

Vous pouvez accéder aux données de correspondance préliminaires et envoyées dans les entrepôts de données configurés et, si nécessaire, les supprimer.

### Accès aux données utilisateur {#access-user-data}

Correspondence Management fournit des API que vous pouvez utiliser pour rechercher et accéder aux instances de brouillon et de lettre envoyée. Grâce aux API, vous pouvez rechercher et ouvrir des instances de lettre à l’aide de l’ID d’instance de lettre ou de l’utilisateur qui a enregistré ou envoyé la correspondance. Pour plus d’informations, reportez-vous à la section [Utiliser les API pour accéder aux instances de lettre](/help/forms/using/cm-apis-to-access-letter-instances.md).

Vous pouvez également accéder à l’instance de lettre dans AEM référentiel à l’aide de CRX DELite. Voir [Données utilisateur et entrepôts de données](/help/forms/using/correspondence-management-handling-user-data.md#data) pour plus d’informations sur les données stockées et l’emplacement du référentiel.

### Suppression de données utilisateur {#delete-user-data}

Pour trouver une instance de lettre contenant les données d’un utilisateur spécifique, vous pouvez :

* Utilisez les API de Correspondence Management si le nom de l’instance de lettre ou l’utilisateur ayant enregistré le brouillon ou envoyé la correspondance est connu
* Utilisez l’option de recherche du référentiel AEM et saisissez des informations d’identification personnelles telles que l’identifiant ou le nom de l’adresse électronique pour trouver le nœud dans lequel l’information est stockée. 

Pour supprimer définitivement des données utilisateur de correspondances sous forme de brouillon et envoyées dans les systèmes AEM, vous devez supprimer manuellement le nœud d’instance de lettre de toutes les instances AEM applicables.
