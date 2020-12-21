---
title: NE PAS PUBLIER L’interface utilisateur basée sur un rôle dans Correspondence Management
seo-title: NE PAS PUBLIER L’interface utilisateur basée sur un rôle dans Correspondence Management
description: 'null'
seo-description: 'null'
page-status-flag: de-activated
uuid: 60808852-f63f-4c0a-badb-b0af93c995a8
contentOwner: gtalwar
products: SG_EXPERIENCEMANAGER/6.3/FORMS
discoiquuid: 342f111e-f15a-4f9a-8993-f90760363c02
translation-type: tm+mt
source-git-commit: cdec5b3c57ce1c80c0ed6b5cb7650b52cf9bc340
workflow-type: tm+mt
source-wordcount: '487'
ht-degree: 28%

---


# NE PAS PUBLIER L’interface utilisateur basée sur le rôle dans Correspondence Management {#do-not-publish-role-based-user-interface-in-correspondence-management}

En AEM, l’administrateur peut fournir un accès par rôle à différents groupes d’utilisateurs qui effectuent diverses actions sur différentes ressources. Par exemple, la fonctionnalité de création ou de modification des dictionnaires de données peut être disponible uniquement pour les utilisateurs d’un groupe d’utilisateurs spécifique, tandis que d’autres utilisateurs peuvent uniquement vue et utiliser les dictionnaires de données.

L’interface AEM affiche les options, telles que la création ou la modification d’un type de ressource, en fonction du niveau d’accès d’un utilisateur. Par exemple, si un utilisateur n’est pas autorisé à créer un dictionnaire de données, l’option de création d’un dictionnaire de données n’apparaît pas dans l’interface utilisateur.

Bien que CRX vous permette de configurer les droits d’accès pour les comptes d’utilisateurs et de groupes, cet article traite des droits d’accès basés sur les rôles ou les groupes d’utilisateurs.

Pour plus d’informations sur les groupes, les permissions, les listes de contrôle d&#39;accès et la gestion des utilisateurs et des groupes, voir [Administration utilisateur et sécurité](/help/sites-administering/security.md).

## Gestion des autorisations {#managing-permissions}

1. Assurez-vous que l’utilisateur pour lequel vous souhaitez gérer les autorisations est ajouté au groupe d’utilisateurs approprié.

   Par exemple, l’utilisateur John Doe est ajouté aux groupes `agents` et `cm-creditcard`. Pour plus d’informations, voir Ajouter des utilisateurs ou des groupes à un groupe. Pour plus d’informations, voir [Gestion des utilisateurs et des groupes d’utilisateurs](/help/communities/users.md).

   ![]()

1. Créez les dossiers en fonction des autorisations à accorder.

   Par exemple, si une entreprise possède des divisions du prêt immobilier, de la carte de crédit et de l&#39;assurance, elle peut créer des dossiers nommés `HomeMortgage`, `CreditCard,`et `Insurance` pour conserver les actifs concernés et donner accès de manière sélective aux agents pour les actifs propres à leur service uniquement.

1. Pour accéder à la sécurité AEM WCM, effectuez l’une des opérations suivantes :

   1. Dans l’écran de bienvenue ou à différents emplacements d’AEM, cliquez sur l’icône de sécurité :

   1. Accédez directement à `https://[server]:[port]/useradmin`. Assurez-vous de vous connecter à AEM en tant qu’administrateur.

      ![]()
   L’arborescence de gauche répertorie tous les utilisateurs et groupes actuellement dans le système. Vous pouvez sélectionner les colonnes que vous souhaitez afficher, trier le contenu des colonnes et même modifier l’ordre dans lequel les colonnes sont affichées en faisant glisser l’en-tête de colonne vers la nouvelle position souhaitée.

   Les onglets permettent d’accéder à diverses configurations :

1. Dans la liste de l’arborescence de gauche, appuyez sur le nom du groupe concerné en appuyant sur le doublon, puis sélectionnez l’onglet Autorisations.

   Pour localiser le nom du groupe, vous pouvez le saisir dans l’espace prévu à cet effet.

1. Dans l’onglet permissions, accédez au chemin d’accès auquel vous souhaitez ajouter des autorisations. Les dossiers Correspondence Management se trouvent sous le dossier `content/apps/cm/`.

   Dans la colonne Membre, cochez la case correspondant aux membres qui doivent disposer d’autorisations au niveau de ce chemin d’accès. Décochez la case correspondant aux membres dont vous souhaitez supprimer les autorisations. Un triangle rouge apparaît dans la cellule à laquelle vous avez apporté des modifications.

   ![useradmin-creditcard](assets/useradmin-creditcard.png)

   >[!NOTE]
   >
   >Les autorisations spécifiées dans un dossier remplacent les autorisations spécifiées dans ses sous-dossiers.

1. Appuyez sur Save (Enregistrer).
1. Texte de l’étape
1. Texte de l’étape
1. Texte de l’étape

