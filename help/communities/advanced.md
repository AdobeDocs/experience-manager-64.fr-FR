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

---


# Scores et badges avancés {#advanced-scoring-and-badges}

## Présentation {#overview}

La notation avancée permet l&#39;attribution de badges pour identifier les membres comme des experts. La notation avancée affecte des points en fonction de la quantité ** et de la qualité du contenu créé par un membre, tandis que la notation de base affecte des points simplement en fonction de la quantité de contenu créé.

Cette différence est due au moteur de notation utilisé pour calculer les scores. Le moteur de notation de base applique des maths simples. Le moteur de notation avancé est un algorithme adaptatif qui récompense les membres actifs qui contribuent à un contenu pertinent et précieux, déduit par le traitement du langage naturel (NLP) d’une rubrique.

Outre la pertinence du contenu, les algorithmes de notation prennent en compte les activités des membres, telles que le vote et le pourcentage de réponses. Bien que le score de base les inclut quantitativement, le score avancé les utilise algorithmiquement.

Par conséquent, le moteur de notation avancé nécessite suffisamment de données pour que l’analyse soit significative. Le seuil de réussite pour devenir un expert est constamment réévalué à mesure que l’algorithme s’ajuste continuellement au volume et à la qualité du contenu créé. Il existe aussi un concept de *dégradation* des postes plus anciens d&#39;un membre. Si un membre expert cesse de participer à l&#39;objet sur lequel il a acquis le statut d&#39;expert, à un moment déterminé (voir configuration [du moteur de](#configurable-scoring-engine)notation), il pourrait perdre son statut d&#39;expert.

La configuration d’un score avancé est pratiquement identique à celle d’un score de base :

