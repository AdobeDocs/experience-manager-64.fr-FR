---
title: Document Security | Gestion des données utilisateur
seo-title: Document Security | Handling user data
description: AEM Forms Document Security vous permet de créer, stocker et appliquer facilement des paramètres de sécurité prédéfinis à vos documents. Cela garantit que seuls les utilisateurs autorisés peuvent utiliser les documents. Découvrez comment Document Security organise les données dans les tables de base de données, accède aux données Document Security et les exporte pour les utilisateurs dans les bases de données et, si nécessaire, supprimez-les définitivement.
seo-description: AEM Forms document security allows you to create, store, and apply predefined security settings to your documents. It ensures that only authorized users can use the documents. Learn how document security organizes data in database tables, access and export document security data for users in the databases, and if required, delete it permanently.
uuid: 1624a465-8b0c-4347-a53f-1118bfa6e18f
topic-tags: grdp
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 898268cb-4426-421f-8f63-d75bd85cb57f
role: Admin
exl-id: eeffd886-8955-46eb-aa6d-dd4da5e8570c
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1032'
ht-degree: 57%

---

# Document Security | Gestion des données utilisateur {#document-security-handling-user-data}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

AEM Forms Document Security vous permet de créer, stocker et appliquer facilement des paramètres de sécurité prédéfinis à vos documents. Cela garantit que seuls les utilisateurs autorisés peuvent utiliser les documents. Vous pouvez protéger des documents à l’aide de stratégies. Une stratégie est un ensemble d’informations qui inclut des paramètres de sécurité et une liste d’utilisateurs autorisés. Vous pouvez appliquer une stratégie à un ou plusieurs documents et autoriser les utilisateurs ajoutés à la gestion des utilisateurs d’AEM Forms JEE.

<!-- Fix broken link For more information about how document security works, see AEM Forms JEE administration help. -->

## Données utilisateur et stockage de données {#user-data-and-data-stores}

Document Security stocke les stratégies et les données relatives aux documents protégés, y compris les données utilisateur dans une base de données, comme MySQL, Oracle, MS SQL Server et IBM DB2. En outre, les données pour les utilisateurs autorisés dans une stratégie stockée dans la gestion des utilisateurs. Pour plus d’informations sur les données stockées dans User Management, consultez la section [Forms User Management : gérer les données utilisateur](/help/forms/using/user-management-handling-user-data.md).

Le tableau suivant indique comment Document Security organise les données dans les tables de base de données.

<table> 
 <tbody> 
  <tr> 
   <td>Table de base de données</td> 
   <td>Description</td> 
  </tr> 
  <tr> 
   <td><code>EdcPrincipalKeyEntity</code></td> 
   <td>Stocke des informations sur les clés principales des utilisateurs. Les clés sont utilisées dans les processus Document Security hors ligne.</td> 
  </tr> 
  <tr> 
   <td><code>EdcAuditEntity</code></td> 
   <td>Stocke des informations sur les événements de contrôle tels que les événements utilisateur, les événements de document et les événements de stratégie.</td> 
  </tr> 
  <tr> 
   <td><p><code>EdcLicenseEntity</code></p> </td> 
   <td>Stocke l’enregistrement d’un document protégé. Il stocke les détails de la licence pour chaque document protégé.</td> 
  </tr> 
  <tr> 
   <td><p><code>EdcDocumentEntity</code></p> </td> 
   <td>Stocke le nom du document pour chaque licence créée dans le système.</td> 
  </tr> 
  <tr> 
   <td><p><code>EdcRevokationEntity</code></p> </td> 
   <td>Stocke des informations sur la révocation et la restauration de documents protégés.</td> 
  </tr> 
  <tr> 
   <td><code>EdcMyPolicyListEntity</code></td> 
   <td>Stocke des informations sur les utilisateurs qui peuvent créer des stratégies personnelles qui apparaissent sous l’onglet Mes stratégies sur la page Stratégies. </td> 
  </tr> 
  <tr> 
   <td><code>EdcPolicyEntity</code></td> 
   <td>Stocke des informations sur les stratégies. Chaque stratégie correspond à une ligne du tableau.</td> 
  </tr> 
  <tr> 
   <td><code>EdcPolicyXmlEntity</code></td> 
   <td>Stocke des fichiers XML pour les stratégies actives. Une stratégie XML<sup> </sup> contient des références aux identifiants principaux des utilisateurs associés à la stratégie. La stratégie XML est stockée en tant qu’objet Blob.</td> 
  </tr> 
  <tr> 
   <td><code>EdcPolicyArchiveEntity</code></td> 
   <td>Stocke des informations sur les stratégies archivées. Une stratégie archivée contient sa stratégie XML enregistrée sous la forme d’un objet Blob.</td> 
  </tr> 
  <tr> 
   <td><p><code>EdcPolicySetPrincipalEntity</code></p> <p><code>EdcPolicySetPrincipalEnt</code> (bases de données Oracle et MS SQL)</p> </td> 
   <td>Stocke le mappage entre le jeu de stratégies et les utilisateurs.</td> 
  </tr> 
  <tr> 
   <td><code>EdcInvitedUserEntity</code></td> 
   <td>Stocke des informations sur l’utilisateur invité.</td> 
  </tr> 
 </tbody> 
