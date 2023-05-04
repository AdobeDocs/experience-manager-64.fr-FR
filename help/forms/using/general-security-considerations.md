---
title: Considérations générales sur la sécurité pour AEM Forms sur JEE
seo-title: General Security Considerations for AEM Forms on JEE
description: Découvrez comment préparer le renforcement de votre environnement AEM Forms sur JEE.
seo-description: Learn how to prepare for hardening your AEM Forms on JEE environment.
uuid: c5f6ffc7-b987-4541-ab60-e97b4ff5b2a4
content-type: reference
topic-tags: Security
products: SG_EXPERIENCEMANAGER/6.4
discoiquuid: 38132225-ecae-4887-8f3d-0b3845059130
role: Admin
exl-id: cde40670-ce9d-4b96-92d3-9e56cb15bdce
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1127'
ht-degree: 51%

---

# Considérations générales sur la sécurité pour AEM Forms sur JEE {#general-security-considerations-for-aem-forms-on-jee}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Découvrez comment préparer le renforcement de votre environnement AEM Forms sur JEE.

Cet article fournit des informations d’introduction qui vous aideront à préparer le renforcement de votre environnement AEM Forms. Elle comprend des informations prérequises sur la sécurité d’AEM Forms on JEE, du système d’exploitation, du serveur d’applications et de la base de données. Passez en revue ces informations avant de continuer à verrouiller votre environnement.

## Informations de sécurité spécifiques au fournisseur {#vendor-specific-security-information}

Cette section contient des informations relatives à la sécurité sur les systèmes d’exploitation, les serveurs d’applications et les bases de données intégrés à votre solution AEM Forms on JEE.

Suivez les liens de cette section pour trouver des informations de sécurité spécifiques à un fournisseur pour votre système d’exploitation, votre base de données et votre serveur d’applications.

### Informations sur la sécurité du système d’exploitation {#operating-system-security-information}

Lorsque vous sécurisez votre système d’exploitation, veillez à implémenter soigneusement les mesures indiquées par le revendeur de votre système d’exploitation, parmi lesquelles :

* Définition et contrôle des utilisateurs, des rôles et des privilèges
* Surveillance des journaux et des journaux d’audit
* Suppression des services et applications inutiles
* Sauvegarde de fichiers

Pour plus de détails sur la sécurité des systèmes d’exploitation pris en charge par AEM Forms sur JEE, consultez les ressources du tableau suivant :

<table> 
 <thead> 
  <tr> 
   <th><p>Système d’exploitation</p> </th> 
   <th><p>Ressource de sécurité</p> </th> 
  </tr> 
 </thead> 
 <tbody>
  <tr> 
   <td><p>IBM® AIX® 7.2</p> </td> 
   <td><p><a href="https://www.ibm.com/support/knowledgecenter/ssw_aix_72/com.ibm.aix.security/security-kickoff.htm" target="_blank">Avantages de la sécurité IBM AIX</a></p> </td> 
  </tr> 
  <tr> 
   <td><p>Microsoft Windows Server® 2012 </p> </td> 
   <td><p><a href="https://blogs.technet.com/b/secguide/archive/2014/08/13/security-baselines-for-windows-8-1-windows-server-2012-r2-and-internet-explorer-11-final.aspx" target="_blank">Guide de sécurité Windows Server 2012</a></p> </td> 
  </tr> 
  <tr> 
   <td><p>Microsoft Windows Server® 2016 </p> </td> 
   <td><p><a href="https://cloudblogs.microsoft.com/windowsserver/2017/08/22/now-available-windows-server-2016-security-guide/">Guide de sécurité Windows Server 2016</a></p> </td> 
  </tr> 
  <tr> 
   <td><p>Red Hat® Linux® AP ou ES</p> </td> 
   <td><p><a href="https://access.redhat.com/documentation/fr-fr/red_hat_enterprise_linux/7/pdf/security_guide/red_hat_enterprise_linux-7-security_guide-fr-fr.pdf" target="_blank">Guide de sécurité Linux pour Red Hat Enterprise</a></p> </td> 
  </tr> 
  <tr> 
   <td><p>Sun Solaris 11</p> </td> 
   <td><p><a href="https://docs.oracle.com/cd/E53394_01/html/E54807/index.html" target="_blank">Recommandations relatives à la sécurité et au renforcement</a></p> </td> 
  </tr> 
  <tr> 
   <td>Oracle Linux® 7 Update 3</td> 
   <td><a href="https://docs.oracle.com/cd/E52668_01/E54670/E54670.pdf" target="_blank">Guide de sécurité pour la version 7</a><br /> </td> 
  </tr> 
  <tr> 
   <td>CentOS 7<sup> </sup></td> 
   <td><a href="https://wiki.centos.org/HowTos/OS_Protection" target="_blank">Documentation sur la protection</a></td> 
  </tr> 
 </tbody> 
