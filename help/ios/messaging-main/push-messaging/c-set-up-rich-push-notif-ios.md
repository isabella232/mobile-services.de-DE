---
description: Sie können Bilddateien an Ihre Apple-Benachrichtigungen anhängen. Das Hinzufügen visueller Komponenten kann die Interaktion Ihrer Benutzer mit Push-Benachrichtigungen deutlich erhöhen.
seo-description: Sie können Bilddateien an Ihre Apple-Benachrichtigungen anhängen. Das Hinzufügen visueller Komponenten kann die Interaktion Ihrer Benutzer mit Push-Benachrichtigungen deutlich erhöhen.
seo-title: Rich-Push-Benachrichtigungen empfangen
title: Rich-Push-Benachrichtigungen empfangen
uuid: 0dbda409-cf49-4eb8-90ee-baf27911dc07
translation-type: tm+mt
source-git-commit: d028fe0f9477bc011aa8fda21a0a389808df0fce
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 38%

---


# Rich-Push-Benachrichtigungen empfangen {#receive-rich-push-notifications}

Sie können Bilddateien an Ihre Apple-Benachrichtigungen anhängen. Das Hinzufügen visueller Komponenten kann die Interaktion Ihrer Benutzer mit Push-Benachrichtigungen deutlich erhöhen.

So erhalten Sie Rich-Push-Benachrichtigungen in Ihrer iOS-App

1. Implementieren Sie die Push-Benachrichtigung für die App, indem Sie die Schritte in [Push-Benachrichtigung](/help/ios/messaging-main/push-messaging/push-messaging.md).
1. Vergewissern Sie sich, dass Sie eine Text-Push-Nachricht an Ihre App senden können.
1. hinzufügen Sie eine Benachrichtigungsdiensterweiterung, indem Sie die folgenden Schritte ausführen:

   1. Wählen Sie im Xcode-Projekt **[!UICONTROL Datei]** > **[!UICONTROL Neu]** > **[!UICONTROL Zielgruppe]**.
   1. Wählen Sie **[!UICONTROL Benachrichtigungsdiensterweiterung aus]**.
   1. Überprüfen Sie, ob die Datei `NotificationService.m` vorhanden ist.

1. Öffnen Sie die Datei `NotificationService.m` und überprüfen Sie, ob die folgenden Delegierungsmethoden vorhanden sind:

   * Eine Methode zum Empfangen einer Benachrichtigungsanfrage.
   * Eine Methode zur Behandlung des Ablaufs der Diensterweiterung.

      Für den Empfang von Rich-Push-Benachrichtigungen wird die erste Methode verwendet:

      ```objective-c
      (void)didReceiveNotificationRequest:(UNNotificationRequest *)request withContentHandler:(void (^)(UNNotificationContent *contentToDeliver))contentHandler;
      ```

      Mithilfe dieser Methode können Sie die Medien-URL von `userInfo` mithilfe des Schlüssels `attachment-url` abrufen. Nachdem Sie die Datei in ein lokales Verzeichnis heruntergeladen haben, fügen Sie den lokalen Pfad zu `bestAttemptContent.attachments` hinzu.

      Hier finden Sie einen Beispielcode in dieser Methode:

      ```objective-c
      - (void)didReceiveNotificationRequest:(UNNotificationRequest *)request withContentHandler:(void (^)(UNNotificationContent * _Nonnull))contentHandler {
      self.contentHandler = contentHandler;
      self.bestAttemptContent = [request.content mutableCopy];
         NSDictionary* userInfo = request.content.userInfo;
      if(userInfo[@"attachment-url"]){
         NSURL* url = [[NSURL alloc] initWithString:userInfo[@"attachment-url"]];
         NSURLSessionDownloadTask* task = [[NSURLSession sharedSession] downloadTaskWithURL:url completionHandler:^(NSURL * _Nullable location, NSURLResponse * _Nullable response, NSError * _Nullable error) {
             if(!location){
                 return;
             }
             NSString* tmpDirectory = NSTemporaryDirectory();
             NSString* tmpFilePath = [NSString stringWithFormat:@"file://%@%d%d%@", tmpDirectory, arc4random_uniform(100000),
                                    arc4random_uniform(100000), [url lastPathComponent]];
             NSURL* tmpUrl = [[NSURL alloc] initWithString:tmpFilePath];
             NSError * fileError = nil;
             [[NSFileManager defaultManager] moveItemAtURL:location toURL:tmpUrl error:&amp;fileError];
             if(fileError){
                 return;
             }
             UNNotificationAttachment* attachment = [UNNotificationAttachment attachmentWithIdentifier:@"video" URL:tmpUrl options:nil error:&amp;fileError];
             if(fileError){
                 return;
             }
             self.bestAttemptContent.attachments = @[attachment];
             self.contentHandler(self.bestAttemptContent);
         }];
         [task resume];
       }
      }
      ```


For more information about rich push notifications with iOS, see [UNNotificationAttachment](https://developer.apple.com/documentation/usernotifications/unnotificationattachment).
