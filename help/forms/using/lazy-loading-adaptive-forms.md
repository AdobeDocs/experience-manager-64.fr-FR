---
title: Amélioration des performances des formulaires volumineux avec le chargement différé
seo-title: Improve performance of large forms with lazy loading
description: Le chargement différé améliore considérablement les performances des formulaires adaptatifs volumineux et complexes en retardant l’initialisation et le chargement des fragments de formulaire jusqu’à ce qu’ils soient visibles.
seo-description: Lazy loading significantly improves the performance of large and complex adaptive forms by deferring initialization and loading of form fragments until they are visible.
uuid: 3ead2b82-f895-4a7b-9683-495fcd94fade
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: d570ead9-8f9c-4668-8b23-e8984d9b25e9
feature: Adaptive Forms
exl-id: 92d88888-343c-4edb-9b11-8e876539573a
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1000'
ht-degree: 45%

---

# Amélioration des performances des formulaires volumineux avec le chargement différé  {#improve-performance-of-large-forms-with-lazy-loading}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

## Introduction au chargement différé {#introduction-to-lazy-loading}

Lorsque les formulaires sont volumineux et complexes et qu’ils contiennent des centaines, voire des milliers de champs, le délai de réponse expérimenté par les utilisateurs est long pour le rendu du formulaire au moment de l’exécution. Pour réduire le temps de réponse, les formulaires adaptatifs vous permettent de diviser les formulaires en fragments logiques et de les configurer pour différer l’initialisation ou le chargement des fragments jusqu’à ce que le fragment doive être visible. Il s’agit du chargement différé. En outre, les fragments configurés pour un chargement différé sont déchargés lorsque l’utilisateur accède à d’autres sections du formulaire et ne sont donc plus visibles.

Découvrons d’abord les exigences et les étapes préparatoires avant de configurer le chargement différé.

## Préparation à la configuration du chargement différé {#preparing-to-configure-lazy-loading}

Avant de configurer le chargement différé des fragments dans votre formulaire adaptatif, il est important de définir des stratégies pour créer des fragments, identifier les valeurs utilisées dans des scripts ou référencées dans d’autres fragments et définir des règles pour contrôler la visibilité des champs dans des fragments chargés en différé.

* **Identifier et créer des fragments**
Vous pouvez configurer les fragments de formulaires adaptatifs uniquement pour le chargement différé. Un fragment est un segment autonome qui réside en dehors d’un formulaire adaptatif et peut être réutilisé dans des formulaires. Ainsi, la première étape de création d’un chargement différé consiste à identifier les sections logiques d’un formulaire et à les convertir en fragments. Vous pouvez créer un fragment à partir de zéro ou enregistrer un panneau de formulaire existant comme fragment.

    Pour plus d’informations sur la création de fragments, voir [Fragments de formulaire adaptatif](/help/forms/using/adaptive-form-fragments.md).

