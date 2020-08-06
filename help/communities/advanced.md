---
title: Scores et badges avancés
seo-title: Scores et badges avancés
description: Configuration d’un score avancé
seo-description: Configuration d’un score avancé
uuid: 3854b668-729a-42b8-b7cd-5d5ec1ca8380
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 42fb3c50-8728-4897-ade9-6b839294a10e
translation-type: tm+mt
source-git-commit: ddf92a270835259998aa28f5960abcf55f56d1fc
workflow-type: tm+mt
source-wordcount: '1141'
ht-degree: 1%

---


# Scores et badges avancés {#advanced-scoring-and-badges}

## Présentation {#overview}

La notation avancée permet l&#39;attribution de badges pour identifier les membres comme experts. La notation avancée attribue des points en fonction de la quantité ** et de la qualité du contenu créé par un membre, tandis que la notation de base attribue des points simplement en fonction de la quantité de contenu créé.

Cette différence est due au moteur de notation utilisé pour calculer les scores. Le moteur de score de base applique des maths simples. Le moteur de score avancé est un algorithme adaptatif qui récompense les membres principaux qui contribuent à un contenu pertinent et précieux, déduit par le traitement du langage naturel (NLP) d’une rubrique.

Outre la pertinence du contenu, les algorithmes de notation prennent en compte les activités membres, telles que le vote et le pourcentage de réponses. Bien que le score de base les inclut quantitativement, le score avancé les utilise de manière algorithmique.

Par conséquent, le moteur d’évaluation avancé nécessite suffisamment de données pour que l’analyse ait du sens. Le seuil de réussite pour devenir un expert est constamment réévalué à mesure que l’algorithme s’ajuste continuellement au volume et à la qualité du contenu créé. Il y a aussi un concept de *décomposition* des postes plus anciens d&#39;un membre. Si un membre expert cesse de participer à la matière sur laquelle il a acquis le statut d&#39;expert, à un moment déterminé (voir configuration [du moteur de](#configurable-scoring-engine)notation), il pourrait perdre son statut d&#39;expert.

La configuration d’un score avancé est pratiquement identique à celle d’un score de base :

