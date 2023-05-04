---
title: Conception de la mise en page
seo-title: Layout Design
description: Détails de conception de la mise en page explique comment créer des mises en page à utiliser pour vos lettres ou communications interactives.
seo-description: Layout Design Details explains how you can create layouts to be used for your letters or Interactive Communications.
uuid: b21af474-07f5-4bfe-af7d-0c322e2452ae
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: correspondence-management, interactive-communications
discoiquuid: 046b1bf9-1ac7-4e2e-ab37-6fe5422dfa20
feature: Correspondence Management
exl-id: 92f90e7f-2869-4201-a927-47de1fc08f5c
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1321'
ht-degree: 19%

---

# Conception de la mise en page {#layout-design}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Les modèles de formulaire XFA ou XDP sont les modèles pour :

* [Lettres](/help/forms/using/create-letter.md)
* [Canal d’impression](/help/forms/using/web-channel-print-channel.md#printchannel) des [communications interactives](/help/forms/using/interactive-communications-overview.md)

* Fragments de disposition

Les XDP sont conçus dans Adobe Forms Designer. Cet article fournit des détails sur la manière de concevoir vos XDP pour créer des correspondances/communications interactives efficaces, notamment où utiliser les champs de formulaire ou les zones cibles et quand utiliser les fragments de disposition.

## Création d’une mise en page pour des lettres ou pour le canal d’impression des communications interactives {#creating-a-layout-for-letters-or-for-interactive-communications-print-channel}

Une mise en page définit l’apparence graphique d’une lettre ou d’un canal d’impression d’une communication interactive. La mise en page peut contenir des champs de formulaire standard tels que &quot;Adresse&quot; et &quot;Numéro de référence&quot;. Elle contient également des sous-formulaires vides indiquant les zones cible. Créez la mise en page dans le concepteur de formulaires et une fois l’application terminée, le spécialiste de l’application la télécharge sur AEM serveur. De là, vous pouvez sélectionner la mise en page lors de la création d’un modèle de correspondance ou d’un canal d’impression d’une communication interactive.

![Concepteur : crée une mise en page](assets/claimsubrogationlayout.png)

Pour créer des mises en page pour les lettres/canal d’impression des communications interactives, procédez comme suit :

1. Analysez la mise en page et déterminez le contenu qui se répétera sur toutes les pages. Il s’agit en général de l’en-tête et du pied de page. Ce contenu est placé sur les gabarits de la mise en page. Le contenu restant va dans le corps des pages de la mise en page. Dans un douilleur de police, le logo et l’adresse de l’entreprise peuvent être ajoutés à l’en-tête et au pied de page du gabarit. Par exemple, l’avis d’annulation utilise la même disposition.
1. Lors de la conception des pages courantes, divisez le contenu des pages en sections. Chaque section est conçue comme un sous-formulaire intégré dans la mise en page ou comme une mise en page de fragment. Si la section contient un tableau, modélisez-la en tant que fragment de mise en page.
1. Une mise en page peut être conçue comme suit :

   1. Faites de chaque section un sous-formulaire distinct contenant tous les éléments de la section.
   1. Faites en sorte que chaque sous-formulaire de section soit enfant du même sous-formulaire parent. La disposition du sous-formulaire parent est définie de manière à ce que l’enchaînement des sections puisse se déplacer vers le bas en cas de fusion de grandes données dans les sections précédentes.
   1. La section Résidence principale peut être réutilisée dans d’autres mises en page. Créez-la en tant que mise en page de fragment.
   1. La section Détails d’intérêt supplémentaires ne contient que deux éléments placés l’un au-dessous de l’autre, elle peut contenir des données volumineuses et est conçue comme une mise en page souple.
   1. Les autres sections contiennent des éléments à des positions spécifiques ; elles sont donc conçues comme des mises en page positionnées.
   1. Ventilez une section dans des sous-formulaires si la section contient des éléments à des positions spécifiques et si ces éléments contiennent de grandes quantités de données. Organisez ensuite les sous-formulaires pour obtenir le comportement souhaité.
   1. Pour la section Résidence principale, ajoutez une zone cible d’espace réservé. Cet espace réservé est lié à la résidence Principal du fragment au moment de la conception de la lettre/communication interactive.
   1. Téléchargez la mise en page (et le fragment, le cas échéant, qui utilise la mise en page) sur le serveur AEM Forms.

## Utilisation d’un schéma {#using-schema}

Vous pouvez utiliser un schéma dans une mise en page ou un fragment de mise en page , mais cela n’est pas obligatoire. Si vous utilisez un schéma, vérifiez les points suivants :

1. La mise en page et tous les fragments de mise en page utilisés dans une lettre/communication interactive utilisent le même schéma que la lettre/communication interactive.
1. Tous les champs à renseigner avec des données sont liés au schéma.

## Création de champs associables {#creating-relatable-fields}

Par défaut, tous les champs sont considérés comme associables à d’autres sources de données. Si votre mise en page contient des champs qui ne sont pas liés à une source de données, nommez le champ avec un suffixe &quot;_int&quot; (interne) ; par exemple, pageCount_int.

Un champ associable doit :

* être un &lt;champ> XFA ou &lt;exclGroup>
* disposer d’une référence de liaison XFA ;
* s’il s’agit d’une &lt;exclgroup>, il doit comporter au moins un champ de bouton radio enfant ; sinon, son type de valeur ne peut pas être déterminé.

Un champ associable doit :

* avoir un nom ;

Un champ associable ne doit pas :

* Inclure un suffixe &quot;_int&quot; dans son nom
* ont une liaison définie sur &quot;none&quot;
* être l’enfant d’un élément &lt;exclGroup>

Tant qu’un champ associable répond aux critères décrits ci-dessus, il peut se trouver à n’importe quel emplacement et dans n’importe quelle profondeur d’imbrication dans la mise en page. Vous pouvez utiliser des champs associables dans les gabarits.

La disposition des champs est plus souple que celle des sous-formulaires de zone cible. toutefois, elles sont liées à un type de valeur unique. Vous pouvez agrandir ou définir un champ sur une largeur et une hauteur fixes, etc. Le résultat du module ou de la règle résolu est placé dans le champ .

## Quand utiliser des sous-formulaires et des champs de texte {#deciding-when-to-use-subforms-and-text-nbsp-fields}

Utilisez un sous-formulaire si vous souhaitez capturer plusieurs contenus de module dans une disposition verticale descendante (plusieurs paragraphes ou images). Votre mise en page doit tenir compte du fait que la hauteur du sous-formulaire varie en fonction de son contenu. Si vous ne pouvez pas être certain que la longueur du contenu associé au sous-formulaire/à la cible ne dépasse jamais l’espace réservé au sous-formulaire dans la mise en page, créez le sous-formulaire en tant qu’enfant dans un conteneur de sous-formulaires avec enchaînement. Ce processus permet de s’assurer que les objets de mise en page situés sous le sous-formulaire sont dirigés vers le bas au fur et à mesure que le sous-formulaire se développe.

Utilisez un champ si vous souhaitez capturer des données de module ou d’élément de dictionnaire de données dans le schéma de votre mise en page (car les champs sont liés à des données) ou pour afficher le contenu d’un module sur un gabarit. N’oubliez pas que le contenu d’une page de gabarit ne présente pas une mise en page souple modulable en fonction du contenu de la page. Assurez-vous donc que le champ d’image est utilisé comme logo de l’en-tête. Ce tableau fournit d’autres critères pour décider quand utiliser un sous-formulaire ou un champ dans une mise en page.

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Utilisez un sous-formulaire lorsque</strong></p> </td> 
   <td><p><strong>Utilisez un champ de texte lorsque</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p>Il contient une combinaison d’éléments, tels que Nom et Prénom.</p> </td> 
   <td><p>Il contient un seul élément, tel qu’un numéro de police.</p> </td> 
  </tr> 
  <tr> 
   <td><p>Il comprend plusieurs paragraphes.</p> </td> 
   <td><p>Le texte est encapsulé et justifié.</p> </td> 
  </tr> 
  <tr> 
   <td><p>Les groupes de données conditionnels, facultatifs et répétitifs sont liés à des sous-formulaires afin de réduire le risque d’erreurs de conception susceptibles de se produire si des scripts sont utilisés pour obtenir les mêmes résultats.</p> </td> 
   <td><p>Des éléments tels que le logo et l’adresse de votre entreprise apparaissent sur toutes les pages d’une lettre/communication interactive. Dans ce cas, créez des champs de formulaire pour ces éléments et placez-les sur le gabarit. Si vous définissez la liaison du champ sur "Aucune liaison de données", les champs "Aucun lien" apparaissent comme des champs associables dans l’éditeur de lettre/communication interactive. Si vous souhaitez associer un type de contenu à ces champs, ils doivent avoir une liaison.</p> <p>Si l’adresse de votre société contient plusieurs lignes de données, utilisez un champ de texte avec l’option "Permettre des lignes multiples" pour représenter l’adresse dans la mise en page.</p> <p>Si le type de données d’un champ de texte est défini sur texte brut, la version en texte brut de la sortie du module est utilisée à la place de la version en texte enrichi (toutes les mises en forme sont ignorées). Pour conserver la mise en forme, définissez le type de données du champ de texte sur texte enrichi.</p> </td> 
  </tr> 
  <tr> 
   <td><p>Enchaînement du texte</p> </td> 
   <td><p>Les champs de texte et d’image sont utilisés dans les pages de gabarit. Les pages de Principal ne peuvent pas utiliser de sous-formulaires comme zones cible.</p> </td> 
  </tr> 
  <tr> 
   <td><p>Les objets sont regroupés et organisés sans lier le sous-formulaire à un élément de données.</p> </td> 
   <td><p> </p> </td> 
  </tr> 
  <tr> 
   <td><p>Le sous-formulaire contient un champ de texte. Le sous-formulaire peut s’agrandir sans écraser d’autres objets en dessous dans la mise en page.</p> </td> 
   <td><p>Vous avez besoin d’un accès facile à ses données dans le post-traitement.</p> </td> 
  </tr> 
 </tbody> 
</table>

## Configuration des éléments répétitifs {#setting-up-repetitive-elements}

Lorsque des éléments tels que le logo et l’adresse de votre organisation apparaissent sur toutes les pages d’une lettre/communication interactive, créez des champs de formulaire pour ces éléments et placez-les sur le gabarit. Utilisez la liaison Nom (Nom du champ) pour ces champs.

## Définition du format de rendu du serveur {#specify-the-server-nbsp-render-format}

Utiliser le format de rendu du serveur de la mise en page dans le formulaire XML dynamique ; dans le cas contraire, les lettres/communications interactives basées sur cette disposition ne peuvent pas s’afficher correctement. Par défaut, le format de rendu du serveur dans Forms Designer est défini sur Formulaire XML dynamique. Pour vous assurer que vous utilisez le format correct :

* Dans Designer, cliquez sur **[!UICONTROL Fichier > Propriétés du formulaire > Par défaut]**, et assurez-vous que le paramètre Rendu/Format du PDF est défini sur Formulaire XML dynamique.
