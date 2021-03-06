---
title: Utilisation des journaux
seo-title: Working with Logs
description: Découvrez comment résoudre les problèmes d’AEM à l’aide des journaux.
seo-description: Learn how to troubleshoot AEM by working with logs.
uuid: b64e0b25-5228-4c2f-9cc1-dde524134026
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: operations
content-type: reference
discoiquuid: b4c1cb82-865b-48dd-b5c0-946e6610ce8e
exl-id: 201e2b57-17c0-4454-9b0e-026e2c95ac63
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 92%

---

# Utilisation des journaux{#working-with-logs}

Cette section contient des informations détaillées sur les journaux disponibles pour vous aider à résoudre les problèmes.

CRX enregistre des journaux détaillés. Après avoir décompressé et démarré Quickstart, vous pouvez retrouver les journaux dans les emplacements suivants :

* crx-quickstart/launchpad/logs
* crx-quickstart/server/logs
* crx-quickstart/logs

## Activation du niveau de journalisation DEBUG {#activating-the-debug-log-level}

Le niveau de journalisation par défaut est INFO, ce qui signifie que les messages DEBUG ne sont pas consignés.

Pour activer le niveau de journalisation DEBUG, utilisez l’explorateur CRX afin de définir

```xml
/libs/sling/config/org.apache.sling.commons.log.LogManager/org.apache.sling.commons.log.level
```

la propriété à corriger. Ne laissez pas le journal au niveau de débogage DEBUG plus longtemps que nécessaire, car cela génère un grand nombre de journaux.

Une ligne dans le fichier de débogage commence généralement par DEBUG, puis fournit le niveau de journalisation, l’action d’installation et le message du journal. Par exemple :

```xml
DEBUG 3 WebApp Panel: WebApp successfully deployed
```

Les niveaux de journalisation sont les suivants :

| 0 | Erreur fatale | L’action a échoué et le programme d’installation ne peut pas continuer. |
|---|---|---|
| 1 | Erreur | L’action a échoué. L’installation se poursuit, mais une partie de CRX n’a pas été installée correctement et ne fonctionnera pas. |
| 2 | Avertissement | L’action a réussi, mais a rencontré des problèmes. CRX risque de ne pas fonctionner correctement. |
| 3 | Informations | L’action a réussi. |

## Option d’informations détaillées utilisée pour la résolution des incidents {#verbose-option-used-for-troubleshooting}

Lorsque vous démarrez CRX, vous pouvez ajouter l’option -v (verbose) à la ligne de commande, comme dans : &quot;

` java -jar crx-<*version*>-<*edition*>.jar -v`

Utilisez l’option d’informations détaillées pour procéder à la résolution des incidents, car cette option affiche une partie de la sortie du journal quickstart sur la console.
