---
title: Différences de caractéristiques entre formulaires HTML5 et formulaires PDF
seo-title: Feature differentiation between HTML5 forms and PDF forms
description: Fonctionnalités prises en charge dans les formulaires et PDF forms HTML5
seo-description: Feature supported in HTML5 forms and PDF forms
uuid: b0a96da5-31d3-4f99-b100-91ad51736ffb
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: 273096d0-b0e1-4519-8af6-11b3414cc172
feature: Mobile Forms
exl-id: 2b82e68c-ec11-417d-a8e2-769da9b35140
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '521'
ht-degree: 37%

---

# Différences de caractéristiques entre formulaires HTML5 et formulaires PDF {#feature-differentiation-between-html-forms-and-pdf-forms}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Le tableau suivant indique les fonctionnalités prises en charge par les formulaires HTML5 et les formulaires PDF :

<table> 
 <tbody>
  <tr>
   <th>Fonctionnalité</th> 
   <th>Formulaires HTML5</th> 
   <th>PDF</th> 
  </tr>
  <tr>
   <td>Codes à barres<br /> </td> 
   <td>Non disponible au niveau de l’interface utilisateur. </td> 
   <td>Pris en charge</td> 
  </tr>
  <tr>
   <td>Champ de signature<br /> </td> 
   <td><strong>Signatures numériques</strong> ne sont pas pris en charge, mais une nouvelle <strong>Signature tactile</strong> est ajouté pour les signatures de type papier. Vous pouvez signer à main levée sur le formulaire à l’aide de la fonction <strong>Signature tactile</strong> champ . La signature est enregistrée sur le formulaire sous forme d’image. Vous pouvez enregistrer les informations de géolocalisation dans la variable <strong>Signature tactile</strong> champ .</td> 
   <td>Champ de signature disponible pour <strong>Signatures numériques</strong>.</td> 
  </tr>
  <tr>
   <td>Fusion des données</td> 
   <td>Pris en charge</td> 
   <td>Pris en charge</td> 
  </tr>
  <tr>
   <td>Images</td> 
   <td>Le schéma d’URI de données est utilisé pour afficher les images. Toutes les versions modernes des navigateurs prennent en charge ce modèle, mais il existe des différences dans la plage des formats d’image pris en charge par chaque navigateur.<br /> </td> 
   <td>Les formats .gif, .png, .jpeg, .bmp et .tiff sont pris en charge.</td> 
  </tr>
  <tr>
   <td>Pagination<br /> </td> 
   <td><p>Un formulaire HTML5 est divisé en panneaux et cases pour lui donner une apparence similaire aux PDF forms. La taille de la page est calculée dynamiquement. Si tout le contenu d’une page d’un formulaire HTML5 est supprimé ou marqué comme masqué, la page vierge est masquée et un espace vide (espace vide) n’est pas affiché entre les pages au-dessus et au-dessous de la page vierge.</p> <p>Si la fusion de données ou les scripts ajoutent du contenu à une page, la longueur de la page s’étend pour s’adapter au contenu nouvellement ajouté. Aucune nouvelle page n’est ajoutée au formulaire pour s’adapter au contenu nouvellement ajouté. </p> <p><strong>Remarque :</strong> lorsque tout le contenu d’une page de formulaire HTML5 est supprimé ou marqué comme masqué, la page vierge (espace blanc) reste visible entre la 1ère et 2e page mais pas entre les autres pages.</p> </td> 
   <td>La pagination des documents PDF dépend du contenu des données fusionnées ou du contenu de l’utilisateur : le nombre de pages est augmenté/réduit en conséquence.</td> 
  </tr>
  <tr>
   <td>En-têtes/pieds de page </td> 
   <td>Pris en charge. <br /> <br /> Les formulaires mobiles HTML5 ne prenant pas en charge les sauts de page, les en-têtes et les pieds de page n’apparaissent qu’une seule fois. Vous pouvez toutefois les configurer dans la mise en page afin qu’elles s’affichent à plusieurs endroits dans l’aperçu des formulaires mobiles.<br /> </td> 
   <td>Pris en charge.</td> 
  </tr>
  <tr>
   <td>Widgets personnalisés</td> 
   <td>Vous pouvez personnaliser des widgets pour améliorer l’expérience utilisateur sur les appareils mobiles.<br /> </td> 
   <td>Tous les widgets sont verrouillés et aucun widget personnalisé ne peut être connecté.<br /> </td> 
  </tr>
  <tr>
   <td>API de script XFA</td> 
   <td>Prend en charge les éléments de scripts XFA les plus fréquemment utilisés. Pour obtenir une liste détaillée des éléments prises en charge, consultez la section <a href="/help/forms/using/scripting-support.md">Prise en charge des scripts</a>.</td> 
   <td>Prend en charge tous les éléments de script XFA.</td> 
  </tr>
  <tr>
   <td>API des scripts Acrobat </td> 
   <td>Les formulaires HTML5 prennent en charge la plupart des API couramment utilisées. Pour plus d’informations, consultez la section <a href="/help/forms/using/scripting-support.md">Prise en charge des scripts</a>.</td> 
   <td>Si le fichier PDF est ouvert dans Acrobat ou Reader, il prend également en charge toutes les API de script fournies par Acrobat.</td> 
  </tr>
  <tr>
   <td>Prise en charge des langues écrites de droite à gauche </td> 
   <td>Pris en charge</td> 
   <td>Pris en charge</td> 
  </tr>
 </tbody>
</table>

Suivez les bonnes pratiques pour activer un modèle de formulaire pour les rendus HTML5 et vous assurer que le comportement et l’aspect des formulaires HTML5 et du PDF XFA sont cohérents. Pour obtenir la liste détaillée des bonnes pratiques, voir [Bonnes pratiques pour concevoir un formulaire HTML5.](/help/forms/using/best-practices-for-html5-forms.md)
