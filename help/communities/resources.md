---
title: 'Console Ressources d’activation '
seo-title: Enablement Resources Console
description: Dans la console Ressources, les responsables de l’activation créent, gèrent et assignent des ressources aux membres d’un site de la communauté d’activation.
seo-description: The Resources console is where Enablement Managers create, manage, and assign resources to members of an enablement community site
uuid: 52445b39-c339-4b39-8004-eb36de99bced
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 1ef15e76-fe7c-4ced-a20d-c0a9385e3ee4
role: Admin
exl-id: 67d80ec9-64c9-43a5-8cb1-9da819471797
source-git-commit: 3c050c33a384d586d74bd641f7622989dc1d6b22
workflow-type: tm+mt
source-wordcount: '2957'
ht-degree: 6%

---

# Console Ressources d’activation  {#enablement-resources-console}

Pour AEM Communities, la console Ressources est l’emplacement où [Chefs d’activation](users.md) créer, gérer et affecter des ressources aux membres d’un site de communauté d’activation.

## Conditions requises {#requirements}

Avant d’ajouter des ressources d’activation pour un site de communauté, les instances AEM doivent être correctement configurées, notamment :

* SCORM
* FFmpeg

Pour plus d’informations, voir [Configuration de l’activation](enablement.md).

>[!CAUTION]
>
>Si SCORM est installé après la création d’un site de communauté, toutes les ressources d’activation présentes avant l’installation de SCORM doivent être recréées.

