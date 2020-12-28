---
title: Notes de mise à jour de Livefyre Feature Pack 2.0.6
seo-title: Notes de mise à jour de Livefyre Feature Pack 2.0.6
description: Notes de mise à jour de Livefyre Feature Pack 2.0.6
seo-description: Notes de mise à jour de Livefyre Feature Pack 2.0.6
uuid: 81ee0527-72c3-4530-80f1-c802ddbe62d0
products: SG_EXPERIENCEMANAGER/6.4
contentOwner: alba
discoiquuid: d445bcfb-7712-472f-bfb4-a8811c2bc4f1
translation-type: tm+mt
source-git-commit: f8ba597c62379ba413309303c2ad066ab7afce1e
workflow-type: tm+mt
source-wordcount: '657'
ht-degree: 5%

---


# Notes de mise à jour de Livefyre Feature Pack 2.0.6 {#livefyre-feature-pack-release-notes}

## Informations sur la version {#release-information}

| Produits | Livefyre Feature Pack 2.0.6 |
|--- |--- |
| Version | 2.0.6 |
| Type | Version de la fonctionnalité |
| Date | 31 août 2018 |
| URL de téléchargement | Contactez votre administrateur |
| Compatibilité (*) | aem 6.4 SP1, 6.4, 6.3 GA et 6.2 SP1 |
| Description | Ce module vous permet d&#39;intégrer les principales fonctionnalités de traitement de Livefyre à votre instance AEM, ce qui vous permet de publier en quelques minutes un contenu précieux généré par les utilisateurs (UGC) à partir des réseaux sociaux vers votre site. |

## Éléments inclus dans Livefyre Feature Pack 2.0.6 {#what-is-included-in-livefyre-feature-pack}

Ce package intègre les principales fonctionnalités de traitement du secteur de Livefyre à votre instance AEM, ce qui vous permet de publier en quelques minutes du contenu précieux généré par les utilisateurs (UGC) à partir des réseaux sociaux sur votre site. Ce package comprend trois composants différents :

**Importer du contenu UGC dans AEM Assets**

* Importez du contenu Twitter et Instagram généré par l’utilisateur (UGC) depuis Livefyre Studio vers AEM Assets à l’aide de l’importateur UGC.
* Accédez à votre bibliothèque Livefyre.
* Effectuez une recherche en temps réel sur Twitter et Instagram à l’aide de la fonction de recherche sur les réseaux sociaux Livefyre.
* Gérer les droits sur l’UGC.

**Ajouter les composants Livefyre à AEM Sites ou aux communautés**

* Créez et personnalisez instantanément des expériences dynamiques et attrayantes à l’aide d’une suite de composants sociaux, notamment des cartes, des galeries et des murs multimédia.
* Publiez l’UGC en AEM Sites ou dans les communautés.

**Importation de catalogues de produits dans Livefyre avec AEM Commerce**

* Intégrez en toute transparence votre catalogue de produits existant dans Livefyre afin d’attirer et de convertir les utilisateurs sur vos sites et de proposer des expériences de CU pouvant être consultées.
* Modifiez ou supprimez des éléments dans votre catalogue de produits commerciaux AEM et mettez automatiquement à jour les modifications dans Livefyre.

Pour obtenir de l’aide sur l’installation, voir [Intégration de Livefyre](https://docs.adobe.com/content/help/en/experience-manager-64/administering/integration/livefyre.html).

### Informations supplémentaires sur la version {#additional-release-information}

En raison des mises à jour affectant l&#39;agrégation du contenu des comptes d&#39;utilisateurs non-professionnels d&#39;Instagram, nous ne pouvons plus publier de commentaires en votre nom ni vérifier automatiquement les réponses de l&#39;auteur. [Cliquez ici pour en savoir plus](https://developers.facebook.com/blog/post/2018/04/04/facebook-api-platform-product-changes/).

>[!NOTE]
>
>Livefyre Feature Pack 2.0.6 ne prend pas en charge AEM interface utilisateur classique.

#### Nouvelle fonctionnalité ou amélioration {#new-feature-or-improvement}

* Ajoute la possibilité de rechercher des comptes UGC avant de configurer des droits de demande de comptes sociaux dans Livefyre. Vous devez configurer des comptes sociaux pour demander des droits ou remplacer la demande de droits si vous possédez le contenu.
* Instagram et Twitter [Le flux de demande de droits UGC](https://docs.adobe.com/content/help/en/experience-manager-64/administering/integration/livefyre.html) a été mis à jour pour se conformer aux dernières API.
* L’état des droits et les actions appropriées s’affichent désormais sur l’écran de demande de droits.

#### Correctifs de bogues {#bug-fixes}

* Correction d’un problème en raison duquel la suppression d’un compte social dans Livefyre Studio utilisé pour la demande de droits entraînait une erreur lors du chargement de la bibliothèque UGC dans AEM.
* Correction d’un problème en raison duquel le nombre d’actifs dans Livefyre Studio ne correspondait pas au nombre d’actifs dans la bibliothèque AEM UGC.
* Correction d’un problème dans la bibliothèque UGC en raison duquel les résultats filtrés s’affichaient après la réinitialisation des options de filtre.
* Correction d’un problème AEM Commerce en raison duquel les boutons d’appel à l’action redirigeaient les utilisateurs vers une URL incorrecte.
* Correction d’un problème en AEM Sites en raison duquel le glissement et le dépôt de plusieurs composants dans l’espace réservé de parsys entraînait sa disparition.
* Correction d’un problème en raison duquel les comptes sociaux désactivés pouvaient être sélectionnés lors de l’envoi d’une demande de droits.
* Correction d’un problème en raison duquel le fait de faire glisser et de déposer l’UGC des ressources dans les sites générait une erreur.
* Correction d’un problème en raison duquel le fait de faire glisser et de déposer les composants Chat et Liveblog dans Sites ne créait pas l’application.
* Correction d’un problème en raison duquel l’application de commentaires générait une erreur lorsque les utilisateurs tentaient de commenter.
* Correction d’un problème en raison duquel l’ajout de Livefyre Media Wall App à un site créait un noeud supplémentaire dans le référentiel de contenu Java.
* Correction d’un problème en raison duquel des sauts de page et des erreurs de console se produisaient dans la recherche UGC Instagram.
* Correction d’un problème en raison duquel les icônes d’utilisateur Instagram généraient des erreurs d’API dans les ressources.
* Correction d’un problème en raison duquel l’application Reviews était ajoutée à un site sans format prédéfini.
* Correction d’un problème lié à la fonctionnalité d’interface utilisateur tactile et à la modification intégrée.
* Correction d’un problème en raison duquel une erreur se produisait lors de l’importation de certains fichiers d’image Instagram.
* Correction d’un problème en raison duquel le client HTTP Livefyre en AEM ne prenait pas en charge la configuration du proxy.
