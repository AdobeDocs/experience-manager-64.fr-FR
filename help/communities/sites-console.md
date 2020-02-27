---
title: Console Sites de communautés
seo-title: Console Sites de communautés
description: Accès à la console Sites des communautés
seo-description: Accès à la console Sites des communautés
uuid: 85017055-b8af-4eeb-a8ab-1cbbba0f5a6a
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 5ac2fcef-05b8-46f7-9a15-997cdd79a3db
translation-type: tm+mt
source-git-commit: 5e30bf76fd3304ed268c45cc8862a9c51c5d30f1

---


# Console Sites de communautés {#communities-sites-console}

La console Sites des communautés donne accès à :

* Création de site
* Modification du site
* Gestion de site
* [Création et modification de groupes](groups.md) imbriqués (sous-communautés)

Reportez-vous à la page [Prise en main des communautés](getting-started.md) AEM pour découvrir à quelle vitesse un site communautaire peut être créé dans l’environnement d’auteur, ainsi que la création de groupes communautaires à partir des environnements d’auteur et de publication.

>[!NOTE]
>
>Les principaux menus Collectivités pour la création de sites [](sites-console.md)communautaires, de modèles [de sites](sites.md)communautaires, de modèles [de groupes](tools-groups.md) communautaires et de fonctions de [communauté ne sont utilisés que dans l’environnement de création.](functions.md)

## Conditions préalables {#prerequisites}

Avant de créer un site communautaire, vous *devez* :

