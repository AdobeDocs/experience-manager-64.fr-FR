---
title: Gestion des listes de révocation des certificats
seo-title: Managing certificate revocationlists
description: Découvrez comment gérer des listes de révocation de certificats.
seo-description: Learn how to manage certificate revocation lists.
uuid: d8c4b64c-a273-4f5d-8b71-f6ea455c0f0a
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_certificates_and_credentials
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 9744cc2d-5e6b-4341-9270-43d479bdca04
exl-id: 45741270-2d57-4d6d-92ef-65b6c1deb448
source-git-commit: bd94d3949f0117aa3e1c9f0e84f7293a5d6b03b4
workflow-type: tm+mt
source-wordcount: '144'
ht-degree: 100%

---

# Gestion des listes de révocation des certificats{#managing-certificate-revocationlists}

Trust Store Management vous permet d’importer, de modifier et de supprimer des listes de révocation des certificats (CRL). Les listes de révocation des certificats codées Base64 et DER sont prises en charge.

## Importation d’une CRL {#import-a-crl}

1. Dans Administration Console, cliquez sur Paramètres > Trust Store Management > Listes de révocation des certificats, puis sur Importer.
1. Dans la zone Alias, saisissez un identificateur pour la liste CRL.
1. Cliquez sur Parcourir pour accéder à la CRL, puis sur OK.

## Exportation d’une CRL {#export-a-crl}

1. Dans Administration Console, cliquez sur Paramètres > Trust Store Management > Listes de révocation des certificats.
1. Cliquez sur le nom d’alias de la liste CRL à exporter, puis sur Exporter.
1. Suivez les instructions pour exporter la liste CRL. Les listes CRL sont exportées en codage à base 64.
1. Cliquez sur OK.

## Suppression d’une CRL {#delete-a-crl}

1. Dans Administration Console, cliquez sur Paramètres > Trust Store Management > Listes de révocation des certificats.
1. Cochez la case correspondant aux listes CRL à supprimer, cliquez sur Supprimer, puis sur OK.
