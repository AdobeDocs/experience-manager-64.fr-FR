---
title: Expérience du site publié
seo-title: Expérience du site publié
description: Accéder à un site publié
seo-description: Accéder à un site publié
uuid: f510224c-d991-4528-864d-44672138740c
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: introduction
content-type: reference
discoiquuid: 4dc54701-68b9-49dd-a212-b0b53330c1c0
translation-type: tm+mt
source-git-commit: 63001012f0d865c2548703ea387c780679128ee7
workflow-type: tm+mt
source-wordcount: '1144'
ht-degree: 2%

---


# Expérience du site publié {#experience-the-published-site}

## Accéder au nouveau site sur Publier {#browse-to-new-site-on-publish}

Maintenant que le site des communautés nouvellement créé a été publié, accédez à l’URL qui s’affiche lors de la création du site, mais sur le serveur de publication, par exemple.

* URL de l’auteur = http://localhost:4502/content/sites/engage/en.html
* URL de publication = http://localhost:4503/content/sites/engage/en.html

Pour éviter toute confusion quant au membre qui est connecté lors de l’auteur et de la publication, il est conseillé d’utiliser différents navigateurs pour chaque instance.

En arrivant sur le site publié, le visiteur du site n’était généralement pas déjà connecté et était anonyme.

## http://localhost:4503/content/sites/engage/en.html {#http-localhost-content-sites-engage-en-html}

![chlimage_1-311](assets/chlimage_1-311.png)

## Visiteur de site anonyme {#anonymous-site-visitor}

Un visiteur de site anonyme voit les éléments suivants dans l’interface utilisateur :

* Titre du site. Didacticiel de prise en main
* Aucun lien de profil
* Aucun lien de message
* Aucun lien de notification
* Champ de recherche
* Connexion au lien
* La bannière de la marque
* Liens de menu pour les composants inclus dans le modèle de site de référence

Si vous sélectionnez divers liens, vous constaterez qu’ils sont en mode lecture seule.

## Empêcher l’accès anonyme au JCR {#prevent-anonymous-access-on-jcr}

Une limitation connue expose le contenu du site de la communauté aux visiteurs anonymes par le biais du contenu jcr et json, bien que **autoriser l’accès anonyme** soit désactivé pour le contenu du site. Cependant, ce comportement peut être contrôlé à l’aide des restrictions Sling comme solution.

Pour protéger le contenu de votre site communautaire contre l’accès d’utilisateurs anonymes par le biais de contenu jcr et json, procédez comme suit :

1. Sur l’instance d’auteur AEM, accédez à https://&lt;hôte>:&lt;port>/editor.html/content/site/&lt;nom du site>.html.

   >[!NOTE]
   >
   >N’accédez pas au site localisé.

1. Accédez à **[!UICONTROL Propriétés de la page]**.

   ![authentification de site](assets/site-authentication.png)

1. Accédez à l’onglet **[!UICONTROL Avancé]**.

   ![page-properties](assets/page-properties.png)

1. Activez **[!UICONTROL Authentification requise]**.
1. Ajoutez le chemin de la page de connexion. Par exemple, `/content/......./GetStarted`.
1. Publiez la page.

## Membre de la communauté approuvée {#trusted-community-member}

