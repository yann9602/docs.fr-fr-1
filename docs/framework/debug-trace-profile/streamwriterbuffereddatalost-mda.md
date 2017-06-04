---
title: "streamWriterBufferedDataLost MDA | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "StreamWriter class, data buffering problems"
  - "managed debugging assistants (MDAs), StreamWriter data buffering"
  - "buffers, StreamWriter problems"
  - "MDAs (managed debugging assistants), StreamWriter data buffering"
  - "StreamWriter buffered data lost"
  - "data buffering problems"
  - "streamWriterBufferedDataLost MDA"
ms.assetid: 6e5c07be-bc5b-437a-8398-8779e23126ab
caps.latest.revision: 8
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 8
---
# streamWriterBufferedDataLost MDA
L'Assistant Débogage managé \(MDA, Managed Debugging Assistant\) `streamWriterBufferedDataLost` est activé lors d'une écriture dans <xref:System.IO.StreamWriter> mais la méthode <xref:System.IO.StreamWriter.Flush%2A> ou <xref:System.IO.StreamWriter.Close%2A> n'est pas appelée par la suite avant la destruction de l'instance du <xref:System.IO.StreamWriter>.  Lorsque cet Assistant Débogage managé est activé, le runtime détermine s'il existe encore des données mises en mémoire tampon dans <xref:System.IO.StreamWriter>.  Si c'est le cas, l'Assistant Débogage managé est activé.  L'appel aux méthodes <xref:System.GC.Collect%2A> et <xref:System.GC.WaitForPendingFinalizers%2A> peut forcer des finaliseurs à s'exécuter.  Sinon, les finaliseurs s'exécuteront à des moments apparemment arbitraires, voire pas du tout lors de la sortie du processus.  L'exécution explicite des finaliseurs avec cet Assistant Débogage managé activé aide à reproduire ce type de problème de façon plus fiable.  
  
## Symptômes  
 Un <xref:System.IO.StreamWriter> n'écrit pas les 1 à 4 derniers octets de données dans un fichier.  
  
## Cause  
 Le <xref:System.IO.StreamWriter> met les données en mémoire tampon en interne, ce qui exige un appel à la méthode <xref:System.IO.StreamWriter.Close%2A> ou <xref:System.IO.StreamWriter.Flush%2A> pour écrire les données mises en mémoire tampon dans le magasin de données sous\-jacent.  Si <xref:System.IO.StreamWriter.Close%2A> ou <xref:System.IO.StreamWriter.Flush%2A> n'est pas appelé au moment opportun, les données mises en mémoire tampon dans l'instance de <xref:System.IO.StreamWriter> ne peuvent être écrites comme prévu.  
  
 L'exemple suivant illustre un code mal écrit que cet Assistant Débogage managé doit intercepter.  
  
```  
// Poorly written code.  
void Write()   
{  
    StreamWriter sw = new StreamWriter("file.txt");  
    sw.WriteLine("Data");  
    // Problem: forgot to close the StreamWriter.  
}  
```  
  
 Le code précédent activera plus certainement cet Assistant Débogage managé si un garbage collection est déclenché avant d'être suspendu jusqu'au terme de l'exécution des finaliseurs.  Pour localiser ce type de problème, vous pouvez ajouter le code suivant à la fin de la méthode précédente dans une version de débogage.  Cela permet d'activer systématiquement l'Assistant Débogage managé même si cela ne résout évidemment pas la cause du problème.  
  
```  
GC.Collect();  
GC.WaitForPendingFinalizers();  
```  
  
## Résolution  
 Veillez à appeler <xref:System.IO.StreamWriter.Close%2A> ou <xref:System.IO.StreamWriter.Flush%2A> sur le <xref:System.IO.StreamWriter> avant de fermer une application ou tout bloc de code possédant une instance de <xref:System.IO.StreamWriter>.  Pour ce faire, une des solutions les plus efficaces consiste à créer l'instance avec un bloc `using` C\# \(`Using` en Visual Basic\) qui garantit l'appel à la méthode <xref:System.IO.StreamWriter.Dispose%2A> pour le writer, ce qui permet de fermer correctement l'instance.  
  
```  
using(StreamWriter sw = new StreamWriter("file.txt"))   
{  
    sw.WriteLine("Data");  
}  
```  
  
 Le code suivant illustre la même solution, à l'aide de `try/finally` au lieu de `using`.  
  
```  
StreamWriter sw;  
try   
{  
    sw = new StreamWriter("file.txt"));  
    sw.WriteLine("Data");  
}  
finally   
{  
    if (sw != null)  
        sw.Close();  
}  
```  
  
 Si aucune de ces solutions ne peut être utilisée \(par exemple, si un <xref:System.IO.StreamWriter> est stocké dans une variable statique et que vous ne pouvez pas exécuter facilement du code à la fin de sa durée de vie\), l'appel à <xref:System.IO.StreamWriter.Flush%2A> sur le <xref:System.IO.StreamWriter> après sa dernière utilisation ou l'affectation de la valeur `true` à la propriété <xref:System.IO.StreamWriter.AutoFlush%2A> avant sa première utilisation doit éviter ce problème.  
  
```  
private static StreamWriter log;  
// static class constructor.  
static WriteToFile()   
{  
    StreamWriter sw = new StreamWriter("log.txt");  
    sw.AutoFlush = true;  
  
    // Publish the StreamWriter for other threads.  
    log = sw;  
}  
```  
  
## Effet sur le runtime  
 Cet Assistant Débogage managé n'a aucun effet sur le runtime.  
  
## Sortie  
 Un message signale cette violation.  
  
## Configuration  
  
```  
<mdaConfig>  
  <assistants>  
    <streamWriterBufferedDataLost />  
  </assistants>  
</mdaConfig>  
```  
  
## Voir aussi  
 <xref:System.IO.StreamWriter>   
 [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)