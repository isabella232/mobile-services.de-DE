---
description: Mithilfe dieser Informationen können Probleme mit Push-Nachrichten behoben werden.
keywords: mobile
seo-description: Mithilfe dieser Informationen können Probleme mit Push-Nachrichten behoben werden.
seo-title: Fehlerbehebung für Push-Nachrichten
solution: Marketing Cloud, Analytics
title: Fehlerbehebung für Push-Nachrichten
topic: Metriken
uuid: c 7 be 4 ab 7-0 cfe -4296-84 a 8-01412 f 4 fd 93 f
translation-type: tm+mt
source-git-commit: e9691f9cbeadd171948aa752b27a014c3ab254d6

---


# Troubleshooting push messaging{#troubleshooting-push-messaging}

Mithilfe dieser Informationen können Probleme mit Push-Nachrichten behoben werden.

## Warum gibt es beim Senden von Push-Nachrichten manchmal Verzögerungen?

Folgende Verzögerungen können bei Push-Nachrichten für Mobile Services auftreten:

* **Warten auf Analytics-Treffer**

   Jede Report Suite verfügt über eine Einstellung, die festlegt, wann eingehende Analytics-Treffer verarbeitet werden sollen. Standardmäßig geschieht dies einmal pro Stunde.

   Die eigentliche Verarbeitung von Analytics-Treffern kann bis zu 30 Minuten dauern, in der Regel sind es jedoch 15 bis 20 Minuten. Angenommen, eine Report Suite verarbeitet Treffer stündlich. Wenn Sie die maximale Zeit von 30 Minuten einberechnen, kann es bis zu 90 Minuten dauern, bis ein eingehender Treffer für eine Push-Nachricht verfügbar ist. Wenn ein Benutzer die App um 9:01 Uhr gestartet hat, wird der Treffer in der Mobile Services-Benutzeroberfläche als neuer Unique User zwischen 10:15 und 10:30 Uhr angezeigt.

* **Warten auf den Push-Dienst**

   Der Push-Dienst (APNS oder GCM) sendet die Nachricht möglicherweise nicht direkt. Zwar sind sie ungewöhnlich, jedoch wurden bereits Wartezeiten von 5–10 Minuten festgestellt. Informationen dazu, ob die Push-Nachricht gesendet wurde, finden Sie in der **[!UICONTROL Berichtsansicht]** der Push-Nachricht. Suchen Sie dort in der Tabelle **[!UICONTROL Nachrichtenverlauf]nach der Nachricht und ermitteln Sie die Anzahl** Veröffentlicht **.**

   >[!TIP]
   >
   >Diese Anzahl ist die Anzahl erfolgreicher Übertragungen an die Push-Dienste. Die Push-Dienste garantieren nicht, dass eine Nachricht gesendet wird.

   Weitere Informationen zur Zuverlässigkeit des Dienstes finden Sie unter:

   * [Servicequalität](https://developer.apple.com/library/content/documentation/NetworkingInternet/Conceptual/RemoteNotificationsPG/APNSOverview.html#//apple_ref/doc/uid/TP40008194-CH8-SW5l)
   * [Lebensdauer einer Nachricht](https://developers.google.com/cloud-messaging/concept-options#lifetime).

## Warum ist mein Android-GCM-API-Schlüssel ungültig?

* **Ungültiger API-Schlüssel**

   Ihr API-Schlüssel kann aus zwei Gründen ungültig sein:

   * Bei dem von Ihnen angegebenen API-Schlüssel handelt es sich nicht um einen Serverschlüssel mit dem richtigen GCM-API-Schlüsselwert.
   * Der Serverschlüssel hat die IPs auf die Whitelist gesetzt und hindert die Adobe-Server am Senden einer Push-Nachricht.

* **Gültigkeit des API-Schlüssels ermitteln**

   Führen Sie folgenden Befehl aus, um die Gültigkeit Ihres API-Schlüssels zu ermitteln:

   **Android**

   ```java
   # api_key=YOUR_API_KEY
   #curl--header"Authorization:key=$api_key"\
       --headerContent-Type:"application/json"\ 
       https://gcm-http.googleapis.com/gcm/send\
       -d"{\"registration_ids\":[\"ABC\"]}"
   ```

   Wenn der HTTP-Status-Code 401 zurückgegeben wird, ist Ihr API-Schlüssel ungültig. Andernfalls erhalten Sie eine etwa wie folgt aussehende Ausgabe:

   ```java
   {"multicast_id":6782339717028231855,"success":0,"failure":1,
   canonical_ids":0,"results":[{"error":"InvalidRegistration"}]}
   ```

   You can also check the validity of a registration token by replacing `"ABC"` with the token.

## Warum funktioniert mein APNS-Zertifikat nicht?

Ihr APNS-Zertifikat kann aus folgenden Gründen ungültig sein:

* Sie verwenden ein Sandbox-Zertifikat anstelle eines Produktionszertifikats.
* Sie verwenden ein nicht unterstütztes Produktions-/Sandbox-Zertifikat.
* You are using `.p8` file instead of a `.p12` file.

## Beheben von Push-Nachrichtenfehlern

**Ein Beispiel**

Im folgenden Beispiel wird veranschaulicht, wie Sie bei Verwendung einer VRS einen Push-Fehler beheben.

Der folgende Kunde verfügt über zwei iOS-Apps:

* App-Name: PhotoShop_app_iOS
   * Übergeordnete RSID: AllAdobe PhotoShop_apps
   * VRSID: PhotoShop_iOS_app_SF
   * VRSID Definition Segment: `a.appid contains “PhotoShop_iOS_app_SF”`
* App-Name: PhotoShop_app_iOS
   * Übergeordnete RSID: AllAdobe PhotoShop_apps
   * RSID: Photoshop_ ios_ app_ LA
   * VRSID Definition Segment: `a.os contains “iOS”`

In this example, if a Photoshop employee sends a push to the *PhotoShop_iOS_app_SF* app, all *PhotoShop_iOS_app_SF app* users receive the push message as expected. But, if the employee sends a message to the *PhotoShop_iOS_app_LA* app, because its VRSID Definition Segment is incorrect (`iOS` instead of `a.os contains "PhotoShop_iOS_app_LA"`), the message is sent to **all** iOS users in *AllAdobe PhotoShop_apps*. Although the message still goes to *PhotoShop_iOS_app_LA* users, the message also blacklists the push IDs for *PhotoShop_iOS_app_SF* users because the *PhotoShop_iOS_app_SF* app has a different certificate. If the segment had been defined as `a.os contains “PhotoShop_iOS_app_LA”`, the push message would have been sent to only *PhotoShop_iOS_app_LA* users.

If passed with the *PhotoShop_IOS_app_LA* push certificate, the push identifiers for the *PhotoShop_iOS_app_SF* come back as `invalid`.

>[!CAUTION]
>
>After you create a push message for an app that is using a VRS and click **[!UICONTROL Save &amp; Send]**, an alert appears that reminds you ensure that each app that is listed **must** have a valid certificate. Wenn nicht **alle** Apps über ein gültiges Zertifikat verfügen, werden Ihre Zielgruppensegmente möglicherweise auf unbestimmte Zeit auf die Blacklist gesetzt, sodass Sie betroffenen Benutzern künftig keine Push-Nachrichten mehr senden können. Weitere Informationen zu Zielgruppensegmenten finden [Sie unter Zielgruppe: Definieren und Konfigurieren von Zielgruppenoptionen für Push-Nachrichten](/help/using/in-app-messaging/t-create-push-message/c-audience-push-message.md).
