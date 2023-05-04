---
title: Lecteurs d’écran pour les formulaires HTML5
seo-title: Screen readers for HTML5 forms
description: Répertorie les lecteurs d’écran pris en charge avec les formulaires HTML5.
seo-description: Lists the screen readers supported with HTML5 forms.
uuid: 035354e2-957f-4eb6-bc16-4ca96ec7ac74
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: hTML5_forms
discoiquuid: 53c57180-7004-4534-9146-603f7770a6fe
feature: Mobile Forms
exl-id: c27eb771-d390-4534-8e67-f1277550e760
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 60%

---

# Lecteurs d’écran pour les formulaires HTML5 {#screen-readers-for-html-forms}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Les composants de HTML5 forms génèrent un modèle de formulaire XFA au format HTML5. Tous les navigateurs standard prenant en charge HTML5 peuvent générer ces formulaires. Pour prendre en charge une expérience de capture de données similaire dans les formulaires PDF et HTML5, la mise en page des PDF forms est conservée dans les formulaires HTML5.

Les formulaires HTML5 utilisent des constructions HTML standard, ce qui permet d’utiliser les outils d’accessibilité usuels du format HTML avec ces formulaires. Si un formulaire est conçu selon les bonnes pratiques relatives aux formulaires accessibles, il fonctionne avec n’importe quel lecteur d’écran pris en charge. De plus, ces formulaires sont activés pour la navigation au clavier.

## Normes d’accessibilité {#accessibility-standards}

Les formulaires HTML5 sont conformes à la section 508 concernant l’accessibilité avec des exceptions connues. Voir [VPAT pour les formulaires HTML5](https://www.adobe.com/content/dam/cc1/en/accessibility/compliance/pdfs/adobe-livecycle-es4-section-508-vpat-portfolio.pdf) pour plus d’informations.

## Lecteurs d’écran certifiés pour les formulaires HTML5 {#certified-screen-readers-for-html-forms}

* JAWS 14.0 sous Microsoft Windows
* Voix off sur Mac OS X et iPad

### JAWS {#jaws}

Toutes les combinaisons de touches et tous les raccourcis par défaut fonctionnent pour les formulaires HTML5. Pour plus d’informations sur l’utilisation de JAWS, consultez le site [https://www.freedomscientific.com/jaws-hq.asp](https://www.freedomscientific.com/products/software/jaws/).

### Voix off {#voiceover}

HTML5 prend en charge toutes les combinaisons de touches et tous les mouvements par défaut de la voix off. Pour plus d’informations sur la configuration et l’utilisation de VoiceOver, consultez le site [https://www.apple.com/accessibility/voiceover/](https://www.apple.com/accessibility/voiceover/).

## Problèmes connus {#known-issues}

* **(Internet Explorer 9 uniquement)** : dans les formulaires HTML5, les pages sont chargées à la demande (dynamiquement). Le chargement des pages à la demande provoque des problèmes dans le fonctionnement des lecteurs d’écran. Lorsque le point de focalisation du lecteur d’écran est sur le dernier champ de la page et que l’utilisateur appuie sur la touche de tabulation, au lieu de passer au premier champ de la page suivante, le lecteur d’écran retourne au premier champ de la première page du formulaire.
* **(Internet Explorer 9 uniquement)** La commande Sélecteur de date dans les formulaires HTML5 n’est pas totalement accessible avec le clavier. Dans le contrôle du Sélecteur de date, si vous appuyez sur les touches Haut/Bas plusieurs fois, le contrôle Sélecteur de date se ferme et le point de focalisation passe au prochain/dernier champ.

* VoiceOver ne peut pas détecter les touches de flèches sur le widget de date sur Safari iPad.
