---
title: Contrôler les événements
seo-title: Monitoring events
description: Lorsque la fonctionnalité de contrôle est activée, Document Security vous permet de surveiller certains types d’événements. Vous pouvez facilement rechercher et trier la liste des événements à l’aide de Document Security.
seo-description: When the auditing capability is enabled, document security enables you to monitor certain types of events. You can easily search and sort the events list using the document security.
uuid: 22add6ff-536d-4cb9-8eac-b72cad5c3ecf
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_document_security
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 379957bf-0634-4182-b269-1b010da4c90f
feature: Document Security
exl-id: 0c4a846f-4e31-435b-a6f6-d0b7c4cd1259
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '994'
ht-degree: 31%

---

# Contrôler les événements {#monitoring-events}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Lorsque la fonctionnalité de contrôle est activée, Document Security vous permet de surveiller certains types d’événements. Les événements visibles dépendent de votre rôle :

**Utilisateurs :** ils peuvent afficher les événements contrôlés sur leurs documents protégés par une stratégie, ainsi que sur les documents protégés qu’ils reçoivent et utilisent.

**Coordinateurs de jeux de stratégies :** ils peuvent afficher les événements contrôlés, notamment les événements de document et de stratégie, pour les documents protégés par des stratégies issues de leurs jeux de stratégies.

**Administrateurs :** ils peuvent afficher les événements contrôlés concernant tous les utilisateurs et documents protégés par une stratégie. Les administrateurs peuvent également effectuer le suivi d’autres types d’événements, y compris les événements d’utilisateur, de document, de stratégie et de système.

>[!NOTE]
>
>Les événements qui se produisent sur une copie d’un document protégé par une stratégie sont également suivis en tant qu’événements sur le document d’origine protégé.

