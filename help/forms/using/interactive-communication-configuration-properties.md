---
title: Propriétés de configuration des communications interactives
seo-title: Propriétés de configuration de la communication interactive
description: Modifier les propriétés de configuration par défaut des communications interactives
seo-description: Modifier les propriétés de configuration par défaut des communications interactives
uuid: 793da9c0-7e8b-464c-b41d-559a72fac9eb
contentOwner: anujkapo
products: SG_EXPERIENCEMANAGER/6.4/FORMS
content-type: reference
topic-tags: interactive-communications
discoiquuid: 1aef2a51-4391-4075-8841-a62ace5606f9
translation-type: tm+mt
source-git-commit: 13d364ec820b48fb8b80da2ffd30faeeb7813a28
workflow-type: tm+mt
source-wordcount: '542'
ht-degree: 70%

---


# Propriétés de configuration des communications interactives {#interactive-communications-configuration-properties}

Modifier les propriétés de configuration par défaut des communications interactives

Les communications interactives incluent les propriétés qui sont configurées automatiquement après l’installation du package du [module complémentaire AEM Forms](/help/forms/using/installing-configuring-aem-forms-osgi.md). Les auteurs de la communication interactive peuvent modifier ces propriétés de configuration par défaut en utilisant la page de **configuration de la console web d’Adobe Experience Manager**.

Ouvrez la page **Configuration de la console Web de Adobe Experience Manager** à l’aide de l’URL suivante :

https://&lt;serveur>:&lt;port>/&lt;contextPath>/system/console/configMgr

Les propriétés de configuration incluent :

* [Configuration de fragments de document](#document-fragments-configuration)
* [Configuration de la création de correspondance](#create-correspondence-configuration)
* [Configuration de canal web du formulaire adaptatif et de la communication interactive](#adaptive-form-and-interactive-communication-web-channel-configuration)
* [Configuration des thèmes de canal web du formulaire adaptatif et de la communication interactive](#adaptive-form-and-interactive-communication-web-channel-theme-configuration)

## Configuration de fragments de document  {#document-fragments-configuration}

Appuyez sur **Configuration des fragments de Document** dans la page **Configuration de la console Web de Adobe Experience Manager** pour vue les propriétés de configuration des fragments de document.

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
   <td>Format d’affichage spécifique aux paramètres régionaux pour les champs, variables et éléments de modèle de données de formulaire disponibles lors de la création d’une communication interactive pour l’impression et les canaux Web.</td> 
   <td> 
    <ul> 
     <li>locale = en_US, de_DE, fr_FR et ja_JP</li> 
     <li>dateFormat = jj-MM-aaaa</li> 
     <li>numberDecimalSeparator = .</li> 
     <li>numberGroupSeparator = ,</li> 
     <li>numberUseGroupSeparator = true</li> 
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

## Configuration de la création de correspondance  {#create-correspondence-configuration}

Appuyez sur **Créer la configuration de correspondance** dans la page **Configuration de la console Web de Adobe Experience Manager** pour vue les propriétés de configuration de l&#39;interface utilisateur de l&#39;agent.

| Propriété | Description | Valeur par défaut | Valeurs acceptables |
|---|---|---|---|
| Afficher le contenu résolu pour modification | Cochez la case pour afficher le contenu résolu (valeurs réelles au lieu d’espaces réservés) lors de la modification du module de texte sur l’interface utilisateur de l’agent. | Non sélectionné | Non applicable |
| Appliquer un filigrane lors de l’aperçu | Cochez la case pour appliquer un filigrane au canal d’impression de la communication interactive en mode Aperçu. | Non sélectionné | Ne s’applique pas |

## Configuration de canal web du formulaire adaptatif et de la communication interactive  {#adaptive-form-and-interactive-communication-web-channel-configuration}

Appuyez sur **Configuration du Canal Web de formulaire adaptatif et de communication interactive** dans la page **Configuration de la console Web de Adobe Experience Manager** pour vue les propriétés de configuration pour le canal Web Adaptive Forms and Interactive Communications. Le tableau suivant décrit les propriétés liées aux communications interactives :

| Propriété | Description | Valeur par défaut | Valeurs acceptables |
|---|---|---|---|
| Afficher l’espace réservé | Cochez la case pour activer l’affichage des espaces réservés pour les champs inclus dans les formulaires adaptatifs et les communications interactives. | Sélectionné | Non applicable |
| Nombre maximal d’entrées de cache | Définissez le nombre maximal de formulaires adaptatifs et de communications interactives pouvant être récupérés à l’aide de la mémoire cache. | 100 | Nombre |
| Rendre le nom de fichier unique | Cochez la case pour attribuer des noms uniques aux fichiers en tant que pièces jointes dans les formulaires adaptatifs et les communications interactives. | Non sélectionné | Ne s’applique pas |

## Configuration des thèmes de canal web du formulaire adaptatif et de la communication interactive  {#adaptive-form-and-interactive-communication-web-channel-theme-configuration}

Appuyez sur **Configuration du thème du Canal Web de formulaire adaptatif et de communication interactive** dans la page **Configuration de la console Web de Adobe Experience Manager** pour vue les propriétés de configuration des thèmes de canal Web de Forms et de communications interactives.

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

