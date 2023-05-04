---
title: Expérience du site publié
seo-title: Experience the Published Site
description: Accès à un site publié
seo-description: Browse to a published site
uuid: f510224c-d991-4528-864d-44672138740c
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: introduction
content-type: reference
discoiquuid: 4dc54701-68b9-49dd-a212-b0b53330c1c0
exl-id: 8f716a59-1116-4855-baeb-3997de71b55f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1171'
ht-degree: 3%

---

# Expérience du site publié {#experience-the-published-site}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

## Accéder au nouveau site lors de la publication {#browse-to-new-site-on-publish}

Maintenant que le site des communautés nouvellement créé a été publié, accédez à l’URL affichée lors de la création du site, mais sur le serveur de publication, par exemple :

* URL de création = http://localhost:4502/content/sites/engage/en.html
* URL de publication = http://localhost:4503/content/sites/engage/en.html

Afin de minimiser la confusion quant au membre qui est connecté lors de l’auteur et de la publication, il est conseillé d’utiliser différents navigateurs pour chaque instance.

En arrivant sur le site publié pour la première fois, le visiteur du site n’était généralement pas déjà connecté et était anonyme.

## http://localhost:4503/content/sites/engage/en.html {#http-localhost-content-sites-engage-en-html}

![chlimage_1-311](assets/chlimage_1-311.png)

## Visiteur anonyme du site {#anonymous-site-visitor}

Un visiteur anonyme du site voit les éléments suivants dans l’interface utilisateur :

* Titre du site. Tutoriel de prise en main
* Aucun lien de profil
* Lien vers aucun message
* Lien Aucune notification
* Champ de recherche
* Lien de connexion
* Bannière de marque
* Liens de menu pour les composants inclus dans le modèle de site de référence

Si vous sélectionnez différents liens, ils sont en lecture seule.

## Empêcher l’accès anonyme sur JCR {#prevent-anonymous-access-on-jcr}

Une limitation connue expose le contenu du site de la communauté aux visiteurs anonymes par le biais de contenu jcr et json , bien que **autoriser l’accès anonyme** est désactivé pour le contenu du site. Cependant, ce comportement peut être contrôlé à l’aide de restrictions Sling comme solution de contournement.

Pour protéger le contenu de votre communauté contre l’accès des utilisateurs anonymes par le biais de jcr content et json , procédez comme suit :

1. Sur l’instance AEM Author, accédez à https://&lt;host>:&lt;port>/editor.html/content/site/&lt;sitename>.html.

   >[!NOTE]
   >
   >Ne pas accéder au site localisé.

1. Accédez à **[!UICONTROL Propriétés de la page]**.

   ![site-authentication](assets/site-authentication.png)

1. Accédez à l’onglet **[!UICONTROL Avancé]**.

   ![page-properties](assets/page-properties.png)

1. Activer **[!UICONTROL Exigence d’authentification]**.
1. Ajoutez le chemin d’accès de la page de connexion. Par exemple, `/content/......./GetStarted`.
1. Publiez la page.

## Membre de la communauté approuvé {#trusted-community-member}

