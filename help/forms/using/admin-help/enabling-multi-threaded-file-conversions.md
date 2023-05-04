---
title: Activation des conversions de fichiers multithreads
seo-title: Enabling multi-threaded file conversions
description: Découvrez comment activer les conversions de fichiers multithreads.
seo-description: Learn how to enable multi-threaded file conversions.
uuid: 830c78aa-4f68-4e01-8b24-69a0275689c7
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_pdf_generator
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 85d655bb-1b6b-4b4d-ae39-eca3ef9b7fd7
feature: PDF Generator
exl-id: f0441588-7c16-40ab-841f-e89576a0d292
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '905'
ht-degree: 10%

---

# Activation des conversions de fichiers multithreads {#enabling-multi-threaded-file-conversions}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

PDF Generator permet d’activer les conversions de fichiers multithreads pour certains types de fichiers. La conversion de fichiers multithreads améliore les performances de PDF Generator en lui permettant d’effectuer plusieurs conversions en même temps.

## Activation des conversions de fichiers multithreads pour les documents OpenOffice, Word et PowerPoint {#enabling-multi-threaded-file-conversions-for-openoffice-word-and-powerpoint-documents}

Par défaut, PDF Generator ne peut convertir qu’un seul document OpenOffice, Microsoft Word ou PowerPoint à la fois. Si vous activez les conversions multithreads, PDF Generator peut convertir plusieurs documents simultanément. PDF Generator lancera plusieurs instances d’OpenOffice ou de PDFMaker (utilisés pour effectuer les conversions Word et PowerPoint).

>[!NOTE]
>
>Les conversions de fichiers multithreads ne sont pas prises en charge avec Microsoft Word 2003 et PowerPoint 2003. Pour activer les conversions de fichiers multithreads, effectuez une mise à niveau vers Microsoft Word 2007 et PowerPoint 2007 ou Microsoft Word 2010 et PowerPoint 2010.

>[!NOTE]
>
>Les conversions de fichiers multithreads ne sont pas prises en charge avec Microsoft Excel, Microsoft Visio, Microsoft Project ou Microsoft Publisher.

Chaque instance d’OpenOffice ou de PDFMaker est lancée à l’aide d’un compte utilisateur distinct. Chaque compte utilisateur ajouté doit être un utilisateur valide disposant de droits d’administrateur sur l’ordinateur du serveur Forms. Dans un environnement organisé en grappe, le même ensemble d’utilisateurs doit être valide pour tous les noeuds de la grappe.

Sur la page Comptes d’utilisateurs d’Administration Console, vous pouvez spécifier les comptes d’utilisateurs à utiliser pour les conversions de fichiers multithreads. Vous pouvez ajouter des comptes, les supprimer ou modifier des mots de passe de compte. Si vous exécutez PDF Generator sous Windows Server 2003 ou Windows Server 2008, ajoutez au moins trois comptes d’utilisateurs disposant de droits d’administrateur.

Lors de l’ajout d’utilisateurs pour OpenOffice, Microsoft Word ou Microsoft PowerPoint sous Windows Server 2003 ou 2008, ou pour OpenOffice sous Linux ou Sun™ Solaris™, fermez les boîtes de dialogue d’activation initiale pour tous les utilisateurs.

### Ajouter le droit de remplacer le jeton de niveau processus {#add-the-right-to-replace-the-process-level-token}

Sur un système d’exploitation Windows, les comptes utilisateur administrateur utilisés pour la conversion de PDF (utilisateurs de PDFG) auront besoin de droits de jeton de niveau processus de remplacement. Vous pouvez ajouter ce droit à l’aide de l’éditeur de stratégie de groupe :

1. Dans le menu Démarrer de Windows, cliquez sur Exécuter, puis saisissez gpedit.msc.
1. Cliquez sur Stratégie d’ordinateur local > Configuration d’ordinateur > Paramètres Windows > Paramètres de sécurité > Stratégies locales > Attribution des droits utilisateur. Modifiez la variable *Remplacer un jeton de niveau processus* pour inclure le groupe Administrateurs.
1. Ajoutez l’utilisateur à l’entrée Remplacer un jeton de niveau processus .

### Configuration supplémentaire requise pour OpenOffice, Microsoft Word et Microsoft PowerPoint sous Windows Server 2008 {#additional-configuration-required-for-openoffice-microsoft-word-and-microsoft-powerpoint-on-windows-server-2008}

Si vous exécutez OpenOffice, Microsoft Word ou Microsoft PowerPoint sous Windows Server 2008, désactivez l’UAC pour chaque utilisateur ajouté.

