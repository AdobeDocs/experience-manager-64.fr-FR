---
title: Création et configuration des rôles
seo-title: Creating and configuring roles
description: Découvrez comment associer des utilisateurs et des groupes à des rôles faisant partie de la base de données User Management. Vous pouvez également créer, modifier et supprimer des rôles.
seo-description: Learn how to associate users and groups with roles that are already part of the User Management database. You can also create, edit, and delete roles.
uuid: e8e4331d-48e1-4fa9-8f44-f885f4ab1a54
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/setting_up_and_organizing_users
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 737fb4d1-adef-47e1-9a0d-8cddd13132cb
exl-id: 794769f8-57c7-43c1-87dd-952121ced3e4
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '2526'
ht-degree: 50%

---

# Création et configuration des rôles{#creating-and-configuring-roles}

Les pages Web de User Management vous permettent d’associer des utilisateurs et des groupes à des rôles faisant partie de la base de données User Management. Vous pouvez également créer, modifier et supprimer des rôles.

User Management comporte deux types de rôles :

**Rôles mutables :** Ce type de rôle peut être modifié et supprimé, et les autorisations de rôle peuvent être ajoutées et supprimées de ces types de rôle. Les rôles que vous créez sont des rôles mutables. Vous pouvez ajouter et supprimer des utilisateurs et groupes affectés à des rôles mutables.

**Rôles non modifiables :** Les rôles par défaut inclus dans User Management sont des rôles non modifiables. Ils ne peuvent être ni modifiés ni supprimés. Toutefois, vous pouvez ajouter ou supprimer des utilisateurs et des groupes affectés à des rôles non modifiables.

Les API d&#39;AEM forms permettent également de créer des rôles modifiables et non modifiables.

## Rôles par défaut {#default-roles}

Les rôles par défaut suivants sont inclus dans la base de données Gestion des utilisateurs.

**Utilisateur d’Administration Console :** peuvent accéder à Administration Console.

**Administrateur de l’application :** Peut utiliser toutes les fonctionnalités de Workbench. Peut utiliser les pages Applications et services de Administration Console pour configurer des propriétés d’exécution de services, des points de fin et la sécurité.

**Administrateur d’AEM forms :** peut effectuer toutes les tâches pour tous les services installés.

**Administrateur de sécurité :** Contrôle les paramètres User Management et gère les utilisateurs et les groupes associés à un domaine User Manager.

**Utilisateur des services :** peut afficher et appeler n’importe quel service ;

**Super administrateur :** a accès à toutes les fonctionnalités d’administration du système, y compris les services ;

**Trust Administrator :** peut gérer les paramètres d’approbation PKI et les informations d’identification PKI gérés à partir de la page Trust Store Management de la console d’administration.

### Rôles par défaut supplémentaires {#additional-default-roles}

Les rôles par défaut supplémentaires suivants peuvent également être inclus, selon les composants d’AEM Forms installés.

**Utilisateur de l’application de téléchargement de document :** Peut télécharger des documents à l’aide de Flex Remoting.

**Administrateur Forms :** peut afficher et modifier les paramètres de la page Forms dans Administration Console.

**AEM forms Contentspace Administrator :** peut afficher et modifier les paramètres de la page Content Services (obsolète) dans Administration Console.

**AEM utilisateur Contentspace de forms :** Peut se connecter aux pages web de Contentspace (obsolète)

**Documentum Connector Administrator :** peut afficher et modifier les paramètres de la page Connector for EMC Documentum dans Administration Console.

**Administrateur du connecteur FileNet d’AEM forms :** peut afficher et modifier les paramètres de la page Connector for IBM FileNet dans Administration Console.

**Administrateur IBM CM Connector :** peut afficher et modifier les paramètres de la page Connector for IBM Content Manager dans Administration Console.

**Administrateur Rights Management :** exécute toutes les tâches requises pour toutes les configurations de serveur sur les pages de Rights Management appropriées ;

**Utilisateur final du Rights Management :** peut accéder aux pages web des utilisateurs finaux Rights Management ;

**Rights Management Invite User :** Peut inviter des utilisateurs

**Rights Management Gérer les utilisateurs invités et locaux :** peut effectuer les tâches requises pour gérer tous les utilisateurs invités et locaux sur les pages de Rights Management appropriées ;

