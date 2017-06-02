---
layout: post
title: "En oversikt over hva apper kan tillate seg i Android uten å spørre om lov"
excerpt: "En oversikt over tillatelser Android gir enhver app som ber om dem – uten at brukeren kan gjøre noe med det."
---
Mange kjenner til tillatelsene apper i Android enten gir seg selv (i eldre versjoner) eller spør om (i nyere versjoner), for eksempel tilgang til kamera, til kontaktene, til å sende og motta tekstmeldinger. I Androids dokumentasjon kalles denne type tillatelser *farlige tillatelser:*

> *Dangerous* permissions cover areas where the app wants data or resources that involve the user's private information, or could potentially affect the user's stored data or the operation of other apps. For example, the ability to read the user's contacts is a dangerous permission. If an app declares that it needs a dangerous permission, the user has to explicitly grant the permission to the app. [(kilde)](https://developer.android.com/guide/topics/permissions/requesting.html#normal-dangerous)

Dersom en tenker seg om, vil en innse at det også finnes en rekke ting apper kan gjøre uten noen slike tillatelser, for eksempel å bruke internett-tilkoblingen. Også disse tingene har et navn, nemlig *normale tillatelser:*

> *Normal* permissions cover areas where your app needs to access data or resources outside the app's sandbox, but where there's very little risk to the user's privacy or the operation of other apps. For example, permission to set the time zone is a normal permission. If an app declares that it needs a normal permission, the system automatically grants the permission to the app.

Dette er altså tillatelser som gis enhver app uten innvirking fra brukeren. Riktignok oppgis også disse tillatelsene i Google Play Store (dersom en trykker på «Tillatelser» nederst på siden); men brukeren har ingen mulighet til nekte appen noen av disse tillatelsene, hverken før eller etter installasjon. Er appen først installert, må brukeren bare innfinne seg med at appen kan benytte seg av de tillatelsene den har bedt om. (Med andre ord er regimentet for normale tillatelser i Android slik det tidligere var for farlige tillatelser: Vil du ha appen, må du gi den alle tillatelser den krever.)

