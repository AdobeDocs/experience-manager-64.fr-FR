---
title: Configuration du mot de passe de liaison LDAP
seo-title: Configure the LDAP bind password
description: 'Découvrez comment configurer le champ du mot de passe de liaison avant d’importer le fichier de configuration dans un autre système. '
seo-description: Learn how to configure the bind password field before you import the configuration file into another system.
uuid: 1ab1907c-8b55-4b6f-bd5b-49f22d78b8a8
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_user_management
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 165b3950-b03f-4848-8361-ffb0a26d2658
exl-id: eaa2c889-d116-4209-9063-0c0b32dd8849
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 100%

---

# Configuration du mot de passe de liaison LDAP{#configure-the-ldap-bind-password}

Pour éviter les risques de sécurité, le champ du mot de passe de liaison n’est pas configuré dans le fichier de configuration (config.xml) exporté. Avant d’importer ce fichier dans un autre système, veillez à configurer ce mot de passe, qui remplace le mot de passe défini dans la base de données. Un mot de passe null ne remplace pas un mot de passe non null existant.

1. Dans Administration Console, cliquez sur Paramètres > Gestion des utilisateurs > Configuration > Importer et exporter des fichiers de configuration.
1. Pour exporter le paramètre de configuration en cours dans un fichier, cliquez sur Exporter, puis enregistrez le fichier de configuration dans un autre emplacement.
1. Dans le fichier, recherchez le nœud `Domains` > *[Votre nom de domaine]* > `DirectoryConfigs` > `LDAPGroupConfig`. Par exemple :

   ```as3
    <node name="LDAPGroupConfig"> 
        <map> 
            <entry key="bindanonymously" value="false" />  
            <entry key="basedn" value="dc=corp,dc=adobe,dc=com" />  
            <entry key="batchSize" value="200" />  
            <entry key="binduser" value="cn=Directory Manager" />  
            <entry key="bindpassword" value="" /> 
        </map>
   ```

   Saisissez une valeur pour `bindpassword` et enregistrez vos modifications.

1. Dans le fichier, recherchez le nœud `Domains` > *[Votre nom de domaine]* > `DirectoryConfigs` > `LDAPGroupConfig` > `LDAPUserConfig`. Par exemple :

   ```as3
    <node name="LDAPUserConfig"> 
        <map> 
            <entry key="bindanonymously" value="false" />  
            <entry key="batchSize" value="200" />  
            <entry key="basedn" value="dc=corp,dc=adobe,dc=com" />  
            <entry key="bindpassword" value="" /> 
            <entry key="binduser" value="cn=Directory Manager" />  
        </map>
   ```

   Saisissez une valeur pour `bindpassword` et enregistrez vos modifications.

1. Pour importer le fichier mis à jour, dans User Management, cliquez sur Configuration > Importer et exporter des fichiers de configuration.
1. Cliquez sur Parcourir pour trouver le fichier, puis sur Importer et enfin sur OK.