**Administrateur du jeu de stratégies de Rights Management :** exécute toutes les tâches requises pour tous les jeux de stratégies sur les pages de Rights Management appropriées ;

**Super administrateur Rights Management :** exécute toutes les tâches requises à partir de la page du Rights Management ;

**Administrateur d’AEM forms Workspace :** peut afficher et modifier les paramètres de la page Workspace dans Administration Console.

***Remarque ** : Flex Workspace est obsolète pour la version d’AEM Forms.*

**Utilisateur de Workspace :** peut se connecter à l’application Workspace destinée aux utilisateurs finaux ;

**Administrateur Output :** peut afficher et modifier les paramètres de la page Output d’Administration Console.

**Administrateur PDFG :** peut afficher et modifier les paramètres de la page PDF Generator dans Administration Console.

**Utilisateur PDFG :** Peut accéder à toutes les fonctionnalités non administratives de PDF Generator

**Application web des extensions Acrobat Reader DC :** Peut utiliser l’application web des extensions Acrobat Reader DC

>[!NOTE]
>
>pour des raisons de sécurité, les utilisateurs disposant de certains types de privilèges d’administrateur n’ont pas accès aux pages Web des utilisateurs finaux de Workspace. Comme ces pages peuvent se trouver en dehors d’un pare-feu, autoriser des tâches d’administration pourrait présenter un risque de sécurité. Seuls les utilisateurs disposant du privilège d’administrateur ou d’utilisateur d’AEM Forms Workspace peuvent accéder aux pages Web des utilisateurs finaux de Workspace.

>[!NOTE]
>
>Flex Workspace est obsolète pour la version d’AEM Forms.

## Création d’un rôle {#create-a-role}

1. Dans Administration Console, cliquez sur Paramètres > Gestion des utilisateurs > Gestion des rôles, puis sur Nouveau rôle.
1. Dans la zone Nom du rôle, saisissez le nom du rôle, indiquez-en éventuellement une description, puis cliquez sur Suivant.

   >[!NOTE]
   >
   >si vous utilisez MySQL, vous ne pouvez pas créer deux rôles portant le même nom, même s’ils diffèrent par l’utilisation de caractères étendus. Par exemple, si vous essayez de créer un rôle nommé abcde alors qu’un autre nommé âbcdè existe déjà, une erreur se produit.

1. Cliquez sur Rechercher des droits et sélectionnez les droits à ajouter au rôle.
1. Cliquez sur OK puis sur Suivant.
1. Affectez ce rôle à des utilisateurs et à des groupes :

   * Cliquez sur Rechercher des utilisateurs/groupes.
   * Dans la zone Rechercher, saisissez vos critères de recherche.
   * Sélectionnez Nom, Adresse électronique ou ID utilisateur, puis Utilisateurs, Groupes ou Utilisateurs et groupes.
   * Sélectionnez le domaine, le nombre de résultats à afficher, puis cliquez sur Rechercher.
   * Cochez les cases correspondant aux utilisateurs et aux groupes auxquels affecter ce rôle, puis cliquez sur OK.

1. Pour afficher les détails relatifs aux utilisateurs et aux groupes, sélectionnez l’entité.
1. Cliquez sur OK, puis sur Terminer.

## Modification d’un rôle {#edit-a-role}

1. Dans Administration Console, cliquez sur Paramètres > Gestion des utilisateurs > Gestion des rôles, puis sur Nom du rôle.

   Par défaut, tous les rôles trouvés dans la base de données User Management s’affichent dans la page Gestion des rôles. Si la liste est trop importante, utilisez la zone Rechercher située en haut de la page pour rechercher un nom de rôle particulier.

1. Cliquez sur le rôle à modifier, modifiez les paramètres généraux, puis cliquez sur Enregistrer.
1. Pour modifier les droits du rôle, cliquez sur l’onglet Droits et procédez comme suit :

   * Pour ajouter de nouveaux droits, cliquez sur Rechercher des droits, activez les cases à cocher correspondant aux droits à ajouter, cliquez sur OK, puis sur Enregistrer.
   * Pour supprimer un droit d’un rôle, activez la case à cocher correspondant au droit, cliquez sur Supprimer, puis sur Enregistrer.

