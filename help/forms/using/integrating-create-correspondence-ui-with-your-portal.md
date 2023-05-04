---
title: Intégration de l’interface utilisateur de création de correspondance dans votre portail personnalisé
seo-title: Integrating Create Correspondence UI with your custom portal
description: Découvrez comment intégrer l’interface utilisateur de création de correspondance à votre portail personnalisé
seo-description: Learn how to integrate create correspondence UI with your custom portal
uuid: 4ae9c5fb-bb9d-46d8-be84-455f386ab443
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: correspondence-management
discoiquuid: cb232931-60b7-4956-bc77-10636c19325e
feature: Correspondence Management
exl-id: 8b1bbd85-66ba-4e96-917a-d768d84a417f
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '514'
ht-degree: 20%

---

# Intégration de l’interface utilisateur de création de correspondance dans votre portail personnalisé {#integrating-create-correspondence-ui-with-your-custom-portal}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

## Présentation {#overview}

Cet article décrit comment intégrer la solution de création de correspondance à votre environnement.

## Appel basé sur une URL {#url-based-invocation}

Pour appeler l’application de création de correspondance à partir d’un portail personnalisé, préparez l’URL avec les paramètres de requête suivants :

* l’identifiant du modèle de lettre (à l’aide du paramètre cmLetterId) ou le nom du modèle de lettre (à l’aide du paramètre cmLetterName) ;

* l’URL des données XML extraites à partir de la source de données sélectionnée (à l’aide du paramètre cmDataUrl).

Par exemple, le portail personnalisé prépare l’URL sous la forme\
`https://[server]:[port]/[contextPath]/aem/forms/createcorrespondence.html?random=[timestamp]&cmLetterId=[letter identifier]&cmDataUrl=[data URL]`, qui pourrait être le href dʼun lien sur le portail.\
Si le nom du modèle de lettre est à portée de main sur le portail, l’URL peut être\
`https://[server]:[port]/content/cm/createcorrespondence.html?cmLetterName=[letter name]&cmDataUrl=[data URL]`.

>[!NOTE]
>
>L’appel de cette manière n’est pas sécurisé, car les paramètres nécessaires sont transmis en tant que requête de GET, en exposant les mêmes paramètres (clairement visibles) dans l’URL.

>[!NOTE]
>
>Avant d’appeler l’application de création de correspondance, enregistrez et chargez les données pour appeler l’interface utilisateur de création de correspondance à l’adresse URL de données donnée. Cela peut être effectué à partir du portail personnalisé ou par un autre processus d’arrière-plan.

## Appel intégré basé sur les données {#inline-data-based-invocation}

Un autre moyen (plus sécurisé) d’appeler l’application de création de correspondance consiste à simplement accéder à l’URL à l’adresse `https://[server]:[port]/[contextPath]/aem/forms/createcorrespondence.html`, lors de l’envoi des paramètres et des données pour appeler l’application de création de correspondance en tant que demande de POST (en les masquant à l’utilisateur final). Cela signifie également que vous pouvez désormais transmettre les données XML pour l’application de création de correspondance en ligne (dans le cadre de la même requête, à l’aide du paramètre cmData), ce qui n’était pas possible/idéal dans l’approche précédente.

### Paramètres de spécification de lettre {#parameters-for-specifying-letter}

<table> 
 <tbody>
  <tr>
   <td><strong>Nom</strong></td> 
   <td><strong>Type</strong></td> 
   <td><strong>Description</strong></td> 
  </tr>
  <tr>
   <td>cmLetterInstanceId</td> 
   <td>Chaîne</td> 
   <td>Identifiant de l’instance de lettre.</td> 
  </tr>
  <tr>
   <td>cmLetterName</td> 
   <td>Chaîne</td> 
   <td><p>Identifiant du modèle de lettre. </p> <p>Si plusieurs lettres CM portent le même nom sur un serveur, l’utilisation du paramètre cmLetterName dans l’URL renvoie l’erreur "Plusieurs lettres portent le même nom". Dans ce cas, utilisez le paramètre cmLetterId dans l’URL au lieu de cmLetterName.</p> </td> 
  </tr>
  <tr>
   <td>cmLetterId</td> 
   <td>Chaîne</td> 
   <td>Nom du modèle de lettre.</td> 
  </tr>
 </tbody>
</table>

L’ordre des paramètres dans le tableau indique la préférence des paramètres utilisés pour le chargement de la lettre.

### Paramètres de spécification de la source de données XML {#parameters-for-specifying-the-xml-data-source}

<table> 
 <tbody>
  <tr>
   <td><strong>Nom</strong></td> 
   <td><strong>Type</strong></td> 
   <td><strong>Description</strong></td> 
  </tr>
  <tr>
   <td>cmDataUrl<br /> </td> 
   <td>URL</td> 
   <td>Données XML provenant d’un fichier source utilisant des protocoles de base tels que cq, ftp, http ou file.<br /> </td> 
  </tr>
  <tr>
   <td>cmLetterInstanceId</td> 
   <td>Chaîne</td> 
   <td>Utilisation des données XML disponibles dans l’instance de lettre.</td> 
  </tr>
  <tr>
   <td>cmUseTestData</td> 
   <td>Booléen</td> 
   <td>Pour réutiliser les données de test associées au dictionnaire de données.</td> 
  </tr>
 </tbody>
</table>

L’ordre des paramètres dans le tableau indique la préférence des paramètres utilisés pour le chargement des données XML.

### Autres paramètres {#other-parameters}

<table> 
 <tbody>
  <tr>
   <td><strong>Nom</strong></td> 
   <td><strong>Type</strong></td> 
   <td><strong>Description</strong></td> 
  </tr>
  <tr>
   <td>cmPreview<br /> </td> 
   <td>Booléen</td> 
   <td>True pour ouvrir la lettre en mode aperçu<br /> </td> 
  </tr>
  <tr>
   <td>Aléatoire</td> 
   <td>Date et heure</td> 
   <td>Pour résoudre les problèmes de mise en cache du navigateur.</td> 
  </tr>
 </tbody>
</table>

Si vous utilisez le protocole http ou cq pour le paramètre cmDataURL, l’URL correspondante doit pouvoir être accessible de manière anonyme.
