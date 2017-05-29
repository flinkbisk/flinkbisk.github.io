Mange kjenner til alle tillatelsene programmer (apper) i Android enten gir seg selv (i eldre versjoner) eller spør om (i nyere versjoner), f.eks. tilgang til kameraet, til mikrofonen, til å ringe. På fagspråket kalles denne type tillatelser *farlige tillatelser.* I Androids egen dokumentasjon kan vi lese:

> *Dangerous* permissions cover areas where the app wants data or resources that involve the user's private information, or could potentially affect the user's stored data or the operation of other apps. For example, the ability to read the user's contacts is a dangerous permission. If an app declares that it needs a dangerous permission, the user has to explicitly grant the permission to the app. [[#]](https://developer.android.com/guide/topics/permissions/requesting.html#normal-dangerous)

Dersom en tenker seg om, vil en innse at det også finnes en rekke ting programmer kan gjøre uten noen spesielle tillatelser, f.eks. å koble til internett. Også disse tingene har et navn, nemlig *normale tillatelser:*

> *Normal* permissions cover areas where your app needs to access data or resources outside the app's sandbox, but where there's very little risk to the user's privacy or the operation of other apps. For example, permission to set the time zone is a normal permission. If an app declares that it needs a normal permission, the system automatically grants the permission to the app. [[#]](https://developer.android.com/guide/topics/permissions/requesting.html#normal-dangerous) 

Så la oss ta en titt på [alt dette](https://developer.android.com/guide/topics/permissions/normal-permissions.html) som utgjør «veldig lite risiko» for brukerens privatsfære.

`ACCESS_LOCATION_EXTRA_COMMANDS`
: Det [virker](https://stackoverflow.com/questions/9917888/android-access-location-extra-commands-permission-uses) som om denne har en slags hjelpefunksjon dersom programmet allerede har tilgang til stedstjenester. Hvis den har noe skadepotensial, tyder ingen søkeresultater på at det er blitt utnyttet.
`ACCESS_NETWORK_STATE`
: Dette gir programmet tilgang til å [lese av «grovkornet nettverksstatus»](https://developer.android.com/reference/android/net/NetworkInfo.State.html), dvs. om telefonen er tilkoblet/frakoblet/kobles til/kobles fra et nettverk.
`ACCESS_NOTIFICATION_POLICY`
: [Gir tilgang](https://developer.android.com/reference/android/app/NotificationManager.Policy.html) til hvor høyt forskjellige typer varsler (anrop, anrop fra kontakter, anrop fra sternemerkede kontakter, gjentatte anrop fra samme nummer, meldinger osv.) prioriteres. Det virker ikke som om den kan gi tilgang til identitene til avsenderne.
ACCESS_WIFI_STATE
BLUETOOTH
BLUETOOTH_ADMIN
BROADCAST_STICKY
CHANGE_NETWORK_STATE
CHANGE_WIFI_MULTICAST_STATE
CHANGE_WIFI_STATE
DISABLE_KEYGUARD
EXPAND_STATUS_BAR
GET_PACKAGE_SIZE
INSTALL_SHORTCUT
INTERNET
KILL_BACKGROUND_PROCESSES
MODIFY_AUDIO_SETTINGS
NFC
READ_SYNC_SETTINGS
READ_SYNC_STATS
RECEIVE_BOOT_COMPLETED
REORDER_TASKS
REQUEST_IGNORE_BATTERY_OPTIMIZATIONS
REQUEST_INSTALL_PACKAGES
SET_ALARM
SET_TIME_ZONE
SET_WALLPAPER
SET_WALLPAPER_HINTS
TRANSMIT_IR
UNINSTALL_SHORTCUT
USE_FINGERPRINT
VIBRATE
WAKE_LOCK
WRITE_SYNC_SETTINGS