1. Pour gérer l’affectation d’un rôle, cliquez sur l’onglet Utilisateurs de rôle et procédez comme suit :

   * Pour affecter le rôle à de nouveaux utilisateurs et à de nouveaux groupes, cliquez sur Rechercher des utilisateurs/groupes et saisissez les informations de recherche. Activez la case à cocher correspondant aux utilisateurs et aux groupes auxquels affecter ce rôle, cliquez sur OK, puis sur Enregistrer.
   * Pour supprimer le rôle, activez la case à cocher correspondant aux utilisateurs ou aux groupes, cliquez sur Retirer, puis sur Enregistrer.

## Suppression d’un rôle {#delete-a-role}

Vous pouvez supprimer tous les rôles créés, mais pas les rôles AEM Forms par défaut intégrés au produit.

1. Dans Administration Console, cliquez sur Paramètres > Gestion des utilisateurs > Gestion des rôles, puis sur Nom du rôle.

   Par défaut, tous les rôles trouvés dans la base de données User Management s’affichent dans la page Gestion des rôles. Si la liste est trop importante, utilisez la zone Rechercher située en haut de la page pour rechercher un nom de rôle particulier.

1. Cochez la case correspondant au rôle à supprimer, cliquez sur Supprimer, puis sur OK.

## Affectation d’un rôle aux utilisateurs et aux groupes {#assign-a-role-to-users-and-groups}

1. Dans Administration Console, cliquez sur Paramètres > Gestion des utilisateurs > Utilisateurs et groupes.
1. Indiquez les informations permettant d’affiner la recherche et cliquez sur Rechercher. Les résultats de recherche apparaissent au bas de la page. Vous pouvez trier la liste en cliquant sur les en-têtes de colonne.
1. Cochez les cases situées en regard des utilisateurs et des groupes à associer au rôle, puis cliquez sur Affecter le rôle.
1. Sélectionnez le rôle à affecter à l’utilisateur ou au groupe, puis cliquez sur OK.

Cette opération peut également s’effectuer via la page Gestion des rôles.

## Identification de la personne à laquelle est affecté un rôle {#determine-who-is-assigned-to-a-role}

1. Dans Administration Console, cliquez sur Paramètres > Gestion des utilisateurs > Gestion des rôles, puis sur Nom du rôle.

   Par défaut, tous les rôles trouvés dans la base de données User Management s’affichent dans la page Gestion des rôles. Si la liste est trop importante, utilisez la zone Rechercher située en haut de la page pour rechercher un nom de rôle particulier.

1. Dans la page Détails du rôle, cliquez sur l’onglet Utilisateurs de rôle. La liste des utilisateurs et des groupes directement associés au rôle s’affiche.

## Modification des droits d’un rôle {#change-role-permissions}

Vous pouvez modifier les droits des rôles que vous avez créés, mais pas ceux qui sont attribués aux rôles AEM Forms par défaut inclus au produit.

1. Dans Administration Console, cliquez sur Paramètres > Gestion des utilisateurs > Gestion des rôles, puis sur Nom du rôle.

   Par défaut, tous les rôles trouvés dans la base de données User Management s’affichent dans la page Gestion des rôles. Si la liste est trop importante, utilisez la zone Rechercher située en haut de la page pour rechercher un nom de rôle particulier.

1. Sélectionnez le rôle dont vous souhaitez afficher les droits, puis cliquez sur l’onglet Droits.
1. Pour modifier ces droits, cliquez sur Rechercher des droits, activez les cases à cocher correspondant aux droits à ajouter au rôle, cliquez sur OK, puis sur Enregistrer.
1. Pour supprimer un droit, sélectionnez-le, cliquez sur Supprimer, puis sur Enregistrer.

### Autorisations d’AEM Forms {#aem-forms-permissions}

**ADD_REMOVE_ENDPOINT_PERM :** Ajout, suppression et modification des points de fin d’un service

**Connexion du Admin Console :** Affichage de la console d’administration

**Certificate Modify :** Modifier les paramètres d’approbation de tout certificat dans Trust Store

**Certificate Read :** Lire tout certificat dans Trust Store

**Certificate Write :** Ajout d’un certificat à Trust Store

**Component Add :** Installer un nouveau composant dans le système

**Suppression de composants :** Suppression de tout composant du système

