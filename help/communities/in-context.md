---
title: Modération dans le contexte
seo-title: In-Context Moderation
description: Comment effectuer des actions de modérateur
seo-description: How to perform moderator actions
uuid: 282a8bea-2822-4e5c-b9f4-4d9a5380d895
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: ee104f6f-123b-4a6e-9031-849fc1318cc5
role: Admin
exl-id: a7678273-81f6-4089-ac73-2458d940e374
source-git-commit: 3c050c33a384d586d74bd641f7622989dc1d6b22
workflow-type: tm+mt
source-wordcount: '789'
ht-degree: 1%

---

# Modération dans le contexte {#in-context-moderation}

Pour AEM Communities, la modération peut être effectuée par les administrateurs et les membres de la communauté de confiance directement sur la page publiée où le contenu de la communauté a été publié.

Lors de l’utilisation d’un [console de modération](moderation.md), les informations affichées pour le contenu incluent un lien vers la page publiée afin de permettre l’accès à d’autres actions de modération disponibles lors de la modération dans le contexte.

## Actions de modération {#moderation-actions}

Visitez la présentation de la modération pour obtenir une description de [actions de modération](moderate-ugc.md#moderation-actions).

## Interface utilisateur de la modération {#moderation-ui}

L’interface utilisateur présentée au modérateur sur l’instance de publication se trouve dans la boîte de dialogue pour la publication et la gestion du contenu généré par l’utilisateur. Les éléments de l’interface utilisateur sont déterminés par l’état du visiteur du site, qu’ils soient ou non...

1. Le membre qui a publié le contenu
1. Un membre de confiance modérateur
1. Un administrateur
1. Connecté, mais pas un administrateur, un modérateur ni un auteur du contenu.
1. Non connecté

## Exemple {#example}

En utilisant la variable [Geometrixx Engage](http://localhost:4503/content/sites/engage/en.html) site créé lorsque [Prise en main d’AEM Communities](getting-started.md), il est possible de configurer rapidement un thread dans un forum sur lequel expérimenter diverses activités de modération dans l’environnement de publication, comme illustré ci-dessous.

Aaron McDonald (aaron.mcdonald@mailinator.com) a été identifié en tant que membre de la communauté de confiance en l’ajoutant au groupe de la communauté-engage-modérateurs lors de la création du site.

Rebekah Larsen (rebekah.larsen@trashymail.com) peut être ajouté en tant que membre du groupe communautaire-engage-members à l’aide de la variable [Console Membres](members.md).

Pour plus d’informations sur les groupes d’utilisateurs de la communauté, consultez [Gestion des utilisateurs et des groupes d’utilisateurs](users.md).

### Création de publications de forum {#create-the-forum-posts}

* Connectez-vous en tant que Rebekah Larsen (rebekah.larsen@trashymail.com)

   * Sélectionner un forum
   * Sélectionner une nouvelle publication
   * Saisie de l’objet

      Quand changer le nectar dans le mangeur d&#39;oiseaux Humming

   * Entrez le texte du corps

      Je n&#39;ai pas eu beaucoup de succès quand je raccroche une mangeoire d&#39;oiseaux colibris chaque année. Il semble qu&#39;ils viennent un jour ou deux alors c&#39;est tout. Je le change une fois par semaine est-ce trop long ? Ai-je besoin de le modifier plus tôt ?
   * Sélectionner une publication
   * Sélectionner Déconnexion

* Connectez-vous en tant qu’Aaron McDonald (aaron.mcdonald@mailinator.com)

   * Sélectionner un forum
   * Pour la rubrique &quot;Hummingbird&quot;, sélectionnez En savoir plus
   * Saisissez le commentaire correspondant à la fonction Publier la réponse .

      Je change la mienne une fois par semaine et je les reçois de mai à octobre.

   * Sélectionner une réponse
   * Sélectionner Déconnexion

* Connectez-vous en tant qu’Andrew Schaeffer (andrew.schaeffer@trashymail.com)

   * Sélectionner un forum
   * Pour la rubrique &quot;Hummingbird&quot;, sélectionnez En savoir plus
   * Saisissez le commentaire correspondant à la fonction Publier la réponse .

      Je vends du nectar et des mangeoires - visitez https://my.viral.url/

   * Sélectionner une réponse
   * Sélectionner Déconnexion

### Visiteur anonyme du site (#5) {#anonymous-site-visitor}

Vous trouverez ci-dessous un aperçu du forum consulté par un visiteur du site qui n’est pas connecté (5).

Un visiteur anonyme du site ne peut afficher que le forum, mais ne peut pas publier de contenu ni effectuer d’actions de modération.

![chlimage_1](assets/chlimage_1.png)

### Nouveau membre (#4) {#new-member}

Sur l’auteur, connectez-vous en tant qu’administrateur et ajoutez Boyd Larsen (boyd.larsen@dodgit.com) en tant que nouveau membre du groupe community-engage-members à l’aide de la variable [Console Membres](members.md), puis déconnectez-vous.

Lors de la publication, connectez-vous en tant que Boyd Larsen et accédez au thread en sélectionnant `Forum`, puis `Read more` pour le billet colibri.

Avis

* Boyd n&#39;a pas participé au forum
* Boyd ne peut rien supprimer
* Boyd est connecté et peut répondre ou marquer du contenu

Have Boyd sélectionnez Flag pour marquer le contenu publié par Andrew.

Déconnexion

![chlimage_1-1](assets/chlimage_1-1.png)

### Administrateur (#3) {#administrator}

Connectez-vous en tant qu’administrateur (admin) et accédez au fil en sélectionnant Forum, puis Lire plus pour une publication.

Avis

* L’administrateur peut marquer, supprimer, modifier, refuser, couper, fermer, épingler, fonction
* L’administrateur peut sélectionner Administration pour accéder à la console de modération.

![community-admin-forum](assets/communityadmin-forum.png)

Sélectionnez l’élément de menu Administration pour accéder à [console de modération](moderation.md) dans l’environnement de publication.

Notez que, pour un administrateur, tout le contenu modérable est visible, et pas seulement le contenu du site de la communauté Geometrixx Engage.

Le filtre de recherche est un panneau latéral qui bascule entre ouverture et fermeture.

Déconnexion.

![modération-console-publication](assets/moderationconsole-publish.png)

### Modérateur de la communauté (#2) {#community-moderator}

Connectez-vous en tant qu’Aaron McDonald (aaron.mcdonal@mailinator.com), un modérateur de la communauté, et accédez au fil en sélectionnant Forum, puis En savoir plus pour la publication colibri.

Avis

* Aaron peut répondre, supprimer, modifier ou refuser sa propre publication.
* Aaron peut également marquer/autoriser, répondre, supprimer, modifier ou refuser tout autre contenu.
* Aaron peut couper le sujet du forum pour le déplacer vers un autre forum pour lequel il modérait
* Aaron peut sélectionner Administration pour accéder à la console de modération.

![chlimage_1-2](assets/chlimage_1-2.png)

Sélectionnez l’élément de menu Administration pour accéder à [console de modération](moderation.md) dans l’environnement de publication.

Notez que, pour un modérateur de communauté, seul le contenu modérable du site de la communauté Geometrixx Engage est visible.

Notez que le modérateur de la communauté dispose des mêmes options que l’administrateur (l’image est avec la barre latérale de recherche activée), mais aucun accès aux autres consoles d’AEM.

Déconnexion.

![modérator access](assets/moderatoraccess.png)

### Auteur de contenu (#1) {#content-author}

Connectez-vous en tant que Rebekah Larsen (rebekah.larsen@mailinator.com), membre de la communauté qui a lancé le fil, et accédez au fil en sélectionnant Forum, puis En savoir plus pour la publication colibri.

Avis

* Rebekah peut supprimer ou modifier sa propre publication
* Rebekah peut également répondre ou marquer d’autres contenus
* Rebekah ne peut pas accéder à la console de modération

![chlimage_1-3](assets/chlimage_1-3.png)
