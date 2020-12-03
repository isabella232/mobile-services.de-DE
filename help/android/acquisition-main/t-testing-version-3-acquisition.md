---
description: Diese Informationen helfen Ihnen dabei, eine Hin&Zurück-Abfrage für einen Version-3-Akquise-Kampagnenlink auf einem Android-Gerät durchzuführen.
keywords: android;library;mobile;sdk
seo-description: Diese Informationen helfen Ihnen dabei, eine Hin&Zurück-Abfrage für einen Version-3-Akquise-Kampagnenlink auf einem Android-Gerät durchzuführen.
seo-title: Testen der Version-3-Akquise
solution: Experience Cloud,Analytics
title: Testen der Version-3-Akquise
topic: Developer and implementation
uuid: 5e38b43d-389e-4412-99e5-3e6223b6ad28
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '820'
ht-degree: 100%

---


# V3-Akquise testen {#testing-version-acquisition}

Diese Informationen helfen Ihnen dabei, eine Hin&amp;Zurück-Abfrage für einen Version-3-Akquise-Kampagnenlink auf einem Android-Gerät durchzuführen.

>[!IMPORTANT]
>
>Die Akquise in Version 3 bezieht sich auf die Akquise-Links, die Sie mithilfe des Akquise-Builders auf der Adobe Mobile Services-Benutzeroberfläche erstellen. Um diese Funktion verwenden zu können, müssen Sie auf Android SDK 4.x für Experience Cloud-Lösungen 4.6.0 oder höher aktualisieren.

Wenn sich die App noch nicht in Google Play befindet, wählen Sie beim Erstellen des Kampagne-Links eine beliebige App als Ziel aus. Dies betrifft nur die App, zu der Sie der Akquise-Server weiterleitet, nachdem Sie auf den Akquise-Link geklickt haben, hat jedoch keine Auswirkungen auf die Fähigkeit, den Link zu testen. Zeichenfolgenparameter der Abfrage werden an den Google Play Store übergeben, der bei der Installation im Zuge einer Kampagnenübertragung an die App übergeben wird. Für die Tests zur Akquise von Hin&amp;Zurück-Abfragen mobiler Apps ist die Simulation dieser Art von Übertragungen erforderlich.

>[!IMPORTANT]
>
>Wenn Sie die Implementierung mit den Install-Referrer-APIs von Google Play durchführen, können Sie die Akquise erst testen, wenn sich Ihre App im Google Play Store befindet.

Vor jedem Testlauf muss die App neu installiert bzw. müssen ihre Daten in den **[!UICONTROL Einstellungen]** gelöscht werden. So wird gewährleistet, dass die anfänglichen Lebenszyklusmetriken mit den Abfragezeichenfolgen-Parametern der Kampagne gesendet werden, wenn die App zum ersten Mal gestartet wird.

1. Führen Sie die erforderlichen Aufgaben in [App-Akquise](/help/android/acquisition-main/acquisition.md) aus und stellen Sie sicher, dass Sie den Broadcast-Empfänger für `INSTALL_REFERRER` ordnungsgemäß implementiert haben.

1. Klicken Sie in der Adobe Mobile Services-Benutzeroberfläche auf **[!UICONTROL Akquise]** > **[!UICONTROL Marketing Links Builder]** und generieren Sie eine Akquise-Marketinglink-URL, die Google Play als Ziel für Android-Geräte festlegt.

   Weitere Informationen finden Sie unter [Marketing Links Builder](/help/using/acquisition-main/c-marketing-links-builder/c-marketing-links-builder.md).

   Beispiel: `https://c00.adobe.com/v3/<appid>/start?a_i_id=iostestapp&a_g_id=com.adobe.android&a_dd=g&ctxa.referrer.campaign.name=name&ctxa.referrer.campaign.trackingcode=trackingcode`.

   >[!TIP]
   >
   >Wenn Sie im Akquise-Link sowohl auf die Android- als auch auf die iOS-App verweisen, nutzen Sie Google Play als standardmäßigen Store.

1. Öffnen Sie den generierten Link in einem Desktop-Browser.

   Sie sollten auf eine Seite umgeleitet werden, deren URL folgendem Beispiel ähnelt:
   `https://play.google.com/store/apps/details?id=com.adobe.android&referrer=utm_campaign%3Dadb_acq_v3%26utm_source%3Dadb_acq_v3%26utm_content%3D91b52ce097b1464b9b47cb2995c493cc6ab2c3a3`

1. Kopieren Sie die eindeutige ID hinter `utm_content%3D`.

   Im vorherigen Beispiel lautet die ID `91b52ce097b1464b9b47cb2995c493cc6ab2c3a3`.

1. Erstellen Sie einen Akquise-Endlink mithilfe der eindeutigen URL aus Schritt 3. Verwenden Sie hierfür folgendes Format:

   `https://c00.adobe.com/v3/<appid>/end?a_ugid=<unique id>`.

   Beispiel: `https://c00.adobe.com/v3/<appid>/end?a_ugid=91b52ce097b1464b9b47cb2995c493cc6ab2c3a3`.

1. Öffnen Sie den Link in einem Desktop-Browser.

   Sie sollten die Kontextdaten ( `contextData` ) in der JSON-Antwort sehen:

   `{"fingerprint":"228d7e6058b1d731dc7a8b8bd0c15e1d78242f31","timestamp":1457989293,"appguid":"","contextData":{"a.referrer.campaign.name":"name","a.referrer.campaign.trackingcode":"trackingcode"}}.`

   Wenn die Kontextdaten ( `contextData` ) nicht angezeigt werden oder Teile der Zeichenfolge fehlen, stellen Sie sicher, dass die Akquise-URL das Format aus [Akquise-Link manuell erstellen](/help/using/acquisition-main/c-marketing-links-builder/acquisition-link-manual.md) aufweist.