**Component Read :** Lire tout composant du système

**Administrateur Contentspace :** Autorisation pour l’administrateur Contentspace (obsolète)

**Contentspace Console Login :** Autorisation de connexion à la console Contentspace (obsolète)

**Contrôle des paramètres principaux :** Gestion des paramètres de la page Paramètres de Core System dans Administration Console

**CREATE_VERSION_PERM :** Création d’une version d’un service

**Credential Modify :** Modification des informations d’identification de signature dans Trust Store

**Credential Read :** Lire les informations d’identification de signature dans Trust Store

**Credential Write :** Ajout d’informations d’identification de signature à Trust Store

**CRL Modify :** Modifier toute liste de révocation des certificats (CRL) dans Trust Store

**CRL Read :** Lire toute liste CRL dans Trust Store

**CRL Write :** Ajout d’une liste CRL à Trust Store

**Déléguer :** Définir une ACL sur une ressource

**DELETE_VERSION_PERM :** Suppression d’une version d’un service

**Document Upload :** Téléchargement de documents dans AEM forms

**Domain Control :** Créer, supprimer ou modifier des paramètres pour tout domaine User Management, y compris ses fournisseurs d’authentification et d’annuaire

**Event Type Edit :** Modification des types d’événement

**Identity Impersonation Control :** Emprunter l’identité dans User Manager

**INVOKE_PERM :** Appeler toutes les opérations sur un service

**LCDS Data Model Control :** Lecture et déploiement de modèles de données dans Data Services

**Mise à jour de License Manager :** Mise à jour des informations de licence

**MODIFY_CONFIG_PERM :** Modification de la configuration d’un service

**TERM** Modification de la version d’un service

**PDFGAdminPermission :** Administrateur PDFG

**PDFGUserPermission :** Utilisateur PDFG

**PERM_DCTM_ADMIN :** Administrateur Documentum Connector

**PERM_FILENET_ADMIN :** Administrateur FileNet Connector

**PERM_FORMS_ADMIN :** Administrateur Forms

**PERM_IBMCM_ADMIN :** Administrateur IBM CM Connector

**PERM_OUTPUT_ADMIN :** Administrateur Output

**PERM_READER_EXTENSIONS_WEB_APPLICATION :** Utilisation de l’application web des extensions Acrobat Reader DC

**PERM_SP_ADMIN :** Gestion des paramètres du connecteur SharePoint

**PERM_WORKSPACE_ADMIN :** Gestion des paramètres de Workspace

**PERM_WORKSPACE_USER :** Connectez-vous à l’application Workspace destinée aux utilisateurs finaux.

**Principal Control :** Gérer les utilisateurs et les groupes pour n’importe quel domaine et gérer les affectations de rôles pour tous les utilisateurs et groupes d’un domaine.

**Lecture/Suppression de l’enregistrement de processus :** Liste et récupération des instances d’audit de workflow

**PROCESS_OWNER_PERM :** Affichage des données de tendance et exécution d’actions administratives sur un service créé à partir d’un processus

**Lecture :** Lire le contenu d&#39;une ressource

**READ_PERM :** Lecture ou affichage d’un service

**Renouveler l’assertion :** Renouveler les assertions dans User Management

**Repository Delegate :** Définir une ACL sur une ressource

**Repository Read :** Lire le contenu d&#39;une ressource

**Repository Traverse :** Inclure une ressource dans une requête de ressources de liste ou lire les métadonnées d’une ressource

**Repository Write :** Écriture des métadonnées et du contenu du référentiel

**Rights Management Change Policy Owner :** Modifier le propriétaire de la stratégie

**Rights Management End User Console Login :** Connexion à l’interface utilisateur de l’utilisateur final du Rights Management

**Configuration de la gestion des Rights Management :** Gestion de la configuration du serveur

**Rights Management Gérer les utilisateurs invités et locaux :** Gestion des utilisateurs invités et locaux

**Rights Management Gérer les jeux de stratégies :** Gérer toutes les stratégies et tous les documents d’un jeu de stratégies

**Rights Management Policy Set Add Coordinator :** Ajouter, supprimer et modifier des autorisations pour les coordinateurs de jeux de stratégies

**Création d’un jeu de stratégies de Rights Management :** Création d’une stratégie pour un jeu de stratégies

