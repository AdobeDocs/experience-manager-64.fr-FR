---
title: Application Sandbox initiale
seo-title: Initial Sandbox Application
description: Créer un modèle, un composant et un script
seo-description: Create template, component, and script
uuid: b0d03376-d8bc-4e98-aea2-a01744c64ccd
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: f74d225e-0245-4d5a-bb93-0ee3f31557aa
exl-id: 3da30cb4-39b2-4495-9e8b-93567b73b644
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '608'
ht-degree: 12%

---

# Application Sandbox initiale {#initial-sandbox-application}

Dans cette section, vous allez créer les éléments suivants :

* Le **[modèle](#createthepagetemplate)** qui sera utilisé pour créer des pages de contenu dans l’exemple de site web
* Le **[composant et script](#create-the-template-s-rendering-component)** qui sera utilisé pour effectuer le rendu des pages du site web

## Création d’un modèle de contenu {#create-the-content-template}

Un modèle définit le contenu par défaut d’une nouvelle page. Les sites web complexes peuvent utiliser plusieurs modèles pour créer différents types de pages. De plus, l’ensemble de modèles peut devenir un plan directeur utilisé pour déployer les modifications apportées à un cluster de serveurs.

Dans le cadre de cet exercice, toutes les pages sont basées sur un modèle simple.

1. Dans le volet d’exploration du CRXDE Lite

   * select `/apps/an-scf-sandbox/templates`
   * **[!UICONTROL Créer > Créer un modèle]**

1. Dans la boîte de dialogue Créer un modèle, entrez les valeurs ci-dessous et cliquez ensuite sur **[!UICONTROL Suivant]** :

   * Libellé: `playpage`
   * Titre: `An SCF Sandbox Play Template`
   * Description: `An SCF Sandbox template for play pages`
   * Type de ressource: `an-scf-sandbox/components/playpage`
   * Classement : &lt;leave as=&quot;&quot; default=&quot;&quot;>

   Le libellé est utilisé pour le nom du noeud.

   Le type de ressource s’affiche sur la page `playpage`Noeud jcr:content de s en tant que propriété `sling:resourceType`. Il identifie le composant (ressource) qui effectue le rendu du contenu lorsqu’il est demandé par un navigateur.

   Dans ce cas, toutes les pages créées à l’aide de la variable `playpage`sont rendus par la fonction `an-scf-sandbox/components/playpage` composant. Par convention, le chemin d’accès au composant est relatif, ce qui permet à Sling de rechercher d’abord la ressource dans la variable `/apps` et, si elle est introuvable, dans la variable `/libs` dossier.

   ![chlimage_1-75](assets/chlimage_1-75.png)

1. Si vous utilisez la fonction copier/coller, assurez-vous que la valeur Type de ressource ne comporte aucun espace de début ou de fin.

   Cliquez sur **[!UICONTROL Suivant]**.

1. &quot;Chemins autorisés&quot; fait référence aux chemins des pages qui utilisent ce modèle, de sorte que le modèle soit répertorié pour la variable **[!UICONTROL Nouvelle page]** boîte de dialogue.

   Pour ajouter un chemin, cliquez sur le bouton plus `+` et type `/content(/.&ast;)?` dans la zone de texte qui s’affiche. Si vous utilisez la fonction copier/coller, assurez-vous qu’il n’existe aucun espace de début ou de fin.

   Remarque : La valeur de la propriété de chemin d’accès autorisée est une *expression régulière.* Les pages de contenu dont le chemin d’accès correspond à l’expression peuvent utiliser le modèle. Dans ce cas, l’expression régulière correspond au chemin de la propriété **/content** et toutes ses sous-pages.

   Lorsqu’un auteur crée une page ci-dessous `/content`, la variable `playpage`Le modèle intitulé &quot;Modèle de page d’un environnement de test SCF&quot; apparaît dans la liste des modèles disponibles à utiliser.

   Une fois la page racine créée à partir du modèle, l’accès au modèle peut être limité à ce site web en modifiant la propriété pour inclure le chemin racine dans l’expression régulière, c’est-à-dire.

   `/content/an-scf-sandbox(/.&ast;)?`

   ![chlimage_1-76](assets/chlimage_1-76.png)

1. Cliquez sur **[!UICONTROL Suivant]**.

   Cliquez sur **[!UICONTROL Suivant]** dans le **[!UICONTROL Parents autorisés]** du panneau.

   Cliquez sur **[!UICONTROL Suivant]** dans le **[!UICONTROL Enfants autorisés]** panneaux.

   Cliquez sur **[!UICONTROL OK]**.

1. Une fois que vous avez cliqué sur OK et que vous avez fini de créer le modèle, des triangles rouges s’affichent dans les coins des valeurs de l’onglet Propriétés pour le nouveau `playpage`modèle. Ces triangles rouges indiquent les modifications qui n’ont pas été enregistrées.

   Cliquez sur **[!UICONTROL Enregistrer tout]** pour enregistrer le nouveau modèle dans le référentiel.

   ![chlimage_1-77](assets/chlimage_1-77.png)

### Création du composant de rendu du modèle {#create-the-template-s-rendering-component}

Créez le *component* qui définit le contenu et effectue le rendu de toutes les pages créées en fonction de la variable [modèle playpage](#createthepagetemplate).

1. Dans CRXDE Lite, cliquez avec le bouton droit de la souris **`/apps/an-scf-sandbox/components`** et cliquez sur **[!UICONTROL Créer > Composant]**.
1. En définissant le nom du noeud (libellé) sur *playpage*, le chemin d’accès au composant est

   `/apps/an-scf-sandbox/components/playpage`

   qui correspond au type de ressource du modèle de page de lecture (éventuellement moins l’initial) **`/apps/`** partie du chemin).

   Dans le **[!UICONTROL Créer un composant]** Dans la boîte de dialogue, saisissez les valeurs de propriété suivantes :

   * Libellé : **playpage**
   * Titre : **Un composant SCF Sandbox Play**
   * Description : **Il s’agit du composant qui effectue le rendu du contenu d’une page Sandbox SCF.**
   * Super Type : *&lt;leave blank=&quot;&quot;>*
   * Groupe:

   ![chlimage_1-78](assets/chlimage_1-78.png)

1. Cliquez sur **[!UICONTROL Suivant]** jusqu’à ce que la variable **[!UICONTROL Enfants autorisés]** du panneau de la boîte de dialogue s’affiche.

   * Cliquez sur **[!UICONTROL OK]**
   * Cliquez sur **[!UICONTROL Enregistrer tout]**

1. Vérifiez que le chemin d’accès au composant et le resourceType du modèle correspondent.

   >[!CAUTION]
   >
   >La correspondance entre le chemin d’accès au composant playpage et la propriété sling:resourceType du modèle playpage est essentielle au bon fonctionnement du site web.

   ![chlimage_1-79](assets/chlimage_1-79.png)
