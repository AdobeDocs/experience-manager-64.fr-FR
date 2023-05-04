---
title: Introduction à l’interface utilisateur de création d’une communication interactive
seo-title: An introduction to the various user interface elements you can use to author Interactive Communication
description: Présentation des différents éléments de l’interface utilisateur que vous pouvez utiliser pour créer une communication interactive
seo-description: An introduction to the various user interface elements you can use to author Interactive Communication
uuid: 4e301b9a-76a1-4beb-9d67-dbd0a3bdd2e4
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: interactive-communications
discoiquuid: 565bfb42-6099-49f4-83ba-b1f0c129aab7
feature: Interactive Communication
exl-id: 1537490b-71b3-4ab3-b8d1-d85eac88d857
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1321'
ht-degree: 62%

---

# Introduction à l’interface utilisateur de création d’une communication interactive {#introduction-to-interactive-communication-authoring-ui}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Présentation des différents éléments de l’interface utilisateur que vous pouvez utiliser pour créer une communication interactive

L’interface utilisateur de création d’une [Communication interactive](/help/forms/using/interactive-communications-overview.md) est intuitive et fournit les éléments suivants pour la création de canaux d’impression et web de la communication interactive :

* Editeur de document glisser-déposer WYSIWYGM
* Référentiel intégré des resources : les ressources téléchargées et créées sur le serveur sont disponibles dans l’explorateur des ressources de l’interface de création des communications interactives.

Lorsque vous [créez une communication interactive ou en modifiez une existante](/help/forms/using/create-interactive-communication.md), vous utilisez les éléments suivants de l’interface utilisateur :

