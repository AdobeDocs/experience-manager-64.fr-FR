---
title: Développement dans CRXDE Lite
seo-title: Developing with CRXDE Lite
description: CRXDE Lite est intégré à AEM et permet d’effectuer des tâches de développement standard dans le navigateur.
seo-description: CRXDE Lite is embedded into AEM and enables you to perform standard development tasks in the browser
uuid: a5eafc8c-f9fa-49ba-ad2f-0cccc427ca49
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: development-tools
content-type: reference
discoiquuid: 19cb3946-32ba-4f0b-89f0-f9272f2373d2
exl-id: 40e24cc6-95a9-4efd-b812-4144ba44b071
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '2167'
ht-degree: 57%

---

# Développement dans CRXDE Lite {#developing-with-crxde-lite}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Cette section décrit comment développer votre application AEM à l’aide de CRXDE Lite.

Pour plus d’informations sur les différents environnements de développement disponibles, reportez-vous à la documentation de présentation .

CRXDE Lite est intégré à CRX/CQ et permet d’effectuer des tâches de développement standard dans le navigateur. En vous connectant à CRXDE Lite, vous pouvez créer un projet, créer et modifier des fichiers (en .jsp et .java, par exemple), des dossiers, des modèles, des composants, des boîtes de dialogue, des nœuds, des propriétés et des bundles.

CRXDE Lite est recommandé si vous ne disposez pas d’un accès direct au serveur AEM, lorsque vous développez une application en étendant ou en modifiant les composants prêts à l’emploi et les bundles Java ou lorsque vous n’avez pas besoin d’un débogueur dédié, de la complétion de code et de la mise en surbrillance de la syntaxe.

>[!NOTE]
>
>À partir de la version 6.4.8.1 d’AEM, l’accès anonyme de CRXDE Lite n’est plus possible.
>Les utilisateurs sont redirigés vers l’écran de connexion.

>[!NOTE]
>
>Il est recommandé d’utiliser la variable [AEM Outils de développement pour Eclipse](/help/sites-developing/aem-eclipse.md) et le [AEM extension HTL Brackets](/help/sites-developing/aem-brackets.md) pendant le développement du projet.

## Prise en main de CRXDE Lite {#getting-started-with-crxde-lite}

Pour commencer à utiliser CRXDE Lite, procédez comme suit :

1. Installez AEM.
1. Dans votre navigateur, saisissez https://`<host>`:`<port>`/crx/de. Par défaut, le paramètre est `http://localhost:4502/crx/de`.
1. Entrez votre **nom d’utilisateur** et votre **mot de passe**. Par défaut, il s’agit de `admin` et `admin`.

1. Cliquez sur **OK**.

L’interface utilisateur de CRXDE Lite est la suivante dans votre navigateur :

![chlimage_1-238](assets/chlimage_1-238.png)

Vous pouvez désormais utiliser CRXDE Lite pour développer votre application.

### Présentation de l’interface utilisateur {#overview-of-the-user-interface}

CRXDE Lite offre les fonctionnalités suivantes :

