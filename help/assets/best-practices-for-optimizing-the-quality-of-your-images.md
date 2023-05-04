---
title: Bonnes pratiques relatives à l’optimisation de la qualité des images
description: Découvrez les bonnes pratiques relatives à l’optimisation de la qualité des images dans Dynamic Media
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.4/ASSETS
topic-tags: dynamic-media
content-type: reference
exl-id: 2e90bea1-eaac-457b-8588-b18d3a6e8d91
feature: Asset Management,Renditions
role: User
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1497'
ht-degree: 53%

---

# Bonnes pratiques relatives à l’optimisation de la qualité des images  {#best-practices-for-optimizing-the-quality-of-your-images}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

L’optimisation de la qualité des images peut être un processus chronophage, car de nombreux facteurs contribuent à l’obtention de résultats acceptables. Le résultat est en partie subjectif parce que les individus perçoivent différemment la qualité de l&#39;image. L&#39;expérimentation structurée est la clé.

AEM comprend plus de 100 commandes de diffusion d’images Dynamic Media pour l’optimisation et l’optimisation des images et des résultats de rendu. Les conseils suivants vous aideront à rationaliser le processus et à obtenir rapidement de bons résultats à l’aide de commandes essentielles et de bonnes pratiques.

## Bonnes pratiques relatives au format d’image (&amp;fmt=) {#best-practices-for-image-format-fmt}

* JPG ou PNG sont les meilleurs choix pour diffuser des images de bonne qualité avec une taille et un poids gérables.
* Si aucune commande de format n’est fournie dans l’URL, la diffusion d’images Dynamic Media est configurée par défaut sur JPG pour la diffusion.
* JPG compresse les images à un ratio de 10:1 et produit généralement des images de plus petite taille. Le format PNG compresse les images à un ratio d’environ 2:1, sauf dans certains cas, par exemple lorsque les images contiennent un arrière-plan blanc. En règle générale, cependant, les fichiers PNG sont plus volumineux que les fichiers JPG.
* JPG utilise la compression avec perte, ce qui signifie que les éléments d’image (pixels) sont déposés pendant la compression. Le format PNG, en revanche, utilise une compression sans perte.
* JPG compresse souvent les images photographiques avec une meilleure fidélité que les images de synthèse avec des bords nets et un contraste prononcés.
* Si vos images contiennent de la transparence, utilisez PNG, car JPG ne prend pas en charge la transparence.

La pratique recommandée pour le format d’image consiste à commencer par le paramètre le plus courant : `&fmt=JPG`.

## Bonnes pratiques relatives à la taille des images {#best-practices-for-image-size}

La réduction dynamique de la taille de l’image est l’une des tâches les plus courantes. Cela implique de spécifier la taille et, éventuellement, le mode de sous-échantillonnage utilisé pour réduire l’image.

* Pour le dimensionnement des images, la meilleure méthode, mais aussi la plus simple, consiste à utiliser `&wid=<value>` et `&hei=<value>,` ou simplement `&hei=<value>`. Ces paramètres définissent automatiquement la largeur de l’image en respectant le format.
* `&resMode=<value>` contrôle l’algorithme utilisé pour le sous-échantillonnage. Commencez par `&resMode=sharp2`. Cette valeur fournit la meilleure qualité d’image. Bien que l’utilisation du sous-échantillonnage `value =bilin` soit plus rapide, elle se traduit souvent par un crénelage des artefacts.

Pour le dimensionnement des images, il est recommandé d’utiliser `&wid=<value>&hei=<value>&resMode=sharp2` ou `&hei=<value>&resMode=sharp2`.

## Bonnes pratiques relatives à l’accentuation des images {#best-practices-for-image-sharpening}

L’accentuation des images est l’aspect le plus complexe du contrôle des images du site web, processus au cours duquel de nombreuses erreurs sont commises. Prenez le temps d’en savoir plus sur le fonctionnement de l’accentuation et du masquage flou dans AEM en vous référant à la variable [Bonnes pratiques relatives à la qualité des images Adobe Dynamic Media Classic et à l’accentuation](/help/assets/assets/sharpening_images.pdf) guide qui s’applique également à AEM.

