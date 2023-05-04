---
title: Créer un groupe d’utilisateurs fermé
seo-title: Creating a Closed User Group
description: Découvrez comment créer un groupe d’utilisateurs fermé.
seo-description: Learn how to create a Closed User Group.
uuid: 03d5fc69-6e4b-41c1-88c9-7454250c29ac
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: Security
content-type: reference
discoiquuid: ba73e267-598d-4c70-a1a8-71bcfcfbf9e5
exl-id: 3a052270-b3ea-4d17-915c-be2b51cdc482
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '831'
ht-degree: 61%

---

# Créer un groupe d’utilisateurs fermé{#creating-a-closed-user-group}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Les groupes d’utilisateurs fermés permettent de restreindre l’accès à des pages spécifiques qui se trouvent sur un site Internet publié. Ces pages requièrent que les membres affectés se connectent et fournissent des informations d’identification de sécurité.

Pour configurer une zone de ce type dans votre site web, procédez comme suit :

* [Créez un groupe d’utilisateurs fermé réel et affectez-y des membres.](#creating-the-user-group-to-be-used)

* [Appliquez ce groupe aux pages concernées](#applying-your-closed-user-group-to-content-pages) et sélectionnez (ou créez) la page de connexion à utiliser par les membres du groupe d’utilisateurs fermé. Cela est spécifié également lors de l’application d’un groupe d’utilisateur fermé à une page de contenu.

* [créer un lien, d’une forme ou d’une autre, vers au moins une page dans la zone protégée ;](#linking-to-the-realm), sinon il ne sera pas visible.
* [configuration de Dispatcher](#configure-dispatcher-for-cugs) en cas d’utilisation.

>[!CAUTION]
>
>Les groupes d’utilisateurs fermés (CUG) doivent toujours être créés en tenant compte des performances.
>
>Bien que le nombre d’utilisateurs et de groupes dans un groupe d’utilisateurs fermé ne soit pas limité, un nombre élevé de groupes d’utilisateurs fermés sur une page peut ralentir les performances de rendu.
>
>L’impact des CUG doit toujours être pris en compte lors des tests de performance.

## Création Du Groupe D’Utilisateurs À Utiliser {#creating-the-user-group-to-be-used}

Pour créer un groupe d’utilisateurs fermé :

1. Accédez à **Outils - Sécurité** depuis l’écran d’accueil d’AEM.

   >[!NOTE]
   >
   >Voir [Gestion des utilisateurs et des groupes](/help/sites-administering/security.md#managing-users-and-groups) pour obtenir des informations complètes sur la création et la configuration des utilisateurs et des groupes.

1. Sélectionnez la **Groupes** de l’écran suivant.

   ![screenshot_2018-10-30at145502](assets/screenshot_2018-10-30at145502.png)

1. Appuyez sur le bouton **Créer** dans le coin supérieur droit pour créer un groupe.
1. Nommez votre groupe, par exemple `cug_access`.

   ![screenshot_2018-10-30at151459](assets/screenshot_2018-10-30at151459.png)

1. Accédez à l’onglet **Membres** et affectez les utilisateurs requis à ce groupe.

   ![screenshot_2018-10-30at151808](assets/screenshot_2018-10-30at151808.png)

1. Activez les utilisateurs affectés à votre groupe d’utilisateurs fermé, en l’occurrence, le groupe `cug_access`.
1. Activez le groupe d’utilisateurs fermé de sorte qu’il soit disponible dans l’environnement de publication. Dans cet exemple, `cug_access`.

## Appliquer votre groupe d’utilisateurs fermé à des pages de contenu {#applying-your-closed-user-group-to-content-pages}

Pour appliquer le groupe d’utilisateurs fermé à une page :

1. Accédez à la page principale de la section restreinte que vous souhaitez affecter à votre groupe d’utilisateurs fermé.
1. Sélectionnez la page en cliquant sur sa miniature, puis sur **Propriétés** dans le panneau supérieur.

   ![screenshot_2018-10-30at162632](assets/screenshot_2018-10-30at162632.png)

1. Dans la fenêtre suivante, accédez à l’onglet **Avancé**.
1. Faites défiler vers le bas et activez la case à cocher dans la section **Exigence d’authentification**.

1. Ajoutez le chemin de votre configuration ci-dessous, puis appuyez sur Enregistrer.
1. Ensuite, accédez à l’onglet **Autorisations** et appuyez sur le bouton **Modifier le groupe d’utilisateurs fermé**.

   ![screenshot_2018-10-30at163003](assets/screenshot_2018-10-30at163003.png)

   >[ATTENTION !]
   >
   > Notez que les groupes d’utilisateurs fermés dans l’onglet Autorisations ne peuvent pas être déployés dans des Live Copies à partir de plans directeurs. Veuillez en tenir compte lors de la configuration de Live Copy.
   >
   > Pour plus d’informations, consultez [cette page](closed-user-groups.md#aem-livecopy).

1. Recherchez et ajoutez votre CUG dans la fenêtre suivante - dans ce cas, ajoutez le groupe nommé **cug_access**. Enfin, la presse **Enregistrer**.
1. Cliquez sur **Activé** pour définir que cette page et les pages enfants appartiennent à un groupe d’utilisateurs fermé.
1. Spécifiez la **Page de connexion** que les membres du groupe utiliseront ; par exemple :

   `/content/geometrixx/en/toolbar/login.html`

   Cette option est facultative. Si rien n’est indiqué, la page de connexion standard est utilisée.

1. Ajoutez les **groupes admis**. Utilisez « + » pour ajouter des groupes ou « – » pour en supprimer. Seuls les membres de ces groupes seront autorisés à se connecter et à accéder aux pages.
1. Affectez un **domaine** (nom pour les groupes de pages), si nécessaire. Laisser vide pour utiliser le titre de la page.
1. Cliquez sur **OK** pour enregistrer la spécification.

Pour plus d’informations sur les profils dans l’environnement de publication et pour proposer des formulaires de connexion et de déconnexion, voir [Gestion de l’identification](/help/sites-administering/identity-management.md).

## Liaison Au Domaine {#linking-to-the-realm}

La cible des liens vers le domaine des CUG n’étant pas visible par l’utilisateur anonyme, le vérificateur de liens supprime ces liens.

Pour éviter cette situation, il est recommandé de créer des pages de redirection non protégées, qui pointent vers des pages dans le domaine Groupe d’utilisateurs fermé. Les entrées de navigation sont alors rendues sans causer de problème au niveau du vérificateur de lien. Ce n’est que lorsque l’utilisateur aura réellement accédé à la page de redirection que l’utilisateur sera redirigé dans le domaine des CUG, après avoir fourni ses informations de connexion.

## Configuration de Dispatcher pour les CUG {#configure-dispatcher-for-cugs}

Si vous utilisez Dispatcher, vous devez définir une ferme de serveurs de Dispatcher avec les propriétés suivantes :

* [virtualhosts](https://helpx.adobe.com/fr/experience-manager/dispatcher/using/dispatcher-configuration.html#identifying-virtual-hosts-virtualhosts): Correspond au chemin d’accès aux pages auxquelles le groupe d’utilisateurs fermé s’applique.
* \sessionmanagement: voir ci-dessous.
* [cache](https://helpx.adobe.com/fr/experience-manager/dispatcher/using/dispatcher-configuration.html#configuring-the-dispatcher-cache-cache): Répertoire de cache dédié aux fichiers auxquels le CUG s’applique.

### Configuration de la gestion des sessions de Dispatcher pour les groupes d’utilisateurs fermés {#configuring-dispatcher-session-management-for-cugs}

Configurez la [gestion des sessions dans le fichier dispatcher.any](https://helpx.adobe.com/fr/experience-manager/dispatcher/using/dispatcher-configuration.html#enabling-secure-sessions-sessionmanagement) pour le groupe d’utilisateurs fermé. Le gestionnaire d’authentification utilisé lorsque l’accès est demandé pour les pages des groupes d’utilisateurs fermés détermine comment configurer la gestion des sessions.

```xml
/sessionmanagement
    ...
    /header "Cookie:login-token" 
    ...
```

>[!NOTE]
>
>Lorsque la gestion des sessions est activée pour une ferme de serveurs de Dispatcher, toutes les pages gérées par la ferme de serveurs ne sont pas mises en cache. Pour mettre en cache les pages qui ne sont pas des groupes d’utilisateurs fermés, créez une seconde ferme de serveurs dans dispatcher.any.\
>qui gère les pages non CUG.

1. Configurez [/sessionmanagement](https://helpx.adobe.com/fr/experience-manager/dispatcher/using/dispatcher-configuration.html#enabling-secure-sessions-sessionmanagement) en définissant `/directory`, par exemple :

   ```xml
   /sessionmanagement
     {
     /directory "/usr/local/apache/.sessions"
     ...
     }
   ```

1. Définissez [/allowAuthorized](https://helpx.adobe.com/fr/experience-manager/dispatcher/using/dispatcher-configuration.html#caching-when-authentication-is-used) sur `0`.
