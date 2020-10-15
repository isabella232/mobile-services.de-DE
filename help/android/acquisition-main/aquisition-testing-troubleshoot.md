---
description: Die folgenden Informationen helfen Ihnen bei der Fehlerbehebung von Problemen beim Akquisetest.
keywords: android;Acquisition;testing
seo-description: Die folgenden Informationen helfen Ihnen bei der Fehlerbehebung von Problemen beim Akquisetest.
seo-title: Fehlerbehebung beim Akquisetest
solution: Experience Cloud,Analytics
title: Fehlerbehebung beim Akquisetest
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '251'
ht-degree: 100%

---


# Fehlerbehebung beim Akquisetest {#aquistion-testing-troubleshooting}

Im Folgenden sind einige Probleme aufgeführt, die beim Testen von Acquisition auftreten können, sowie einige mögliche Lösungen:

* Falls nicht anders angegeben, sollte die Datei ADBMobileConfig.json im Ordner „Assets“ abgelegt werden.

* Beim Namen wird zwischen Groß- und Kleinschreibung unterschieden. Verwenden Sie daher keine Kleinbuchstaben.

   Sie müssen sicherstellen, dass `Config.setContext(this.getApplicationContext())` aus der Hauptaktivität aufgerufen wird. Weitere Informationen finden Sie unter [Konfigurationsmethoden](https://docs.adobe.com/content/help/de-DE/mobile-services/android/configuration-android/methods.html).

* In der bereitgestellten Datei AndroidManifest.xml fehlen einige Benutzerberechtigungen. Diese sind erforderlich, um Daten zu senden und Offline-Tracking-Aufrufe aufzuzeichnen:

   ```html
   <manifest..>
   ... 
   <uses-permission android:name="android.permission.INTERNET" />
   <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
   </manifest>
   ```

* Wenn „referrer timeout“ in Ihrer Konfiguration auf `referrerTimeout: 5` gesetzt ist, müssen Sie den Installations-Intent innerhalb von 5 Sekunden nach der Installation und dem ersten Start der App senden, um die am Installationstreffer angehängten Referrer-Informationen anzuzeigen.

   Erhöhen Sie den Wert `referrerTimeout` für manuelle Tests auf 10–15 Sekunden, damit Sie genügend Zeit haben, die Referrer-Informationen zu senden, bevor der Installationstreffer verarbeitet wird.

* Es ist wichtig, dass Sie alle Schritte in der [Testing Marketing Link-Akquise](https://docs.adobe.com/content/help/de-DE/mobile-services/android/acquisition-android/t-testing-marketing-link-acquisition.html) in der Reihenfolge ausführen und sicherstellen, dass Sie `adb` Shell und dann Folgendes ausführen:

   ```java
   am broadcast -a com.android.vending.INSTALL_REFERRER -n 
   nl.postnl.app/.tracking.AdobeAcquisitionLinkBroadcastReceiver --es "referrer"
   "utm_source=adb_acq_v3&utm_campaign=adb_acq_v3&utm_content=<the newly generated id at step #7>"
   ```

>[!IMPORTANT]
>
>Um den Referrer-Intent korrekt zu verarbeiten, müssen Sie diese beiden Befehle unabhängig voneinander ausführen.  Andernfalls wird `adb` die Referrer-Informationen maskieren und die vom Broadcast-Empfänger empfangenen Daten sind unvollständig.
