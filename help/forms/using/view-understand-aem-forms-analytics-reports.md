---
title: Consulter et comprendre les rapports d’analyse d’AEM Forms
seo-title: View and understand AEM Forms analytics reports
description: AEM Forms s’intègre à Adobe Analytics et fournit des analyses résumées et détaillées sur vos formulaires adaptatifs publiés.
seo-description: AEM Forms integrates with Adobe Analytics and provides you summary and detailed analytics about your published adaptive forms.
uuid: 193f472d-4aa3-4c31-b3c7-b5a2957dfb3d
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/FORMS
topic-tags: integrations
discoiquuid: a9045816-cae7-42cf-a734-6c3a25d0f522
exl-id: 0483b6ed-676a-4272-a00e-23d53a979b07
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '1086'
ht-degree: 45%

---

# Consulter et comprendre les rapports d’analyse d’AEM Forms {#view-and-understand-aem-forms-analytics-reports}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Adobe Experience Manager Forms s’intègre à Adobe Analytics, ce qui permet la capture et le suivi des mesures de performances des formulaires et des documents que vous avez publiés. L’analyse de ces mesures contribue à une prise de décisions éclairée fondée sur les données, eu égard aux modifications requises pour concevoir des formulaires ou des documents plus faciles à utiliser.

## Configuration des analyses {#setting-up-analytics}

La fonctionnalité d’analyse d’AEM Forms est disponible dans le package complémentaire d’AEM Forms. Pour plus d’informations sur l’installation du module complémentaire, voir [Installation et configuration d’AEM Forms](/help/forms/using/installing-configuring-aem-forms-osgi.md).

