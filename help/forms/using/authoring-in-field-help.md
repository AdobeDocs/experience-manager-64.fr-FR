---
title: Création d’une aide contextuelle pour les champs de formulaire
seo-title: Authoring in-context help for form fields
description: 'AEM Forms permet d’ajouter une aide contextuelle aux champs et aux panneaux des formulaires adaptatifs sous forme de texte ou de contenu multimédia enrichi tel que des vidéos. '
seo-description: AEM Forms allows you to add in-context help to adaptive form fields and panels, as text or rich media, including videos.
uuid: 07427ddd-9d35-41f6-a807-0e418aade199
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: author
discoiquuid: 893a72c7-d68f-464f-9765-ec2272189e58
feature: Adaptive Forms
exl-id: 0c761c0c-fbe4-4129-8a90-c4ef1127a762
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 100%

---

# Création d’une aide contextuelle pour les champs de formulaire {#authoring-in-context-help-for-form-fields}

## Présentation {#introduction}

Dans certains cas, les utilisateurs finaux qui remplissent un formulaire ne sont pas toujours sûrs des informations qu’ils doivent indiquer dans un champ spécifique. Pour résoudre ce problème, les formulaires adaptatifs prennent en charge l’ajout de texte ou d’une aide contextuelle riche à un champ de formulaire. Cela permet d’améliorer l’expérience de remplissage du formulaire et d’éviter toute ambiguïté pour les utilisateurs finaux.

Cet article décrit comment les auteurs de formulaires peuvent ajouter une aide contextuelle lors de la création de formulaires adaptatifs.

## Ajout d’une aide contextuelle {#add-in-context-help}

Vous pouvez spécifier une aide contextuelle à l’aide des options suivantes dans la section Contenu de l’aide de l’onglet Propriétés de la barre latérale.

* [Description courte](/help/forms/using/authoring-in-field-help.md#p-short-description-p)
* [Description longue](/help/forms/using/authoring-in-field-help.md#p-long-description-p)

![Aide contextuelle pour les champs de formulaire](assets/descriptions.png)

>[!NOTE]
>
>La description longue remplace la description courte. Si vous avez spécifié les deux, seule la description longue s’affiche.

### Description courte {#short-description}

Le champ Description courte permet de fournir des conseils courts et rapides pour le remplissage d’un champ de formulaire. Le texte saisi dans le champ Description courte s’affiche sous forme d’info-bulle lorsque le pointeur de la souris est placé sur le champ.

![Description courte pour l’ajout d’une aide contextuelle pour des champs de formulaire](assets/tooltip.png)

>[!NOTE]
>
>Sélectionnez **Toujours afficher la description courte** pour afficher en permanence le texte de l’aide sous le champ.

![Aide contextuelle courte affichée en permanence sous le champ](assets/short1.png)

### Description longue {#long-description}

Vous pouvez utiliser le champ Description longue pour saisir un texte long ou incorporer du contenu multimédia enrichi, dont des vidéos, pour apporter une aide contextuelle. Par exemple, l’illustration ci-dessous montre comment incorporer une vidéo pour apporter une aide contextuelle.

![Ajout de contenu multimédia enrichi comme aide contextuelle pour les champs de formulaire](assets/long-descriptions.png)

L’ajout d’une description longue affiche une icône **?** en regard du champ. Un clic sur l’icône affiche le contenu ajouté à la section Description longue.

![Exemple d’aide contextuelle sous forme de contenu multimédia enrichi](assets/photoshop.png)

### Aide au niveau d’un panneau {#panel-level-help}

Outre l’aide contextuelle pour les champs de formulaire, vous pouvez spécifier une aide au niveau d’un panneau sous l’onglet Contenu de l’aide du panneau Modifier.

![Ajout d’une aide contextuelle pour un panneau de formulaire](assets/panel-level-help.png)

L’ajout d’une aide pour un panneau affiche une icône **?** en regard de la description du panneau. Un clic sur l’icône affiche le contenu ajouté dans la section Contenu de l’aide du panneau Modifier.

![Exemple d’aide contextuelle au niveau d’un panneau](assets/photoshop-1.png)
