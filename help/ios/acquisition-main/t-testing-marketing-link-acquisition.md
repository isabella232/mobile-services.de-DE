---
description: Die folgenden Anweisungen helfen Ihnen dabei, eine Hin&Zurück-Abfrage für eine Akquise-Kampagne mit einem Marketing-Link vorzunehmen, der auf einem Gerätefingerabdruck basiert.
keywords: android;library;mobile;sdk
seo-description: Die folgenden Anweisungen helfen Ihnen dabei, eine Hin&Zurück-Abfrage für eine Akquise-Kampagne mit einem Marketinglink vorzunehmen, der auf einem Gerätefingerabdruck basiert.
seo-title: Marketinglink-Akquise testen
solution: Experience Cloud,Analytics
title: Marketing-Link-Akquise testen
topic: Developer and implementation
uuid: 69503e01-182d-44c6-b0fb-e1c012ffa3bd
translation-type: tm+mt
source-git-commit: ae16f224eeaeefa29b2e1479270a72694c79aaa0
workflow-type: tm+mt
source-wordcount: '562'
ht-degree: 100%

---


# Marketinglink-Akquise testen {#testing-marketing-link-acquisition}

Die folgenden Anweisungen helfen Ihnen dabei, eine Hin&amp;Zurück-Abfrage für eine Akquise-Kampagne mit einem Marketinglink vorzunehmen, der auf einem Gerätefingerabdruck basiert.

1. Führen Sie die erforderlichen Schritte in [App-Akquise](/help/ios/acquisition-main/acquisition.md) aus.
1. Klicken Sie auf der Adobe Mobile Services-Benutzeroberfläche auf **[!UICONTROL Marketing Links Builder]** und generieren Sie eine Akquise-Marketing-Link-URL, die den App Store als das Ziel für iOS-Geräte festlegt.

   Beispiel:

   ```
   https://c00.adobe.com/v3/da120731d6c09658b82d8fac78da1d5fc2d09c48e21b3a55f9e2d7344e08425d/start?a_dl=57477650072932ec6d3a470f
   ```

   Weitere Informationen finden Sie unter [Marketing Links Builder](/help/using/acquisition-main/c-marketing-links-builder/c-marketing-links-builder.md).


1. Öffnen Sie den generierten Link auf dem iOS-Gerät und öffnen Sie `https://c00.adobe.com/v3/<appid>/end`.

   Es sollte „contextData“ in der JSON-Antwort angezeigt werden:

   ```js
   {"fingerprint":"bae91bb778f0ad52e37f0892961d06ac6a5c935b","endCallbacks":["***"],"timestamp":1464301217,"appguid":"da120731d6c09658b82d8fac78da1d5fc2d09c48e21b3a55f9e2d7344e08425d","contextData":
   {"a.launch.campaign.trackingcode":"twdf4546","a.referrer.campaign.name":"iOS Demo","a.referrer.campaign.trackingcode":"twdf4546"}
   ,"adobeData":{"unique_id":"8c14098d7c79e8a180c15e4b2403549d3cc21ea8","deeplinkid":"57477650072932ec6d3a470f"}}
   ```

1. Stellen Sie sicher, dass die folgenden Einstellungen in Ihrer Konfigurationsdatei vorhanden sind:

   | Wenn | Wert |
   |--- |--- |
   | Akquise | Der Server sollte `c00.adobe.com` sein. `appid` sollte der *`appid`* in Ihrem Akquise-Link entsprechen. |
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

   Falls diese Protokolle nicht angezeigt werden, sollten Sie sicherstellen, dass Sie die Schritte 4 und 5 abgeschlossen haben.

   Im Folgenden finden Sie einige Informationen zu möglichen Fehlern:

   * `Analytics - Unable to retrieve acquisition service response (<error message>)`:

      Netzwerkfehler.

   * `Analytics - Unable to parse acquisition service response (<error message>)`

      Die Antwort weist kein korrektes Format auf.

   * `Analytics - Unable to parse acquisition service response (no contextData parameter in response)`

      In der Antwort ist kein `contextData`-Parameter enthalten.

   * `Analytics - Acquisition referrer data was not complete, ignoring`

      `a.referrer.campaign.name` ist nicht in `contextData` vorhanden.

   * `Analytics - Acquisition referrer timed out`

      Fehler beim Abrufen der Antwort in der durch `referrerTimeout` definierten Zeit. Erhöhen Sie den Wert und versuchen Sie es erneut. Sie sollten auch sicherstellen, dass Sie den Akquise-Link vor der Installation der App geöffnet haben und dass Sie dasselbe Netzwerk verwenden, wenn Sie auf die URL klicken und die App öffnen.

Beachten Sie die folgenden Informationen:

* Der Akquiseserver bietet eine Zuordnungsübereinstimmung, die auf der IP-Adresse und den „user-agent“-Informationen basiert, die beim Klicken auf den Link (Schritt 6) und beim Start der App (Schritt 7) aufgezeichnet werden.

   Sie sollten sich im selben Netzwerk befinden, wenn Sie auf die URL klicken und wenn Sie die App öffnen.

* Durch die Verwendung von HTTP-Überwachungstools können über die App gesendete Treffer überwacht werden, um die Verifizierung der Akquisezuordnung bereitzustellen.

   Es sollten eine Anfrage vom Typ `/v3/<appid>/start` und eine Anfrage vom Typ `/v3/<appid>/end` angezeigt werden, die an den Akquiseserver gesendet werden.

* Variationen in „user-agent“ führen möglicherweise dazu, dass die Zuordnung fehlschlägt.

   Vergewissern Sie sich, dass `https://c00.adobe.com/v3/<appid>/start` und `https://c00.adobe.com/v3/<appid>/end` über dieselben Werte für „user-agent“ verfügen.

* Der Akquiselink und der Treffer aus dem SDK sollten dasselbe HTTP-/HTTPS-Protokoll verwenden.

   Wenn der Link und der Treffer unterschiedliche Protokolle verwenden (beispielsweise verwendet der Link HTTP und das SDK HTTPS), kann die IP-Adresse bei einigen Betreibern für jede Anfrage unterschiedlich sein. Dies könnte zu Fehlern bei der Zuordnung führen.

* Die Marketinglinks werden serverseitig mit einer zehnminütigen Ablaufzeit zwischengespeichert.

   Wenn Sie Änderungen an den Marketinglinks vornehmen, sollten Sie etwa 10 Minuten warten, bevor Sie die Links verwenden.