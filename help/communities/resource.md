---
title: Créer et affecter des ressources d'activation
seo-title: Créer et affecter des ressources d'activation
description: Ressources d'activation des Ajoutes
seo-description: Ressources d'activation des Ajoutes
uuid: da940242-0c9b-4ad8-8880-61fd41461c3b
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: introduction
content-type: reference
discoiquuid: 8fe97181-600e-42ac-af25-d5d4db248740
translation-type: tm+mt
source-git-commit: 28948f1f8678512f8fc970a4289cb01cde86c5c2
workflow-type: tm+mt
source-wordcount: '714'
ht-degree: 6%

---


# Créer et affecter des ressources d&#39;activation {#create-and-assign-enablement-resources}

## Ajouter une ressource d&#39;activation {#add-an-enablement-resource}

Pour ajouter une ressource d’activation au nouveau site de la communauté :

* Sur l’instance d’auteur
   * Par exemple, [http://localhost:4502/](http://localhost:4503/)
* Se connecter en tant qu’administrateur système
* Dans la navigation globale, sélectionnez **Communautés > [Ressources](resources.md)**.

   ![chlimage_1-199](assets/chlimage_1-199.png)
   ![chlimage_1-200](assets/chlimage_1-200.png)
* Sélectionner le site de la communauté sur lequel les ressources d&#39;activation sont ajoutées
   * Sélectionner `Enablement Tutorial`
* Dans le menu, sélectionnez ` Create`
* Sélectionner **[!UICONTROL Ressource]**

![chlimage_1-201](assets/chlimage_1-201.png)

### Informations de base {#basic-info}

Renseignez les informations de base de la ressource :

* **[!UICONTROL Nom]** du site : est défini sur le nom du site de la communauté sélectionnée : Didacticiel d’activation
* **[!UICONTROL Nom de la ressource&amp;ast;]** : Leçon de ski 1
* **[!UICONTROL Balises]** : Didacticiel : Sports / Ski
* **[!UICONTROL Afficher dans le catalogue]** : Activé
* **[!UICONTROL Description]** : Glisser sur la neige pour les débutants
* **[!UICONTROL Ajouter l&#39;image]** : Ajouter une image pour représenter la Ressource au membre dans sa vue Affectations
   ![chlimage_1-202](assets/chlimage_1-202.png)
* Sélectionnez **[!UICONTROL Suivant]**

### Ajouter du contenu {#add-content}

Bien qu&#39;il semble que plusieurs ressources puissent être sélectionnées, une seule est autorisée.

Sélectionnez `'+' icon`, dans le coin supérieur droit, pour commencer le processus de sélection de la ressource en identifiant la source.

![chlimage_1-203](assets/chlimage_1-203.png) ![chlimage_1-204](assets/chlimage_1-204.png)

Téléchargez une ressource. Si une ressource vidéo, téléchargez une image personnalisée à afficher avant la lecture des débuts de la vidéo ou autorisez la génération d’une miniature à partir de la vidéo (cela peut prendre quelques minutes - il n’est pas nécessaire d’attendre).

![chlimage_1-205](assets/chlimage_1-205.png)

* sélectionner **[!UICONTROL Suivant]**

### Paramètres {#settings}

* ****
Paramètres de SocialLaissez les paramètres par défaut pour expérimenter l’observation et l’évaluation des ressources d’activation par les apprenants.
* **[!UICONTROL Échéance]**

   *(Facultatif)* Une date de fin de l&#39;affectation peut être sélectionnée.
* **[!UICONTROL Auteur de la ressource]**

   *(Facultatif)* Laissez ce champ vide.
* **[!UICONTROL Contact&amp;ast de la ressource ;]**

   *(Obligatoire)* Utilisez le menu déroulant pour sélectionner un membre  `Quinn Harper`.
* **[!UICONTROL Expert de la ressource]**

   *(Facultatif)* Laissez ce champ vide.
   **Remarque** : si les utilisateurs ou les groupes ne sont pas visibles, vérifiez qu’ils ont été ajoutés au  `Community Enable Members` groupe et  ** enregistrés sur l’instance de publication.
   ![chlimage_1-206](assets/chlimage_1-206.png)
* Sélectionnez **[!UICONTROL Suivant]**

### Affectations {#assignments}

* **[!UICONTROL Ajouter]**
les personnes affectéesNe pas définir car cette ressource d&#39;activation sera ajoutée à un chemin d&#39;apprentissage. Si un apprenant est affecté à la ressource d&#39;activation individuelle ainsi qu&#39;à un fichier learningPath contenant la ressource d&#39;activation, l&#39;apprenant est affecté à la ressource d&#39;activation deux fois.

![chlimage_1-207](assets/chlimage_1-207.png)

* Sélectionnez **[!UICONTROL Créer]**

![chlimage_1-208](assets/chlimage_1-208.png)

La création réussie de la Ressource retourne à la console Ressources avec la Ressource nouvellement créée sélectionnée. A partir de cette console, il est possible de publier, d’ajouter des apprenants et de modifier d’autres paramètres.

Pour télécharger une nouvelle version de la ressource d&#39;activation, il est recommandé de créer une nouvelle ressource, puis d&#39;annuler l&#39;inscription des membres de l&#39;ancienne version et de les inscrire dans la nouvelle version.

### Publier la ressource {#publish-the-resource}

Pour que les inscrits puissent voir les ressources affectées, elles doivent être publiées :

* Sélectionner l&#39;icône `Publish`monde

L’Activation est confirmée par un message de réussite :

![chlimage_1-209](assets/chlimage_1-209.png)

## Ajouter une deuxième ressource d&#39;activation {#add-a-second-enablement-resource}

Répétez les étapes ci-dessus pour créer et publier une seconde ressource d’activation associée à partir de laquelle un chemin d’apprentissage sera créé.

![chlimage_1-210](assets/chlimage_1-210.png)

**** Publier la seconde ressource.

Revenez à la liste des ressources du didacticiel d&#39;activation.

*Conseil : si les deux ressources ne sont pas visibles, actualisez la page.*

![chlimage_1-211](assets/chlimage_1-211.png)

## Ajouter un parcours de formation {#add-a-learning-path}

Un parcours d&#39;apprentissage est un regroupement logique de ressources d&#39;activation qui forment un cours.

* Dans la console Ressources, sélectionnez `+ Create`
* Sélectionner **[!UICONTROL Chemin d&#39;apprentissage]**

![chlimage_1-212](assets/chlimage_1-212.png)

Ajoutez **[!UICONTROL Informations de base]** :

* **[!UICONTROL Nom]** du chemin d&#39;apprentissage : Leçons de ski
* **[!UICONTROL Balises]** : Didacticiel : Ski
* **[!UICONTROL Afficher dans le catalogue]** : laisser sans contrôle
* **[!UICONTROL Téléchargez une]** image représentant le chemin d’apprentissage dans la console Ressources.

![chlimage_1-213](assets/chlimage_1-213.png)

* Sélectionnez **[!UICONTROL Suivant]**

Ignorez le panneau suivant, car il n’existe aucun chemin d’apprentissage prérequis à ajouter.

* Sélectionnez **[!UICONTROL Suivant]**

Dans le panneau Ajouter les ressources

* Sélectionnez `+ Add Resources` pour sélectionner les 2 ressources de ski lessions à ajouter au parcours d&#39;apprentissage.

   Remarque : Seules les ressources **publiées** seront sélectionnables.

>[!NOTE]
>
>Vous pouvez uniquement sélectionner les ressources disponibles au même niveau que le chemin d’apprentissage. Par exemple, pour un parcours d’apprentissage créé dans un groupe, seules les ressources au niveau du groupe sont disponibles ; pour un parcours d&#39;apprentissage créé dans un site communautaire, les ressources de ce site sont disponibles pour l&#39;ajout au chemin d&#39;apprentissage.

* Sélectionnez **[!UICONTROL Envoyer]**.

![chlimage_1-214](assets/chlimage_1-214.png) ![chlimage_1-215](assets/chlimage_1-215.png)

* Sélectionnez **[!UICONTROL Suivant]**

![chlimage_1-216](assets/chlimage_1-216.png)

* **[!UICONTROL Ajouter les]**
assignationsUtilisez le menu déroulant pour sélectionner 
`Community Ski Class` qui devrait inclure des membres  `Riley Taylor` et  `Sidney Croft.`

* **[!UICONTROL Contact&amp;ast du parcours d&#39;apprentissage ;]**

   *(Obligatoire)* Utilisez le menu déroulant pour sélectionner un membre  `Quinn Harper`.

* Sélectionnez **[!UICONTROL Créer]**

![chlimage_1-217](assets/chlimage_1-217.png)

La création réussie du chemin d’apprentissage revient à la console Ressources avec le nouveau chemin d’apprentissage sélectionné. A partir de cette console, il est possible de publier, d’ajouter des apprenants et de modifier d’autres paramètres.

**** Publiez le chemin d’apprentissage.

