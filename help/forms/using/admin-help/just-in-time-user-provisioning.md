---
title: Approvisionnement juste à temps d’utilisateurs
seo-title: Just-in-time user provisioning
description: Utilisez la mise en service juste à temps pour ajouter des utilisateurs à User Management après une authentification réussie et affecter dynamiquement les rôles et groupes appropriés au nouvel utilisateur.
seo-description: Use just-in-time provisioning to add users to User Management after successfull authentication and dynamically assign relevant roles and groups to the new user.
uuid: a5ad4698-70bb-487b-a069-7133e2f420c2
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/setting_up_and_organizing_users
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: e80c3f98-baa1-45bc-b713-51a2eb5ec165
exl-id: 8c205d1d-d17e-4810-8ef9-a8bdcd9aa1c2
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '609'
ht-degree: 30%

---

# Approvisionnement juste à temps {#just-in-time-user-provisioning}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

AEM forms prend en charge la mise en service juste à temps des utilisateurs qui n’existent pas encore dans User Management. Avec la mise en service juste à temps, les utilisateurs sont automatiquement ajoutés à User Management une fois leurs informations d’identification authentifiées. En outre, les rôles et groupes pertinents sont affectés dynamiquement au nouvel utilisateur.

## Nécessité de l’approvisionnement juste à temps des utilisateurs {#need-for-just-in-time-user-provisioning}

Voici comment fonctionne l’authentification traditionnelle :

1. Lorsqu’un utilisateur tente de se connecter à AEM forms, User Management transmet les informations d’identification de l’utilisateur de manière séquentielle à tous les fournisseurs d’authentification disponibles. (Les informations d’identification comprennent un nom d’utilisateur/mot de passe, un ticket Kerberos, une signature PKCS7, etc.)
1. Le fournisseur d’authentification valide les informations d’identification.
1. Le fournisseur d’authentification vérifie ensuite si l’utilisateur existe dans la base de données User Management. Les résultats possibles sont les suivants :

   **Existe :** si l’utilisateur est en cours et déverrouillé, User Management renvoie un succès d’authentification. Toutefois, si l’utilisateur n’est pas en cours ou s’il est verrouillé, User Management signale un échec d’authentification.

   **N’existe pas :** User Management renvoie un échec d’authentification.

   **Non valide :** User Management renvoie un échec d’authentification.

1. Le résultat renvoyé par le fournisseur d’authentification est évalué. Si le fournisseur d’authentification a renvoyé une authentification réussie, l’utilisateur est autorisé à se connecter. Sinon, User Management vérifie auprès du fournisseur d’authentification suivant (étapes 2 à 3).
1. L’échec de l’authentification est renvoyé si aucun fournisseur d’authentification disponible ne valide les informations d’identification de l’utilisateur.

Lors de la mise en oeuvre de l’approvisionnement juste à temps, un nouvel utilisateur est créé dynamiquement dans User Management si l’un des fournisseurs d’authentification valide les informations d’identification de l’utilisateur. (Après l’étape 3 de la procédure d’authentification traditionnelle, ci-dessus.)

## Mise en oeuvre de l’approvisionnement juste à temps des utilisateurs {#implement-just-in-time-user-provisioning}

### API pour l’approvisionnement juste à temps {#apis-for-just-in-time-provisioning}

AEM forms fournit les API suivantes pour la mise en service juste à temps :

