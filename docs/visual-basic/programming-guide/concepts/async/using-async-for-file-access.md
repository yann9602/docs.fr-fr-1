---
title: "Utiliser Async pour l’accès aux fichiers (Visual Basic) | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: c989305f-08e3-4687-95c3-948465cda202
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: e0e548989b1d2c32b9faf5ce0dd90ae371dfc028
ms.lasthandoff: 03/13/2017

---
# <a name="using-async-for-file-access-visual-basic"></a>Utilisation d’async pour l’accès aux fichiers (Visual Basic)
Vous pouvez utiliser la fonctionnalité Async pour accéder aux fichiers. La fonctionnalité Async vous permet d’appeler des méthodes asynchrones sans utiliser de rappels ni fractionner votre code entre plusieurs méthodes ou expressions lambda. Pour rendre le code synchrone asynchrone, vous juste appelez une méthode asynchrone au lieu d’une méthode synchrone et ajoutez quelques mots clés pour le code.  
  
 Vous pouvez envisager les raisons pour l’ajout d’asynchronie aux appels d’accès de fichier suivantes :  
  
-   Comportement asynchrone rend les applications de l’interface utilisateur plus réactive, car le thread d’interface utilisateur qui lance l’opération peut effectuer d’autres tâches. Si le thread d’interface utilisateur doit exécuter du code qui prend beaucoup de temps (par exemple, plus de 50 millisecondes), l’interface utilisateur peut bloquer jusqu'à ce que l’e/s est terminée et que le thread d’interface utilisateur peut encore traiter clavier et d’entrée et d’autres événements de souris.  
  
-   Comportement asynchrone améliore l’évolutivité d’ASP.NET et d’autres applications basées sur le serveur en réduisant la nécessité pour les threads. Si l’application utilise un thread dédié par réponse mille demandes sont traitées simultanément, les threads de milliers sont nécessaires. Opérations asynchrones souvent n’avez pas besoin d’utiliser un thread pendant l’attente. Ils utilisent le thread d’achèvement d’e/s existant brièvement à la fin.  
  
-   La latence d’une opération d’accès de fichier peut être très faible dans les conditions actuelles, mais la latence peut augmenter considérablement à l’avenir. Par exemple, un fichier peut être déplacé vers un serveur qui est dans le monde entier.  
  
-   La surcharge de l’utilisation de la fonctionnalité Async est faible.  
  
-   Tâches asynchrones peuvent facilement être exécutées en parallèle.  
  
## <a name="running-the-examples"></a>Exécution des exemples  
 Pour exécuter les exemples dans cette rubrique, vous pouvez créer un **Application WPF** ou **Application Windows Forms** , puis ajoutez un **bouton**. Dans son `Click` événement, ajoutez un appel à la première méthode dans chaque exemple.  
  
 Dans les exemples suivants, sont les suivantes `Imports` instructions.  
  
```vb  
Imports System  
Imports System.Collections.Generic  
Imports System.Diagnostics  
Imports System.IO  
Imports System.Text  
Imports System.Threading.Tasks  
```  
  
## <a name="use-of-the-filestream-class"></a>Utilisation de la classe FileStream  
 Les exemples de cette rubrique utilisent la <xref:System.IO.FileStream>classe, qui possède une option entraînant des e/s asynchrones se produire au niveau du système d’exploitation.</xref:System.IO.FileStream> À l’aide de cette option, vous pouvez éviter de bloquer un thread de pool de threads dans de nombreux cas. Pour activer cette option, vous spécifiez la `useAsync=true` ou `options=FileOptions.Asynchronous` argument dans l’appel de constructeur.  
  
 Vous ne pouvez pas utiliser cette option et <xref:System.IO.StreamReader> <xref:System.IO.StreamWriter>Si vous les ouvrez directement en spécifiant un chemin d’accès.</xref:System.IO.StreamWriter> </xref:System.IO.StreamReader> Toutefois, vous pouvez utiliser cette option si vous leur fournissez un <xref:System.IO.Stream>qui le <xref:System.IO.FileStream>classe ouvert.</xref:System.IO.FileStream> </xref:System.IO.Stream> Notez que les appels asynchrones sont plus rapides dans les applications d’interface utilisateur même si un thread est bloqué, car le thread d’interface utilisateur n’est pas bloquée pendant l’attente.  
  
## <a name="writing-text"></a>Écriture de texte  
 L’exemple suivant écrit du texte dans un fichier. À chaque instruction await, la méthode se termine immédiatement. Lorsque le fichier d’e/s est terminé, la méthode reprend à l’instruction qui suit l’instruction await. Notez que le modificateur async est la définition des méthodes qui utilisent l’instruction await.  
  
```vb  
Public Async Sub ProcessWrite()  
    Dim filePath = "temp2.txt"  
    Dim text = "Hello World" & ControlChars.CrLf  
  
    Await WriteTextAsync(filePath, text)  
End Sub  
  
Private Async Function WriteTextAsync(filePath As String, text As String) As Task  
    Dim encodedText As Byte() = Encoding.Unicode.GetBytes(text)  
  
    Using sourceStream As New FileStream(filePath,  
        FileMode.Append, FileAccess.Write, FileShare.None,  
        bufferSize:=4096, useAsync:=True)  
  
        Await sourceStream.WriteAsync(encodedText, 0, encodedText.Length)  
    End Using  
End Function  
```  
  
 L’exemple d’origine comporte l’instruction `Await sourceStream.WriteAsync(encodedText, 0, encodedText.Length)`, qui est une contraction des deux instructions suivantes :  
  
