---
title: Console Groupes de communautés
seo-title: Console Groupes de communautés
description: La console Groupes permet de créer des groupes de la communauté
seo-description: La console Groupes permet de créer des groupes de la communauté
uuid: 7dac2d1b-78fc-4b39-a2cb-100f1e220c23
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 1293c01a-7308-494a-ab48-bd9938205b81
pagetitle: Community Groups Console
translation-type: tm+mt
source-git-commit: 28948f1f8678512f8fc970a4289cb01cde86c5c2

---


# Console Groupes de communautés {#community-groups-console}

La console Groupes permet de créer des groupes de la communauté lorsqu’une structure [de](sites-console.md#step1) modèle de site de la communauté inclut la fonction [](functions.md#groups-function)Groupes.

* Les groupes peuvent être imbriqués dans d’autres groupes. Cela se produit lorsque la [structure du nouveau groupe](tools-groups.md) contient la fonction de groupes.
* Pour l’environnement de création uniquement, il existe un assistant de création de groupe similaire à l’assistant de création de site.
* Il est possible de configurer la possibilité pour les membres de créer des groupes à partir de l’environnement de publication lors de l’ajout d’une fonction Groupes à une structure de site communautaire ou de groupe communautaire.

Parmi les trois modèles de groupe inclus, seul le `Reference Group` modèle inclut une fonction de groupe dans sa structure.

Plusieurs facettes des groupes communautaires sont :

* Création : un nouveau groupe peut être créé à l’auteur et, éventuellement, à la publication
* Contrôle : groupe peut être ouvert ou secret
* Imbrication : un groupe peut contenir zéro ou plusieurs groupes

>[!NOTE]
>
>Les groupes communautaires créés dans l’environnement de publication avant l’ [existence de la console](https://helpx.adobe.com/in/experience-manager/6-3/communities/using/version-history.html#FeaturePack1FP1)Groupes communautaires ne seront pas répertoriés dans la console Groupes communautaires et ne pourront donc pas être modifiés à l’aide de la console.

>[!NOTE]
>
>Cette console Groupes, accessible uniquement à partir de la console Sites des communautés, ne doit pas être confondue avec la console [](members.md) Groupes de membres pour la gestion des groupes de membres.
>
>Les groupes de membres sont des groupes d’utilisateurs enregistrés dans l’environnement de publication et accessibles depuis l’environnement d’auteur à l’aide du service [](deploy-communities.md#tunnel-service-on-author)tunnel.

## Création de groupe {#group-creation}

Pour accéder à la console Groupes :

* Sur l’auteur, connectez-vous avec les droits d’administrateur
* A partir de la navigation globale : **[!UICONTROL Communautés > Sites]**
* Sélectionner un dossier de site communautaire existant pour l&#39;ouvrir
* Sélection d’une instance d’un site de la communauté dans le dossier

   * La structure du site communautaire doit inclure une fonction de groupe
   * Ces captures d’écran proviennent du didacticiel Prise en main après [création de groupes lors de la publication](published-site.md)

![chlimage_1-133](assets/chlimage_1-133.png)

Sélectionnez le dossier **** Groupes pour l’ouvrir.

Lorsqu’ils sont ouverts, tous les groupes existants, qu’ils soient créés à l’auteur ou à la publication, s’affichent.

Dans cette console Groupes, il est possible de créer de nouveaux groupes.

![chlimage_1-134](assets/chlimage_1-134.png)

* Sélectionner **[!UICONTROL Créer un groupe]** , bouton

### Étape 1 : Modèle Groupe de communautés {#step-community-group-template}

![groupe multilingue](assets/multilingualgroup.png)

* **[!UICONTROL Titre]** du groupe de la communauté : Titre d’affichage du groupe.

   Le titre s’affiche sur le site publié pour le groupe.

* **[!UICONTROL Groupe de communautés Description]**: Description du groupe.
* **[!UICONTROL Racine]** du groupe de communautés : Chemin racine du groupe.

   La racine par défaut est le site parent, mais elle peut être déplacée à n’importe quel emplacement du site Web. Il n’est pas recommandé de le modifier.

* **[!UICONTROL Autres groupes communautaires disponibles]** Menu Langues : Utilisez le menu déroulant pour sélectionner la ou les langues des groupes communautaires disponibles. Le menu affiche toutes les langues dans lesquelles le site de la communauté parent est créé. Les utilisateurs peuvent sélectionner l’une de ces langues pour créer des groupes dans plusieurs paramètres régionaux au cours de cette seule étape. Un même groupe est créé dans plusieurs langues spécifiées dans la console Groupes des sites de communauté respectifs.

* **[!UICONTROL Nom]** du groupe de la communauté : Nom de la page racine du groupe qui apparaît dans l’URL

   * Vérifiez deux fois le nom, car il n’est pas facilement modifié une fois le groupe créé.
   * L’URL de base s’affichera sous le `Community Group Name`
   * Pour une URL valide, ajoutez &quot;.html&quot;

      *Par exemple*, `http://localhost:4502/content/sites/mysight/en/mygroup.html`

* **[!UICONTROL Menu Modèle]** de groupe de communautés : utilisez le menu déroulant pour choisir un modèle [de groupe](tools.md)communautaire disponible.

### Étape 2 : Conception {#step-design}

#### COMMUNITY GROUP THEME {#community-group-theme}

![community_grouptheme](assets/communitygrouptheme.png)

La structure utilise [Twitter Bootstrap](https://twitterbootstrap.org/) pour apporter une conception adaptée et flexible au site. L’un des nombreux thèmes d’amorçage préchargés peut être sélectionné pour mettre en forme le modèle de groupe de communautés sélectionné ou un thème d’amorçage peut être téléchargé.

Une fois sélectionné, le thème sera superposé avec une coche bleue opaque.

Il est possible de sélectionner un thème différent du thème du site parent.

Une fois le site de la communauté publié, il est possible de [modifier les propriétés](#modifying-group-properties) et de sélectionner un autre thème.

#### COMMUNITY GROUP BRANDING {#community-group-branding}

![chlimage_1-135](assets/chlimage_1-135.png)

L’image de marque du site de la communauté est une image affichée sous forme d’en-tête dans la partie supérieure de chaque page. Il est possible d&#39;afficher une bannière pour le groupe qui diffère des autres pages du site.

L’image doit être dimensionnée de manière à être aussi large que l’affichage prévu de la page dans le navigateur et à 120 pixels de hauteur.

Lorsque vous créez ou sélectionnez une image, gardez à l’esprit :

* La hauteur de l’image sera rognée à 120 pixels, mesurée à partir du bord supérieur de l’image.
* L’image est épinglée sur le bord gauche de la fenêtre du navigateur.
* L’image n’est pas redimensionnée, de telle sorte que lorsque la largeur de l’image est...

   * Inférieur à la largeur du navigateur, l’image se répète horizontalement.
   * Plus grande que la largeur du navigateur, l’image semble recadrée.

### Étape 3 : Paramètres {#step-settings}

#### MODERATION {#moderation}

![chlimage_1-136](assets/chlimage_1-136.png)

Par défaut, la liste des modérateurs du site de la communauté parent est héritée.

Il est possible d’ajouter des modérateurs spécifiques au groupe :

* Rechercher des membres (de l’environnement de publication) pour les ajouter en tant que modérateurs

#### MEMBERSHIP {#membership}

Le paramètre d&#39;adhésion permet de choisir l&#39;une des trois façons de sécuriser un groupe communautaire.

![chlimage_1-137](assets/chlimage_1-137.png)

* Abonnement facultatif

   S’il est sélectionné, le groupe de la communauté est un groupe public. Les membres du site peuvent participer au groupe et publier sans rejoindre explicitement le groupe. La valeur par défaut est sélectionnée.
* Abonnement requis

   s’il est sélectionné, le groupe communautaire est un groupe ouvert. Les membres du site de la communauté peuvent consulter le contenu du groupe, mais doivent rejoindre le groupe avant de pouvoir publier du contenu. Les membres se joignent en sélectionnant le `Join` bouton dans l’environnement de publication. La valeur par défaut n’est pas sélectionnée.

* Abonnement restreint

   s’il est sélectionné, le groupe communautaire est un groupe secret. Les membres de la communauté doivent être explicitement invités. Les membres invités sont saisis dans la zone de recherche. Les membres peuvent être ajoutés ultérieurement à l’aide des consoles [Membres et Groupes](members.md) de l’environnement d’auteur. La valeur par défaut n’est pas sélectionnée.

#### Miniature {#thumbnail}

![chlimage_1-138](assets/chlimage_1-138.png)

La miniature est une image à afficher pour le groupe sur l’auteur et la publication.

La taille optimale d’une image de groupe est de 170 x 90 pixels dans un format d’image pris en charge (JPG ou PNG, par exemple).

Si aucune image n’est ajoutée, une image par défaut est affichée.

![chlimage_1-139](assets/chlimage_1-139.png)

### Étape 4 : Créer un groupe {#step-create-group}

![chlimage_1-140](assets/chlimage_1-140.png)

Si des ajustements sont nécessaires, utilisez le bouton **Précédent** pour les effectuer.

Une fois **Créer** sélectionné et démarré, le processus de création du groupe ne peut plus être interrompu.

Une fois le processus terminé, la carte du nouveau site (groupe) de sous-communauté s’affiche dans la console Communautés Sites Groupes, d’où les auteurs peuvent ajouter du contenu de page ou les administrateurs peuvent modifier les propriétés du site.

![createcommunitygroup-1](assets/createcommunitygroup-1.png)

>[!NOTE]
>
>Le groupe est créé dans toutes les langues, comme indiqué à l’ [étape 1 : Modèle](groups.md#step1communitygrouptemplate) de groupe communautaire dans d’autres langues de groupe communautaire disponibles, dans la console Groupes communautaires des sites communautaires respectifs.

## Création de contenu de groupe {#authoring-group-content}

![chlimage_1-141](assets/chlimage_1-141.png)

Le contenu de la page d’un groupe peut être créé avec les mêmes outils que toute autre page AEM. Pour ouvrir le groupe en vue de sa création, sélectionnez l’icône Ouvrir le site qui s’affiche lorsque vous passez la souris sur la carte du groupe.

## Modification des propriétés du groupe {#modifying-group-properties}

Les propriétés d’un site de sous-communauté existant, spécifiées au cours du processus de création de groupe de communauté, peuvent être modifiées en sélectionnant l’icône Modifier le site qui s’affiche lorsque vous passez la souris sur la carte du groupe :

![chlimage_1-142](assets/chlimage_1-142.png)

Les détails des propriétés suivantes correspondent aux descriptions fournies dans la section Création [de](#group-creation) groupe. Tout groupe imbriqué peut être modifié, qu’il soit créé dans l’environnement de publication ou dans l’environnement de création.

![chlimage_1-143](assets/chlimage_1-143.png)

### Modification de base {#modify-basic}

Le panneau BASIC permet de modifier les

* Titre de groupe de communautés
* Description du groupe de communautés

Le nom du groupe de la communauté ne peut pas être modifié.

Le choix d’un modèle de groupe de communautés différent n’aurait aucun impact sur un site de groupes de communautés existant, car il n’existe aucune connexion entre les modèles et les sites.

La [STRUCTURE](#modify-structure) de la sous-communauté peut plutôt être modifiée.

### Modifier la structure {#modify-structure}

Le panneau STRUCTURE permet de modifier la structure initialement créée à partir du modèle de groupe de communautés sélectionné lors de la création du site de sous-communauté à partir de l’environnement d’auteur ou de publication. Depuis le panneau, il est possible de

* Faire glisser des fonctions [de](functions.md) communauté supplémentaires dans la structure du site
* Sur une instance d’une fonction de communauté dans la structure du site :

   * **`gear icon`**

      Modifier les paramètres, y compris le titre d’affichage et le nom de l’URL, ainsi que les groupes de membres [privilégiés](users.md#privilegedmembersgroups)

   * **`trashcan icon`**

      Supprimer (supprimer) des fonctions de la structure du site

   * **`grid icon`**

      Modifier l&#39;ordre des fonctions tel qu&#39;il s&#39;affiche dans la barre de navigation de niveau supérieur du site

>[!CAUTION]
>
>Bien que le titre d’affichage puisse être modifié sans effets secondaires, il n’est pas recommandé de modifier le nom d’URL d’une fonction de communauté appartenant à un site de la communauté.
>
>Par exemple, renommer l’URL ne déplace pas l’UGC existant, avec pour effet de &quot;perdre&quot; l’UGC.

>[!CAUTION]
>
>La fonction de groupes *ne doit pas* être la *première ou la seule* fonction de la structure du site.
>
>Toute autre fonction, telle que la fonction [de](functions.md#page-function)page, doit être incluse et répertoriée en premier.

#### Exemple : Ajout d’une fonction de calendrier à une structure de sous-communauté (groupe) {#example-adding-a-calendar-function-to-a-sub-community-group-structure}

![chlimage_1-144](assets/chlimage_1-144.png)

### Modifier la conception {#modify-design}

Le panneau DESIGN permet de modifier le thème :

* [Thème de groupe de communautés](#community-group-theme)
* [Valorisation marque groupe communautés](#community-group-branding)

   * Accédez au bas du panneau pour modifier l’image de marque.

### Modifier les paramètres {#modify-settings}

Le panneau PARAMÈTRES permet d’ajouter des [modérateurs](#moderation)de communauté.

### Modifier l’adhésion {#modify-membership}

Le groupe [MEMBRES](#membership) est uniquement informatif. Il n&#39;est pas possible de modifier le type d&#39;appartenance au groupe établi, qu&#39;il soit facultatif, obligatoire ou restreint.

### Modifier la miniature {#modify-thumbnail}

Le panneau [VIGNETTE](#thumbnail) permet de télécharger une image pour représenter le groupe de la communauté aux visiteurs du site dans l&#39;environnement de publication ainsi que dans la console Groupes du site des communautés dans l&#39;environnement de création.

## Publication du groupe {#publishing-the-group}

![chlimage_1-145](assets/chlimage_1-145.png)

Après la création ou la modification d’un groupe de la communauté, il est possible de le publier (activer) en sélectionnant l’ `Publish Site` icône.

Une fois le groupe publié, un message s’affiche :

![chlimage_1-146](assets/chlimage_1-146.png)

>[!CAUTION]
>
>Le site de la communauté parent et les groupes parents auraient déjà dû être publiés.
>
>Le site communautaire et les groupes imbriqués devraient être publiés de manière descendante.

## Suppression du groupe {#deleting-the-group}

![deleteicon](assets/deleteicon.png)

Supprimez un groupe dans la console Groupes de la communauté en sélectionnant l’icône Supprimer le groupe qui s’affiche lorsque vous passez la souris sur le groupe.

Cela supprime tous les éléments associés au groupe, par exemple tout le contenu du groupe est définitivement supprimé et les abonnements des utilisateurs sont supprimés du système.