* [Barre latérale](#sidebar)
* [Barre d’outils Page](#page-toolbar)

* [Barre d’outils de composants](#component-toolbar)
* Zone de contenu

![Interface utilisateur de création de communication interactive](assets/form-editor.png)

**A.** Barre latérale **B.** Barre d’outils de la page **C.** Zone de contenu

## Barre latérale {#sidebar}

![Barre latérale](assets/sidebar-comps.png)

[Cliquez pour agrandir](assets/sidebar-comps-1.png)

**A.** Explorateur de canaux **B.** Explorateur de contenu **C.** Explorateur de propriétés **D.** Explorateur de ressources **E.** Explorateur de composants **F.** Explorateur des sources de données - Modèle de données **G.** Explorateur des sources de données - Contenu Principal

La barre latérale contient les éléments suivants :

* **Explorateur de canaux**

   Le navigateur Canal vous permet de basculer entre les canaux d’impression et web de la communication interactive. En fonction du canal sélectionné dans l’explorateur de canaux, les navigateurs, tels que Contenu et Composants, affichent les options.

* **Explorateur de contenu**

   Dans l’explorateur de contenu, vous pouvez voir la hiérarchie des objets du document pour le canal sélectionné. L’auteur peut accéder à un composant spécifique en appuyant sur cet élément dans l’arborescence de l’objet de document. L’auteur peut rechercher des objets dans le canal web et les réorganiser à partir de cette arborescence.

* **Explorateur de propriétés**

   Permet de modifier les propriétés d’un composant. Les propriétés affichées varient en fonction du composant. Par exemple, pour afficher les propriétés du conteneur de documents :

   Sélectionnez un composant, puis appuyez sur ![champ-level](assets/field-level.png) > **Conteneur de documents**, puis appuyez sur ![cmppr](assets/cmppr.png).

* **Explorateur de ressources**

   Segmente différents types de contenu, tels que des fragments de mise en page, des images, des documents, des pages et des vidéos. L’auteur peut glisser-déposer des actifs dans la communication interactive.

* **Explorateur de composants**

   Comprend des composants que vous pouvez utiliser pour créer les canaux d’impression et web d’un document. Vous pouvez faire glisser des composants dans la communication interactive afin d’ajouter des éléments, puis configurer les éléments ajoutés conformément aux exigences. Le tableau ci-dessous décrit les composants répertoriés dans l’explorateur de composants pour les canaux d’impression et web :

| **Composant** | **Canal d’impression** | **Canal web** | **Fonctionnalité** |
|---|---|---|---|
| Graphique | ✓ | ✓ | Ajoute un graphique que vous pouvez utiliser dans une communication interactive pour la représentation visuelle des données bidimensionnelles récupérées à partir d’un élément de collecte de modèle de données de formulaire. |
| Fragment de document | ✓ | ✓ | Vous permet d’ajouter un composant réutilisable, du texte, une liste ou une condition à une communication interactive. Le composant réutilisable que vous ajoutez à une communication interactive peut être basé sur modèle de données de formulaire ou sans modèle de données de formulaire. |
| Image | ✓ | ✓ | Vous permet d’insérer une image. |
| Panneau | - | ✓ | Le composant Panneau est un espace réservé permettant de regrouper d’autres composants et contrôle la disposition d’un groupe de composants dans une communication interactive. Un composant de panneau vous permet également de rendre un groupe de composants répétables pour l’utilisateur final, par exemple dans plusieurs entrées requises pour remplir des informations d’identification pédagogiques. Il est également recommandé d’utiliser un panneau pour chaque onglet d’une communication interactive dotée de plusieurs onglets. |
| Tableau | &amp;ast; | ✓ | Ajoute un tableau qui permet de classer les données par lignes et par colonnes. |
| Zone cible | &amp;ast;&amp;ast; | ✓ | Insère une zone cible dans un canal web pour organiser les composants spécifiques au canal web. |
| Texte | - | ✓ | Ajoute du texte au canal web d’une communication interactive. Le texte peut utiliser des objets de modèle de données de formulaire pour rendre le contenu dynamique. |

&amp;ast; Utilisez des fragments de mise en page dans le canal d’impression pour ajouter des tableaux.

&amp;ast;&amp;ast; Dans le canal d’impression, les zones cible sont prédéfinies dans le modèle XDP/impression. Vous ne pouvez pas ajouter de nouvelles zones cibles à l’aide de l’interface utilisateur de création de communication interactive.

* **Explorateur de sources de données**

   L’ explorateur de sources de données affiche les sources de données disponibles dans le modèle de données de formulaire que vous avez sélectionné lors de la création de la communication interactive.

### Points clés de l’utilisation des composants {#key-points-for-working-with-components}

Les points clés lors de l’utilisation des composants de communication interactive sont les suivants :

* Chaque composant est associé à des propriétés qui contrôlent son apparence et ses fonctionnalités. Pour configurer les propriétés d’un composant, appuyez sur celui-ci et sélectionnez ![cmppr](assets/cmppr.png) pour ouvrir les propriétés du composant dans l’explorateur de propriétés.
* Un composant est identifié par son nom d’élément. Lorsque vous cliquez sur ![cmppr](assets/cmppr.png), vous pouvez changer le nom du composant en modifiant la valeur du champ Nom de l’élément dans l’explorateur de propriétés. Le champ Nom de l’élément accepte uniquement les lettres, les chiffres, les tirets (-) et les traits de soulignement (_). Les autres caractères spéciaux ne sont pas autorisés et le nom de l’élément doit commencer par une lettre.
* Vous pouvez modifier la propriété de titre d’un composant de communication interactive en ligne dans l’éditeur sans ouvrir l’explorateur de propriétés tant que le titre est visible sur la communication interactive. Pour ce faire :

   1. Appuyez pour sélectionner un composant qui a une propriété Titre et dont la propriété Masquer le titre est désactivée.
   1. Cliquez sur ![aem_6_3_edit](assets/aem_6_3_edit.png) pour rendre le titre modifiable.
   1. Modifiez le titre et appuyez sur la touche Retour ou appuyez n’importe où en dehors du composant pour enregistrer les modifications. Appuyez sur la touche Échap pour annuler les modifications.

## Barre d’outils de composants {#component-toolbar}

![](do-not-localize/toolbar.png)

Lorsque vous sélectionnez un composant, une barre d’outils s’affiche pour vous permettre de l’utiliser. Vous avez la possibilité de couper, coller, déplacer et spécifier les propriétés des composants. Vous avez le choix entre :

A. **Configurer** : lorsque vous appuyez sur **Configurer**, les propriétés du composant sont visibles dans la barre latérale.

B.**Modifier les règles** : lorsque vous cliquez sur Modifier les règles, l’éditeur de règles apparaît dans lequel vous pouvez modifier et créer des règles pour le composant sélectionné. Dans l’éditeur de règles, vous pouvez également sélectionner d’autres objets de formulaire (composants) et modifier/créer des règles pour ces objets de formulaire.

C.** Copier** : permet de copier un composant et le coller ailleurs dans la communication interactive.

D.**Couper** : permet de déplacer un composant d’un endroit à un autre dans la communication interactive.

E. **Supprimer** : permet de supprimer le composant de la communication interactive.

F. **Insérer le composant** : permet d’insérer un composant au-dessus du composant sélectionné.

G. **Coller** : permet de coller le composant coupé ou copié à l’aide des options décrites ci-dessus.

H. **Groupe** : permet de sélectionner plusieurs composants permettant de couper, copier ou coller plusieurs composants ensemble.

I. **Parent** : permet de sélectionner le parent d’un composant.

J. **Plus**: Fournit d’autres options pour utiliser le composant sélectionné.

* Afficher l’expression SOM (pour les panneaux uniquement)
* Associer des objets dans le panneau (pour les panneaux uniquement)
* Modifier le fragment (pour les fragments uniquement)
* Enregistrement d’un panneau en tant que fragment (pour les panneaux uniquement)
* Ajouter un panneau enfant (pour les panneaux uniquement)
* Barre d’outils Ajouter un panneau (pour les panneaux uniquement)
* Remplacer (pas pour les panneaux)

## Barre d’outils Page {#page-toolbar}

La barre d’outils de la page, située en haut de l’écran, propose des options permettant de prévisualiser la communication interactive et d’en modifier les propriétés. Vous pouvez prévisualiser la communication interactive lors de sa création et apporter des modifications en conséquence. Dans la barre d’outils de la page, vous voyez :

* Activer/désactiver le panneau latéral![ toggle-side-panel](assets/toggle-side-panel.png) : affiche ou masque la barre latérale.
* Informations sur la page ![pageinformationad](assets/pageinformationad.png): vous permet d’afficher les propriétés de la page.
* Émulateur ![règle](assets/ruler.png): vous permet de simuler l’aspect de votre communication interactive pour différentes tailles d’affichage telles que des tablettes et des téléphones.
* Modifier : permet de sélectionner d’autres modes comme : Modifier, Style, Développeur et Conception.

   * Modifier : modifie les propriétés de la communication interactive et de ses composants. Exemple : l’ajout d’un composant, le dépôt d’une image et l’indication des champs obligatoires.
   * Style : Vous permet de mettre en forme l’aspect des composants de votre communication interactive. Par exemple, en mode Style, vous pouvez sélectionner un panneau et définir sa couleur d’arrière-plan.
   * Développeur : permet à un développeur de :

      * Découvrir en quoi consiste la communication interactive.
      * Déboguer en temps réel afin de mieux résoudre les problèmes.
   * Cible : permet d’activer ou de désactiver les composants personnalisés ou les composants prêts à l’emploi qui ne sont pas répertoriés dans la barre latérale.


* Aperçu : permet de prévisualiser la communication interactive avant de le publier.
