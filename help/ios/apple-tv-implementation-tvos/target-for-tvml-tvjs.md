---
description: Sie können Adobe Target in Ihren TVML-/TVJS-Apps nutzen, indem Sie direkte Ersetzungen in Ihren .xml-Dateien vornehmen. Bestimmen Sie Bereiche Ihrer Seite, die durch Target-Inhalt ersetzt werden sollen, indem Sie das benutzerdefinierte ADBTarget-XML-Element verwenden.
seo-description: Sie können Adobe Target in Ihren TVML-/TVJS-Apps nutzen, indem Sie direkte Ersetzungen in Ihren .xml-Dateien vornehmen. Bestimmen Sie Bereiche Ihrer Seite, die durch Target-Inhalt ersetzt werden sollen, indem Sie das benutzerdefinierte ADBTarget-XML-Element verwenden.
seo-title: Adobe Target für TVML/TVJS
title: Adobe Target für TVML/TVJS
uuid: afd5a583-5266-43f2-8cb0-0ace89c53a57
translation-type: tm+mt
source-git-commit: 46a0b8e0087c65880f46545a78f74d5985e36cdc

---


# Adobe Target für TVML/TVJS{#adobe-target-for-tvml-tvjs}

Sie können Adobe Target in Ihren TVML-/TVJS-Apps nutzen, indem Sie direkte Ersetzungen in Ihren .xml-Dateien vornehmen. Bestimmen Sie Bereiche Ihrer Seite, die durch Target-Inhalt ersetzt werden sollen, indem Sie das benutzerdefinierte ADBTarget-XML-Element verwenden.

>[!IMPORTANT]
>
>Before using the `ADBTarget` element in your TVML pages, you must configure your TVML/TVJS app to use the tvOS SDK. Weitere Informationen finden Sie unter Implementierung von [Apple TV mit tvOS](/help/ios/apple-tv-implementation-tvos/apple-tv-implementation-tvos.md).

## Erste Schritte {#section_88445645FD67416EAF6FDC3E3D3F5C33}

1. Identify the `.xml` file in which you want to use your Target location.
1. Add an `ADBTarget` element to the file as a child of the `<document>` element.
1. If Target fails to find your Mbox location, or it times out, the value between your `<ADBTarget>` and `</ADBTarget>` tags is used as default content.

## Configure your mbox in Target {#section_F2DA140C34B0421D976046F825B23123}

The returned content from Target replaces all content between `<ADBTarget>` and `</ADBTarget>`, including both `ADBTarget` tags.

>[!TIP]
>
>Sie sollten das, was Sie ersetzen möchten, entsprechend planen.

Ihr Anwendungsfall sollte so einfach sein wie das Ersetzen eines Zeichenfolgenwerts in einer Bezeichnung oder so komplex wie das Ersetzen einer gesamten Seite.

## ADBTarget-Element konfigurieren {#section_44A7AEC6FC0648ADAD0BACB57D493AFA}

Im Element `ADBTarget` müssen Sie den Mbox-Namen in der Eigenschaft `mbox` angeben. You can optionally add custom properties to your request in the `customParameterName="customParameterValue"` format.

* **`mbox`**

   Name Ihrer Mbox-Position.

   * Eigenschaftstyp: Zeichenfolge
   * This property is required.

* **`id`**

   Die Bestell-ID.

   * Eigenschaftstyp: Zeichenfolge
   * Diese Eigenschaft ist **nicht** erforderlich.

* **`total`**

   Die Bestellsumme.

   * Eigenschaftstyp: Zeichenfolge
   * This property is not required.****

* **`purchasedProductIds`**

   Eine kommagetrennte Liste der erworbenen Produkt-IDs für diese Bestellung.

   * Das folgende Codebeispiel für diese Eigenschaft:


      ```objective-c
      purchasedProductIds="product1,product2,product3" 
      ```

   * Property type: String
   * Diese Eigenschaft ist **nicht** erforderlich.

* **`mboxParameters`**

   Eine Liste von Schlüssel-Wert-Paaren für `mboxParameters`. Jeder Eintrag in dieser Zeichenfolge wird durch ein Semikolon getrennt und die Schlüsselwerte werden durch einen Doppelpunkt voneinander getrennt.

   * Das folgende Codebeispiel für diese Eigenschaft:

      ```objective-c
      mboxParameters="mboxparameterKey:mboxParameterValue;mboxParameterKey1:mboxParameterValue1;mboxParameterKey2:mboxParameterValue2"
      ```

   * Eigenschaftstyp: Zeichenfolge
   * Diese Eigenschaft ist **nicht** erforderlich.

* **`customParameterName`**

   Der Wert dieser Eigenschaft lautet `customParameterValue`.

   * Eigenschaftstyp: Zeichenfolge
   * Diese Eigenschaft ist **nicht** erforderlich.


## Beispiele {#section_6D6D6E8C7FE147168FC30D83CBC06985}

### Beispiel 1

Im folgenden Beispiel wird ein `ADBTarget`-Element auf der Seite `LandingPage.xml.js` verwendet, um die Inhalte eines Alarms zu ersetzen:

#### Konfigurieren von Target

Angenommen, Sie besitzen eine Mbox-Position mit dem Namen `landingPage` und der Angebotsinhalt ist auf Folgendes festgelegt:

```objective-c
<title>My cool landing page</title> 
<description>Thanks for coming to my page</description> 
```

#### Konfigurieren von „landingPage.xml.js“

* Im Folgenden finden Sie die Konfiguration für „landingPage.xml.js“:

   ```js
   <alertTemplate> 
       <ADBTarget mbox="landingPage">  
           <title>TargetTestPage</title> 
           <description>Load fail or timeout (defaultContent)</description> 
       </ADBTarget>  
   </alertTemplate> 
   ```

* Wenn die Anforderung zu Target erfolgreich ist und Ihr Angebotsinhalt zurückgegeben wird, wird auf Ihrer Seite Folgendes ausgegeben:

   ```objective-c
   <alertTemplate> 
       <title>My cool landing page</title> 
       <description>Thanks for coming to my page</description> 
   </alertTemplate>
   ```

* Wenn der Target-Server nicht erreicht werden kann oder bei der Anforderung eine Zeitüberschreitung auftritt, wird auf Ihrer Seite Folgendes ausgegeben:

   ```objective-c
   <alertTemplate> 
       <title>TargetTestPage</title> 
       <description>Load fail or timeout (defaultContent)</description> 
   </alertTemplate>
   ```

### Beispiel 2

Im folgenden Beispiel wird veranschaulicht, wie Ihrem `ADBTarget`-Element benutzerdefinierte Daten hinzugefügt werden. Mit dieser Methode können Sie bedingte Erfahrungen und Angebotsinhalte für diese Mbox-Position in Target erstellen:

```objective-c
<alertTemplate> 
    <ADBTarget mbox="landingPage" customData="custom data" moreCustomData="more custom data"> 
        <title>TargetTestPage</title> 
        <description>Load fail or timeout (defaultContent)</description> 
    </ADBTarget>  
</alertTemplate>
```