Cette expérience suppose que [Aaron McDonald](tutorials.md#demo-users) a été affecté aux rôles de [gestionnaire de communauté et modérateur](create-site.md#roles). Si ce n’est pas le cas, revenez à l’environnement de création en [modification des paramètres du site](sites-console.md#modifying-site-properties) et sélectionnez Aaron McDonald comme gestionnaire de communauté et modérateur.

Dans le coin supérieur droit, sélectionnez `Log in`et signez avec le nom d’utilisateur &quot;aaron.mcdonald@mailinator.com&quot; et le mot de passe &quot;password&quot;. Vous pouvez vous connecter à l’aide des informations d’identification Twitter ou Facebook.

![chlimage_1-312](assets/chlimage_1-312.png)

Une fois connecté, notez qu’il existe un nouvel élément de menu, `Administration`, qui s’affiche car le membre a reçu le rôle de modérateur. La sélection de différents liens est plus intéressante.

![chlimage_1-313](assets/chlimage_1-313.png)

Notez que la page Calendrier est la page d’accueil, car le modèle de site de référence sélectionné incluait d’abord la fonction Calendrier , suivie de la fonction Flux d’activités, Forum , etc. Cette structure est visible à partir du [Modèle de site](sites.md#edit-site-template) ou lors de la modification des propriétés du site dans l’environnement de création :

![chlimage_1-314](assets/chlimage_1-314.png)

>[!NOTE]
>
>Pour plus d’informations sur les composants et les fonctions de Communities, voir
>
>* [Composants Communities](author-communities.md) (pour les auteurs)
>* [Principes fondamentaux des composants, fonctions et fonctionnalités](essentials.md) (pour les développeurs)
>


## Lien du forum {#forum-link}

Pour afficher la fonction de base du forum, cliquez sur le lien Forum .

Les membres peuvent publier un nouveau sujet ou suivre un sujet.

Les visiteurs du site peuvent afficher les publications et les trier de différentes manières.

![chlimage_1-315](assets/chlimage_1-315.png)

## Lien Groupes {#groups-link}

Dans la mesure où Aaron est administrateur de groupe, la sélection du lien Groupes permettra à Aaron de créer un nouveau groupe de communautés en sélectionnant un modèle de groupe, une image, que le groupe soit ouvert ou secret, et en invitant des membres.

Il s’agit d’un exemple dans lequel un groupe est créé dans l’environnement de publication.

Les groupes peuvent également être créés dans l’environnement de création et gérés dans le site de la communauté dans l’environnement de création (le [Console Groupes de communautés](groups.md)). L’expérience de [création de groupes sur l’instance de création](nested-groups.md) est le suivant de ce tutoriel.

![chlimage_1-316](assets/chlimage_1-316.png)

Création d’un groupe de référence :

1. Sélectionner **[!UICONTROL Nouveau groupe]**
1. **[!UICONTROL Onglet Paramètres]**
   * Nom de groupe: `Sports`
   * Description: `A parent group for various sporting groups`
   * Nom de l’URL de groupe: `sports`
   * select `Open Group` (autoriser tout membre de la communauté à y participer en y rejoignant)
1. **[!UICONTROL Onglet Modèle]**
   * Sélectionner `Reference Group` (contient une fonction de groupes dans sa structure pour autoriser les groupes imbriqués)
1. Sélectionner **[!UICONTROL Créer un groupe]**

![chlimage_1-317](assets/chlimage_1-317.png)

Une fois le nouveau groupe créé, **sélectionnez le nouveau groupe Sports** afin de créer deux groupes (imbriqués) dans celui-ci. Comme une structure de site ne peut pas commencer par la fonction de groupes, après l’ouverture du groupe Sports, il est nécessaire de sélectionner le lien Groupes :

![chlimage_1-318](assets/chlimage_1-318.png)

Le deuxième ensemble de liens, commençant par `Blog`, appartiennent au groupe actuellement sélectionné, le `Sports`groupe. En sélectionnant &quot;Sports&quot; `Groups` , il est possible d’imbriquer deux groupes dans le groupe Sports .

Par exemple, ajoutez deux n `ew groups.`

* Un nom `Baseball`
   * Laissez-le défini comme `Open Group` (abonnement requis)
   * Dans l’onglet Modèles , sélectionnez `Conversational Group`
* Un nom `Gymnastics`
   * Modifiez son paramètre en `Member Only Group` (abonnement restreint)
   * Dans l’onglet Modèles , sélectionnez `Conversational Group`

**Avis**:

* Une actualisation de la page peut s’avérer nécessaire avant l’affichage des deux groupes.
* Ce modèle n’inclut *pas* la fonction de groupes. Il ne sera donc plus possible d’imbriquer les groupes.
* Sur l’auteur, la variable [Console Groupes](groups.md) fournit un troisième choix : une `Public Group` (abonnement facultatif)

Une fois les deux groupes créés, sélectionnez le groupe Baseball, un groupe ouvert, et notez ses liens : `Discussions` `What's New` `Members`
Les liens du groupe s&#39;affichent sous les liens du site principal et donnent les résultats suivants :

![chlimage_1-319](assets/chlimage_1-319.png)

Sur l’instance de création, avec les privilèges d’administrateur, accédez à la [Console Groupes de communautés](members.md) et ajoutez Weston McCall au `Community Engage Gymnastics <uid> Members` groupe.

Continuez à publier, déconnectez-vous en tant qu’Aaron McDonald et affichez les groupes du groupe Sports en tant que visiteur anonyme du site :

* Depuis la page d’accueil
* Sélectionner `Groups`link
* Sélectionner `Sports`link
* Sélectionnez le Sports `Groups`link

Seul le groupe de baseball sera visible.

Connectez-vous en tant que Weston McCall (weston.mccall@dodgit.com/password) et accédez au même emplacement. Remarquez que Weston peut `Join` l’ouverture `Baseball` et soit `enter or Leave` le privé `Gymnastics`groupe.

![chlimage_1-320](assets/chlimage_1-320.png)

## Lien de page web {#web-page-link}

Affichez la page Web de base incluse dans le site en sélectionnant le lien Page Web . Les outils de création d’AEM standard peuvent être utilisés pour ajouter du contenu à cette page dans l’environnement de création.

Par exemple, accédez à **author** ouvrez l’instance `engage` dans le dossier [Console Sites Communities](sites-console.md), sélectionnez la variable **Ouvrir le site** pour accéder au mode d’édition de l’auteur. Sélectionnez ensuite le mode Aperçu pour sélectionner le `Web Page`puis sélectionnez le mode d’édition pour ajouter les composants Titre et Texte . Enfin, republiez uniquement la page ou l’ensemble du site.

![chlimage_1-321](assets/chlimage_1-321.png)

## Lien d’administration {#administration-link}

Lorsque le membre de la communauté dispose de privilèges de modération, le lien Administration est visible et sa sélection affiche le contenu de la communauté publié et lui permet d’être [modéré](moderate-ugc.md) d’une manière semblable à la fonction [console de modération](moderation.md) dans l’environnement de création.

Utilisez le bouton Précédent du navigateur pour revenir au site publié. La plupart des consoles ne sont pas accessibles à partir de la navigation globale dans l’environnement de publication.

![chlimage_1-322](assets/chlimage_1-322.png)

## Auto-inscription {#self-registration}

Une fois déconnecté, il est possible de créer un nouvel enregistrement d’utilisateur.

* Sélectionner `Log In`
* Sélectionner `Sign up for a new account`

![chlimage_1-323](assets/chlimage_1-323.png) ![chlimage_1-324](assets/chlimage_1-324.png)

Par défaut, l’adresse électronique est l’identifiant de connexion. Si cette option n’est pas cochée, le visiteur peut saisir son propre identifiant de connexion (nom d’utilisateur). Le nom d’utilisateur doit être unique dans l’environnement de publication.

Après avoir spécifié le nom, l’adresse électronique et le mot de passe de l’utilisateur, sélectionnez `Sign Up`crée l’utilisateur et lui permet de le signer.

Une fois connecté, la première page présentée est leur `Profile`, qu’ils peuvent personnaliser.

![chlimage_1-325](assets/chlimage_1-325.png)

Si le membre oublie son identifiant de connexion, il est possible de le récupérer en utilisant son adresse email.

![chlimage_1-326](assets/chlimage_1-326.png)
