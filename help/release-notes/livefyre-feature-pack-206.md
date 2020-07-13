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
source-git-commit: f1bf1545689b977a0f5074954df224db58cbd695
workflow-type: tm+mt
source-wordcount: '653'
ht-degree: 7%

---


# Livefyre Feature Pack 2.0.6 Release Notes {#livefyre-feature-pack-release-notes}

## Informations sur la version {#release-information}

<table> 
 <tbody>
  <tr>
   <td>Produits</td> 
   <td>Livefyre Feature Pack 2.0.6</td> 
  </tr>
  <tr>
   <td>Version</td> 
   <td>2.0.6</td> 
  </tr>
  <tr>
   <td>Type</td> 
   <td>Version de la fonctionnalité</td> 
  </tr>
  <tr>
   <td>Date</td> 
   <td>31 août 2018</td> 
  </tr>
  <tr>
   <td>URL de téléchargement<br /> </td> 
   <td>Contactez votre administrateur</td> 
  </tr>
  <tr>
   <td>Compatibilité (*)</td> 
   <td>AEM 6.4 SP1, 6.4, 6.3 GA et 6.2 SP1</td> 
  </tr>
  <tr>
   <td>Description</td> 
   <td>Ce package vous permet d’intégrer les principales fonctionnalités de traitement de Livefyre à votre instance AEM, ce qui vous permet de publier en quelques minutes un contenu précieux généré par les utilisateurs à partir des réseaux sociaux vers votre site.</td> 
  </tr>
 </tbody>
</table>

## What is included in Livefyre Feature Pack 2.0.6 {#what-is-included-in-livefyre-feature-pack}

Ce package intègre les principales fonctionnalités de traitement du secteur de Livefyre à votre instance AEM, ce qui vous permet de publier en quelques minutes du contenu précieux généré par les utilisateurs (UGC) depuis les réseaux sociaux vers votre site. Ce package comprend trois composants différents :

**Importer du contenu UGC en AEM Assets**

* Importez du contenu Twitter et Instagram généré par l’utilisateur (UGC) de Livefyre Studio en AEM Assets à l’aide de l’importateur UGC.
* Accédez à votre bibliothèque Livefyre.
* Effectuez une recherche en temps réel sur Twitter et Instagram à l’aide de la fonction de recherche sur les réseaux sociaux Livefyre.
* Gérer les droits sur l’UGC.

**Ajouter les composants Livefyre aux AEM Sites ou aux communautés**

* Créez et personnalisez instantanément des expériences dynamiques et attrayantes à l’aide d’une suite de composants sociaux, notamment des cartes, des galeries et des murs multimédia.
* Publiez l’UGC en AEM Sites ou en communautés.

**Importation de catalogues de produits dans Livefyre avec AEM Commerce**

* Intégrez en toute transparence votre catalogue de produits existant dans Livefyre afin d’attirer et de convertir les utilisateurs sur vos sites et de proposer des expériences de CU pouvant être consultées.
* Modifiez ou supprimez des éléments dans votre catalogue de produits AEM Commerce et mettez automatiquement à jour les modifications dans Livefyre.

Pour obtenir de l’aide sur l’installation, voir [Intégration à Livefyre](https://helpx.adobe.com/fr/experience-manager/6-4/sites/administering/using/livefyre.html).

### Informations supplémentaires sur la version {#additional-release-information}

En raison des mises à jour affectant l&#39;agrégation du contenu des comptes d&#39;utilisateurs non-professionnels d&#39;Instagram, nous ne pouvons plus publier de commentaires en votre nom ni vérifier automatiquement les réponses de l&#39;auteur. [Cliquez ici pour en savoir plus](https://developers.facebook.com/blog/post/2018/04/04/facebook-api-platform-product-changes/).

>[!NOTE]
>
>Livefyre Feature Pack 2.0.6 ne prend pas en charge l’interface utilisateur d’AEM Classic.

#### Nouvelle fonctionnalité ou amélioration {#new-feature-or-improvement}

* Ajoute la possibilité de rechercher l’UGC avant de configurer des droits pour demander des comptes sociaux dans Livefyre. Vous devez configurer des comptes sociaux pour demander des droits ou remplacer la demande de droits si vous possédez le contenu.
* Le flux de travail [des demandes de droits](https://helpx.adobe.com/fr/experience-manager/6-4/sites/administering/using/livefyre.html) UGC Instagram et Twitter a été mis à jour pour se conformer aux dernières API.
* L’état des droits et les actions appropriées s’affichent désormais sur l’écran de demande de droits.

#### Correctifs {#bug-fixes}

* Correction d’un problème en raison duquel la suppression d’un compte social dans Livefyre Studio utilisé pour la demande de droits entraînait une erreur lors du chargement de la bibliothèque UGC dans AEM.
* Correction d’un problème en raison duquel le nombre de ressources dans Livefyre Studio ne correspondait pas au nombre de ressources dans la bibliothèque AEM UGC.
* Correction d’un problème dans la bibliothèque UGC en raison duquel les résultats filtrés s’affichaient après la réinitialisation des options de filtre.
* Correction d’un problème dans AEM Commerce en raison duquel les boutons d’appel à l’action redirigeaient les utilisateurs vers une URL incorrecte.
* Correction d’un problème en AEM Sites en raison duquel le glissement et le dépôt de plusieurs composants dans l’espace réservé de parsys entraînait leur disparition.
* Correction d’un problème en raison duquel les comptes sociaux désactivés pouvaient être sélectionnés lors de l’envoi d’une demande de droits.
* Correction d’un problème en raison duquel le fait de faire glisser et de déposer l’UGC des ressources dans les sites générait une erreur.
* Correction d’un problème en raison duquel le fait de faire glisser et de déposer des composants Chat et Liveblog dans Sites ne créait pas l’application.
* Correction d’un problème en raison duquel l’application de commentaires générait une erreur lorsque les utilisateurs tentaient de commenter.
* Correction d’un problème en raison duquel l’ajout de Livefyre Media Wall App à un site créait un noeud supplémentaire dans le référentiel de contenu Java.
* Correction d’un problème en raison duquel des sauts de page et des erreurs de console se produisaient dans la recherche UGC Instagram.
* Correction d’un problème en raison duquel les icônes d’utilisateur Instagram généraient des erreurs d’API dans les ressources.
* Correction d’un problème en raison duquel l’application Reviews était ajoutée à un site sans format prédéfini.
* Correction d’un problème lié à la fonctionnalité d’interface utilisateur tactile et à la modification intégrée.
* Correction d’un problème en raison duquel une erreur se produisait lors de l’importation de certains fichiers d’image Instagram.
* Correction d’un problème en raison duquel le client HTTP Livefyre dans AEM ne prenait pas en charge la configuration du proxy.

