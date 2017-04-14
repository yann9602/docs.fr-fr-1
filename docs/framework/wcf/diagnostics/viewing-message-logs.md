---
title: "Consultation des journaux de messages | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3012fa13-f650-45fb-aaea-c5cca8c7d372
caps.latest.revision: 22
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 22
---
# Consultation des journaux de messages
Cette rubrique explique comment consulter les journaux de messages.  
  
## Consultation des journaux de messages dans Service Trace Viewer  
 Un message sera transformé s'il est traité par [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].Par conséquent, un message consigné reflète uniquement le contenu du message au moment où il a été consigné, et non pas le contenu sur le câble.  
  
 Comme la sortie de l'enregistrement des messages n'est pas liée au format de transfert du message, l'enregistrement des messages génère le message décodé.Si vous avez configuré l'enregistrement des messages correctement, tout message enregistré doit être au format de texte brut.Par exemple, le format \(texte brut\) des messages enregistrés n'est pas affecté par l'utilisation d'un encodeur de message binaire.  
  
 La sortie de XmlWriterTraceListener est un fichier qui contient une séquence de fragments XML.Sachez qu'il ne s'agit pas d'un fichier XML valide.Nous vous recommandons d'utiliser [Service Trace Viewer Tool \(SvcTraceViewer.exe\)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) pour consulter les fichiers journaux de messages.Pour plus d'informations sur l'utilisation de cet outil, consultez [Utilisation de Service Trace Viewer pour afficher les suivis corrélés et résoudre les problèmes](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).  
  
 Dans Service Trace Viewer, les messages sont répertoriés sous l'onglet **Message**.Les messages qui ont provoqué, ou qui sont liés à, une erreur de traitement sont surlignés en jaune \(niveau d'avertissement\) ou en rouge \(niveau d'erreur\), selon la gravité de l'erreur.Si vous double\-cliquez sur le message, le suivi du message s'affiche dans le contexte de la demande.  
  
> [!NOTE]
>  Si un message n'a pas d'en\-tête, aucune balise `<header/>` n'est enregistrée.  
  
## Consultation des messages consignés par un client, un relais et un service  
 Votre environnement peut contenir un client, qui envoie un message à un relais, qui par la suite envoie le message au service.Si la journalisation des messages est activée sur les trois emplacements, et que les trois journaux de messages sont affichés dans [Service Trace Viewer Tool \(SvcTraceViewer.exe\)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) simultanément, les échanges de journaux de messages seront restitués de manière incorrecte.Cela est dû au fait que `CorrelationId` et `ActivityId` dans l'en\-tête de message ne sont pas uniques pour chaque paire émetteur\-récepteur.  
  
 Pour résoudre ce problème, utilisez l'une des méthodes suivantes :  
  
-   N'affichez que deux des trois journaux de messages à la fois dans [Service Trace Viewer Tool \(SvcTraceViewer.exe\)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).  
  
-   Si vous devez afficher simultanément les trois journaux dans [Service Trace Viewer Tool \(SvcTraceViewer.exe\)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md), vous pouvez modifier le service de relais en créant une instance <xref:System.ServiceModel.Channels.Message>.Cette instance doit être une copie du corps du message entrant et de tous les en\-têtes à l'exception de `ActivityId` et `Action`.L'exemple de code suivant montre comment procéder.  
  
```  
Message outgoingMessage = Message.CreateMessage(incomingMessage.Version, incomingMessage.Headers.Action, incomingMessage.GetReaderAtBodyContents());  
  
for (int i = 0; i < incomingMessage.Headers.Count; i++)  
{  
   if (incomingMessage.Headers[i].Name.Equals("ActivityId", StringComparison.InvariantCultureIgnoreCase) ||  
incomingMessage.Headers[i].Name.Equals("Action", StringComparison.InvariantCultureIgnoreCase))  
   {  
      continue;  
    }  
    outgoingMessage.Headers.CopyHeaderFrom(incomingMessage, i);  
}  
```  
  
## Cas exceptionnels de contenu de journalisation de message inexact  
 Dans les conditions suivantes, les messages consignés peuvent ne pas être la représentation exacte du flux d'octets présent sur le câble.  
  
-   Concernant BasicHttpBinding, les en\-têtes d'enveloppe sont enregistrés pour les messages entrants de l'espace de noms \/addressing\/none.  
  
-   Les espaces blancs peuvent être incompatibles.  
  
-   Concernant les messages entrants, les éléments vides peuvent être représentés différemment.Par exemple, \<tag\>\<\/tag\> au lieu de \<tag\/\>  
  
-   Lorsque la journalisation PII connue est désactivée soit par défaut, soit par le paramètre explicite enableLoggingKnownPii\= "true".  
  
-   L'encodage est activé pour la conversion au format UTF\-8.  
  
## Voir aussi  
 [Service Trace Viewer Tool \(SvcTraceViewer.exe\)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)   
 [Utilisation de Service Trace Viewer pour afficher les suivis corrélés et résoudre les problèmes](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)   
 [Enregistrement des messages](../../../../docs/framework/wcf/diagnostics/message-logging.md)