* **Identifier et marquer les valeurs globales**
Les transactions Forms utilisent des éléments dynamiques pour capturer les données appropriées depuis les utilisateurs et les traiter afin de simplifier l’expérience de remplissage. Par exemple, votre formulaire contient le champ A dans le fragment X dont la valeur détermine la validité du champ B dans un autre fragment. Dans ce cas, si le fragment X est marqué pour le chargement différé, la valeur du champ A doit être disponible pour valider le champ B même si le fragment X n’est pas chargé. Pour ce faire, vous pouvez marquer le champ A comme étant global, ce qui garantit que sa valeur est disponible pour la validation du champ B lorsque le fragment X n’est pas chargé.

   Pour plus d’informations sur la façon de créer une valeur de champ global, voir [Configuration du chargement différé](/help/forms/using/lazy-loading-adaptive-forms.md#p-configuring-lazy-loading-p).

* **Règles d’écriture pour le contrôle de la visibilité des champs**
Les formulaires incluent certains champs et sections qui ne s’appliquent pas à tous les utilisateurs et dans tous les cas. Les auteurs et les développeurs Forms utilisent la visibilité ou les règles d’affichage/masquage pour contrôler leur visibilité en fonction des entrées de l’utilisateur. Par exemple, le champ Adresse du bureau n’est pas affiché pour les utilisateurs qui choisissent Sans emploi dans le champ État de l’emploi d’un formulaire. Pour plus d’informations sur l’écriture de règles, voir [Utilisation de l’éditeur de règles](/help/forms/using/rule-editor.md).

   Vous pouvez exploiter les règles de visibilité dans les fragments chargés de manière différée de sorte que les champs conditionnels soient affichés uniquement lorsqu’ils sont obligatoires. En outre, marquez le champ conditionnel comme étant global pour vous y référer dans l’expression de visibilité du fragment chargé en différé.

## Configuration du chargement différé {#configuring-lazy-loading}

Pour activer le chargement différé sur un fragment de formulaire adaptatif, procédez comme suit :

1. Ouvrez le formulaire adaptatif en mode création qui contient le fragment que vous souhaitez activer pour le chargement différé.
1. Sélectionnez le fragment de formulaire adaptatif et cliquez sur ![cmppr](assets/cmppr.png).
1. Dans la barre latérale, activez **[!UICONTROL Chargement tardif d’un fragment]** et appuyez sur **Terminé**.

   ![Activer le chargement différé du fragment de formulaire adaptatif](assets/lazy-loading-fragment.png)

   Le fragment est désormais activé pour le chargement différé.

Vous pouvez marquer les valeurs des objets du fragment chargé en différé comme étant globales, de sorte qu’elles puissent être utilisées dans des scripts lorsque le fragment contenant n’est pas chargé. Procédez comme suit :

1. Ouvrez le fragment de formulaire adaptatif en mode création.
1. Appuyez sur le champ dont la valeur est à marquer comme globale, puis appuyez sur ![](assets/cmppr.png).
1. Dans la barre latérale, activez **[!UICONTROL Utiliser la valeur pendant le chargement différé]**.
   ![Champ de chargement différé dans la barre latérale](assets/enable-lazy-loading.png)

   La valeur est maintenant marquée comme globale et sera disponible dans les scripts même lorsque le fragment contenant est déchargé.

## Éléments à prendre en compte et bonnes pratiques pour la configuration du chargement différé {#considerations-and-best-practices-for-configuring-lazy-loading}

Voici certaines restrictions, recommandations et aspects importants à garder à l’esprit lorsque vous travaillez avec le chargement différé :

* Il est recommandé d’utiliser des formulaires adaptatifs basés sur un schéma XSD plutôt que des formulaires adaptatifs basés sur XFA pour configurer le chargement différé sur des formulaires volumineux. Le gain de performances dû à l’implémentation du chargement différé dans les formulaires adaptatifs basés sur XFA est relativement inférieur à celui des formulaires adaptatifs basés sur XSD.
* Ne configurez pas le chargement différé sur les fragments dans une mise en page en grille réactive. Cela peut entraîner une dégradation des performances.
* Il est recommandé de ne pas configurer le chargement différé sur les fragments du premier panneau qui s’affichent lors du chargement du formulaire adaptatif.
* Le chargement différé est pris en charge jusqu’à deux niveaux dans la hiérarchie de fragment.
* Assurez-vous que les champs marqués comme globaux sont uniques dans un formulaire adaptatif.
* Pensez à créer des règles de visibilité pour les fragments qui doivent s’afficher ou être masqués en fonction d’une condition. Par exemple, vous pouvez afficher ou masquer le fragment Conjoint(e) selon la valeur État civil spécifiée par l’utilisateur.
* Les composants des pièces jointes et des conditions générales ne sont pas pris en charge dans les fragments chargés en différé.

### Script des bonnes pratiques pour la configuration du chargement différé {#scripting-best-practices-for-configuring-lazy-loading}

Voici des aspects importants à garder à l’esprit lors du développement des scripts pour les panneaux de chargement différé :

* Assurez-vous que les scripts d’initialisation et de calcul utilisés dans les champs d’un fragment chargé différé sont idempotents par nature. Les scripts idempotents sont ceux qui ont le même effet même après plusieurs exécutions.
* Utilisez la propriété disponible globalement des champs pour rendre la valeur des champs situés dans un panneau de chargement différé disponible pour tous les autres panneaux d’un formulaire.
* Ne transférez pas la valeur de référence d’un champ dans un panneau différé, quel que soit le champ marqué globalement sur les fragments ou non.
* Utilisez la fonction de réinitialisation du panneau pour réinitialiser tout ce qui est visible dans le panneau à l’aide de l’expression de clic suivante.

   guideBridge.resolveNode(guideBridge.getFocus({&quot;focusOption&quot;: &quot;navigablePanel&quot;})).resetData()
