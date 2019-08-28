---
description: Die folgenden Anweisungen helfen Ihnen beim Roundtrip einer Akquise-Kampagne mit einem Marketing-Link, der auf einem Fingerabdruck des Geräts basiert.
keywords: android; library; mobile; sdk
seo-description: Die folgenden Anweisungen helfen Ihnen beim Roundtrip einer Akquise-Kampagne mit einem Marketing-Link, der auf einem Fingerabdruck des Geräts basiert.
seo-title: Testen von Marketing Link-Akquisen
solution: Marketing Cloud, Analytics
title: Testen von Marketing Link-Akquisen
topic: Entwickler und Implementierung
uuid: 69503 e 01-182 d -44 c 6-b 0 fb-e 1 c 012 ffa 3 bd
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# Testing Marketing Link acquisition {#testing-marketing-link-acquisition}

Die folgenden Anweisungen helfen Ihnen beim Roundtrip einer Akquise-Kampagne mit einem Marketing-Link, der auf einem Fingerabdruck des Geräts basiert.

1. Führen Sie die erforderlichen Schritte in der [Mobile App-Akquise aus](/help/ios/acquisition-main/acquisition.md).
1. In the Adobe Mobile Services UI, click **[!UICONTROL Marketing Links Builder]** and generate an acquisition Marketing Link URL that sets the App Store as the destination for iOS devices.

   Beispiel:

   ```
   https://c00.adobe.com/v3/da120731d6c09658b82d8fac78da1d5fc2d09c48e21b3a55f9e2d7344e08425d/start?a_dl=57477650072932ec6d3a470f
   ```

   Weitere Informationen finden Sie unter [Marketing Links Builder](/help/using/acquisition-main/c-marketing-links-builder/c-marketing-links-builder.md).


1. Open the generated link on the iOS device and open `https://c00.adobe.com/v3/<appid>/end`.

   Es sollte „contextData“ in der JSON-Antwort angezeigt werden:

   ```js{"fingerprint":"bae91bb778f0ad52e37f0892961d06ac6a5c935b","endCallbacks":["***"],"timestamp":1464301217,"appguid":"da120731d6c09658b82d8fac78da1d5fc2d09c48e21b3a55f9e2d7344e08425d","contextData":
   {"a.launch.campaign.trackingcode":"twdf4546","a.referrer.campaign.name":"iOS Demo","a.referrer.campaign.trackingcode":"twdf4546"}
   ,"adobeData":{"unique_id":"8c14098d7c79e8a180c15e4b2403549d3cc21ea8","deeplinkid":"57477650072932ec6d3a470f"}}
   ```

1. Stellen Sie sicher, dass die folgenden Einstellungen in Ihrer Konfigurationsdatei vorhanden sind:

   | Wenn | Wert |
   |--- |--- |
   | Akquise | The server should be  `c00.adobe.com`. `appid` sollte mit dem *`appid`* in Ihrem Akquise-Link übereinstimmen. |
   | analytics | `referrerTimeout` sollte einen Wert größer als 0 aufweisen. |

1. (Bedingt) Wenn die SSL-Einstellung in der Konfigurationsdatei Ihrer App `false` lautet, sollten Sie Ihren Akquiselink so aktualisieren, dass er das HTTP-Protokoll anstelle von HTTPS verwendet.
1. Klicken Sie auf dem Mobilgerät auf den generierten Link, auf dem Sie die App installieren möchten.

   Die Server von Adobe (`c00.adobe.com`) speichern den Fingerabdruck und nehmen eine Umleitung zum App-Store vor. Die App muss nicht für Testzwecke heruntergeladen werden.
1. Starten Sie die Anwendung erstmals auf demselben Mobilgerät, das Sie in Schritt 6 verwendet haben.

   Bei Bedarf können Sie die App löschen und erneut installieren.
1. (Optional) Aktivieren Sie die Debug-Protokollierung des SDK, um zusätzliche Informationen abzurufen.

   Wenn alles funktioniert, sollten Sie folgende Protokolle erhalten:

   `"Analytics - Trying to fetch referrer data from <acquisition end url>"`
   `"Analytics - Received Referrer Data(<Json Object>)"`

   Wenn diese Protokolle nicht angezeigt werden, überprüfen Sie, ob Sie die Schritte 4 und 5 abgeschlossen haben.

   Im Folgenden finden Sie einige Informationen zu möglichen Fehlern:

   * `Analytics - Unable to retrieve acquisition service response (<error message>)`:

      Netzwerkfehler.

   * `Analytics - Unable to parse acquisition service response (<error message>)`

      Die Antwort weist kein korrektes Format auf.

   * `Analytics - Unable to parse acquisition service response (no contextData parameter in response)`

      In der Antwort ist kein `contextData`-Parameter enthalten.

   * `Analytics - Acquisition referrer data was not complete, ignoring`

      `a.referrer.campaign.name` ist nicht enthalten `contextData`.

   * `Analytics - Acquisition referrer timed out`

      Fehler beim Abrufen der Antwort in der durch `referrerTimeout` definierten Zeit. Erhöhen Sie den Wert und versuchen Sie es erneut. Sie sollten darüber hinaus sicherstellen, dass Sie den Akquiselink geöffnet haben, bevor Sie die App installieren, und dass Sie dasselbe Netzwerk verwenden, wenn Sie auf die URL klicken und die App öffnen.

Beachten Sie die folgenden Informationen:

* Der Akquiseserver bietet eine Zuordnungsübereinstimmung, die auf der IP-Adresse und den „user-agent“-Informationen basiert, die beim Klicken auf den Link (Schritt 6) und beim Start der App (Schritt 7) aufgezeichnet werden.

   Sie sollten sich im selben Netzwerk befinden, wenn Sie auf die URL klicken und wenn Sie die App öffnen.

* Durch die Verwendung von HTTP-Überwachungstools können über die App gesendete Treffer überwacht werden, um die Verifizierung der Akquisezuordnung bereitzustellen.

   You should see one `/v3/<appid>/start` request and one `/v3/<appid>/end` request that are sent to the acquisition server.

* Variationen in „user-agent“ führen möglicherweise dazu, dass die Zuordnung fehlschlägt.

   Stellen Sie sicher `https://c00.adobe.com/v3/<appid>/start` , dass und `https://c00.adobe.com/v3/<appid>/end` dieselben Benutzeragenten-Werte vorhanden sind.

* Der Akquiselink und der Treffer aus dem SDK sollten dasselbe HTTP-/HTTPS-Protokoll verwenden.

   Wenn der Link und der Treffer verschiedene Protokolle verwenden, z. B. wenn der Link HTTP verwendet und das SDK HTTPS verwendet, kann sich die IP-Adresse für jede Anforderung auf einigen Netzbetreibern unterscheiden. Dies könnte zu Fehlern bei der Zuordnung führen.

* Die Marketing-Links werden auf dem Server mit einer Gültigkeitsdauer von zehn Minuten zwischengespeichert.

   Wenn Sie Änderungen an Marketing-Links vornehmen, sollten Sie ungefähr 10 Minuten warten, bevor Sie die Links verwenden.