* Les règles de notation et de badge de base et avancées sont [appliquées au contenu](implementing-scoring.md#apply-rules-to-content) de la même manière.
   * Des règles de notation et de badge de base et avancées peuvent être appliquées au même contenu
* [L’activation des badges pour les composants](implementing-scoring.md#enable-badges-for-component) est générique

Les différences dans la configuration des règles de notation et de badge sont les suivantes :

* Moteur de notation avancé configurable
* Règles de notation avancées :
   * `scoringType` défini sur **[!UICONTROL avancé]**
   * Mot de passe requis

* Règles de mise en badge avancées :
   * `badgingType` défini sur **[!UICONTROL avancé]**
   * `badgingLevels` définir le nombre de niveaux d&#39;experts à attribuer
   * Nécessite un `badgingPaths` tableau de badges au lieu des points de mappage de la baie de seuils aux badges

>[!NOTE]
>
>Pour utiliser des fonctionnalités avancées de notation et de badge, installez le package [d’identification des](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq640/social/cq-social-expert-identification-pkg)experts.

## Moteur de score configurable {#configurable-scoring-engine}

Le moteur de notation avancé fournit une configuration OSGi avec des paramètres qui affectent l’algorithme de notation avancé.

![chlimage_1-260](assets/chlimage_1-260.png)

* **[!UICONTROL Pondérations]** Pour une rubrique, spécifiez le verbe qui doit avoir la priorité la plus élevée lors du calcul du score. Une ou plusieurs rubriques peuvent être entrées, mais limitées à **un verbe par rubrique**. Voir [Rubriques et verbes](implementing-scoring.md#topics-and-verbs).

   Saisi comme `topic,verb` avec la virgule d’échappement. Par exemple :

   `/social/forum/hbs/social/forum\,ADD`

   
La valeur par défaut est le verbe ADD pour les composants QnA et de forum.


* **[!UICONTROL Plage de score]**

   La plage des scores avancés est définie par cette valeur (score maximum possible) et par 0 (score minimum possible).

   La valeur par défaut est 100, de sorte que la plage de notation soit comprise entre 0 et 100.


* **[!UICONTROL Intervalle de décomposition d&#39;entité]**

   Ce paramètre représente le nombre d’heures après lesquelles tous les scores d’entité sont décalés. Ceci est nécessaire pour ne plus inclure de contenu ancien dans les scores d’un site communautaire.

   La valeur par défaut est de 2 16 000 heures (~24 ans).


* **[!UICONTROL Note du taux de croissance]**

   Indique le score. entre 0 et plage de notation, au-delà de laquelle la croissance ralentit pour limiter le nombre d&#39;experts.

   La valeur par défaut est 50.

## Règles de score avancées {#advanced-scoring-rules}

Dans le score de base, la quantité nécessaire pour gagner un badge est connue.

Dans le cadre d’un score avancé, la quantité nécessaire est constamment ajustée en fonction de la quantité de données de qualité au sein du système. Le score est calculé en permanence de la même manière qu’une courbe en cloche.

Si un membre a obtenu un badge d&#39;expert sur un sujet qui n&#39;est plus actif, il est possible qu&#39;il perde son badge à cause de la carie au fil du temps.

### ScoringType {#scoringtype}

Une règle d’évaluation est un ensemble de sous-règles d’évaluation, chacune d’elles déclarant la règle `scoringType`.

Pour appeler le moteur de notation avancé, `scoringType`vous devez définir `advanced`.

Voir Sous-règles [de score](implementing-scoring.md#scoring-sub-rules).

![chlimage_1-261](assets/chlimage_1-261.png)

### Stopwords {#stopwords}

Le package d’évaluation avancé installe un dossier de configuration contenant un fichier de mots-clés :

* `/etc/community/scoring/configuration/stopwords`

L’algorithme de notation avancé utilise la liste des mots contenus dans le fichier de mots-clés pour identifier les mots anglais courants qui sont ignorés pendant le traitement du contenu.

On ne s&#39;attend pas à ce que ce fichier soit modifié.

Si le fichier de mots-clés est manquant, le moteur de notation avancé renvoie une erreur.

## Règles de badge avancées {#advanced-badging-rules}

Les propriétés avancées des règles de mise en badge diffèrent des propriétés [de](implementing-scoring.md#badging-rules)base des règles de mise en badge.

Au lieu d’associer des points à une image d’insigne, il suffit d’identifier le nombre d’experts autorisés et l’image d’insigne à attribuer.

![chlimage_1-262](assets/chlimage_1-262.png)

| **Propriété** | **Type** | **Description de la valeur** |
|---------------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| badgingPath | Chaîne[] | (Obligatoire) Chaîne multi-valeurs d’images de badge jusqu’au nombre de niveaux de badge. Les chemins d&#39;image du badge doivent être triés afin que le premier soit attribué au plus haut expert. S&#39;il y a moins de badges que ceux indiqués par badgingLevels, le dernier badge de la baie remplit le reste de la baie. Exemple d’entrée :/etc/community/badging/images/expert-badge/jcr:content/expert.png |
| badgingLevels | Long | (Facultatif) Indique les niveaux d’expertise à attribuer. Par exemple, s’il doit y avoir un expert et un presque expert (deux badges), la valeur doit être définie sur 2. Le badgingLevel doit correspondre au nombre d’images de badge liées à un expert répertoriées pour la propriété badgingPath. La valeur par défaut est 1. |
| badgingType | Chaîne | (Obligatoire) Identifie le moteur de notation comme étant &quot;de base&quot; ou &quot;avancé&quot;. Défini sur &quot;advanced&quot;, sinon la valeur par défaut est &quot;basic&quot;. |
| scoringRules | Chaîne[] | (Facultatif) Chaîne à plusieurs valeurs qui limite la règle de badge aux événements de notation identifiés par la ou les règles de notation répertoriées.Exemple d&#39;entrée :/etc/community/score/rule/relief-commentaires-scoreDefault n&#39;est pas une restriction. |

## Règles et badge inclus {#included-rules-and-badge}

### Badge inclus {#included-badge}

Cette version bêta comprend un badge d’expert basé sur la récompense :

* expert

   `/etc/community/badging/images/expert-badge/jcr:content/expert.png`

![chlimage_1-263](assets/chlimage_1-263.png)

Pour que le badge d&#39;expert apparaisse comme une récompense pour l&#39;activité, deux choses doivent se produire :

* `badges` doit être activé pour la fonctionnalité, telle qu’un forum ou un composant QnA
* les règles avancées de notation et de badge doivent être appliquées à la page (ou à l’ancêtre) sur laquelle le composant est placé.

Consultez les informations de base pour :

* [Activation du badge pour un composant](implementing-scoring.md#enable-badges-for-component)
* [Application de règles](implementing-scoring.md#apply-rules-to-content)

### Règles et sous-règles de score incluses {#included-scoring-rules-and-sub-rules}

La version bêta comprend deux règles de notation avancées pour la fonction [de](functions.md#forum-function) forum (une pour le forum et les composants de commentaires de la fonctionnalité de forum) :

1. /etc/community/score/Rules/relief-commentaires-score

   * `subRules[]` =

      /etc/community/scoring/Rules/sub-Rules/relief-commentaires-rule

      /etc/community/scoring/Rules/sub-Rules/stituts-de-suite-voter-règle-propriétaire

      /etc/community/scoring/Rules/sub-Rules/relief-voter-rule

2. /etc/community/score/Rules/relief-forums-score

   * `subRules[]` =

      /etc/community/score/rule/sub-rule/legacy-forums-rule

      /etc/community/scoring/Rules/sub-Rules/relief-commentaires-rule

      /etc/community/scoring/Rules/sub-Rules/stituts-de-suite-voter-règle-propriétaire

**Remarque:**

* Les deux `rules`et `sub-rules` les noeuds sont de type `cq:Page`
* `subRules` est un attribut de type String[] sur le `jcr:content` noeud de la règle
* `sub-rules` peut être partagée entre différentes règles de notation
* `rules` doit être situé dans un emplacement de référentiel avec une autorisation de lecture pour tout le monde
   * les noms de règle doivent être uniques, quel que soit l’emplacement

### Règles de badge incluses {#included-badging-rules}

Cette version comprend deux règles de mise en badge avancées qui correspondent aux règles [de notation des commentaires et des forums](#included-scoring-rules-and-sub-rules)avancés.

* /etc/community/badging/Rules/relief-comments-badging
* /etc/community/badging/Rules/relief-forums-badging

**Remarque:**

* `rules` les noeuds sont de type `cq:Page`
* `rules`doit être situé dans un emplacement de référentiel avec une autorisation de lecture pour tout le monde
   * les noms de règle doivent être uniques, quel que soit l’emplacement