```as3
package com.adobe.idp.um.spi.authentication  ; 
publ ic interface IdentityCreator { 
/** 
* Tries  to create a user with the  in formation  provided in the <code>UserProvisioningBO</code> object. 
* If the user is successfully created, a valid AuthResponse is returned along with the information using which the user was created. 
* It is the responsibility of the IdentityCreator to set the User obje ct  in the cre dential map with th e  ke y  <code>UMA u thenticationUtil.authenticatedUserKey</code> 
* The credentials are available in the <code>UserProvisioningBO</code> object in the 'credentials' property. 
* If the IdentityCreator is unable to create a user due to any reason, it returns <code>null</code> 
* @param userBO An object of <code>com.adobe. i dp.um . spi.authenti c ationUserProvisioningBO</code> 
* @return */public AuthResponse create(UserProvisioningBO userBO); 
/** 
* Returns the name of the IdentityCreator which will be registered in preferences. 
* This name is used to associate the IdentityProvider with the Auth Provider Configuration in the domain. 
* @return The name of the Identity Creator which is recognized in Configuration. 
*/ 
public String getName(); 
} 
package com.adobe.idp.um.spi.authentication; 
import com.adobe.idp.um.api.infomodel.User; 
public interface AssignmentProvider { 
/** 
* Tries to assign roles or permissions or group memberships to users created via Just-in-time provisioning. 
* @param user The User created via the Just-in-time provisioning process. 
* @return a Boolean flag indicating whether the assignment was successful or not. 
*/ 
public Boolean assign(User user); 
/** 
* Returns the name of the AssignmentProvider through which it is registered under preferences. 
* This name is used to associate the AssignmentProvider with the Auth Provider Configuration in the domain. 
* @return The name of the AssignmentProvider which is recognized in Configuration. 
*/public String getName(); 
}
```

### Remarques concernant la création d’un domaine juste à temps {#considerations-while-creating-a-just-in-time-enabled-domain}

* Lors de la création d’un `IdentityCreator` personnalisé pour un domaine hybride, assurez-vous qu’un mot de passe factice est spécifié pour l’utilisateur local. Ne laissez pas ce champ de mot de passe vide.
* Recommandation : utilisez `DomainSpecificAuthentication` pour valider les informations d’identification de l’utilisateur pour un domaine spécifique.

### Créer un domaine d’approvisionnement juste à temps {#create-a-just-in-time-enabled-domain}

1. Créez un DSC mettant en oeuvre les API dans la section &quot;API pour la mise en service juste à temps&quot;.
1. Déployez le DSC sur le serveur Forms.
1. Créer un domaine d’approvisionnement juste à temps:

   * Dans Administration Console, cliquez sur Paramètres > User Management > Gestion des domaines > Nouveau domaine d’entreprise.
   * Configurez le domaine et sélectionnez Activer l’approvisionnement juste à temps. <!--Fix broken link (See Setting up and managing domains).-->
   * Ajoutez des fournisseurs d’authentification. Lors de l’ajout de fournisseurs d’authentification, dans l’écran Nouvelle authentification, sélectionnez un créateur d’identités et un fournisseur d’affectation enregistrés.

1. Enregistrez le nouveau domaine.

## En arrière-plan {#behind-the-scenes}

Supposons qu’un utilisateur essaie de se connecter à AEM forms et qu’un fournisseur d’authentification accepte ses informations d’identification. Si l’utilisateur n’existe pas encore dans la base de données User Management, la vérification d’identité de l’utilisateur échoue. AEM forms effectue désormais les actions suivantes :

1. Création d’un objet `UserProvisioningBO` avec les données d’authentification et placement de l’objet dans une carte d’informations d’identification.
1. Extraction et appel des `UserProvisioningBO` et `IdentityCreator` enregistrés pour le domaine en se basant sur les informations du domaine renvoyées par `AssignmentProvider`.
1. Appelez `IdentityCreator`. Si une `AuthResponse` positive est renvoyée, extraction de `UserInfo` de la carte d’informations d’identification. Transmission de UserInfo à `AssignmentProvider` pour l’affectation des groupes et des rôles après la création de l’utilisateur.
1. Si l’utilisateur a été créé avec succès, renvoyez la tentative de connexion de l’utilisateur.
1. Pour les domaines hybrides, extrayez les informations utilisateur des données d’authentification fournies au fournisseur d’authentification. Si ces informations sont récupérées correctement, créez l’utilisateur à la volée.

>[!NOTE]
>
>la fonction d’approvisionnement juste à temps comprend une mise en œuvre par défaut de `IdentityCreator` que vous pouvez utiliser pour créer des utilisateurs de manière dynamique. Les utilisateurs sont créés avec les informations associées aux annuaires dans ce domaine.
