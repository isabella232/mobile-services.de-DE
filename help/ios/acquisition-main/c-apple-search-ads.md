---
description: Das Adobe-SDK nutzt die Zuordnungs-APIs der Suchanzeigen-App von Apple, damit Entwickler und Marketingexperten App-Downloads, die von Suchanzeigenkampagnen im Apple App Store stammen, verfolgen und zuordnen können.
seo-description: Das Adobe-SDK nutzt die Zuordnungs-APIs der Suchanzeigen-App von Apple, damit Entwickler und Marketingexperten App-Downloads, die von Suchanzeigenkampagnen im Apple App Store stammen, verfolgen und zuordnen können.
seo-title: Apple-Suchanzeigen
solution: Marketing Cloud, Analytics
title: Apple-Suchanzeigen
topic: Entwickler und Implementierung
uuid: 790080e8-067e-4bfd-a169-0027db4fdff3
translation-type: tm+mt
source-git-commit: ebcc04ab3e80aafb9d9ec2e1fbc809c743554cb7

---


# Apple-Suchanzeigen {#apple-search-ads}

Das Adobe-SDK nutzt die Zuordnungs-APIs der Suchanzeigen-App von Apple, damit Entwickler und Marketingexperten App-Downloads, die von Suchanzeigenkampagnen im Apple App Store stammen, verfolgen und zuordnen können. Weitere Informationen zu Suchanzeigekampagnen finden Sie unter [Apple-Suchanzeigen](https://searchads.apple.com).

## Vorteile {#section_CEA30C652AC8470784B8054E299B80FA}

Vorteile durch die Verwendung von Apple-Werbeanzeigen:

* Messen Sie ganz einfach die Effektivität Ihrer Suchanzeigen-App-Downloadkampagnen, indem Sie der App einige Codezeilen hinzufügen.
* Entwickler können auf das Datum bzw. die Uhrzeit des Downloads sowie auf das gebotene Keyword zugreifen, das die Konversion verursacht hat.

## Implementieren von Apple-Werbeanzeigen {#section_F1094676793540CFA1DBB540174EEB6A}

>[!TIP]
>
>Zur Implementierung von Apple Ads müssen Sie über das iOS SDK Version 4.13.2 oder höher verfügen.

So aktivieren Sie Ihre App für die Suchanzeigenzuordnung:

1. Implementieren Sie das Adobe-SDK, Version 4.13.2 oder höher.

   Weitere Informationen finden Sie unter [Core implementation and lifecycle](/help/ios/getting-started/dev-qs.md).

1. Fügen Sie das iAd-Framework zu Ihrer Xcode-Projektdatei für Ihre App hinzu.

## Erstellen von Berichten zur Suchanzeigenzuordnung {#section_1AF4E0B4F8E94F36B38CA3D3E384D0A4}

1. Apple-Suchanzeigen-Zuordnungsdaten werden im Akquisenamen, in der Quelle und den Begriffswerten angegeben.

   If attribution = `true`, all of the `iad-*` fields will be included in the lifecycle hit.

   Zusätzlich werden die folgenden Werte aus dem `"iad"`-Wörterbuch unseren typischen Akquisekontext-Datenfeldern zugeordnet:

   * `"iad-campaign-id"` --&gt; `"a.referrer.campaign.trackingcode"`
   * `"iad-campaign-name"` --&gt; `"a.referrer.campaign.name"`
   * `"iad-adgroup-id"` --&gt; `"a.referrer.campaign.content"`
   * `"iad-keyword"` --&gt; `"a.referrer.campaign.term"`
   Diese Zuordnung stellt sicher, dass die Werte in unseren Standardberichten verfügbar sind.
