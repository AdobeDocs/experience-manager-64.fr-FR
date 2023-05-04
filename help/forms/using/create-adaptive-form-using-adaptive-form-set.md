---
title: Créer un formulaire adaptatif à l’aide d’un jeu de formulaires adaptatifs
seo-title: Create an adaptive form using a set of adaptive forms
description: Avec AEM Forms, rassemblez les formulaires adaptatifs pour créer un seul grand formulaire adaptatif et comprenez ses fonctionnalités.
seo-description: With AEM Forms, bring adaptive forms together to author a single large adaptive form, and understand its features.
uuid: 1423038b-8261-455b-b4ff-7be7222448c9
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: 75ee94f7-e939-409b-b8cb-8fdc3f79bb63
feature: Adaptive Forms
exl-id: 969b0c11-adc7-476e-8c82-d444fccba984
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '605'
ht-degree: 48%

---

# Créer un formulaire adaptatif à l’aide d’un jeu de formulaires adaptatifs {#create-an-adaptive-form-using-a-set-of-adaptive-forms}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

## Présentation {#overview}

Dans un processus, tel qu’une demande d’ouverture de compte bancaire, vos utilisateurs remplissent plusieurs formulaires. Au lieu de leur demander de remplir un ensemble de formulaires, vous pouvez empiler les formulaires et créer un formulaire volumineux (formulaire parent). Lorsque vous ajoutez un formulaire adaptatif au formulaire plus volumineux, il est ajouté sous la forme d’un panneau (formulaire enfant). Vous ajoutez un ensemble de formulaires enfants pour créer un formulaire parent. Vous pouvez afficher ou masquer les panneaux en fonction des entrées de l’utilisateur. Les boutons du formulaire parent, tels que l’envoi et la réinitialisation, remplacent les boutons du formulaire enfant. Pour ajouter un formulaire adaptatif dans le formulaire parent, vous pouvez faire glisser et déposer le formulaire adaptatif depuis l’explorateur de ressources (comme les fragments de formulaire adaptatif).

Les fonctions disponibles sont :

* Création indépendante
* Affichage/masquage des formulaires appropriés
* Chargement différé

Des fonctionnalités telles que la création indépendante et le chargement différé offrent des performances améliorées par rapport à l’utilisation de composants individuels pour créer le formulaire parent.

>[!NOTE]
>
>Vous ne pouvez pas utiliser de formulaires/fragments adaptatifs basés sur XFA en tant que formulaires enfants ou parents.

## En arrière-plan {#behind-the-scenes}

Vous pouvez ajouter des formulaires adaptatifs et des fragments XSD dans le formulaire parent. La structure du formulaire parent est la même que [n’importe quel formulaire adaptatif](/help/forms/using/prepopulate-adaptive-form-fields.md). Lorsque vous ajoutez un formulaire adaptatif en tant que formulaire enfant, il est ajouté sous la forme d’un panneau dans le formulaire parent. Les données d’un formulaire enfant lié sont stockées sous les données racines `data` de la section `afBoundData` du schéma XML du formulaire parent.

Par exemple, vos clients remplissent un formulaire de demande. Les deux premiers champs du formulaire sont le nom et l’identité. Son XML est :

```xml
<afData>
    <afUnboundData>
        <data />
    </afUnboundData>
    <afBoundData>
        <data xmlns:xfa="https://www.xfa.org/schema/xfa-data/1.0/">
            <applicantName>Sarah Rose</applicantName>
            <applicantId>1234</applicantId>
        </data>
    </afBoundData>
</afData>
```

Vous ajoutez un autre formulaire à la demande qui permet à vos clients de renseigner leur adresse professionnelle. Le schéma racine du formulaire enfant est `officeAddress`. Appliquez `bindref` `/application/officeAddress` ou `/officeAddress`. Si `bindref` n’est pas fourni, le formulaire enfant est ajouté comme sous-arborescence `officeAddress`. Examinez le XML du formulaire ci-dessous : 

