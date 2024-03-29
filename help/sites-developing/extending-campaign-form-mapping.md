---
title: Créer des mappages de formulaires personnalisés
seo-title: Creating Custom Form Mappings
description: Lorsque vous créez un tableau personnalisé dans Adobe Campaign, vous souhaiterez peut-être créer un formulaire dans AEM qui correspond à ce tableau personnalisé.
seo-description: When you create a custom table in Adobe Campaign, you may want to build a form in AEM that maps to that custom table
uuid: f3bde513-6edb-4eb6-9048-40045ee08c4a
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: extending-aem
content-type: reference
discoiquuid: d5dac1db-2dde-4b75-a31b-e057b447f6e2
exl-id: 3270a279-13ef-4bbf-aafe-539df388c652
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '566'
ht-degree: 15%

---

# Créer des mappages de formulaires personnalisés{#creating-custom-form-mappings}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Lorsque vous créez un tableau personnalisé dans Adobe Campaign, vous souhaiterez peut-être créer un formulaire dans AEM mappé à ce tableau personnalisé.

Ce document décrit comment créer des mappages de formulaire personnalisés. Lorsque vous aurez terminé les étapes de ce document, vous fournirez à vos utilisateurs une page d’événement dans laquelle ils pourront s’inscrire pour un événement à venir. Vous suivez ensuite ces utilisateurs via Adobe Campaign.

## Prérequis {#prerequisites}

Les éléments suivants doivent être installés :

* Adobe Experience Manager
* Adobe Campaign Classic

Pour plus d’informations, consultez [Intégration d’AEM à Adobe Campaign Classic](/help/sites-administering/campaignonpremise.md).

## Créer des mappages de formulaires personnalisés {#creating-custom-form-mappings-2}

Pour créer des mappages de formulaire personnalisés, vous devez suivre les étapes de haut niveau décrites en détail dans les sections suivantes :

1. Créez un tableau personnalisé.
1. Étendre le **seed** table.
1. Créez un mappage personnalisé.
1. Créez une diffusion basée sur le mapping personnalisé.
1. Créez le formulaire dans AEM, qui utilisera la diffusion créée.
1. Envoyez le formulaire pour le tester.

### Création d’un tableau personnalisé dans Adobe Campaign {#creating-the-custom-table-in-adobe-campaign}

Commencez par créer un tableau personnalisé dans Adobe Campaign. Dans cet exemple, nous allons utiliser la définition suivante pour créer un tableau d’événements :

```xml
<element autopk="true" label="Event" labelSingular="Event" name="event">
 <attribute label="Event Date" name="eventdate" type="date"/>
 <attribute label="Event Name" name="eventname" type="string"/>
 <attribute label="Email" name="email" type="string"/>
 <attribute label="Number of Seats" name="seats" type="long"/>
</element>
```

Après avoir créé le tableau d’événements, exécutez le **Assistant Mise à jour de la structure de la base de données** pour créer le tableau.

### Extension de la table de contrôle {#extending-the-seed-table}

Dans Adobe Campaign, appuyez/cliquez sur **Ajouter** pour créer une extension de la fonction **Adresses de contrôle (nms)** table.

![chlimage_1-194](assets/chlimage_1-194.png)

Utilisez à présent les champs du tableau d’**événement** pour étendre le tableau **source** :

```xml
<element label="Event" name="custom_cus_event">
 <attribute name="eventname" template="cus:event:event/@eventname"/>
 <attribute name="eventdate" template="cus:event:event/@eventdate"/>
 <attribute name="email" template="cus:event:event/@email"/>
 <attribute name="seats" template="cus:event:event/@seats"/>
 </element>
```

Ensuite, exécutez **Assistant Mise à jour de base de données** pour appliquer les modifications.

### Création d’un mapping de ciblage personnalisé {#creating-custom-target-mapping}

Dans **Administration/Gestion de campagne** t, accédez à **Mappages de Target** et ajouter un nouveau T **Mappage de ciblage.**

>[!NOTE]
>
>Veillez à utiliser un nom significatif pour **Nom interne**.

![chlimage_1-195](assets/chlimage_1-195.png)

### Création d’un modèle de diffusion personnalisé {#creating-a-custom-delivery-template}

Dans cette étape, vous ajoutez un modèle de diffusion qui utilise le modèle créé **Mapping de ciblage**.

Dans **Ressources/Modèles**, accédez au Modèle de diffusion et dupliquez la diffusion AEM existante. Lorsque vous cliquez sur **À**, sélectionnez l’événement de création **Mapping de ciblage**.

![chlimage_1-196](assets/chlimage_1-196.png)

### Création du formulaire dans AEM {#building-the-form-in-aem}

Dans AEM, assurez-vous d’avoir configuré un Cloud Service dans **Propriétés de la page**.

Ensuite, dans la variable **Adobe Campaign** , sélectionnez la diffusion qui a été créée dans [Création d’un modèle de diffusion personnalisé](#creating-a-custom-delivery-template).

![chlimage_1-197](assets/chlimage_1-197.png)

Lors de la configuration des champs, veillez à spécifier des noms d’élément uniques pour les champs de formulaire.

Une fois les champs configurés, vous devez modifier manuellement le mappage.

Dans CRXDE-lite, accédez au **jcr:content** (de la page) et modifiez le noeud **acMapping** par le nom interne de la propriété **Mapping de ciblage**.

![chlimage_1-198](assets/chlimage_1-198.png)

Dans la configuration du formulaire, veillez à cocher la case « Créer s’il n’existe pas ».

![chlimage_1-199](assets/chlimage_1-199.png)

### Envoi du formulaire {#submitting-the-form}

Vous pouvez désormais envoyer le formulaire et valider, du côté Adobe Campaign, l’enregistrement des valeurs.

![chlimage_1-200](assets/chlimage_1-200.png)

## Résolution des problèmes {#troubleshooting}

**&quot;Type non valide pour la valeur &#39;02/02/2015&#39; de l&#39;élément &#39;@eventdate&#39; (document de type &#39;Événement&#39; ([adb:event])&#39;)&quot;)&quot;**

Lors de l’envoi du formulaire, cette erreur est consignée dans la variable **error.log** dans AEM.

Cela est dû à un format non valide pour le champ de date. La solution consiste à fournir **aaaa-mm-jj** comme valeur.
