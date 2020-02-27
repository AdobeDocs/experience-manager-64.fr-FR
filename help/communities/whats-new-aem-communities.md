---
title: Nouveautés des communautés AEM 6.4
seo-title: Nouveautés des communautés AEM 6.4
description: 'null'
seo-description: 'null'
uuid: e4bf343c-59cd-48ac-bee4-85db109e4c65
contentOwner: mgulati
discoiquuid: 3e3c867f-afb0-4402-94f4-16e1a556ddee
translation-type: tm+mt
source-git-commit: 3d2b91565e14e85e9e701663c8d0ded03e5b430c

---


# What&#39;s New in AEM 6.4 Communities {#what-s-new-in-aem-communities}

Les communautés AEM offrent une structure aux entreprises pour collaborer entre leurs partenaires, clients et employés. Il permet aux entreprises d&#39;engager et de transmettre des connaissances à leurs parties prenantes afin d&#39;améliorer la valeur de leur marque.

Les communautés AEM 6.4 intègrent des fonctionnalités qui améliorent l’expérience des utilisateurs de la communauté et simplifient les tâches quotidiennes des administrateurs, des modérateurs et des gestionnaires de la communauté.

Lisez plus loin pour découvrir rapidement les nouvelles fonctionnalités et améliorations. Also, see AEM 6.4 Communities [release notes](../release-notes/communities-release-notes.md). Pour consulter la documentation des communautés AEM 6.4, consultez le Guide [d’utilisation des communautés](home.md)AEM 6.4.

## Gestion des sous-communautés ou des groupes communautaires {#managing-sub-communities-or-community-groups}

Les communautés AEM permettent aux administrateurs de communautés de créer des groupes et des sous-groupes dans le site des communautés, à l’aide de modèles prédéfinis, dans l’environnement de création. Ces groupes servent de sous-communautés, qui peuvent hériter de nombreuses configurations, telles que les thèmes et le style du site parent. Toutefois, ces groupes peuvent différer du site parent, par exemple s’ils disposent d’un ensemble différent de modérateurs de groupe ou s’ils peuvent varier au niveau de sécurité. Ces groupes fonctionnent comme des mini-communautés indépendantes à part entière, qui sont renforcées par les améliorations suivantes.

### Création de groupes de différents paramètres régionaux en une seule étape {#create-multi-locale-groups-in-single-step}

Dans le cadre d’un site communautaire, des groupes multilingues peuvent être créés en une seule opération. **[!UICONTROL Le champ Langue(s)]** de groupe(s) de communauté disponible(s) **[!UICONTROL supplémentaire(s) dans la page Modèle]** de groupe de [communauté, disponible lors de la création d’un](groups.md) nouveau groupede communauté dans un site de communauté, le rend possible.

![multilingualgroup-1](assets/multilingualgroup-1.png)

Pour créer de tels groupes, les utilisateurs peuvent simplement accéder à la collection de groupes du site de communautés souhaité à partir de la console Sites. Créez un groupe et spécifiez les langues souhaitées dans le champ Langue(s) **** supplémentaire(s) du groupe de communautés disponible de la page Modèle **[!UICONTROL de groupe de]** communautés.

### Supprimer des groupes de communautés de la console Groupes {#delete-community-groups-from-groups-console}