1. Cliquez sur Panneau de Contrôle > Comptes d’utilisateurs > Activer ou désactiver le contrôle des comptes d’utilisateurs.
1. Désélectionnez la case &quot;Utiliser le contrôle de compte d’utilisateur (UAC) pour vous aider à protéger votre ordinateur&quot; et cliquez sur OK.
1. Redémarrez l’ordinateur pour que les paramètres prennent effet.

### Configuration supplémentaire requise pour OpenOffice sous Linux ou Solaris {#additional-configuration-required-for-openoffice-on-linux-or-solaris}

1. Ajout de comptes d’utilisateurs. (Voir [Ajout d’un compte d’utilisateur](enabling-multi-threaded-file-conversions.md#add-a-user-account).)
1. Ensuite, vous apportez des modifications au fichier /etc/sudoers. L’autorisation par défaut pour ce fichier est 440. Définissez l’autorisation d’écriture pour ce fichier.
1. Ajoutez des entrées pour les utilisateurs supplémentaires (autres que l’administrateur exécutant le serveur Forms) dans le fichier /etc/sudoers. Par exemple, si vous exécutez AEM Forms en utilisant le nom d’utilisateur « Icadm » et un serveur appelé « myhost » et que vous souhaitez incarner les utilisateurs user1 et user2, ajoutez les entrées suivantes dans le fichier /etc/sudoers :

   ```as3
    lcadm myhost=(user1) NOPASSWD: ALL 
    lcadm myhost=(user2) NOPASSWD: ALL
   ```

   Cette configuration permet à lcadm d’exécuter n’importe quelle commande sur l’hôte &quot;myhost&quot; en tant qu’&quot;user1&quot; ou &quot;user2&quot; sans demander de mot de passe.

   >[!NOTE]
   >
   >Assurez-vous que vous avez attribué les rôles utilisateur système et utilisateur PDFG à &quot;user1&quot; et &quot;user2&quot; . Pour attribuer un rôle PDFG à un utilisateur, voir [Ajout d’un compte d’utilisateur](enabling-multi-threaded-file-conversions.md#add-a-user-account)

1. Toujours dans le fichier /etc/sudoers, recherchez et commentez cette ligne en ajoutant un signe dièse (#) au début de la ligne :

   ```as3
   Defaults requiretty
   ```

   Vous pouvez ainsi ajouter des utilisateurs Linux.

1. Remplacez l’autorisation pour le fichier etc/sudoers par 440.
1. Autorisez tous les utilisateurs ajoutés via l’option [Ajout d’un compte utilisateur](enabling-multi-threaded-file-conversions.md#add-a-user-account) à se connecter au serveur Forms. Par exemple, pour autoriser un utilisateur local nommé user1 à se connecter au serveur Forms, utilisez la commande suivante :

   `xhost +local:user1@`

   Pour plus d’informations, consultez la documentation sur les commandes xhost.

1. Redémarrez le serveur.

>[!NOTE]
>
>OpenOffice doit être installé dans un répertoire accessible à tous les utilisateurs de PDFG. Vous pouvez le vérifier en vous connectant en tant qu’utilisateur PDFG et en vérifiant si vous pouvez lancer OpenOffice sans problème.

### Ajout d’un compte d’utilisateur {#add-a-user-account}

1. Dans Administration Console, cliquez sur Services > Générateur de PDF > Comptes d’utilisateur.
1. Cliquez sur Ajouter et saisissez le nom et le mot de passe d’un utilisateur possédant des privilèges d’administrateur sur le serveur Forms. Si vous configurez des utilisateurs pour OpenOffice, fermez les boîtes de dialogue d’activation OpenOffice initiales.

   >[!NOTE]
   >
   >Si vous configurez des utilisateurs pour OpenOffice, le nombre d’instances d’OpenOffice ne peut pas être supérieur au nombre de comptes d’utilisateurs spécifié dans cette étape.

1. Redémarrez le serveur Forms.

### Suppression d’un utilisateur de la liste utilisée pour les conversions de fichiers multithreads {#remove-a-user-from-the-list-used-for-multi-threaded-file-conversions}

1. Dans Administration Console, cliquez sur Services > Générateur de PDF > Comptes d’utilisateur.
1. Cochez la case en regard de l’utilisateur à supprimer, puis cliquez sur Supprimer.
1. Sur la page de confirmation, cliquez sur Supprimer.
1. Redémarrez le serveur Forms.

### Modification du mot de passe d’un compte {#change-the-password-for-an-account}

1. Dans Administration Console, cliquez sur Services > Générateur de PDF > Comptes d’utilisateur.
1. Cliquez sur le nom d’utilisateur, puis saisissez et confirmez le nouveau mot de passe. Ce mot de passe doit correspondre au mot de passe système de l’utilisateur.
