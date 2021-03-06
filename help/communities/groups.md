---
title: Console des groupes communautaires
seo-title: Community Groups Console
description: La console Groupes permet de créer des groupes de communautés.
seo-description: Groups console lets you create Community groups
uuid: 7dac2d1b-78fc-4b39-a2cb-100f1e220c23
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 1293c01a-7308-494a-ab48-bd9938205b81
pagetitle: Community Groups Console
role: Admin
exl-id: f8f19ad6-d6cd-4abd-bc31-6baba3e0356e
source-git-commit: 9178c3a01e7f450d3794f41605fb3788231c88c0
workflow-type: tm+mt
source-wordcount: '1628'
ht-degree: 2%

---

# Console des groupes communautaires {#community-groups-console}

La console Groupes permet d’accéder à la création de groupes de communautés lorsqu’un site de communauté [structure de modèle](sites-console.md#step1) inclut la variable [fonction groups](functions.md#groups-function).

* Les groupes peuvent être imbriqués dans d’autres groupes. Cela se produit lorsque la variable [structure du nouveau groupe](tools-groups.md) contient la fonction groups .
* Pour l’environnement de création uniquement, il existe un assistant de création de groupe similaire à l’assistant de création de site.
* Le fait que les membres puissent créer des groupes à partir de l’environnement de publication ou non est configurable lors de l’ajout d’une fonction Groupes à une structure de site de communauté ou de groupe de communauté.

Des trois modèles de groupe inclus, seul le `Reference Group` inclut une fonction de groupes dans sa structure.

Plusieurs facettes des groupes communautaires sont les suivantes :

* Création : un nouveau groupe peut être créé lors de l’auteur et éventuellement lors de la publication.
* Contrôle : Le groupe peut être ouvert ou secret
* Imbrication : un groupe ne peut contenir aucun ou plusieurs groupes ;

>[!NOTE]
>
>Groupes de communautés, créés dans l’environnement de publication avant l’événement [existence de la console Groupes communautaires](https://helpx.adobe.com/in/experience-manager/6-3/communities/using/version-history.html#FeaturePack1FP1), ne sont pas répertoriés dans la console Groupes de la communauté et ne sont donc pas modifiables à l’aide de la console.

>[!NOTE]
>
>Cette console Groupes, accessible uniquement à partir de la console Sites des communautés , ne doit pas être confondue avec le membre. [Console Groupes](members.md) pour la gestion des groupes de membres.
>
>Les groupes de membres sont des groupes d’utilisateurs enregistrés dans l’environnement de publication et accessibles à partir de l’environnement de création à l’aide de la variable [service tunnel](deploy-communities.md#tunnel-service-on-author).

## Création de groupe {#group-creation}

Pour accéder à la console Groupes , procédez comme suit :

* Sur l’auteur, connectez-vous avec les privilèges d’administrateur
* À partir de la navigation globale : **[!UICONTROL Communautés > Sites]**
* Sélectionner un dossier de site de communauté existant pour l’ouvrir
* Sélection d’une instance d’un site communautaire dans le dossier

   * La structure du site de la communauté doit inclure une fonction de groupe.
   * Ces captures d’écran proviennent du tutoriel Prise en main suivant [création de groupes lors de la publication](published-site.md)

![chlimage_1-133](assets/chlimage_1-133.png)

Sélectionnez la **[!UICONTROL Dossier Groupes]** pour l’ouvrir.

Une fois ouverts, tous les groupes existants, qu’ils soient créés dans l’instance de création ou de publication, s’affichent.

Dans cette console Groupes , il est possible de créer des groupes.

![chlimage_1-134](assets/chlimage_1-134.png)

* Sélectionner **[!UICONTROL Créer un groupe]** button

### Étape 1 : Modèle de groupe de communautés {#step-community-group-template}

![groupe multilingue](assets/multilingualgroup.png)

* **[!UICONTROL Titre du groupe de communautés]**: Titre affiché pour le groupe.

   Le titre apparaît sur le site publié pour le groupe.

* **[!UICONTROL Description du groupe de communautés]**: Description du groupe.
* **[!UICONTROL Racine du groupe de communautés]**: Chemin d’accès racine au groupe.

   La racine par défaut est le site parent, mais elle peut être déplacée à n’importe quel emplacement du site web. Il n’est pas recommandé de le modifier.

* **[!UICONTROL Langues de groupe communautaire disponibles supplémentaires]** menu : Utilisez le menu déroulant pour sélectionner la ou les langues des groupes de communautés disponibles. Le menu affiche toutes les langues dans lesquelles le site de la communauté parent est créé. Les utilisateurs peuvent sélectionner l’une de ces langues pour créer des groupes dans plusieurs paramètres régionaux au cours de cette seule étape. Un même groupe est créé dans plusieurs langues spécifiées dans la console Groupes des sites de communauté respectifs.

* **[!UICONTROL Nom du groupe de communautés]**: Nom de la page racine du groupe qui apparaît dans l’URL.

   * Vérifiez deux fois le nom, car il n’est pas facilement modifié une fois le groupe créé.
   * L’URL de base s’affiche sous le `Community Group Name`
   * Pour une URL valide, ajoutez &quot;.html&quot;

      *Par exemple*, `http://localhost:4502/content/sites/mysight/en/mygroup.html`

* **[!UICONTROL Modèle de groupe de communautés]** menu : utiliser le menu déroulant pour choisir un [modèle de groupe de communautés](tools.md).

### Étape 2 : Conception {#step-design}

#### THÈME DU GROUPE COMMUNAUTAIRE {#community-group-theme}

![community itygrouptheme](assets/communitygrouptheme.png)

La structure utilise `Twitter Bootstrap` pour apporter une conception réactive et flexible au site. Un des nombreux thèmes de Bootstrap préchargés peut être sélectionné pour mettre en forme le modèle de groupe de communautés sélectionné ou un thème de Bootstrap peut être chargé.

Lorsqu’il est sélectionné, le thème est recouvert d’une coche bleue opaque.

Il est possible de sélectionner un thème qui diffère du thème du site parent.

Une fois le site de la communauté publié, il est possible de [modification des propriétés](#modifying-group-properties) et sélectionnez un autre thème.

#### MARQUE DES GROUPES COMMUNAUTAIRES {#community-group-branding}

![chlimage_1-135](assets/chlimage_1-135.png)

La valorisation de marque du site de la communauté est une image affichée en tant qu’en-tête dans la partie supérieure de chaque page. Il est possible d’afficher une bannière pour le groupe qui diffère des autres pages du site.

L’image doit être dimensionnée de manière à être aussi large que l’affichage prévu de la page dans le navigateur et de 120 pixels de hauteur.

Lors de la création ou de la sélection d’une image, gardez à l’esprit les points suivants :

* La hauteur de l’image sera recadrée à 120 pixels mesurés à partir du bord supérieur de l’image.
* L’image est épinglée sur le bord gauche de la fenêtre du navigateur.
* L’image n’est pas redimensionnée, de sorte que lorsque la largeur de l’image est...

   * Moins que la largeur du navigateur, l’image se répète horizontalement.
   * Supérieur à la largeur du navigateur, l’image semble recadrée.

### Étape 3 : Paramètres {#step-settings}

#### MODÉRATION {#moderation}

![chlimage_1-136](assets/chlimage_1-136.png)

Par défaut, la liste des modérateurs du site de la communauté parente est héritée.

Il est possible d’ajouter des modérateurs spécifiques au groupe :

* Recherchez des membres (de l’environnement de publication) à ajouter en tant que modérateurs.

#### ABONNEMENT {#membership}

Le paramètre d’appartenance permet de sélectionner l’une des trois méthodes pour sécuriser un groupe de communautés.

![chlimage_1-137](assets/chlimage_1-137.png)

* Abonnement facultatif

   Si cette option est sélectionnée, le groupe de communautés est un groupe public. Les membres du site peuvent participer au groupe et publier sans rejoindre explicitement le groupe. La valeur par défaut est sélectionnée.
* Abonnement requis

   s’il est sélectionné, le groupe de la communauté est un groupe ouvert. Les membres de la communauté peuvent consulter le contenu du groupe, mais doivent rejoindre le groupe avant de pouvoir publier du contenu. Les membres se joignent en sélectionnant `Join` dans l’environnement de publication. La valeur par défaut n’est pas sélectionnée.

* Abonnement restreint

   s’il est sélectionné, le groupe de la communauté est un groupe secret. Les membres de la communauté doivent être invités explicitement. Les membres invités sont saisis dans la zone de recherche. Les membres peuvent être ajoutés ultérieurement à l’aide de la variable [Consoles Membres et Groupes](members.md) l’environnement de création. La valeur par défaut n’est pas sélectionnée.

#### Miniature {#thumbnail}

![chlimage_1-138](assets/chlimage_1-138.png)

La miniature est une image à afficher pour le groupe lors de l’auteur et de la publication.

La taille optimale d’une image de groupe est de 170 x 90 pixels dans un format d’image pris en charge (JPG ou PNG, par exemple).

Si aucune image n’est ajoutée, une image par défaut s’affiche.

![chlimage_1-139](assets/chlimage_1-139.png)

### Étape 4 : Créer un groupe {#step-create-group}

![chlimage_1-140](assets/chlimage_1-140.png)

Si des ajustements sont nécessaires, utilisez la méthode **Précédent** pour les créer.

Une fois **Créer** est sélectionné et démarré, le processus de création du groupe ne peut pas être interrompu.

Une fois le processus terminé, la carte du nouveau site (groupe) de sous-communautés s’affiche dans la console Groupes de sites de communautés , à partir de laquelle les auteurs peuvent ajouter du contenu de page ou les administrateurs peuvent modifier les propriétés du site.

![createccommunity-group-1](assets/createcommunitygroup-1.png)

>[!NOTE]
>
>Le groupe est créé dans toutes les langues, comme indiqué dans la section [Étape 1 : Modèle de groupe de communautés](groups.md#step1communitygrouptemplate) dans Langues de groupe de communautés disponibles supplémentaires, dans la console Groupes de communautés des sites de communauté respectifs.

## Création de contenu de groupe {#authoring-group-content}

![chlimage_1-141](assets/chlimage_1-141.png)

Le contenu de la page d’un groupe peut être créé avec les mêmes outils que toute autre page AEM. Pour ouvrir le groupe à des fins de création, sélectionnez l’icône Ouvrir le site qui s’affiche lorsque vous pointez sur la carte du groupe.

## Modification des propriétés de groupe {#modifying-group-properties}

Les propriétés d’un site de sous-communauté existant, spécifiées pendant le processus de création du groupe de la communauté, peuvent être modifiées en sélectionnant l’icône Modifier le site qui s’affiche lorsque vous pointez sur la carte du groupe :

![chlimage_1-142](assets/chlimage_1-142.png)

Les détails des propriétés suivantes correspondent aux descriptions fournies dans la section [Création de groupe](#group-creation) . Tout groupe imbriqué peut être modifié, qu’il soit créé dans l’environnement de publication ou dans l’environnement de création.

![chlimage_1-143](assets/chlimage_1-143.png)

### Modification de base {#modify-basic}

Le panneau BASIC permet de modifier les

* Titre de groupe de communautés
* Description du groupe de communautés

Le nom du groupe de la communauté ne peut pas être modifié.

Le choix d’un modèle de groupe de communautés différent n’aurait aucun impact sur un site de groupe de communautés existant, car il n’existe aucune connexion entre les modèles et les sites.

Au lieu de cela, la variable [STRUCTURE](#modify-structure) de la sous-communauté peut être modifiée.

### Modifier la structure {#modify-structure}

Le panneau STRUCTURE permet de modifier la structure initialement créée à partir du modèle de groupe de communautés sélectionné lors de la création du site de sous-communauté à partir de l’environnement de création ou de publication. Dans le panneau , il est possible de

* Glisser-déposer des [fonctions de communauté](functions.md) dans la structure du site ;
* Sur une instance d’une fonction de communauté dans la structure du site :

   * **`gear icon`**

      Modifier les paramètres, y compris le titre d’affichage et le nom de l’URL, ainsi que [groupes de membres privilégiés](users.md#privilegedmembersgroups)

   * **`trashcan icon`**

      Suppression de fonctions de la structure du site

   * **`grid icon`**

      Modifier l’ordre des fonctions tel qu’affiché dans la barre de navigation de niveau supérieur du site

>[!CAUTION]
>
>Bien que le titre d’affichage puisse être modifié sans effets secondaires, il n’est pas recommandé de modifier le nom d’URL d’une fonction de communauté appartenant à un site de communauté.
>
>Par exemple, renommer l’URL ne déplace pas le contenu créé par l’utilisateur existant, ce qui a pour effet de &quot;perdre&quot; le contenu créé par l’utilisateur.

>[!CAUTION]
>
>La fonction groups doit *not* be *first ni unique* dans la structure du site.
>
>Toute autre fonction, telle que [fonction de page](functions.md#page-function), doit être inclus et répertorié en premier.

#### Exemple : Ajout d’une fonction Calendrier à une structure de sous-communauté (groupe) {#example-adding-a-calendar-function-to-a-sub-community-group-structure}

![chlimage_1-144](assets/chlimage_1-144.png)

### Modifier la conception {#modify-design}

Le panneau CONCEPTION permet de modifier le thème :

* [Thème de groupe de communautés](#community-group-theme)
* [Valorisation marque groupe communautés](#community-group-branding)

   * Faites défiler l’écran jusqu’au bas du panneau pour modifier l’image de marque.

### Modifier les paramètres {#modify-settings}

Le panneau PARAMÈTRES permet d’ajouter une communauté. [modérateurs](#moderation).

### Modifier l’appartenance {#modify-membership}

Le [ABONNEMENT](#membership) est fourni uniquement à titre d’information. Il n’est pas possible de modifier le type d’appartenance au groupe établi, qu’il soit facultatif, obligatoire ou restreint.

### Modifier la miniature {#modify-thumbnail}

Le [MINIATURE](#thumbnail) permet de charger une image afin de représenter le groupe de la communauté aux visiteurs du site dans l’environnement de publication, ainsi que dans la console Groupes du site Communities dans l’environnement de création.

## Publication du groupe {#publishing-the-group}

![chlimage_1-145](assets/chlimage_1-145.png)

Une fois qu’un groupe de communautés a été créé ou modifié, il est possible de le publier (d’activer) en sélectionnant `Publish Site` icône .

Une fois la publication du groupe terminée, un message s’affiche :

![chlimage_1-146](assets/chlimage_1-146.png)

>[!CAUTION]
>
>Le site de la communauté parente et les groupes parents doivent déjà avoir été publiés.
>
>Le site communautaire et les groupes imbriqués doivent être publiés de manière descendante.

## Suppression du groupe {#deleting-the-group}

![deleteicon](assets/deleteicon.png)

Supprimez un groupe dans la console Groupes de la communauté en sélectionnant l’icône Supprimer le groupe qui s’affiche lorsque vous placez le pointeur de la souris sur le groupe.

Cela supprime tous les éléments associés au groupe. Par exemple, tout le contenu du groupe est définitivement supprimé et les appartenances des utilisateurs sont supprimées du système.
