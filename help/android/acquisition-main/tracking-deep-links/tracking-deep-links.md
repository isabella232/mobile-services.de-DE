---
description: Sie können diese Information verwenden, um mithilfe des Adobe Mobile Android SDK (verzögerte) Deep-Links in Ihren mobilen Apps zu verfolgen.
keywords: android; library; mobile; sdk
seo-description: Sie können diese Information verwenden, um mithilfe des Adobe Mobile Android SDK (verzögerte) Deep-Links in Ihren mobilen Apps zu verfolgen.
seo-title: Verfolgen von Deep Links in Adobe Mobile Services
solution: Marketing Cloud, Analytics
title: Verfolgen von Deep-Links
topic: Entwickler und Implementierung
uuid: ebb 1 c 08 c-a 246-40 b 3-9 ac 6-4606 a 14 b 4 c 5 a
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# Tracking deep links {#tracking-deep-links}

Sie können diese Information verwenden, um mithilfe des Adobe Mobile Android SDK (verzögerte) Deep-Links in Ihren mobilen Apps zu verfolgen.

## Verfolgen von Deep Links

1. Fügen Sie das SDK zu Ihrem Projekt hinzu und implementieren Sie Lebenszyklusmetriken.

   Weitere Informationen finden Sie unter *Fügen Sie das SDK und die Config-Datei zu Ihrem intellij IDEA oder Eclipse Project* in [Core Implementation und Lebenszyklus hinzu](/help/android/getting-started/dev-qs.md).

1. Registrieren Sie die Anwendung für die Verarbeitung von URLs.

   For more information, see [URLs](https://developer.android.com/training/basics/intents/filters.html).
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

The Adobe Mobile] SDK can parse key and value pairs of data that is appended to any Deep or Universal Link as long as the link contains a key with the `a.deeplink.id` label and a corresponding non-null and user-generated value. All key and value pairs of data that are appended to the link will be parsed, attached to a lifecycle hit, and sent to Adobe Analytics] as long as the link contains the `a.deeplink.id` key and value.

Des Weiteren können Sie einen oder mehrere der folgenden reservierten Schlüssel (mit benutzergenerierten Werten) an den Deep- oder universellen Link anhängen:

* `a.launch.campaign.trackingcode`
* `a.launch.campaign.source`
* `a.launch.campaign.medium`
* `a.launch.campaign.term`
* `a.launch.campaign.content`

Bei diesen Schlüsseln handelt es sich um vorab zugeordnete Variablen für das Reporting in Adobe Analytics. Weitere Informationen zu Zuordnungs- und Verarbeitungsregeln finden Sie unter [Verarbeitungsregeln und Kontextdaten](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/processing-rules/processing-rules.html).

## Verfolgen verzögerter Deep Links (für die Verwendung mit Marketing-Links)

Im Falle eines verzögerten Deep-Links öffnet das Adobe-SDK einen neuen Intent mit dem Deep-Link als Intent-Daten. Dieser Prozess wird als externer Deep-Link unter Verwendung des obigen Codes behandelt.

## Deep link public information {#section_1815396353614DA8A63D8D92112217E7}

### Konstanten

```java
/* 
 * Used for message deep link tracking
 * Key for deep link URL. 
 */
public static final String ADB_MESSAGE_DEEPLINK_KEY = "adb_deeplink";
```