(Voir [Options de contrôle des événements](/help/forms/using/admin-help/configuring-client-server-options.md#event-auditing-options).)

Un événement d’échec est enregistré si un utilisateur non autorisé tente d’afficher un document ou de se connecter à l’aide d’un nom d’utilisateur ou d’un mot de passe incorrect.

>[!NOTE]
>
>Les événements d’accès anonymes ayant échoué pour les documents peuvent être consignés si une stratégie est modifiée pour supprimer l’accès anonyme. Lorsqu’un destinataire autorisé tente d’accéder à un document protégé par la stratégie modifiée, la tentative d’accès anonyme est toujours en cours, mais échoue.

Si une stratégie autorise l’accès d’utilisateurs anonymes, mais que l’administrateur désactive ultérieurement l’accès anonyme pour Document Security, l’accès anonyme échoue pour les documents protégés par la stratégie et l’événement n’est pas consigné.

## Activation du contrôle des événements {#enable-event-auditing}

Ces exigences de configuration doivent être respectées pour que le contrôle des événements ait lieu :

* Le système ou l’administrateur doit activer la fonctionnalité de contrôle pour le serveur.

   (Voir [Configuration des paramètres de contrôle et de confidentialité des événements](/help/forms/using/admin-help/configuring-client-server-options.md#configuring-event-auditing-and-privacy-settings).)

* Le contrôle doit être activé pour la stratégie utilisée pour protéger le document. (Voir [Création et modification de stratégies](/help/forms/using/admin-help/creating-policies.md#creating-and-editing-policies).)

## Recherche d’un événement {#search-for-an-event}

Vous pouvez rechercher la liste des événements et afficher des descriptions plus détaillées sur les événements. Les descriptions détaillées incluent des informations telles que l’ID de l’événement, la description, l’adresse IP, l’organisation, l’utilisateur concerné, la date et l’heure auxquelles l’événement s’est produit, les activités refusées et les événements hors ligne (lorsque les utilisateurs tentent d’utiliser un document lorsqu’ils ne sont pas connectés à Document Security).

Vous pouvez rechercher des événements sur la page Événements à l’aide d’une combinaison de critères de recherche d’événements et de dates auxquelles les événements se sont produits. Les événements que vous pouvez rechercher dépendent de votre rôle :

**Utilisateurs :** ils peuvent afficher les événements contrôlés sur leurs documents protégés par une stratégie, ainsi que sur les documents protégés qu’ils reçoivent et utilisent. Les options de recherche disponibles sont les suivantes :

**Événements me
concernant :** les utilisateurs peuvent rechercher des événements concernant les documents protégés par une stratégie qu’ils ont créés ou reçus. Par exemple, si un utilisateur ouvre, affiche ou imprime un document qui était protégé par une autre personne, l’utilisateur ne voit que les événements concernant ce document.

**Événements liés à mes documents :** les utilisateurs peuvent rechercher tous les événements relatifs à leurs propres documents protégés par une stratégie. Les utilisateurs voient les événements générés par chaque personne ayant manipulé leurs documents.

**Coordinateurs de jeux de stratégies :** ils peuvent afficher les événements contrôlés (notamment les événements de document et de stratégie) pour les documents protégés par des stratégies issues de leurs jeux de stratégies. Voici les options de disponibles :

**Événements de document pour lesquels
je suis coordinateur de jeux de stratégies :** les coordinateurs de jeux de stratégies qui disposent de l’autorisation d’affichage des événements peuvent rechercher les événements liés aux documents protégés par des stratégies issues de leurs jeux de stratégies.

**Événements de stratégie pour lesquels je suis coordinateur de jeux de stratégies :** les coordinateurs de jeux de stratégies qui disposent de l’autorisation d’affichage des événements peuvent rechercher les événements liés aux stratégies issues de leurs jeux de stratégies.

**Administrateurs :** ils peuvent afficher les événements contrôlés concernant tous les utilisateurs et documents protégés par une stratégie. Les administrateurs peuvent également effectuer le suivi d’autres types. En outre, les administrateurs peuvent subdiviser davantage les recherches d’événements en fonction du type d’utilisateur :

**Utilisateurs connus :** utilisateurs se trouvant dans les répertoires sources ou enregistrés en tant qu’utilisateurs externes.

**Utilisateurs anonymes :** utilisateurs non identifiés qui accèdent à un document protégé par une stratégie autorisant un accès anonyme.

**Utilisateurs système :** événements déclenchés par le serveur, comme la synchronisation d’un répertoire.

1. Dans la page Document Security, cliquez sur Événements.
1. Dans la liste Rechercher, sélectionnez les critères de recherche à utiliser. En fonction de votre sélection dans la liste Rechercher, une deuxième liste s’affiche, fournissant des critères de recherche supplémentaires. Le cas échéant, saisissez les critères de recherche dans la zone de texte.

   Pour plus d’informations sur les types d’événement spécifiques, voir [Options de contrôle des événements](/help/forms/using/admin-help/configuring-client-server-options.md#event-auditing-options).

1. Dans la liste Utilisateur , sélectionnez le type d’utilisateur qui a exécuté l’événement :

   * Si vous sélectionnez Utilisateur connu, une seconde zone de recherche s’affiche, dans laquelle vous devez saisir le nom ou l’adresse électronique de l’utilisateur.
   * Si vous ne connaissez pas ces valeurs, cliquez sur l’icône de recherche du carnet d’adresses pour rechercher l’utilisateur par nom d’utilisateur ou adresse électronique.

1. Dans la liste Date, sélectionnez une option de période. Si vous sélectionnez Dates personnalisées, des zones s’affichent, dans lesquelles vous saisissez la date au format aaaa/mm/jj. Vous pouvez également utiliser le sélecteur de date pour spécifier la période :

   * Cliquez sur le calendrier pour ouvrir le sélecteur de date.
   * Utilisez les flèches pour trouver un an et un mois.
   * Cliquez sur un jour du mois dans le calendrier.
   * Cliquez sur OK pour fermer le sélecteur de date.

1. Dans la liste Afficher, sélectionnez le nombre de résultats de recherche à afficher par page.
1. Cliquez sur Rechercher.

   Tous les événements ayant échoué sont mis en surbrillance dans la liste avec une icône de refus.

1. Pour afficher les détails sur un événement, cliquez sur la description de l’événement dans la liste.

## Tri de la liste des événements {#sort-the-event-list}

Vous pouvez trier la liste des événements par en-tête de colonne pour trouver plus facilement les événements. Les icônes en forme de triangle en regard de l’en-tête de colonne indiquent la colonne à trier. Un triangle orienté vers le haut indique l’ordre croissant, tandis qu’un triangle orienté vers le bas indique l’ordre décroissant.

1. Cliquez sur l’en-tête de colonne approprié.
1. Pour modifier l’ordre de tri, cliquez de nouveau sur l’en-tête de colonne.