1. Wiederholen Sie Schritt 3, um eine neue eindeutige URL zu erhalten.
1. Stellen Sie sicher, dass die folgenden Einstellungen in Ihrer Konfigurationsdatei vorhanden sind:

   | Wenn | Wert |
   |--- |--- |
   | Akquise | Der Server sollte `c00.adobe.com` sein. *`appid`* sollte der `appid` in Ihrem Akquise-Link entsprechen. |
   | analytics | Legen Sie für Testzwecke das Zeitlimit des Werbers so fest, dass ausreichend Zeit (mindestens 60 Sekunden) zum manuellen Durchführen des Versands zur Verfügung steht. Sie können die ursprüngliche Zeitlimiteinstellung nach dem Test wiederherstellen. |

1. Verbinden Sie das Gerät mit einem Computer, deinstallieren Sie die App und installieren Sie sie anschließend erneut.
1. Starten Sie ADB Shell und rufen Sie die Anwendung auf dem Gerät auf.
1. Senden Sie einen Broadcast mithilfe des folgenden `adb`-Befehls:

   `am broadcast -a com.android.vending.INSTALL_REFERRER -n com.adobe.android/com.adobe.android.YourBroadcastReceiver --es "referrer" "utm_source=adb_acq_v3&utm_campaign=adb_acq_v3&utm_content=<unique id get on step 5>"`

1. Führen Sie die folgenden Schritte aus:
   1. Ersetzen Sie `com.adobe.android` durch den Paketnamen Ihrer Anwendung.
   1. Ändern Sie die Empfängerreferenz zum Standort des Kampagnenverfolgungs-Empfängers in Ihrer App
   1. Ersetzen Sie die Werte für `utm_content`.

   Wenn der Broadcast erfolgreich ist, können Sie eine Antwort ähnlich der folgenden erhalten:

   `Broadcasting: Intent
{ act=com.android.vending.INSTALL_REFERRER cmp=com.adobe.adms.tests/.ReferralReceiver (has extras) }
Broadcast completed: result=0`

1. (Optional) Sie können die Debugging-Protokollierung des SDK aktivieren, um zusätzliche Informationen zu erhalten.

   Wenn alles funktioniert, sollten Sie folgende Protokolle erhalten:

`"Analytics - Received referrer information(<referrer content>)"   "Analytics - Trying to fetch referrer data from (acquisition end url)"; "Analytics - Received Referrer Data(<A JSON Response>)"`

Falls die Protokolle oben nicht angezeigt werden, sollten Sie sicherstellen, dass Sie die Schritte 6 bis 12 abgeschlossen haben.

Die folgende Tabelle enthält weitere Informationen zu möglichen Fehlern:

| Fehler | Beschreibung |
|--- |--- |
| Analytics - Unable to decode response(*String*). | Die Antwort ist falsch formatiert. |
| Analytics - Unable to parse response (*a JSON Response*). | Die JSON-Zeichenfolge ist falsch formatiert. |
| Analytics - Unable to parse acquisition service response (no contextData parameter in response). | In der Antwort ist kein contextData-Parameter enthalten. |
| Analytics - Acquisition referrer data was not complete (no `a.referrer.campaign.name` in context data), ignoring. | `a.referrer.campaign.name` ist nicht in contextData vorhanden. |
| Analytics - Acquisition referrer timed out. | Die Antwort konnte nicht in der durch `referrerTimeout` festgelegten Zeit abgerufen werden. Erhöhen Sie den Wert und versuchen Sie es erneut.  Sie sollten auch sicherstellen, dass Sie den Akquise-Link geöffnet haben, bevor Sie die App installieren. |

Beachten Sie die folgenden Informationen:

* Treffer, die von der App gesendet werden, können mithilfe von HTTP-Überwachungstools überwacht werden, um die Akquise-Zuordnung zu überprüfen.
* Weitere Informationen zu `INSTALL_REFERRER`-Broadcasts finden Sie unter [Testen der Google Play-Kampagnenmessung](https://developers.google.com/analytics/solutions/testing-play-campaigns) im Google Developers-Handbuch.

* Für Android 4.8.2 wurde eine Fehlerbehebung veröffentlicht.

   Aktualisieren Sie das SDK vor dem Testen auf die neueste Version.

* Sie können das bereitgestellte Java-Tool `acquisitionTest.jar` verwenden, um die eindeutige ID abzurufen und den Installations-Referrer-Broadcast durchzuführen. So erhalten Sie die Informationen aus den Schritten 3 bis 12.

   **Java-Tool installieren**

So installieren Sie das Java-Tool:

1. Laden Sie die Datei [`acquisitionTester.zip`](/help/android/assets/acquisitionTester.zip) herunter.

1. Extrahieren Sie die JAR-Datei.

   Sie können die Datei in der Befehlszeile ausführen.

   Beispiel:

   ```java
   java -jar acquisitionTester.jar -a com.adobe.test -r com.adobe.test.ReferrerReceiver -l "https://c00.adobe.com/v3/appid/start?a_i_id=123456&a_g_id=com.adobe.test&a_dd=i&ctxa.referrer.campaign.name=name&ctxa.referrer.campaign.trackingcode=1234
   ```
