---
title: Intégration à Acrobat Sign | Gestion des données utilisateur
seo-title: Integration with Acrobat Sign | Handling user data
description: AEM Forms s’intègre à Acrobat Sign pour permettre aux processus de signature électronique dans les formulaires adaptatifs de traiter les formulaires ou les contrats pour les processus juridiques, de vente, de paie et de gestion des ressources humaines. Explorez plus en détail les données utilisateur, les entrepôts de données, ainsi que l’accès et la suppression des données utilisateur.
seo-description: AEM Forms integrates with Acrobat Sign to enable e-signature workflows in adaptive forms to process forms or agreements for legal, sales, payroll, human resource management workflows. Dig deeper on user data, data stores, and access and delete user data.
uuid: cb3a455d-2e33-44c8-8f71-3a7ecd939cd8
topic-tags: grdp
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: e9e0d8fb-955e-4021-9e9a-9c95c6ffe88d
feature: Acrobat Sign
role: Admin
exl-id: c2061de7-8627-4595-b96c-aa2d6abffddd
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 13%

---

# Intégration à Acrobat Sign | Gestion des données utilisateur {#integration-with-adobe-sign-handling-user-data}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

AEM Forms s’intègre à Acrobat Sign pour permettre aux processus de signature électronique dans les formulaires adaptatifs de traiter les formulaires ou les contrats pour les processus juridiques, de vente, de paie et de gestion des ressources humaines. Il autorise les processus de signature pour un ou plusieurs utilisateurs, des processus séquentiels et simultanés, la signature de formulaire en tant qu’utilisateur anonyme ou connecté et propose plusieurs méthodes d’authentification pour les utilisateurs.

Lorsqu’un signataire ou plusieurs signataires signent et envoient un formulaire adaptatif, un accord Acrobat Sign est généré, qui contient des informations sur les signataires.

Pour plus d’informations sur l’intégration d’AEM Forms à Acrobat Sign, voir [Utilisation d’Acrobat Sign dans un formulaire adaptatif](/help/forms/using/working-with-adobe-sign.md).

## Données utilisateur et stockage de données {#data}

Le formulaire adaptatif activé par Acrobat Sign contient des informations sur les signataires et peut inclure d’autres données utilisateur collectées par le formulaire adaptatif. Le service Acrobat Sign enregistre les données utilisateur avec la signature dans le contrat. L’accord est enregistré sur le serveur Acrobat Sign configuré dans les services cloud AEM Forms. En outre, si le formulaire adaptatif est configuré pour utiliser l’action d’envoi du portail Forms, les données de l’accord sont enregistrées dans l’entrepôt de données du portail de formulaires avec les données de formulaire.

## Accès et suppression des données utilisateur {#access-and-delete-user-data}

Les données utilisateur sont collectées dans le contrat, mais ne sont enregistrées dans aucune des tables de service. Acrobat Sign permet aux administrateurs de faire leurs propres choix sur la gestion des données qu’ils contrôlent dans le service. Les administrateurs de la confidentialité du service Acrobat Sign peuvent répertorier ou supprimer des contrats en fonction de l’adresse électronique d’un demandeur.

Acrobat Sign propose une application web qui permet la recherche des accords par les participants, et si nécessaire, leur suppression. Pour plus d’informations, voir [Acrobat Sign - Fonctionnalité : Suppression des informations sur l’utilisateur](https://helpx.adobe.com/fr/sign/using/gdpr-compliance.html).

Les données d’accord pour les formulaires adaptatifs configurés pour utiliser l’action d’envoi du portail Forms sont également enregistrées dans l’entrepôt de données du portail de formulaires. Pour accéder aux données de l’entrepôt de données de Forms Portal et les supprimer, reportez-vous à la section [Portail Forms | Gestion des données utilisateur](/help/forms/using/forms-portal-handling-user-data.md).