```vb  
Dim theTask As Task = sourceStream.WriteAsync(encodedText, 0, encodedText.Length)  
Await theTask  
```  
  
 La première instruction retourne une tâche et entraîne le traitement de fichier Démarrer. La deuxième instruction avec l’expression await entraîne la méthode immédiatement quitter et retourner une autre tâche. Lorsque le fichier de traitement ultérieur est terminée, l’exécution retourne à l’instruction qui suit await. Pour plus d’informations, consultez [flux de contrôle dans les programmes Async (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md).  
  
## <a name="reading-text"></a>Lire du texte  
 L’exemple suivant lit un fichier texte. Le texte est mis en mémoire tampon et, dans ce cas, placé dans un <xref:System.Text.StringBuilder>.</xref:System.Text.StringBuilder> Contrairement à l’exemple précédent, l’évaluation de l’expression await génère une valeur. Le <xref:System.IO.Stream.ReadAsync%2A>méthode renvoie un <xref:System.Threading.Tasks.Task> \< <xref:System.Int32>>, de sorte que l’évaluation de l’expression await génère une `Int32` valeur (`numRead`) une fois l’opération terminée.</xref:System.Int32> </xref:System.Threading.Tasks.Task> </xref:System.IO.Stream.ReadAsync%2A> Pour plus d’informations, consultez [les Types de retour Async (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).  
  
```vb  
Public Async Sub ProcessRead()  
    Dim filePath = "temp2.txt"  
  
    If File.Exists(filePath) = False Then  
        Debug.WriteLine("file not found: " & filePath)  
    Else  
        Try  
            Dim text As String = Await ReadTextAsync(filePath)  
            Debug.WriteLine(text)  
        Catch ex As Exception  
            Debug.WriteLine(ex.Message)  
        End Try  
    End If  
End Sub  
  
Private Async Function ReadTextAsync(filePath As String) As Task(Of String)  
  
    Using sourceStream As New FileStream(filePath,  
        FileMode.Open, FileAccess.Read, FileShare.Read,  
        bufferSize:=4096, useAsync:=True)  
  
        Dim sb As New StringBuilder  
  
        Dim buffer As Byte() = New Byte(&H1000) {}  
        Dim numRead As Integer  
        numRead = Await sourceStream.ReadAsync(buffer, 0, buffer.Length)  
        While numRead <> 0  
            Dim text As String = Encoding.Unicode.GetString(buffer, 0, numRead)  
            sb.Append(text)  
  
            numRead = Await sourceStream.ReadAsync(buffer, 0, buffer.Length)  
        End While  
  
        Return sb.ToString  
    End Using  
End Function  
```  
  
## <a name="parallel-asynchronous-io"></a>E/s asynchrones parallèles  
 L’exemple suivant montre le traitement en parallèle en écrivant 10 fichiers texte. Pour chaque fichier, la <xref:System.IO.Stream.WriteAsync%2A>méthode retourne une tâche qui est ensuite ajoutée à une liste de tâches.</xref:System.IO.Stream.WriteAsync%2A> La `Await Task.WhenAll(tasks)` instruction quitte la méthode et reprend au sein de la méthode lorsque le traitement du fichier est terminé pour toutes les tâches.  
  
 L’exemple ferme tous les <xref:System.IO.FileStream>instances dans un `Finally` bloquer une fois les tâches terminées.</xref:System.IO.FileStream> Si chaque `FileStream` a été créé à la place dans un `Imports` instruction, le `FileStream` peut être supprimé avant que la tâche a été effectuée.  
  
 Notez que toute amélioration des performances est presque entièrement à partir du traitement parallèle et pas le traitement asynchrone. Les avantages d’asynchronie sont qu’il n’occuper plusieurs threads, et qu’il ne bloquer le thread d’interface utilisateur.  
  
```vb  
Public Async Sub ProcessWriteMult()  
    Dim folder = "tempfolder\"  
    Dim tasks As New List(Of Task)  
    Dim sourceStreams As New List(Of FileStream)  
  
    Try  
        For index = 1 To 10  
            Dim text = "In file " & index.ToString & ControlChars.CrLf  
  
            Dim fileName = "thefile" & index.ToString("00") & ".txt"  
            Dim filePath = folder & fileName  
  
            Dim encodedText As Byte() = Encoding.Unicode.GetBytes(text)  
  
            Dim sourceStream As New FileStream(filePath,  
                FileMode.Append, FileAccess.Write, FileShare.None,  
                bufferSize:=4096, useAsync:=True)  
  
            Dim theTask As Task = sourceStream.WriteAsync(encodedText, 0, encodedText.Length)  
            sourceStreams.Add(sourceStream)  
  
            tasks.Add(theTask)  
        Next  
  
        Await Task.WhenAll(tasks)  
    Finally  
        For Each sourceStream As FileStream In sourceStreams  
            sourceStream.Close()  
        Next  
    End Try  
End Sub  
```  
  
 Lorsque vous utilisez le <xref:System.IO.Stream.WriteAsync%2A>et <xref:System.IO.Stream.ReadAsync%2A>méthodes, vous pouvez spécifier un <xref:System.Threading.CancellationToken>, qui vous permet d’annuler le flux de l’opération intermédiaire.</xref:System.Threading.CancellationToken> </xref:System.IO.Stream.ReadAsync%2A> </xref:System.IO.Stream.WriteAsync%2A> Pour plus d’informations, consultez [réglage (Visual Basic) de votre Application Async](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md) et [l’annulation dans les Threads managés](http://msdn.microsoft.com/library/eea11fe5-d8b0-4314-bb5d-8a58166fb1c3).  
  
## <a name="see-also"></a>Voir aussi  
 [Programmation asynchrone avec Async et Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)   
 [Types de retour Async (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md)   
 [Flux de contrôle dans les programmes Async (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)