```xml
<afData>
    <afUnboundData>
        <data />
    </afUnboundData>
    <afBoundData>
        <data xmlns:xfa="https://www.xfa.org/schema/xfa-data/1.0/">
            <applicantName>Sarah Rose</applicantName>
            <applicantId>1234</applicantId>
            <officeAddress>
                <addressLine>1, Geometrixx City</addressLine>
                <zip>11111</zip>
            </officeAddress>
        </data>
    </afBoundData>
</afData>
```

Si vous insérez un autre formulaire qui permet à vos clients de fournir une adresse, appliquez `bindref` `/application/houseAddress or /houseAddress.`. Le XML ressemble à ceci :

```xml
<afData>
    <afUnboundData>
        <data />
    </afUnboundData>
    <afBoundData>
        <data xmlns:xfa="https://www.xfa.org/schema/xfa-data/1.0/">
            <applicantName>Sarah Rose</applicantName>
            <applicantId>1234</applicantId>
            <officeAddress>
                <addressLine>1, Geometrixx City</addressLine>
                <zip>11111</zip>
            </officeAddress>
            <houseAddress>
                <addressLine>2, Geometrixx City</addressLine>
                <zip>11111</zip>
            </houseAddress>
        </data>
    </afBoundData>
</afData>
```

Si vous souhaitez conserver le même nom de sous-racine comme schéma racine (`Address` dans cet exemple), utilisez des bindrefs indexés.

Par exemple, vous pouvez appliquer les bindrefs `/application/address[1]` ou `/address[1]` et `/application/address[2]` ou `/address[2]`. Le XML du formulaire est :

```xml
<afData>
    <afUnboundData>
        <data />
    </afUnboundData>
    <afBoundData>
        <data xmlns:xfa="https://www.xfa.org/schema/xfa-data/1.0/">
            <applicantName>Sarah Rose</applicantName>
            <applicantId>1234</applicantId>
            <address>
                <addressLine>1, Geometrixx City</addressLine>
                <zip>11111</zip>
            </address>
            <address>
                <addressLine>2, Geometrixx City</addressLine>
                <zip>11111</zip>
            </address>
        </data>
    </afBoundData>
</afData>
```

Vous pouvez modifier la sous-arborescence par défaut du formulaire ou du fragment adaptatif à l’aide de la propriété `bindRef`. La propriété `bindRef` vous permet de spécifier le chemin qui pointe vers un emplacement dans l’arborescence du schéma XML.

Si le lien du formulaire enfant est annulé, ses données sont stockées sous les données racines `data` de la section `afUnboundData` du schéma XML du formulaire parent.

Vous pouvez ajouter plusieurs fois un formulaire adaptatif en tant que formulaire enfant. Assurez-vous que le `bindRef` est modifié correctement, de sorte que chaque instance utilisée du formulaire adaptatif pointe vers une sous-racine différente sous les données racines.

>[!NOTE]
>
>Si différents formulaires/fragments sont mappés à la même sous-racine, les données sont écrasées.

## Ajout d’un formulaire adaptatif en tant que formulaire enfant à l’aide de l’explorateur de ressources {#adding-an-adaptive-form-as-a-child-form-using-asset-browser}

Effectuez les étapes suivantes pour ajouter un formulaire adaptatif en tant que formulaire enfant à l’aide de l’explorateur de ressources.

1. Ouvrez le formulaire parent en mode d’édition.
1. Dans la barre latérale, cliquez sur **Ressources** ![assets-browser](assets/assets-browser.png). Sous Ressources, sélectionner **Formulaire adaptatif** dans la liste déroulante.
   [ ![Sélection d’un formulaire adaptatif dans Ressources](assets/asset.png)](assets/asset-1.png)

1. Glissez et déposez le formulaire adaptatif que vous souhaitez ajouter en tant que formulaire enfant.
   [ ![Faites glisser le formulaire adaptatif sur votre site](assets/drag-drop.png)](assets/drag-drop-1.png). Le formulaire adaptatif que vous déposez est ajouté en tant que formulaire enfant.
