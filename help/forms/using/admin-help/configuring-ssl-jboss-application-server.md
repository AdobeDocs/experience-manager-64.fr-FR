---
title: Configurer SSL pour JBoss Application Server
seo-title: Configuring SSL for JBoss Application Server
description: Découvrez comment configurer SSL pour JBoss Application Server.
seo-description: Learn how to configure SSL for JBoss Application Server.
uuid: 7c13cf00-ea89-4894-a4fc-aaeec7ae9f66
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_ssl
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: c187daa4-41b7-47dc-9669-d7120850cafd
exl-id: 1888b8c7-d077-4e54-b442-5df0ba557513
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '944'
ht-degree: 72%

---

# Configurer SSL pour JBoss Application Server {#configuring-ssl-for-jboss-application-server}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Pour configurer SSL sur JBoss Application Server, vous avez besoin d’informations d’identification SSL pour l’authentification. Vous pouvez utiliser l’outil Java keytool pour créer des informations d’identification ou demander et importer des informations d’identification à partir d’une autorité de certification (CA). Vous devez ensuite activer SSL sur JBoss.

Vous pouvez exécuter keytool en utilisant une seule commande qui comprend toutes les informations nécessaires à la création du fichier de stockage des clés.

Dans cette procédure :

* `[appserver root]` correspond au répertoire racine du serveur d’applications exécutant AEM Forms.
* `[type]` correspond à un nom de dossier qui varie selon le type d’installation réalisé.

## Création d’informations d’identification SSL {#create-an-ssl-credential}

1. Dans une invite de commande, accédez à *[JAVA HOME]*/bin et saisissez la commande suivante pour créer les informations d’identification et le fichier de stockage des clés :

   `keytool -genkey -dname "CN=`*Nom de l’hôte* `, OU=`*Nom du groupe* `, O=`*Nom de la société* `,L=`*Nom de la ville* `, S=`*État* `, C=`Code du pays&quot; `-alias "AEMForms Cert"` `-keyalg RSA -keypass`*mots_de_passe_clés* `-keystore`*nom_stockage_clés* `.keystore`

   >[!NOTE]
   >
   >Remplacez `[JAVA_HOME]` par le répertoire dans lequel le JDK est installé, puis remplacez le texte en italique par des valeurs correspondant à votre environnement. nom_hôte correspond au nom de domaine complet du serveur d’applications.

1. Saisissez le `keystore_password` lorsque vous êtes invité à saisir un mot de passe. Le mot de passe du fichier de stockage des clés et celui de la clé doivent être identiques.

   >[!NOTE]
   >
   >Le `keystore_password` *saisi à cette étape peut correspondre au mot de passe (mots_de_passe_clés) saisi à l’étape 1, ou être différent.*

1. Copiez le fichier *nom_stockage_clés*.keystore dans le répertoire `[appserver root]/server/[type]/conf` en saisissant l’une des commandes suivantes :

   * (Serveur unique Windows) `copy` `keystorename.keystore[appserver root]\standalone\configuration`
   * (Cluster de serveurs Windows) Copiez `keystorename.keystore[appserver root]\domain\configuration`
   * (Serveur unique Linux) `cp keystorename.keystore [appserver root]/standalone/configuration`
   * (Grappe de serveurs Linux) `cp <em>keystorename</em>.keystore<em>[appserver root]</em>/domain/configuration`


1. Exportez le fichier de certificat en exécutant la commande suivante :

   * (Serveur unique) `keytool -export -alias "AEMForms Cert" -file AEMForms_cert.cer -keystore [appserver root]/standalone/configuration/keystorename.keystore`
   * (Cluster de serveurs) `keytool -export -alias "AEMForms Cert" -file AEMForms_cert.cer -keystore [appserver root]/domain/configuration/keystorename.keystore`

1. Saisissez le *mot_de_passe_clés* lorsque vous êtes invité à saisir un mot de passe.
1. Copiez le fichier AEMForms_cert.cer dans le répertoire *[racine du serveur d’applications]\conf* en saisissant la commande suivante :

   * (Serveur unique Windows) `copy AEMForms_cert.cer [appserver root]\standalone\configuration`
   * (Grappe de serveurs Windows) `copy AEMForms_cert.cer [appserver root]\domain\configuration`
   * (Serveur unique Linux) `cp AEMForms _cert.cer [appserver root]\standalone\configuration`
   * (Grappe de serveurs Linux) `cp AEMForms _cert.cer [appserver root]\domain\configuration`