</table>

## Accès et suppression des données utilisateur {#access-and-delete-user-data}

Vous pouvez accéder aux données Document Security et les exporter pour les utilisateurs dans les bases de données. Si nécessaire, supprimez-les définitivement.

Pour exporter ou supprimer des données utilisateur d’une base de données, vous devez vous connecter à la base de données à l’aide d’un client de base de données et rechercher l’identifiant principal en fonction de certaines informations d’identification personnelle de l’utilisateur. Par exemple, pour récupérer l’ID principal d’un utilisateur à l’aide d’un ID de connexion, exécutez la commande `select` suivante sur la base de données.

Dans la commande `select`, remplacez `<user_login_id>` par l’ID de connexion de l’utilisateur dont vous souhaitez récupérer l’ID principal depuis le tableau de la base de données `EdcPrincipalUserEntity`.

```sql
select refprincipalid from EdcPrincipalUserEntity where uidstring = <user_login_id>
```

Une fois que vous connaissez l’ID principal, vous pouvez exporter ou supprimer les données utilisateur.

### Exportation des données utilisateur {#export-user-data}

Exécutez les commandes de base de données suivantes pour exporter les données utilisateur d’un ID principal à partir des tables de base de données. Dans la commande `select`, remplacez `<principal_id>` par l’ID principal de l’utilisateur dont vous souhaitez exporter les données.

>[!NOTE]
>
>Les commandes suivantes utilisent des noms de tables de base de données dans les bases de données MySQL et IBM DB2. Lors de l’exécution de ces commandes sur les bases de données Oracle et MS SQL, remplacez `EdcPolicySetPrincipalEntity` par `EdcPolicySetPrincipalEnt` dans les commandes.

```sql
Select * from EdcPrincipalKeyEntity where principalid = '<principal_id>';

Select * from EdcLicenseEntity where publisherId = '<principal_id>';

Select * from EdcDocumentEntity where id in (Select documentid from EdcLicenseEntity where publisherId = '<principal_id>');

Select * from EdcRevokationEntity where licenseid in (Select id from EdcLicenseEntity where publisherId = '<principal_id>');

Select * from EdcMyPolicyListEntity where principalId = '<principal_id>';

Select * from edcpolicyentity where policyownerId = '<principal_id>';

Select * from edcpolicyxmlentity where policyidref in (Select id from edcpolicyentity where policyownerId = '<principal_id>');

Select * from edcpolicyarchiveentity where policyownerId = '<principal_id>';

Select * from edcpolicysetprincipalentity where principalId = '<principal_id>';

Select * from edcinviteduserentity where principalId = '<principal_id>';
```

