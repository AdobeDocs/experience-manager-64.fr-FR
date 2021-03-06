---
title: Intégration à Adobe Sign | Gestion des données utilisateur
seo-title: Integration with Adobe Sign | Handling user data
description: AEM Forms s’intègre à Adobe Sign pour autoriser les processus de signature électronique dans les formulaires adaptatifs pour traiter des formulaires ou des contrats pour les flux de travail juridiques, commerciaux, de rémunération et de gestion des ressources humaines. Explorez plus en détail les données utilisateur, les entrepôts de données, ainsi que l’accès et la suppression des données utilisateur.
seo-description: AEM Forms integrates with Adobe Sign to enable e-signature workflows in adaptive forms to process forms or agreements for legal, sales, payroll, human resource management workflows. Dig deeper on user data, data stores, and access and delete user data.
uuid: cb3a455d-2e33-44c8-8f71-3a7ecd939cd8
topic-tags: grdp
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: e9e0d8fb-955e-4021-9e9a-9c95c6ffe88d
feature: Adobe Sign
role: Admin
exl-id: c2061de7-8627-4595-b96c-aa2d6abffddd
source-git-commit: 3c050c33a384d586d74bd641f7622989dc1d6b22
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 86%

---

# Intégration à Adobe Sign | Gestion des données utilisateur {#integration-with-adobe-sign-handling-user-data}

AEM Forms s’intègre à Adobe Sign pour autoriser les processus de signature électronique dans les formulaires adaptatifs pour traiter des formulaires ou des contrats pour les flux de travail juridiques, commerciaux, de rémunération et de gestion des ressources humaines. Il autorise les processus de signature pour un ou plusieurs utilisateurs, des processus séquentiels et simultanés, la signature de formulaire en tant qu’utilisateur anonyme ou connecté et propose plusieurs méthodes d’authentification pour les utilisateurs.

Lorsqu’un ou plusieurs utilisateurs signent et envoient un formulaire adaptatif, un contrat Adobe Sign contenant des informations sur les signataires est généré.

Pour plus d’informations sur l’intégration d’AEM Forms à Adobe Sign, voir [Utilisation d’Adobe Sign dans un formulaire adaptatif](/help/forms/using/working-with-adobe-sign.md).

## Données utilisateur et stockage de données {#data}

Le formulaire adaptatif activé par Adobe Sign inclut des informations sur les signataires et peut inclure d’autres données utilisateur collectées par le formulaire adaptatif. Le service Adobe Sign enregistre les données de l’utilisateur à l’aide de la signature du contrat. Le contrat est enregistré sur le serveur Adobe Sign configuré dans les services cloud d’AEM Forms. Par ailleurs, si le formulaire adaptatif est configuré pour utiliser l’action d’envoi du portail Forms, les données du contrat sont enregistrées dans le stockage de données du portail Forms avec les données du formulaire.

## Accès et suppression des données utilisateur {#access-and-delete-user-data}

Les données utilisateur sont collectées dans le contrat mais ne sont enregistrées dans aucune des tables de service. Adobe Sign permet aux administrateurs de faire leurs propres choix concernant la gestion des données qu’ils contrôlent dans le service. Les administrateurs de confidentialité sur le service d’Adobe Sign peuvent répertorier ou supprimer des contrats en fonction de l’adresse électronique du demandeur.

Adobe Sign propose une application Web qui permet de rechercher des contrats en filtrant par participants et, si nécessaire, de les supprimer. Pour plus d’informations, voir [Adobe Sign - Fonctionnalité : Suppression des informations sur l’utilisateur](https://helpx.adobe.com/sign/help/adobesign_gdpr_user_deletion.html).

Les données de contrat des formulaires adaptatifs configurés pour utiliser l’action d’envoi du portail Forms sont également enregistrées dans le stockage de données du portail Forms. Pour accéder à des données et les supprimer depuis le stockage de données du portail Forms, reportez-vous à la section [Portail Forms | Gestion des données utilisateur](/help/forms/using/forms-portal-handling-user-data.md).
