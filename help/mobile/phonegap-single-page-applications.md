---
title: Applications sur une seule page
seo-title: Single Page Applications
description: Consultez cette page pour en savoir plus sur les applications d’une seule page, c’est-à-dire que vous pouvez créer une application qui fonctionne de la même manière qu’une application de bureau ou mobile.
seo-description: Follow this page to learn about single page applications, that is, you can create an application that performs identically to a desktop or mobile application.
uuid: d1865e79-6e7c-4149-95c0-556e61478b01
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/MOBILE
topic-tags: developing-adobe-phonegap-enterprise
discoiquuid: a5b5e40e-2457-45fe-9632-baf5008fe8bf
exl-id: a0847b2b-d508-474d-a155-8ee891c566fa
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1023'
ht-degree: 3%

---

# Applications sur une seule page{#single-page-applications}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

>[!NOTE]
>
>Adobe recommande d’utiliser l’éditeur d’application d’une seule page (SPA) pour les projets nécessitant un rendu côté client basé sur la structure SPA (par exemple, React). [En savoir plus](/help/sites-developing/spa-overview.md).

[Applications d’une seule page](https://en.wikipedia.org/wiki/Single-page_application) (SPA) ont atteint une masse critique, largement considérée comme le modèle le plus efficace pour créer des expériences harmonieuses avec la technologie web. En suivant un modèle de SPA, vous pouvez créer une application qui fonctionne de la même manière qu’une application de bureau ou mobile, mais qui atteint une multitude de plateformes d’appareils et de facteurs de formulaire en raison de sa base dans les normes web ouvertes.

En règle générale, les SPA semblent plus performants que les sites web basés sur des pages classiques, car ils chargent généralement une page de HTML complète. **only** (y compris CSS, JS et le contenu de police pris en charge), puis chargez uniquement les éléments nécessaires à chaque changement d’état dans l’application. Ce qui est nécessaire à ce changement d’état peut varier en fonction de l’ensemble de technologies choisi, mais inclut généralement un fragment de HTML unique pour remplacer la &quot;vue&quot; existante, et l’exécution d’un bloc de code JS pour câbler la nouvelle vue et effectuer tout rendu de modèle côté client qui peut être nécessaire. La vitesse de ce changement d’état peut être encore améliorée en prenant en charge les mécanismes de mise en cache des modèles, ou même l’accès hors ligne au contenu des modèles si Adobe PhoneGap est utilisé.

AEM 6.1 prend en charge la création et la gestion de SPA par le biais d’Applications d’Adobe. Cet article présente les concepts sous-jacents de la SPA et leur utilisation [AngularJS](https://angularjs.org/) pour importer votre marque dans App Store et Google Play.

## SPA dans les applications AEM {#spa-in-aem-apps}

La structure d’applications d’une seule page d’AEM Apps permet d’obtenir des performances élevées d’une application AngularJS, tout en permettant aux auteurs (ou à d’autres personnes non techniques) de créer et de gérer le contenu de l’application via l’environnement d’éditeur par glisser-déposer optimisé pour les écrans tactiles, traditionnellement réservé à la gestion des sites web. Un site a-t-il déjà été créé avec AEM ? Vous constaterez que la réutilisation de votre contenu, de vos composants, de vos workflows, de vos ressources et de vos autorisations est facile avec les applications AEM.

## Module d’application AngularJS {#angularjs-application-module}

AEM Apps gère une grande partie de la configuration AngularJS pour vous, y compris l’assemblage du module de niveau supérieur de votre application. Par défaut, ce module est nommé &quot;AEMAngularApp&quot; et le script responsable de sa génération se trouve (et est superposé) sur /libs/mobileapps/components/angular/ng-page/angular-app-module.js.jsp.

Une partie de l’initialisation de votre application implique de spécifier les modules AngularJS dont dépend l’application. La liste des modules utilisés par votre application est spécifiée par un script situé dans /libs/mobileapps/components/angular/ng-page/angular-module-list.js.jsp et peut être recouverte par le composant de page de vos applications afin d’extraire tout module AngularJS supplémentaire requis par votre application. Par exemple, comparez le script ci-dessus à l’implémentation de Geometrixx (située à l’adresse /apps/geometrixx-outdoors-app/components/angular/ng-geometrixx-page/angular-module-list.js.jsp).

Pour prendre en charge la navigation entre les états distincts de votre application, le script angular-app-module effectue une itération sur toutes les pages descendantes de la page de votre application de niveau supérieur afin de générer un ensemble d’&quot;itinéraires&quot; et de configurer chaque chemin sur le service $routeProvider de l’Angular. Pour un exemple de la manière dont cela se pratique, consultez le script angular-app-module généré par l’exemple d’application Geometrixx Outdoors : (le lien nécessite une instance locale) [http://localhost:4502/content/phonegap/conference-app/en/home.angular-app-module.js](http://localhost:4502/content/phonegap/conference-app/en/home.angular-app-module.js)

En se connectant à AEMAngularApp généré, vous trouverez une série d’itinéraires spécifiés comme suit :

```xml
$routeProvider
.when('/content/phonegap/geometrixx-outdoors/en/home/products/:id', {
    templateUrl: 'home/products.template.html',
    controller: 'contentphonegapgeometrixxoutdoorsenhomeproducts'
})
```

L’exemple ci-dessus illustre un exemple de transmission d’un paramètre dans le cadre du chemin d’accès. Dans cet exemple, nous indiquons que lorsqu’un chemin qui correspond au modèle spécifié (/content/phonegap/geometrixx-outdoors/en/home/products/:id) est demandé, il doit être géré par le modèle home/products.template.html et utiliser le contrôleur &#39;contentphonegapgeometrixx-doorsendevoirs&#39;.

Le modèle à charger lorsque cet itinéraire est demandé est spécifié par la propriété templateUrl . Ce modèle contiendra le HTML des composants d’AEM qui ont été inclus sur la page, ainsi que toute directive AngularJS nécessaire pour câbler le côté client de l’application. Pour obtenir un exemple de directive AngularJS dans un composant de Geometrixx, consultez la ligne 45 du template.jsp du carrousel de glissement (/apps/geometrixx-outdoors-app/components/swipe-carousel/template.jsp).

## Contrôleurs de page {#page-controllers}

Selon les propres termes de l’Angular, &quot;un contrôleur est une fonction constructeur JavaScript utilisée pour augmenter la portée de l’Angular.&quot; ([source](https://docs.angularjs.org/guide/controller)) Chaque page d’une application AEM est automatiquement connectée à un contrôleur qui peut être augmenté par n’importe quel contrôleur qui spécifie une `frameworkType` de `angular`. Prenez le composant ng-text comme exemple (/libs/mobileapps/components/angular/ng-text), y compris le noeud cq:template qui s’assure que chaque fois que ce composant est ajouté à une page, il inclut cette propriété importante.

Pour un exemple de contrôleur plus complexe, ouvrez le script ng-template-page controller.jsp (situé dans /apps/geometrixx-outdoors-app/components/angular/ng-template-page). Le code JavaScript généré lors de l’exécution est particulièrement intéressant, car il s’affiche comme suit :

```xml
// Controller for page 'products'
.controller('contentphonegapgeometrixxoutdoorsenhomeproducts', ['$scope', '$http', '$routeParams',
    function($scope, $http, $routeParams) {
        var sku = $routeParams.id;
        var productPath = '/' + sku.substring(0, 2) + '/' + sku.substring(0, 4) + '/' + sku;
        var data = $http.get('home/products' + productPath + '.angular.json' + cacheKiller);

        /* ng-product component controller (path: content-par/ng-product) */
        data.then(function(response) {
            $scope.contentparngproduct = response.data["content-par/ng-product"].items;
        });

        /* ng-image component controller (path: content-par/ng-product/ng-image) */
        data.then(function(response) {
            $scope.contentparngproductngimage = response.data["content-par/ng-product/ng-image"].items;
        });
    }
])
```

Dans l’exemple ci-dessus, vous remarquerez que nous prenons un paramètre de la variable `$routeParams` puis les masser dans la structure de répertoires dans laquelle sont stockées nos données JSON. En traitant le sku `id` de cette manière, nous sommes en mesure de fournir un modèle de produit unique qui peut générer les données de produit pour potentiellement des milliers de produits distincts. Il s’agit d’un modèle beaucoup plus évolutif qui nécessite un itinéraire individuel pour chaque élément d’une base de données de produits (potentiellement) massive.

Deux éléments sont également à l’oeuvre ici : ng-product augmente la portée avec les données qu’il extrait de ce qui précède `$http` appelez . Il existe également une image ng sur cette page qui, à son tour, augmente également la portée avec la valeur qu’elle récupère de la réponse. En vertu de l&#39;Angular `$http` , chaque composant patiente jusqu’à ce que la requête soit terminée et que la promesse qu’il a créée soit remplie.

## Les étapes suivantes {#the-next-steps}

Une fois que vous avez appris les applications d’une seule page, reportez-vous à la section [Développement d’applications avec l’interface de ligne de commande PhoneGap](/help/mobile/phonegap-apps-pg-cli.md).
