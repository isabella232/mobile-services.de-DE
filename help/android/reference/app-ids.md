---
description: In der folgenden Tabelle werden die verschiedenen App-IDs beschrieben, die vom Android SDK und von Adobe Mobile Services verwendet werden.
solution: Experience Cloud,Analytics
title: App-IDs
topic-fix: Developer and implementation
uuid: 3ac99489-6269-439e-a814-24102ef220b1
exl-id: 28358dd6-50dd-4ba9-9fb0-5271eae69d28
source-git-commit: f18d65c738ba16d9f1459ca485d87be708cf23d2
workflow-type: tm+mt
source-wordcount: '201'
ht-degree: 100%

---

# App-IDs{#app-ids}

In der folgenden Tabelle werden die verschiedenen App-IDs beschrieben, die vom Android SDK und von Adobe Mobile Services verwendet werden.

| ID | Beschreibung |
|--- |--- |
| Mit Lebenszyklusmetriken gesendete ID | Dies ist eine Kombination des App-Namens und der Bundle-Version, die im App Store eingereicht wird. Dieser Wert wird für den Bericht Versionen in Adobe Mobile Services verwendet und Sie können diesen Wert zum Filtern verwenden, um nur bestimmte Release-Versionen Ihrer App anzuzeigen. |
| App Store-ID | Diese ID wird Ihrer App vom Appstore zugewiesen und in Adobe Mobile Services bereitgestellt, wenn Sie Akquise-Links erstellen. |
| AppID in ADBMobile-JSON-Konfiguration | Dies ist eine eindeutige ID, die der App-Instanz von Adobe Mobile Services für alle zugehörigen Metadaten im System zugewiesen wird. Diese ID wird verwendet, um eindeutige URLs für die Akquise-Verfolgung oder für Verfolgungslinks zu erstellen. Diese ID wird automatisch zur ADBMobile-JSON-Konfigurationsdatei hinzugefügt, wenn Sie sie vom UI herunterladen. Sie finden Sie unter App-Einstellungen verwalten in den Akquise-Einstellungen für Ihre App. |
