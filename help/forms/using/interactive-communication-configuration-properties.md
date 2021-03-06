---
title: Propriétés de configuration des communications interactives
seo-title: Interactive Communication configuration properties
description: Modifier les propriétés de configuration par défaut des communications interactives
seo-description: Edit default configuration properties for Interactive Communications
uuid: 793da9c0-7e8b-464c-b41d-559a72fac9eb
contentOwner: anujkapo
products: SG_EXPERIENCEMANAGER/6.4/FORMS
content-type: reference
topic-tags: interactive-communications
discoiquuid: 1aef2a51-4391-4075-8841-a62ace5606f9
feature: Interactive Communication
exl-id: 2caf7242-8588-4fc9-9429-40e24416d6eb
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '531'
ht-degree: 94%

---

# Propriétés de configuration des communications interactives {#interactive-communications-configuration-properties}

Modifier les propriétés de configuration par défaut des communications interactives

Les communications interactives incluent les propriétés qui sont configurées automatiquement après l’installation du package du [module complémentaire AEM Forms](/help/forms/using/installing-configuring-aem-forms-osgi.md). Les auteurs de la communication interactive peuvent modifier ces propriétés de configuration par défaut en utilisant la page de **configuration de la console web d’Adobe Experience Manager**.

Ouvrez la page de **configuration de la console web d’Adobe Experience Manager** à l’aide de l’adresse suivante :

https://&lt;server>:&lt;port>/&lt;contextpath>/system/console/configMgr

Les propriétés de configuration incluent :

* [Configuration de fragments de document](#document-fragments-configuration)
* [Configuration de la création de correspondance](#create-correspondence-configuration)
* [Configuration de canal web du formulaire adaptatif et de la communication interactive](#adaptive-form-and-interactive-communication-web-channel-configuration)
* [Configuration des thèmes de canal web du formulaire adaptatif et de la communication interactive](#adaptive-form-and-interactive-communication-web-channel-theme-configuration)

## Configuration de fragments de document {#document-fragments-configuration}

Appuyer **Configuration des fragments de document** sur le **Configuration de la console web Adobe Experience Manager** pour afficher les propriétés de configuration des fragments de document.

<table> 
 <tbody> 
  <tr> 
   <td>Propriété</td> 
   <td>Description</td> 
   <td>Valeur par défaut</td> 
   <td>Valeurs acceptables</td> 
  </tr> 
  <tr> 
   <td>Data Display Formats</td> 
   <td>Format d’affichage spécifique aux paramètres régionaux pour les champs, variables et éléments de modèle de données de formulaire disponibles lors de la création d’une communication interactive pour les canaux d’impression et web.</td> 
   <td> 
    <ul> 
     <li>Paramètre régional = en_US, de_DE, fr_FR et ja_JP</li> 
     <li>dateFormat = dd-MM-yyyy</li> 
     <li>numberDecimalSeparator = .</li> 
     <li>numberGroupSeparator = ,</li> 
     <li>numberUseGroupSeparator = true</li> 
    </ul> </td> 
   <td><p>—</p> </td> 
  </tr> 
  <tr> 
   <td>Indentation</td> 
   <td>Largeur de l’unité unique de mise en retrait appliquée au texte dans des fragments de document de liste.</td> 
   <td>12,7 mm</td> 
   <td>Nombre</td> 
  </tr> 
  <tr> 
   <td>Roman Numbers Minimum Width</td> 
   <td>Largeur minimale à appliquer à la puce/au champ numérique lors de l’utilisation de chiffres romains dans des fragments de document de liste. </td> 
   <td>12,7 mm</td> 
   <td>Nombre</td> 
  </tr> 
  <tr> 
   <td>Number Minimum Width</td> 
   <td>Largeur minimale à appliquer à la puce/au champ numérique lors de l’utilisation de listes numérotées à l’exception des chiffres romains dans des fragments de document de liste.</td> 
   <td>8,0 mm</td> 
   <td>Nombre</td> 
  </tr> 
 </tbody> 
</table>

## Configuration de la création de correspondance {#create-correspondence-configuration}

Cliquez sur **Configuration de la création de correspondance** sur la page **Configuration de la console web d’Adobe Experience Manager** pour afficher les propriétés de configuration de l’interface utilisateur de l’agent.

| Propriété | Description | Valeur par défaut | Valeurs acceptables |
|---|---|---|---|
| Afficher le contenu résolu pour modification | Cochez la case pour afficher le contenu résolu (valeurs réelles au lieu d’espaces réservés) lors de la modification du module de texte sur l’interface utilisateur de l’agent. | Non sélectionné | Non applicable |
| Appliquer un filigrane lors de l’aperçu | Cochez la case pour appliquer un filigrane au canal d’impression de la communication interactive en mode Aperçu. | Non sélectionné | Non applicable |

## Configuration de canal web du formulaire adaptatif et de la communication interactive {#adaptive-form-and-interactive-communication-web-channel-configuration}

Appuyez sur **Configuration du canal web du formulaire adaptatif et de la communication interactive** sur la page **Configuration de la console web d’Adobe Experience Manager** pour afficher les propriétés de configuration du canal web du formulaire adaptatif et des communications interactives. Le tableau suivant décrit les propriétés liées aux communications interactives :

| Propriété | Description | Valeur par défaut | Valeurs acceptables |
|---|---|---|---|
| Afficher l’espace réservé | Cochez la case pour activer l’affichage des espaces réservés pour les champs inclus dans les formulaires adaptatifs et les communications interactives. | Sélectionné | Non applicable |
| Nombre maximal d’entrées de cache | Définissez le nombre maximal de formulaires adaptatifs et de communications interactives pouvant être récupérés à l’aide de la mémoire cache. | 100 | Nombre |
| Rendre le nom de fichier unique | Cochez la case pour attribuer des noms uniques aux fichiers en tant que pièces jointes dans les formulaires adaptatifs et les communications interactives. | Non sélectionné | Non applicable |

## Configuration des thèmes de canal web du formulaire adaptatif et de la communication interactive {#adaptive-form-and-interactive-communication-web-channel-theme-configuration}

Appuyez sur **Configuration des thèmes du canal web du formulaire adaptatif et de la communication interactive** sur la page **Configuration de la console web d’Adobe Experience Manager** pour afficher les propriétés de configuration des thèmes du canal web du formulaire adaptatif et des communications interactives.

<table> 
 <tbody> 
  <tr> 
   <td>Propriété</td> 
   <td>Description</td> 
   <td>Valeur par défaut</td> 
   <td>Valeurs acceptables</td> 
  </tr> 
  <tr> 
   <td>Nom de la liste de polices</td> 
   <td>Liste des polices pouvant être utilisées lors de la création de formulaires adaptatifs et de communications interactives.</td> 
   <td><p>Georgia</p> <p>Book Antiqua</p> <p>Times New Roman</p> <p>Arial</p> <p>Arial black</p> <p>Impact</p> <p>Palatino Linotype</p> </td> 
   <td>Toutes les polices valides du serveur Adobe</td> 
  </tr> 
 </tbody> 
</table>