* Vérifier qu’une ou plusieurs instances de publication sont en cours d’exécution
* Activer le service [](deploy-communities.md#tunnel-service-on-author) tunnel pour gérer les membres et les groupes de membres
* Identifier l’éditeur [principal](deploy-communities.md#primary-publisher)
* [Configuration de la réplication](deploy-communities.md#replication-agents-on-author) lorsque le port d’éditeur principal n’est pas le port par défaut (4503)

Pour vous assurer que le site est prêt à prendre en charge de nombreuses fonctionnalités, il est recommandé de procéder comme suit :

* Installation du [dernier Feature Pack](deploy-communities.md#latestfeaturepack)
* Activer [Adobe Analytics](analytics.md) pour les communautés AEM
* Configurer le [courrier électronique](email.md)
* Identification des administrateurs [de communauté](users.md#creating-community-members)
* [Activer le gestionnaire](social-login.md#adobe-granite-oauth-authentication-handler) OAuth pour la connexion sociale

## Accès à la console Sites de communautés {#accessing-communities-sites-console}

Dans l’environnement de création, pour accéder à la console Sites des communautés :

* A partir de la navigation globale : **[!UICONTROL Communautés > Sites]**

La console Sites des communautés affiche tous les sites communautaires existants. A partir de cette console, les sites de la communauté peuvent être créés, modifiés, gérés et supprimés.

Pour créer un site communautaire, sélectionnez l’icône **Créer** .

Pour accéder à un site communautaire existant, sélectionnez l’icône de dossier des sites afin de créer, modifier, publier, exporter ou ajouter un groupe imbriqué.

Par exemple, l’image suivante montre la console Sites des communautés principale qui affiche les dossiers de deux sites de la communauté : [activer](getting-started-enablement.md) et [engager](getting-started.md):

![chlimage_1-448](assets/chlimage_1-448.png)

## Création de site {#site-creation}

La console de création de site fournit une approche pas à pas pour assembler les fonctionnalités du site en fonction d’un modèle [et de paramètres de site](sites.md) communautaire sélectionnés.

Chaque site créé comprend une fonction de connexion, car les visiteurs du site doivent se connecter avant de pouvoir publier du contenu, envoyer des messages ou participer à un groupe. Les autres fonctionnalités incluses sont les profils utilisateur, la messagerie, les notifications, le menu du site, la recherche, le thème et la marque.

Le processus est lancé en sélectionnant le `Create` bouton situé en haut de la console Sites des communautés.

Le processus de création est une série d’étapes présentées sous forme de panneaux contenant un ensemble de fonctionnalités à configurer (présentées sous forme de sous-panneaux). Il est possible de passer à l’étape **suivante** ou **** de revenir à l’étape précédente avant de valider le site dans l’étape finale.

### Étape 1 : Modèle de site {#step-site-template}

![newsitetemplate](assets/newsitetemplate.png)

Dans le panneau Modèle de site, le titre, la description, la racine du site, la langue de base, le nom et le modèle de site sont spécifiés :

* **[!UICONTROL Titre]** du site de la communauté : Titre d’affichage du site.

   Le titre s’affiche sur le site publié ainsi que dans l’interface utilisateur d’administration du site.

* **[!UICONTROL Description]** du site de la communauté : Description du site.

   La description n’apparaît pas sur le site publié.

* **[!UICONTROL Racine]** du site de la communauté : Chemin d’accès racine au site.

   La racine par défaut est `/content/sites`, mais elle peut être déplacée à n’importe quel emplacement du site Web.

* **[!UICONTROL Langue]** de base du site de la communauté : (ne pas toucher à la langue unique : Anglais) utilisez le menu déroulant pour choisir une *ou plusieurs* langues de base disponibles : allemand, italien, français, japonais, espagnol, portugais (Brésil), chinois (traditionnel) et chinois (simplifié). Un site communautaire sera créé pour chaque langue ajoutée et existera dans le même dossier de site, conformément aux bonnes pratiques décrites dans la section [Traduction de contenu pour les sites](../../help/sites-administering/translation.md)multilingues. La page racine de chaque site contiendra une page enfant nommée par le code de langue de l&#39;une des langues sélectionnées, comme &quot;en&quot; pour l&#39;anglais ou &quot;fr&quot; pour le français.

* **[!UICONTROL Nom]** du site de la communauté : Nom de la page racine du site qui apparaît dans l’URL

   * Vérifiez deux fois le nom, car il n&#39;est pas facilement modifié une fois le site créé.
   * L’URL de base ( `https://*server:port/site root/site name*)` s’affichera sous le `Community Site Name`
   * Pour une URL valide, ajoutez un code de langue de base + &quot;.html&quot;

      *Par exemple*, `http://localhost:4502/content/sites/mysight/en.html`

* **[!UICONTROL Menu Modèle]** de site de la communauté : Utilisez le menu déroulant pour choisir un modèle [de site](tools.md)communautaire disponible.

Sélectionnez **[!UICONTROL Suivant]**

### Étape 2 : Conception {#step-design}

Le panneau Conception contient deux sous-panneaux permettant de sélectionner le thème et la bannière de marque :

#### COMMUNITY SITE THEME {#community-site-theme}

![sitetheme-1](assets/sitetheme-1.png)

La structure utilise [Twitter Bootstrap](https://twitterbootstrap.org/) pour apporter une conception adaptée et flexible au site. L&#39;un des nombreux thèmes d&#39;amorçage préchargés peut être sélectionné pour mettre en forme le modèle de site de la communauté sélectionnée ou un thème d&#39;amorçage peut être téléchargé.

Une fois sélectionné, le thème sera superposé avec une coche bleue opaque.

Une fois le site de la communauté publié, il est possible de [modifier les propriétés](#modifying-site-properties) et de sélectionner un autre thème.

#### COMMUNITY SITE BRANDING {#community-site-branding}

![chlimage_1-449](assets/chlimage_1-449.png)

L’image de marque du site de la communauté est une image affichée sous forme d’en-tête dans la partie supérieure de chaque page.

L’image doit être dimensionnée de manière à être aussi large que l’affichage prévu de la page dans le navigateur et à 120 pixels de hauteur.

Lorsque vous créez ou sélectionnez une image, gardez à l’esprit :

* La hauteur de l’image sera rognée à 120 pixels, mesurée à partir du bord supérieur de l’image.
* L’image est épinglée sur le bord gauche de la fenêtre du navigateur.
* L’image n’est pas redimensionnée, de telle sorte que lorsque la largeur de l’image est...

   * Inférieur à la largeur du navigateur, l’image se répète horizontalement.
   * Plus grande que la largeur du navigateur, l’image semble recadrée.

Sélectionnez **[!UICONTROL Suivant]**.

### Étape 3 : Paramètres {#step-settings}

Le panneau Paramètres contient plusieurs sous-panneaux présentant les fonctionnalités à configurer avant de passer à la dernière étape de création du site.

* [GESTION DES UTILISATEURS](#user-management)
* [BALISAGE](#tagging)
* [RÔLES](#roles)
* [MODÉRATION](#moderation)
* [ANALYTICS](#analytics)
* [TRADUCTION](#translation)
* [ACTIVER](#enablement)

>[!NOTE]
>
>**Activer le service de tunnel**
>
>Plusieurs des sous-panneaux Paramètres permettent d’affecter un membre de confiance pour modérer l’UGC, gérer des groupes ou être des contacts pour les ressources d’activation dans l’environnement de publication.
>
>La convention permet aux [utilisateurs et aux groupes](users.md) d’utilisateurs côté publication (membres et groupes de membres) de ne pas être dupliqués dans l’environnement d’auteur.
>
>Ainsi, lors de la création du site de la communauté dans l’environnement d’auteur et de l’affectation de membres de confiance à différents rôles, il est nécessaire de récupérer les données des membres de l’environnement de publication.
>
>Pour ce faire, activez l’environnement ` [AEM Communities Publish Tunnel Service](deploy-communities.md#tunnel-service-on-author)`de création.

#### USER MANAGEMENT {#user-management}

![createsitesettings-1](assets/createsitesettings-1.png)

>[!NOTE]
>
>Il est recommandé que les sites [de la communauté d’](overview.md#enablement-community) activation soient privés (pour plus d’informations, contactez votre gestionnaire de compte).
>
>Un site communautaire est privé lorsque les visiteurs anonymes du site se voient refuser l’accès, qu’ils ne s’enregistrent pas eux-mêmes et qu’ils ne peuvent pas utiliser la connexion sociale.

* **[!UICONTROL Autoriser l&#39;enregistrement d&#39;utilisateur]**

   Si cette option est cochée, les visiteurs du site peuvent devenir membres de la communauté par auto-inscription.

   Si cette option n’est pas cochée, le site communautaire est *restreint* et les visiteurs du site doivent être affectés au groupe de membres du site, faire une demande ou être envoyés par courrier électronique. Si cette option est désactivée, l’accès anonyme ne doit pas être autorisé.

   Désélectionnez un site *communautaire privé* . Cette option est cochée par défaut.

* **[!UICONTROL Autoriser l&#39;accès anonyme]**

   Si cette option est cochée, le site communautaire est *ouvert* et tout visiteur du site peut y accéder.

   Si cette option est désactivée, seuls les membres connectés peuvent accéder au site.

   Désélectionnez un site *communautaire privé* . Cette option est cochée par défaut.

* **[!UICONTROL Autoriser les messages]**

   Si cette option est cochée, les membres peuvent envoyer des messages entre eux et au groupe sur le site communautaire.

   Si cette option est désactivée, la messagerie n’est pas configurée pour la communauté.

   Cette option n’est pas cochée par défaut.

* **[!UICONTROL Autoriser les connexions sociales : Facebook]**

   Si cette option est cochée, autorisez les visiteurs du site à se connecter avec leurs identifiants de compte Facebook. La configuration [de cloud](social-login.md#create-a-facebook-connect-cloud-service) Facebook sélectionnée doit être configurée pour ajouter des utilisateurs au groupe de membres du site de la communauté une fois le site de la communauté créé.

   Si cette option est désactivée, aucune connexion Facebook n’est présentée.

   Ne vérifiez pas la présence d’un site communautaire *privé* . Cette option n’est pas cochée par défaut.

* **[!UICONTROL Autoriser les connexions sociales : Twitter]**

   Si cette option est cochée, autorisez les visiteurs du site à se connecter à l’aide de leurs identifiants de compte Twitter. La configuration [de cloud](social-login.md#create-a-twitter-connect-cloud-service) Twitter sélectionnée doit être configurée pour ajouter des utilisateurs au groupe de membres du site de la communauté une fois le site de la communauté créé.

   Si cette option est désactivée, aucune connexion Twitter n’est présentée.

   Ne vérifiez pas la présence d’un site communautaire *privé* . Cette option n’est pas cochée par défaut.

>[!NOTE]

**[!UICONTROL Autorisation des connexions aux réseaux sociaux]**
>Bien que des exemples de configurations Facebook et Twitter puissent exister et être sélectionnables, pour un environnement [de](../../help/sites-administering/production-ready.md)production, il est nécessaire de créer des applications Facebook et Twitter personnalisées. Voir Connexion [aux réseaux sociaux avec Facebook et Twitter](social-login.md).
>
#### TAGGING {#tagging}

![chlimage_1-450](assets/chlimage_1-450.png)

Les balises qui peuvent être appliquées au contenu de la communauté sont contrôlées en sélectionnant des espaces de noms de balise précédemment définis dans la console [de](../../help/sites-administering/tags.md#tagging-console)balisage.

En outre, la sélection des espaces de noms de balises pour le site de la communauté limite la sélection présentée lors de la définition de catalogues et de ressources. Voir Ressources [d’activation du](tag-resources.md) balisage pour obtenir des informations importantes.

* Zone de recherche de texte : Commencer à taper pour identifier les balises autorisées à être utilisées sur le site

#### ROLES {#roles}

![chlimage_1-451](assets/chlimage_1-451.png)

Les [rôles des membres](users.md) de la communauté sont assignés avec ces paramètres.

Il est facile de trouver des membres de la communauté en effectuant une recherche par type.

* **[!UICONTROL Gestionnaires de la communauté]**

   Commencez à taper pour sélectionner un ou plusieurs membres de la communauté ou groupes de membres qui peuvent gérer des membres de la communauté et des groupes de membres.

* **[!UICONTROL Modérateurs de la communauté]**

   Commencez la saisie pour sélectionner un ou plusieurs membres de la communauté ou groupes de membres auxquels il faut faire confiance en tant que modérateurs du contenu généré par l’utilisateur.

* **[!UICONTROL Membres privilégiés de la communauté]**

   Commencez à taper pour sélectionner un ou plusieurs membres de la communauté ou groupes de membres afin de pouvoir créer du contenu lorsqu’ `Allow Privileged Member` il a été sélectionné pour une fonction [de](functions.md)communauté.

#### MODERATION {#moderation}

![chlimage_1-452](assets/chlimage_1-452.png)

Le paramètre global de modération du contenu généré par l’utilisateur (UGC) est contrôlé par ces paramètres. Les composants individuels disposent de paramètres supplémentaires pour contrôler la modération.

* **[!UICONTROL Le contenu est prémodéré]**

   Si cette option est cochée, le contenu de la communauté publié n’apparaîtra pas avant d’être approuvé par un modérateur. Cette option n’est pas cochée par défaut. For more information, see [Moderating Community Content](moderate-ugc.md#premoderation).

* **[!UICONTROL Seuil de marquage avant que le contenu ne soit masqué]**

   Si la valeur est supérieure à 0, le nombre de fois où une rubrique ou une publication doit être marquée avant d’être masquée dans la vue publique. Si elle est définie sur -1, la rubrique ou la publication marquée n’est jamais masquée de la vue publique. La valeur par défaut est 5.

#### ANALYTICS {#analytics}

![chlimage_1-453](assets/chlimage_1-453.png)

* **[!UICONTROL Activer les analyses]**

   Disponible uniquement lorsque Adobe Analytics a été [configuré](analytics.md) pour les fonctionnalités des communautés.

   Cette option n’est pas cochée par défaut. Si cette option est activée, un menu de sélection supplémentaire s’affiche :

![chlimage_1-454](assets/chlimage_1-454.png)

* **[!UICONTROL Référence de la structure de configuration du cloud]**

   Dans le menu déroulant, sélectionnez la structure de service cloud Analytics configurée pour ce site de la communauté.

   `Communities`est l’exemple de structure de la documentation sur la configuration [Analytics pour les fonctionnalités](analytics.md#aem-analytics-framework-configuration) des communautés.

#### TRANSLATION {#translation}

![chlimage_1-455](assets/chlimage_1-455.png)

* **[!UICONTROL Autoriser la traduction]** automatique Lorsque cette option est cochée (la valeur par défaut est désactivée), la traduction automatique est activée pour l’UGC dans le site. Cela n’affecte aucun autre contenu, tel que le contenu de la page, même si le site est configuré en tant que site multilingue. Voir [Traduction de contenu](translate-ugc.md) généré par l’utilisateur pour en savoir plus sur la configuration d’un service de traduction sous licence pour les communautés AEM. Voir [Traduction de contenu pour les sites](../../help/sites-administering/translation.md) multilingues pour obtenir un aperçu complet.

![chlimage_1-456](assets/chlimage_1-456.png)

* **[!UICONTROL Activer la traduction automatique pour les langues sélectionnées]**

   Les langues activées pour la traduction automatique sont par défaut définies dans le paramètre système spécifié par la configuration [de l’intégration de la](translate-ugc.md#translation-integration-configuration)traduction. Ces paramètres par défaut peuvent être remplacés pour ce site en supprimant les valeurs par défaut et/ou en sélectionnant d’autres langues dans le menu déroulant.

* **[!UICONTROL Sélectionner le fournisseur de traduction]**

   Par défaut, le fournisseur de services est un service d’évaluation utilisé `microsoft`pour la démonstration uniquement. Si aucun fournisseur de services de traduction n’est autorisé, **l’option Autoriser la traduction** automatique doit être désactivée.

* **[!UICONTROL Sélectionner le magasin partagé global]**

   Pour un site Web avec plusieurs copies de langue, une boutique partagée globale fournit un seul fil de conversation, visible à partir de chaque copie de langue. Pour ce faire, sélectionnez l&#39;une des langues incluses comme copie de langue. La valeur par défaut est *Pas de magasin* partagé global.

* **[!UICONTROL Sélectionner la configuration du fournisseur de traduction]**

   Choisissez une structure [d’intégration de](../../help/sites-administering/tc-tic.md) traduction créée pour le fournisseur de traduction sous licence.

* **Sélectionner les options de traduction pour votre site de la communauté**

   * **[!UICONTROL Traduire la page entière]**

      Si cette option est sélectionnée, tous les UGC d’une page sont traduits dans la langue de base de la page.

      La valeur par défaut *n’est pas sélectionnée*.

   * **[!UICONTROL Traduire la sélection uniquement]**

      Si cette option est sélectionnée, une option de traduction s’affiche en regard de chaque publication, ce qui permet de traduire des publications individuelles dans la langue de base de la page.

      Default is *selected*.

* **Sélectionner les options de rémanence**

   * **[!UICONTROL Traduire les contributions à la demande de l’utilisateur et les conserver ensuite]**

      Si cette option est sélectionnée, le contenu n’est pas traduit tant qu’une requête n’a pas été effectuée. Une fois traduite, la traduction est stockée dans le référentiel.

      La valeur par défaut *n’est pas sélectionnée*.

   * **[!UICONTROL Ne pas conserver les traductions]**

      Si cette option est sélectionnée, les traductions ne sont pas stockées dans le référentiel.

      Si cette option n’est pas sélectionnée, les traductions sont conservées.

      La valeur par défaut *n’est pas sélectionnée*.

* **[!UICONTROL Rendu]** intelligentSélectionnez l’un des

   * `Always show contributions in the original language` (default)
   * `Always show contributions in user preferred language`
   * `Show contributions in user preferred language for only logged-in users`

#### ENABLEMENT {#enablement}

![chlimage_1-457](assets/chlimage_1-457.png)

Les `ENABLEMENT`paramètres sont applicables lorsque le modèle de site de la communauté choisie inclut la fonction [](functions.md#assignments-function)d’affectation, disponible lorsque les fonctionnalités d’activation sont sous licence et [configurées](enablement.md). Le modèle de site de référence qui inclut la fonction des affectations est `Reference Structured Learning Site Template.`

* **[!UICONTROL Responsables d’activation]**

   (obligatoire) Seuls les membres du `Community Enablementmanagers` groupe sont disponibles pour être sélectionnés pour gérer cette communauté d&#39;activation. Les gestionnaires d’activation sont chargés d’affecter des membres aux ressources. Voir aussi [Gestion des utilisateurs et des groupes](users.md)d’utilisateurs.

* **[!UICONTROL ID d’entreprise Marketing Cloud]**

   (Facultatif) ID d’une licence Analytics de pulsation [vidéo](analytics.md#video-heartbeat-analytics) .

Sélectionnez **[!UICONTROL Suivant]**.

### Étape 4 : Créer un site de communautés {#step-create-communities-site}

Si des ajustements sont nécessaires, utilisez le bouton **Précédent** pour les effectuer.

Une fois **Créer** sélectionné et démarré, le processus de création du site ne peut plus être interrompu.

Une fois le site créé :

* La modification de l’URL (nom du noeud) n’est pas prise en charge
* Les modifications futures du modèle de site de la communauté n’affecteront pas le site de la communauté créé.
* La désactivation du modèle de site de la communauté n’affectera pas le site créé.
* Il est possible de modifier la [STRUCTURE](#modify-structure) d&#39;un site communautaire en modifiant ses propriétés

![chlimage_1-458](assets/chlimage_1-458.png)

Une fois le processus terminé, le dossier du nouveau site s’affiche dans la console Sites des communautés, d’où les auteurs peuvent ajouter du contenu de page ou les administrateurs peuvent modifier les propriétés du site.

![chlimage_1-459](assets/chlimage_1-459.png)

Pour modifier un site de la communauté, sélectionnez son dossier de projet pour l’ouvrir :

![siteactions-2](assets/siteactions-2.png)

Lorsque vous passez le curseur de la souris sur un site ou touchez une carte du site, des icônes s’affichent pour permettre de [modifier le site en mode](#authoring-site-content)d’auteur, d’ [ouvrir les propriétés du site en vue de les modifier](#modifying-site-properties), de [publier le site](#publishing-the-site), d’ [exporter le site et de supprimer le site.](#exporting-the-site)[](#deleting-the-site)

## Création de contenu du site {#authoring-site-content}

![chlimage_1-460](assets/chlimage_1-460.png)

Le contenu d’un site peut être créé avec les mêmes outils que tout autre site Web AEM. Pour ouvrir le site à des fins de création, sélectionnez l’ `Open Site` icône qui s’affiche lorsque vous survolez le site avec la souris. Le site s&#39;ouvrira dans un nouvel onglet afin que la console Sites des communautés reste accessible.

![chlimage_1-461](assets/chlimage_1-461.png)

>[!NOTE]
If not familiar with AEM, view the documentation on [basic handling](../../help/sites-authoring/basic-handling.md) and a [quick guide to authoring pages](../../help/sites-authoring/qg-page-authoring.md).

## Modification des propriétés du site {#modifying-site-properties}

![chlimage_1-462](assets/chlimage_1-462.png)

Les propriétés d&#39;un site existant, spécifiées au cours du processus de création du site, peuvent être modifiées en sélectionnant l&#39; `Edit Site`icône qui s&#39;affiche lorsque vous passez la souris sur le site.

`Details of the following properties match the descriptions provided in the` Section Création [](#site-creation) du site.

![chlimage_1-463](assets/chlimage_1-463.png)

### Modification de base {#modify-basic}

Le panneau BASIC permet de modifier les

* Titre du site de la communauté
* Description du site de la communauté

Le nom du site de la communauté ne peut pas être modifié.

Le choix d’un modèle de site communautaire différent n’aurait aucune incidence sur un site communautaire existant, car il n’y a plus de lien entre les modèles et les sites.

La [STRUCTURE](#modify-structure) du site communautaire peut être modifiée.

### Modifier la structure {#modify-structure}

Le panneau STRUCTURE permet de modifier la structure initialement créée à partir du modèle de site de la communauté sélectionnée. Depuis le panneau, il est possible de

* Faire glisser des fonctions [de](functions.md) communauté supplémentaires dans la structure du site
* Sur une instance d’une fonction de communauté dans la structure du site :

   * **`gear icon`**

      modifier les paramètres, y compris le titre d’affichage et le nom d’URL&amp;ast;

      ainsi que les groupes de membres [privilégiés](users.md#privilegedmembersgroups)

   * **`trashcan icon`**

      
supprimer (supprimer) des fonctions de la structure du site

   * **`grid icon`**

      
modifier l’ordre des fonctions tel qu’il s’affiche dans la barre de navigation de niveau supérieur du site ;

>[!NOTE]
Vous pouvez modifier l&#39;ordre de toutes les fonctions de la Structure du site, à l&#39;exception de la fonction en haut. Par conséquent, la page d’accueil du site des communautés ne peut pas être modifiée.

>[!CAUTION]
Bien que le titre d’affichage puisse être modifié sans effets secondaires, il n’est pas recommandé de modifier le nom d’URL d’une fonction de communauté appartenant à un site de la communauté.
Par exemple, renommer l’URL ne déplace pas l’UGC existant, avec pour effet de &quot;perdre&quot; l’UGC.

>[!CAUTION]
La fonction de groupes *ne doit pas* être la *première ou la seule* fonction de la structure du site.
Toute autre fonction, telle que la fonction [de](functions.md#page-function)page, doit être incluse et répertoriée en premier.

#### Exemple : Ajout d’une fonction de catalogue à une structure de site communautaire {#example-adding-a-catalog-function-to-a-community-site-structure}

![chlimage_1-464](assets/chlimage_1-464.png)

### Modifier la conception {#modify-design}

Le panneau DESIGN permet d’appliquer un nouveau thème :

* [Thème des sites de la communauté](#community-site-theme)
* [Valorisation de marque des sites de la communauté](#community-site-branding)
   * Accédez au bas du panneau pour modifier l’image de marque.

### Modifier les paramètres {#modify-settings}

Le panneau PARAMÈTRES permet d’accéder à la plupart des paramètres des sous-panneaux de l’étape 3 de la création d’un site communautaire :

* [Gestion des utilisateurs](#user-management)
* [Balises](#tagging)
* [Modération](#moderation)
* [Rôles des membres](#roles)
* [Analyse](#analytics)
* [Traduction](#translation)

### Modifier la miniature {#modify-thumbnail}

Le panneau MINIATURE permet de télécharger une image pour représenter le site dans la console Sites des communautés.

### Modifier l&#39;activation {#modify-enablement}

Le panneau ENABLEMENT permet d’accéder aux paramètres fournis lors de la création du site communautaire.

Voir la description [ENABLEMENT](#enablement) .

## Publication du site {#publishing-the-site}

Après la création ou la modification d’un site communautaire, il est possible de le publier (activer) en sélectionnant l’ `Publish Site` icône qui apparaît lorsque vous passez la souris sur le site.

![chlimage_1-465](assets/chlimage_1-465.png)

Il y aura une indication une fois le site publié.

![chlimage_1-466](assets/chlimage_1-466.png)

### Publication avec des groupes imbriqués {#publishing-with-nested-groups}

Après avoir publié un site de la communauté, il est nécessaire de publier individuellement chaque sous-communauté (groupe imbriqué) créée à l’aide de la console [](groups.md)Groupes.

## Exportation du site {#exporting-the-site}

![chlimage_1-467](assets/chlimage_1-467.png)

Sélectionnez l’icône d’exportation, lorsque vous passez la souris sur le site, pour créer un package du site de la communauté stocké dans le gestionnaire de [packages](../../help/sites-administering/package-manager.md) et téléchargé.\
Notez que l’UGC n’est pas inclus dans le package du site.

## Suppression du site {#deleting-the-site}

![deleteicon-1](assets/deleteicon-1.png)

Pour supprimer le site de la communauté, sélectionnez l&#39;icône Supprimer le site qui s&#39;affiche lorsque vous passez la souris sur le site dans la console du site Communautés. Cette action supprime tous les éléments associés au site, tels que l’UGC, les groupes d’utilisateurs, les ressources et les enregistrements de base de données.

## Groupes d’utilisateurs de la communauté créés {#created-community-user-groups}

Une fois le nouveau site de la communauté publié, les nouveaux groupes de membres (les groupes d’utilisateurs sont créés dans l’environnement de publication) disposent des autorisations appropriées définies pour divers rôles d’administrateur et de membre.

Le nom créé pour les groupes de membres inclut le nom *du* site donné au site à l’ [étape 1](#step13asitetemplate) (le nom qui apparaît dans l’URL) ainsi qu’un identifiant unique afin d’éviter les conflits avec les sites et les groupes de la communauté ayant le même nom de site pour différentes racines de site de la communauté.

Par exemple, si le nom était &quot;engager&quot; pour un site intitulé &quot;Didacticiel de prise en main&quot;, le groupe d’utilisateurs pour les modérateurs serait :

* Titre : Modérateurs d’engagement de la communauté
* Nom : communauté-*engagement-uid*-modérateurs

Notez que tous les membres affectés à des rôles de modérateurs ou d’administrateurs de groupe lors de la création du site seront affectés au groupe approprié ainsi qu’au groupe de membres. Ces groupes et affectations de membres sont créés lors de la publication du nouveau site.

Pour plus d’informations, voir [Gestion des utilisateurs et des groupes](users.md)d’utilisateurs.

>[!NOTE]
Si vous [autorisez la connexion à Social : Facebook](#user-management) est activé une fois le groupe d’utilisateurs
* community-*&lt;nom-site>*-*&lt;uid>*-members

est créée, le service [cloud](social-login.md#createafacebookcloudservice) Facebook appliqué doit être configuré pour ajouter des utilisateurs à ce groupe.

## Erreur de configuration pour l’authentification {#configure-for-authentication-error}

Par défaut, un site de la communauté redirige vers un exemple de page de connexion lorsque l’utilisateur saisit des informations d’identification erronées et ne parvient pas à se connecter. Cet exemple de connexion ne sera pas présent sur un serveur [de](../../help/sites-administering/production-ready.md)production.

Pour rediriger correctement un site, une fois qu’il a été configuré et poussé vers la publication, procédez comme suit pour obtenir l’échec de l’authentification de la redirection vers le site de la communauté :

* Sur chaque instance de publication AEM
* Première connexion avec droits d’administrateur
* Access the [Web Console](../../help/sites-deploying/configuring-osgi.md)
   * For example, [http://localhost:4503/system/console/configMgr](http://localhost:4503/system/console/configMgr)

* Localiser `Adobe Granite Login Selector Authentication Handler`
* Sélectionnez l’ `pencil`icône pour ouvrir la configuration à modifier.
* Entrez les mappages **[!UICONTROL de page de]** connexion comme suit :

   `/content/sites/<site-name>/path/to/login/page:/content/sites/<site-name>`

   par exemple:

   `/content/sites/engage/en/signin:/content/sites/engage/en`

* Sélectionnez **[!UICONTROL Enregistrer]**

![chlimage_1-468](assets/chlimage_1-468.png)

### Tester la redirection de l&#39;authentification {#test-authentication-redirection}

Sur la même instance de publication AEM configurée avec un mappage de page de connexion pour le site de la communauté :

* Accédez à la page d&#39;accueil du site de la communauté
   * Par exemple, [http://localhost:4503/content/sites/engage/en.html](http://localhost:4503/content/sites/engage/en.html)

* Sélectionner Déconnexion
* Sélectionner Connexion
* Entrez des informations d’identification manifestement incorrectes, telles que le nom d’utilisateur &quot;x&quot; et le mot de passe &quot;x&quot;.
* La page de connexion doit s’afficher avec une erreur de connexion non valide.

![chlimage_1-469](assets/chlimage_1-469.png)

## Accès aux sites de la communauté à partir de la console Sites principaux {#accessing-community-sites-from-main-sites-console}

Dans la console Sites de navigation globale, les sites de la communauté se trouvent dans le `Community Sites` dossier.

Bien qu&#39;il soit possible d&#39;accéder à un site communautaire de cette façon, pour les tâches administratives, le site communautaire doit être accessible à partir de la console Sites communautaires.

![chlimage_1-470](assets/chlimage_1-470.png)

