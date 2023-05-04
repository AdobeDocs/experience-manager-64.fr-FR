---
title: Résolution des problèmes d’AEM lors de la création
seo-title: Troubleshooting AEM when Authoring
description: Problèmes que vous pouvez rencontrer lors de l’utilisation d’AEM
seo-description: Some issues that you might encounter when using AEM
uuid: 99af51ea-8628-4811-83f2-ab3f88f0279e
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: da0a5644-2e1d-4394-a6aa-11bb41406ba6
exl-id: b0890070-c9e8-4ce4-9149-00c8c38298ce
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 55%

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

      * `http://localhost:4502/sites.html/content?`
      * Ceci demandera la page directement auprès d’AEM et contournera le dispatcher. Si vous recevez la page mise à jour, ceci indique que vous devez vider la mémoire cache du dispatcher.
   * Contactez l’administrateur du système en cas de problèmes avec les files d’attente de réplication.


## Actions de composant non visibles dans la barre d’outils {#component-actions-not-visible-on-toolbar}

* **Problème** :

   * La plage entière des actions de composants applicables n’est pas visible lors de la modification d’une page de contenu dans l’environnement de création.

* **Raison** :

   * Dans de rares cas, une action précédente peut avoir un impact sur la barre d’outils.

* **Solution** :

   * Actualisez la page.
