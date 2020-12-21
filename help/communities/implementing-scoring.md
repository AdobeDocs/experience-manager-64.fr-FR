---
title: Score et badges des communautés
seo-title: Score et badges des communautés
description: Les notes et les badges AEM Communities vous permettent d'identifier et de récompenser les membres de la communauté
seo-description: Les notes et les badges AEM Communities vous permettent d'identifier et de récompenser les membres de la communauté
uuid: ca6f22d6-f25d-4f26-b589-81d1f2c830f9
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: b19b3c24-82a0-468c-a077-9f3edb96afc9
tagskeywords: scoring, badging, badges, gamification
translation-type: tm+mt
source-git-commit: 09f8adac1d5fc4edeca03d6955faddf5ea045405
workflow-type: tm+mt
source-wordcount: '2885'
ht-degree: 3%

---


# Scores et badges des communautés {#communities-scoring-and-badges}

## Présentation {#overview}

La fonction de notation et de badges AEM Communities permet d&#39;identifier et de récompenser les membres de la communauté.

Les principaux aspects de la notation et des badges sont les suivants :

* [Attribuer des ](#assign-and-revoke-badges) badges pour identifier le rôle d&#39;un membre dans la communauté

* [Attribution de base de ](#enable-scoring) badgestes aux membres pour encourager leur participation (quantité de contenu créé)
* [Attribution avancée de ](advanced.md) badgess pour identifier les membres comme experts (qualité du contenu créé)

**** Notez que l’attribution de badges  [n’est pas activée par défaut](implementing-scoring.md#main-pars-text-237875536).

>[!CAUTION]
>
>La structure d’implémentation visible dans le CRXDE Lite peut être modifiée une fois que l’interface utilisateur est disponible.

## Badges {#badges}

Les insignes sont placés sous le nom d&#39;un membre pour indiquer soit son rôle, soit son statut dans la communauté. Les badges peuvent être affichés sous forme d&#39;image ou de nom. Lorsqu’il est affiché sous forme d’image, le nom est inclus en tant que texte de remplacement pour l’accessibilité.

Par défaut, les badges se trouvent dans le référentiel à l’adresse

* /etc/community/badging/images

S&#39;ils sont stockés à un autre emplacement, ils doivent être lus accessibles à tous.

Les insignes sont différenciés en UGC selon qu&#39;ils ont été attribués ou acquis selon les règles. Actuellement, les badges attribués apparaissent sous forme de texte et les badges gagnés apparaissent sous forme d’image.

### Interface utilisateur de gestion des badges {#badge-management-ui}

La console Communautés [Badges](badges.md) permet d&#39;ajouter des badges personnalisés qui peuvent être affichés pour un membre lorsqu&#39;il est gagné (attribué) ou lorsqu&#39;il assume un rôle spécifique dans la communauté (attribué).

### Badges affectés {#assigned-badges}

Un administrateur attribue aux membres de la communauté des badges fondés sur le rôle en fonction de leur rôle dans la communauté.

Les badges attribués (et attribués) sont stockés dans le [SRP](srp.md) sélectionné et ne sont pas directement accessibles. Tant qu’une interface graphique n’est pas disponible, le seul moyen d’attribuer des badges basés sur les rôles consiste à le faire avec du code ou de l’URL. Pour obtenir des instructions sur les URL, voir la section intitulée [Attribuer et révoquer des badges](#assign-and-revoke-badges).

Cette version comprend trois badges basés sur les rôles :

* Modérateur

   `/etc/community/badging/images/moderator/jcr:content/moderator.png`

* Gestionnaire de groupes

   `/etc/community/badging/images/group-manager/jcr:content/group-manager.png`

* Membre privilégié

   `/etc/community/badging/images/privileged-member/jcr:content/privileged-member.png`

![chlimage_1-366](assets/chlimage_1-366.png)

### Badges attribués {#awarded-badges}

Le service de notation accorde aux membres de la communauté des badges récompensés en fonction des règles appliquées à leur activité dans la communauté.

Pour que les badges apparaissent comme une récompense pour l&#39;activité, deux choses doivent se produire :

* Le badge doit être [activé](#enable-badges-for-component) pour le composant de fonction.
* Les règles de score et de badge doivent être [appliquées](#apply-rules-to-content) à la page (ou à l’ancêtre) sur laquelle le composant est placé.

La version comprend trois badges basés sur la récompense :

* Or

   `/etc/community/badging/images/gold-badge/jcr:content/gold.png`

* Argent

   `/etc/community/badging/images/silver-badge/jcr:content/silver.png`

* Bronze

   `/etc/community/badging/images/bronze-badge/jcr:content/bronze.png`

![chlimage_1-367](assets/chlimage_1-367.png)

>[!NOTE]
>
>Les règles de score peuvent être configurées pour affecter des points négatifs aux publications marquées comme inappropriées et affecter ainsi la valeur de score. Cependant, une fois qu’un badge est gagné, il ne sera pas automatiquement supprimé en raison de la réduction du point de notation ou des modifications de la règle de notation.
>
>Les badges attribués peuvent être révoqués de la même manière que les badges attribués. Voir la section [Attribuer et révoquer les badges](#assign-and-revoke-badges). Les améliorations futures comprendront une interface utilisateur pour gérer les badges des membres.

### Badges personnalisés {#custom-badges}

Les badges personnalisés peuvent être installés à l&#39;aide de la console [Badges](badges.md) et être affectés ou spécifiés dans les règles de badge.

Une fois installés à partir de la console Badges, les badges personnalisés sont automatiquement répliqués dans l’environnement de publication.

## Activer le score {#enable-scoring}

Le score n’est pas activé par défaut. Les étapes de base pour la configuration et l&#39;activation de la notation et de l&#39;attribution des badges sont les suivantes :

* Identifier les règles pour les points de rémunération ([règles de notation](#scoring-rules))
* Pour les points cumulés par règle de score, affectez [badges](#badges) ([règles de badge](#badging-rules))

* [Appliquer les règles de notation et de badge à un site communautaire](#apply-rules-to-content)
* [Activation du badge pour les fonctionnalités de la communauté](#enable-badges-for-component)

Consultez la section [Test rapide](#quick-test) pour activer la notation pour un site communautaire à l’aide des règles de notation et de badge par défaut pour les forums et les commentaires.

### Appliquer des règles au contenu {#apply-rules-to-content}

Pour activer la notation et les badges, ajoutez les propriétés `scoringRules` et `badgingRules`à tout noeud de l&#39;arborescence de contenu du site.

Si le site est déjà publié, après avoir appliqué toutes les règles et activé les composants, republiez le site.

Les règles qui s’appliquent à un composant activé par badge sont celles du noeud actif ou de son ancêtre.

Si le noeud est de type `cq:Page` (recommandé), ajoutez les propriétés à son `jcr:content`noeud à l&#39;aide de CRXDE|Lite.

| **Propriété** | **Type** | **Description** |
|---|---|---|
| badgingRules | Chaîne[] | une liste de tableau de [règles de badge](#badging-rules) |
| scoringRules | Chaîne[] | une liste de tableau de [règles de score](#scoring-rules) |

>[!NOTE]
>
>Si une règle d’évaluation ne semble pas avoir d’effet sur l’attribution des badges, assurez-vous que la règle d’évaluation n’a pas été bloquée par la propriété scoringRules de la règle d’évaluation. Consultez la section intitulée [Règles d’insigne](#badging-rules).

### Activer les badges pour le composant {#enable-badges-for-component}

Les règles d’évaluation et de classement ne sont en vigueur que pour les instances de composants qui ont activé la mise en badge en modifiant la configuration du composant en [mode de création](author-communities.md).

Une propriété booléenne, `allowBadges`, active/désactive l&#39;affichage des badges pour une instance de composant. Il est configurable dans la boîte de dialogue de modification des composants [](author-communities.md) pour les composants de forum, de QnA et de commentaires par le biais d&#39;une case à cocher intitulée **Afficher les badges**.

#### Exemple : allowBadges pour l&#39;instance de composant Forum {#example-allowbadges-for-forum-component-instance}

![chlimage_1-368](assets/chlimage_1-368.png)

>[!NOTE]
>
>N’importe quel composant peut être superposé pour afficher les badges à l’aide du code HBS trouvé dans les forums, QnA et les commentaires comme exemple.

## Règles de score {#scoring-rules}

Les règles de score sont la base de la notation pour l’attribution de badges.

Très simplement, chaque règle de score est une liste d’une ou de plusieurs sous-règles. Des règles de score sont appliquées au contenu du site de la communauté afin d’identifier les règles à appliquer lorsque les badges sont activés.

Les règles de score sont héritées, mais pas additifs. Par exemple :

* Si la page2 contient la règle de score2 et sa page1 ancêtre contient la règle de score1
* Une action sur un composant page2 appelle à la fois règle1 et règle2.
* Si les deux règles contiennent des sous-règles applicables pour le même `topic/verb` :

   * Seule la sous-règle de la règle2 affectera le score.
   * Les scores des deux sous-règles ne sont pas additionnés.

Lorsqu’il existe plusieurs règles de score, les scores sont conservés séparément pour chaque règle.

Les règles de score sont des noeuds de type `cq:Page` avec des propriétés sur son `jcr:content`noeud qui spécifient la liste des sous-règles qui le définissent.

Les scores sont stockés dans SRP.

>[!NOTE]
>
>Bonne pratique : nommez de manière unique chaque règle de score.
>
>Les noms des règles de score doivent être globalement uniques ; ils ne devraient pas se terminer par le même nom.
>
>Exemple de ce que *ne pas* faire :\
>/etc/community/scoring/rules/site1/forums-score\
>/etc/community/scoring/rules/site2/forums-score

### Sous-règles de score {#scoring-sub-rules}

Les sous-règles de notation contiennent les propriétés qui détaillent les valeurs de participation à la communauté.

Chaque sous-règle de notation identifie

* Quelles sont les activités suivies ?
* Quelle fonction communautaire spécifique implique ?
* Nombre de points attribués

Par défaut, les points sont attribués au membre qui agit, sauf si la sous-règle spécifie le propriétaire du contenu comme recevant les points ( `forOwner`).

Chaque sous-règle peut être incluse dans une ou plusieurs règles de notation.

Le nom de la sous-règle suit généralement le modèle d’utilisation d’un *sujet, objet* et *verbe*. Par exemple :

* membre-commentaire-créer
* membre-réception-vote

Les sous-règles sont des noeuds de type `cq:Page` avec des propriétés sur son `jcr:content`noeud qui spécifient les [verbes et rubriques](#topics-and-verbs).

<table> 
 <tbody> 
  <tr> 
   <th>Propriété</th> 
   <th>Type</th> 
   <th> Valeur Description</th> 
  </tr> 
  <tr> 
   <td><i><code>VERB</code></i></td> 
   <td>Long</td> 
   <td> 
    <ul> 
     <li>requis ; le verbe correspond à une action de événement</li> 
     <li>il doit y avoir au moins une propriété verbe</li> 
     <li>le verbe doit être saisi en UPPERCASE</li> 
     <li>il peut y avoir plusieurs propriétés de verbes, mais aucun duplicata</li> 
     <li>la valeur est le score à appliquer pour ce événement</li> 
     <li>la valeur peut être positive ou négative</li> 
     <li>une liste de verbes prise en charge dans la version se trouve dans la section <a href="#topics-and-verbs">Rubriques et verbes</a>.</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><code>topics</code></td> 
   <td>Chaîne[]</td> 
   <td> 
    <ul> 
     <li>facultatif ; restreint la sous-règle aux composants de la communauté identifiés par des sujets de événement</li> 
     <li>si spécifié : est une chaîne de plusieurs valeurs de rubriques de événement</li> 
     <li>une liste des rubriques de la version se trouve dans la section <a href="#topics-and-verbs">Rubriques et verbes</a>.</li> 
     <li>par défaut est appliquée à toutes les rubriques associées aux verbes.</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><code>forOwner</code></td> 
   <td>Booléen</td> 
   <td> 
    <ul> 
     <li>facultatif ; n'est pas pertinent lorsque le membre agit sur le contenu qu'il possède</li> 
     <li>si la valeur est true, appliquez un score au propriétaire du contenu concerné</li> 
     <li>si la valeur est false, appliquer un score à l'action du membre</li> 
     <li>false par défaut</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><code>scoringType</code></td> 
   <td>Chaîne</td> 
   <td> 
    <ul> 
     <li>facultatif ; identifie le moteur de notation</li> 
     <li>si "de base", spécifie le moteur de notation en fonction de la quantité 
      <ul> 
       <li>inclus dans la version</li> 
      </ul> </li> 
     <li>si "avancé", indique le moteur de notation en fonction de la qualité et de la quantité 
      <ul> 
       <li>nécessite un <a href="advanced.md">package supplémentaire</a></li> 
      </ul> </li> 
     <li>default is "basic"</li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

### Règles et sous-règles de score incluses {#included-scoring-rules-and-sub-rules}

Cette version comprend deux règles de notation pour la fonction [Forum](functions.md#forum-function) (une pour les composants Forum et Commentaires de la fonction Forum) :

1. /etc/community/score/rules/commentaires-score

   * subRules[] =

      /etc/community/scoring/rules/sub-rules/members-comment-create

      /etc/community/scoring/rules/sub-rules/members-receive-vote

      /etc/community/scoring/rules/sub-rules/members-don-vote

      /etc/community/scoring/rules/sub-rules/members-is-modérated

1. /etc/community/scoring/rules/forums-score

   * subRules[] =

      /etc/community/scoring/rules/sub-rules/membre-forum-create

      /etc/community/scoring/rules/sub-rules/members-receive-vote

      /etc/community/scoring/rules/sub-rules/members-don-vote

      /etc/community/scoring/rules/sub-rules/members-is-modérated

**Remarques:**

* Les noeuds `rules`et `sub-rules` sont de type cq:Page

* `subRules`est un attribut de type [] Stringon the rule&#39;s  `jcr:content` node

* `sub-rules` peut être partagée entre différentes règles de notation
* `rules`doit être situé dans un emplacement de référentiel avec une autorisation de lecture pour tout le monde

   * Les noms de règle doivent être uniques, quel que soit l’emplacement

### Activation de règles de score personnalisées {#activating-custom-scoring-rules}

Toute modification ou tout ajout apporté aux règles de notation ou aux sous-règles apportées dans l’environnement d’auteur doit être installé lors de la publication.

## Règles d’insigne {#badging-rules}

Les règles de mise en badge lient les règles de notation aux badges en spécifiant :

* Quelle règle de score
* Le score nécessaire pour obtenir un badge spécifique

Les règles de badge sont des noeuds de type `cq:Page` avec des propriétés sur son `jcr:content`noeud qui mettent en corrélation les règles de score avec les scores et les badges.

Les règles de badge consistent en une propriété `thresholds`obligatoire qui est une liste ordonnée de scores mappés à des badges. Les scores doivent être triés en valeur croissante. Par exemple :

* `1|/etc/community/badging/images/bronze-badge/jcr:content/bronze.png`

   * Un badge en bronze est décerné pour avoir gagné 1 point

* `60|/etc/community/badging/images/silver-badge/jcr:content/silver.png`

   * Un badge d&#39;argent est attribué lorsque 60 points ont été accumulés

* `80|/etc/community/badging/images/gold-badge/jcr:content/gold.png`

   * Un badge d&#39;or est attribué lorsque 80 points ont été accumulés

Les règles de badge sont associées à des règles de score, qui déterminent comment les points s’accumulent. Voir la section intitulée [Appliquer des règles au contenu](#apply-rules-to-content).

La propriété `scoringRules`d&#39;une règle de badge limite simplement les règles de score qui peuvent être associées à cette règle de badge particulière.

>[!NOTE]
>
>Meilleure pratique : créez des images de badge propres à chaque site AEM.

![chlimage_1-369](assets/chlimage_1-369.png)

<table> 
 <tbody> 
  <tr> 
   <th>Propriété</th> 
   <th>Type</th> 
   <th>Valeur Description</th> 
  </tr> 
  <tr> 
   <td>seuils</td> 
   <td>Chaîne[]</td> 
   <td><em>(obligatoire)</em> Chaîne à plusieurs valeurs du formulaire "numéro|chemin" 
    <ul> 
     <li>nombre = score</li> 
     <li>| = la ligne verticale char (U+007C)</li> 
     <li>chemin = chemin complet vers la ressource image de badge</li> 
    </ul> Les chaînes doivent être triées afin que les nombres augmentent en valeur et qu’aucun espace vide ne s’affiche entre le nombre et le chemin.<br /> Exemple d'entrée :<br /> <code>80|/etc/community/badging/images/gold-badge/jcr:content/gold.png</code></td> 
  </tr> 
  <tr> 
   <td>badgingType</td> 
   <td>Chaîne</td> 
   <td><em>(Facultatif)</em> Identifie le moteur d’évaluation comme étant "de base" ou "avancé". Si vous souhaitez utiliser le moteur de score avancé, voir <a href="advanced.md">Advanced Scoring and Badges</a>. La valeur par défaut est "basic".</td> 
  </tr> 
  <tr> 
   <td> 
    <code>scoringRules </code></td> 
   <td>Chaîne[]</td> 
   <td>(<em>facultatif</em>) Chaîne à plusieurs valeurs pour limiter la règle de badge aux événements de notation identifiés par les règles de notation</td> 
  </tr> 
 </tbody> 
</table>

### Règles de mise en badge incluses {#included-badging-rules}

Cette version comprend deux règles de mise en badge qui correspondent aux [Forums et aux ](#includedscoringrules) règles de score des commentaires.

* /etc/community/badging/rules/comments-badging
* /etc/community/badging/rules/forums-badging

**Remarques:**

* `rules` les noeuds sont de type cq:Page
* `rules`doit être situé dans un emplacement de référentiel avec une autorisation de lecture pour tout le monde

   * Les noms de règle doivent être uniques, quel que soit l’emplacement

### Activation de règles de badge personnalisé {#activating-custom-badging-rules}

Toute modification ou tout ajout apporté aux règles de mise en badge ou aux images effectuées dans l’environnement d’auteur doit être installé lors de la publication.

## Affectation et révocation de badges {#assign-and-revoke-badges}

Des badges peuvent être attribués à des membres à l&#39;aide de la console [members](members.md#badges-tab) ou par programmation à l&#39;aide des commandes cURL.

Les commandes cURL suivantes indiquent ce qui est nécessaire pour une demande HTTP d’attribution et de révocation de badges. Le format de base est le suivant :

cURL -i -X POST -H *header* -u *signature * -F *opération * -F *badge * *membre-profil-url*

*header* = &quot;Accepter:application/json&quot;\
en-tête personnalisé à transmettre au serveur (obligatoire)

*signature* = administrator-id:password\
par exemple : admin:admin

*operation* = &quot;:operation=social:assignBadge&quot; OU &quot;:operation=social:deleteBadge&quot;

*badge* = &quot;badgeContentPath=*badge-image-file*&quot;

*badge-image-file* = l’emplacement du fichier image de badge dans le référentiel.\
par exemple : /etc/community/badging/images/modérator/jcr:content/moderator.png

*Member-profil-url* = point de terminaison du profil du membre lors de la publication\
par exemple : https://&lt;serveur>:&lt;port>/home/users/community/riley/profile.social.json

>[!NOTE]
>
>Le *membre-profil-url*
>
>* Peut faire référence à une instance d’auteur si le service de tunnel [Tunnel ](users.md#tunnel-service) est activé
>* Peut être un nom aléatoire et obscur - voir [Liste de contrôle de sécurité](../../help/sites-administering/security-checklist.md#verify-that-you-are-not-disclosing-personally-identifiable-information-in-the-users-home-path) concernant l&#39;ID autorisé

>



### Exemples: {#examples}

#### Attribuer un badge de modérateur {#assign-a-moderator-badge}

```shell
curl -i -X POST -H "Accept:application/json" -u admin:admin -F ":operation=social:assignBadge" -F "badgeContentPath=/etc/community/badging/images/moderator/jcr:content/moderator.png" /home/users/community/updcs9DndLEI74DB9zsB/profile.social.json
```

#### Révoquer un badge argenté affecté {#revoke-an-assigned-silver-badge}

```shell
curl -i -X POST -H "Accept:application/json" -u admin:admin -F ":operation=social:deleteBadge" -F "badgeContentPath=/etc/community/badging/images/silver/jcr:content/silver.png" /home/users/community/updcs9DndLEI74DB9zsB/profile.social.json
```

>[!NOTE]
>
>L’utilisation de cURL pour attribuer et révoquer des badges fonctionne pour n’importe quelle image de badge, mais lorsqu’elle est affectée à la place de celle acquise, elle est marquée comme des badges attribués et gérée en conséquence.

## Scores et badges pour les composants personnalisés {#scoring-and-badges-for-custom-components}

Il est possible de créer des règles de score et de badge pour les composants personnalisés en associant les rubriques de événement créées pour le composant aux verbes.

## Rubriques et verbes {#topics-and-verbs}

Lorsque les membres interagissent avec les fonctionnalités des communautés, des événements sont envoyés qui peuvent déclencher des écouteurs asynchrones, tels que des notifications et des scores.

L’instance SocialEvent d’un composant enregistre les événements sous la forme `actions`qui se produisent pour un `topic`. SocialEvent inclut une méthode permettant de renvoyer une `verb`valeur associée à l’action. Il existe une relation *n-1* entre `actions`et `verbs`.

Pour les composants de communautés livrés, les tableaux suivants décrivent les `verbs`définies pour chaque `topic`disponible pour l&#39;utilisation dans [sous-règles de notation](#scoring-sub-rules).

>[!NOTE]
>
>Une nouvelle propriété booléenne, `allowBadges`, active/désactive l&#39;affichage des badges pour une instance de composant. Il sera configurable dans les boîtes de dialogue de modification de composant [mises à jour](author-communities.md) via une case à cocher intitulée **Badges d&#39;affichage**.

**[Calendrier](calendar.md)**
ComponentSocialEvent  `topic`= com/adobe/cq/social/calendar

| **Verbe** | **Description** |
|---|---|
| POST | crée un événement de calendrier |
| AJOUTER | commentaires d&#39;un membre sur un événement de calendrier |
| UPDATE | le événement de calendrier ou le commentaire du membre est modifié |
| DELETE | le événement de calendrier ou le commentaire du membre est supprimé |

**[Commentaires](comments.md)**
ComponentSocialEvent  `topic`= com/adobe/cq/social/comment

| **Verbe** | **Description** |
|---|---|
| POST | crée un commentaire |
| AJOUTER | réponse du membre au commentaire |
| METTRE À JOUR | le commentaire du membre est modifié |
| DELETE | le commentaire du membre est supprimé |

**[File Library](file-library.md)**
ComponentSocialEvent  `topic`= com/adobe/cq/social/fileLibrary

| **Verbe** | **Description** |
|---|---|
| POST | crée un dossier |
| ATTAQUE | le membre télécharge un fichier |
| METTRE À JOUR | met à jour un dossier ou un fichier |
| DELETE | supprime un dossier ou un fichier |

**[Forum](forum.md)**
ComponentSocialEvent  `topic`= com/adobe/cq/social/forum

| **Verbe** | **Description** |
|---|---|
| POST | membre crée une rubrique de forum |
| AJOUTER | réponses des membres au sujet du forum |
| METTRE À JOUR | le sujet ou la réponse du forum du membre est modifié |
| DELETE | le sujet ou la réponse du membre du forum est supprimé |

**[Journal](blog-feature.md)**
ComponentSocialEvent  `topic`= com/adobe/cq/social/journal

| **Verbe** | **Description** |
|---|---|
| POST | crée un article de blog |
| AJOUTER | commentaires d&#39;un membre sur un article de blog |
| METTRE À JOUR | article ou commentaire du blog du membre modifié |
| DELETE | article ou commentaire du blog du membre supprimé |

**[QnA](working-with-qna.md)**
ComponentSocialEvent  `topic` = com/adobe/cq/social/qna

| **Verbe** | **Description** |
|---|---|
| POST | crée une question QnA |
| AJOUTER | crée une réponse QnA |
| METTRE À JOUR | Question ou réponse QnA du membre modifiée |
| SELECT | la réponse du membre est sélectionnée |
| DÉSÉLECTIONNER | la réponse du membre est désélectionnée |
| DELETE | QnUne question ou réponse du membre est supprimée |

**[Critiques](reviews.md)**
ComponentSocialEvent  `topic`= com/adobe/cq/social/review

| **Verbe** | **Description** |
|---|---|
| POST | membre crée une révision |
| METTRE À JOUR | révision du membre est modifiée |
| DELETE | la révision du membre est supprimée |

**[Evaluation](rating.md)**
ComponentSocialEvent  `topic`= com/adobe/cq/social/tally/rating

| **Verbe** | **Description** |
|---|---|
| AJOUTE | le contenu du membre a été amélioré |
| SUPPRESSION DE LA COTE | le contenu du membre a été réduit |

**[Vote du](voting.md)**
composantSocialEvent  `topic`= com/adobe/cq/social/tally/vote

| **Verbe** | **Description** |
|---|---|
| AJOUTER VOTE | le contenu du député a été voté |
| SUPPRIMER LE VOTE | le contenu du député a été rejeté, voté |

****
Composants prenant en charge la modérationSocialEvent  `topic`= com/adobe/cq/social/modération

| **Verbe** | **Description** |
|---|---|
| DENY | le contenu du membre est refusé |
| INDICATEUR INAPPROPRIÉ | le contenu du membre est marqué |
| INAPPROPRIÉ | le contenu du membre n&#39;est pas marqué |
| ACCEPTER | le contenu du membre est approuvé par le modérateur |
| CLOSE | le membre ferme les commentaires aux modifications et aux réponses |
| OUVRIR | membre réouvre le commentaire |

### Événements de composants personnalisés {#custom-component-events}

Pour un composant personnalisé, un SocialEvent est appelé pour enregistrer les événements du composant sous la forme `actions`qui se produisent pour un `topic`.

Pour prendre en charge le score, SocialEvent doit remplacer la méthode `getVerb()` afin qu’un `verb`approprié soit renvoyé pour chaque `action`. L&#39;élément `verb` renvoyé pour une action peut être couramment utilisé (tel que `POST`) ou spécialisé pour le composant (tel que `ADD RATING`). Il existe une relation *n-1* entre `actions`et `verbs`.

## Résolution des incidents {#troubleshooting}

### Les badges n&#39;apparaissent pas {#badges-are-not-appearing}

Si des règles de notation et de badge ont été appliquées au contenu du site Web, mais que les badges ne sont attribués à aucune activité, assurez-vous que les badges ont été activés pour l’instance de ce composant.

Voir [Activer les badges pour le composant](#enable-badges-for-component).

### La règle de score n&#39;a aucun effet {#scoring-rule-has-no-effect}

Si des règles de notation et de badge ont été appliquées au contenu du site Web et que des badges sont attribués pour certaines actions, mais pas pour d’autres, vérifiez que la règle de badge n’a pas limité les règles de notation auxquelles elle s’applique.

Voir la propriété `scoringRules`des [Règles d&#39;insigne](#badging-rules).

### Type sensible à la casse {#case-sensitive-typo}

La plupart des propriétés et valeurs, en particulier les verbes, sont sensibles à la casse. Les verbes doivent être en MAJUSCULES lorsqu’ils sont utilisés dans une sous-règle de score.

Si la fonction ne fonctionne pas comme prévu, assurez-vous que les données ont été saisies correctement.

## Test rapide {#quick-test}

Il est possible d’essayer rapidement de marquer et de marquer des points à l’aide du site [Didacticiel de prise en main](getting-started.md) (engager) :

* Accéder au CRXDE Lite sur l’auteur
* Accédez à la page de base :

   * /content/sites/learn/fr/jcr:content

* Ajoutez la propriété badgingRules :

   * **Nom** : `badgingRules`
   * **Type** : `String`
   * Sélectionner **[!UICONTROL Multi]**
   * Sélectionner **[!UICONTROL Ajouter]**
   * Enter `/etc/community/badging/rules/forums-badging`
   * Sélectionner `+`
   * Saisissez `/etc/community/badging/rules/comments-badging`
   * **[!UICONTROL Cliquez sur OK]**

* Ajoutez la propriété scoringRules :

   * **Nom** : `scoringRules`
   * **Type** : `String`
   * Sélectionner **[!UICONTROL Multi]**
   * Sélectionner **[!UICONTROL Ajouter]**
   * Saisissez `/etc/community/scoring/rules/forums-scoring`
   * Sélectionner `+`
   * Saisissez `/etc/community/scoring/rules/comments-scoring`
   * **[!UICONTROL Cliquez sur OK]**

* Sélectionner **[!UICONTROL Enregistrer tout]**

![chlimage_1-370](assets/chlimage_1-370.png)

Ensuite, assurez-vous que les composants du forum et des commentaires permettent l&#39;affichage des badges :

* Utilisation de nouveau du CRXDE Lite
* Accédez au composant de forum

   * `/content/sites/engage/en/forum/jcr:content/content/primary/forum`

* Ajoutez la propriété booléenne allowBadges, si nécessaire, et assurez-vous qu’elle est vraie.

   * **Nom** : `allowBadges`
   * **Type** : `Boolean`
   * **Valeur**: `true`

![chlimage_1-371](assets/chlimage_1-371.png)

Ensuite, [republier](sites-console.md#publishing-the-site) le site communautaire.

Enfin,

* Accédez au composant sur l’instance de publication
* Connectez-vous en tant que membre de la communauté (par exemple : weston.mccall@dodgit.com / mot de passe)
* Publier un nouveau sujet de forum
* La page doit être actualisée pour que le badge s’affiche.

   * Déconnexion et connexion en tant que membre de la communauté différent (par exemple : aaron.mcdonald@mailinator.com / mot de passe)

* Sélectionner le forum

Cela devrait permettre au membre de la communauté d&#39;obtenir un badge en bronze visible avec son billet sur le forum car le premier seuil de la règle de badge de forums est un score de 1.

![bronzebadge](assets/bronzebadge.png)

## Informations supplémentaires {#additional-information}

Pour plus d&#39;informations, consultez la page [Scoring and Badges Essentials](configure-scoring.md) destinée aux développeurs.

Pour plus d’informations sur le moteur de score avancé, voir [Advanced Scoring and Badges](advanced.md).

Le tableau de bord configurable [composant](enabling-leaderboard.md) et [fonction](functions.md#leaderboard-function) simplifie l&#39;affichage des membres et leurs scores sur un site communautaire.
