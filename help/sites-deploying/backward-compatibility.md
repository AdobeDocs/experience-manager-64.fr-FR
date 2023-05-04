---
title: Compatibilité ascendante dans AEM 6.4
seo-title: Backward Compatibility in AEM 6.4
description: Découvrez comment conserver la compatibilité de vos applications et configurations avec AEM 6.4
seo-description: Learn how to keep your apps and configurations compatible with AEM 6.4
uuid: 2fa8525e-7f3b-4096-ac85-01c2c76bc9ac
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: upgrading
content-type: reference
discoiquuid: 5e76fe09-4d37-4c8c-8baf-97e75689bd26
feature: Upgrading
exl-id: 5798100a-e03a-43f8-9189-ae51c06e192b
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '522'
ht-degree: 25%

---

# Compatibilité ascendante dans AEM 6.4{#backward-compatibility-in-aem}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

## Présentation {#overview}

>[!NOTE]
>
>Pour obtenir la liste des modifications de contenu et de configuration qui ne font pas partie du module de compatibilité, voir [Restructuration des référentiels dans AEM 6.4](/help/sites-deploying/repository-restructuring.md).

Dans AEM 6.4, toutes les fonctionnalités ont été développées en tenant compte de la compatibilité ascendante.

Dans la majorité des cas, les utilisateurs qui exécutent AEM 6.3 ne doivent pas changer le code ni les personnalisations lorsqu’ils effectuent la mise à niveau. Pour les clients AEM 6.1 et 6.2, il n’y a pas de modifications de rupture supplémentaires qui seraient rencontrées lors d’une mise à niveau vers la version 6.3.

Pour les exceptions où les fonctionnalités n’ont pas pu être maintenues rétrocompatibles, la compatibilité ascendante pour les lots et le contenu peut être obtenue en installant un package de compatibilité pour la version 6.3 (voir comment configurer ci-dessous pour plus d’informations sur l’emplacement de téléchargement). Ce package de compatibilité rétablit la compatibilité des applications conformes à AEM 6.3.

Le package de compatibilité vous permet d’exécuter AEM en mode de compatibilité et de différer le développement personnalisé par rapport aux nouvelles fonctionnalités d’AEM :

>[!NOTE]
>
>Notez que le package de compatibilité n’est qu’une solution temporaire visant à différer le développement requis pour garantir une compatibilité avec AEM 6.4. Il est recommandé de ne l’utiliser qu’en dernier ressort si vous ne parvenez pas à remédier aux problèmes de compatibilité par le biais du développement immédiatement après la mise à niveau. Il est vivement recommandé de passer en mode natif et de désinstaller le package de compatibilité une fois que vous avez décidé de procéder au développement personnalisé basé sur la version 6.4 et de bénéficier de toutes les fonctionnalités de la version 6.4.

![screen_shot_2018-04-05at43339pm](assets/screen_shot_2018-04-05at43339pm.png)

Le module de compatibilité possède deux modes : **Routage activé** et **Routage désactivé**.

AEM 6.4 peut ainsi être exécuté en trois modes :

**Mode natif :**

Le mode natif est destiné aux clients qui souhaitent utiliser toutes les nouvelles fonctionnalités d’AEM 6.4 et qui sont prêts à effectuer un certain développement pour que leurs personnalisations fonctionnent avec toutes les nouvelles fonctionnalités.

Cela signifie que vous devrez peut-être effectuer des ajustements dans votre application immédiatement après la mise à niveau.

**Mode de compatibilité : Package de compatibilité installé avec Routage activé**

Le mode de compatibilité est destiné aux clients qui disposent de personnalisations d’interfaces non rétrocompatibles. Cela permet à AEM de s’exécuter en mode de compatibilité et de différer le développement personnalisé requis par rapport aux nouvelles fonctionnalités AEM qui ne sont pas compatibles avec certaines de vos données de code personnalisé.

**Mode hérité : Package de compatibilité installé avec Routage désactivé**

Le mode hérité est destiné aux clients disposant d’interfaces personnalisées basées sur du code hérité ou obsolète d’AEM qui a été déplacé dans le package de compatibilité.

![image2018-2-12_23-58-37](assets/image2018-2-12_23-58-37.png)

## Méthode de configuration {#how-to-set-up}

Le package de compatibilité AEM 6.3 peut être installé en tant que package à l’aide du gestionnaire de modules. Vous pouvez télécharger le [Package de compatibilité AEM 6.3 de la distribution logicielle](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/compatpack/aem-compat-cq64-to-cq63) site.

Une fois le package de compatibilité installé, le routage peut être activé ou désactivé à l’aide d’un commutateur dans la configuration OSGI, comme indiqué ci-dessous :

![screen_shot_2017-11-27at122421pm](assets/screen_shot_2017-11-27at122421pm.png)

Une fois le package de compatibilité installé et configuré, les fonctionnalités sont utilisées sur la base du mode de compatibilité choisi.
