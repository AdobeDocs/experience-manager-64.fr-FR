---
title: Guide rapide relatif à WCAG 2.0
seo-title: Quick Guide to WCAG 2.0
description: Lisez un aperçu rapide des consignes d’accessibilité de WCAG 2.0.
seo-description: Read a quick overview of the WCAG 2.0 accessibility guidelines.
uuid: a5cf463e-89e9-4cc0-9c91-69a1fd3d8ea2
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/MANAGING
topic-tags: managing-accessibility
content-type: reference
discoiquuid: 3cac0e34-7514-48ce-a93b-592bbdbcd252
exl-id: 80edcd53-bc3c-4f61-8dfb-c592e7e51f60
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1708'
ht-degree: 46%

---

# Guide rapide relatif à WCAG 2.0{#quick-guide-to-wcag}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

AEM a été développé afin de maximiser la conformité aux directives d’accessibilité du contenu web :

Le [Consignes d’accessibilité du contenu web version 2.0 (WCAG2)](https://www.w3.org/TR/WCAG/) sont un ensemble de directives reconnues internationalement et développées par la [World Wide Web Consortium (W3C)](https://www.w3.org/) sous leur [Web Accessibility Initiative (WAI)](https://www.w3.org/WAI/).

Le WCAG 2.0 regroupe un ensemble de consignes et de critères de réussite qui ne sont pas associés à une technologie particulière et visant à rendre les contenus web plus accessibles aux personnes en situation de handicap. Elles fournissent aux auteurs, aux concepteurs et aux développeurs de contenu web des conseils à suivre afin de s’assurer que les ressources qu’ils produisent sont aussi accessibles que possible pour autant de personnes que possible, quel que soit le handicap qu’elles peuvent avoir ; par exemple, une déficience visuelle, des troubles de l’audition, des difficultés d’apprentissage ou des restrictions liées à l’âge.

Par exemple, la description d’une image (ou de tout autre contenu non textuel) à l’aide de l’attribut `alt` dans le code HTML avantage considérablement les personnes non voyantes ou malvoyantes. La description textuelle dans l’attribut `alt` peut être convertie en sortie vocale ou transmise aux affichages électroniques en braille actualisables.

En outre, WCAG 2.0 peut présenter des avantages pour d’autres bénéficiaires, y compris les personnes qui peuvent être *handicapées par rapport à la situation*, c’est-à-dire les personnes qui, en raison de circonstances telles que la technologie de navigation, la vitesse de la connexion réseau ou l’environnement de navigation, peuvent rencontrer des obstacles similaires à ceux des personnes handicapées.

En utilisant Adobe Experience Manager, les auteurs de contenu et/ou les propriétaires de sites web peuvent créer du contenu web qui satisfait les critères de réussite des niveaux A et AA pertinents de WCAG 2.0.

Par conséquent, la compréhension des objectifs de WCAG 2.0 et de la structure des consignes représente une part importante dans la compréhension de l’accessibilité web, de même que la compréhension de la façon dont les consignes peuvent vous aider à créer du contenu web accessible.

L’objectif de WCAG 2.0 est de fournir des consignes présentant les caractéristiques suivantes :

* Are **agnostique en technologie :**

   En d’autres termes, des consignes qui peuvent être appliquées à un large éventail de formats de contenu web, et pas seulement à des HTMLS. Ainsi, WCAG 2.0 peut couvrir le contenu généré par ou fourni au format PDF, Flash, JavaScript, ainsi que d’autres technologies web actuelles et futures. Cela vise à corriger une faiblesse reconnue de WCAG 1.0, en ce qu’il était axé sur le HTML au détriment d’autres formats de contenu web.

* Are **testable :**

   Chaque consigne est écrite de manière à pouvoir être testée objectivement pour s’assurer qu’un groupe d’experts en accessibilité conviendrait généralement que la consigne a été respectée. L’un des défis des consignes d’accessibilité est que, alors que certaines peuvent être testées par des moyens techniques, d’autres requièrent un jugement humain afin de vérifier si la consigne a été respectée. WCAG 2.0 a été écrit dans le but de réduire la subjectivité présente dans certaines des consignes et points de contrôle de WCAG 1.0.

* Prise en charge de l’implémentation **hiérarchisée et contextuelle :**

   Comme pour WCAG 1.0, les consignes WCAG 2.0 reçoivent des priorités, en fonction de l’impact probable du manquement à cette consigne sur un groupe particulier d’utilisateurs présentant un handicap. Cela permet aux auteurs de prendre une décision éclairée sur les consignes les plus importantes pour leur situation donnée. En outre, la notion d’ *accessibilité prise en charge* est introduite. Cela permet aux auteurs de prendre des décisions sur la meilleure manière d’utiliser les technologies web qui peuvent ne pas présenter l’accessibilité totale, ou peut exiger des utilisateurs qu’ils disposent de technologies d’assistance et/ou de navigateurs spécifiques, permettant ainsi de tirer profit des fonctions d’accessibilité.

Ces objectifs ont considérablement influencé la structure de WCAG 2.0.

>[!NOTE]
>
>Il n’est pas possible de créer un site web qui traite chaque handicap ou type possible de personne. L’objectif de WCAG 2.0 est d’aider les auteurs de contenu web à créer des sites qui sont, dans la mesure du possible, accessibles dans certaines conditions et dans la limite du raisonnable.

>[!NOTE]
>
>Si vous connaissez WCAG 1.0, vous remarquerez quelques modifications dans WCAG 2.0. Elles concernent la portée, l’organisation et l’objectif.

## Structure {#structure}

WCAG 2.0 présente les concepts de création de contenu web accessible d’une manière progressivement détaillée. Cela peut donner l’impression que WCAG 2.0 est un ensemble très complexe de documents liés, mais le but est de fournir (progressivement) des informations plus détaillées à mesure que les auteurs en ont besoin, plutôt que de fournir l’ensemble dans un document très volumineux.

WCAG 2.0 est constitué de quatre principes clés de conception accessible. Ces éléments sont les suivants :

1. **Perceptible**: un utilisateur peut-il sentir le contenu web en question ?
1. **Opérable**: un utilisateur peut-il naviguer, saisir des données ou interagir autrement avec le contenu web ?
1. **Compréhensible**: un utilisateur peut-il traiter et comprendre le contenu web qui lui est présenté ?
1. **Robuste**: le contenu web est-il disponible de la manière prévue dans un large éventail d’environnements de navigation, y compris les environnements de navigation hérités et émergents ?

Ces principes sont parfois évoqués par l&#39;acronyme POUR.

* Chaque **Principe** se compose d’un ou de plusieurs **directives**.

   * Les instructions sont rédigées en tant qu’instructions, qui sont soit positives (faites ceci...), soit négatives (ne faites pas cela...).
   * Les directives sont numérotées 1.1 à 4.1, où le premier numéro correspond au principe parent.

* Chaque ligne guide est composée d’une ou de plusieurs **critères de réussite**.

   * Les critères de réussite sont écrits sous la forme d’instructions, qui sont `True` ou `False` pour n’importe quelle page web donnée.
   * Les critères de réussite peuvent inclure des choix ou des exceptions ; dans les situations où les critères de réussite ne doivent pas être remplis.
   * Les critères de réussite sont numérotés selon la ligne directrice et le principe parents, de 1.1.1 à 4.1.1. Ils ont également un nom court résumant l’intention du critère, à titre de référence plus facile. Par exemple, le critère de réussite 1.1.1 est une alternative non textuelle.
   * Les critères de réussite incluent une liste de **techniques** associées (décrites plus en détail ci-dessous).

## Ressources annexes {#supporting-resources}

Outre les composants fondamentaux de WCAG 2.0 qui sont les principes, consignes et critères de réussite, il existe plusieurs documents annexes. Certains d’entre eux contiennent des conseils spécifiques sur la façon de respecter ces consignes. D’autres sont des références plus générales destinées à aider les programmateurs web, les concepteurs et les développeurs, quelles que soient leurs capacités, à comprendre et à utiliser WCAG 2.0 aussi efficacement que possible.

WCAG 2.0 est un document stable qui ne changera pas. Toutefois, la plupart de ces ressources annexes sont des documents dynamiques ; elles changeront et se développeront au fil du temps, à mesure que de nouvelles technologies et de nouveaux exemples seront disponibles sur la façon de parvenir à l’accessibilité web.

### Ressources WCAG 2.0 {#wcag-resources}

* [Présentation de tous les documents relatifs à WCAG 2.0](https://www.w3.org/WAI/intro/wcag.php);
* [Explication de la relation entre les différents composants](https://www.w3.org/WAI/intro/wcag20);
* [Questions fréquemment posées concernant WCAG 2.0](https://www.w3.org/WAI/WCAG20/wcag2faq.html);

### Techniques relatives à WCAG 2.0 {#techniques-for-wcag}

Les techniques relatives à WCAG 2.0 sont disponibles sur la page [Techniques relatives à WCAG 2.0](https://www.w3.org/TR/WCAG20-TECHS/).

Les **techniques** forment le niveau sous les critères de réussite dans la hiérarchie de WCAG 2.0. Elles sont classées par WAI comme étant informatives, et non normatives. En d’autres termes, une technique spécifique ne doit pas nécessairement être suivie pour qu’une ressource soit conforme à WCAG 2.0.

Étant donné que les techniques sont beaucoup plus spécifiques que les critères de réussite, elles se rapportent généralement à une technologie ou à un type de contenu spécifique (par exemple, HTML ou vidéo) ou à une situation (par exemple, application de commerce électronique ou d’apprentissage en ligne). Vous pouvez considérer les techniques comme des exemples éprouvés de la manière dont des consignes spécifiques et des critères de réussite peuvent être satisfaits, afin qu’elles soient utiles aux auteurs et aux développeurs travaillant dans des contextes spécifiques.

Les techniques sont accessibles :

* par collection (les techniques peuvent être générales ou associées à une technologie ou un format spécifique, comme HTML, CSS ou des scripts côté client) ;
* Des critères de réussite associés. Les techniques peuvent s’appliquer à plusieurs critères de réussite.

Chaque technique possède un numéro unique, qui se rapporte à sa collection. Par exemple, l’une des techniques ARIA est *Technique ARIA2 : Identification des champs requis avec la propriété &quot;required&quot;*.

Les techniques peuvent être suffisantes, consultatives ou en cas d’échec :

* A *Technique suffisante* est un critère qui, s’il est suivi, suffira à remplir un critère de réussite particulier.
* Un *Technique consultative* est un critère qui, s’il est suivi, aura un impact positif sur l’accessibilité, mais peut ne pas suffire à lui seul pour garantir qu’un critère de réussite particulier est satisfait.
* A *Échec* est une technique décrivant un exemple spécifique de cas où un critère de réussite ne serait pas rempli.

Les détails des techniques incluent une description, l’applicabilité, des exemples, des ressources pour plus d’informations et des détails sur la façon dont les auteurs peuvent tester une application réussie de la technique.

La liste des techniques n’est pas terminée, et WAI la met constamment à jour avec de nouveaux exemples en fonction des développements dans la technologie web, les approches de conception et l’état de la recherche. Il est donc bon de vérifier régulièrement la liste des techniques pour les nouveaux ajouts.

### Présentation de WCAG 2.0 {#understanding-wcag}

Il s’agit d’une série de documents qui fournissent des conseils aux lecteurs pour les aider à comprendre l’objectif de directives spécifiques et de critères de réussite. Vous pouvez [télécharger une introduction, ainsi que des liens vers des informations plus détaillées](https://www.w3.org/TR/2008/NOTE-UNDERSTANDING-WCAG20-20081211/Overview.html).

Chaque consigne et critère de réussite possède également sa propre page &quot;Compréhension&quot;, qui fournit des informations sur :

* l’intention de la ligne directrice ;
* des critères de réussite spécifiques ;
* Techniques consultatives qui aident à répondre aux exigences de la consigne, mais qui ne tombent sous aucun critère de réussite spécifique.

La page de &quot;compréhension&quot; individuelle de chaque critère de réussite fournit des informations sur :

* l’intention du critère de réussite ;
* Exemples généraux sur la façon dont le critère de réussite peut être rempli;
* Ressources connexes (hors W3C) sur la façon de remplir le critère de réussite ;
* des techniques et échecs : exemples spécifiques et détaillés de la façon dont le critère de réussite peut être rempli (décrits plus en détail ci-dessous) ;
* les termes clés : glossaire des termes importants pour comprendre le critère de réussite.

En voici un exemple : [Présentation du critère de réussite 1.1.1 (« contenu non textuel »)](https://www.w3.org/TR/2008/NOTE-UNDERSTANDING-WCAG20-20081211/text-equiv-all.html).

### Conformité à WCAG 2.0 {#how-to-meet-wcag}

La section « Comment se conformer » est disponible sur la page [Comment se conformer à WCAG 2.0](https://www.w3.org/WAI/WCAG20/quickref/). Cette section offre une autre présentation de WCAG, ce qui permet d’affiner le contenu des consignes par rapport à celles qui sont les plus pertinentes pour les intérêts ou les circonstances d’un lecteur. Les Readers peuvent filtrer les techniques de critères de réussite qu’ils souhaitent afficher en spécifiant des technologies de contenu web particulières, telles que les feuilles de style en cascade ou les scripts, ou en spécifiant un ou plusieurs niveaux de priorité particuliers.

Sans filtrage, cette ressource fournit tous les critères de réussite regroupés par consigne. Pour chaque critère de réussite, les informations suivantes sont fournies :

* le texte du critère de réussite ;
* un lien vers le document de &quot;compréhension&quot; correspondant ;
* Une liste des techniques suffisantes connexes, avec un lien vers les détails de chaque technique ;
* une liste des techniques consultatives connexes, avec un lien vers les détails de chaque technique (le cas échéant) ;
* Liste des échecs associés, en lien avec les détails de chaque échec.
