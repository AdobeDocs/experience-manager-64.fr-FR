---
title: Notes de mise à jour de Livefyre Feature Pack 2.0.6
seo-title: Notes de mise à jour de Livefyre Feature Pack 2.0.6
description: Notes de mise à jour de Livefyre Feature Pack 2.0.6
seo-description: Notes de mise à jour de Livefyre Feature Pack 2.0.6
uuid: 81ee0527-72c3-4530-80f1-c802ddbe62d0
products: SG_EXPERIENCEMANAGER/6.4
contentOwner: alba
discoiquuid: d445bcfb-7712-472f-bfb4-a8811c2bc4f1
exl-id: e09d2d59-41f0-4cf2-bcf3-ec3dbc3b8474
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '657'
ht-degree: 5%

---

# Notes de mise à jour du pack de fonctionnalités Livefyre 2.0.6 {#livefyre-feature-pack-release-notes}

## Informations sur la version {#release-information}

| Produits | Livefyre Feature Pack 2.0.6 |
|--- |--- |
| Version | 2.0.6 |
| Type | Version de la fonctionnalité |
| Date | 31 août 2018 |
| URL de téléchargement | Contacter votre administrateur |
| Compatibilité (*) | AEM 6.4 SP1, 6.4, 6.3 GA et 6.2 SP1 |
| Description | Ce module vous permet d’intégrer les fonctionnalités de traitement de pointe de Livefyre à votre instance AEM, ce qui vous permet de publier en quelques minutes sur votre site du contenu généré par les utilisateurs à partir des réseaux sociaux. |

## Éléments inclus dans le pack de fonctionnalités Livefyre 2.0.6 {#what-is-included-in-livefyre-feature-pack}

Ce module intègre les principales fonctionnalités de traitement du secteur Livefyre à votre instance AEM, ce qui vous permet de publier en quelques minutes sur votre site du contenu créé par les utilisateurs (UGC) à partir des réseaux sociaux. Ce module contient trois composants différents :

**Importation de contenu UGC dans AEM Assets**

* Importez du contenu généré par l’utilisateur Twitter et Instagram de Livefyre Studio vers AEM Assets à l’aide de l’importateur de contenu créé par l’utilisateur.
* Accédez à votre bibliothèque Livefyre.
* Effectuez des recherches en temps réel sur Twitter et Instagram à l’aide de Livefyre Social Search.
* Gestion des droits sur le contenu généré par l’utilisateur.

**Ajout de composants Livefyre à AEM Sites ou Communities**

* Créez et personnalisez instantanément des expériences dynamiques et attrayantes à l’aide d’une suite de composants sociaux, notamment des cartes, des galeries et des murs multimédia.
* Publiez le contenu créé par l’utilisateur dans AEM Sites ou Communities.

**Importation de catalogues de produits dans Livefyre avec AEM Commerce**

* Intégrez en toute transparence votre catalogue de produits existant dans Livefyre afin de stimuler l’engagement et la conversion des utilisateurs sur vos sites et de proposer des expériences de contenu créé par l’utilisateur Shoppable.
* Modifiez ou supprimez des éléments dans votre catalogue de produits Commerce AEM et mettez automatiquement à jour les modifications dans Livefyre.

Pour obtenir de l’aide sur l’installation, voir [Intégration à Livefyre](https://docs.adobe.com/content/help/en/experience-manager-64/administering/integration/livefyre.html).

### Informations supplémentaires sur la version {#additional-release-information}

En raison des mises à jour affectant l’agrégation du contenu des comptes utilisateurs non professionnels d’Instagram, nous ne pouvons plus publier de commentaires en votre nom ni vérifier automatiquement les réponses de l’auteur. [Cliquez ici pour en savoir plus](https://developers.facebook.com/blog/post/2018/04/04/facebook-api-platform-product-changes/).

>[!NOTE]
>
>Livefyre Feature Pack 2.0.6 ne prend pas en charge AEM IU classique.

#### Nouvelle fonctionnalité ou amélioration {#new-feature-or-improvement}

* Ajout de la possibilité de rechercher du contenu créé par l’utilisateur avant de configurer des comptes de réseaux sociaux de demande de droits dans Livefyre. Vous devez configurer des comptes de réseaux sociaux pour demander des droits ou remplacer la demande de droits si vous possédez le contenu.
* Mise à jour du [workflow de demande de droits UGC](https://docs.adobe.com/content/help/en/experience-manager-64/administering/integration/livefyre.html) Instagram et Twitter pour se conformer aux dernières API -
* L’état des droits et les actions appropriées s’affichent désormais dans l’écran de demande de droits.

#### Correctifs de bogues {#bug-fixes}

* Correction d’un problème en raison duquel la suppression d’un compte social dans Livefyre Studio utilisé pour la demande de droits entraînait une erreur lors du chargement de la bibliothèque UGC dans AEM.
* Correction d’un problème en raison duquel le nombre de ressources dans Livefyre Studio ne correspondait pas au nombre de ressources dans la bibliothèque UGC AEM.
* Correction d’un problème dans la bibliothèque UGC en raison duquel les résultats filtrés s’affichaient après la réinitialisation des options de filtre.
* Correction d’un problème lié à AEM Commerce en raison duquel les boutons d’appel à l’action redirigeaient les utilisateurs vers une URL incorrecte.
* Correction d’un problème dans AEM Sites en raison duquel le fait de faire glisser plusieurs composants dans l’espace réservé parsys provoquait leur disparition.
* Correction d’un problème en raison duquel les comptes sociaux désactivés pouvaient être sélectionnés lors de l’envoi d’une demande de droits.
* Correction d’un problème en raison duquel le fait de faire glisser et déposer du contenu créé par l’utilisateur des ressources vers Sites générait une erreur.
* Correction d’un problème en raison duquel le fait de faire glisser des composants Chat et Liveblog dans Sites ne créait pas l’application.
* Correction d’un problème en raison duquel l’application de commentaires produisait une erreur lorsque les utilisateurs tentaient de commenter.
* Correction d’un problème en raison duquel l’ajout de l’application Mur multimédia Livefyre à un site créait un noeud supplémentaire dans le référentiel de contenu Java.
* Correction d’un problème qui provoquait des sauts de page et des erreurs de console dans la recherche de contenu créé par l’utilisateur Instagram.
* Correction d’un problème en raison duquel les icônes d’utilisateur d’Instagram généraient des erreurs d’API dans Assets.
* Correction d’un problème en raison duquel l’application Révisions était ajoutée à un site sans format prédéfini.
* Correction d’un problème lié à la fonctionnalité d’interface utilisateur tactile et à la modification en ligne.
* Correction d’un problème provoquant une erreur lors de l’importation de certaines ressources d’image Instagram.
* Correction d’un problème en raison duquel le client HTTP Livefyre dans AEM ne prenait pas en charge la configuration du proxy.
