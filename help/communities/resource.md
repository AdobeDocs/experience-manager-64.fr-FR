---
title: Créer et attribuer des ressources d’activation
seo-title: Créer et attribuer des ressources d’activation
description: Ajout de ressources d’activation
seo-description: Ajout de ressources d’activation
uuid: da940242-0c9b-4ad8-8880-61fd41461c3b
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: introduction
content-type: reference
discoiquuid: 8fe97181-600e-42ac-af25-d5d4db248740
exl-id: 9f447a54-4512-41ab-b8d3-327e751eda58
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '714'
ht-degree: 6%

---

# Créer et attribuer des ressources d’activation {#create-and-assign-enablement-resources}

## Ajouter une ressource d’activation {#add-an-enablement-resource}

Pour ajouter une ressource d’activation au nouveau site de la communauté :

* Sur l’instance de création
   * Par exemple, [http://localhost:4502/](http://localhost:4503/)
* Connexion en tant qu’administrateur système
* Dans la navigation globale, sélectionnez **Communautés > [Ressources](resources.md)**

   ![chlimage_1-199](assets/chlimage_1-199.png)
   ![chlimage_1-200](assets/chlimage_1-200.png)
* Sélectionnez le site de la communauté sur lequel des ressources d’activation sont ajoutées.
   * Sélectionner `Enablement Tutorial`
* Dans le menu, sélectionnez ` Create`
* Sélectionnez **[!UICONTROL Ressource]**

![chlimage_1-201](assets/chlimage_1-201.png)

### Informations de base {#basic-info}

Renseignez les informations de base de la ressource :

* **[!UICONTROL Nom du site]** : définissez sur le nom du site de communauté sélectionné : Tutoriel sur l’activation
* **[!UICONTROL Resource Name&amp;ast;]** : Leçon de ski 1
* **[!UICONTROL Balises]** : Tutoriel : Sports / Ski
* **[!UICONTROL Afficher dans le catalogue]** : Activé
* **[!UICONTROL Description]** : Glisser sur la neige pour les débutants
* **[!UICONTROL Ajouter une image]** : Ajoutez une image pour représenter la ressource au membre dans la vue Affectations.
   ![chlimage_1-202](assets/chlimage_1-202.png)
* Sélectionnez **[!UICONTROL Suivant]**

### Ajouter du contenu {#add-content}

Bien qu’il s’affiche comme si plusieurs ressources pouvaient être sélectionnées, une seule est autorisée.

Sélectionnez `'+' icon`, dans le coin supérieur droit, pour lancer le processus de choix de la ressource en identifiant la source.

![chlimage_1-203](assets/chlimage_1-203.png) ![chlimage_1-204](assets/chlimage_1-204.png)

Téléchargez une ressource. Si une ressource vidéo, téléchargez une image personnalisée à afficher avant le début de la lecture de la vidéo ou autorisez la génération d’une miniature à partir de la vidéo (cela peut prendre quelques minutes, il n’est pas nécessaire d’attendre).

![chlimage_1-205](assets/chlimage_1-205.png)

* sélectionnez **[!UICONTROL Suivant]**

### Paramètres {#settings}

* ****
Paramètres de Social : laissez les paramètres par défaut pour expérimenter l’observation et l’évaluation des ressources d’activation par les apprenants.
* **[!UICONTROL Échéance]**

   *(Facultatif)* Une date à laquelle l’affectation doit être terminée peut être sélectionnée.
* **[!UICONTROL Auteur de la ressource]**

   *(Facultatif)* Laissez vide.
* **[!UICONTROL Resource Contact&amp;ast;]**

   *(Obligatoire)* Utilisez le menu déroulant pour sélectionner un membre  `Quinn Harper`.
* **[!UICONTROL Expert de la ressource]**

   *(Facultatif)* Laissez vide.
   **Remarque** : si les utilisateurs ou les groupes ne sont pas visibles, vérifiez qu’ils ont été ajoutés au  `Community Enable Members` groupe et  ** enregistrés sur l’instance de publication.
   ![chlimage_1-206](assets/chlimage_1-206.png)
* Sélectionnez **[!UICONTROL Suivant]**

### Affectations {#assignments}

* **[!UICONTROL Ajoutez]**
AssigneeLeave non défini, car cette ressource d’activation sera ajoutée à un parcours d’apprentissage. Si un apprenant est affecté à la ressource d’activation individuelle ainsi qu’à un fichier learningPath contenant la ressource d’activation, il sera affecté deux fois à la ressource d’activation.

![chlimage_1-207](assets/chlimage_1-207.png)

* Sélectionnez **[!UICONTROL Créer]**

![chlimage_1-208](assets/chlimage_1-208.png)

La création réussie de la ressource renvoie à la console Ressources avec la ressource nouvellement créée sélectionnée. Dans cette console, vous pouvez publier, ajouter des apprenants et modifier d’autres paramètres.

Pour charger une nouvelle version de la ressource d’activation, il est recommandé de créer une nouvelle ressource, puis de désinscrire les membres de l’ancienne version et de les inscrire à la nouvelle version.

### Publier la ressource {#publish-the-resource}

Avant que les inscrits puissent voir la ressource affectée, elle doit être publiée :

* Icône Sélectionner le monde `Publish`

L’activation est confirmée par un message de succès :

![chlimage_1-209](assets/chlimage_1-209.png)

## Ajout d’une ressource de deuxième activation {#add-a-second-enablement-resource}

Répétez les étapes ci-dessus pour créer et publier une seconde ressource d’activation associée à partir de laquelle un parcours d’apprentissage sera créé.

![chlimage_1-210](assets/chlimage_1-210.png)

**** Publiez la deuxième ressource.

Revenez à la liste des ressources du tutoriel d’activation.

*Conseil : si les deux ressources ne sont pas visibles, actualisez la page.*

![chlimage_1-211](assets/chlimage_1-211.png)

## Ajouter un chemin d’apprentissage {#add-a-learning-path}

Un parcours d’apprentissage est un regroupement logique de ressources d’activation qui forment un cours.

* Dans la console Ressources, sélectionnez `+ Create`
* Sélectionnez **[!UICONTROL Chemin d’apprentissage]**

![chlimage_1-212](assets/chlimage_1-212.png)

Ajoutez les **[!UICONTROL Informations de base]** :

* **[!UICONTROL Nom du chemin d’apprentissage]** : Leçons de ski
* **[!UICONTROL Balises]** : Tutoriel : Ski
* **[!UICONTROL Afficher dans le catalogue]** : ne pas cocher
* **[!UICONTROL Chargement d’une]** image pour représenter le chemin d’apprentissage dans la console Ressources

![chlimage_1-213](assets/chlimage_1-213.png)

* Sélectionnez **[!UICONTROL Suivant]**

Ignorez le panneau suivant, car il n’existe aucun parcours d’apprentissage prérequis à ajouter.

* Sélectionnez **[!UICONTROL Suivant]**

Dans le panneau Ajouter des ressources

* Sélectionnez `+ Add Resources` pour sélectionner les 2 ressources de ski lessions à ajouter au chemin d’apprentissage.

   Remarque : Seules les ressources **publiées** peuvent être sélectionnées.

>[!NOTE]
>
>Vous ne pouvez sélectionner que les ressources disponibles au même niveau que le chemin d’apprentissage. Par exemple, pour un parcours d’apprentissage créé dans un groupe, seules les ressources au niveau du groupe sont disponibles ; pour un parcours d’apprentissage créé dans un site communautaire, les ressources de ce site peuvent être ajoutées au chemin d’apprentissage.

* Sélectionnez **[!UICONTROL Envoyer]**.

![chlimage_1-214](assets/chlimage_1-214.png) ![chlimage_1-215](assets/chlimage_1-215.png)

* Sélectionnez **[!UICONTROL Suivant]**

![chlimage_1-216](assets/chlimage_1-216.png)

* **[!UICONTROL Ajouter des]**
personnes à affecterUtilisez le menu déroulant pour sélectionner la variable 
`Community Ski Class` , qui doit inclure des membres  `Riley Taylor` et  `Sidney Croft.`

* **[!UICONTROL Formation Path Contact&amp;ast;]**

   *(Obligatoire)* Utilisez le menu déroulant pour sélectionner un membre  `Quinn Harper`.

* Sélectionnez **[!UICONTROL Créer]**

![chlimage_1-217](assets/chlimage_1-217.png)

La création réussie du chemin d’apprentissage revient à la console Ressources avec le nouveau chemin d’apprentissage sélectionné. Dans cette console, vous pouvez publier, ajouter des apprenants et modifier d’autres paramètres.

**** Publiez le chemin d’apprentissage.
