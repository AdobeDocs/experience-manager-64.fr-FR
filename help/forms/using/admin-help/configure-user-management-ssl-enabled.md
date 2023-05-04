---
title: Configuration de User Management pour un serveur LDAP compatible SSL
seo-title: Configure User Management for an SSL-enabled LDAP server
description: Découvrez comment configurer User Management pour un serveur LDAP SSL afin de permettre le fonctionnement correct de la synchronisation sur LDAPS.
seo-description: Learn how  to configure User Management for an SSL-enabled LDAP server to enable synchronization to work properly over LDAPS.
uuid: 4b3f8ac7-fa38-4adf-a851-82d55fe431fe
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_user_management
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: e6e7e2fa-579d-4b36-8598-6ced469a94b1
exl-id: 9ed22c75-bce7-4d26-a4cd-a58e41e5068e
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 29%

---

# Configurer User Management pour un serveur LDAP compatible SSL {#configure-user-management-for-an-ssl-enabled-ldap-server}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Pour que la synchronisation fonctionne correctement sur LDAPS, les certificats LDAP émis par l’autorité de certification doivent être présents dans l’environnement d’exécution Java (JRE) du serveur d’applications. Importez le certificat dans le fichier cacerts de l’environnement JRE du serveur d’applications, fichier se trouvant généralement dans le répertoire *[JAVA_HOME]*/jre/lib/security/cacerts.

1. Activez SSL sur le serveur d’annuaire. Pour plus d’informations, consultez la documentation fournie par le fournisseur de votre répertoire.
1. Exportez un certificat client à partir du serveur d’annuaire.
1. Utilisez le programme keytool pour importer le fichier du certificat client dans la boutique de certificats de la machine virtuelle Java (JVM™) par défaut du serveur d’applications d’AEM forms. La procédure pour cette tâche varie en fonction de la JVM et des chemins d’installation du client. Par exemple, si vous utilisez BEA WebLogic Server avec JDK 1.5, saisissez ce texte à partir d’une invite de commande :

   `keytool -import -alias`*alias* `-file certificatename -keystore C:\bea\jdk15_04\jre\lib\security\cacerts`

1. A l’invite, spécifiez votre mot de passe (pour Java, le mot de passe par défaut est `changeit`). Une fois le certificat importé, un message vous confirme la réussite de l’opération.
1. Lorsque vous y êtes invité, saisissez`Yes` pour approuver le certificat.
1. Activez SSL dans User Management et, lors de la configuration des paramètres d’annuaire, sélectionnez Oui pour l’option SSL et modifiez le paramètre de port en conséquence. Le numéro de port par défaut est 636.

>[!NOTE]
>
>Si vous rencontrez des problèmes lors de l’utilisation de SSL, utilisez un navigateur LDAP pour vérifier s’il peut accéder au système LDAP lors de l’utilisation de SSL. Si le navigateur LDAP ne peut pas accéder à , votre certificat ou serveur d’applications n’est pas configuré correctement. Si le navigateur LDAP fonctionne correctement et que vous rencontrez toujours des problèmes, User Management n’est pas configuré correctement.