>[!NOTE]
>
>Avec la publication de [AEM 6.3](deploy-communities.md#latestfeaturepack) et les Feature Packs Communities équivalents [AEM 6.2 FP3](deploy-communities.md#latestfeaturepack) et [AEM 6.1 FP7](https://docs.adobe.com/content/docs/en/aem/6-1/deploy/communities.html#Latest Feature Pack), la fonction d’activation ne nécessite plus de balise [Base de données MySQL](mysql.md).

## Terminologie {#terminology}

### Ressource {#resource}

Les ressources sont essentielles à une [communauté d&#39;activation](overview.md#enablement-community). Ce sont les matériaux qui permettent aux membres d&#39;améliorer leurs compétences.

Caractéristiques d’une ressource :

* Peut être de type
   * Image (JPG, PNG, GIF, BMP)
   * Vidéo (MP4)
   * Flash (SWF)
   * Document (PDF)
   * Quiz (SCORM)
* Peut être référencé à partir d’un ou de plusieurs parcours d’apprentissage

### Cursus de formation {#learning-path}

Un parcours d’apprentissage est un ensemble logique de ressources d’activation regroupées pour faciliter l’affectation des membres.

### Groupe de membres {#members-group}

Lors de la création d’un site communautaire, le nom donné au site pour l’URL est utilisé pour la création de la variable [groupes d’utilisateurs spécifiques au site](users.md) configurés avec différentes autorisations pour différents rôles. Tous ces groupes créés automatiquement sont précédés du préfixe `Community *<site-name>*`.

Un de ces groupes d’utilisateurs est : `Community *<site-name>* Members` , qui identifie les utilisateurs enregistrés dans l’environnement de publication en tant que membres de la communauté. Voir le tutoriel [Prise en main d’AEM Communities pour l’activation](getting-started-enablement.md) par exemple.

Pour [communautés d&#39;engagement](overview.md#egagementcommunity), il est raisonnable de permettre aux visiteurs du site de s’enregistrer ou d’utiliser la connexion sociale, à ce stade ils sont automatiquement ajoutés au groupe de membres.

Pour [communautés d’activation](overview.md#enablement-community), il est recommandé de rendre le site privé, ce qui nécessite ensuite qu’un administrateur ajoute des utilisateurs au groupe de membres.

## Accès aux ressources d’activation d’un site de la communauté {#accessing-a-community-site-s-enablement-resources}

### Accédez aux ressources de Communities {#navigate-to-communities-resources}

Dans l’environnement de création, pour accéder à la console Ressources

* À partir de la navigation globale : **[!UICONTROL Navigation > Communautés > Ressources]**

![chlimage_1-163](assets/chlimage_1-163.png)

### Sélection d’un site communautaire {#select-a-community-site}

La console Ressources des communautés affiche tous les sites de la communauté.

Les ressources d’activation sont créées pour un site de communauté spécifique après avoir sélectionné le site dans la console Ressources.

Une fois qu’un site de communauté spécifique est sélectionné, toutes les ressources d’activation et tous les parcours d’apprentissage existants sont accessibles pour la gestion et la modification, et de nouvelles ressources d’activation et de nouveaux chemins d’apprentissage peuvent être créés.

![chlimage_1-164](assets/chlimage_1-164.png)

#### Rechercher {#search-features}

![chlimage_1-165](assets/chlimage_1-165.png)

Sélectionnez l’icône de basculement du panneau latéral afin de rechercher une ressource d’activation ou un chemin d’apprentissage. Lorsque cette option est sélectionnée, un panneau de recherche s’ouvre dans la partie gauche de la console et fournit une zone de texte dans laquelle les termes de recherche peuvent être saisis.

![chlimage_1-166](assets/chlimage_1-166.png)

#### Mode de sélection {#selection-mode}

Pour sélectionner plusieurs ressources d’activation, sélectionnez-les en premier en pointant la souris sur la carte et en sélectionnant l’icône en forme de coche. Une fois la sélection effectuée, toute autre carte est ajoutée au groupe de sélection. Si vous sélectionnez une deuxième fois, la carte est désélectionnée.

![chlimage_1-167](assets/chlimage_1-167.png)

## Création d’une ressource {#create-a-resource}

![chlimage_1-168](assets/chlimage_1-168.png)

Pour ajouter une nouvelle ressource d’activation au site de la communauté

* Sélectionnez la `Create` icon
* Dans le sous-menu qui s’affiche, sélectionnez `Resource`

Cela lance un processus détaillé de

* Description de la ressource (nom, image de carte et texte)
* Sélectionner le contenu de la ressource
* Sélection d’une image de couverture pour la ressource
* Identifier les contacts de la ressource
* Affectation de ressources aux membres

Lorsque la ressource fait partie d’un cours, un parcours d’apprentissage, les membres ne doivent être affectés qu’au chemin d’apprentissage. Des affectations peuvent être ajoutées une fois la ressource d’activation créée.

### 1 Informations de base {#basic-info}

![chlimage_1-169](assets/chlimage_1-169.png)

* **[!UICONTROL Ajouter image]**

   (*facultatif*) Image à afficher sur la carte de la ressource d’activation dans la page d’affectation du membre, ainsi que dans la console Ressources. L’image est sélectionnée à partir du système de fichiers local du serveur. Si aucune image n’est fournie, une miniature est générée pour la ressource chargée.

   ***Remarque***: la taille d’image recommandée n’est pas simplement de 480 x 480 pixels. En raison de la conception réactive des cartes pour diverses dimensions de navigateur, la taille d’affichage varie de 220 x 165 pixels à 400 x 165 pixels.

* **[!UICONTROL Nom du site]**

   (*readonly*) Site de la communauté auquel la ressource est ajoutée.

* **[!UICONTROL Resource Name&amp;ast;]**

   (*required*) Nom d’affichage de la ressource. Un nom de noeud valide est créé à partir du nom d’affichage.

* **[!UICONTROL Balises]**

   (*facultatif*) Une ou plusieurs balises peuvent être sélectionnées pour associer la ressource d’activation à un ou plusieurs catalogues. Voir [Balisage des ressources d’activation](tag-resources.md).

* **[!UICONTROL Afficher dans le catalogue]**

   Lorsque cette option est désactivée, la ressource d’activation n’apparaît dans aucun catalogue. Si cette case est cochée, la ressource d’activation s’affiche dans tous les catalogues, sauf si [pré-filtré](catalog-developer-essentials.md#pre-filters) ou les filtres membres de l’interface utilisateur. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Description]**

   (*facultatif*) Description à afficher pour la ressource d’activation.

* **[!UICONTROL Petite ressource]**

   (*facultatif*) Sélectionné à partir d’AEM Assets. Image miniature représentant la ressource dans l’environnement de publication, par exemple dans un catalogue.

* **[!UICONTROL Grande ressource]**

   (*facultatif*) Sélectionné à partir d’AEM Assets. Image de grande taille représentant la ressource dans l’environnement de publication, par exemple sur la page principale d’une ressource.

* **[!UICONTROL Ressource de fragment de contenu]**

   (*facultatif*) Sélectionné à partir d’AEM Assets. Un fragment de contenu qui peut être référencé dans l’environnement de publication, mais qui n’est pas utilisé par défaut.

* Sélectionnez **[!UICONTROL Suivant]**

### 2 Ajouter du contenu {#add-content}

![chlimage_1-170](assets/chlimage_1-170.png)

Bien qu’il s’affiche comme si plusieurs ressources d’activation pouvaient être sélectionnées, une seule est autorisée.

Sélectionnez la `'+' icon`, dans le coin supérieur droit, pour lancer le processus de choix de la ressource en identifiant la source.

![chlimage_1-171](assets/chlimage_1-171.png)

* **[!UICONTROL Télécharger à partir de mes fichiers locaux]**
Le téléchargement depuis le système de fichiers local utilise l’explorateur de fichiers natif pour sélectionner et charger un fichier. Les types de fichiers pris en charge sont SCORM.zip (HTML5 ou SWF), MP4, vidéo, SWF, PDF et types d’images (JPG, PNG, GIF, BMP). Le nom de fichier devient le nom de la ressource, qui est ajouté à la bibliothèque de ressources.

* **[!UICONTROL Parcourir la bibliothèque de ressources]**
Sélectionnez dans la bibliothèque de ressources. La sélection est limitée à celles qui sont visibles dans le site de la communauté.

* **[!UICONTROL Ajouter une URL externe]**

   Saisissez un lien vers le contenu d’apprentissage.

   Dans la boîte de dialogue qui s’ouvre, saisissez :

   * **[!UICONTROL Titre]**

      Nom de la ressource pour la ressource d’activation.

   * **[!UICONTROL URL]**

      URL d’une ressource.

* **[!UICONTROL Ajouter une URL Adobe Connect]**

   Saisissez un lien vers une session Adobe Connect.

   Dans la boîte de dialogue qui s’ouvre, saisissez :

   * **[!UICONTROL Titre]**

      Nom de la ressource pour la ressource d’activation.

   * **[!UICONTROL URL]**

      URL d’une session Adobe Connect.

* **[!UICONTROL Définir une ressource externe]**

   Indiquez l&#39;emplacement où le matériau doit être présenté. Les valeurs de l’état et du score de succès sont saisies manuellement (voir [Rapports](reports.md)). Une image de couverture téléchargée peut être utilisée pour fournir des informations supplémentaires.

   Dans la boîte de dialogue qui s’ouvre, saisissez :

   * **[!UICONTROL Titre]**

      Nom de la ressource pour la ressource d’activation.

   * **[!UICONTROL Emplacement]**

      Emplacement d’un site physique, tel qu’une salle de classe.

#### Exemple de ressource vidéo ajoutée {#example-of-an-added-video-resource}

![chlimage_1-172](assets/chlimage_1-172.png)

* **[!UICONTROL Image de couverture des ressources]**

   L’image de couverture est une image à afficher lors de la première consultation de la ressource d’activation. Par exemple, l’image de couverture s’affiche lorsqu’une ressource vidéo n’est pas encore en cours de lecture. Si une image personnalisée n’est pas téléchargée, une image par défaut s’affiche. Pour les ressources vidéo, il peut être possible de [générer une miniature ;](enablement.md#ffmpeg), mais uniquement lors du chargement et non lorsque la vidéo est référencée en tant qu’URL. Pour les ressources d’emplacement, l’image peut être utilisée pour fournir des informations supplémentaires.

   La taille recommandée pour l’image de couverture est de 640 x 360 pixels.

* Sélectionnez **[!UICONTROL Suivant]**

### Paramètres 3 {#settings}

![chlimage_1-173](assets/chlimage_1-173.png)

>[!NOTE]
>
>Les apprenants ne doivent pas être inscrits directement dans les ressources d’activation qui doivent être référencées à partir d’un parcours d’apprentissage. Les apprenants doivent uniquement être inscrits dans le parcours d’apprentissage.
>
>Si un membre est inscrit à la fois dans une ressource et dans un chemin d’apprentissage qui référence cette ressource, ses affectations affichent la ressource unique et la ressource dans le chemin d’apprentissage.

* **[!UICONTROL Paramètres des réseaux sociaux]**

   Ces paramètres déterminent si les apprenants peuvent ou non fournir des informations concernant la ressource d’activation. Le [paramètres de modération](sites-console.md#moderation) sont ceux du site de la communauté parent.

   * **[!UICONTROL Autoriser les commentaires]**

      Si cette case est cochée, les membres sont autorisés à commenter la ressource. Cette option est cochée par défaut.

   * **[!UICONTROL Autoriser les évaluations]**

      Si cette case est cochée, les membres sont autorisés à évaluer la ressource. Cette option est cochée par défaut.

   * **[!UICONTROL Autoriser l&#39;accès anonyme]**

      Si cette case est cochée, les visiteurs anonymes du site sont autorisés à afficher la ressource dans un catalogue lorsque le site de la communauté autorise également l’accès anonyme. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Échéance]**

   *(Facultatif)* Une date à laquelle l’affectation doit être terminée peut être sélectionnée.

* **[!UICONTROL Auteur de la ressource]**
   *(Facultatif)* L’auteur de la ressource d’activation. Utilisez le menu déroulant pour effectuer une sélection parmi les utilisateurs qui sont membres du groupe [groupe de membres](#members-group).

* **[!UICONTROL Resource Contact&amp;ast;]**
   *(Obligatoire)* Personne que le membre peut contacter concernant la ressource d’activation. Utilisez le menu déroulant pour effectuer une sélection parmi les utilisateurs qui sont membres du groupe [groupe de membres](#members-group).

* **[!UICONTROL Expert de la ressource]**
   *(Facultatif)* Personne que le membre peut contacter et qui possède une expertise concernant la ressource d’activation. Utilisez le menu déroulant pour effectuer une sélection parmi les utilisateurs qui sont membres de la fonction [groupe de membres](#members-group).

### 4 affectations {#assignments}

![chlimage_1-174](assets/chlimage_1-174.png)

* **[!UICONTROL Ajouter des entités]**
Utilisez le menu déroulant pour effectuer une sélection dans [members](#members-group) - les utilisateurs et les groupes d’utilisateurs (répertoriés en gras) - qui doivent être inscrits en tant qu’apprenants. Lorsque les membres se connectent au site de la communauté, les ressources d’activation (et les parcours d’apprentissage) dans lesquels ils sont inscrits apparaissent sur leur [Affectations](functions.md#assignments-function) page.

* Sélectionnez **[!UICONTROL Créer]**.

![chlimage_1-175](assets/chlimage_1-175.png)

La création réussie de la ressource d’activation renvoie à la console Ressources avec la ressource nouvellement créée sélectionnée. Depuis cette console, il est possible de [gérer la ressource](#managing-a-resource).

## Création d’un parcours d’apprentissage {#create-a-learning-path}

![chlimage_1-176](assets/chlimage_1-176.png)

Ajout d’un nouveau chemin d’apprentissage au site de la communauté

* Sélectionnez la `Create` icon
* Dans le sous-menu qui s’affiche, sélectionnez `Learning Path`

Cela lance un processus détaillé de

* Identification du parcours d’apprentissage
* Fournir une image de carte représentant le chemin d’apprentissage pour les apprenants
* Référencer les ressources d’activation à inclure dans le chemin d’apprentissage
* Classer éventuellement les ressources
* Identification facultative des parcours d’apprentissage prérequis
* Identification d&#39;un contact de parcours d&#39;apprentissage
* Inscription de membres

Pour les ressources d’activation incluses dans un parcours d’apprentissage, les affectations ne doivent être effectuées que pour le chemin d’apprentissage et non pour les ressources individuelles.

### Informations de base {#basic-info-1}

![chlimage_1-177](assets/chlimage_1-177.png)

* **[!UICONTROL Ajouter image]**

   (*facultatif*) Image à afficher sur la carte du chemin d’apprentissage dans la page des affectations du membre, ainsi que dans la console Ressources. L’image est sélectionnée à partir du système de fichiers local du serveur. Si aucune image n’est fournie, une miniature est générée pour la ressource chargée.

   ***Remarque***: la taille d’image recommandée n’est plus simplement de 480 x 480 pixels. En raison de la conception réactive des cartes pour diverses dimensions de navigateur, la taille d’affichage varie de 220 x 165 pixels à 400 x 165 pixels.

* **[!UICONTROL Nom du site]**

   (*readonly*) Site de la communauté auquel la ressource est ajoutée.

* **[!UICONTROL Nom du cursus de formation]**

   (*required*) Nom d’affichage du chemin d’apprentissage. Un nom de noeud valide est créé à partir du nom d’affichage.

* **[!UICONTROL Balises]**

   (*facultatif*) Vous pouvez choisir une ou plusieurs balises qui associent le chemin d’apprentissage à un ou plusieurs catalogues. Voir [Balisage des ressources d’activation](tag-resources.md).

* **[!UICONTROL Afficher dans le catalogue]**

   Lorsque cette option est désactivée, le chemin d’apprentissage n’apparaît dans aucun catalogue. Si cette case est cochée, le chemin d’apprentissage s’affiche dans tous les catalogues, sauf si [pré-filtré](catalog-developer-essentials.md#pre-filters) ou les filtres membres de l’interface utilisateur. L’affichage du parcours d’apprentissage dans un catalogue permet indirectement d’accéder en LECTURE à toutes ses ressources contenues. Cette option n’est pas cochée par défaut.

* **[!UICONTROL Description]**

   (*facultatif*) Description à afficher pour la ressource d’activation.

* **[!UICONTROL Petite ressource]**

   (*facultatif*) Sélectionné à partir d’AEM Assets. Image miniature représentant la ressource dans l’environnement de publication, par exemple dans un catalogue.

* **[!UICONTROL Grande ressource]**

   (*facultatif*) Sélectionné à partir d’AEM Assets. Image de grande taille représentant la ressource dans l’environnement de publication, par exemple sur la page principale d’une ressource.

* **[!UICONTROL Ressource de fragment de contenu]**

   (*facultatif*) Sélectionné à partir d’AEM Assets. Un fragment de contenu qui peut être référencé dans l’environnement de publication, mais qui n’est pas utilisé par défaut.

* Sélectionnez **[!UICONTROL Suivant]**

### Ajouter des conditions préalables {#add-prerequisites}

![chlimage_1-178](assets/chlimage_1-178.png)

* **[!UICONTROL Cursus de formation prérequis]**
(
*facultatif*) Lorsque d’autres chemins d’apprentissage publiés sont sélectionnés, ils doivent être remplis avant qu’un apprenant ne puisse sélectionner ce chemin d’apprentissage.

* Sélectionnez **[!UICONTROL Suivant]**

### Ajouter des ressources {#add-resources}

![chlimage_1-179](assets/chlimage_1-179.png)

* **[!UICONTROL Mettre en place l’ordre du cursus de formation]**

   (*facultatif*) s’il est défini sur Activé, l’ordre dans lequel les ressources d’activation sont ajoutées est l’ordre dans lequel les apprenants sont requis pour poursuivre le parcours d’apprentissage. La valeur par défaut est Off.

* **[!UICONTROL Ressources]**

   Une ou plusieurs ressources sélectionnées parmi les ressources d’activation *publiées* créées pour le site de la communauté en cours.

>[!NOTE]
>
>Vous ne pouvez sélectionner que les ressources disponibles au même niveau que le chemin d’apprentissage. Par exemple, pour un parcours d’apprentissage créé dans un groupe, seules les ressources au niveau du groupe sont disponibles ; pour un parcours d’apprentissage créé dans un site communautaire, les ressources de ce site peuvent être ajoutées au chemin d’apprentissage.

* Sélectionnez **[!UICONTROL Suivant]**.

### Paramètres {#settings-1}

![chlimage_1-180](assets/chlimage_1-180.png)

* **[!UICONTROL Ajouter des inscriptions]**

   Utilisez le menu déroulant pour sélectionner parmi les membres et les groupes de membres (répertoriés en gras) qui sont membres du site de la communauté. [groupe de membres](#members-group). Il n’est pas nécessaire d’ajouter des affectations lors de la première création du chemin d’apprentissage. Les propriétés du chemin d’apprentissage peuvent être modifiées pour ajouter des apprenants ultérieurement.

* **[!UICONTROL Formation Path Contact&amp;ast;]**

   *(Obligatoire)* Personne que le membre peut contacter concernant le parcours d’apprentissage. Utilisez le menu déroulant pour effectuer une sélection parmi les utilisateurs membres du site de la communauté. [groupe de membres](#members-group).

* Sélectionnez **[!UICONTROL Créer]**

>[!NOTE]
>
>Les ressources d’activation référencées à partir du chemin d’apprentissage ne doivent pas répertorier les mêmes personnes concernées (apprenants), le cas échéant.
>
>Si un membre est inscrit à la fois dans une ressource d’activation et un chemin d’apprentissage qui référence cette ressource, ses affectations affichent la ressource unique et la ressource dans le chemin d’apprentissage.

## Gestion d’une ressource {#managing-a-resource}

Pour gérer une seule ressource d’activation

* Dans la console Ressources
* Sélectionnez le site de la communauté qui contient la ressource.
* Sélectionner la ressource

Pour la ressource d&#39;activation sélectionnée, il est possible de :

* Afficher les propriétés (par défaut)
* Modification des propriétés
* Supprimer
* Publication
* Annuler la publication

Pour charger une nouvelle version de la ressource d’activation, il est recommandé de créer une nouvelle ressource, puis de désinscrire les membres de l’ancienne version et de les inscrire à la nouvelle version.

### Modifier la ressource {#edit-resource}

![chlimage_1-181](assets/chlimage_1-181.png)

En sélectionnant l&#39;icône en forme de crayon, les étapes de création d&#39;une ressource d&#39;activation sont rendues disponibles afin que toutes les informations fournies puissent être modifiées.

Si la seule modification consiste à modifier les affectations à l’étape Paramètres, l’enregistrement des modifications entraîne la publication des modifications. Si d’autres modifications sont apportées, la ressource doit être explicitement publiée après l’enregistrement.

### Supprimer la ressource {#delete-resource}

![chlimage_1-182](assets/chlimage_1-182.png)

En sélectionnant l’icône de la corbeille, la ressource d’activation sera `Delete`d après confirmation.

### Publication {#publish}

![chlimage_1-183](assets/chlimage_1-183.png)

Avant que les apprenants puissent voir une ressource d’activation affectée, elle doit être publiée :

* Sélectionnez l’icône représentant un monde pour `Publish`
* Dans la boîte de dialogue qui s’affiche, sélectionnez **[!UICONTROL Publier]** again
* Sélectionner **[!UICONTROL Fermer]**

Même si la boîte de dialogue indique que l’action est mise en file d’attente, elle est souvent publiée immédiatement.

### Annuler la publication {#unpublish}

![chlimage_1-184](assets/chlimage_1-184.png)

Pour rendre temporairement les ressources d’activation inaccessibles aux membres de l’environnement de publication sans les supprimer, utilisez l’icône du monde pour `Unpublish`la ressource.

### Rapport {#report}

![chlimage_1-185](assets/chlimage_1-185.png)

L’icône Rapport permet d’accéder aux rapports générés lorsque les apprenants interagissent avec les ressources d’activation qui leur sont affectées dans l’environnement de publication. Le rapport varie en fonction du type de ressource.

Pour tous les parcours d’apprentissage, il est possible d’afficher un rapport en fonction des ressources ou des apprenants ( `User Report`).

![chlimage_1-186](assets/chlimage_1-186.png)

Ce rapport est spécifique à la ressource d’activation actuelle ou au parcours de formation. La profondeur de création de rapports dépend de si [Adobe Analytics](analytics.md) est sous licence et activé pour le site de la communauté. Le [Chronologie](#timeline), [Engagement des visionneuses](#viewer-engagement), et [Engagement par appareil](#engagement-by-device) Les rapports sont importés à partir d’Adobe Analytics en fonction de la variable [intervalle d’interrogation](analytics.md#report-importer).

Pour toutes les ressources d’activation, qu’Adobe Analytics soit activé ou non, il existe des rapports sur [État du cessionnaire](#assignee-status) et [Évaluations](#ratings) ainsi que d’une [Résumé du rapport](#report-summary) table.

![chlimage_1-187](assets/chlimage_1-187.png)

#### Chronologie {#timeline}

Le rapport Chronologie Analytics indique le moment où des événements se produisent au fil du temps pour cette ressource d’activation :

* **Vues**

   Une vue est lorsqu’un apprenant visite la page des détails de la ressource.

* **Lectures**

   Une lecture se produit lorsque alLearning interagit avec la ressource, par exemple en lisant une vidéo ou en ouvrant un PDF.

* **Evaluations**

   Une évaluation est lorsqu’un apprenant affecte une évaluation par étoiles à une ressource.

* **Commentaires**

   Un commentaire est lorsqu’alLearning ajoute un commentaire

L’axe vertical correspond au nombre d’événements.

L’axe horizontal est l’heure du calendrier.

[Adobe Analytics requis](sites-console.md#analytics).

#### Engagement de la visionneuse {#viewer-engagement}

Le rapport Engagement des visionneuses Analytics indique, pour les ressources vidéo, le nombre d’apprenants qui ont consulté la ressource et, s’ils n’ont pas lu la ressource jusqu’à la fin, à quel moment les apprenants ont cessé de la lire.

L’axe vertical correspond au nombre d’apprenants qui ont consulté cette ressource.

L&#39;axe horizontal correspond à la durée de cette ressource.

[ID d’entreprise Marketing Cloud requis](sites-console.md#enablement).

#### Engagement par périphérique {#engagement-by-device}

Le rapport Engagement Analytics par appareil, pour les ressources vidéo, décrit le pourcentage d’affichages lus à partir du bureau et depuis le mobile.

[ID d’entreprise Marketing Cloud requis](sites-console.md#enablement).

#### État des cessionnaires {#assignee-status}

Le rapport État du cessionnaire, basé sur le nombre d’apprenants, décrit le nombre d’utilisateurs ayant

* **Non démarré**
* **En cours**
* **Terminé**

#### Evaluations {#ratings}

Le rapport Évaluations est basé sur le nombre d’apprenants qui ont évalué la ressource d’activation, indiquant le nombre de chaque évaluation par étoiles suivie d’un résumé du nombre total d’évaluations et de la note moyenne.

#### Résumé du rapport {#report-summary}

Pour une ressource d’activation, le résumé du rapport est une liste de tableaux.

* Chaque apprenant qui a interagi avec la ressource
   * Leur statut
   * Si la ressource leur a été affectée
      * Contrairement à leur recherche de la ressource dans un catalogue
   * Nombre de commentaires publiés
   * La note donnée, le cas échéant

Pour un rapport Ressource de chemin d’apprentissage, le résumé du rapport est une liste de tableaux.

* Chaque ressource incluse dans le chemin d’apprentissage
   * État de publication
   * Nombre de vues
   * Nombre de lectures
   * Note moyenne
   * Format
   * Taille
   * Nom du site de la communauté

Pour un rapport d’utilisateur de parcours de formation, le résumé du rapport est une liste de tableaux.

* Chaque apprenant affecté au parcours d’apprentissage
   * Nombre de ressources terminées
   * Leur statut

Il est possible d&#39;ajuster l&#39;affichage du tableau en sélectionnant les colonnes à l&#39;aide de la fonction `Show / hide columns` sélecteur.

#### Télécharger le rapport au format CSV {#download-report-as-csv}

Le tableau Résumé des rapports peut être téléchargé au format CSV à l’aide d’un bouton situé en haut de la console.

* pour une ressource d’activation : `Download Resource Report as CSV` button
* pour un parcours d’apprentissage : `Download Learning Path Report as CSV` button

L’intégralité du résumé des rapports est téléchargée, quelles que soient les colonnes sélectionnées pour l’affichage.
