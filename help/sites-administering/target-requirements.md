---
title: Conditions préalables à l’intégration à Adobe Target
seo-title: Prerequisites for Integrating with Adobe Target
description: Découvrez les conditions préalables à l’intégration à Adobe Target.
seo-description: Find out about the prerequisites for integrating with Adobe Target.
uuid: 88be6a97-c964-4e42-a3a2-ed9b2c9ee49e
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: integration
content-type: reference
discoiquuid: a84fd0ab-0bcd-48cf-bba3-fb29308fa0f8
exl-id: f47e5c6a-ed52-4493-83bd-73e5e693d117
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '558'
ht-degree: 66%

---

# Conditions préalables à l’intégration à Adobe Target{#prerequisites-for-integrating-with-adobe-target}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Dans le cadre de l’[intégration d’AEM et Adobe Target](/help/sites-administering/target.md), vous devez vous inscrire à Adobe Target, configurer l’agent de réplication et sécuriser les paramètres d’activité sur le nœud de publication.

## Enregistrement auprès d’Adobe Target {#registering-with-adobe-target}

Pour intégrer AEM à Adobe Target, vous devez disposer d’un compte Adobe Target valide. Ce compte doit disposer au minimum des autorisations de niveau **approbateur **. Lorsque vous vous inscrivez à Adobe Target, vous recevez un code client. Vous avez besoin du code client ainsi que de votre nom d’utilisateur et de votre mot de passe Adobe Target pour vous connecter AEM à Adobe Target.

Le code client identifie le compte client Adobe Target lors de l’appel du serveur Adobe Target.

>[!NOTE]
>
>Votre compte doit également être activé par l’équipe Target pour pouvoir utiliser l’intégration.
>
>
>Si ce n&#39;est pas le cas, veuillez contacter [Assistance clientèle d’Adobe Target](https://experienceleague.adobe.com/docs/target/using/cmp-resources-and-contact-information.html?lang=fr).

## Activation de l’agent de réplication Target {#enabling-the-target-replication-agent}

L’[agent de réplication](/help/sites-deploying/replication.md) Test&amp;Target doit être activé sur l’instance de création. Notez que cet agent de réplication n’est pas activé par défaut si vous utilisez le mode d’exécution [nosamplecontent](/help/sites-deploying/configure-runmodes.md#using-samplecontent-and-nosamplecontent) pour installer AEM. Pour plus d’informations sur la sécurisation de votre environnement de production, voir [Liste de contrôle de sécurité](/help/sites-administering/security-checklist.md).

1. Sur la page d’accueil AEM, cliquez ou appuyez sur **Outils** > **Déploiement** > **Réplication**.
1. Cliquez ou appuyez sur **Agents sur l’auteur**.
1. Cliquez ou appuyez sur **Test et cible (test et cible)** agent de réplication, puis cliquez ou appuyez sur **Modifier**.
1. Sélectionnez l’option Activé , puis cliquez ou appuyez sur **OK**.

   >[!NOTE]
   >
   >Lorsque vous configurez l’agent de réplication Test&amp;Target, sous l’onglet **transport**, l’URI est défini par défaut sur **tnt:///**. Ne remplacez pas cet URI par **https://admin.testandtarget.omniture.com**.
   >
   >Veuillez noter que si vous tentez de tester la connexion avec **tnt:///**, elle renvoie une erreur. Ce comportement est prévu, car cet URI est destiné à un usage interne uniquement et ne doit pas être utilisé avec **Tester la connexion**.

## Sécurisation du nœud de paramètres d’activité {#securing-the-activity-settings-node}

Vous devez sécuriser le nœud de paramètres d’activité **c:ActivitySettings** sur l’instance de publication de sorte qu’il ne soit pas accessible pour les utilisateurs normaux. Le nœud de paramètres d’activité doit être accessible uniquement au service gérant la synchronisation de l’activité avec Adobe Target.

Le nœud **cq:ActivitySettings** est disponible dans CRXDE Lite sous `/content/campaigns/*nameofbrand*`/*sous le nœud jcr:content des activités,* par exemple `/content/campaign/we-retail/master/myactivity/jcr:content/cq:ActivitySettings`. Ce nœud est créé après que vous ciblez un composant.

Le nœud **cq:ActivitySettings** sous le nœud jcr:content de l’activité est protégé par les listes ACL suivantes :

* Refuser tout pour tous
* Autoriser jcr:read,rep:write pour &quot;target-activity-authors&quot; (l’auteur est membre de ce groupe prêt à l’emploi)
* Autoriser jcr:read,rep:write pour &quot;targetservice&quot;

Ces paramètres permettent de garantir que les utilisateurs ordinaires n’ont pas accès aux propriétés de nœud. Utilisez les mêmes listes ACL sur les instances de création et de publication. Consultez la section [Administration et sécurité des utilisateurs](/help/sites-administering/security.md) pour plus d’informations.

## Configuration de l’externaliseur AEM {#configuring-the-aem-externalizer}

Lors de la modification d’une activité dans Adobe Target, l’URL pointe sur **localhost**, à moins que vous ne modifiiez l’URL sur le nœud de création AEM.

Pour configurer l’externaliseur AEM, procédez comme suit :

1. Accédez à la console web OSGi : **https://&lt;server>:&lt;port>/system/console/configMgr.**
1. Recherchez **Externalisateur de lien Day CQ** et saisissez le domaine du nœud de création.

   ![chlimage_1-120](assets/chlimage_1-120.png)
