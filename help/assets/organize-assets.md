---
title: Organisez vos ressources numériques.
description: Organisez vos ressources numériques, images, fichiers, dossiers, etc. à l’aide de Experience Manager.
contentOwner: AG
feature: Gestion des ressources, Recherche
role: User
exl-id: 41e083b3-e956-4346-9a99-008de2c6a169
source-git-commit: 5d96c09ef764b02e08dcdf480da1ee18f4d9a30c
workflow-type: tm+mt
source-wordcount: '809'
ht-degree: 19%

---

# Organisez vos ressources numériques. {#organize-digital-assets}

L’ensemble des ressources numériques, des métadonnées et du contenu des documents Microsoft Office et PDF sont extraits et rendus utilisables dans une requête. Les recherches permettent un filtrage élaboré des ressources et respectent entièrement les autorisations. Les métadonnées sont décrites en détail dans la section Métadonnées de la gestion des ressources numériques.

AEM Assets prend en charge plusieurs manières d’organiser le contenu. Vous pouvez les organiser de manière hiérarchique à l’aide de dossiers ou les organiser de manière ad hoc et non ordonnée à l’aide de balises, par exemple. Les utilisateurs peuvent modifier les balises dans l’éditeur de ressources de gestion des actifs numériques où les sous-ressources, rendus et métadonnées sont affichés.

## Organisation des ressources dans des dossiers {#organize-using-folders}

La méthode la plus simple pour organiser les ressources consiste à les enregistrer dans des dossiers. C’est analogue à l’organisation de fichiers dans des dossiers de notre système de fichiers local. Pour plus d’informations sur la création et la gestion des dossiers, voir [Gestion des ressources](managing-assets-touch-ui.md). La manière dont vous nommez les fichiers et les dossiers, organisez les sous-dossiers et gérez les fichiers dans ces dossiers peut avoir un impact significatif sur la manière dont ces ressources sont traitées. Grâce à des stratégies d’attribution de noms de fichiers et de dossiers cohérentes et appropriées, ainsi qu’à de bonnes pratiques de métadonnées, vous pouvez tirer le meilleur parti de votre référentiel de ressources numériques.

* Dans la plupart des cas, votre référentiel de ressources numériques est toujours en croissance. Il est donc important de formaliser l’utilisation des métadonnées, la structure des dossiers et l’attribution de noms aux fichiers au début du cycle de création de contenu.
* Utilisez les dossiers uniquement pour imposer une structure de stockage cohérente pour vos ressources numériques. Cette cohérence aide votre processus et à mieux gérer vos ressources. Par exemple, les ressources placées dans les types de dossiers suivants peuvent vous aider à utiliser les [profils appropriés à utiliser pour le traitement des ressources](processing-profiles.md) :

   * **Dossiers de développement** : contiennent les ressources numériques que vous utilisez actuellement.
   * **Dossiers de clients** : contiennent des ressources numériques en fonction des clients ou des noms de projet.
   * **Dossiers**  Principal : contiennent les ressources numériques sources originales.
   * **Dossiers de rendus** : contiennent les rendus et les copies des ressources numériques sources originales.
   * **Dossiers de taille de fichier** : contiennent des ressources numériques en fonction des tailles de fichier petite, moyenne et volumineuse.
   * **Dossiers intermédiaires** : contiennent les ressources numériques qui sont prêtes à être publiées sur votre site web.
   * **Dossiers de type MIME**  : contiennent des ressources numériques spécifiques à des types MIME tels que des images, des documents et des fichiers multimédia.
   * **Dossiers d’archives** : contiennent les ressources numériques retirées.
   * **Dossiers reposant sur une date** : contiennent des ressources numériques en fonction d’une date de création ou d’une date de dernière modification.

* Créez un répertoire de dossiers susceptibles de ne pas changer, de sorte que toute personnalisation ou automatisation continue de fonctionner. Par exemple, les profils de traitement affectés continuent à fonctionner.
* Si une ressource est déjà publiée, utilisez AEM pour la déplacer vers un autre dossier et la republier à partir de son nouvel emplacement, l’emplacement d’origine de la ressource publiée est toujours disponible, ainsi que la ressource qui vient d’être republiée. Toutefois, la ressource publiée d’origine est *perdue* à AEM et ne peut pas être annulée. Par conséquent, il est recommandé d’abord d’annuler la publication d’une ressource, puis de la déplacer vers un autre dossier.

## Organisation des ressources à l’aide de balises {#use-tags-to-organize-assets}

À l’aide de balises, en tant que métadonnées, vous pouvez facilement rechercher des ressources, créer des collections à l’aide des résultats de recherche, améliorer le classement de certaines ressources et utiliser les algorithmes d’IA Adobe Sensei pour la découverte de ressources.

Adobe Experience Manager Assets utilise un algorithme d’auto-apprentissage pour créer des balises hautement descriptives qui vous permettent de trouver la ressource appropriée en quelques clics seulement. Le balisage intelligent utilise Adobe Sensei, notre intelligence artificielle et notre structure d’apprentissage automatique, qui peuvent être formés pour reconnaître et appliquer des balises standard et commerciales à l’imagerie. Les balises intelligentes peuvent également identifier le contenu, les mots individuels ou les expressions et appliquer automatiquement des balises descriptives aux ressources.

Pour plus d’informations, voir les articles suivants :

* [À propos des balises dans AEM](/help/sites-authoring/tags.md)
* [Modification des métadonnées de ressource](meta-edit.md)
* [Balises intelligentes améliorées dans Assets](enhanced-smart-tags.md)

## Organisation en tant que collections {#organize-as-collections}

Avec les collections de ressources dans Experience Manager Assets, vous pouvez rationaliser la création, la modification et le partage de ressources entre les utilisateurs. Créez plusieurs types de collections en fonction de leur utilisation, y compris des collections contenant une liste de référence statique de ressources, dossiers et collections, ainsi que des collections qui extraient des ressources en fonction de critères de recherche.  Vous pouvez également créer des collections avec des ressources provenant de différents emplacements et les partager avec plusieurs utilisateurs disposant de différents niveaux d’accès, d’affichage et de modification des privilèges.

Pour plus d’informations, voir [Gestion des collections](managing-collections-touch-ui.md)

<!-- TBD items: add screenshots where applicable
Any hints/recommendations of when to use what method of organizing? Some examples of how organizing helps towards a better taxonomy and improved content velocity.
Add back links to blog posts by marketing?
-->

## Organisation de vos ressources pour utiliser des profils {#organize-to-use-profiles}

Un profil de traitement contient des commandes de traitement des ressources qui s’appliquent aux ressources qui sont chargées dans des dossiers prédéfinis. Les profils sont utilisés pour automatiser le traitement du contenu d’un dossier ou de ressources fraîchement chargées. Vous pouvez tirer parti des profils pour mieux organiser vos ressources.

La normalisation de l’utilisation des métadonnées, de l’attribution des noms de fichiers et de la structure des dossiers vous permet d’appliquer des profils de traitement à vos dossiers avec une précision et une cohérence accrues.

Pour plus d’informations sur les différents profils que vous pouvez créer et gérer pour traiter des ressources, voir :

* [Profils de traitement des métadonnées, des images et des vidéos](processing-profiles.md)
* [Profils de métadonnées](metadata-profiles.md)
* [Profils vidéo](video-profiles.md)
* [Profils d’image Dynamic Media](image-profiles.md)
