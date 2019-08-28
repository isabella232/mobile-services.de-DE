---
description: Sie können die Daten, die Sie von der App erhalten, verfolgen und verwalten, indem Sie verschiedene Variablen und Metriken konfigurieren.
keywords: mobile
seo-description: Sie können die Daten, die Sie von der App erhalten, verfolgen und verwalten, indem Sie verschiedene Variablen und Metriken konfigurieren.
seo-title: Verwalten Ihrer App
solution: Marketing Cloud, Analytics
title: Verwalten Ihrer App
topic: Metriken
uuid: 0 cc 356 c 3-8457-40 a 7-8 c 97-7 cbc 68 a 5 dc 0 c
translation-type: tm+mt
source-git-commit: 54150c39325070f37f8e1612204a745d81551ea7

---


# Verwalten Ihrer App {#managing-your-app}

Sie können die Daten, die Sie von der App erhalten, verfolgen und verwalten, indem Sie verschiedene Variablen und Metriken konfigurieren.

## Variablen und Metriken verwalten {#section_EC2D58AC334F4ED49E764B81C2423A62}

* **Standardvariablen und Metriken**

   Jede App enthält Variablen und Metriken zur Verfolgung von Warenkorb und Kaufaktivitäten. Some purchase information cannot be handled with processing rules, so the SDK exposes the special `"&&products"` context data. Sie können beispielsweise Variablen zum Hinzufügen bzw. Entfernen von Produkten zum bzw. aus dem Warenkorb, zu abgeschlossenen Kaufvorgängen, Bestellungen usw. festlegen. Die Kontextdaten müssen den Daten in Adobe Analytics zugeordnet werden. Wenn diese Variable mittels einer einfachen Zuordnung aus Kontextdaten aufgefüllt wird, ist dies der Schlüssel für die Zuordnung. Lassen Sie es leer, wenn die Variable durch komplexere Regeln in den Analytics Admin Tools gefüllt wird.

   Weitere Informationen zu diesen Variablen und Metriken finden Sie unter folgenden Themen:

   * [Produktvariablen in Android](/help/android/analytics-main/products/products.md)
   * [Produktvariablen in ios](/help/ios/analytics-main/products/products.md)

* **Benutzerdefinierte Variablen**

   Auf der Seite Benutzerdefinierte Variablen werden alle benutzerdefinierten Analytics-Variablen angezeigt, die für die Report Suite, die die Daten Ihrer App enthält, konfiguriert sind. Sie können auf dieser Seite weitere Variablen aktivieren und Kontextdaten Analytics-Variablen zuordnen.

### Kontextdaten Analytics-Variablen zuordnen

Click **[!UICONTROL Manage App Settings]** &gt; **[!UICONTROL Manage Variables &amp; Metrics]** &gt; **[!UICONTROL Custom Variables]**.

