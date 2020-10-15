---
description: Dieses Thema enthält Informationen zur Fehlerbehebung bei Problemen, die während des Akquisetests auftreten können.
keywords: android;library;mobile;sdk
seo-description: Dieses Thema enthält Informationen zur Fehlerbehebung bei Problemen, die während des Akquisetests auftreten können.
seo-title: Fehlerbehebung beim Akquisetest
solution: Experience Cloud,Analytics
title: Fehlerbehebung beim Akquisetest
topic: Developer and implementation
translation-type: ht
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: ht
source-wordcount: '248'
ht-degree: 100%

---


# Fehlerbehebung beim Akquisetest {#troubleshoot-acquisition-testing}

Dieses Thema enthält Informationen zur Fehlerbehebung bei Problemen, die während des Akquisetests auftreten können.

* Falls nicht anders angegeben, sollte die Datei ADBMobileConfig.json im Ordner `assets` abgelegt werden.

   Beim Namen wird zwischen Groß- und Kleinschreibung unterschieden. Verwenden Sie daher keine Groß- oder Kleinbuchstaben.

* Stellen Sie sicher, dass `Config.setContext(this.getApplicationContext())` von Ihrer Hauptaktivität aufgerufen wird.

   Weitere Informationen finden Sie unter [Konfigurationsmethoden](https://docs.adobe.com/content/help/de-DE/mobile-services/android/configuration-android/methods.html).

* Stellen Sie sicher, dass die erforderlichen Berechtigungen für das Mobile SDK in der Datei `AndroidManifest.xml` vorhanden sind:

   ```html
   <manifest ..>
   ... 
   <uses-permission android:name="android.permission.INTERNET" />
   <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
   </manifest>
   ```

* Wenn der Wert `referrerTimeout` in der Datei ADMobileConfig.json auf 5 gesetzt ist, müssen Sie den Installations-Intent innerhalb von 5 Sekunden nach der Installation und dem ersten Start der App senden, um die an den Installationstreffer angehängten Referrer-Informationen anzuzeigen.

   Für manuelle Tests wird empfohlen, den Wert `referrerTimeout` auf 10–15 Sekunden zu erhöhen, damit Sie genügend Zeit haben, die Referrer-Informationen zu senden, bevor der Installationstreffer verarbeitet wird.

* Führen Sie alle Schritte unter [Testen der Marketinglink-Akquise](https://docs.adobe.com/content/help/de-DE/mobile-services/android/acquisition-android/t-testing-marketing-link-acquisition.html) aus und stellen Sie sicher, dass Sie den `adb shell` Befehl zuerst und dann Folgendes ausführen:

   ```java
   am broadcast -a com.android.vending.INSTALL_REFERRER -n nl.postnl.app/.tracking.AdobeAcquisitionLinkBroadcastReceiver --es "referrer" "utm_source=adb_acq_v3&utm_campaign=adb_acq_v3&utm_content=<the newly generated id at step #7>"
   ```

>[!IMPORTANT]
>
>Um den Referrer-Intent korrekt zu verarbeiten, müssen Sie diese beiden Befehle unabhängig voneinander ausführen. Andernfalls wird `adb` den Referrer-Informationen doppelt entgehen und die vom Broadcast-Empfänger empfangenen Daten sind unvollständig.