>[!NOTE]
>
>Pour exporter des données à partir du tableau `EdcAuditEntity`, utilisez l’API [EventManager.exportEvents](https://helpx.adobe.com/experience-manager/6-4/forms/ProgramLC/javadoc/index.html?com/adobe/livecycle/rightsmanagement/client/EventManager.html) qui utilise [EventSearchFilter](https://helpx.adobe.com/experience-manager/6-4/forms/ProgramLC/javadoc/com/adobe/livecycle/rightsmanagement/client/infomodel/EventSearchFilter.html) en tant que paramètre pour exporter les données de contrôle en fonction de `principalId`, `policyId` ou `licenseId`.

Pour obtenir des informations complètes sur un utilisateur du système, vous devez accéder et exporter les données de la base de données User Management. Pour plus d’informations, reportez-vous à la section [Forms UserManagement : gérer les données utilisateur](/help/forms/using/user-management-handling-user-data.md).

### Suppression de données utilisateur {#delete-user-data}

Procédez comme suit pour supprimer les données Document Security d’un ID principal des tables de base de données.

1. Arrêtez le serveur AEM Forms.
1. Exécutez les commandes de base de données suivantes pour supprimer les données de l’ID principal des tables de base de données pour Document Security. Dans la commande `Delete`, remplacez `<principal_id>` par l’ID principal de l’utilisateur dont vous souhaitez supprimer les données.

   ```sql
   Delete from EdcPrincipalKeyEntity where principalid = '<principal_id>';
   
   Delete from EdcMyPolicyListEntity where principalId = '<principal_id>';
   
   Delete from edcpolicyarchiveentity where policyownerId = '<principal_id>';
   
   Delete from edcpolicysetprincipalentity where principalId = '<principal_id>';
   
   Delete from edcinviteduserentity where principalId = '<principal_id>';
   ```

   >[!NOTE]
   >
   >Pour supprimer des données à partir du tableau `EdcAuditEntity`, utilisez l’API [EventManager.deleteEvents](https://helpx.adobe.com/experience-manager/6-4/forms/ProgramLC/javadoc/index.html?com/adobe/livecycle/rightsmanagement/client/EventManager.html) qui utilise [EventSearchFilter](https://helpx.adobe.com/experience-manager/6-4/forms/ProgramLC/javadoc/com/adobe/livecycle/rightsmanagement/client/infomodel/EventSearchFilter.html) en tant que paramètre pour supprimer les données de contrôle en fonction de `principalId`, `policyId` ou `licenseId`.

1. Les fichiers XML de stratégie actifs et archivés sont stockés dans les tableaux de base de données `EdcPolicyXmlEntity` et `EdcPolicyArchiveEntity`, respectivement. Pour supprimer les données d’un utilisateur de ces tables, procédez comme suit :

   1. Ouvrez l’objet Blob XML de chaque ligne dans le tableau `EdcPolicyXMLEntity` ou `EdcPolicyArchiveEntity` et extrayez le fichier XML. Le fichier XML ressemble à l’un des fichiers ci-dessous.
   1. Modifiez le fichier XML pour supprimer l’objet Blob de l’ID principal.
   1. Répétez les étapes 1 et 2 pour l’autre fichier.

   >[!NOTE]
   >
   >Vous devez supprimer l’intégralité de l’objet Blob dans la balise `Principal` pour un ID principal ou la stratégie XML risque d’être endommagée ou inutilisable.

   ```xml
   <ns2:Principal PrincipalNameType="USER">
       <ns2:PrincipalDomain>OID</ns2:PrincipalDomain>
       <ns2:PrincipalName>56F33FEB-098A-1036-A651-00000A2A2656</ns2:PrincipalName>
   </ns2:Principal>
   </ns2:PolicyEntry>
       <ns2:Property PropertyName="isCertified">
           <ns2:PropertyValue xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance" xmlns:xs="https://www.w3.org/2001/XMLSchema" xsi:type="xs:string">false</ns2:PropertyValue>
       </ns2:Property>
       <ns2:Property PropertyName="encryptionAlgorithm">
           <ns2:PropertyValue xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance" xmlns:xs="https://www.w3.org/2001/XMLSchema" xsi:type="xs:string">AES128</ns2:PropertyValue>
       </ns2:Property>
       <ns2:Property PropertyName="AccessDeniedErrorMessage">
           <ns2:PropertyValue xmlns:xsi="https://www.w3.org/2001/XMLSchema-instance" xmlns:xs="https://www.w3.org/2001/XMLSchema" xsi:type="xs:string"></ns2:PropertyValue>
       </ns2:Property>
   <ns2:PolicyEntry>
   <ns2:Permission PermissionName="ns3:com.adobe.aps.onlineOpen" Access="ALLOW"/>
   <ns2:Permission PermissionName="ns3:com.adobe.aps.pdf.copy" Access="ALLOW"/>
   <ns2:Permission PermissionName="ns3:com.adobe.aps.offlineOpen" Access="ALLOW"/>
   <ns2:Permission PermissionName="ns3:com.adobe.aps.pdf.accessible" Access="ALLOW"/>
   <ns2:Permission PermissionName="ns3:com.adobe.aps.pdf.editNotes" Access="ALLOW"/>
   <ns2:Permission PermissionName="ns3:com.adobe.aps.pdf.edit" Access="ALLOW"/>
   <ns2:Permission PermissionName="ns3:com.adobe.aps.pdf.fillAndSign" Access="ALLOW"/>
   <ns2:Permission PermissionName="ns3:com.adobe.aps.pdf.printHigh" Access="ALLOW"/>
   <ns2:Permission PermissionName="ns3:com.adobe.aps.pdf.printLow" Access="ALLOW"/>
   ```

   Outre la suppression des données directement à partir de la table `EdcPolicyXmlEntity`, vous pouvez également utiliser les deux méthodes suivantes :

   **Utilisation de la console d’administration**

   1. Connectez-vous en tant qu’administrateur à la console d’administration de Forms JEE à l’adresse suivante : https://[*server*]:[*port*]/adminui.
   1. Accédez à **[!UICONTROL Services > Document Security > Jeux de stratégie]**.
   1. Ouvrez un jeu de stratégies et supprimez l’utilisateur de la stratégie.

   **Utilisation de la page Web de Document Security**

   Les utilisateurs de Document Security autorisés à créer des stratégies personnelles peuvent supprimer des données utilisateur de leurs stratégies. Pour ce faire :

   1. Les utilisateurs possédant des stratégies personnelles peuvent se connecter à leur page web de Document Security à l’adresse suivante : https://[*server*]:[*port*]/edc.
   1. Accédez à **[!UICONTROL Services > Document Security > Mes stratégies]**.
   1. Ouvrez une stratégie et supprimez l’utilisateur de la stratégie.

   >[!NOTE]
   >
   >Les administrateurs peuvent rechercher des données utilisateur de stratégies personnelles d’autres utilisateurs, y accéder et les supprimer dans **[!UICONTROL Services > Document Security > Mes stratégies]** à l’aide de la console d’administration.

1. Supprimez les données de l’ID principal de la base de données User Management. Pour obtenir des instructions détaillées, reportez-vous à la section [Forms User Management : gérer les données utilisateur](/help/forms/using/user-management-handling-user-data.md).
1. Démarrez le serveur AEM Forms.
