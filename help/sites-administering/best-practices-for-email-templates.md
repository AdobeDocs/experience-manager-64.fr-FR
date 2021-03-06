---
title: Meilleures pratiques des modèles de courrier électronique
description: Découvrez les bonnes pratiques relatives à la conception d’emails, qui génère un modèle de campagne email bien développé dans Adobe Experience Manager.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: best-practices, integration
exl-id: a72c0f77-458f-4ea0-b8ca-59e71fef2c5d
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '1053'
ht-degree: 43%

---

# Meilleures pratiques des modèles de courrier électronique{#best-practices-for-email-templates}

Ce document décrit certaines des meilleures pratiques concernant la conception de courrier électronique, qui aboutissent à la création d’un modèle de campagne par courrier électronique bien développé.

La campagne de démonstration disponible dans AEM observe toutes ces meilleures pratiques. La manière dont les meilleures pratiques sont mises en œuvre dans la campagne de démonstration est décrite pour chaque bonne pratique.

Utilisez ces meilleures pratiques pour créer votre propre newsletter.

>[!NOTE]
>
>Tout le contenu d’une campagne doit être créé sous une `master` page de type `cq/personalization/components/ambitpage`. Par exemple, si vous planifiez une structure de campagne, procédez comme suit :
>
>* `/content/campaigns/teasers/en/campaign-promotion-global`
>
>Assurez-vous qu’il réside sous un gabarit :
>
>* `/content/campaigns/teasers/master/en/campaign-promotion-global`


>[!NOTE]
>
>Lors de la création d’un modèle de courrier électronique pour Adobe Campaign, vous devez inclure la propriété . **acMapping** avec la valeur **mapRecipient** dans le **jcr:content** du modèle, ou vous ne pourrez pas sélectionner le modèle Adobe Campaign dans **Propriétés de la page** d’AEM (le champ est désactivé).

## Composant de modèle/page {#template-page-component}

***/libs/mcm/campaign/components/campaign_newsletterpage***

<table> 
 <tbody> 
  <tr> 
   <td><strong>Bonne pratique</strong></td> 
   <td><strong>Mise en œuvre</strong></td> 
  </tr> 
  <tr> 
   <td><p>Spécifiez le type de document pour garantir un rendu cohérent.</p> <p>Ajouter DOCTYPE au début (HTML ou XHTML)</p> </td> 
   <td><p>Est configurable en modifiant la conception <i>cq:doctype</i> dans<i>"/etc/designs/default/jcr:content/campaign_newsletterpage"</i></p> <p>La valeur par défaut est "XHTML" :</p> <p>&lt;!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "https://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd"&gt;</p> <p>Peut être remplacé par "HTML_5" :</p> <p>&lt;!DOCTYPE HTML&gt;</p> </td> 
  </tr> 
  <tr> 
   <td><p>Spécifiez la définition des caractères pour garantir un rendu correct des caractères spéciaux.</p> <p>Ajoutez la déclaration CHARSET (par exemple, iso-8859-15, UTF-8) à &lt;head&gt;</p> </td> 
   <td><p>Est défini sur UTF-8.</p> <p>&lt;meta http-equiv="content-type" content="text/html; charset=UTF-8"&gt;</p> </td> 
  </tr> 
  <tr> 
   <td><p>Codez toute la structure à l’aide de la fonction &lt;table&gt;élément . Pour des mises en page plus compliquées, vous devez imbriquer les tableaux pour créer des structures complexes.</p> <p>Les emails devraient avoir l’air bien, même sans CSS.</p> </td> 
   <td><p>Les tableaux sont utilisés dans tout le modèle pour structurer le contenu. Actuellement, il est possible d’utiliser un maximum de quatre tableaux imbriqués (1 tableau de base + 3 niveaux d’imbrication)</p> <p>&lt;div&gt; Les balises ne sont utilisées qu’en mode création pour garantir une modification correcte des composants.</p> </td> 
  </tr> 
  <tr> 
   <td>Utilisez les attributs d’élément (cellpadding, valign et width, par exemple) pour définir les dimensions du tableau. Ceci force une structure boîte-modèle.</td> 
   <td><p>Toutes les tables contiennent les attributs nécessaires, tels que <i>border</i>, <i>cellpadding</i>, <i>cellspacing</i> et <i>width</i>.</p> <p>Pour harmoniser le positionnement des éléments dans les tableaux, toutes les cellules du tableau comportent l’attribut <i>valign="top"</i> en cours de définition.</p> </td> 
  </tr> 
  <tr> 
   <td><p>Tenez compte, si possible, de la convivialité des appareils mobiles. Utilisez les requêtes multimédias pour augmenter la taille du texte sur les petits écrans et fournir des zones actives de la taille d’une vignette pour les liens.</p> <p>Rendez un courrier électronique interactif si la conception l’autorise.</p> </td> 
   <td>Dans la mesure où les styles CSS sont utilisés pour illustrer la conception de démonstration, les requêtes multimédias le sont pour proposer une version conviviale pour les appareils mobiles.</td> 
  </tr> 
  <tr> 
   <td>Le code CSS intégré est préférable à l’insertion de toutes les feuilles CSS au début.</td> 
   <td><p>Pour mieux démontrer la structure HTML sous-jacente et utiliser la possibilité de personnaliser la structure de newsletter, seules certaines définitions CSS ont été intégrées.</p> <p>Les styles de base et les variations de modèle ont été extraits dans un bloc de style dans &lt;head&gt; de la page. À l’envoi final de la newsletter, ces définitions CSS doivent être intégrées dans la structure HTML. Un mécanisme d’intégration automatique est prévu, mais n’est actuellement pas disponible.</p> </td> 
  </tr> 
  <tr> 
   <td>Restez simple avec votre CSS. Évitez les déclarations de style composées, les formes courtes de code, les propriétés de mise en page CSS, les sélecteurs complexes et les pseudo-éléments.</td> 
   <td>Dans la mesure où les styles CSS sont utilisés pour illustrer la conception de démonstration, les recommandations CSS sont observées.</td> 
  </tr> 
  <tr> 
   <td>La largeur maximale des emails doit être comprise entre 600 et 800 pixels. Ils auront ainsi un meilleur comportement dans le panneau d’aperçu de la plupart des clients.</td> 
   <td>Le <i>width</i> de la table de contenu est limitée à 600 px dans la conception de démonstration.</td> 
  </tr> 
 </tbody> 
