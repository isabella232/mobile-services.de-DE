---
description: Sie können diese Information verwenden, um mithilfe des Adobe Mobile Android SDK (verzögerte) Deep-Links in Ihren mobilen Apps zu verfolgen.
keywords: Android;Bibliothek;Mobile;SDK
seo-description: Sie können diese Information verwenden, um mithilfe des Adobe Mobile Android SDK (verzögerte) Deep-Links in Ihren mobilen Apps zu verfolgen.
seo-title: Deep-Links in Adobe Mobile Services verfolgen
solution: Experience Cloud,Analytics
title: Verfolgen von Deep-Links
topic: Entwickler und Implementierung
uuid: ebb1c08c-a246-40b3-9ac6-4606a14b4c5a
translation-type: ht
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# Deep-Links verfolgen {#tracking-deep-links}

Sie können diese Information verwenden, um mithilfe des Adobe Mobile Android SDK (verzögerte) Deep-Links in Ihren mobilen Apps zu verfolgen.

## Deep-Links verfolgen

1. Fügen Sie das SDK zu Ihrem Projekt hinzu und implementieren Sie Lebenszyklusmetriken.

   Weitere Informationen finden Sie unter *SDK und Konfigurationsdatei zu Ihrem IntelliJ IDEA- oder Eclipse-Projekt hinzufügen* in [Grundlegende Implementierung und Lebenszyklus](/help/android/getting-started/dev-qs.md).

1. Registrieren Sie die Anwendung für die Verarbeitung von URLs.

   Weitere Informationen dazu finden Sie unter [URLs](https://developer.android.com/training/basics/intents/filters.html).
1. Übergeben Sie die Aktivität mit dem Deep-Link-Intent per `collectLifecycleData` an das Adobe-SDK.

   Im Folgenden finden Sie einen Beispielpfad-Deep-Link:

   ```java
   public class ParseDeepLinkActivity extends Activity { 
       @Override 
       protected void onCreate(Bundle savedInstanceState) { 
           super.onCreate(savedInstanceState); 
   
           Config.collectLifecycleData(this); 
           ... 
       } 
   }
   ```

Das Adobe Mobile SDK kann Schlüssel-Wert-Paare von an Deep- oder universelle Links angehängten Daten analysieren, sofern der Link einen Schlüssel mit der Bezeichnung `a.deeplink.id`, einen entsprechenden Wert, der nicht „Null“ entspricht, sowie einen vom Benutzer generierten Wert aufweist. Alle Schlüssel-Wert-Paare von Daten, die an den Link angehängt sind, werden analysiert, an einen Lebenszyklustreffer angehängt und an Adobe Analytics gesendet, sofern der Link das Schlüssel-Wert-Paar `a.deeplink.id` enthält.

Zusätzlich können Sie auswählen, ob Sie einen oder mehrere der folgenden reservierten Schlüssel (mit benutzergenerierten Werten) an Deep- oder universelle Links anhängen möchten:

* `a.launch.campaign.trackingcode`
* `a.launch.campaign.source`
* `a.launch.campaign.medium`
* `a.launch.campaign.term`
* `a.launch.campaign.content`

Bei diesen Schlüsseln handelt es sich um vorab zugeordnete Variablen für das Reporting in Adobe Analytics. Weitere Informationen zu Zuordnungs- und Verarbeitungsregeln finden Sie unter [Verarbeitungsregeln und Kontextdaten](https://docs.adobe.com/content/help/de-DE/analytics/admin/admin-tools/processing-rules/processing-rules.html).

## Verzögerte Deep-Links (zur Verwendung mit Marketinglinks) verfolgen

Im Falle eines verzögerten Deep-Links öffnet das Adobe-SDK einen neuen Intent mit dem Deep-Link als Intent-Daten. Dieser Prozess wird als externer Deep-Link unter Verwendung des obigen Codes behandelt.

## Öffentliche Deep-Link-Informationen {#section_1815396353614DA8A63D8D92112217E7}

### Konstanten

```java
/* 
 * Used for message deep link tracking
 * Key for deep link URL. 
 */
public static final String ADB_MESSAGE_DEEPLINK_KEY = "adb_deeplink";
```