1. Affichez le contenu du certificat en exécutant la commande suivante :

   * `keytool -printcert -v -file [appserver root]\standalone\configuration\AEMForms_cert.cer`
   * `keytool -printcert -v -file [appserver root]\domain\configuration\AEMForms_cert.cer`

1. Le cas échéant, pour autoriser l’accès en écriture au fichier cacerts dans `[JAVA_HOME]\jre\lib\security`, procédez comme suit :

   * (Windows) Cliquez avec le bouton droit de la souris sur le fichier cacerts et sélectionnez Propriétés, puis l’attribut Lecture seule.
   * (Linux) Saisissez `chmod 777 cacerts`

1. Importez le certificat en saisissant la commande suivante :

   `keytool -import -alias “AEMForms Cert” -file`*AEMForms_cert* `.cer -keystore`*JAVA_HOME* `\jre\lib\security\cacerts`

1. Saisissez `changeit` comme mot de passe. Il s’agit du mot de passe par défaut d’une installation Java, mais l’administration système peut l’avoir modifié.
1. À l’invite `Trust this certificate? [no]` :, sasissez `yes`. La confirmation &quot;Le certificat a été ajouté au KeyStore&quot; s’affiche.
1. Si vous vous connectez via SSL depuis Workbench, installez le certificat sur l’ordinateur Workbench.
1. Dans un éditeur de texte, ouvrez les fichiers suivants pour les modifier :

   * Serveur unique : `[appserver root]`/standalone/configuration/lc_&lt;dbname/turnkey>.xml

   * Grappe de serveurs : `[appserver root]`/domain/configuration/host.xml

   * Grappe de serveurs : `[appserver root]`/domain/configuration/domain_&lt;dbname>.xml

1. 
   * **Pour un serveur unique,** ajoutez l’élément suivant dans le fichier lc_&lt;dbaname/tunkey>.xml après la section &lt;security-realms> :

   ```as3
   <security-realm name="SSLRealm">
   <server-identities>
   <ssl>
   <keystore path="C:/Adobe/Adobe_Experience_Manager_Forms/jboss/standalone/configuration/aemformses.keystore" keystore-password="changeit" alias="AEMformsCert" key-password="changeit"/>
   </ssl>
   </server-identities>
   </security-realm>
   ```

   Recherchez la section `<server>` située après le code suivant :

   `<http-listener name="default" socket-binding="http" redirect-socket="https" max-post-size="104857600"/>`

   Ajoutez ce qui suit à la section &lt;server> située après le code ci-dessus :

   ```
   <https-listener name="default-secure" socket-binding="https" security-realm="SSLRealm"/>
   ```

   * **Pour une grappe de serveurs,** ajoutez ce qui suit dans [racine du serveur d’applications]\domain\configuration\host.xml sur tous les nœuds, après la section &lt;security-realms> :

   ```as3
   <security-realm name="SSLRealm">
   <server-identities>
   <ssl>
   <keystore path="C:/Adobe/Adobe_Experience_Manager_Forms/jboss/standalone/configuration/aemformses.keystore" keystore-password="changeit" alias="AEMForms Cert" key-password="changeit"/>
   </ssl>
   </server-identities>
   </security-realm>
   ```

   Sur le nœud principal de la grappe de serveurs, dans [racine du serveur d’applications]\domain\configuration\domain_ &lt;dbname>.xml, recherchez la section &lt;server> située après le code suivant :

   `<http-listener name="default" socket-binding="http" redirect-socket="https" max-post-size="104857600"/>`

   Ajoutez ce qui suit à la section &lt;server> située après le code ci-dessus :

   ```
   <https-listener name="default-secure" socket-binding="https" security-realm="SSLRealm"/>
   ```

