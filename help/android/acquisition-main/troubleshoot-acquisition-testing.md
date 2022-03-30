---
description: Dieses Thema enthält Informationen zur Fehlerbehebung bei Problemen, die während des Akquisetests auftreten können.
keywords: Android;Bibliothek;Mobile;SDK
solution: Experience Cloud Services,Analytics
title: Fehlerbehebung beim Akquisetest
topic-fix: Developer and implementation
exl-id: 1ed2ad89-4e89-43da-aa21-f688b4d1c0d1
source-git-commit: 5434d8809aac11b4ad6dd1a3c74dae7dd98f095a
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 100%

---

# Fehlerbehebung beim Akquisetest {#troubleshoot-acquisition-testing}

Dieses Thema enthält Informationen zur Fehlerbehebung bei Problemen, die während des Akquisetests auftreten können.

* Falls nicht anders angegeben, sollte die Datei ADBMobileConfig.json im Ordner `assets` abgelegt werden.

   Beim Namen wird zwischen Groß- und Kleinschreibung unterschieden. Verwenden Sie daher keine Groß- oder Kleinbuchstaben.

* Stellen Sie sicher, dass `Config.setContext(this.getApplicationContext())` von Ihrer Hauptaktivität aufgerufen wird.

   Weitere Informationen finden Sie unter [Konfigurationsmethoden](../configuration/methods.md).

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

* Führen Sie alle Schritte unter [Testen der Marketinglink-Akquise](t-testing-marketing-link-acquisition.md) aus und stellen Sie sicher, dass Sie den `adb shell` Befehl zuerst und dann Folgendes ausführen:

   ```java
   am broadcast -a com.android.vending.INSTALL_REFERRER -n nl.postnl.app/.tracking.AdobeAcquisitionLinkBroadcastReceiver --es "referrer" "utm_source=adb_acq_v3&utm_campaign=adb_acq_v3&utm_content=<the newly generated id at step #7>"
   ```

>[!IMPORTANT]
>
>Um den Referrer-Intent korrekt zu verarbeiten, müssen Sie diese beiden Befehle unabhängig voneinander ausführen. Andernfalls wird `adb` den Referrer-Informationen doppelt entgehen und die vom Broadcast-Empfänger empfangenen Daten sind unvollständig.
