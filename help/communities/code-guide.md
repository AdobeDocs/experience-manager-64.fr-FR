---
title: Consignes de codage
seo-title: Coding Guidelines
description: Conseils, astuces et conseils pour les développeurs de communautés
seo-description: Communities developer guidelines, tips, and tricks
uuid: 311ef4f7-7f2c-44c3-bcf2-f68713752623
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: 244cd43c-a573-495d-b80c-b97ba9d19b75
exl-id: 022043cd-35ed-49b1-b5b4-5cc92d29cef4
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 3%

---

# Consignes de codage {#coding-guidelines}

## Conseils, astuces et astuces {#guidelines-tips-and-tricks}

L’utilisation d’AEM Communities est passée d’une dépendance importante aux pages de serveur Java à une flexibilité dans le choix de langages de script de modèle dans lesquels la logique commerciale, le style et le contenu de page sont distincts l’un de l’autre.

L’API SocialResourceProvider offre une plus grande flexibilité pour l’utilisation du contenu généré par l’utilisateur, ce qui évite d’avoir à identifier ce qui [SRP](srp.md) a été sélectionnée pour le déploiement.

Vous trouverez ci-dessous diverses instructions de codage et bonnes pratiques pour les développeurs AEM Communities :

### Code {#code}

* [Accès au contenu généré par l’utilisateur avec SRP](accessing-ugc-with-srp.md) - comment éviter d’écrire une application qui ne fonctionne que lorsque le contenu créé par l’utilisateur est stocké dans JCR (JSRP).
* [Refactorisation de SocialUtils](socialutils.md) - méthodes d’utilitaire pour SRP qui remplacent SocialUtils.
* [Conventions de dénomination](naming-conventions.md) - conventions de dénomination pour les classes Java personnalisées.

### Scripts {#scripts}

* [Chargement partiel des composants de communauté](sideloading.md) : procédure d’ajout dynamique d’un composant après le chargement de la page.
* [Principes élémentaires de l’éditeur de texte enrichi](rte.md) - Comment personnaliser l’interface utilisateur de texte enrichi fournie aux membres pour la publication de contenu.

### IDE {#ide}

* [Utilisation de Maven pour Communities](maven.md) - Comment inclure le fichier jar de l’API Communities.
* [Refactorisation de SocialUtils](socialutils.md) - méthodes d’utilitaire pour SRP qui remplacent SocialUtils.
