---
description: Das Adobe-SDK nutzt die Zuordnungs-APIs der Suchanzeigen-App von Apple, damit Entwickler und Marketingexperten App-Downloads, die von Suchanzeigenkampagnen im Apple App Store stammen, verfolgen und zuordnen können.
solution: Experience Cloud,Analytics
title: Apple Search Ads
topic-fix: Developer and implementation
uuid: 790080e8-067e-4bfd-a169-0027db4fdff3
exl-id: efcdd430-f08d-4ee2-85f3-2697c3bd72db
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 100%

---

# Apple Search Ads {#apple-search-ads}

Das Adobe-SDK nutzt die Zuordnungs-APIs der Suchanzeigen-App von Apple, damit Entwickler und Marketingexperten App-Downloads, die von Suchanzeigenkampagnen im Apple App Store stammen, verfolgen und zuordnen können. Weitere Informationen zu Suchanzeigekampagnen finden Sie unter [Apple Search Ads](https://searchads.apple.com/de/).

## Vorteile {#section_CEA30C652AC8470784B8054E299B80FA}

Vorteile durch die Verwendung von Apple-Werbeanzeigen:

* Messen Sie ganz einfach die Effektivität Ihrer Suchanzeigen-App-Downloadkampagnen, indem Sie der App einige Codezeilen hinzufügen.
* Entwickler können auf das Datum bzw. die Uhrzeit des Downloads sowie auf das gebotene Keyword zugreifen, das die Konversion verursacht hat.

## Implementieren von Apple-Werbeanzeigen {#section_F1094676793540CFA1DBB540174EEB6A}

>[!TIP]
>
>Zum Implementieren von Apple-Werbeanzeigen müssen Sie über das iOS-SDK, Version 4.13.2 oder höher, verfügen.

So aktivieren Sie Ihre App für die Suchanzeigenzuordnung:

1. Implementieren Sie das Adobe SDK, Version 4.13.2 oder höher.

   Weitere Informationen finden Sie unter [Grundlegende Implementierung und Lebenszyklus](/help/ios/getting-started/dev-qs.md).

1. Fügen Sie das iAd-Framework zu Ihrer Xcode-Projektdatei für Ihre App hinzu.

## Erstellen von Berichten zur Suchanzeigenzuordnung {#section_1AF4E0B4F8E94F36B38CA3D3E384D0A4}

1. Apple Search Ads-Zuordnungsdaten werden im Akquisenamen, in der Quelle und den Begriffswerten angegeben.

   Wenn die Zuordnung `true` lautet, sind alle Felder vom Typ `iad-*` im Lebenszyklustreffer enthalten.

   Zusätzlich werden die folgenden Werte aus dem `"iad"`-Wörterbuch unseren typischen Akquisitionskontext-Datenfeldern zugeordnet:

   * `"iad-campaign-id"` --> `"a.referrer.campaign.trackingcode"`
   * `"iad-campaign-name"` —>  `"a.referrer.campaign.name"`
   * `"iad-adgroup-id"` —>  `"a.referrer.campaign.content"`
   * `"iad-keyword"` —>  `"a.referrer.campaign.term"`
   Diese Zuordnung stellt sicher, dass die Werte in unseren Standardberichten verfügbar sind.
