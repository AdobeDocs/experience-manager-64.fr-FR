---
title: Restructuration des référentiels de Forms dans AEM 6.4
seo-title: Forms Repository Restructuring in AEM 6.4
description: Découvrez comment apporter les modifications nécessaires pour migrer vers la nouvelle structure de référentiel dans AEM 6.4 pour Forms.
seo-description: Learn how to make the necessary changes in order to migrate to the new repository structure in AEM 6.4 for Forms.
uuid: e60830d4-23ca-4be9-941a-ee4abe4786a6
products: SG_EXPERIENCEMANAGER/6.4/SITES
content-type: reference
topic-tags: repo_restructuring
discoiquuid: 1ce9a622-5968-407f-a74b-d325a2bff669
feature: Upgrading
exl-id: a2d6524e-3f5b-4d1e-af64-61ff95889657
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '529'
ht-degree: 100%

---

# Restructuration des référentiels de Forms dans AEM 6.4{#forms-repository-restructuring-in-aem}

Comme indiqué dans la page parent [Restructuration des référentiels dans AEM 6.4](/help/sites-deploying/repository-restructuring.md), les clients effectuant une mise à niveau vers AEM 6.4 doivent utiliser cette page pour évaluer le travail associé aux modifications des référentiels ayant un impact sur la solution AEM Forms. Certaines modifications demandent du travail lors du processus de mise à niveau vers AEM 6.4, tandis que d’autres peuvent être différées jusqu’à une mise à niveau vers la version 6.5.

**Avec la mise à niveau vers la version 6.4**

