---
title: Créer un formulaire adaptatif à l’aide d’un jeu de formulaires adaptatifs
seo-title: Créer un formulaire adaptatif à l’aide d’un jeu de formulaires adaptatifs
description: 'Avec AEM Forms, regroupez les formulaires adaptatifs pour générer un seul grand formulaire adaptatif et explorez ses fonctionnalités. '
seo-description: 'Avec AEM Forms, regroupez les formulaires adaptatifs pour générer un seul grand formulaire adaptatif et explorez ses fonctionnalités. '
uuid: 1423038b-8261-455b-b4ff-7be7222448c9
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: develop
discoiquuid: 75ee94f7-e939-409b-b8cb-8fdc3f79bb63
feature: Formulaires adaptatifs
exl-id: 969b0c11-adc7-476e-8c82-d444fccba984
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '599'
ht-degree: 75%

---

# Créer un formulaire adaptatif à l’aide d’un jeu de formulaires adaptatifs {#create-an-adaptive-form-using-a-set-of-adaptive-forms}

## Présentation {#overview}

Dans un flux de travail tel qu’une demande d’ouverture de compte bancaire, vos utilisateurs remplissent plusieurs formulaires. Au lieu de leur demander de remplir un jeu de formulaires, vous pouvez empiler les formulaires et créer un grand formulaire (formulaire parent). Lorsque vous ajoutez un formulaire adaptatif au grand formulaire, il est ajouté sous la forme d’un panneau (formulaire enfant). Vous additionnez un jeu de formulaires enfants pour créer un formulaire parent. Vous pouvez afficher ou masquer les panneaux en fonction de l’entrée utilisateur. Les boutons du formulaire parent, tels que Envoyer et Réinitialiser, remplacent les boutons du formulaire enfant. Pour ajouter un formulaire adaptatif dans le formulaire parent, vous pouvez faire glisser et déposer le formulaire adaptatif depuis l’explorateur de ressources (comme des fragments de formulaire adaptatif).

Les fonctions disponibles sont :

* Création indépendante
* Affichage/Masquage des formulaires pertinents
* Chargement différé

Certaines fonctionnalités, telles que la création indépendante et le chargement différé, améliorent nettement les performances par rapport à l’utilisation de composants individuels pour créer le formulaire parent.

>[!NOTE]
>
>Vous ne pouvez pas utiliser des formulaires ou des fragments adaptatifs basés sur XFA en tant que formulaires enfant ou parent.

## Arrière-plan {#behind-the-scenes}

Vous pouvez ajouter des formulaires et des fragments adaptatifs basés sur XSD dans le formulaire parent. La structure du formulaire parent est la même que celle d’un [formulaire adaptatif](/help/forms/using/prepopulate-adaptive-form-fields.md) courant. Lorsque vous ajoutez un formulaire adaptatif en tant que formulaire enfant, il est ajouté en tant que panneau dans le formulaire parent. Les données d’un formulaire enfant lié sont stockées sous la racine `data`de la section `afBoundData` du schéma XML du formulaire parent.

Par exemple, vos clients remplissent le formulaire de demande. Les deux premiers champs du formulaire sont le nom et l’identité. Son XML est :

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

Vous ajoutez un autre formulaire à la demande qui permet aux clients de remplir leur adresse professionnelle. Le schéma racine du formulaire enfant est`officeAddress` . Appliquez `bindref` `/application/officeAddress` ou `/officeAddress`. Si `bindref` n’est pas fourni, le formulaire enfant est ajouté comme sous-arborescence `officeAddress`. Voir le XML du formulaire ci-dessous :

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

Si vous insérez un autre formulaire qui permet à vos clients de fournir l&#39;adresse du domicile, appliquez `bindref` `/application/houseAddress or /houseAddress.`Le XML ressemble à ceci :

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

Si vous souhaitez conserver le même nom de sous-racine que la racine du schéma ( `Address`dans cet exemple), utilisez des bindrefs indexés.

Par exemple, appliquez des bindrefs `/application/address[1]` ou `/address[1]` et `/application/address[2]` ou `/address[2]`. Le XML du formulaire est :

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

Si le formulaire enfant n’est pas lié, ses données sont stockées sous la racine `data`de la section `afUnboundData` du schéma XML du formulaire parent.

Vous pouvez ajouter plusieurs fois un formulaire adaptatif en tant que formulaire enfant. Assurez-vous que le `bindRef` est modifié correctement, de sorte que chaque instance utilisée du formulaire adaptatif pointe vers une sous-racine différente sous les données racines.

>[!NOTE]
>
>Si des formulaires ou des fragments différents sont associés à la même sous-racine, les données sont remplacées.

## Ajouter un formulaire adaptatif en tant que formulaire enfant à l’aide de l’explorateur de ressources  {#adding-an-adaptive-form-as-a-child-form-using-asset-browser}

Effectuez les étapes suivantes pour ajouter un formulaire adaptatif en tant que formulaire enfant à l’aide de l’explorateur de ressources.

1. Ouvrez le formulaire parent en mode de modification.
1. Dans la barre latérale, cliquez sur **Ressources** ![assets-browser](assets/assets-browser.png). Sous Ressources, sélectionner **Formulaire adaptatif** dans la liste déroulante.
   [ ![Sélection d’un formulaire adaptatif dans Ressources](assets/asset.png)](assets/asset-1.png)

1. Glissez et déposez le formulaire adaptatif que vous souhaitez ajouter en tant que formulaire enfant.
   [ ![Faites glisser et déposez le formulaire adaptatif dans votre ](assets/drag-drop.png)](assets/drag-drop-1.png)site. Le formulaire adaptatif que vous déposez est ajouté en tant que formulaire enfant.
