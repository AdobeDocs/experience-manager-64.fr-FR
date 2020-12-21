---
title: Intégration de l’interface utilisateur de création de correspondance dans votre portail personnalisé
seo-title: Intégration de l’interface utilisateur de création de correspondance dans votre portail personnalisé
description: Découvrez comment intégrer l’interface utilisateur de création de correspondance dans votre portail personnalisé
seo-description: Découvrez comment intégrer l’interface utilisateur de création de correspondance dans votre portail personnalisé
uuid: 4ae9c5fb-bb9d-46d8-be84-455f386ab443
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: correspondence-management
discoiquuid: cb232931-60b7-4956-bc77-10636c19325e
translation-type: tm+mt
source-git-commit: 13d364ec820b48fb8b80da2ffd30faeeb7813a28
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 78%

---


# Intégration de l’interface utilisateur de création de correspondance dans votre portail personnalisé {#integrating-create-correspondence-ui-with-your-custom-portal}

## Présentation {#overview}

Cet article décrit la méthode d’intégration de la solution de création de correspondance dans votre environnement.

## Appel basé sur une URL  {#url-based-invocation}

Il est possible d’appeler l’application de création de correspondance à partir d’un portail personnalisé en préparant une URL selon les paramètres de demande suivants :

* l’identifiant du modèle de lettre (à l’aide du paramètre cmLetterId) ou le nom du modèle de lettre (à l’aide du paramètre cmLetterName) ; 

* l’URL des données XML extraites à partir de la source de données sélectionnée (à l’aide du paramètre cmDataUrl).

Par exemple, le portail personnalisé prépare l’URL en tant que\
`https://[server]:[port]/[contextPath]/aem/forms/createcorrespondence.html?random=[timestamp]&cmLetterId=[letter identifier]&cmDataUrl=[data URL]`, qui peut être la valeur href d’un lien sur le portail.\
Si le nom du modèle de lettre est disponible sur le portail, l’URL peut être\
`https://[server]:[port]/content/cm/createcorrespondence.html?cmLetterName=[letter name]&cmDataUrl=[data URL]`.

>[!NOTE]
>
>Cette manière d’appeler l’application n’est pas sûre, car les paramètres nécessaires sont transmis dans le cadre d’une demande GET et affichés (de façon clairement visible) dans l’URL.

>[!NOTE]
>
>Avant d’appeler l’application de création de correspondance, enregistrez et chargez les données d’appel de l’interface utilisateur de création de correspondance au niveau de l’URL de données requise. Cette opération peut être réalisée à partir du portail personnalisé ou à l’aide d’un autre processus différent d’arrière-plan.

## Appel inséré basé sur les données  {#inline-data-based-invocation}

Un autre moyen (et plus sécurisé) d&#39;appeler l&#39;application de création de correspondance peut consister à simplement accéder à l&#39;URL `https://[server]:[port]/[contextPath]/aem/forms/createcorrespondence.html`, tout en envoyant les paramètres et les données pour appeler l&#39;application de création de correspondance en tant que demande de POST (en les masquant de l&#39;utilisateur final). En outre, vous pouvez désormais transmettre les données XML à l’application de création de correspondance en mode POST (dans le cadre de la même demande à l’aide du paramètre cmData), ce qui n’était pas possible (ou idéal) dans l’approche précédente.

### Paramètres de définition de lettre  {#parameters-for-specifying-letter}

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
   <td>Identificateur de l’instance de lettre.</td> 
  </tr>
  <tr>
   <td>cmLetterName</td> 
   <td>Chaîne</td> 
   <td><p>Identifiant du modèle de lettre. </p> <p>Si plusieurs lettres CM portent le même nom sur un serveur, l’utilisation du paramètre cmLetterName dans l’URL génère une erreur « Plusieurs lettres existent avec le nom ». Dans ce cas, utilisez le paramètre cmLetterId dans l’URL au lieu de cmLetterName.</p> </td> 
  </tr>
  <tr>
   <td>cmLetterId</td> 
   <td>Chaîne</td> 
   <td>Nom du modèle de lettre.</td> 
  </tr>
 </tbody>
</table>

L’ordre des paramètres du tableau indique la préférence de paramètres utilisés pour le chargement de la lettre.

### Paramètres de définition de la source de données XML  {#parameters-for-specifying-the-xml-data-source}

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
   <td>Données XML à partir d’un fichier source utilisant des protocoles de base, tels que cq, ftp, http ou file.<br />  </td> 
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

L’ordre des paramètres du tableau indique la préférence de paramètres utilisés pour le chargement des données XML.

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
   <td>Permet d’ouvrir la lettre en mode aperçu<br /> </td> 
  </tr>
  <tr>
   <td>Aléatoire</td> 
   <td>Horodatage</td> 
   <td>Pour résoudre les problèmes de mise en cache du navigateur.</td> 
  </tr>
 </tbody>
</table>

Si vous utilisez le protocole http ou cq pour cmDataURL, l’URL de http/cq doit être accessible anonymement.