Cette expérience suppose que [Aaron McDonald](tutorials.md#demo-users) se voit attribuer les rôles de [gestionnaire communautaire et modérateur](create-site.md#roles). Dans le cas contraire, revenez à l’environnement auteur pour [modifier les paramètres du site](sites-console.md#modifying-site-properties) et sélectionnez Aaron McDonald comme gestionnaire de communauté et modérateur.

Dans le coin supérieur droit, sélectionnez `Log in` et signez avec le nom d&#39;utilisateur &quot;aaron.mcdonald@mailinator.com&quot; et le mot de passe &quot;password&quot;. Vous pouvez vous connecter à l’aide des informations d’identification Twitter ou Facebook.

![chlimage_1-312](assets/chlimage_1-312.png)

Une fois connecté, notez qu&#39;il existe un nouvel élément de menu, `Administration`, qui s&#39;affiche car le membre a reçu le rôle de modérateur. Maintenant, choisir divers liens est plus intéressant.

![chlimage_1-313](assets/chlimage_1-313.png)

Notez que la page Calendrier correspond à la page d&#39;accueil, car le modèle de site de référence choisi comprenait d’abord la fonction Calendrier, suivie de la fonction de flux d’Activité, de la fonction de forum, etc. Cette structure est visible à partir de la console [Modèle de site](sites.md#edit-site-template) ou lors de la modification des propriétés du site dans l’environnement d’auteur :

![chlimage_1-314](assets/chlimage_1-314.png)

>[!NOTE]
>
>Pour plus d&#39;informations sur les composants et les fonctions des communautés, consultez la rubrique
>
>* [Composants](author-communities.md)  de communautés (pour les auteurs)
>* [Composants, fonctions et fonctionnalités essentiels](essentials.md)  (pour les développeurs)

>



## Lien du forum {#forum-link}

Vue la fonction de base du forum en sélectionnant le lien du forum.

Les membres peuvent publier un nouveau sujet ou suivre un sujet.

Les visiteurs du site peuvent vue et trier les publications de différentes manières.

![chlimage_1-315](assets/chlimage_1-315.png)

## Lien Groupes {#groups-link}

Etant donné qu’Aaron est un administrateur de groupe, la sélection du lien Groupes permettra à Aaron de créer un nouveau groupe communautaire en sélectionnant un modèle de groupe, une image, que le groupe soit ouvert ou secret, et en invitant des membres.

Il s’agit d’un exemple de création d’un groupe dans l’environnement de publication.

Les groupes peuvent également être créés dans l&#39;environnement d&#39;auteur et gérés dans le site communautaire de l&#39;environnement d&#39;auteur (la [console Groupes communautaires](groups.md)). L&#39;expérience de [création de groupes sur author](nested-groups.md) est présentée dans ce didacticiel.

![chlimage_1-316](assets/chlimage_1-316.png)

Créer un groupe de référence :

1. Sélectionner **[!UICONTROL Nouveau groupe]**
1. **[!UICONTROL Onglet Settings]**
   * Nom du groupe: `Sports`
   * Description: `A parent group for various sporting groups`
   * Nom de l’URL de groupe: `sports`
   * sélectionner `Open Group` (autoriser tout membre de la communauté à participer en se joignant)
1. **[!UICONTROL Onglet Modèle]**
   * Sélectionnez `Reference Group` (contient une fonction de groupes dans sa structure pour autoriser les groupes imbriqués).
1. Sélectionner **[!UICONTROL Créer un groupe]**

![chlimage_1-317](assets/chlimage_1-317.png)

Une fois le nouveau groupe créé, **sélectionnez le nouveau groupe Sports** afin de créer deux groupes (imbriqués) au sein de celui-ci. Comme une structure de site ne peut pas commencer par la fonction de groupes, après avoir ouvert le groupe Sports, il est nécessaire de sélectionner le lien Groupes :

![chlimage_1-318](assets/chlimage_1-318.png)

Le deuxième ensemble de liens, commençant par `Blog`, appartient au groupe actuellement sélectionné, le groupe `Sports`. En sélectionnant le lien Sports `Groups`, vous pouvez imbriquer deux groupes dans le groupe Sports.

Par exemple, ajoutez deux n `ew groups.`

* Un nom nommé `Baseball`
   * Laissez-le défini comme `Open Group` (adhésion obligatoire)
   * Dans l&#39;onglet Modèles, sélectionnez `Conversational Group`
* Un nom nommé `Gymnastics`
   * Modifiez son paramètre en `Member Only Group` (adhésion restreinte).
   * Dans l&#39;onglet Modèles, sélectionnez `Conversational Group`

**Avis**:

* Une actualisation de la page peut s’avérer nécessaire avant l’affichage des deux groupes.
* Ce modèle n’inclut *pas la fonction de groupes ; il n’est donc pas possible d’imbriquer davantage de groupes.
* Sur l’auteur, la console [Groupes](groups.md) fournit un troisième choix : un `Public Group` (abonnement facultatif).

Une fois les deux groupes créés, sélectionnez le groupe de baseball, un groupe ouvert, et notez ses liens : `Discussions` `What's New` `Members`
Les liens du groupe s&#39;affichent sous les liens du site principal et les résultats s&#39;affichent comme suit :

![chlimage_1-319](assets/chlimage_1-319.png)

Sur author - with administrative privilèges, accédez à la console [Groupes de communautés](members.md) et ajoutez Weston McCall au groupe `Community Engage Gymnastics <uid> Members`.

Poursuivant sur la publication, déconnectez-vous en tant que Aaron McDonald, et vue des groupes du groupe Sports en tant que visiteur anonyme du site :

* De la page d&#39;accueil
* Sélectionner un `Groups`lien
* Sélectionner un `Sports`lien
* Sélectionnez le lien Sports `Groups`

Seul le groupe de baseball sera visible.

Connectez-vous en tant que Weston McCall (weston.mccall@dodgit.com / mot de passe) et accédez au même emplacement. Notez que Weston peut `Join` le groupe `Baseball` ouvert et `enter or Leave` le groupe `Gymnastics`privé.

![chlimage_1-320](assets/chlimage_1-320.png)

## Lien de page Web {#web-page-link}

Vue de la page Web de base incluse dans le site en sélectionnant le lien Page Web. Les outils de création AEM standard peuvent être utilisés pour ajouter du contenu à cette page dans l’environnement d’auteur.

Par exemple, accédez à l&#39;instance **author**, ouvrez le dossier `engage` dans la console [Sites des communautés](sites-console.md), sélectionnez l&#39;icône **Ouvrir le site** pour passer en mode d&#39;édition de l&#39;auteur. Sélectionnez ensuite le mode de prévisualisation pour sélectionner le lien `Web Page`puis le mode de modification pour ajouter les composants Titre et Texte. Enfin, republiez uniquement la page ou l’ensemble du site.

![chlimage_1-321](assets/chlimage_1-321.png)

## Lien d&#39;administration {#administration-link}

Lorsque le membre de la communauté dispose de privilèges de modération, le lien Administration est visible et sa sélection affiche le contenu de la communauté publié et lui permet d’être [modéré](moderate-ugc.md) d’une manière similaire à la [console de modération](moderation.md) de l’environnement d’auteur.

Utilisez le bouton Retour du navigateur pour revenir au site publié. La plupart des consoles ne sont pas accessibles à partir de la navigation globale dans l’environnement de publication.

![chlimage_1-322](assets/chlimage_1-322.png)

## Auto-inscription {#self-registration}

Une fois déconnecté, il est possible de créer une nouvelle inscription d’utilisateur.

* Sélectionner `Log In`
* Sélectionner `Sign up for a new account`

![chlimage_1-323](assets/chlimage_1-323.png) ![chlimage_1-324](assets/chlimage_1-324.png)

Par défaut, l’adresse électronique correspond à l’identifiant de connexion. Si cette option n’est pas cochée, le visiteur peut saisir son propre identifiant de connexion (nom d’utilisateur). Le nom d’utilisateur doit être unique dans l’environnement de publication.

Après avoir spécifié le nom, l’adresse électronique et le mot de passe de l’utilisateur, la sélection de `Sign Up`crée l’utilisateur et lui permet de signer.

Une fois connecté, la première page présentée est leur `Profile`page, qu’ils peuvent personnaliser.

![chlimage_1-325](assets/chlimage_1-325.png)

Si le membre oublie son ID de connexion, il est possible de récupérer son adresse électronique.

![chlimage_1-326](assets/chlimage_1-326.png)