<table> 
 <tbody> 
  <tr> 
   <td>Barre de commutation supérieure</td> 
   <td>Permet de basculer rapidement entre CRXDE Lite, Package Manager et Package Share.</td> 
  </tr> 
  <tr> 
   <td>Widget de chemin de noeud</td> 
   <td><p>Affiche le chemin d’accès au noeud actuellement sélectionné.</p> <p>Vous pouvez également l’utiliser pour accéder à un noeud, en entrant le chemin à la main ou en le collant à partir d’un autre emplacement, puis en appuyant sur Entrée.</p> <p>Il permet aussi de rechercher des nœuds par nom de nœud. Entrez le nom du nœud que vous souhaitez rechercher et patientez (ou appuyez sur le symbole de recherche sur le côté droit). Entrez par exemple la chaîne <em>oak</em> dans le widget pour voir comment la recherche fonctionne. Si un ou plusieurs nœuds sont chargés dans le volet de l’explorateur, la liste s’affiche et vous pouvez sélectionner le chemin et appuyer sur Entrée pour y accéder. Notez que la recherche ne fonctionne que pour les nœuds actuellement chargés dans l’application cliente CRXDE dans le navigateur. Si vous souhaitez effectuer une recherche dans l’ensemble du référentiel, utilisez Outils, puis Requête.</p> </td> 
  </tr> 
  <tr> 
   <td>Volet Explorateur</td> 
   <td><p>Affiche une arborescence de tous les noeuds du référentiel.</p> <p>Cliquez sur un nœud pour afficher ses propriétés dans l’onglet <strong>Propriétés</strong>. Après avoir cliqué sur un nœud, vous pouvez sélectionner une action dans la barre d’outils. Cliquez de nouveau sur le noeud pour le renommer.</p> <p>Filtre de navigation dans l’arborescence (icône en forme de paire de jumelles) : vous permet de filtrer les nœuds du référentiel pour lesquels le nom contient le texte saisi. S’applique uniquement aux nœuds qui ont été chargés localement.<br /> </p> </td> 
  </tr> 
  <tr> 
   <td>Volet Modifier</td> 
   <td><p><strong>Accueil</strong> tab : vous permet de rechercher du contenu et/ou de la documentation et d’accéder aux ressources des développeurs (documentation, blog de développeur, base de connaissances) et à l’assistance (page d’accueil et centre d’assistance d’Adobe).<br /> </p> <p>Double-cliquez sur un fichier dans le volet de <strong>l’explorateur</strong> pour afficher son contenu, par exemple un fichier .jsp ou un fichier .java. Vous pouvez ensuite le modifier et enregistrer les modifications.</p> <p>Une fois qu’un fichier est modifié dans la fonction <strong>Modifier</strong> , les outils suivants sont disponibles dans la barre d’outils :<br /> </p> - <strong>Afficher dans l’arborescence : </strong>affiche le fichier dans l’arborescence du référentiel.<br /> - <strong>Rechercher/remplacer...</strong>: effectuez une recherche ou un remplacement.<br /> <br /> Double-cliquez sur la ligne d’état du <strong>Modifier</strong> ouvre la fenêtre <strong>Aller à la ligne</strong> pour saisir un numéro de ligne spécifique à laquelle vous souhaitez accéder.<br /> </td> 
  </tr> 
  <tr> 
   <td>Onglet Propriétés.<br /> </td> 
   <td>Affiche les propriétés du nœud que vous avez sélectionné. Vous pouvez ajouter de nouvelles propriétés ou supprimer celles qui existent déjà.<br /> </td> 
  </tr> 
  <tr> 
   <td>Onglet Contrôle d’accès</td> 
   <td><p>Afficher les autorisations en fonction du chemin d’accès, du niveau du référentiel ou de l’entité de sécurité actuelle.</p> <p>Les autorisations sont divisées en</p> <p>- <strong>Stratégie de contrôle d’accès applicable</strong>: Stratégies pouvant être appliquées à la sélection en cours.</p> <p>- <strong>Stratégies de contrôle d’accès locales</strong>: Stratégies actuelles appliquées localement à la sélection actuelle.</p> <p>- <strong>Stratégies de contrôle d’accès efficaces</strong>: Les stratégies actuelles appliquées à la sélection actuelle peuvent être définies localement ou héritées des noeuds parents.</p> <p>Remarque. Pour pouvoir voir les informations de contrôle d’accès, l’utilisateur connecté à CRXDE Lite doit avoir le droit de lire les entrées ACL. L’utilisateur anonyme ne peut pas voir ces informations par défaut. Connectez-vous en tant qu’administrateur, par exemple pour voir les informations.</p> </td> 
  </tr> 
  <tr> 
   <td>Onglet Réplication</td> 
   <td><p>Affiche l’état de la réplication du nœud actif. Vous pouvez répliquer et supprimer la réplication du nœud actif.</p> </td> 
  </tr> 
  <tr> 
   <td>Onglet Console<br /> </td> 
   <td><p><strong>Journaux du serveur</strong>:</p> <p>Affiche les messages de journaux. Vous pouvez configurer le niveau de journalisation, effacer la console, épingler à la position de défilement sélectionnée et activer/désactiver l’affichage des messages.<br /> </p> <p><strong>Gestion de version</strong> :</p> <p>Affiche les messages de contrôle de version.<br /> </p> </td> 
  </tr> 
  <tr> 
   <td>Onglet Infos sur le build<br /> </td> 
   <td>Affiche des informations lorsqu’un lot est en cours de création.<br /> </td> 
  </tr> 
  <tr> 
   <td>Actualiser<br /> </td> 
   <td>Actualise la sélection actuelle. Les modifications des autres utilisateurs sont mises à jour dans votre vue du référentiel. Les modifications que vous avez apportées ne sont pas concernées.<br /> </td> 
  </tr> 
  <tr> 
   <td>Enregistrer tout</td> 
   <td><p><strong>Enregistrer tout</strong>:<br /> </p> <p>Enregistre tous les changements que vous avez apportés. Tant que vous n’avez pas cliqué sur Enregistrer, les modifications sont temporaires et seront perdues lorsque vous quitterez la console.</p> <p><strong>Rétablir</strong> :</p> <p>Ignore toutes les modifications que vous avez apportées au noeud sélectionné depuis la dernière action d’enregistrement, puis recharge l’état actuel du référentiel pour le noeud sélectionné.</p> <p><strong>Tout rétablir</strong>:</p> <p>Ignore toutes les modifications que vous avez apportées à l’ensemble du référentiel depuis la dernière action d’enregistrement, puis recharge l’état actuel du référentiel.</p> </td> 
  </tr> 
  <tr> 
   <td>Créer ...<br /> </td> 
   <td><p>Menu déroulant permettant de créer les éléments suivants sous le noeud sélectionné :<br /> </p> <p>- <strong>Noeud</strong>: un noeud avec un type de noeud arbitraire ;<br /> </p> <p>- <strong>Fichier</strong> : nœud nt:file et son sous-nœud nt:resource</p> <p>- <strong>Dossier</strong>: nt:folder node</p> <p>- <strong>Modèle</strong>: Modèle AEM</p> <p>- <strong>Composant</strong>: Composant AEM</p> <p>- <strong>Boîte de dialogue</strong>: Boîte de dialogue AEM</p> </td> 
  </tr> 
  <tr> 
   <td>Supprimer<br /> </td> 
   <td>Supprime le noeud sélectionné.<br /> </td> 
  </tr> 
  <tr> 
   <td>Copier</td> 
   <td>Copie le noeud sélectionné.<br /> </td> 
  </tr> 
  <tr> 
   <td>Coller<br /> </td> 
   <td>Colle le nœud copié sous le nœud sélectionné.<br /> </td> 
  </tr> 
  <tr> 
   <td>Déplacer ...<br /> </td> 
   <td>Déplace le noeud sélectionné vers le noeud défini dans la boîte de dialogue.</td> 
  </tr> 
  <tr> 
   <td>Renommer ...<br /> </td> 
   <td>Renomme le noeud sélectionné.<br /> </td> 
  </tr> 
  <tr> 
   <td>Mixins ...<br /> </td> 
   <td>Permet d’ajouter des types mixin au type de nœud. Les types de mixin sont principalement utilisés pour ajouter des fonctionnalités avancées telles que le contrôle de version, le contrôle d’accès, le référencement et le verrouillage au noeud.</td> 
  </tr> 
  <tr> 
   <td>Outils<br /> </td> 
   <td><p>Menu déroulant avec les outils suivants :</p> <p>- <strong>Configuration du serveur ...</strong>: pour accéder à la console Felix.</p> <p>- <strong>Requête ...</strong>: pour interroger le référentiel.</p> <p>- <strong>Privilèges ...</strong>: pour ouvrir la gestion des privilèges, où vous pouvez afficher et ajouter des privilèges.</p> <p>- <strong>Tester le contrôle d’accès ...</strong>: un emplacement où vous pouvez tester l’autorisation pour un chemin et/ou une entité.</p> <p>- <strong>Exporter le type de noeud</strong>: pour exporter les types de noeud dans le système en tant que notation cnd.</p> <p>- <strong>Importer le type de noeud...</strong>: pour importer des types de noeuds à l’aide de la notation cnd.</p>  <p>- <strong>Installer SiteCatalyst Debugger...</strong>: instructions sur l’installation d’Analytics Debugger.</p> </td> 
  </tr> 
  <tr> 
   <td>Widget de connexion<br /> </td> 
   <td><p>Affiche les utilisateurs actuellement connectés et l’espace de travail dans lequel ils sont connectés, par exemple admin@crx.default.</p> <p>Cliquez dessus pour vous connecter ou vous reconnecter en tant qu’utilisateur spécifique. Si vous ne spécifiez pas d’espace de travail auquel vous connecter, vous serez connecté à l’espace de travail par défaut, crx.default.</p> <p>Si vous souhaitez parcourir le référentiel en tant qu’utilisateur anonyme, utilisez <strong>anonyme</strong> comme nom de connexion et tout mot de passe (par exemple, un espace ou un point).<br /> </p> <p>Si votre autorisation n’est plus valide (par exemple, elle a expiré), le widget de connexion affiche « <strong>Connexion - Non autorisée ...</strong> ». Cliquez dessus pour vous reconnecter.</p> </td> 
  </tr> 
 </tbody> 