</table>

### Informations sur la sécurité des serveurs d’applications {#application-server-security-information}

Lorsque vous sécurisez votre serveur d’applications, veiller à implémenter soigneusement les mesures indiquées par le revendeur de votre serveur, parmi lesquelles :

* Utilisation d’un nom d’utilisateur administrateur non évident
* Désactivation des services inutiles
* Sécurisation du gestionnaire de console
* Activation des cookies sécurisés
* Fermeture des ports inutiles
* Limitation des clients par adresses ou domaines IP
* Utilisation de Java™ Security Manager pour limiter les privilèges par programmation

Pour plus d’informations sur la sécurité des serveurs d’applications pris en charge par AEM Forms on JEE, reportez-vous aux ressources indiquées dans le tableau ci-dessous.

<table> 
 <thead> 
  <tr> 
   <th><p>Serveur d’applications</p> </th> 
   <th><p>Ressource de sécurité</p> </th> 
  </tr> 
 </thead> 
 <tbody>
  <tr> 
   <td><p>Oracle WebLogic®</p> </td> 
   <td><p>Recherchez « Understanding WebLogic Security » sur <a href="https://download.oracle.com/docs/">https://download.oracle.com/docs/</a>.</p> </td> 
  </tr> 
  <tr> 
   <td><p>IBM WebSphere®</p> </td> 
   <td><p><a href="https://www.ibm.com/developerworks/websphere/zones/was/security/" target="_blank">Sécurisation des applications dans leur environnement</a></p> </td> 
  </tr> 
  <tr> 
   <td><p>Red Hat® JBoss®</p> </td> 
   <td><p><a href="https://docs.jboss.org/author/display/AS7/Security+subsystem+configuration">Configuration du sous-système de sécurité</a></p> </td> 
  </tr> 
 </tbody> 
</table>

### Informations sur la sécurité des bases de données {#database-security-information}

Lorsque vous sécurisez votre base de données, veillez à implémenter soigneusement les mesures indiquées par le revendeur de votre base de données, parmi lesquelles :

* Restriction des opérations avec des listes de contrôle d’accès (ACL)
* Utilisation de ports non standard
* Masquer la base de données derrière un pare-feu
* Chiffrement des données sensibles avant leur écriture dans la base de données (voir la documentation du fabricant de la base de données)

Pour plus d’informations sur la sécurité des bases de données prises en charge par AEM Forms on JEE, reportez-vous aux ressources indiquées dans le tableau ci-dessous.

<table> 
 <thead> 
  <tr> 
   <th><p>Base de données</p> </th> 
   <th><p>Ressource de sécurité</p> </th> 
  </tr> 
 </thead> 
 <tbody>
  <tr> 
   <td><p>IBM DB2® 11.1</p> </td> 
   <td><p><a href="https://www.ibm.com/fr-fr/analytics/db2">Bibliothèque de la famille de produits DB2</a></p> </td> 
  </tr> 
  <tr> 
   <td><p>Microsoft SQL Server 2016</p> </td> 
   <td>Recherchez « SQL Server 2016 : sécurité » sur le Web.</td> 
  </tr> 
  <tr> 
   <td><p>MySQL 5</p> </td> 
   <td><p><a href="https://dev.mysql.com/doc/refman/5.0/en/security.html">MySQL 5.0 General Security Issues</a></p> <p><a href="https://dev.mysql.com/doc/refman/5.1/en/security.html">MySQL 5.1 General Security Issues</a></p> </td> 
  </tr> 
  <tr> 
   <td><p>Oracle® 12c</p> </td> 
   <td><p>Reportez-vous au chapitre Security dans <a href="https://docs.oracle.com/database/121/TDPSG/GUID-6E2F4E53-5D87-4FCD-9C9C-6792217D7014.htm#TDPSG94426" target="_blank">Oracle 12g Documentation</a></p> </td> 
  </tr> 
 </tbody> 
</table>

Ce tableau décrit les ports par défaut devant être ouverts pendant le processus de configuration d’AEM Forms on JEE. Si vous vous connectez via https, ajustez les informations de port et les adresses IP en conséquence. Pour plus d’informations sur la configuration des ports, voir *Installation et déploiement d’AEM Forms on JEE* pour votre serveur d’applications.

