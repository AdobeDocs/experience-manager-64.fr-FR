---
title: Résolution des problèmes d’AEM lors de la création
seo-title: Troubleshooting AEM when Authoring
description: La section suivante traite de certains problèmes susceptibles d’être rencontrés lorsque vous utilisez AEM, ainsi que des suggestions pour résoudre ces problèmes.
seo-description: The following section covers some issues that you might encounter when using AEM, together with suggestions on how to troubleshoot them.
uuid: eb95e5ba-1eed-4ffb-80c1-9b8468820c22
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: 9b492b17-9029-46ae-9dc0-bb21e6b484df
exl-id: 09409631-c579-4b1f-9193-1348896f6a09
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 64%

---

# Résolution des problèmes d’AEM lors de la création{#troubleshooting-aem-when-authoring}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

La section suivante traite de certains problèmes susceptibles d’être rencontrés lorsque vous utilisez AEM, ainsi que des suggestions pour résoudre ces problèmes.

>[!NOTE]
>
>Si vous rencontrez des problèmes, il est également intéressant de consulter les [problèmes connus](/help/release-notes/known-issues.md) relatifs à votre instance (packs de version et pack de services).

>[!NOTE]
>
>Les utilisateurs disposant de droits d’administrateur et souhaitant résoudre les problèmes liés à AEM peuvent utiliser les méthodes de dépannage décrites dans la section [AEM de dépannage (pour les administrateurs)](/help/sites-administering/troubleshoot.md). Si vous ne disposez pas des privilèges suffisants, contactez votre administrateur système pour connaître les AEM de dépannage.

## Ancienne version de la page toujours visible sur le site de publication {#old-page-version-still-on-published-site}

* **Problème** :

   * Vous avez apporté des modifications à une page et répliqué la page sur le site de publication, mais l’événement *old* La version de la page est toujours affichée sur le site de publication.

* **Raison** :

   * Cela peut avoir plusieurs causes, le plus souvent le cache (votre navigateur local ou Dispatcher), bien que cela puisse parfois poser un problème avec la file d’attente de réplication.

* **Solutions** :

   * Il existe différentes possibilités :
   * Vérifiez que la page a bien été répliquée. Vérifiez le statut de la page et, si nécessaire, le statut de la file d’attente de réplication.
   * Effacez la mémoire cache du navigateur local et accédez de nouveau à votre page.
   * Ajoutez `?` à la fin de l’URL de la page. Par exemple :

      `http://localhost:4502/sites.html/content?`

      Ceci demandera la page directement auprès d’AEM et contournera le dispatcher. Si vous recevez la page mise à jour, ceci indique que vous devez vider la mémoire cache du dispatcher.

   * Contactez l’administrateur du système en cas de problèmes avec les files d’attente de réplication.

## Sidekick non visible {#sidekick-not-visible}

* **Problème** :

   * Le sidekick n’est pas visible lors de la modification d’une page de contenu dans l’environnement de création.

* **Raison** :

   * Dans de rares cas, il se peut que vous ayez positionné l’en-tête de votre sidekick en dehors de votre fenêtre active. Cela signifie que vous ne pouvez pas le repositionner.

* **Solution** :

   * Fermez votre session en cours et rouvrez-la. Le sidekick revient à la position par défaut.

## Chercher et Remplacer : toutes les instances ne sont pas remplacées {#find-replace-not-all-instances-are-replaced}

* **Problème :**

   * Si vous utilisez l’option **Rechercher et remplacer**, il se peut que certaines instances du terme `find` ne soient pas remplacées sur une page.

* **Raison** :

   * Le fonctionnement de l’option **Rechercher et remplacer** dépend de la façon dont le contenu est enregistré et s’il peut faire l’objet de recherches. Par exemple, un texte de blog est stocké dans la propriété `jcr:text`, qui n’est pas configurée pour faire l’objet de recherches. L’étendue par défaut du servlet de recherche et de remplacement couvre les propriétés suivantes :

      * `jcr:title`
      * `jcr:description`
      * `jcr:text`
      * `text`

* **Solution** :

   * Ces définitions peuvent être modifiées dans la configuration du **servlet Rechercher et remplacer de la gestion de contenu Web Day CQ** à l’aide de la **console Web**, par exemple à l’adresse

      `http://localhost:4502/system/console/configMgr`
