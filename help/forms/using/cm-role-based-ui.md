---
title: NE PAS PUBLIER L’interface utilisateur en fonction du rôle dans Correspondence Management
seo-title: DO NOT PUBLISH Role based user interface in Correspondence Management
description: NE PAS PUBLIER L’interface utilisateur en fonction du rôle dans Correspondence Management
seo-description: DO NOT PUBLISH Role based user interface in Correspondence Management
page-status-flag: de-activated
uuid: 60808852-f63f-4c0a-badb-b0af93c995a8
contentOwner: gtalwar
products: SG_EXPERIENCEMANAGER/6.3/FORMS
discoiquuid: 342f111e-f15a-4f9a-8993-f90760363c02
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '521'
ht-degree: 17%

---


# NE PAS PUBLIER L’interface utilisateur en fonction du rôle dans Correspondence Management {#do-not-publish-role-based-user-interface-in-correspondence-management}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Dans AEM, l’administrateur peut fournir un accès en fonction du rôle à différents groupes d’utilisateurs pour effectuer diverses actions sur différentes ressources. Par exemple, la fonctionnalité de création ou de modification des dictionnaires de données peut être disponible uniquement pour les utilisateurs d’un groupe d’utilisateurs spécifique, tandis que d’autres utilisateurs peuvent uniquement afficher et utiliser les dictionnaires de données.

L’interface d’AEM affiche les options, telles que la création ou la modification d’un type de ressource, en fonction du niveau d’accès d’un utilisateur. Par exemple, si un utilisateur ne dispose pas des autorisations nécessaires pour créer un dictionnaire de données, l’option permettant de créer un dictionnaire de données n’apparaît pas dans l’interface utilisateur.

Bien que CRX vous permette de configurer les droits d’accès pour les comptes d’utilisateurs et de groupes, cet article traite des droits d’accès basés sur les rôles ou les groupes d’utilisateurs.

Pour plus d’informations sur les groupes, les autorisations, les listes de contrôle d’accès et la gestion des utilisateurs et des groupes, voir [Administration et sécurité des utilisateurs](/help/sites-administering/security.md).

## Gestion des autorisations {#managing-permissions}

1. Assurez-vous que l’utilisateur pour lequel vous souhaitez gérer les autorisations est ajouté au groupe d’utilisateurs approprié.

   Par exemple, l’utilisateur John Doe est ajouté aux groupes. `agents` et `cm-creditcard`. Pour plus d’informations, voir Ajout d’utilisateurs ou de groupes à un groupe. Pour plus d’informations, voir [Gestion des utilisateurs et des groupes d’utilisateurs](/help/communities/users.md).

   ![]()

1. Créez les dossiers adaptés aux autorisations prévues.

   Par exemple, si une entreprise possède des divisions de prêt immobilier, de carte de crédit et d’assurance, elle peut créer des dossiers nommés `HomeMortgage`, `CreditCard,`et `Insurance` conserver les ressources appropriées et donner accès sélectivement aux agents pour les ressources pertinentes uniquement pour leur service.

1. Pour accéder à AEM sécurité WCM, effectuez l’une des opérations suivantes :

   1. Dans l’écran d’accueil ou à différents emplacements d’AEM, cliquez sur l’icône de sécurité :

   1. Accédez directement à `https://[server]:[port]/useradmin`. Assurez-vous de vous connecter à AEM avec des droits d’administration.

      ![]()
   L’arborescence de gauche répertorie tous les utilisateurs et groupes actuellement dans le système. Vous pouvez sélectionner les colonnes à afficher, trier le contenu des colonnes et même modifier l’ordre d’affichage des colonnes en faisant glisser l’en-tête de colonne vers une nouvelle position.

   Les onglets permettent d’accéder à diverses configurations :

1. Dans l’arborescence de gauche, appuyez deux fois sur le nom du groupe approprié, puis sélectionnez l’onglet Autorisations .

   Pour localiser le nom du groupe, vous pouvez saisir son nom dans l’espace prévu à cet effet.

1. Dans l’onglet Autorisations, accédez au chemin auquel vous souhaitez ajouter des autorisations. Les dossiers de Correspondence Management se trouvent sous le `content/apps/cm/` dossier.

   Dans la colonne Membre, cochez la case correspondant aux membres qui doivent disposer d’autorisations au niveau de ce chemin d’accès. Décochez la case correspondant aux membres dont vous souhaitez supprimer les autorisations. Un triangle rouge apparaît dans la cellule sur laquelle vous avez apporté des modifications.

   ![useradmin-creditcard](assets/useradmin-creditcard.png)

   >[!NOTE]
   >
   >Les autorisations spécifiées dans un dossier remplacent les autorisations spécifiées dans ses sous-dossiers.

1. Appuyez sur Enregistrer.
1. Texte de l’étape
1. Texte de l’étape
1. Texte de l’étape

