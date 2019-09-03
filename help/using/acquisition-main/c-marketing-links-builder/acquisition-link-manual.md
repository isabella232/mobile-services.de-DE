---
description: Sie können Marketing-Links erstellen, um neue mobile App-Benutzer spontan zu akquirieren, indem Sie die URL-Parameter manuell konfigurieren.
keywords: mobile
seo-description: Sie können Marketing-Links erstellen, um neue mobile App-Benutzer spontan zu akquirieren, indem Sie die URL-Parameter manuell konfigurieren.
seo-title: Akquise-Links manuell erstellen
solution: Marketing Cloud, Analytics
title: Akquise-Links manuell erstellen
topic: Metriken
uuid: d 7709203-f 793-4982-adaa -9 c 3 c 914 aca 2 b
translation-type: tm+mt
source-git-commit: 54e3b2d673356a616987537d20758bef8b044db4

---


# Akquise-Links manuell erstellen {#create-acquisition-link-manually}

Sie können Marketing-Links erstellen, um neue mobile App-Benutzer spontan zu akquirieren, indem Sie die URL-Parameter manuell konfigurieren.

>[!IMPORTANT]
>
>Für diese Funktion ist SDK Version 4.6 oder höher erforderlich. Weitere Informationen finden Sie unter [Voraussetzungen für die Akquise](/help/using/acquisition-main/c-acquisition-prerequisites.md).

Das folgende Diagramm illustriert die Komponenten eines manuell erstellten Tracking-Links und zeigt die verschiedenen URL-Parameter an, die Sie beim manuellen Erstellen von Akquise-Links korrekt konfigurieren müssen.

![](assets/acquisition_url.png)

Dieser Link ist so konfiguriert, dass er für eine mobile App eine plattformspezifische Weiterleitung an den Google Play Store oder den Apple App Store durchführt. Für den Fall, dass das Ziel nicht bestimmt werden kann, wurde der Apple App Store als Standard festgelegt. Nachdem die App installiert wurde, wird der benutzerdefinierte Kontextschlüssel `my.custom.key:test` an den Treffer für die Analytics-Installation angehängt.

Wenn Sie Links manuell erstellen, verwenden Sie das folgende URL-Format:

`http(s)://c00.adobe.com/v3/ {mobile-services-app-hash}/start? {parameters}`

>[!TIP]
>
>Die verwendete Android-SDK hat keine Auswirkungen auf diesen Prozess.

Stellen Sie bei iOS sicher, dass Sie das richtige Protokoll verwenden:

* Use **HTTP** if you are using the iOS SDKs before version 4.7.0, or if you are using iOS SDK 4.7.0 or later, and if **[!UICONTROL Use HTTPS]** is **not** selected on the Manage App Settings page.
* Use **HTTPS** if you are using iOS SDK 4.7.0 or later and **[!UICONTROL Use HTTPS]** **is** selected on the Manage App Settings page.

Wo folgende Bedingungen erfüllt wurden:

* `{mobile-services-app-hash}` stimmt mit der Anwendungskennung in der Konfigurationsdatei `acquisition:appid ` überein.

   You can locate `{mobile-services-app-hash}` in the Manage App Settings page under Acquisition SDK Options in the Tracking ID field.

   ![](assets/tracking-id.png)

* `{parameters}` ist eine Liste mit speziell benannten Standard-URL-Abfrageparametern.

Im Folgenden finden Sie eine Liste der Parameter:

* **`a_g_id`**

   App-Kennung für Google Play Store.

   * Beispielwert: `com.adobe.beardcons`

* **`a_g_lo`**

   Gebietsschema-Überschreibung für Google Play Store.

   * Beispielwert: `ko`

* **`a_i_id`**

   App-Kennung für iTunes.

   * Beispielwert: `835196493`

* **`a_i_lo`**

   Gebietsschema-Überschreibung für iTunes.

   * Beispielwert: `jp`

* **`a_dd`**

   Standard-Store für automatische Umleitung.

   * Beispielwert: `i | g`

* **`a_cid`**

   Benutzerdefinierte ID-Überschreibung (allgemein IDFA für iOS und ADID für Android).

   * Beispielwert: `Any String < 255 characters (UTF-8 encoded)`

* **`ctx*`**

   Keys prefixed with `ctx` will be in the context data of the resulting launch hit.

   * Beispielwert: `ctxmy.custom.key=myValue`

* **`ctxa.referrer.campaign.name`**

   Name der Akquise-Kampagne.

   Dieser Parameter ist für das Reporting erforderlich, wenn Sie die Performance verschiedener Akquise-Links vergleichen möchten.

   * Beispielwert: Summit-Konferenz 2015

* **`ctxa.referrer.campaign.trackingcode`**

   Trackingcode

   Dieser Parameter ist für das Reporting erforderlich, wenn Sie die Performance verschiedener Akquise-Links vergleichen möchten.

   * Beispielwert: `lexsxouj`

* **`ctxa.referrer.campaign.source`**

   Die Quelle.

   * Beispielwert: Werbenetzwerk

* **`ctxa.referrer.campaign.medium`**

   Mittel

   * Beispielwert: E-Mail

* **`ctxa.referrer.campaign.content`**

   Inhalt

   * Beispielwert: Bild # 325689

* **`ctxa.referrer.campaign.term`**

   Begriff

   * Beispielwert: hiking + scrits


Wenn Sie Akquise-Links manuell erstellen, beachten Sie die folgenden Informationen:

* Alle Parameter, die mit den in der oben stehenden Tabelle aufgeführten Parametern nicht übereinstimmen, werden als Teil der Appstore-Umleitung übergeben.
* Alle Parameter sind technisch optional, obwohl der Link nicht funktionsfähig ist, wenn mindestens eine Store-ID angegeben ist.

   An example of a store ID is `a_g_id`/ `a_i_id`.

* Wenn der Ziel-Store nicht automatisch bestimmt werden kann und kein Standardwert bereitgestellt wird, wird der Fehler 404 zurückgegeben.