**Stratégie de suppression du jeu de stratégies de Rights Management :** Suppression d’une stratégie d’un jeu de stratégies

**Stratégie de modification du jeu de stratégies de Rights Management :** Modification d’une stratégie dans un jeu de stratégies

**Rights Management Policy Set Manage Document Publisher :** Lorsque vous créez des jeux de stratégies, vous attribuez aux utilisateurs le rôle d’éditeur de document. L’éditeur est l’utilisateur qui protège le document avec une stratégie.

**Rights Management Policy Set Remove Coordinator :** Suppression d’un coordinateur de jeux de stratégies d’un jeu

**Document de révocation du jeu de stratégies de Rights Management :** Révocation de l’accès aux documents d’un jeu de stratégies

**Stratégie de changement de jeu de stratégies de Rights Management :** Changement de stratégies pour un document

**Document de révocation du jeu de stratégies de Rights Management :** Annulation de la révocation d’un document

**Événement d’affichage du jeu de stratégies de Rights Management :** Affichage des événements de stratégie et de document d’une stratégie ou d’un document dans un jeu de stratégies

**Événements du serveur de vue Rights Management :** Recherche et affichage de tous les événements de contrôle

**Contrôle de rôle :** Création, suppression et modification des rôles dans User Management

**Service Activate :** Démarrez n’importe quel service, le rendant disponible pour appel

**Service Add :** Déployez un nouveau service dans le registre des services. Cela inclut l’ajout de nouveaux processus et de variantes de processus.

**Service Deactivate :** Arrêter tout service du système

**Service Delete :** Supprimez tout service du système, y compris les processus et les variantes de processus.

**Service Invoke :** Appeler tout service dans le registre de services disponible au moment de l’exécution

**Service Modify :** Modifiez les propriétés de configuration de tout service du système. Cela inclut le verrouillage et le déverrouillage d’un service dans l’IDE, et l’ajout ou la suppression de points de fin au niveau d’un service.

**Service Read :** Lisez tous les services du système. Cela inclut tous les processus et variantes de processus.

**SERVICE_AGENT_PERM :** Afficher des données et interagir avec des instances de processus pour un service créé à partir d’un processus

**SERVICE_MANAGER_PERM :** Exécution de l’équilibrage de charge et d’autres actions administratives sur un service créé à partir d’un processus

**START_STOP_PERM :** Démarrer ou arrêter un service

**SUPERVISOR_PERM :** Affichage des données d’instance de processus pour un service créé à partir d’un processus

**Traverse :** Inclure une ressource dans une requête de ressources de liste ou lire les métadonnées d’une ressource

**Write :** Écriture des métadonnées et du contenu du référentiel

**Ouverture de fichiers dans Workbench**

Pour consulter le contenu de l’affichage Ressources de Workbench et ouvrir des fichiers, un utilisateur a besoin des autorisations suivantes :

* Repository Read
* Repository Traverse
* Service Invoke
* Service Read

## Suppression d’un utilisateur ou d’un groupe d’un rôle {#remove-a-user-or-group-from-a-role}

La page Gestion des rôles permet de supprimer des utilisateurs et des groupes d’un rôle particulier. Si l’utilisateur ou le groupe a hérité de l’affectation du rôle, il est impossible de supprimer ce rôle au niveau de l’utilisateur ou du groupe. Supprimez l’utilisateur ou le groupe dans l’arborescence d’héritage ou supprimez le rôle depuis le parent.

1. Dans Administration Console, cliquez sur Paramètres > Gestion des utilisateurs > Gestion des rôles, puis sur Nom du rôle.

   Par défaut, tous les rôles trouvés dans la base de données User Management s’affichent dans la page Gestion des rôles. Si la liste est trop importante, utilisez la zone Rechercher située en haut de la page pour rechercher un nom de rôle particulier.

1. Dans la liste des rôles, cliquez sur le nom du rôle à mettre à jour, puis cliquez sur l’onglet Utilisateurs de rôle. La liste des utilisateurs et des groupes associés au rôle s’affiche.
1. Cochez les cases situées en regard des utilisateurs et des groupes à supprimer du rôle, puis cliquez sur Retirer.
1. Cliquez sur Enregistrer, puis sur OK.