<table> 
 <thead> 
  <tr> 
   <th><p>Produit ou service</p> </th> 
   <th><p>Numéro de port</p> </th> 
  </tr> 
 </thead> 
 <tbody>
  <tr> 
   <td><p>JBoss </p> </td> 
   <td><p>8080</p> </td> 
  </tr> 
  <tr> 
   <td><p>WebLo gic</p> </td> 
   <td><p>7001</p> </td> 
  </tr> 
  <tr> 
   <td><p>Serveur géré WebLogic</p> </td> 
   <td><p>Défini par l’administrateur lors de la configuration</p> </td> 
  </tr> 
  <tr> 
   <td><p>WebSphere</p> </td> 
   <td><p>9060, si la sécurité globale est activée, la valeur de port SSL par défaut est 9043.</p> <p>9080</p> </td> 
  </tr> 
  <tr> 
   <td><p>Serveur BAM</p> </td> 
   <td><p>7001</p> </td> 
  </tr> 
  <tr> 
   <td><p>SOAP</p> </td> 
   <td><p>8880</p> </td> 
  </tr> 
  <tr> 
   <td><p>MySQL</p> </td> 
   <td><p>3306</p> </td> 
  </tr> 
  <tr> 
   <td><p>Oracle</p> </td> 
   <td><p>1521</p> </td> 
  </tr> 
  <tr> 
   <td><p>DB2</p> </td> 
   <td><p>50 000</p> </td> 
  </tr> 
  <tr> 
   <td><p>SQL Server</p> </td> 
   <td><p>1433</p> </td> 
  </tr> 
  <tr> 
   <td><p>LDAP</p> </td> 
   <td><p>port sur lequel le serveur LDAP est en cours d’exécution. Le port par défaut est généralement 389. Cependant, si vous sélectionnez l’option SSL, le port par défaut est généralement 636. Vérifiez auprès de votre administrateur LDAP le numéro de port à utiliser.</p> </td> 
  </tr> 
 </tbody> 
</table>

### Configuration de JBoss pour utiliser un port HTTP autre que celui par défaut {#configuring-jboss-to-use-a-non-default-http-port}

JBoss Application Server utilise 8080 comme port HTTP par défaut. JBoss dispose également des ports 8180, 8280 et 8380 préconfigurés, qui sont commentés dans le fichier jboss-service.xml. Si votre ordinateur comporte déjà une application utilisant ce port, modifiez le port utilisé par AEM Forms on JEE en procédant comme suit :

1. Ouvrez le fichier suivant pour le modifier :

   Installation sur un serveur : [racine JBoss]/standalone/configuration/standalone.xml

   Installations de cluster : [racine JBoss]/domain/configuration/domain.xml

1. Modifiez la valeur de lʼattribut **port** dans la balise **&lt;socket-binding>** vers un numéro de port personnalisé. Dans lʼexemple suivant, le port 8090 est utilisé :

   &lt;socket-binding name=&quot;http&quot; port=&quot;8090&quot;/>

1. Enregistrez et fermez le fichier.
1. Redémarrez le serveur d’applications JBoss.

## Considérations relatives à la sécurité d’AEM Forms on JEE {#aem-forms-on-jee-security-considerations}

Cette section décrit certains problèmes de sécurité spécifiques à AEM Forms on JEE que vous devez connaître.

### Informations d’identification de messagerie non chiffrées dans la base de données {#email-credentials-not-encrypted-in-database}

Les informations d’identification stockées par les applications ne sont pas chiffrées avant d’être stockées dans la base de données d’AEM Forms on JEE. Lorsque vous configurez un point de terminaison de service pour utiliser le courrier électronique, les informations de mot de passe utilisées dans le cadre de cette configuration de point de terminaison ne sont pas chiffrées lorsqu’elles sont stockées dans la base de données.

### Contenu sensible pour les Rights Management dans la base de données {#sensitive-content-for-rights-management-in-the-database}

AEM Forms sur JEE utilise sa base de données pour stocker des informations clés sur des documents sensibles et d’autres données cryptographiques utilisées pour les documents de stratégie. Le fait de sécuriser la base de données contre les intrusions contribue à la protection de ces informations sensibles.

### Mot de passe en texte clair {#password-in-clear-text-format-in-adobe-ds-xml}

Le serveur d’applications utilisé pour exécuter AEM Forms sur JEE nécessite sa propre configuration pour accéder à votre base de données via une source de données configurée sur le serveur d’applications. Veillez à ce que votre serveur d’applications n’expose pas le mot de passe de votre base de données en texte lisible dans le fichier de configuration de sa source de données.

Le fichier lc_[database].xml ne doit pas contenir de mot de passe en texte clair. Consultez le revendeur de votre serveur d’applications pour savoir comment chiffrer ces mots de passe pour votre serveur d’applications.

>[!NOTE]
>
>Le programme d’installation clé en main d’AEM Forms on JEE JBoss chiffre le mot de passe de la base de données.

IBM WebSphere Application Server et Oracle WebLogic Server peuvent chiffrer par défaut les mots de passe des sources de données. Vérifiez ce point dans la documentation de votre serveur d’applications.

### Protection de la clé privée stockée dans Trust Store {#protecting-the-private-key-stored-in-trust-store}

Les clés privées ou les informations d’identification importées dans Trust Store sont stockées dans la base de données d’AEM Forms on JEE. Prenez des mesures de sécurité appropriées pour sécuriser la base de données et limiter l’accès aux seuls administrateurs indiqués.
