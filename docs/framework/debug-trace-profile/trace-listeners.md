---
title: "Écouteurs de la trace"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Listener object types
- listeners
- Trace class, listeners
- trace listeners, about trace listeners
- Listeners collection
- trace listeners
- tracing [.NET Framework], trace listeners
- logs, trace listeners
ms.assetid: 444b0d33-67ea-4c36-9e94-79c50f839025
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 56cbde16eff89d25960e510e7eec2424f15e51b5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="trace-listeners"></a>Écouteurs de la trace
Quand vous utilisez **Trace**, **Debug** et <xref:System.Diagnostics.TraceSource>, vous devez disposer d’un mécanisme de collecte et d’enregistrement des messages envoyés. Les messages de suivi sont reçus par des *écouteurs*. Le but d'un écouteur est de collecter, de stocker et de router les messages de suivi. Les écouteurs dirigent la sortie de suivi vers une cible appropriée, telle qu'un journal, une fenêtre ou un fichier de texte.  
  
 Les écouteurs sont disponibles pour les classes **Debug**, **Trace** et <xref:System.Diagnostics.TraceSource>, et chacune d’elles peut envoyer sa sortie à de nombreux objets écouteur. Voici les écouteurs prédéfinis couramment utilisés :  
  
-   <xref:System.Diagnostics.TextWriterTraceListener> redirige la sortie vers une instance de la classe <xref:System.IO.TextWriter> ou vers toute classe <xref:System.IO.Stream>. Il peut également écrire dans la console ou un fichier, car il s'agit de classes <xref:System.IO.Stream>.  
  
-   <xref:System.Diagnostics.EventLogTraceListener> redirige la sortie vers un journal d'événements.  
  
-   <xref:System.Diagnostics.DefaultTraceListener> émet des messages **Write** et **WriteLine** vers **OutputDebugString** et la méthode **Debugger.Log**. Dans Visual Studio, cela entraîne l'affichage des messages de débogage dans la fenêtre de sortie. Les messages **Fail** et les messages **Assert** d’échec émettent également vers l’API Windows **OutputDebugString** et la méthode **Debugger.Log**, et entraînent aussi l’affichage d’une boîte de message. Ce comportement est le comportement par défaut pour les messages **Debug** et **Trace**, car **DefaultTraceListener** est le seul écouteur automatiquement inclus dans chaque collection `Listeners`.  
  
-   <xref:System.Diagnostics.ConsoleTraceListener> dirige la sortie de traçage ou de débogage vers la sortie standard ou le flux d'erreurs standard.  
  
-   <xref:System.Diagnostics.DelimitedListTraceListener> dirige la sortie de traçage ou de débogage vers un writer de texte (par ex., un writer de flux), ou vers un flux de données (par ex., un flux de fichiers). Le format de la sortie de trace est un format de texte délimité qui utilise le délimiteur spécifié par la propriété <xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A>.  
  
-   <xref:System.Diagnostics.XmlWriterTraceListener> dirige la sortie de traçage ou de débogage sous forme de données encodées en XML vers un <xref:System.IO.TextWriter> ou un <xref:System.IO.Stream>, par exemple, un <xref:System.IO.FileStream>.  
  
 Si vous voulez qu’un autre écouteur en plus de <xref:System.Diagnostics.DefaultTraceListener> reçoive également la sortie de **Debug**, **Trace** et <xref:System.Diagnostics.TraceSource>, vous devez l’ajouter à la collection `Listeners`. Pour plus d’informations, consultez [Guide pratique pour créer et initialiser des écouteurs de suivi](../../../docs/framework/debug-trace-profile/how-to-create-and-initialize-trace-listeners.md) et [Guide pratique pour utiliser un TraceSource et des filtres avec des écouteurs de suivi](../../../docs/framework/debug-trace-profile/how-to-use-tracesource-and-filters-with-trace-listeners.md). N’importe quel écouteur de la collection **Listeners** reçoit les mêmes messages en provenance des méthodes de sortie de suivi. Par exemple, supposons que vous définissiez deux écouteurs : **TextWriterTraceListener** et **EventLogTraceListener**. Chaque écouteur reçoit le même message. **TextWriterTraceListener** dirige sa sortie vers un flux et **EventLogTraceListener** dirige sa sortie vers un journal des événements.  
  
 L’exemple suivant montre comment envoyer la sortie vers la collection **Listeners**.  
  
```vb  
' Use this example when debugging.  
Debug.WriteLine("Error in Widget 42")  
' Use this example when tracing.  
Trace.WriteLine("Error in Widget 42")  
```  
  
```csharp  
// Use this example when debugging.  
System.Diagnostics.Debug.WriteLine("Error in Widget 42");  
// Use this example when tracing.  
System.Diagnostics.Trace.WriteLine("Error in Widget 42");  
```  
  
 Debug et Trace partagent la même collection **Listeners** ; par conséquent, si vous ajoutez un objet écouteur à une collection **Debug.Listeners** dans votre application, il est également ajouté à la collection **Trace.Listeners**.  
  
 L'exemple suivant montre comment utiliser un écouteur pour envoyer des informations de traçage à une console :  
  
```vb  
Trace.Listeners.Clear()  
Trace.Listeners.Add(New TextWriterTraceListener(Console.Out))  
```  
  
```csharp  
System.Diagnostics.Trace.Listeners.Clear();  
System.Diagnostics.Trace.Listeners.Add(  
   new System.Diagnostics.TextWriterTraceListener(Console.Out));  
```  
  
## <a name="developer-defined-listeners"></a>Écouteurs définis par le développeur  
 Vous pouvez définir vos propres écouteurs en héritant de la classe de base **TraceListener** et en remplaçant ses méthodes par vos méthodes personnalisées. Pour plus d'informations sur la création d'écouteurs définis par le développeur, voir <xref:System.Diagnostics.TraceListener> dans la documentation .NET Framework.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Diagnostics.TextWriterTraceListener>  
 <xref:System.Diagnostics.EventLogTraceListener>  
 <xref:System.Diagnostics.DefaultTraceListener>  
 <xref:System.Diagnostics.TraceListener>  
 [Suivi et instrumentation d’applications](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)  
 [Commutateurs de suivi](../../../docs/framework/debug-trace-profile/trace-switches.md)
