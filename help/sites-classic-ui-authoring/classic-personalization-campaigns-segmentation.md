---
title: Compréhension de la segmentation
seo-title: Understanding Segmentation
description: La segmentation est un élément clé de la création d’une campagne. Dans la plupart des cas, vous devez avoir des segments déjà définis avant de démarrer votre campagne.
seo-description: Segmentation is a key consideration when creating a campaign. In most cases, you will need to have segments already defined before starting your campaign.
uuid: 609d83b3-df0e-44ad-8e27-90b676d2666b
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: personalization
content-type: reference
discoiquuid: bb75f4ab-d983-45f6-98a3-da8bd9b63751
exl-id: 441cf983-e1dc-4343-9c2c-e5ed5891e84b
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '565'
ht-degree: 72%

---

# Compréhension de la segmentation{#understanding-segmentation}

La segmentation est un élément clé de la création d’une campagne. Dans la plupart des cas, vous devez avoir des segments déjà définis avant de démarrer votre campagne.

Les visiteurs de site se rendent sur un site en fonction d’intérêts et d’objectifs divers. Le fait de comprendre ces objectifs et de satisfaire à ces attentes est un important facteur de réussite en matière de marketing en ligne.

La segmentation permet d’y parvenir en procédant à une analyse et à une caractérisation des aspects suivants du visiteur :

* son activité sur le site web
* son profil
* son activité sur d’autres sites web.

Le contenu peut cibler les besoins et centres d’intérêts spécifiques des visiteurs en fonction du ou des segments correspondants.

## Utilisation de la segmentation {#using-segmentation}

Les segments sont définis dans la section [Configuration de la segmentation](/help/sites-administering/campaign-segmentation.md). Ils sont utilisés afin d’orienter le contenu réel affiché pour une audience cible spécifique.

## Terminologie de la segmentation {#segmentation-terminology}

Lors de la discussion de la segmentation, la terminologie suivante est utilisée :

**Visiteur** Un visiteur est une personne qui visite un site web. La visite de cette personne commence généralement à partir d’une page de référence, puis aboutit à l’affichage d’une ou de plusieurs pages de votre propre site web. Un profil de comportement peut être créé à partir des détails de la visite de cette personne.

**Utilisateur** Un utilisateur est un visiteur qui s’inscrit auprès du site web pour recevoir un profil de compte. Pour générer son profil, il fournit des informations d’identification supplémentaires telles qu’une adresse électronique, son sexe, entre autres. Des informations supplémentaires peuvent également être collectées, y compris l’activité communautaire et les comportements d’achats, entre autres choses encore. En fonction des informations fournies dans le profil, un profil démographique peut être créé.

**Caractéristique** Une caractéristique est une caractéristique ou une propriété d’un visiteur qui peut être utilisée pour déterminer son appartenance à un segment spécifique.

**Segment** Un segment est un ensemble de visiteurs qui partagent certaines caractéristiques. Les segments doivent être distincts, avec un minimum de chevauchement avec les autres segments.

**Caractéristiques comportementales** Les caractéristiques comportementales sont liées au comportement d’un visiteur sur le site web. Celles-ci comprennent les éléments suivants :

* L’intérêt au sein de votre site web ; notamment les pages visitées et les produits achetés.
* L’intérêt sur le site web de référence ; notamment les termes de recherche utilisés ou les publicités cliquées.
* L’intérêt sur d’autres sites, déterminé à l’aide d’outils tels que Spyjax.
* La fidélité du visiteur ; la durée de la visite, la fréquence des visites.

**Caractéristiques démographiques** Il s’agit de caractéristiques de population sélectionnées, notamment :

* Âge
* Revenu
* Taille de la famille
* État civil
* Sexe
* Emplacement

**Caractéristiques dérivées**  

Certaines caractéristiques démographiques sont difficiles à déterminer sans inscription, mais peuvent être extraites en combinant les caractéristiques comportementales et démographiques.

Par exemple, la combinaison de l’URL de référence (en tant que caractéristique comportementale) avec des données démographiques (acquises à partir d’outils tels que [Google Ad Planner](https://www.google.com/adplanner/)) permet aux propriétaires du site d’extraire les caractéristiques comportementales de leurs visiteurs.

**Sous-segment** Un segment peut être divisé en plusieurs sous-segments. Ceci s’effectue en définissant des caractéristiques supplémentaires.

**Page Teaser** Une page de teaser est destinée à une audience spécifique. Elle contient du contenu réutilisable qui peut être utilisé dans le paragraphe de teaser.

**Campagne** Une campagne est un ensemble de pages de teaser et de pages de marketing par e-mail, telles que des newsletters ou des invitations. Typiquement, une campagne dure pendant une période limitée, puis elle est remplacée par une autre campagne.

**Paragraphe de teaser** Il s’agit d’un paragraphe qui extrait du contenu d’une autre page selon une stratégie de sélection. Cette stratégie de sélection peut tenir compte de segments et de campagnes.

**Liste** Une liste est extraite à partir d’un segment d’utilisateurs enregistrés. Par exemple, l’emplacement utilisé pour diriger le contenu du paragraphe de teaser.

>[!NOTE]
>
>Veuillez consulter [Segmentation](/help/sites-administering/campaign-segmentation.md) pour plus d’informations sur les segments dans AEM.