Så la oss ta en titt på tillatelsene som utgjør «veldig lite risiko» for brukerens privatsfære. Dokumentasjonen har [en liste over dem](https://developer.android.com/guide/topics/permissions/normal-permissions.html) og beskriver alle tillatelsene på [en egen side](https://developer.android.com/reference/android/Manifest.permission.html). Beskrivelsene er dessverre tekniske, og ofte finnes det heller ikke andre steder i den offisielle dokumentasjonen en god forklaring på hva en tillatelse består i. Jeg har gjort et forsøk på å kategorisere tillatelsene etter hvor betydningsfulle jeg anser dem for å være sett fra et personvernsperspektiv.

Merk at jeg i hovedsak tar for meg situasjonen i nyeste versjon av Android (Nougat/7.1.1; dokumentasjonen er egentlig for neste versjon, Android O). I tidligere versjoner – for ikke å nevne telefonprodusenters egne Android-utgaver – ser det til dels mye verre ut; og det er jo dette som er realiteten for de aller fleste Android-brukere. Men her er så mange andre ting verre at regimet for normale tillatelser blir som en bagatell å regne. (Dette er noe jeg håper jeg får skrevet om en gang i fremtiden.)

Se også: [Android Apps do not need your permission to violate your privacy](https://growthbug.com/android-apps-do-not-need-your-permission-to-violate-your-privacy-a9f94bb497a0) om «some of the Normal Permissions and possible risk they may carry». Teksten omtaler også noen tillatelser som nå er blitt fjernet (men selvsagt fortsatt er å finne på de fleste Android-telefoner).

## Farlig

[`ACCESS_WIFI_STATE`](https://developer.android.com/reference/android/Manifest.permission.html#ACCESS_WIFI_STATE)
: «Allows applications to access information about Wi-Fi networks.» Gir appen tilgang til det om er å vite om trådløse nettverk i nærheten (navn, signalfrekvens- og styrke, MAC-adresse m.m.). [WifiAnalyzer](https://vremsoftwaredevelopment.github.io/WiFiAnalyzer/) er et eksempel på en app som utnytter det.

[`CHANGE_WIFI_STATE`](https://developer.android.com/reference/android/Manifest.permission.html#CHANGE_WIFI_STATE)
: «Allows applications to change Wi-Fi connectivity state.» Trolig gir dette appen tillatelse til å aktivere og deaktivere trådløst nettverkstilkobling, til å koble seg fra et trådløst nettverk og til å be telefonen koble seg til et trådløst nettverk. Appen kan ikke uten videre koble enheten til et nytt, bestemt nettverk; det setter wifi i en slags tilkoblingsmodus, samme modus som når wifi slås på manuelt. (Disse antakelsene baserer jeg på hvordan appen [Wi-Fi Privacy Police](https://github.com/BramBonne/privacypolice) fungerer.)

[`ACCESS_NETWORK_STATE`](https://developer.android.com/reference/android/Manifest.permission.html#ACCESS_NETWORK_STATE)
: Lar appen [stille forespørsler](https://developer.android.com/reference/android/net/ConnectivityManager.html) om «the state of network connectivity. It also notifies applications when network connectivity changes.»

[`CHANGE_NETWORK_STATE`](https://developer.android.com/reference/android/Manifest.permission.html#CHANGE_NETWORK_STATE)
: Lar appen [be om](https://developer.android.com/reference/android/net/ConnectivityManager.html) «a network to satisfy a set of [`NetworkCapabilities`](https://developer.android.com/reference/android/net/NetworkCapabilities.html).


[`INTERNET`](https://developer.android.com/reference/android/Manifest.permission.html#KILL_BACKGROUND_PROCESSES)
: «Allows applications to open network sockets.» Dette innbærer ikke bare at appen har nett-tilgang; den har også tilgang til detaljerte opplysninger om andre appers nett-koblinger, noe f.eks. appen [Net Monitor](https://github.com/SecUSo/privacy-friendly-netmonitor) benytter seg av. Men selve innholdet i andre appers nett-tilkoblinger gir denne tillatelsen ikke tilgang til, virker det som.


[`BLUETOOTH`](https://developer.android.com/reference/android/Manifest.permission.html#BLUETOOTH)
: «Allows applications to connect to paired bluetooth devices.»

[`BLUETOOTH_ADMIN`](https://developer.android.com/reference/android/Manifest.permission.html#BLUETOOTH_ADMIN)
: «Allows applications to discover and pair bluetooth devices.» (Uten innblanding fra brukeren?)

[`NFC`](https://developer.android.com/reference/android/Manifest.permission.html#NFC)
: «Allows applications to perform I/O operations over NFC.»

[`TRANSMIT_IR`](https://developer.android.com/reference/android/Manifest.permission.html#TRANSMIT_IR)
: «Allows using the device's IR transmitter, if available.»


### Foruroligende (selv om alt har en nytteverdi i enkelttilfeller)

[`CHANGE_WIFI_MULTICAST_STATE`](https://developer.android.com/reference/android/Manifest.permission.html#CHANGE_WIFI_MULTICAST_STATE)
: «Allows applications to enter Wi-Fi Multicast mode.» Lar appen slå på/av mottakelse av nettverkstrafikk som addresseres til flere enheter på en gang. Denne rettigheten har nok ingen betydning med tanke på personvern; det er heller snakk om batteribruk.

[`EXPAND_STATUS_BAR`](https://developer.android.com/reference/android/Manifest.permission.html#EXPAND_STATUS_BAR)
: «Allows an application to expand or collapse the status bar.» Det er det området øverst på skjermen der klokke, batteriindikator osv. vises. Denne tillatelsen gjelder (nok) bare når appen selv er i forgrunnen.

Alle apper kan se hvilke andre apper som er installert. Dette er ikke engang en tillatelse.

[`GET_PACKAGE_SIZE`](https://developer.android.com/reference/android/Manifest.permission.html#GET_PACKAGE_SIZE)
: «Allows an application to find out the space used by any package.»

[`INSTALL_SHORTCUT`](https://developer.android.com/reference/android/Manifest.permission.html#INSTALL_SHORTCUT)
: «Allows an application to install a shortcut in Launcher,» det vil si på det området en selv kan legge snarveier til apper.

[~~`UNINSTALL_SHORTCUT`~~](https://developer.android.com/reference/android/Manifest.permission.html#UNINSTALL_SHORTCUT)
: «This permission is no longer supported.»

[`KILL_BACKGROUND_PROCESSES`](https://developer.android.com/reference/android/Manifest.permission.html#KILL_BACKGROUND_PROCESSES)
: «Allows an application to call [`killBackgroundProcesses(String)`](https://developer.android.com/reference/android/app/ActivityManager.html#killBackgroundProcesses(java.lang.String)),» der `String` er navnet på en app (pakke). «This is the same as the kernel killing those processes to reclaim memory; the system will take care of restarting these processes in the future as needed.»

[`MODIFY_AUDIO_SETTINGS`](https://developer.android.com/reference/android/Manifest.permission.html#MODIFY_AUDIO_SETTINGS)
: «Allows an application to modify global audio settings.» Lar ikke appen starte opptak av lyd eller lignende.

[`REORDER_TASKS`](https://developer.android.com/reference/android/Manifest.permission.html#REORDER_TASKS)
: «Allows an application to change the Z-order of tasks,» det vil si at appen kan plassere seg selv i forgrunnen, foran den appen som allerede er der. [(kilde)](https://developer.android.com/guide/components/activities/tasks-and-back-stack.html)

[`READ_SYNC_SETTINGS`](https://developer.android.com/reference/android/Manifest.permission.html#READ_SYNC_SETTINGS)
: «Allows applications to read the sync settings.» Sammen med `WRITE_SYNC_SETTINGS` (nedenfor) lar denne tillatelsen appen sette opp synkronisering av egne data. Jeg vil anta at dette ikke gir appen mulighet til å endre eller lese av andre appers synkroniserings-prosesser (f.eks. av avtaler i kalenderen). Les mer [her](https://developer.android.com/training/sync-adapters/creating-sync-adapter.html).

[`WRITE_SYNC_SETTINGS`](https://developer.android.com/reference/android/Manifest.permission.html#WRITE_SYNC_SETTINGS)
: «Allows applications to write the sync settings.»

[`READ_SYNC_STATS`](https://developer.android.com/reference/android/Manifest.permission.html#READ_SYNC_STATS)
: «Allows applications to read the sync stats.»

[`REQUEST_IGNORE_BATTERY_OPTIMIZATIONS`](https://developer.android.com/reference/android/Manifest.permission.html#REQUEST_IGNORE_BATTERY_OPTIMIZATIONS)
: Lar en app slippe å bli berørt av batterisparingstiltak.

[`REQUEST_DELETE_PACKAGES`](https://developer.android.com/reference/android/Manifest.permission.html#REQUEST_INSTALL_PACKAGES)
: «Allows an application to request deleting packages.»

[`REQUEST_INSTALL_PACKAGES`](https://developer.android.com/reference/android/Manifest.permission.html#REQUEST_INSTALL_PACKAGES)
: «Allows an application to request installing packages.»

[`SET_TIME_ZONE`](https://developer.android.com/reference/android/Manifest.permission.html#SET_TIME_ZONE)
: «Allows applications to set the system time zone.» (Men det står at denne tillatensen ikke er for tredjeparts-apper.)

[`SET_WALLPAPER`](https://developer.android.com/reference/android/Manifest.permission.html#SET_WALLPAPER)
: «Allows applications to set the wallpaper.»

[`SET_WALLPAPER_HINTS`](https://developer.android.com/reference/android/Manifest.permission.html#SET_WALLPAPER_HINTS)
: «Allows applications to set the wallpaper hints.» *Hint* [er](https://developer.android.com/reference/android/app/WallpaperManager.html) «The rectangular subregion of the streamed image that should be displayed as wallpaper.»

[`WAKE_LOCK`](https://developer.android.com/reference/android/Manifest.permission.html#WAKE_LOCK)
: «Allows using PowerManager WakeLocks to keep processor from sleeping or screen from dimming.»


## Trolig harmløs

[`ACCESS_LOCATION_EXTRA_COMMANDS`](https://developer.android.com/reference/android/Manifest.permission.html#ACCESS_LOCATION_EXTRA_COMMANDS)
: Det [virker](https://stackoverflow.com/questions/9917888/android-access-location-extra-commands-permission-uses) som om denne har en slags hjelpefunksjon dersom appen allerede har tilgang til stedstjenester. Hvis den har noe skadepotensial, tyder ingen søkeresultater på at det er blitt utnyttet. (Men hvorfor er ikke denne tillatelsen da integrert i tillatelsen for tilgang til stedstjenester?)

[`ACCESS_NOTIFICATION_POLICY`](https://developer.android.com/reference/android/Manifest.permission.html#ACCESS_NOTIFICATION_POLICY)
: [Gir tilgang](https://developer.android.com/reference/android/app/NotificationManager.Policy.html) til hvor høyt forskjellige typer varsler (anrop, anrop fra kontakter, anrop fra sternemerkede kontakter, gjentatte anrop fra samme nummer, meldinger osv.) prioriteres. Det virker ikke som om den kan gi tilgang til identitene til dem (kontaktene, telefonnumrene) som tilhører de forskjellige gruppene.

[`BROADCAST_STICKY`](https://developer.android.com/reference/android/Manifest.permission.html#BROADCAST_STICKY)
: «Allows an application to broadcast sticky intents. These are broadcasts whose data is held by the system after being finished, so that clients can quickly retrieve that data without having to wait for the next broadcast.» Dette høres skumlere ut enn det er. Det er snakk om at en opplysning en app sender til systemet (f.eks. batteristatus), beholdes i systemet slik at en annen app kan hente den uten at det første appen må sende den på nytt. Les mer [her](https://stackoverflow.com/questions/26038839/knowing-about-sticky-intent-in-android).

[`RECEIVE_BOOT_COMPLETED`](https://developer.android.com/reference/android/Manifest.permission.html#RECEIVE_BOOT_COMPLETED)
: «Allows an application to receive the `ACTION_BOOT_COMPLETED` that is broadcast after the system finishes booting.»

[`SET_ALARM`](https://developer.android.com/reference/android/Manifest.permission.html#SET_ALARM)
: «Allows an application to broadcast an Intent to set an alarm for the user.» Appen kan be brukeren om å aktivere en alarm; den kan ikke aktivere en alarm selv.

[`VIBRATE`](https://developer.android.com/reference/android/Manifest.permission.html#VIBRATE)
: «Allows access to the vibrator.»

[`USE_FINGERPRINT`](https://developer.android.com/reference/android/Manifest.permission.html#USE_FINGERPRINT)
: «Allows an app to use fingerprint hardware.» At dette gir appen tilgang til selve fingeravtrykkene som er lagret, kan jeg ikke tenke meg.
