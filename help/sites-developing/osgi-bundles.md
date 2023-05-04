---
title: Lots OSGi
seo-title: OSGI Bundles
description: Conseils pour gérer vos lots OSGi
seo-description: Tips for managing your OSGi bundles
uuid: 07af7089-a233-4e5b-928c-76ddc0af8839
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: 8d3374ac-51dd-4ff5-84c9-495c937ade12
exl-id: 19df20a9-7c89-4dfa-8eca-81c4a14c21ff
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 62%

---

# Lots OSGi{#osgi-bundles}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

## Utilisation du contrôle de version sémantique {#use-semantic-versioning}

Les bonnes pratiques de numérotation de version sémantique sont disponibles à l’adresse [https://semver.org/](https://semver.org/).

## N’incorporez pas plus de classes et de fichiers JAR que nécessaire dans les lots OSGi. {#do-not-embed-more-classes-and-jars-than-strictly-needed-in-osgi-bundles}

Les bibliothèques courantes doivent être prises en compte dans des lots distincts. Cela leur permet d’être réutilisées dans vos lots. Lors de l’encapsulation d’une *JAR* dans un lot OSGI, veillez à vérifier les sources en ligne pour vérifier si quelqu’un a déjà effectué cette opération auparavant. Voici quelques emplacements courants pour trouver les wrappers de bundle existants : Apache Felix, Apache Sling, Apache Geronimo, Apache ServiceMix, Eclipse Bundle Recipes et le référentiel SpringSource Enterprise Bundle Repository.

## Dépendre des versions de lots les plus basses nécessaires {#depend-on-the-lowest-needed-bundle-versions}

Pour les dépendances au moment de la compilation dans les fichiers POM, utilisez toujours la plus ancienne version possible exposant l’API requise. Cela permet davantage de compatibilité ascendante et facilite les correctifs de rétroportage des versions plus anciennes.

## Exportez un ensemble restreint de packages à partir des lots OSGi. {#export-a-minimal-set-of-packages-from-osgi-bundles}

Dès qu’un package est exporté, nous créons une API dont les autres peuvent dépendre. Veillez à exporter le moins possible et à vérifier que ce qui est exporté est une API. Il est beaucoup plus facile de rendre publique une méthode/classe privée que de rendre privé un élément précédemment exporté.

Les mises en œuvre doivent toujours être placées dans un package *impl* distinct. Par défaut, la variable *maven-bundle-plugin* exportera tout élément du projet qui n’a pas de *impl* dans son nom.

## Définissez toujours explicitement une version sémantique pour chaque package exporté. {#always-explicitly-define-a-semantic-version-for-each-package-exported}

Cela permet aux consommateurs de votre API d’évoluer avec vous. Lorsque vous procédez de la sorte, respectez toujours les bonnes pratiques de contrôle de version sémantique. Cela permet aux consommateurs de votre API de déterminer les types de modifications à attendre dans une nouvelle version.

## Incluez les informations de métatype lorsqu’elles sont exposées. {#include-metatype-information-where-exposed}

En spécifiant des informations de métatype pertinentes, vos services et composants sont plus faciles à comprendre dans la console Felix. La liste des attributs et annotations SCR peut être trouvée à l’adresse : [https://felix.apache.org/documentation/subprojects/apache-felix-maven-scr-plugin/scr-annotations.html](https://felix.apache.org/documentation/subprojects/apache-felix-maven-scr-plugin/scr-annotations.html).