1. Remplacez la valeur des attributs `keystoreFile` et `keystorePass` par le mot de passe du fichier de stockage des clés que vous avez spécifié lors de la création dudit fichier.
1. Redémarrez le serveur d’applications :

   * Pour les installations clé en main :

      * Dans le Panneau de Contrôle Windows, cliquez sur Outils d’administration, puis sur Services.
      * Sélectionnez JBoss pour Adobe Experience Manager forms.
      * Sélectionnez Action > Arrêter.
      * Attendez que l’état du service s’affiche comme arrêté.
      * Sélectionnez Action > Démarrer.
   * Pour les installations de JBoss configurées manuellement ou préconfigurées par Adobe :

      * À partir d’une invite de commande, accédez à *`[appserver root]`*\bin.
      * Arrêtez le serveur en saisissant la commande suivante :

         * (Windows) `shutdown.bat -S`
         * (Linux) `./shutdown.sh -S`
      * Patientez jusqu’à ce que le processus JBoss soit complètement arrêté (lorsque le processus JBoss renvoie le contrôle au terminal dans lequel il a été démarré).
      * Démarrez le serveur en saisissant la commande suivante :

         * (Windows) `run.bat -c <profile>`
         * (Linux) `./run.sh -c <profile>`



1. Pour accéder à la console d’administration en utilisant SSL, saisissez `https://[host name]:[port]/adminui` dans un navigateur Web :

   Le port SSL par défaut pour JBoss est 8443. À partir de là, spécifiez ce port lors de l’accès à AEM forms.

## Demande d’informations d’identification auprès d’une autorité de certification {#request-a-credential-from-a-ca}

1. Dans une invite de commande, accédez à *[JAVA_HOME]*/bin et saisissez la commande suivante pour créer le fichier de stockage des clés et la clé :

   `keytool -genkey -dname "CN=`*Nom de l’hôte* `, OU=`*Nom du groupe* `, O=`*Nom de la société* `, L=`*Nom de la ville* `, S=`*État* `, C=`*Code du pays*&quot; `-alias "AEMForms Cert"` `-keyalg RSA -keypass`-*mot_de_passe_clés* `-keystore`*nom_stockage_clé* `.keystore`

   >[!NOTE]
   >
   >Remplacez *`[JAVA_HOME]`* par le répertoire dans lequel le JDK est installé, puis remplacez le texte en italique par des valeurs correspondant à votre environnement.

1. Saisissez le commande suivante afin de générer une demande de certificat à envoyer à l’autorité de certification :

   `keytool -certreq -alias` « AEMForms Cert » `-keystore`*nom_stockage_clés* `.keystore -file`*AEMFormsRequest.csr*

1. Une fois votre demande de fichier de certificat remplie, procédez comme suit.

## Utilisation d’informations d’identification obtenues auprès d’une autorité de certification pour activer SSL {#use-a-credential-obtained-from-a-ca-to-enable-ssl}

1. Dans une invite de commande, accédez à *`[JAVA HOME]`*/bin et saisissez la commande suivante pour importer le certificat racine de l’autorité de certification avec laquelle le CSR a été signé :

   `keytool -import -trustcacerts -file` rootcert.pem -keystore ` keystorename.keystore -alias root`

   Si le certificat racine ne figure pas dans le navigateur, importez-le également à cet endroit.

   >[!NOTE]
   >
   >Remplacez *`[JAVA_HOME]`par le répertoire dans lequel le JDK est installé, puis remplacez le texte en italique par des valeurs correspondant à votre environnement.*

1. Dans une invite de commande, accédez à *`[JAVA HOME]`*/bin et saisissez la commande suivante pour importer les informations d’identification dans le fichier de stockage des clés :

   `keytool -import -trustcacerts -file`*nom_certificat_CA* `.crt -keystore`*nom_stockage_clés* `.keystore`

   >[!NOTE]
   >
   >* Remplacez `[JAVA_HOME]` par le répertoire dans lequel le JDK est installé, puis remplacez le texte en italique par des valeurs correspondant à votre environnement.
   >* Le certificat signé par l’autorité de certification importé remplacera un certificat public autosigné s’il existe.


1. Suivez les étapes 13 à 18 de la section Création d’informations d’identification SSL.
