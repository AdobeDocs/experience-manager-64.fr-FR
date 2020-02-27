---
title: Mise en œuvre d’Android Player
seo-title: Mise en œuvre d’Android Player
description: 'Suivez cette page pour découvrir la mise en œuvre d’Android Watchdog, une solution pour restaurer le lecteur suite à une panne. '
seo-description: 'Suivez cette page pour découvrir la mise en œuvre d’Android Watchdog, une solution pour restaurer le lecteur suite à une panne. '
uuid: 37527a6a-dcc5-4256-abeb-e1f95ff80be4
contentOwner: Jyotika syal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.4/SCREENS
topic-tags: administering
discoiquuid: e6ec1641-4323-4c79-b932-b857feb1df21
translation-type: tm+mt
source-git-commit: 1ebe1e871767605dd4295429c3d0b4de4dd66939

---


# Mise en œuvre d’Android Player {#implementing-android-player}

Un ***watchdog*** est une solution permettant de restaurer le lecteur suite à une panne. Les applications doivent s’inscrire auprès du service watchdog, puis envoyer régulièrement des messages au service lui indiquant qu’elles sont actives. Au cas où le service watchdog ne reçoit pas de message de maintien en activité dans le délai imparti, le service tente de redémarrer l’appareil pour une restauration propre (s’il dispose des droits suffisants) ou de redémarrer l’application.

## Mise en œuvre d’Android Watchdog {#implementing-android-watchdog}

En raison de l’architecture d’Android, le redémarrage de l’appareil requiert que l’application dispose d’autorisations système. Pour ce faire, vous devez signer le fichier apk à l’aide des clés de signature du fabricant, faute de quoi le service watchdog redémarre l’application du lecteur, mais pas l’appareil.

### Signature de fichiers apk Android à l’aide des clés du fabricant      {#signage-of-android-apks-using-manufacturer-keys}

To access some of the privileged APIs of Android such as *PowerManager* or *HDMIControlServices*, you need to sign the android apk using the manufacturer&#39;s keys.

>[!CAUTION]
>
>Conditions préalables :
>
>Le kit SDK Android doit être installé avant que vous n’exécutiez les étapes suivantes.

Suivez les étapes ci-dessous pour signer le fichier apk Android à l’aide des clés du fabricant :

1. Téléchargez le fichier apk à partir de Google Play ou de la page [Téléchargements du lecteur AEM Screens](https://download.macromedia.com/screens/)
1. Procurez-vous les clés de plateforme du fabricant pour obtenir un fichier *pk8* et *pem*

1. Localisez l’outil apksigner dans le kit SDK Android à l’aide de la commande find ~/Library/Android/sdk/build-tools -name &quot;apksigner&quot;
1. &lt;pathto> /apksigner sign --key platform.pk8 --cert platform.x509.pem aemscreensplayer.apk
1. Recherchez le chemin d’accès à l’outil d’alignement zip dans le SDK Android.
1. &lt;pathto> /zipalign -fv 4 aemscreensplayer.apk aemscreensaligned.apk
1. Installez ***aemscreensaligned.apk*** via adb install sur l’appareil.

## Mise en œuvre du watchdog Android {#android-watchdog-implementation}

Le service watchdog Android est mis en œuvre en tant que module externe cordova via *AlarmManager*.

Le diagramme suivant illustre la mise en œuvre du service watchdog :

![chlimage_1-43](assets/chlimage_1-43.png)

**1. Initialisation** Au moment de l’initialisation du module externe cordova, les autorisations sont vérifiées pour voir si nous disposons des autorisations système et donc de l’autorisation Redémarrer. Si ces deux critères sont satisfaits, une tentative en attente d’exécution de Redémarrer est créée. Dans le cas contraire, une tentative en attente de redémarrage de l’application (en fonction de son activité de lancement) est créée.

**2. Minuteur de maintien en activité** Un minuteur de maintien en activité est utilisé pour déclencher un événement toutes les 15 secondes. Dans cet événement, vous devez annuler la tentative en attente existante (pour redémarrer l’application) et enregistrer une nouvelle tentative en attente pour les mêmes 60 secondes à l’avenir (en remettant à plus tard le redémarrage).

>[!NOTE]
>
>Sous Android, *AlarmManager* est utilisé pour enregistrer les *pendingIntents* qui peuvent s’exécuter même si l’application est en panne et que sa distribution d’alarme est incorrecte à partir d’API 19 (Kitkat). Conservez un certain espace entre l’intervalle du minuteur et l’alarme *pendingIntent* de *AlarmManager*.

**3. Panne d’application** En cas de panne, le pendingIntent pour la commande Redémarrer enregistré avec AlarmManager n’est plus réinitialisé et donc exécute un redémarrage de l’application (en fonction des autorisations disponibles lors de l’initialisation du module externe cordova).