</table>

### Création d’un dossier {#creating-a-folder}

Pour créer un dossier avec CRXDE Lite :

1. Ouvrez CRXDE Lite dans un navigateur.
1. Dans le volet de navigation, cliquez avec le bouton droit sur le dossier sous lequel vous souhaitez créer le nouveau dossier, sélectionnez **Créer...**, puis **Créer un dossier...**.

1. Entrez le **nom** du dossier et cliquez sur **OK**.

1. Cliquez sur **Enregistrer tout** pour enregistrer les modifications sur le serveur.

### Création d’un modèle {#creating-a-template}

Pour créer un modèle avec CRXDE Lite :

1. Ouvrez CRXDE Lite dans un navigateur.
1. Dans le volet de navigation, cliquez avec le bouton droit sur le dossier dans lequel vous souhaitez créer le modèle, sélectionnez **Créer ...**, puis **Créer un modèle ...**.

1. Définissez les champs **Libellé**, **Titre**, **Description**, **Type de ressource** et **Classement** du modèle. Cliquez sur **Suivant**.

1. Cette étape est facultative : définissez **Chemins autorisés**. Cliquez sur **Suivant**.

1. Cette étape est facultative : définissez les **Parents autorisés**. Cliquez sur **Suivant**.

1. Cette étape est facultative : définissez les **Enfants autorisés**. Cliquez sur **OK**.

