---
title: Mise en œuvre d’un composant React pour SPA
seo-title: Implementing a React Component for SPA
description: Cet article présente un exemple d’adaptation d’un composant React simple et existant pour le faire fonctionner avec l’éditeur de SPA d’AEM.
seo-description: This article presents an example of how to adapt a simple, existing React component to work with the AEM SPA Editor.
uuid: aebca2ea-a020-45e1-8043-f8c21154c660
contentOwner: bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: spa
content-type: reference
discoiquuid: 86a981fe-25f3-451a-b262-8c497619e0ac
exl-id: da0e076b-afb7-4ebe-8e5e-48c00750e453
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '594'
ht-degree: 88%

---

# Mise en œuvre d’un composant React pour SPA {#implementing-a-react-component-for-spa}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Les applications monopage (SPA) peuvent améliorer considérablement votre expérience des sites web. Les développeurs souhaitent pouvoir créer des sites à l’aide de structures SPA et les auteurs souhaitent modifier facilement du contenu dans AEM pour un site créé à l’aide de structures SPA.

La fonction de création d’application sur une seule page constitue une solution complète pour la prise en charge de ce type d’application dans AEM. Cet article présente un exemple d’adaptation d’un composant React simple et existant pour le faire fonctionner avec l’éditeur de SPA d’AEM.

>[!NOTE]
>La fonction Éditeur d’application sur une seule page (SPA) requiert AEM Service Pack 2 ou version ultérieure.
>
>L’éditeur de SPA est la solution recommandée pour les projets nécessitant un rendu côté client basé sur un framework de SPA (par exemple React ou Angular).

## Présentation {#introduction}

Grâce à un contrat simple et léger requis par AEM et établi entre la SPA et l’éditeur de SPA d’Adobe, il est facile d’utiliser une application JavaScript existante et de l’adapter à une SPA dans AEM.

Cet article illustre l’exemple du composant Météo de la SPA d’exemple We.Retail Journal.

Vous devez connaître la [structure d’une application SPA pour AEM](/help/sites-developing/spa-getting-started-react.md) avant de lire cet article.

>[!CAUTION]
>Ce document n’utilise l’[exemple d’application Journal We.Retail](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail-journal) qu’à des fins de démonstration. Ce dernier ne doit pas être utilisé dans le cadre d’un projet.
>
>Tout projet AEM doit exploiter l’[archétype de projet AEM](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=fr), qui prend en charge les projets SPA à l’aide de React ou d’Angular et utilise le SDK SPA.

## Le composant Météo {#the-weather-component}

Le composant Météo se trouve dans le coin supérieur gauche de l’application We.Retail Journal. Il affiche la météo actuelle d’un emplacement défini, en extrayant dynamiquement les données météorologiques.

### Utilisation du widget Météo {#using-the-weather-widget}

![screen_shot_2018-06-08at143224](assets/screen_shot_2018-06-08at143224.png)

Lors de la création du contenu de la SPA dans l’éditeur de SPA, le composant Météo apparaît comme tout autre composant d’AEM, avec une barre d’outils, et il est modifiable.

![screen_shot_2018-06-08at143304](assets/screen_shot_2018-06-08at143304.png)

La ville peut être mise à jour dans une boîte de dialogue comme tout autre composant AEM.

![screen_shot_2018-06-08at143446](assets/screen_shot_2018-06-08at143446.png)

La modification est conservée et le composant se met automatiquement à jour avec les nouvelles données météorologiques.

![screen_shot_2018-06-08at143524](assets/screen_shot_2018-06-08at143524.png)

### Implémentation du composant Météo {#weather-component-implementation}

Le composant Météo est en fait basé sur un composant React disponible publiquement, appelé [React Open Weather](https://www.npmjs.com/package/react-open-weather), adapté pour fonctionner en tant que composant dans l’exemple d’application de SPA We.Retail Journal.

Vous trouverez ci-dessous des extraits de la documentation NPM sur l’utilisation du composant React Open Weather.

![screen_shot_2018-06-08at144723](assets/screen_shot_2018-06-08at144723.png) ![screen_shot_2018-06-08at144215](assets/screen_shot_2018-06-08at144215.png)

Vérification du code du composant Météo personnalisé (`Weather.js`) dans l’application We.Retail Journal :

* **Ligne 16** : le widget React Open Weather est chargé comme désiré.
* **Ligne 46** : la fonction `MapTo` associe ce composant React à un composant AEM correspondant afin qu’il puisse être modifié dans l’éditeur de SPA.

* **Lignes 22 à 29** : `EditConfig` est défini, en vérifiant si la ville a été renseignée et en définissant la valeur si elle est vide.

* **Lignes 31 à 44** : le composant Météo étend la classe `Component` et fournit les données requises telles que définies dans la documentation d’utilisation du NPM pour le composant React Open Weather, et effectue le rendu du composant.

```javascript
/*~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
 ~ Copyright 2018 Adobe Systems Incorporated
 ~
 ~ Licensed under the Apache License, Version 2.0 (the "License");
 ~ you may not use this file except in compliance with the License.
 ~ You may obtain a copy of the License at
 ~
 ~     https://www.apache.org/licenses/LICENSE-2.0
 ~
 ~ Unless required by applicable law or agreed to in writing, software
 ~ distributed under the License is distributed on an "AS IS" BASIS,
 ~ WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
 ~ See the License for the specific language governing permissions and
 ~ limitations under the License.
 ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~*/
import React, {Component} from 'react';
import ReactWeather from 'react-open-weather';
import {MapTo} from '@adobe/aem-react-editable-components';

require('./Weather.css');

const WeatherEditConfig = {

    emptyLabel: 'Weather',

    isEmpty: function() {
        return !this.props || !this.props.cq_model || !this.props.cq_model.city || this.props.cq_model.city.trim().length < 1;
    }
};

class Weather extends Component {

    render() {
        let apiKey = "12345678901234567890";
        let city;

        if (this.props.cq_model) {
            city = this.props.cq_model.city;
            return <ReactWeather key={'react-weather' + Date.now()} forecast="today" apikey={apiKey} type="city" city={city} />
        }

        return null;
    }
}

MapTo('we-retail-journal/global/components/weather')(Weather, WeatherEditConfig);
```

Bien qu’un composant principal doive déjà exister, l’équipe de développement front-end peut exploiter le composant React Open Weather dans le SPA We.Retail Journal avec très peu de codage.

## Étape suivante {#next-step}

Pour plus d’informations sur le développement de SPA pour AEM, consultez l’article [Développement de SPA pour AEM](/help/sites-developing/spa-architecture.md).