These mappings call the same API that is used in [Processing Rules](https://docs.adobe.com/content/help/en/analytics/admin/admin-tools/processing-rules/processing-rules.html).

![Kontextdatenzuordnung](assets/custom_data_content.png)

Im Folgenden finden Sie eine Liste der benutzerdefinierten Variablen, die Sie konfigurieren können:

* The **[!UICONTROL Custom Properties]** (or props) answer the question "which one?" Props können auf einen Textwert festgelegt werden, der mit anderen Variablen und Metriken verknüpft wird, die im selben Hit gesendet wurden. Die Werte können verwendet werden, um Berichte zu filtern, oder sie können in einer Rangfolge durch eine verknüpfte Metrik aufgelistet werden.

   Wenn ein Wert für eine Eigenschaft in einem Nachverfolgungsaufruf (bzw. Hit) festgelegt wird, gilt er nur für diesen Aufruf.

* The **[!UICONTROL Custom Variables]** (or evars) also answer the question "which one?" Ein eVar-Wert kann jedoch nicht nur auf den Hit zutreffen, für den er gesendet wird, sondern auch für Variablen und Metriken, die in folgenden Hits gesendet werden, bis der Wert abläuft oder ein neuer Wert festgelegt wird.
* The **[!UICONTROL Custom List Variables (or Multi-Value Variables)]** behave the same as variables except they allow you to capture multiple values on one hit. Weitere Informationen finden Sie unter [Listenvariablen](https://docs.adobe.com/content/help/en/analytics/implementation/javascript-implementation/variables-analytics-reporting/page-variables.html).

Die folgenden Zuordnungen werden in Analytics als in Mobile Services erstellt angezeigt.

* **[!UICONTROL Name]**

   Der Anzeigename der Datenerfassungsvariablen.

* **[!UICONTROL Kontextdaten]**

   Wenn diese Variable mittels einer einfachen Zuordnung aus Kontextdaten aufgefüllt wird, ist dies der Schlüssel für die Zuordnung. Wenn die Variable durch komplexere Regeln in Analytics Admin Tools aufgefüllt wird, lassen Sie dieses Feld leer.

   Klicken Sie in die Kontextdatenspalte und wählen Sie die Kontextdatenvariable aus, die Sie zuordnen möchten. In der Dropdown-Liste sind die Variablen enthalten, die in den letzten 30 Tagen empfangen wurden. Sollte die gewünschte Kontextdatenvariable hier nicht aufgeführt sein, können Sie sie auch eingeben.

* **[!UICONTROL Persistenz (benutzerdefinierte Variablen und benutzerdefinierte Listenvariablen)]**

   Die Persistenz bestimmt den Punkt, an dem der Wert einer benutzerdefinierten Variable (eVar) verfällt oder an dem sie nicht mehr mit zusätzlichen Hits verknüpft wird. Wenn eine eVar bereits abgelaufen ist, wenn ein Hit auftritt, wird für diese eVar der Wert Keine mit dem Hit verknüpft. Das bedeutet, dass kein eVar-Wert aktiv war, als der Hit auftrat.

   Sie können eine der folgenden Optionen auswählen:

   * **[!UICONTROL Sitzung]**

      Der evar-Wert bleibt für die Länge des Analytics-Besuchs bestehen.

   * **[!UICONTROL Tracking-Anruf]**

      Der evar-Wert bleibt nur für den Verfolgungsaufruf oder Treffer bestehen, in dem er enthalten war.

   * **[!UICONTROL Unbeschränkte Gültigkeit]**

      Der evar-Wert bleibt für alle nachfolgenden Verfolgungsaufrufe bestehen.
   * **[!UICONTROL Advanced]**

      Adobe Analytics verfügt über eine erweiterte Benutzeroberfläche für die Einstellung der Persistenz von eVars. Wenn ein Persistenzwert für die evar festgelegt ist, die in Mobile Services nicht unterstützt wird, wird dieser Wert in der Mobile Services-Benutzeroberfläche angezeigt.

      To manage eVars, click **[!UICONTROL Adobe Analytics Report Suite Manager]** &gt; **[!UICONTROL Conversion Variables UI]**.

   * **[!UICONTROL Listenunterstützung]**

      Ermöglicht die Übergabe mehrerer Werte, die mit der Eigenschaft verknüpft werden sollen, in einem Verfolgungsaufruf. Das Trennzeichen muss ein Zeichen sein und darf keine Null oder kein Leerzeichen sein.

   * **[!UICONTROL Trennzeichen]**

      Das Trennzeichen muss ein Zeichen sein und darf keine Null oder kein Leerzeichen sein.

### Zusätzliche Analytics-Variablen

Über die Dropdownliste am Ende jedes Variablenabschnitts können Sie weitere Variablen aktivieren.

![eine Variable hinzufügen](assets/add_variable.png)

Wählen Sie eine bisher ungenutzte Variablennummer aus und geben Sie einen Namen ein. Optional können Sie die Kontextdatenvariable, die Sie speichern möchten, sowie weitere Informationen eingeben.

* **Benutzerdefinierte Metriken**

   Metriken (oder Ereignisse) beantworten die Fragen *?* oder *wie viele?*. Ereignisse können bei jeder Aktion des Benutzers gesteigert werden oder numerische Werte, wie z. B. einen Preis, enthalten. Benutzerdefinierte Metriken beinhalten Ereignisse, z. B. wenn eine App erstellt, die PDF- oder CSV-Datei heruntergeladen oder exportiert, eine Kampagne gespeichert, das SDK heruntergeladen, ein Bericht ausgeführt, ein Appstore-Link hinzugefügt oder eine In-App-Nachricht aktiviert wird.

   Wählen Sie eines der folgenden benutzerdefinierten Metriktypen:

   * **[!UICONTROL Ganzzahl]**
   * **[!UICONTROL Dezimalzahl]**
   * **[!UICONTROL Währung]**

## Zielpunkte verwalten {#section_990EF15E4E3B42CC807FCD9BEC8DB4C6}

Mit Zielpunkten können Sie geografische Standorte definieren, die Sie für Korrelationszwecke, Targeting mit In-App-Nachrichten usw. verwenden können. Wenn ein Treffer innerhalb eines Zielpunkts gesendet wird, wird der Zielpunkt an den Treffer angehängt. Weitere Informationen zu Zielpunkten finden Sie unter [Zielpunkte verwalten](/help/using/location/t-manage-points.md).

## Link-Ziele verwalten {#section_F722A387E22A430187B063D358A87711}

Sie können Link-Ziele erstellen, bearbeiten, archivieren, dearchivieren und löschen. Diese Ziele können dann inline aufgerufen werden, wenn Marketing-Links, Push-Benachrichtigungen oder In-App-Nachrichten erstellt werden. Weitere Informationen zu Link-Zielen finden Sie unter [Link-Ziele verwalten](/help/using/acquisition-main/c-manage-link-destinations/t-archive-unarchive-link-destinations.md).

## Postbacks verwalten {#section_78B0A8D7AE6940E78D85AE3AB829E860}

Mit Postbacks können Sie durch Adobe Mobile erfasste Daten an einen Drittanbieterserver senden. Mit denselben Auslösern und Eigenschaften wie bei der Anzeige einer In-App-Nachricht können Sie Mobile so konfigurieren, dass es benutzerdefinierte Daten an ein Drittanbieterziel sendet. Weitere Informationen zu Postbacks finden Sie unter [Postbacks konfigurieren](/help/using/c-manage-app-settings/c-mob-confg-app/signals.md)