1. Cliquez sur **Enregistrer tout** pour enregistrer les modifications sur le serveur.

Il crée les éléments suivants :

* un nœud de type `cq:Template` avec les propriétés du modèle ;

* un nœud enfant de type `cq:PageContent` avec les propriétés de contenu de page.

Vous pouvez ajouter des propriétés à votre modèle : reportez-vous à la section [Création d’une propriété](#creating-a-property) .

### Création d’un composant {#creating-a-component}

La fonctionnalité décrite ici n’est disponible que si le type de noeud `cq:Component` est disponible dans le référentiel.

Pour créer un composant avec CRXDE Lite :

1. Ouvrez CRXDE Lite dans un navigateur.
1. Dans le volet de navigation, cliquez avec le bouton droit sur le dossier dans lequel vous souhaitez créer le composant, sélectionnez **Créer ...**, puis **Créer un composant ...**.

1. Définissez les champs **Libellé**, **Titre**, **Description**, **Super type ressource** et **Groupe** du modèle. Cliquez sur **Suivant**.

1. Cette étape est facultative : définissez les propriétés du composant **Est conteneur, Pas de décoration**, **Nom de cellule** et **Chemin de la boîte de dialogue**. Cliquez sur **Suivant**.

1. Cette étape est facultative : définissez la propriété de composant **Parents autorisés**. Cliquez sur **Suivant**.

1. Cette étape est facultative : définissez la propriété de composant **Enfant autorisé**. Cliquez sur **OK**.

1. Cliquez sur **Enregistrer tout** pour enregistrer les modifications sur le serveur.

Il crée les éléments suivants :

* un nœud de type `cq:Component`.
* Propriétés du composant
* Un script .jsp de composant

### Création d’une boîte de dialogue {#creating-a-dialog}

Pour créer une boîte de dialogue avec CRXDE Lite :

1. Ouvrez CRXDE Lite dans un navigateur.
1. Dans le volet de navigation, cliquez avec le bouton droit sur le composant dans lequel vous souhaitez créer la boîte de dialogue, sélectionnez **Créer ...**, puis **Créer une boîte de dialogue ...**.

1. Entrez le **Libellé** et le **Titre**. Cliquez sur **OK**.

1. Cliquez sur **Enregistrer tout** l pour enregistrer les modifications sur le serveur.

Il crée une boîte de dialogue avec la structure suivante :

`dialog[cq:Dialog]/items[cq:Widget]/items[cq:WidgetCollection]/tab1[cq:Panel]`

Vous pouvez maintenant adapter la boîte de dialogue à vos besoins en modifiant les propriétés ou en créant de nouveaux noeuds.

Vous pouvez également utiliser l’éditeur de boîte dialogue pour modifier une boîte de dialogue. Un double-clic sur le nœud dialog dans CRXDE Lite fait apparaître l’éditeur. Vous trouverez plus d’informations sur l’éditeur de boîte de dialogue [here](/help/sites-developing/dialog-editor.md).

### Création d’un nœud {#creating-a-node}

Pour créer un noeud avec CRXDE Lite :

1. Ouvrez CRXDE Lite dans un navigateur.
1. Dans le volet de navigation, cliquez avec le bouton droit sur le nœud où vous souhaitez créer le nouveau nœud, sélectionnez **Créer ...**, puis **Créer un nœud ...**.

1. Entrez le **Nom** et le **Type**. Cliquez sur **OK**.

1. Cliquez sur **Enregistrer tout** pour enregistrer les modifications sur le serveur.

Vous pouvez désormais adapter le nœud à vos besoins en modifiant les propriétés ou en ajoutant de nouveaux nœuds.

>[!NOTE]
>
>La plupart des opérations de modification, y compris Créer un nœud, conserve toutes les modifications en mémoire et les stocke dans le référentiel lors de l’enregistrement uniquement (avec le bouton Enregistrer tout). Cependant, certaines opérations telles que le déplacement sont automatiquement conservées.
>
>La validation du nœud nouvellement créé qui est ou non autorisé par le type de nœud du nœud parent est également effectuée par le référentiel JCR en premier, lors de l’enregistrement des modifications. Si vous recevez un message d’erreur lors de l’enregistrement d’un nœud, vérifiez si la structure du contenu est valide (par exemple, vous ne pouvez pas créer un nœud `nt:unstructured` en tant qu’enfant du nœud `nt:folder`).

### Création d’une propriété {#creating-a-property}

Pour créer une propriété avec CRXDE Lite :

1. Ouvrez CRXDE Lite dans un navigateur.
1. Dans le volet de navigation, sélectionnez le nœud dans lequel vous souhaitez ajouter la nouvelle propriété.
1. Dans l’onglet **Propriétés** du volet inférieur, entrez le **Nom**, le **Type** et la **Valeur**. Cliquez sur **Ajouter**.

1. Cliquez sur **Enregistrer tout** pour enregistrer les modifications sur le serveur.

### Création d’un script {#creating-a-script}

Pour créer un script :

1. Ouvrez CRXDE Lite dans un navigateur.
1. Dans le volet de navigation, cliquez avec le bouton droit de la souris sur le composant dans lequel vous souhaitez créer le script, puis sélectionnez **Créer ...**, puis **Créer un fichier ...**.

1. Entrez le **nom** du fichier, y compris son extension. Cliquez sur **OK**.

1. Le nouveau fichier s’ouvre sous la forme d’un onglet dans le volet Modifier.
1. Modifiez le fichier.
1. Cliquez sur **Enregistrer tout** pour enregistrer les modifications.

### Exportation et importation de types de nœuds {#exporting-and-importing-node-types}

[Avec CRXDE Lite, vous pouvez importer et exporter des définitions de type de nœud dans la notation CND (Compact Namespace et Node Type Definition).](http://jackrabbit.apache.org/jcr/node-type-notation.html)

Pour exporter une définition de type de noeud :

1. Ouvrez CRXDE Lite dans un navigateur.
1. Sélectionnez le noeud requis.
1. Sélectionnez **Outils**, puis **Exporter le type de nœud**.

1. La définition, en notation cnd, est affichée dans votre navigateur. Enregistrez les informations si nécessaire.

Pour importer une définition de type de noeud :

1. Ouvrez CRXDE Lite dans un navigateur.
1. Sélectionnez **Outils**, puis **Importer le type de nœud...**.

1. Saisissez la notation CND pour la définition dans la zone de texte.
1. Vérifier **Autoriser la mise à jour** si vous mettez à jour une définition existante.
1. Cliquez sur **Importer**.

### Journalisation {#logging}

CRXDE Lite permet d’afficher le fichier `error.log` qui se trouve sur le système de fichiers sous `<crx-install-dir>/crx-quickstart/server/logs` et de filtrer selon le niveau de journalisation approprié. Procédez comme suit :

1. Ouvrez CRXDE Lite dans un navigateur.
1. Dans le **Console** au bas de la fenêtre, dans le menu déroulant à droite, sélectionnez **Journaux du serveur**.

1. Cliquez sur le bouton **Arrêter** pour afficher les messages.

Vous pouvez :

* Ajuster les paramètres du journal dans la console Felix en cliquant sur l’icône **Configurations de journalisation**.
* Effacez les messages en cliquant sur le bouton **Pinceau** icône .
* Épingler le message à la sélection en cours en cliquant sur l’icône **Épingler**.
* Activer ou désactiver l’affichage des messages en cliquant sur l’icône **Stop**.

## Contrôle d’accès {#access-control}

>[!NOTE]
>
>Consultez [Administration des utilisateurs, groupes et droits d’accès](/help/sites-administering/user-group-ac-admin.md) pour plus d’informations.
