---
title: Création du modèle de page AEM personnalisé avec des composants de formulaire Adobe Campaign
seo-title: Creating Custom AEM Page Template with Adobe Campaign Form Components
description: Créez un modèle de page personnalisé qui utilise des composants de formulaire Adobe Campaign.
seo-description: Build a custom page template that uses Adobe Campaign Form components
uuid: 8162ace2-b661-4c39-b0fb-288e1c035b9c
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: extending-aem
content-type: reference
discoiquuid: c3f6eed4-bbda-454a-88ce-c7f2041d4217
exl-id: e70c9d23-5a4d-4137-82ad-3f3237f468c0
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 55%

---

# Création du modèle de page AEM personnalisé avec des composants de formulaire Adobe Campaign{#creating-custom-aem-page-template-with-adobe-campaign-form-components}

Cette page explique comment créer un modèle de page personnalisé qui utilise [Formulaire Adobe Campaign](/help/sites-authoring/adobe-campaign-components.md) composants en examinant la manière dont le modèle de Geometrixx-plein ( `/apps/geometrixx-outdoors/components/page_campaign_profile`) est implémenté et vous indique les informations importantes dont vous avez besoin lors de la création de votre propre modèle personnalisé.

>[!NOTE]
>
>[Les exemples de courrier électronique et de formulaire sont disponibles uniquement dans Geometrixx](/help/sites-developing/we-retail.md). Téléchargez un exemple de contenu Geometrixx à partir de Package Share.

Pour créer un modèle de page AEM personnalisé à l’aide de composants de formulaire Adobe Campaign, vérifiez que vous disposez des éléments suivants :

1. **resourceSuperType correct**

   Assurez-vous que le composant de page hérite de `mcm/campaign/components/profile`.

   Cela est nécessaire pour que les servlets obtiennent et enregistrent des informations.

   * `com.day.cq.mcm.campaign.servlets.TemplateListServlet`
   * `com.day.cq.mcm.campaign.servlets.SaveProfileServlet`

   ![chlimage_1-201](assets/chlimage_1-201.png)

1. **Paramètres de ClientContext**

   Lorsque vous examinez les paramètres de ClientContext ( `/etc/designs/geometrixx-outdoors/jcr:content/page_campaign_profile`) les paramètres suivants s’affichent :

   * Points de ClientContext vers `/etc/clientcontext/campaign`
   * Il existe également un nœud *config* supplémentaire.

   ![chlimage_1-202](assets/chlimage_1-202.png)

1. **head.jsp (/apps/geometrixx-outdoors/components/page_campaign_profile/head.jsp)**

   Dans le fichier **head.jsp**, vous voyez les lignes suivantes qui utilisent **clientcontext-config** et **cloudservice-hook** :

   ```
   <cq:include path="config" resourceType="cq/personalization/components/clientcontext_optimized/config"/>
   <sling:include path="contexthub" resourceType="granite/contexthub/components/contexthub"/>
   <cq:include script="/libs/cq/cloudserviceconfigs/components/servicelibs/servicelibs.jsp"/>
   ```

1. **body.jsp (/apps/geometrixx-outdoors/components/page_campaign_profile/body.jsp)**

   Dans **body.jsp**, les services cloud sont chargés au bas de la page :

   ```
   <cq:include path="cloudservices" resourceType="cq/cloudserviceconfigs/components/servicecomponents"/>
   ```

1. **Propriétés de la page de campagne**

   Pour pouvoir sélectionner un modèle Adobe Campaign, les propriétés de page sont étendues avec l’onglet **Campagne** :

   `/apps/geometrixx-outdoors/components/page_campaign_profile/dialog/items/tabs/items/campaign`

   ![chlimage_1-203](assets/chlimage_1-203.png)

1. **Paramètres de modèle**.

   Dans le modèle ( `/apps/geometrixx-outdoors/templates/campaign_profile/jcr:content`) les valeurs par défaut suivantes s’affichent :

   | **acMapping** | mapRecipient (pour Adobe Campaign 6.1), profile (pour Adobe Campaign Standard) |
   |---|---|
   | **acTemplateId** | mail |

   ![chlimage_1-204](assets/chlimage_1-204.png)
