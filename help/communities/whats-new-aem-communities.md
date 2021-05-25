---
title: Nouveautés d’AEM 6.4 Communities
description: AEM Communities offre un cadre aux entreprises pour collaborer entre leurs partenaires, clients et employés.
uuid: e4bf343c-59cd-48ac-bee4-85db109e4c65
contentOwner: mgulati
discoiquuid: 3e3c867f-afb0-4402-94f4-16e1a556ddee
exl-id: fcdc65c9-929d-4a87-8ff7-5e3cf5711fd9
source-git-commit: 1a7ecec2f3c2618bb6d0280a8f9a66754cd8a1a3
workflow-type: tm+mt
source-wordcount: '1040'
ht-degree: 1%

---

# Nouveautés d’AEM 6.4 Communities {#what-s-new-in-aem-communities}

AEM Communities offre un cadre aux entreprises pour collaborer entre leurs partenaires, clients et employés. Il transmet des capacités sociales à la structure du site web et aide les entreprises à impliquer et à transmettre des connaissances à leurs parties prenantes, afin d’améliorer la valeur de leur marque à leur manière.

AEM 6.4 Communities offre des fonctionnalités pour améliorer l’expérience des utilisateurs de la communauté et faciliter les tâches quotidiennes des administrateurs, des modérateurs et des gestionnaires de la communauté.

Pour une introduction rapide aux nouvelles fonctionnalités et améliorations, reportez-vous à la section . Voir également les [notes de mise à jour d’AEM 6.4 Communities](../release-notes/communities-release-notes.md). Pour accéder à la documentation d’AEM 6.4 Communities, consultez le [Guide de l’utilisateur d’AEM 6.4 Communities](home.md).

## Gestion des sous-communautés ou des groupes communautaires {#managing-sub-communities-or-community-groups}

AEM Communities permet aux administrateurs de la communauté de créer des groupes et des sous-groupes sur le site des communautés, à l’aide de modèles prédéfinis, dans l’environnement de création. Ces groupes servent de sous-communautés, qui peuvent hériter de nombreuses configurations, telles que les thèmes et le style du site parent. Cependant, ces groupes peuvent différer du site parent, par exemple s’ils disposent d’un ensemble différent de modérateurs de groupe ou peuvent varier au niveau de sécurité. Ces groupes fonctionnent comme des mini-communautés indépendantes et à part entière, qui sont dotées des améliorations suivantes.

### Création de groupes de différents paramètres régionaux en une seule étape {#create-multi-locale-groups-in-single-step}

Dans le cadre d’un site de communauté, les groupes multilingues peuvent être créés en une seule opération. **[!UICONTROL Le champ]** Langue(s) de groupe de communauté disponible(s) supplémentaire(s) dans le  **[!UICONTROL modèle de groupe de]** communauté, disponible lors de la création d’un  [nouveau ](groups.md) groupe de communauté dans un site de communauté, rend cela possible.

![multilingualgroup-1](assets/multilingualgroup-1.png)

Pour créer ces groupes, les utilisateurs peuvent simplement accéder à la collection de groupes du site des communautés souhaité à partir de la console Sites. Créez un groupe et indiquez les langues souhaitées dans le champ **[!UICONTROL Langue(s) du groupe de la communauté disponible supplémentaire]** de la page **[!UICONTROL Modèle du groupe de la communauté]**.

### Supprimer des groupes de communautés de la console des groupes {#delete-community-groups-from-groups-console}