AEM 6.4 Communities fournit l’icône Supprimer le groupe sur les groupes de communautés existants, dans la collection Groupes de communautés dans la console Sites de la communauté. Cela permet la suppression [d’un](groups.md#deleting-the-group) groupe en un seul clic, ainsi que la suppression de tous les éléments associés (tels que le contenu et les abonnements utilisateur) au groupe.

![deletegrp](assets/deletegrp.png)

### Création et affectation de ressources d’activation dans des groupes {#create-and-assign-enablement-resources-within-groups}

Le contenu d’apprentissage peut désormais être créé, géré et publié pour un ensemble spécifique de membres ciblés de la communauté. En raison de la disponibilité des fonctions de catalogue et d&#39;affectation pour les groupes de la communauté (et pas seulement pour l&#39;ensemble du site de la communauté), les gestionnaires de l&#39;activation peuvent [affecter des ressources](resource.md) d&#39;activation et un chemin d&#39;apprentissage à un petit groupe de personnes également.

![assignmentcatalog](assets/assignmentcatalog.png)

## Modération du contenu généré par l’utilisateur {#moderating-user-generated-content}

Les communautés AEM 6.4 offrent peu d’améliorations à la modération, qui sont essentielles pour faciliter la vie quotidienne des modérateurs de la communauté.

### Détection automatique du contenu indésirable  {#automatic-spam-detection}

Le nouveau moteur de détection du spam permet de filtrer le contenu généré par les utilisateurs non désirés et non sollicités sur les sites ou groupes de la communauté. Lorsqu’elle est activée, cette fonctionnalité peut marquer un élément de contenu généré par l’utilisateur comme indésirable ou non indésirable, en fonction d’un ensemble prédéfini de mots de ce type. Les modérateurs peuvent agir sur le contenu pour le refuser ou le laisser apparaître sur l’instance de publication. Ces actions de modération peuvent être exécutées en ligne ou via la console de modération en bloc.

![spamdetection-1](assets/spamdetection-1.png)

[Le détecteur](moderate-ugc.md#spam-detection) de messages indésirables détecte et signale un élément donné du contenu généré par l’utilisateur avec une précision de 90 %. Toutefois, cette fonctionnalité n’est pas activée par défaut. Pour l&#39;activer, les administrateurs de la communauté doivent accéder à configMgr sur le système/la console et ajouter le processus de spam.

![spamprocess-1](assets/spamprocess-1.png)

### Nouveaux filtres (Réponse/Sans réponse) pour QnA {#new-answered-unanswered-filters-for-qna}

AEM 6.4 ajoute deux [nouveaux filtres](moderation.md#filter-rail), nommés Répondu et Non répondu pour les questions QnA, à la console de modération en bloc. Ces filtres sont disponibles sous Statut dans le rail de filtre.

![états](assets/statuses.png)

Lors de la sélection de l’état Réponse, toutes les questions auxquelles le modérateur répond sont visibles dans la zone de contenu. Alors que si seul l’état Non répondu est sélectionné, le modérateur verra tout le contenu (pour tous les types de contenu), à l’exception des questions auxquelles il a répondu, car la propriété responsable de la Question avec réponse n’existe pas dans le cas des questions sans réponse et d’autres contenus tels que le sujet du forum, l’article de blog ou les commentaires.

### Marquage avec signet des filtres de modération {#bookmark-moderation-filters}

Les communautés AEM permettent de [mettre en signet les filtres](moderation.md#filter-rail) de modération prédéfinis sur la console de modération. Ces signets enregistrés peuvent être réexaminés ultérieurement et partagés avec d’autres utilisateurs.

Les utilisateurs doivent simplement sélectionner les filtres souhaités dans le rail de filtre de la console de modération, pour afficher l’UGC filtré et mettre en signet les filtres sur leurs navigateurs. Ces filtres sont ajoutés à la fin de la chaîne d’URL. Ils peuvent donc être partagés, réutilisés et réexaminés ultérieurement.

## Gestion des sites de la communauté {#managing-community-sites}

Les communautés AEM 6.4 apportent des améliorations à la gestion du site, qui garantissent que de nombreux sites communautaires dans une langue différente sont facilement créés, gérés et supprimés par les administrateurs du site.

### Créer des sites de communauté multilingue en une seule étape {#create-multi-locale-community-sites-in-one-step}

Les communautés AEM permettent de créer des sites [communautaires](create-site.md) multilingues en une seule opération. Cela est possible en raison de la disponibilité de plusieurs langues à sélectionner dans le champ Langue **[!UICONTROL de base du site]** communautaire de la page Modèle **[!UICONTROL de]** site, tout en créant un nouveau site communautaire à partir de la console des sites.

![multilocalesite](assets/multilocalesite.png)

Les utilisateurs peuvent sélectionner simultanément des dossiers de configuration, des marques et de nombreuses autres configurations pour tous ces sites.

### Supprimer les sites de la communauté de la console Sites {#delete-community-sites-from-sites-console}

AEM 6.4 Communities fournit l’icône Supprimer le site sur les sites communautaires existants, dans la console Sites communautaires. Cela permet la [suppression du site](create-site.md) et des éléments associés en un seul clic.

![siteactions](assets/siteactions.png)

## Managing UGC and user profiles {#managing-ugc-and-user-profiles}

Tout en maintenant la protection des données utilisateur au coeur de l’expérience des communautés, les communautés AEM exposent [des API prêtes à l’emploi](user-ugc-management-service.md) et [échantillonnent des servlets](https://github.com/Adobe-Marketing-Cloud/aem-communities-ugc-migration/tree/master/bundles/communities-ugc-management-servlet). Ces API permettent de gérer en bloc (suppression en masse et exportation en bloc) le contenu généré par l’utilisateur et de supprimer les profils utilisateur. Elles sont également essentielles pour gérer les demandes de conformité au RDDC de l’UE.

## Nouveautés {#what-s-changed}

* La vérification Captcha, lors de la création d’un nouveau site communautaire, n’est plus disponible en standard dans les communautés AEM 6.4. Cependant, le site des Communautés peut être personnalisé pour inclure le composant [Google reCAPTCHA](https://helpx.adobe.com/experience-manager/using/aem_recaptcha.html) pour une meilleure sécurité.
* L’option de téléchargement d’une page CSS personnalisée a été supprimée des sites de la communauté et du thème des groupes.
* Les icônes Contenu uniquement et Rechercher ont été ajoutées dans le rail de filtre de l’interface utilisateur de modération en bloc.
* Le filtre Chemin du contenu a été ajouté dans le rail de filtre de l’interface utilisateur de modération en bloc.
* Le passage au mode en masse et le mode de sortie en masse ont été supprimés de l’interface utilisateur de modération en bloc. Pour passer en mode de sélection multiple, cliquez sur l’icône Sélectionner ( ![sélecteur](assets/selecticon.png)) sur une publication, qui s’affiche lorsque vous passez la souris dessus (bureau) ou lorsque vous appuyez et maintenez un doigt sur la publication (mobile).