* [Divers](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md#misc)

**Avant de procéder à la mise à niveau vers la version 6.5**

* [Configuration du service cloud Echosign](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md#echosign-cloud-service-configuration)
* [Configurations du service cloud Recaptcha](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md#recaptcha-cloud-service-configurations)
* [Configurations du service cloud Typekit](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md#typekit-cloud-service-configurations)
* [Divers](/help/sites-deploying/forms-repository-restructuring-in-aem-6-4.md#misc)

## Avec la mise à niveau vers la version 6.4 {#with-upgrade}

### Divers {#misc}

| **Emplacement précédent** | `/etc/clientlibs/fd/fp` |
|---|---|
| **Nouveaux emplacements** | `/libs/fd/fp/components` |
| **Conseils de restructuration** | Toute référence explicite dans le code personnalisé à l’emplacement existant doit être mise à jour vers le nouvel emplacement. |
| **Remarques** | Ces bibliothèques clientes ne doivent pas être modifiées ou étendues. |

| **Emplacement précédent** | `/etc/clientlibs/fd/rte` |
|---|---|
| **Nouveaux emplacements** | `/libs/fd/rte` |
| **Conseils de restructuration** | Pour les ressources des bibliothèques clientes pouvant être référencées par des chemins absolus, vous devez utiliser des chemins plus récents dans les nouvelles ressources. |
| **Remarques** | S/O |

| **Emplacement précédent** | `/etc/clientlibs/fd/af` |
|---|---|
| **Nouveaux emplacements** | `/libs/fd/af/authoring/clientlibs` |
| **Conseils de restructuration** | Pour les ressources des bibliothèques clientes pouvant être référencées par des chemins absolus, vous devez utiliser des chemins plus récents dans les nouvelles ressources. |
| **Remarques** | S/O |

| **Emplacement précédent** | `/etc/clientlibs/fd/xfaforms` |
|---|---|
| **Nouveaux emplacements** | `/libs/fd/xfaforms/clientlibs/` |
| **Conseils de restructuration** | Pour les ressources des bibliothèques clientes pouvant être référencées par des chemins absolus, vous devez utiliser des chemins plus récents dans les nouvelles ressources. |
| **Remarques** | S/O |

| **Emplacement précédent** | `/etc/clientlibs/fd/af` |
|---|---|
| **Nouveaux emplacements** | `/libs/fd/af/runtime/clientlibs` |
| **Conseils de restructuration** | Pour les ressources des bibliothèques clientes pouvant être référencées par des chemins absolus, vous devez utiliser des chemins plus récents dans les nouvelles ressources. |
| **Remarques** | S/O |

| **Emplacement précédent** | `/etc/clientlibs/fd/af` |
|---|---|
| **Nouveaux emplacements** | `/libs/fd/af/runtime/clientlibs` |
| **Conseils de restructuration** | Pour les ressources des bibliothèques clientes pouvant être référencées par des chemins absolus, vous devez utiliser des chemins plus récents dans les nouvelles ressources. |
| **Remarques** | S/O |

| **Emplacement précédent** | `/etc/clientlibs/fd/expeditor` |
|---|---|
| **Nouveaux emplacements** | `/libs/fd/expeditor/clientlibs` |
| **Conseils de restructuration** | Pour les ressources des bibliothèques clientes pouvant être référencées par des chemins absolus, vous devez utiliser des chemins plus récents dans les nouvelles ressources. |
| **Remarques** | S/O |

| **Emplacement précédent** | `/etc/clientlibs/fd/fmaddon` |
|---|---|
| **Nouveaux emplacements** | `/libs/fd/fmaddon` |
| **Conseils de restructuration** | La modification de ces clientlibs n’a jamais été recommandée ou prise en charge. Si des modifications ont été apportées à ces clientlibs, vous devez les restaurer pour utiliser le code fourni par AEM. |
| **Remarques** | S/O |

| **Emplacement précédent** | `/etc/aep` |
|---|---|
| **Nouveaux emplacements** | `/var/fd/content/annotations` |
| **Conseils de restructuration** | La modification de ces clientlibs n’a jamais été recommandée ou prise en charge. Si des modifications ont été apportées à ces clientlibs, vous devez les restaurer pour utiliser le code fourni par AEM. |
| **Remarques** | S/O |

## Avant de procéder à la mise à niveau vers la version 6.5 {#prior-to-upgrade}

### Configuration du service cloud Echosign {#echosign-cloud-service-configuration}

| **Emplacement précédent** | `/etc/cloudservices/echosign` |
|---|---|
| **Nouveaux emplacements** | `/conf/<tenant>/settings/cloudconfigs/echosign` |
| **Conseils de restructuration** | L’utilitaire [Migration différée de contenu](/help/sites-deploying/lazy-content-migration.md) doit être déclenché depuis l’interface utilisateur de migration Forms. |
| **Remarques** | S/O |

### Configurations du service cloud Recaptcha {#recaptcha-cloud-service-configurations}

| **Emplacement précédent** | `/etc/cloudservices/recaptcha` |
|---|---|
| **Nouveaux emplacements** | `/conf/<tenant>/settings/cloudconfigs/recaptcha` |
| **Conseils de restructuration** | L’utilitaire [Migration différée de contenu](/help/sites-deploying/lazy-content-migration.md) doit être déclenché depuis l’interface utilisateur de migration Forms. |
| **Remarques** | S/O |

### Configurations du service cloud Typekit {#typekit-cloud-service-configurations}

| **Emplacement précédent** | `/etc/cloudservices/typekit` |
|---|---|
| **Nouveaux emplacements** | `/conf/<tenant>/settings/cloudconfigs/typekit` |
| **Conseils de restructuration** | L’utilitaire [Migration différée de contenu](/help/sites-deploying/lazy-content-migration.md) doit être déclenché depuis l’interface utilisateur de migration Forms. |
| **Remarques** | S/O |

### Divers {#misc-1}

| **Emplacement précédent** | `/etc/cloudservices/fdm` |
|---|---|
| **Nouveaux emplacements** | `/conf/<tenant>/settings/cloudconfigs/fdm` |
| **Conseils de restructuration** | L’utilitaire [Migration différée de contenu](/help/sites-deploying/lazy-content-migration.md) doit être déclenché depuis l’interface utilisateur de migration Forms. |
| **Remarques** | S/O |

| **Emplacement précédent** | `/etc/designs/fd/fp` |
|---|---|
| **Nouveaux emplacements** | `/libs/fd/fp` |
| **Conseils de restructuration** | Toute référence aux modèles /etc doit être éventuellement mise à jour pour pointer vers leurs équivalents `/libs`. |
| **Remarques** | S/O |
