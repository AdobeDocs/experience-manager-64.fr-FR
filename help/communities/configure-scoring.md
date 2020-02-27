---
title: Scores et insignes essentiels
seo-title: Scores et insignes essentiels
description: Présentation de la fonctionnalité Scores et badges
seo-description: Présentation de la fonctionnalité Scores et badges
uuid: 858ca54f-b416-445d-a449-cef7eed33926
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.4/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: ddb86546-d04b-4967-937b-50a19b0237a0
translation-type: tm+mt
source-git-commit: 8c66f2b0053882bd1c998d8e01dbb0573881bc87

---


# Scores et insignes essentiels {#scoring-and-badges-essentials}

La fonction de notation et de badges des communautés AEM permet d’identifier et de récompenser les membres de la communauté.

Les détails de la configuration de la fonctionnalité sont décrits dans la section

* [Score et badges des communautés](implementing-scoring.md)

Cette page contient des informations techniques supplémentaires :

* Comment [afficher un badge](#displaying-badges) sous forme d’image ou de texte
* Comment activer la journalisation [de débogage étendue](#debug-log-for-scoring-and-badging)
* Comment [accéder à l&#39;UGC](#ugc-for-scoring-and-badging) en rapport avec la notation et le badge

>[!CAUTION]
>
>La structure d’implémentation visible dans CRXDE Lite peut être modifiée.

## Affichage des badges {#displaying-badges}

Le contrôle d’un badge affiché sous forme de texte ou d’image côté client dans le modèle HBS est activé.

Par exemple, recherchez `this.isAssigned` dans `/libs/social/forum/components/hbs/topic/list-item.hbs`:

```
{{#each author.badges}}

  {{#if this.isAssigned}}

    <div class="scf-badge-text">

      {{this.title}}

    </div>

  {{/if}}

{{/each}}

{{#each author.badges}}

  {{#unless this.isAssigned}}

    <img class="scf-badge-image" alt="{{this.title}}" title="{{this.title}}" src="{{this.imageUrl}}" />

  {{/unless}}

{{/each}}
```

Si la valeur est true, isAssigned indique que le badge a été affecté à un rôle et que le badge doit être affiché sous forme de texte.

Si la valeur est false, est Attribué indique que le badge a été attribué pour un score gagné et que le badge doit être affiché sous forme d’image.

Toute modification de ce comportement doit être apportée dans un script personnalisé (remplacement ou recouvrement). Voir Personnalisation [côté](client-customize.md)client.

## Journal de débogage pour le score et le badge {#debug-log-for-scoring-and-badging}

Pour faciliter le débogage du score et du badge, vous pouvez configurer un fichier journal personnalisé. Le contenu de ce fichier journal peut alors être fourni au service clientèle en cas de problème avec la fonctionnalité.

Pour obtenir des instructions détaillées, consultez [Création d’un fichier](../../help/sites-deploying/monitoring-and-maintaining.md#create-a-custom-log-file)journal personnalisé.

Pour configurer rapidement un fichier journal en ligne :

1. Accédez à la prise en charge **[!UICONTROL du journal de la console Web]** Adobe Experience Manager, par exemple

   * http://localhost:4502/system/console/slinglog

1. Sélectionner **[!UICONTROL Ajouter un nouveau journal]**

   1. Sélectionner `DEBUG` pour le niveau **[!UICONTROL journal]**
   1. Entrez un nom pour le fichier **** journal, par exemple

      * logs/scoring-debug.log
   1. Entrez deux entrées **[!UICONTROL de journal]** (classe) (à l’aide de l’ `+` icône)

      * `com.adobe.cq.social.scoring`
      * `com.adobe.cq.social.badging`
   1. Sélectionnez **[!UICONTROL Enregistrer]**



![chlimage_1-248](assets/chlimage_1-248.png)

Pour afficher les entrées de journal :

* Depuis la console Web

   * Sous le menu **[!UICONTROL État]**
   * Sélectionner les fichiers **[!UICONTROL journaux]**
   * Recherchez le nom du fichier journal, tel que `scoring-debug`

* Sur le disque local du serveur

   * Le fichier journal se trouve sous &lt;*server-install-dir*>/crx-quickstart/logs/&lt;*log-file-name*>.log
   * Par exemple, `.../crx-quickstart/logs/scoring-debug.log`

![chlimage_1-249](assets/chlimage_1-249.png)

## UGC pour le score et le badge {#ugc-for-scoring-and-badging}

Il est possible d’afficher l’UGC en ce qui concerne la notation et la notation lorsque le SRP choisi est JSRP ou MSRP, mais pas ASRP. (Si vous ne connaissez pas ces termes, consultez Présentation [du fournisseur de ressources de stockage](working-with-srp.md) et de [stockage de contenu de la](srp.md)communauté.)

Les descriptions d’accès aux données de score et de badge utilisent JSRP, car l’UGC est facilement accessible à l’aide de [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md).

**JSRP sur l&#39;auteur**: l’expérimentation dans l’environnement d’auteur entraîne l’affichage de l’UGC uniquement à partir de l’environnement d’auteur.

**JSRP sur publication**: de même, si vous effectuez des tests sur l’environnement de publication, il sera nécessaire d’accéder à CRXDE Lite avec des droits d’administrateur sur une instance de publication. Si l’instance de publication s’exécute en mode [de](../../help/sites-administering/production-ready.md) production (mode d’exécution nosamplecontent), il sera nécessaire d’ [activer CRXDE Lite](../../help/sites-administering/enabling-crxde-lite.md).

L’emplacement de base de l’UGC sur JSRP est `/content/usergenerated/asi/jcr/`.

### API de score et de badge {#scoring-and-badging-apis}

Les API suivantes peuvent être utilisées :

* [com.adobe.cq.social.scoring.api](https://docs.adobe.com/content/docs/en/aem/6-3/develop/ref/javadoc/com/adobe/cq/social/scoring/api/package-summary.html)
* [com.adobe.cq.social.badging.api](https://docs.adobe.com/content/docs/en/aem/6-3/develop/ref/javadoc/com/adobe/cq/social/badging/api/package-summary.html)

Les derniers Javadocs pour les [versions](deploy-communities.md#LatestReleases) installées sont accessibles aux développeurs à partir du référentiel Adobe. Voir [Utilisation de Maven pour les communautés : Javadocs](maven.md#javadocs).

**L’emplacement et le format de l’UGC dans le référentiel peuvent être modifiés sans avertissement**.

### Exemple de configuration {#example-setup}

Les captures d’écran des données du référentiel proviennent de la configuration de la notation et du badge pour un forum sur deux sites AEM différents :

1. Un site AEM avec un identifiant unique (site de la communauté créé à l’aide de l’assistant) :

   * Utilisation du site Didacticiel de prise en main (engager) créé pendant le didacticiel de [prise en main](getting-started.md)
   * Localisation du noeud de la page du forum

      * `/content/sites/engage/en/forum/jcr:content`
   * Ajout de propriétés de notation et de badge

      * scoreRules = [/etc/community/score/rule/commentaires-score,/etc/community/score/règles/forums-score]
      * badgingRules =[/etc/community/badging/rule/commentaires-score,/etc/community/badging/rule/forums-score]
   * Localisation du noeud du composant de forum

      * `/content/sites/engage/en/forum/jcr:content/content/primary/forum`

         ( `sling:resourceType = social/forum/components/hbs/forum`)
   * Ajouter une propriété pour afficher les badges

      * `allowBadges = true`
   * Un utilisateur se connecte, crée un sujet de forum et reçoit un badge de bronze





1. Un site AEM *sans* ID unique :

   * Utilisation du guide des composants [de la communauté](components-guide.md)
   * Localisation du noeud de la page du forum

      * `/content/community-components/en/forum/jcr:content`
   * Ajout de propriétés de notation et de badge

      * 
         ```
         scoringRules = [/etc/community/scoring/rules/comments-scoring,
         /etc/community/scoring/rules/forums-scoring]
         ```

      * 
         ```
         badgingRules =[/etc/community/badging/rules/comments-scoring,
         /etc/community/badging/rules/forums-scoring]
         ```
   * Localisation du noeud du composant de forum

      * `/content/community-components/en/forum/jcr:content/content/forum`

         ( `sling:resourceType = social/forum/components/hbs/forum`)
   * Ajouter une propriété pour afficher les badges

      * `allowBadges = true`
   * Un utilisateur se connecte, crée un sujet de forum et reçoit un badge de bronze





1. Un badge de modérateur est attribué à un utilisateur à l’aide de cURL :

```shell
curl -i -X POST -H "Accept:application/json" -u admin:admin -F ":operation=social:assignBadge" -F "badgeContentPath=/etc/community/badging/images/moderator/jcr:content/moderator.png" http://localhost:4503/home/users/community/w271OOup2Z4DjnOQrviv/profile.social.json
```

Comme un utilisateur a obtenu deux badges en bronze et qu’il a reçu un badge de modérateur, voici comment l’utilisateur apparaît avec son entrée sur le forum :

![chlimage_1-250](assets/chlimage_1-250.png)

>[!NOTE]
>
>Cet exemple ne suit pas les bonnes pratiques suivantes :
>
>* les noms des règles de notation doivent être uniques au niveau mondial ; ils ne doivent pas se terminer par le même nom.\
   >  Voici un exemple de ce que *ne pas* faire :\
   >  /etc/community/score/rule/site1/forums-score\
   >  /etc/community/score/rule/site2/forums-score
   >
   >
* création d’images de badge uniques pour différents sites AEM
>



### Accès au score UGC {#access-scoring-ugc}

Il est préférable d’utiliser les [API](#scoring-and-badging-apis) .

À des fins d’enquête, à l’aide de JSRP pour l’exemple, le dossier de base contenant les scores est

* `/content/usergenerated/asi/jcr/scoring`

Le noeud enfant de `scoring`est le nom de la règle de notation. Il est donc recommandé que les noms des règles de notation sur un serveur soient globalement uniques.

Pour le site Geometrixx Engage, l’utilisateur et son score se trouvent dans un chemin construit avec le nom de la règle de notation, l’ID du site de la communauté ( `engage-ba81p`), un ID unique et l’ID de l’utilisateur :

* `.../scoring/forums-scoring/engage-ba81p/6d179715c0e93cb2b20886aa0434ca9b5a540401/riley`

Pour le site de guide Composants de la communauté, l’utilisateur et son score se trouvent dans un chemin construit avec le nom de la règle de notation, un ID par défaut ( `default-site`), un ID unique et l’ID de l’utilisateur :

* `.../scoring/forums-scoring/default-site/b27a17cb4910a9b69fe81fb1b492ba672d2c086e/riley`

Le score est stocké dans la propriété `scoreValue_tl` qui peut directement contenir uniquement une valeur ou indirectement faire référence à un atomicCounter.

![chlimage_1-251](assets/chlimage_1-251.png)

### Insigne d&#39;accès UGC {#access-badging-ugc}

Il est préférable d’utiliser les [API](#scoring-and-badging-apis) .

À des fins d’enquête, à l’aide de JSRP, par exemple, le dossier de base contenant des informations sur les badges attribués ou attribués est

* /content/usergenerate/asi/jcr

Suivi du chemin d’accès au profil de l’utilisateur, se terminant par un dossier de badges, tel que

* /home/users/community/w271OOup2Z4DjnOQrviv/profile/badges

#### Badge décerné {#awarded-badge}

![chlimage_1-252](assets/chlimage_1-252.png)

#### badge attribué {#assigned-badge}

![chlimage_1-253](assets/chlimage_1-253.png)

## Informations supplémentaires {#additional-information}

Pour afficher une liste triée de membres en fonction des points :

* [Fonction](functions.md#leaderboard-function) du tableau de bord pour l’inclusion dans un site communautaire ou un modèle de groupe.
* [Composant](enabling-leaderboard.md)de classement, composant incitatif de la fonction de classement, pour la création de pages.

