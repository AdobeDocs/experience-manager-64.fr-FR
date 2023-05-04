---
title: Concept de la création
seo-title: Concept of Authoring
description: Concepts de création dans AEM
seo-description: Concepts of authoring in AEM
uuid: 824c8b91-07c7-471b-b3aa-5a73d6d48414
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: introduction
content-type: reference
discoiquuid: 72ee013a-7a60-41ee-9421-2846e4c6bc68
exl-id: 23e30de9-1a30-484a-b370-f9f0d45b4e41
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '583'
ht-degree: 68%

---

# Concept de création et de publication{#authoring}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

AEM fournit deux environnements :

* Création
* Publication

Ces fonctions interagissent pour vous permettre de rendre le contenu disponible sur votre site web, de sorte que vos visiteurs puissent le lire.

L’environnement de création fournit les mécanismes de création, de mise à jour et de révision de ce contenu avant de le publier :

* Un auteur crée et révise le contenu (qui peut être de plusieurs types, par exemple des pages, des ressources, des publications, etc.)
* qui, à un moment donné, sera publié sur votre site Web.

![chlimage_1-289](assets/chlimage_1-289.png)

Dans l’environnement de création, les fonctions d’AEM sont accessibles dans deux interfaces utilisateur. Dans l’environnement de publication, vous concevez l’aspect de l’interface proposée aux utilisateurs.

## Environnement de création {#author-environment}

L’auteur travaille dans ce qu’on appelle l’**[environnement de création](/help/sites-authoring/home.md)**. Il s’agit d’une interface facile à utiliser (interface utilisateur graphique) pour créer le contenu. En fait, cette interface se trouve habituellement derrière le pare-feu d’une entreprise qui fournit une protection complète et implique que l’auteur se connecte à l’aide d’un compte doté des droits d’accès appropriés.

>[!NOTE]
>
>Votre compte doit disposer des droits d’accès appropriés pour créer, modifier ou publier du contenu.

Selon la configuration de votre instance et de vos droits d’accès personnels, vous pouvez effectuer de nombreuses tâches sur votre contenu, notamment :

* générer du nouveau contenu ou modifier du contenu existant sur une page ;
* utiliser les modèles prédéfinis pour créer des pages de contenu ;
* créer, modifier et gérer vos ressources et collections ;
* créer, modifier et gérer vos publications ;
* développer vos campagnes et les ressources associées ;
* développer et gérer des sites communautaires ;
* déplacer, copier ou supprimer des pages de contenu, des ressources, etc. ;
* publier (ou annuler la publication) des pages, des ressources, etc.

Certaines tâches administratives peuvent aussi vous aider à gérer votre contenu :

* workflow qui déterminent le mode de gestion des modifications ; par exemple, application d’une révision avant publication
* projets qui coordonnent des tâches individuelles

>[!NOTE]
>
>AEM est également [administré](/help/sites-administering/home.md) (pour la plupart des tâches) à partir de l’environnement de création.

## Environnement de publication {#publish-environment}

Une fois prêt, le contenu du site AEM est publié dans l’**environnement de publication**. Ici, vos pages sont mises à la disposition de l’audience prévue, en fonction de l’aspect global de l’interface que vous avez conçue.

En règle générale, l’environnement de publication se trouve à l’intérieur de la zone démilitarisée ; en d&#39;autres termes, disponible sur l&#39;internet, mais plus sous la pleine protection du réseau interne.

Lorsque le site AEM est un [site communautaire](/help/communities/overview.md), ou inclut des [composants de Communities](/help/communities/author-communities.md), des utilisateurs (membres) connectés peuvent interagir avec les fonctions de Communities. Par exemple, ils peuvent interagir sur un forum, publier un commentaire ou suivre d’autres membres. Les membres peuvent être autorisés à effectuer des activités normalement réservées à l’environnement de création, telles que la création de nouvelles pages (groupes de communautés), d’articles de blog et la modération des publications d’autres membres.

>[!NOTE]
>
>Il existe malheureusement une interférence dans la terminologie utilisée. Cela peut se produire avec les fonctions suivantes :
>
>* **Publier/dépublier**
   >  Termes principalement utilisés pour évoquer les opérations qui rendent votre contenu publiquement accessible dans votre environnement de publication (ou non).
>
>* **Activer/Désactiver**
   >  Ces termes sont synonymes de publication/dépublication. Elles sont plus courantes dans l’IU classique.
>
>* **Répliquer/Réplication**
   >  Ces termes techniques décrivent le déplacement des données (par exemple de contenu de la page, de fichiers, de code, de commentaires de l’utilisateur) d’un environnement à un autre ; par ex., lors de la publication ou de la réplication inverse des commentaires d’utilisateur.
>


## Dispatcher {#dispatcher}

Afin que les visiteurs de votre site Web bénéficient de performances optimales, le **[Dispatcher](https://helpx.adobe.com/fr/experience-manager/dispatcher/user-guide.html)** met en œuvre des mécanismes de mise en cache et d’équilibrage de la charge.