</table>

## Images {#images}

/libs/mcm/campaign/components/image

| **Bonne pratique** | **Mise en œuvre** |
|---|---|
| Ajouter *alt* Attributs aux images | Le *alt* a été défini comme obligatoire pour le composant d’image. |
| Utilisation *jpg* au lieu de *png* format des images | Les images seront toujours diffusées en tant que JPG par le composant d’image. |
| Utilisation `<img>` au lieu des images d’arrière-plan dans un tableau. | Aucune donnée d’image d’arrière-plan n’est utilisée dans les modèles. |
| Ajoutez l’attribut style=&quot;bloc d’affichage&quot; sur les images. Permet d’obtenir un affichage correct dans Gmail. | Toutes les images contiennent par défaut la valeur *style=&quot;bloc d’affichage&quot;* attribut. |

## Texte et liens {#text-and-links}

/libs/mcm/campaign/components/heading, /libs/mcm/campaign/components/textimage

<table> 
 <tbody> 
  <tr> 
   <td><strong>Bonne pratique</strong></td> 
   <td><strong>Mise en œuvre</strong></td> 
  </tr> 
  <tr> 
   <td>Utilisez du code html  plutôt que du style dans CSS (famille de polices).</td> 
   <td>L’éditeur de texte enrichi (par exemple, dans le composant textimage) prend désormais en charge le choix et l’application de familles de polices et de tailles de police aux textes sélectionnés. Ils seront rendus sous la forme de balises.</td> 
  </tr> 
  <tr> 
   <td>Utilisez des polices de base interplateformes, telles que <i>Arial, Verdana, Géorgie</i> et <i>Times New Roman</i>.</td> 
   <td><p>Dépend de la conception de la newsletter.</p> <p>Pour la conception de démonstration, la police "Helvetica" est utilisée, mais revient à la police sans-serif générique, si elle n’est pas présente.</p> </td> 
  </tr> 
 </tbody> 
</table>

## Générique {#generic}

| **Bonne pratique** | **Mise en œuvre** |
|---|---|
| Utilisez le validateur W3C pour corriger le code du HTML. Assurez-vous que toutes les balises ouvertes sont correctement fermées. | Le code a été validé. Pour la documentation transitoire XHTML, seul l’attribut xmlns manquant pour la propriété `<html>` élément est manquant. |
| Ne vous embêtez pas avec JavaScript ou Flash : ces technologies ne sont généralement pas prises en charge par les clients de messagerie. | Ni JavaScript ni Flash ne sont utilisés dans le modèle de newsletter. |
| Ajoutez une version en texte brut pour l’envoi en plusieurs parties. | Un nouveau widget a été intégré aux propriétés de la page pour extraire facilement une version en texte brut du contenu de la page. Ceci peut être utilisé comme point de départ pour la version en texte brut finale. |

## Modèles et exemples de newsletter de campagne {#campaign-newsletter-templates-and-examples}

AEM est fourni avec des modèles et des composants clé en main vous permettant de créer des newsletters de campagne. Vous pouvez utiliser ces modèles et composants pour créer vos newsletters personnalisées.

### Modèles {#templates}

Pour offrir une base solide et élargir la variété de possibilités de flux de contenu, trois types de modèle légèrement différents sont disponibles clé en main. Vous pouvez facilement utiliser ces modèles pour créer une newsletter personnalisée.

Tous ont une **header**, un **pied de page** et un **corps** . Sous la section de corps, chaque modèle diffère en **conception de colonne** (1, 2 ou 3 colonnes).

![chlimage_1-318](assets/chlimage_1-318.png)

### Composants {#components}

[Sept composants sont actuellement disponibles dans les modèles de campagne](/help/sites-authoring/adobe-campaign-components.md). Tous ces composants sont basés sur le langage de balisage **HTL** d’Adobe.

| **Nom du composant** | **Chemin du composant** |
|---|---|
| En-tête | /libs/mcm/campaign/components/heading |
| Image | /libs/mcm/campaign/components/image |
| Texte et personnalisation | /libs/mcm/campaign/components/personalization |
| Textimage | /libs/mcm/campaign/components/textimage |
| Lien | /libs/mcm/campaign/components/reference |
| Modèle d’image Dynamic Media Classic (anciennement Scene7) | /libs/mcm/campaign/s7image |
| Référence ciblée | /libs/mcm/campaign/components/reference |

>[!NOTE]
>
>Ces composants sont optimisés pour le contenu de courrier électronique. En d’autres termes, ils respectent les meilleures pratiques décrites dans ce document. L’utilisation d’autres composants clé en main va généralement à l’encontre de ces règles.

Ces composants sont décrits en détail dans [Composants Adobe Campaign](/help/sites-authoring/adobe-campaign-components.md).