* Les règles de notation et de badge de base et avancées sont [appliquées de la même manière au contenu](implementing-scoring.md#apply-rules-to-content) .
   * Des règles de notation et de badge de base et avancées peuvent être appliquées au même contenu.
* [L&#39;activation de badges pour les composants](implementing-scoring.md#enable-badges-for-component) est générique

Les différences dans la configuration des règles de notation et de badge sont les suivantes :

* Moteur de notation avancé configurable
* Règles de notation avancées :
   * `scoringType` défini sur **[!UICONTROL avancé]**
   * Nécessite des mots de passe

* Règles de mise en badge avancées :
   * `badgingType` défini sur **[!UICONTROL avancé]**
   * `badgingLevels` définir sur le nombre de niveaux d&#39;experts à attribuer
   * Nécessite un `badgingPaths` tableau de badges plutôt que des points de mappage de la baie de seuils pour les badges

>[!NOTE]
>
>Pour utiliser les capacités avancées de notation et de badge, installez le package [d’identification des](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/social/cq-social-expert-identification-pkg)experts.

## Moteur de score configurable {#configurable-scoring-engine}

Le moteur d’évaluation avancé fournit une configuration OSGi avec des paramètres qui affectent l’algorithme d’évaluation avancé.

![chlimage_1-260](assets/chlimage_1-260.png)

* **[!UICONTROL poids]** de score Pour une rubrique, spécifiez le verbe qui doit recevoir la priorité la plus élevée lors du calcul de la note. Une ou plusieurs rubriques peuvent être entrées, mais limitées à **un verbe par rubrique**. Voir [Rubriques et verbes](implementing-scoring.md#topics-and-verbs).

   Entré sous forme `topic,verb` d’échappement de la virgule. Par exemple :

   `/social/forum/hbs/social/forum\,ADD`

   La valeur par défaut est définie sur le verbe AJOUTER pour les composants QnA et de forum.


* **[!UICONTROL Plage de score]**

   La plage des scores avancés est définie par cette valeur (score maximum possible) et 0 (score le plus bas possible).

   La valeur par défaut est 100, de sorte que la plage de score soit comprise entre 0 et 100.


* **[!UICONTROL Intervalle de décomposition d&#39;entité]**

   Ce paramètre représente le nombre d’heures après lesquelles tous les scores d’entité sont décalés. Ceci est nécessaire pour ne plus inclure de contenu ancien dans les scores d’un site communautaire.

   La valeur par défaut est de 2 16 000 heures (~24 ans).


* **[!UICONTROL Taux de croissance du score]**

   Indique le score. entre 0 et plage de score, au-delà de laquelle la croissance ralentit pour limiter le nombre d&#39;experts.

   La valeur par défaut est 50.

## Règles de score avancées {#advanced-scoring-rules}

Dans le score de base, la quantité nécessaire pour gagner un badge est connue.

Dans le cadre d’un score avancé, la quantité nécessaire est constamment ajustée en fonction de la quantité de données de qualité au sein du système. Le score est calculé en permanence de la même manière qu&#39;une courbe en cloche.

Si un membre a gagné un badge d&#39;expert sur un sujet qui n&#39;est plus principal, il est possible qu&#39;il perde son badge à cause de la dégradation au fil du temps.

### ScoringType {#scoringtype}

Une règle d’évaluation est un ensemble de sous-règles d’évaluation, dont chacune déclare la `scoringType`règle.

Pour appeler le moteur d’évaluation avancé, la valeur `scoringType`doit `advanced`être définie.

Voir Sous-règles [](implementing-scoring.md#scoring-sub-rules)de score.

![chlimage_1-261](assets/chlimage_1-261.png)

### Mots-clés {#stopwords}

Le package d’évaluation avancé installe un dossier de configuration contenant un fichier de mots de passe :

* `/etc/community/scoring/configuration/stopwords`

L’algorithme d’évaluation avancé utilise la liste des mots contenus dans le fichier de mots-clés pour identifier les mots anglais courants qui sont ignorés pendant le traitement du contenu.

On ne s&#39;attend pas à ce que ce fichier soit modifié.

Si le fichier de mots-clés est manquant, le moteur d’évaluation avancé génère une erreur.

## Règles de badge avancées {#advanced-badging-rules}

Les propriétés de règle de badge avancées diffèrent des propriétés [de règle de badge](implementing-scoring.md#badging-rules)de base.

Au lieu d&#39;associer des points à une image de badge, il suffit d&#39;identifier le nombre d&#39;experts autorisés et l&#39;image de badge à attribuer.

![chlimage_1-262](assets/chlimage_1-262.png)

| **Propriété** | **Type** | **Description de la valeur** |
|---------------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| badgingPath | Chaîne[] | (Obligatoire) Chaîne multi-valeurs d’images de badge jusqu’au nombre de badgingLevels. Les chemins d&#39;image du badge doivent être commandés pour que le premier soit attribué au plus haut expert. S&#39;il y a moins de badges qu&#39;indiqué par badgingLevels, le dernier badge de la baie remplit le reste de la baie. Exemple d’entrée : /etc/community/badging/images/expert-badge/jcr:content/expert.png |
| badgingLevels | Long | (Facultatif) Indique les niveaux d’expertise à attribuer. Par exemple, s’il doit y avoir un expert et un quasi expert (deux insignes), la valeur doit être définie sur 2. Le badgingLevel doit correspondre au nombre d’images de badge d’expert répertoriées pour la propriété badgingPath. La valeur par défaut est 1. |
| badgingType | Chaîne | (Obligatoire) Identifie le moteur de score comme étant &quot;de base&quot; ou &quot;avancé&quot;. Défini sur &quot;avancé&quot;, sinon la valeur par défaut est &quot;de base&quot;. |
| scoringRules | Chaîne[] | (Facultatif) Chaîne à plusieurs valeurs pour limiter la règle de badge aux événements de notation identifiés par la ou les règles de score répertoriées.Exemple d&#39;entrée : /etc/community/scoring/rules/relief-comments-scoringLa valeur par défaut n&#39;est pas une restriction. |

## Règles et badge inclus {#included-rules-and-badge}

### Badge inclus {#included-badge}

Cette version bêta comprend un badge d&#39;expert basé sur la récompense :

* expert

   `/etc/community/badging/images/expert-badge/jcr:content/expert.png`

![chlimage_1-263](assets/chlimage_1-263.png)

Pour que l&#39;insigne d&#39;expert puisse apparaître comme une récompense pour l&#39;activité, deux choses doivent se produire :

* `badges` doit être activé pour la fonctionnalité, telle qu’un forum ou un composant QnA.
* les règles avancées de notation et de badge doivent être appliquées à la page (ou à l’ancêtre) sur laquelle le composant est placé.

Consultez les informations de base pour :

* [Activation de la mise en badge pour un composant](implementing-scoring.md#enable-badges-for-component)
* [Application de règles](implementing-scoring.md#apply-rules-to-content)

### Règles et sous-règles de score incluses {#included-scoring-rules-and-sub-rules}

La version bêta comprend deux règles de notation avancées pour la fonction [de](functions.md#forum-function) forum (une pour le forum et les commentaires pour les composants du forum) :

1. /etc/community/scoring/rules/pliants-commentaires-score

   * `subRules[]` =

      /etc/community/scoring/rules/sub-rules/avancés-commentaires-rule

      /etc/community/scoring/rules/sub-rules/avancés-voter-rule-owner

      /etc/community/scoring/rules/sub-rules/avancés-voter-rule

2. /etc/community/scoring/rules/puisque-forums-score

   * `subRules[]` =

      /etc/community/scoring/rules/sub-rules/avancés-forums-rule

      /etc/community/scoring/rules/sub-rules/avancés-commentaires-rule

      /etc/community/scoring/rules/sub-rules/avancés-voter-rule-owner

**Notes:**

* Les deux `rules`et `sub-rules` noeuds sont de type `cq:Page`
* `subRules` est un attribut de type String[] sur le `jcr:content` noeud de la règle.
* `sub-rules` peut être partagée entre différentes règles de notation
* `rules` doit être situé dans un emplacement de référentiel avec une autorisation de lecture pour tout le monde
   * les noms de règle doivent être uniques, quel que soit l’emplacement

### Règles de mise en badge incluses {#included-badging-rules}

Cette version comprend deux règles de mise en badge avancées qui correspondent aux forums [avancés et aux règles](#included-scoring-rules-and-sub-rules)de notation des commentaires.

* /etc/community/badging/rules/relief-commentaires-badging
* /etc/community/badging/rules/avancés-forums-badging

**Notes:**

* `rules` les noeuds sont de type `cq:Page`
* `rules`doit être situé dans un emplacement de référentiel avec une autorisation de lecture pour tout le monde
   * les noms de règle doivent être uniques, quel que soit l’emplacement