Outre le module complémentaire, vous avez besoin d’un compte Adobe Analytics. Pour plus d’informations sur la solution, voir [Adobe Analytics](https://www.adobe.com/fr/solutions/digital-analytics.html).

Une fois que vous disposez du module complémentaire AEM Forms et d’un compte Adobe Analytics, intégrez le compte Adobe Analytics à AEM Forms et activez le suivi sur vos formulaires ou documents, comme décrit à la section [Configuration des analyses et des rapports](/help/forms/using/configure-analytics-forms-documents.md).

## Enregistrement des informations sur l’interaction utilisateur {#how-user-interaction-information-is-recorded}

Lorsqu’un utilisateur interagit avec le formulaire, les interactions sont enregistrées et envoyées au serveur Analytics. La liste suivante indique les appels au serveur pour diverses activités utilisateur :

* 2 appels par champ par visite
* 1 pour la visite de panneau
* 1 pour l’enregistrement
* 2 pour envoi
* 2 pour l’enregistrement
* 1 pour obtenir de l’aide
* 1 pour chaque erreur de validation
* 1 pour le rendu de formulaire + 1 pour la visite de panneau par défaut + 1 pour la première visite de champ par défaut
* 2 pour l’abandon de formulaire

>[!NOTE]
>
>Cette liste n&#39;est pas exhaustive.

## Affichage des rapports d’analyse {#summary-report}

Pour afficher les rapports d’analyse, procédez comme suit :

1. Connectez-vous au portail AEM à l’adresse `https://[hostname]:[port]`
1. Cliquez sur **Formulaires > Formulaires &amp; Documents**.

1. Sélectionnez le formulaire pour lequel vous souhaitez afficher les rapports d’analyse.
1. Sélectionnez **Plus > Rapports Analytics**.

![analyticsreport](assets/analyticsreport.png)

**A.** Commande de rapport d’analyse

AEM Forms affiche des rapports d’analyse pour le formulaire et chaque panneau de celui-ci, comme illustré dans le rapport de synthèse ci-dessous.

![Rapport de synthèse d’un formulaire adaptatif](assets/analyticsdashboard_callout.png)

**A.** Conversions **B.** Synthèse de niveau formulaire **C.** Synthèse de niveau panneau **D.** Navigateurs des visiteurs - filtre **E.** Système d’exploitation des visiteurs - filtre **F.** Langue des visiteurs - filtre

Par défaut, le rapport d’analyse des sept derniers jours s’affiche. Vous pouvez afficher des rapports pour les 15 derniers jours, le dernier mois, etc., ou spécifier une période.

>[!NOTE]
>
>Les options telles que 7 derniers jours et 15 derniers jours n’incluent pas de données pour le jour où vous générez le rapport d’analyse. Pour inclure les données du jour actuel, vous devez spécifier la période incluant le jour actuel, puis exécuter le rapport.

![date-range](assets/date-range.png)

## Graphique de conversions pour les formulaires adaptatifs et de HTML5 {#conversions-graph-for-adaptive-and-html-forms}

Le graphique de conversions au niveau du formulaire vous donne un aperçu des performances du formulaire par le biais des indicateurs de performances clés (IPC) suivants :

* **Rendus**: Nombre d’ouvertures d’un formulaire
* **Visiteurs**: Nombre de visiteurs dans le formulaire
* **Envois**: Nombre de fois où le formulaire est envoyé

![conversion-graph](assets/conversion-graph.png)

## Rapport d’analyse pour les formulaires adaptatifs et de HTML5 {#analytics-report-for-adaptive-and-html-forms}

La section de synthèse de niveau formulaire donne des informations sur les performances du formulaire à l’aide des indicateurs de performances clés (IPC) suivants :

* **Durée moyenne de remplissage** : temps moyen passé au remplissage du formulaire. Lorsque les utilisateurs passent du temps sur le formulaire sans toutefois l’envoyer, ce temps n’est pas inclus dans le calcul.
* **Rendus** : nombre de fois que le formulaire a été affiché ou ouvert.

* **Brouillons**: Nombre de fois où le formulaire a été enregistré en tant que brouillon
* **Envois**: Nombre de fois où le formulaire a été envoyé
* **Abandonner**: Nombre de fois où les utilisateurs ont commencé à remplir le formulaire, puis l’ont quitté sans le compléter
* **Visiteurs uniques :** nombre de fois que le formulaire est généré par des visiteurs uniques. Pour plus d’informations sur les visiteurs uniques, voir [Visiteurs uniques, visites et comportement des clients](https://helpx.adobe.com/fr/analytics/kb/unique-visitors-visitor-behavior.html). 

![Rapport d’analyse de synthèse de niveau formulaire développé](assets/analytics-report.png)

## Rapport Panneau {#bottom-summary-report}

La section de résumé au niveau du panneau fournit les informations suivantes sur chaque panneau du formulaire :

* **Durée moyenne de remplissage** : temps moyen passé au remplissage du panneau, que le formulaire soit soumis ou non

* **Erreurs rencontrées** : nombre moyen d’erreurs rencontrées par les utilisateurs sur des champs d’un panneau. La valeur Erreurs rencontrées est calculée en divisant le nombre total d’erreurs rencontrées dans un champ par le nombre de rendus du formulaire.

* **Aide accessible** : nombre moyen de fois qu’un utilisateur a accédé à l’aide contextuelle pour les champs du panneau. La valeur Aide accessible est calculée en divisant le nombre total d’accès à l’aide pour un champ par le nombre de rendus du formulaire.

### Rapport détaillé de panneau {#detailed-panel-report}

Vous pouvez également afficher les détails de chaque panneau en cliquant sur le nom d’un panneau dans le rapport Panneau.

![Rapport détaillé de panneau](assets/panel-report-detailed.png)

Le rapport détaillé affiche les valeurs de tous les champs du panneau.

Le rapport Panneau comporte trois onglets :

* **Rapport de temps** (par défaut) : affiche le temps, en nombre de secondes, passé à remplir chacun des champs du panneau.
* **Rapport d’erreurs** : nombre d’erreurs générées par les utilisateurs qui remplissent les champs
* **Rapport sur l’aide** : nombre de fois que l’aide d’un champ en particulier a été affiché

Vous pouvez naviguer entre les panneaux, si plusieurs panneaux sont disponibles. 

### Filtres : Navigateur, système d’exploitation et langue {#filters-browser-os-and-language}

Les tableaux Répartition de navigateur, Répartition du système d’exploitation et Répartition des langues affichent les rendus, les visiteurs et les envois selon les navigateurs, le système d’exploitation et la langue des utilisateurs de formulaire. Par défaut, ces tableaux affichent cinq entrées au maximum. Vous pouvez cliquer sur Afficher plus pour afficher plus d’entrées, puis sur Afficher moins pour revenir aux cinq entrées normales ou moins.

Pour filtrer davantage les données d’analyse, vous pouvez cliquer sur une entrée dans l’un des tableaux. Par exemple, si vous cliquez sur Google Chrome dans le tableau de distribution du navigateur, le rapport est rendu avec les données relatives au navigateur Google Chrome, comme suit :

![Filtre appliqué au Rapport d’analyse - Google Chrome ](assets/filter.png)

Si vous consultez le rapport Panneau après l’application d’un filtre, les données des rapports sont également affichées selon le filtre appliqué.

Lorsqu’un filtre est appliqué :

* Les tableaux de distribution deviennent en lecture seule, car un seul filtre peut être appliqué à la fois.
* Le tableau du filtre appliqué disparaît.
* Vous pouvez cliquer sur le bouton Fermer (mis en surbrillance ci-dessous) pour supprimer le filtre appliqué.

![Bouton Fermer supprimant le filtre appliqué](assets/close-filter.png)

## Tests A/B {#a-b-testing}

Si le test A/B est activé et configuré pour le formulaire, la page du rapport comporte une liste déroulante que vous pouvez utiliser pour afficher le rapport de test A/B. Le rapport de test A/B affiche la performances comparatives deux versions du formulaire que vous avez définis.

Pour plus d’informations sur les tests A/B, voir [Création et gestion des tests A/B pour les formulaires adaptatifs](/help/forms/using/ab-testing-adaptive-forms.md).
