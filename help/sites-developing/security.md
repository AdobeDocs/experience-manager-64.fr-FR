---
title: Sécurité
seo-title: Security
description: La sécurité des applications commence pendant la phase de développement.
seo-description: Application Security starts during the development phase
exl-id: 22c48f8c-38df-4c9b-88cf-67f6ae46e7e1
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 56%

---

# Sécurité{#security}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

La sécurité des applications commence pendant la phase de développement. Adobe recommande d’appliquer les bonnes pratiques de sécurité suivantes.

## Utilisation de la session de requête {#use-request-session}

Selon le principe de moindre privilège, Adobe recommande d’effectuer chaque accès au référentiel en utilisant la session liée à la requête de l’utilisateur et au contrôle d’accès approprié.

## Protect contre les scripts intersites (XSS) {#protect-against-cross-site-scripting-xss}

Les scripts de site à site (XSS) permettent aux pirates d’injecter du code dans des pages web consultées par d’autres utilisateurs. Cette vulnérabilité de sécurité peut être exploitée par des utilisateurs web malveillants pour contourner les contrôles d’accès.

AEM applique le principe de filtrage de tout le contenu fourni par l’utilisateur en sortie. La prévention de XSS est prioritaire lors des phases de développement et de test.

Le mécanisme de protection XSS proposé par AEM est basé sur la [Bibliothèque Java AntiSamy](https://www.owasp.org/index.php/Category:OWASP_AntiSamy_Project) fournie par [OWASP (The Open Web Application Security Project)](https://www.owasp.org/). La configuration par défaut d’AntiSamy se trouve à l’adresse

`/libs/cq/xssprotection/config.xml`

Il est important que vous adaptiez cette configuration à vos besoins en matière de sécurité en recouvrant le fichier de configuration. Vous trouverez, dans la [documentation officielle d’AntiSamy](https://www.owasp.org/index.php/Category:OWASP_AntiSamy_Project), toutes les informations nécessaires pour satisfaire vos exigences en matière de sécurité.

>[!NOTE]
>
>Il est vivement conseillé de toujours accéder à l’API de protection XSS en utilisant l’interface [XSSAPI fournie par AEM](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/javadoc/com/adobe/granite/xss/XSSAPI.html).

En outre, un pare-feu d’application web, tel que le [mod_security pour Apache](https://www.modsecurity.org), peut fournir un contrôle centralisé fiable sur la sécurité de l’environnement de déploiement, ainsi qu’une protection contre les attaques XSS qui n’étaient pas détectées précédemment.

## Accès aux informations du Cloud Service {#access-to-cloud-service-information}

>[!NOTE]
>
>Les listes de contrôle d’accès pour les informations du Cloud Service ainsi que les paramètres OSGi requis pour sécuriser votre instance sont automatisés dans le cadre de la [Mode Prêt pour la production](/help/sites-administering/production-ready.md). Cela signifie que vous ne devez pas apporter de modifications manuelles à la configuration. Cependant, il est conseillé de les passer en revue avant le déploiement proprement dit.

Lorsque vous [intégrer votre instance AEM à Adobe Marketing Cloud](/help/sites-administering/marketing-cloud.md) vous utilisez [Configurations Cloud Service](/help/sites-developing/extending-cloud-config.md). Les informations relatives à ces configurations, ainsi que les statistiques collectées, sont stockées dans le référentiel. Si vous utilisez cette fonctionnalité, nous vous recommandons de vérifier si la sécurité par défaut de ces informations correspond à vos besoins.

Le module webservicesupport écrit des statistiques et des informations de configuration sous :

`/etc/cloudservices`

Avec les autorisations par défaut :

* Environnement de création : `read` pour `contributors`

* Environnement de publication : `read` pour `everyone`

## Protection contre les attaques CRSF {#protect-against-cross-site-request-forgery-attacks}

Pour plus d’informations sur les mécanismes de sécurité mis en œuvre par AEM pour limiter les attaques CSRF, reportez-vous à la section [Filtre du référent Sling](/help/sites-administering/security-checklist.md#protect-against-cross-site-request-forgery) de la liste de contrôle de sécurité et à la [documentation du framework de protection CSRF](/help/sites-developing/csrf-protection.md).