AEM 6.4 Communities fournit l’icône Supprimer le groupe sur les groupes de communautés existants, dans la collection Groupes de communautés dans la console Sites de la communauté. Cela active la [suppression de groupe](groups.md#deleting-the-group) en un seul clic, ainsi que la suppression de tous les éléments associés (tels que le contenu et les appartenances utilisateur) au groupe.

![deletegrp](assets/deletegrp.png)

### Créer et attribuer des ressources d’activation dans des groupes {#create-and-assign-enablement-resources-within-groups}

Le contenu d’apprentissage peut désormais être créé, géré et publié pour un ensemble spécifique de membres ciblés de la communauté. En raison de la disponibilité des fonctions de catalogue et d’affectation pour les groupes de communautés (et pas seulement pour l’ensemble du site de la communauté), les gestionnaires d’activation peuvent [affecter des ressources d’activation](resource.md) et un parcours d’apprentissage à un petit groupe de personnes également.

![assignmentcatalog](assets/assignmentcatalog.png)

## Modération du contenu généré par l’utilisateur {#moderating-user-generated-content}

AEM 6.4 Communities offre peu d’améliorations à la modération, qui sont essentielles pour faciliter la vie quotidienne des modérateurs de la communauté.

### Détection automatique du contenu indésirable  {#automatic-spam-detection}

Le nouveau moteur de détection des emails indésirables permet de filtrer le contenu non souhaité et non sollicité généré par les utilisateurs sur les sites ou groupes de la communauté. Lorsqu’elle est activée, cette fonctionnalité peut marquer un élément de contenu généré par l’utilisateur comme indésirable ou non indésirable en fonction d’un ensemble prédéfini de mots indésirables. Les modérateurs peuvent agir sur le contenu pour le refuser ou l’autoriser à apparaître sur l’instance de publication. Ces actions de modération peuvent être exécutées en ligne ou par le biais de la console de modération en bloc.

![spamdétection-1](assets/spamdetection-1.png)

[Le ](moderate-ugc.md#spam-detection) détecteur de spam détecte et marque un élément donné de contenu généré par l’utilisateur avec une précision de 90 %. Toutefois, cette fonctionnalité n’est pas activée par défaut. Pour l’activer, les administrateurs de la communauté doivent accéder à configMgr sur le système/la console et ajouter Spam Process.

![spamprocess-1](assets/spamprocess-1.png)

### Nouveaux filtres (réponses/sans réponse) pour Q&amp;R {#new-answered-unanswered-filters-for-qna}

AEM 6.4 ajoute deux [nouveaux filtres](moderation.md#filter-rail), nommés Répondu et Non répondu pour les questions Q&amp;R, à la console de modération en bloc. Ces filtres sont disponibles sous État dans le rail de filtres.

![stats](assets/statuses.png)

Lorsque vous sélectionnez l’état Répondu , toutes les questions qui ont reçu une réponse sont visibles par le modérateur dans la zone de contenu. En revanche, si seul l’état Non reçu est sélectionné, le modérateur verra tout le contenu (pour tous les types de contenu), à l’exception des questions auxquelles il a répondu, car la propriété responsable de la Question à laquelle il a répondu n’existe pas dans le cas de questions sans réponse et d’autres contenus tels que le sujet du forum, l’article de blog ou les commentaires.

### Marquage avec signet des filtres de modération {#bookmark-moderation-filters}

AEM Communities permet de [marquer d’un signet les filtres de modération prédéfinis](moderation.md#filter-rail) sur la console de modération. Ces signets enregistrés peuvent être revus ultérieurement et partagés avec d’autres utilisateurs.

Les utilisateurs doivent simplement sélectionner les filtres de votre choix dans la console de modération, afin d’afficher le contenu généré par l’utilisateur filtré et de mettre en signet les filtres sur leur navigateur. Ces filtres sont ajoutés à la fin de la chaîne d’URL et peuvent donc être partagés, réutilisés et revus ultérieurement.

## Gestion des sites de la communauté {#managing-community-sites}

AEM 6.4 Communities fournit des améliorations à la gestion de site, qui permettent de créer, gérer et supprimer facilement de nombreux sites communautaires dans différentes langues par les administrateurs de site.

### Créer des sites de communauté multilocale en une seule étape {#create-multi-locale-community-sites-in-one-step}

AEM Communities permet de créer des [sites de communauté multilingues](create-site.md) en une seule opération. Cela est possible en raison de la disponibilité de plusieurs langues dans lesquelles effectuer un choix dans le champ **[!UICONTROL Langue de base du site de la communauté]** de la page **[!UICONTROL Modèle de site]**, lors de la création d’un site de communauté à partir de la console Sites.

![multilocalesite](assets/multilocalesite.png)

Les utilisateurs peuvent sélectionner simultanément des dossiers de configuration, des marques et de nombreuses autres configurations pour tous ces sites.

### Supprimer des sites communautaires de la console Sites {#delete-community-sites-from-sites-console}

AEM 6.4 Communities fournit l’icône Supprimer le site sur les sites de communauté existants, dans la console Sites de la communauté. Cela permet la [suppression du site](create-site.md) et des éléments associés en un seul clic.

![siteactions](assets/siteactions.png)

## Gestion du contenu généré par l’utilisateur et profils utilisateur {#managing-ugc-and-user-profiles}

En maintenant la protection des données utilisateur au coeur de l’expérience des communautés, AEM Communities expose les [API prêtes à l’emploi](user-ugc-management-service.md) et [exemple de servlet](https://github.com/Adobe-Marketing-Cloud/aem-communities-ugc-migration/tree/main/bundles/communities-ugc-management-servlet). Ces API permettent de gérer en masse (suppression et exportation en masse) le contenu généré par les utilisateurs et de supprimer les profils utilisateur. Elles jouent également un rôle essentiel dans le traitement des demandes de conformité au RGPD de l’UE.

## Modifications {#what-s-changed}

* La vérification de Captcha, lors de la création d&#39;un nouveau site communautaire, n&#39;est plus disponible d&#39;usine dans AEM 6.4 Communities. Cependant, le site Communities peut être personnalisé pour inclure [le composant Google reCAPTCHA](https://helpx.adobe.com/experience-manager/using/aem_recaptcha.html) pour une meilleure sécurité.
* L’option de téléchargement d’une page CSS personnalisée a été supprimée du thème des sites et groupes de la communauté.
* Les icônes Contenu uniquement et Recherche ont été ajoutées dans le rail de filtrage de l’interface utilisateur de modération en bloc.
* Le filtre Chemin d’accès au contenu a été ajouté dans le rail de filtre de l’interface utilisateur de modération en bloc.
* Le passage en mode masse et la sortie du mode en bloc ont été supprimés de l’interface utilisateur de modération en bloc. Pour entrer en mode à sélection multiple, cliquez sur l’icône Sélectionner ( ![sélecteur](assets/selecticon.png)) sur une publication, qui s’affiche lorsque vous pointez dessus avec la souris (bureau) ou lorsque vous appuyez et tenez un doigt sur la publication (mobile).
