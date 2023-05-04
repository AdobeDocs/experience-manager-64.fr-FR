---
title: Les 10 plus grands risques d’OWASP
seo-title: OWASP Top 10
description: Découvrez comment AEM gère les 10 principaux risques de sécurité OWASP.
seo-description: Learn how AEM deals with the top 10 OWASP security risks.
uuid: a5a7e130-e15b-47ae-ba21-448f9ac76074
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.4/SITES
topic-tags: Security
content-type: reference
discoiquuid: e5323ae8-bc37-4bc6-bca6-9763e18c8e76
exl-id: c29472c8-9a93-4cb1-9cb1-05fc155ba736
source-git-commit: c5b816d74c6f02f85476d16868844f39b4c47996
workflow-type: tm+mt
source-wordcount: '532'
ht-degree: 57%

---

# Les 10 plus grands risques d’OWASP{#owasp-top}

>[!CAUTION]
>
>AEM 6.4 a atteint la fin de la prise en charge étendue et cette documentation n’est plus mise à jour. Pour plus d’informations, voir notre [période de support technique](https://helpx.adobe.com/fr/support/programs/eol-matrix.html). Rechercher les versions prises en charge [here](https://experienceleague.adobe.com/docs/?lang=fr).

Le [Ouvrir le projet Web Application Security](https://www.owasp.org) (OWASP) conserve une liste de ce qu’ils considèrent comme la variable [Les 10 principaux risques de sécurité des applications web](https://www.owasp.org/index.php/OWASP_Top_Ten_Project).

Ils sont répertoriés ci-dessous, ainsi qu’une explication de la façon dont CRX les traite.

## 1. Injection {#injection}

* SQL -Empêché par défaut : La configuration de référentiel par défaut ne comprend ni ne requiert de base de données traditionnelle et toutes les données sont stockées dans le référentiel de contenu. Tous les accès sont limités aux utilisateurs authentifiés et ne peuvent avoir lieu que via l’API JCR. SQL est pris en charge pour les requêtes de recherche uniquement (SELECT). SQL offre en outre une prise en charge de la liaison des valeurs.
* LDAP : l’injection LDAP n’est pas possible, car le module d’authentification filtre l’entrée et effectue l’importation de l’utilisateur à l’aide de la méthode bind.
* Système d’exploitation : aucune exécution de shell n’est effectuée dans l’application.

## 2. Script intersite (XSS) {#cross-site-scripting-xss}

La solution générale consiste à coder toutes les sorties du contenu créé par l’utilisateur avec une bibliothèque de protection XSS côté serveur basée sur [OWASP Encoder](https://www.owasp.org/index.php/OWASP_Java_Encoder_Project) et [AntiSamy](https://www.owasp.org/index.php/Category:OWASP_AntiSamy_Project).

Le XSS est une priorité majeure pendant le test et le développement et les problèmes détectés sont (généralement) résolus immédiatement.

## 3. Authentification interrompue et gestion des sessions {#broken-authentication-and-session-management}

AEM utilise des techniques d’authentification performantes et éprouvées, qui font appel à [Apache Jackrabbit](https://jackrabbit.apache.org/) et [Apache Sling](https://sling.apache.org/). Les sessions de navigateur ou HTTP ne sont pas utilisées dans AEM.

## 4. Références d’objets directs non sécurisées {#insecure-direct-object-references}

Tous les accès aux objets de données sont arbitrés par le référentiel et donc restreints par le contrôle d’accès basé sur les rôles.

## 5. Cross-Site Request Forgery (CSRF) {#cross-site-request-forgery-csrf}

Une attaque Cross-Site Request Forgery (CSRF) est arbitrée en injectant automatiquement un jeton cryptographique dans l’ensemble des formulaires et des requêtes AJAX et en vérifiant ce jeton sur le serveur pour chaque requête POST.

En outre, AEM est fourni avec un filtre référent-en-tête, qui peut être configuré pour autoriser *uniquement* les requêtes POST d’hôtes spécifiques (inscrits dans une liste autorisée).

## 6. Erreur de configuration de la sécurité {#security-misconfiguration}

Il est impossible de garantir que tous les logiciels sont toujours correctement configurés. Toutefois, nous nous efforçons de fournir autant d’assistance que possible et de rendre la configuration aussi simple possible. De plus, AEM navires avec [Contrôle d’intégrité de la sécurité intégré](/help/sites-administering/operations-dashboard.md) qui vous aident à surveiller en un coup d’oeil la configuration de la sécurité.

Veuillez examiner la [Liste de contrôle de sécurité](/help/sites-administering/security-checklist.md) pour plus d’informations et obtenir des instructions étape par étape.

## 7. Stockage cryptographique non sécurisé {#insecure-cryptographic-storage}

Les mots de passe sont stockés en tant que hachages cryptographiques dans le noeud utilisateur ; par défaut, ces noeuds ne sont lisibles que par l’administrateur et l’utilisateur lui-même.

Les données sensibles telles que les informations d’identification tierces sont stockées sous forme chiffrée à l’aide d’une bibliothèque cryptographique certifiée FIPS 140-2.

## 8. Échec de la limitation de l’accès à l’URL {#failure-to-restrict-url-access}

Le référentiel permet de définir des [autorisations précises (comme spécifié par JCR)](https://www.adobe.io/experience-manager/reference-materials/spec/jcr/2.0/16_Access_Control_Management.html) pour n’importe quel utilisateur ou groupe dans n’importe quel chemin d’accès, via des entrées de contrôle d’accès. Les restrictions d’accès sont appliquées par le référentiel.

## 9. Protection insuffisante de la couche de transfert {#insufficient-transport-layer-protection}

Atténué par la configuration du serveur (par exemple, utilisez HTTPS uniquement).

## 10. Redirections et transferts non validés {#unvalidated-redirects-and-forwards}

Risque atténué en restreignant toutes les redirections à des destinations fournies par l’utilisateur vers des emplacements internes.