Voir aussi [Accentuation d’une image avec un masque flou](https://helpx.adobe.com/photoshop/using/adjusting-image-sharpness-blur.html).

Avec AEM, vous pouvez accentuer les images lors de l’ingestion, lors de la distribution, ou les deux. Dans la plupart des cas, cependant, vous devez accentuer les images en utilisant une seule méthode ou l’autre, mais pas les deux. L’accentuation des images lors de la diffusion, sur une URL, vous donne généralement les meilleurs résultats.

Vous pouvez utiliser deux méthodes d’accentuation d’image :

* Accentuation simple (`&op_sharpen`) : à l’instar du filtre d’accentuation utilisé dans Photoshop, l’accentuation simple applique une accentuation de base à l’affichage final de l’image à la suite d’un redimensionnement dynamique. Cependant, cette méthode ne peut pas être configurée par l’utilisateur. Il est recommandé de ne pas utiliser &amp;op_sharpen sauf si cette méthode est requise.
* Masquage flou (`&op_USM`) : le masquage flou est un filtre d’accentuation standard. La bonne pratique consiste à accentuer les images à l’aide d’un masquage flou en suivant les instructions ci-dessous. Le masquage flou permet de contrôler les trois paramètres suivants :

   * `&op_sharpen=`quantité,rayon,seuil

      * **[!UICONTROL quantité]** (0 à 5, intensité de l’effet)
      * **[!UICONTROL rayon]** (0 à 250, largeur des « lignes d’accentuation » tracées autour de l’objet accentué, mesurées en pixels.)

             Gardez à l’esprit que les paramètres rayon et quantité fonctionnent l’un par rapport à l’autre. La réduction du rayon peut être compensée en augmentant la quantité. Le rayon permet un contrôle plus précis, car une valeur inférieure accentue uniquement les pixels de contour, tandis qu’une valeur supérieure traite une plus grande plage de pixels.
         
      * **[!UICONTROL seuil]** (0 à 255, sensibilité de l’effet)

             Ce paramètre définit l’écart recherché entre les pixels accentués et la zone environnante avant qu’ils ne soient considérés comme des pixels de contour et que le filtre les accentue. Le paramètre **[!UICONTROL seuil]** permet d’éviter l’accentuation excessive de zones aux couleurs similaires, telles que les tons chair. Par exemple, une valeur seuil de 12 permet d’ignorer les légères variations de la luminosité de la peau pour éviter d’ajouter du « bruit », tout en ajoutant un contraste sur les bords dans les zones à fort contraste, comme l’endroit où les cils rencontrent la peau.
         
         Pour plus d’informations sur la définition de ces trois paramètres, y compris les bonnes pratiques à utiliser avec le filtre, voir la section [Bonnes pratiques relatives à la qualité des images Adobe Dynamic Media Classic et à l’accentuation](/help/assets/assets/sharpening_images.pdf) guide (s’applique également à Dynamic Media sur AEM).
   * AEM permet également de contrôler un quatrième paramètre : monochrome (0,1). Ce paramètre détermine si le masquage flou est appliqué séparément à chaque composante de couleur en utilisant la valeur 0, ou à la luminosité/intensité de l’image en utilisant la valeur 1.


Il est recommandé de commencer par le paramètre rayon du masque flou. Les paramètres de rayon que vous pouvez commencer par sont les suivants :

* **[!UICONTROL Site web]** : 0,2 à 0,3 pixel
* **[!UICONTROL Impression photographique (250 à 300 ppp)]** : 0,3 à 0,5 pixel
* **[!UICONTROL Impression offset (266 à 300 ppp)]** : 0,7 à 1,0 pixel
* **[!UICONTROL Impression sur toile (150 ppp)]** : 1,5 à 2,0 pixels

Augmentez graduellement la valeur de 1,75 à 4. Si l’accentuation ne correspond toujours pas à votre choix, augmentez le rayon d’un point décimal et réexécutez la quantité de 1,75 à 4. Répétez l’opération si nécessaire.

Laissez le paramètre monochrome sur 0.

### Bonnes pratiques relatives à la compression des JPEG (&amp;qlt=) {#best-practices-for-compression-qlt}

* Ce paramètre contrôle la qualité du codage des JPG. Une valeur élevée produit une image de meilleure qualité, mais un fichier plus volumineux ; en revanche, une valeur faible signifie une image de qualité inférieure mais un fichier plus petit. La plage de ce paramètre est comprise entre 0 et 100.
* Pour optimiser la qualité, ne définissez pas la valeur du paramètre sur 100. La différence entre un paramètre de 90, 95 et 100 est presque imperceptible, mais 100 augmente inutilement la taille du fichier image. En conséquence, pour optimiser la qualité, mais éviter que les fichiers image deviennent trop volumineux, définissez `qlt=<value>` sur 90 ou 95.
* Pour optimiser pour une petite taille de fichier image tout en conservant la qualité de l’image à un niveau acceptable, définissez la `qlt=<value>` sur 80. Les valeurs inférieures à 70-75 entraînent une dégradation significative de la qualité de l’image.
* Une bonne pratique pour rester dans la moyenne consiste à définir `qlt=<value>` sur 85.
* Utilisation du drapeau chromatique dans le paramètre `qlt=`

   * Le paramètre `qlt=` possède un deuxième paramètre qui vous permet d’activer le sous-échantillonnage chromatique RVB à l’aide de la valeur `,1` ou de le désactiver à l’aide de la valeur `,0`.
   * Pour faire simple, commencez par désactiver le sous-échantillonnage chromatique RVB (`,0`). Ce paramètre produit généralement une image de meilleure qualité, en particulier pour les images de synthèse contenant beaucoup de contours nets et un fort contraste.

La bonne pratique pour la compression JPG consiste à utiliser `&qlt=85,0`.

## Bonnes pratiques relatives au dimensionnement des JPEG (&amp;jpegSize=) {#best-practices-for-jpeg-sizing-jpegsize}

Le paramètre jpegSize est utile pour garantir qu’une image n’excède pas une certaine taille pour sa diffusion sur les appareils dont la mémoire est limitée.

* Ce paramètre est défini en kilo-octets (`jpegSize=<size_in_kilobytes>`). Il définit la taille maximale autorisée pour la diffusion de l’image.
* `&jpegSize=` interagit avec le paramètre de compression JPG `&qlt=`. Si la réponse JPG avec le paramètre de compression JPG spécifié (`&qlt=`) ne dépasse pas la valeur jpegSize, l’image est renvoyée avec `&qlt=` tel que défini. Sinon, `&qlt=` est graduellement diminué jusqu’à ce que l’image soit ajustée à la taille maximale autorisée ou jusqu’à ce que le système détermine qu’il ne peut pas procéder à l’ajustement et renvoie une erreur.

Une bonne pratique consiste à définir `&jpegSize=` et à ajouter le paramètre `&qlt=` si vous diffusez des images JPG vers des appareils dont la mémoire est limitée.

## Résumé des bonnes pratiques {#best-practices-summary}

En règle générale, pour obtenir une image de qualité élevée mais un fichier de petite taille, commencez par la combinaison de paramètres suivante :

`fmt=jpg&qlt=85,0&resMode=sharp2&op_usm=1.75,0.3,2,0`

Cette combinaison de paramètres produit d’excellents résultats dans la plupart des cas.

Si l’image nécessite une optimisation supplémentaire, affinez progressivement les paramètres d’accentuation (masquage flou) en commençant par un rayon de 0,2 ou 0,3. Ensuite, augmentez progressivement la quantité de 1,75 à un maximum de 4 (équivalent à 400 % dans Photoshop). Vérifiez que le résultat souhaité est obtenu.

Si les résultats de l’accentuation ne sont toujours pas satisfaisants, augmentez le rayon par incréments décimaux. Pour chaque incrément décimal, relancez la quantité à 1,75 et augmentez-la progressivement à 4. Répétez cette procédure jusqu’à obtenir le résultat souhaité. Bien que les valeurs ci-dessus soient une approche validée par les studios de création, n’oubliez pas que vous pouvez commencer par d’autres valeurs et suivre d’autres stratégies. Que les résultats vous conviennent ou non est une question subjective, par conséquent l&#39;expérimentation structurée est la clé.

Au fur et à mesure de vos tests, vous trouverez peut-être également les suggestions générales suivantes utiles pour optimiser votre workflow :

* Testez différents paramètres en temps réel, directement sur une URL.
* Gardez à l’esprit que vous pouvez regrouper les commandes de diffusion d’images Dynamic Media dans un paramètre d’image prédéfini. Il s’agit en outre d’une bonne pratique. Un paramètre d’image prédéfini est, en fait, constitué de macros de commande d’URL avec des noms de paramètres prédéfinis personnalisés tels que `$thumb_low$` et `&product_high$`. Le nom du paramètre prédéfini personnalisé dans un chemin d’URL appelle ces paramètres prédéfinis. Cette fonctionnalité vous aide à gérer les commandes et les paramètres de qualité pour différents modèles d’utilisation des images sur vos sites web et raccourcit la longueur globale des URL.
* AEM fournit également des méthodes plus avancées pour régler la qualité des images, telles que l’application de l’accentuation des images lors de l’ingestion. Pour les cas d’utilisation plus complexes où il peut s’avérer nécessaire d’affiner et d’optimiser le rendu, n’hésitez pas à faire appel à [Adobe Professional Services](https://www.adobe.com/fr/experience-cloud/consulting-services.html).
