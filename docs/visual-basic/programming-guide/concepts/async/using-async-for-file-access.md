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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 85f5fe17a012402c406eed972debd1f5889dd393
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="using-async-for-file-access-visual-basic"></a><span data-ttu-id="12dbc-102">Utilisation d’async pour l’accès aux fichiers (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="12dbc-102">Using Async for File Access (Visual Basic)</span></span>
<span data-ttu-id="12dbc-103">Vous pouvez utiliser la fonctionnalité Async pour accéder aux fichiers.</span><span class="sxs-lookup"><span data-stu-id="12dbc-103">You can use the Async feature to access files.</span></span> <span data-ttu-id="12dbc-104">La fonctionnalité Async vous permet d’appeler des méthodes asynchrones sans utiliser de rappels ni fractionner votre code entre plusieurs méthodes ou expressions lambda.</span><span class="sxs-lookup"><span data-stu-id="12dbc-104">By using the Async feature, you can call into asynchronous methods without using callbacks or splitting your code across multiple methods or lambda expressions.</span></span> <span data-ttu-id="12dbc-105">Pour rendre le code synchrone asynchrone, vous juste appelez une méthode asynchrone au lieu d’une méthode synchrone et ajoutez quelques mots clés pour le code.</span><span class="sxs-lookup"><span data-stu-id="12dbc-105">To make synchronous code asynchronous, you just call an asynchronous method instead of a synchronous method and add a few keywords to the code.</span></span>  
  
 <span data-ttu-id="12dbc-106">Vous pouvez envisager les raisons pour l’ajout d’asynchronie aux appels d’accès de fichier suivantes :</span><span class="sxs-lookup"><span data-stu-id="12dbc-106">You might consider the following reasons for adding asynchrony to file access calls:</span></span>  
  
-   <span data-ttu-id="12dbc-107">Comportement asynchrone rend les applications de l’interface utilisateur plus réactive, car le thread d’interface utilisateur qui lance l’opération peut effectuer d’autres tâches.</span><span class="sxs-lookup"><span data-stu-id="12dbc-107">Asynchrony makes UI applications more responsive because the UI thread that launches the operation can perform other work.</span></span> <span data-ttu-id="12dbc-108">Si le thread d’interface utilisateur doit exécuter du code qui prend beaucoup de temps (par exemple, plus de 50 millisecondes), l’interface utilisateur peut bloquer jusqu'à ce que l’e/s est terminée et que le thread d’interface utilisateur peut encore traiter clavier et d’entrée et d’autres événements de souris.</span><span class="sxs-lookup"><span data-stu-id="12dbc-108">If the UI thread must execute code that takes a long time (for example, more than 50 milliseconds), the UI may freeze until the I/O is complete and the UI thread can again process keyboard and mouse input and other events.</span></span>  
  
-   <span data-ttu-id="12dbc-109">Comportement asynchrone améliore l’évolutivité d’ASP.NET et d’autres applications basées sur le serveur en réduisant la nécessité pour les threads.</span><span class="sxs-lookup"><span data-stu-id="12dbc-109">Asynchrony improves the scalability of ASP.NET and other server-based applications by reducing the need for threads.</span></span> <span data-ttu-id="12dbc-110">Si l’application utilise un thread dédié par réponse mille demandes sont traitées simultanément, les threads de milliers sont nécessaires.</span><span class="sxs-lookup"><span data-stu-id="12dbc-110">If the application uses a dedicated thread per response and a thousand requests are being handled simultaneously, a thousand threads are needed.</span></span> <span data-ttu-id="12dbc-111">Opérations asynchrones souvent n’avez pas besoin d’utiliser un thread pendant l’attente.</span><span class="sxs-lookup"><span data-stu-id="12dbc-111">Asynchronous operations often don’t need to use a thread during the wait.</span></span> <span data-ttu-id="12dbc-112">Ils utilisent le thread d’achèvement d’e/s existant brièvement à la fin.</span><span class="sxs-lookup"><span data-stu-id="12dbc-112">They use the existing I/O completion thread briefly at the end.</span></span>  
  
-   <span data-ttu-id="12dbc-113">La latence d’une opération d’accès de fichier peut être très faible dans les conditions actuelles, mais la latence peut augmenter considérablement à l’avenir.</span><span class="sxs-lookup"><span data-stu-id="12dbc-113">The latency of a file access operation might be very low under current conditions, but the latency may greatly increase in the future.</span></span> <span data-ttu-id="12dbc-114">Par exemple, un fichier peut être déplacé vers un serveur qui est dans le monde entier.</span><span class="sxs-lookup"><span data-stu-id="12dbc-114">For example, a file may be moved to a server that's across the world.</span></span>  
  
-   <span data-ttu-id="12dbc-115">La surcharge de l’utilisation de la fonctionnalité Async est faible.</span><span class="sxs-lookup"><span data-stu-id="12dbc-115">The added overhead of using the Async feature is small.</span></span>  
  
-   <span data-ttu-id="12dbc-116">Tâches asynchrones peuvent facilement être exécutées en parallèle.</span><span class="sxs-lookup"><span data-stu-id="12dbc-116">Asynchronous tasks can easily be run in parallel.</span></span>  
  
## <a name="running-the-examples"></a><span data-ttu-id="12dbc-117">Exécution des exemples</span><span class="sxs-lookup"><span data-stu-id="12dbc-117">Running the Examples</span></span>  
 <span data-ttu-id="12dbc-118">Pour exécuter les exemples dans cette rubrique, vous pouvez créer un **Application WPF** ou **Application Windows Forms** , puis ajoutez un **bouton**.</span><span class="sxs-lookup"><span data-stu-id="12dbc-118">To run the examples in this topic, you can create a **WPF Application** or a **Windows Forms Application** and then add a **Button**.</span></span> <span data-ttu-id="12dbc-119">Dans son `Click` événement, ajoutez un appel à la première méthode dans chaque exemple.</span><span class="sxs-lookup"><span data-stu-id="12dbc-119">In the button's `Click` event, add a call to the first method in each example.</span></span>  
  
 <span data-ttu-id="12dbc-120">Dans les exemples suivants, sont les suivantes `Imports` instructions.</span><span class="sxs-lookup"><span data-stu-id="12dbc-120">In the following examples, include the following `Imports` statements.</span></span>  
  
```vb  
Imports System  
Imports System.Collections.Generic  
Imports System.Diagnostics  
Imports System.IO  
Imports System.Text  
Imports System.Threading.Tasks  
```  
  
## <a name="use-of-the-filestream-class"></a><span data-ttu-id="12dbc-121">Utilisation de la classe FileStream</span><span class="sxs-lookup"><span data-stu-id="12dbc-121">Use of the FileStream Class</span></span>  
 <span data-ttu-id="12dbc-122">Les exemples de cette rubrique utilisent la <xref:System.IO.FileStream>classe, qui possède une option entraînant des e/s asynchrones se produire au niveau du système d’exploitation.</xref:System.IO.FileStream></span><span class="sxs-lookup"><span data-stu-id="12dbc-122">The examples in this topic use the <xref:System.IO.FileStream> class, which has an option that causes asynchronous I/O to occur at the operating system level.</span></span> <span data-ttu-id="12dbc-123">À l’aide de cette option, vous pouvez éviter de bloquer un thread de pool de threads dans de nombreux cas.</span><span class="sxs-lookup"><span data-stu-id="12dbc-123">By using this option, you can avoid blocking a ThreadPool thread in many cases.</span></span> <span data-ttu-id="12dbc-124">Pour activer cette option, vous spécifiez la `useAsync=true` ou `options=FileOptions.Asynchronous` argument dans l’appel de constructeur.</span><span class="sxs-lookup"><span data-stu-id="12dbc-124">To enable this option, you specify the `useAsync=true` or `options=FileOptions.Asynchronous` argument in the constructor call.</span></span>  
  
 <span data-ttu-id="12dbc-125">Vous ne pouvez pas utiliser cette option et <xref:System.IO.StreamReader> <xref:System.IO.StreamWriter>Si vous les ouvrez directement en spécifiant un chemin d’accès.</xref:System.IO.StreamWriter> </xref:System.IO.StreamReader></span><span class="sxs-lookup"><span data-stu-id="12dbc-125">You can’t use this option with <xref:System.IO.StreamReader> and <xref:System.IO.StreamWriter> if you open them directly by specifying a file path.</span></span> <span data-ttu-id="12dbc-126">Toutefois, vous pouvez utiliser cette option si vous leur fournissez un <xref:System.IO.Stream>qui le <xref:System.IO.FileStream>classe ouvert.</xref:System.IO.FileStream> </xref:System.IO.Stream></span><span class="sxs-lookup"><span data-stu-id="12dbc-126">However, you can use this option if you provide them a <xref:System.IO.Stream> that the <xref:System.IO.FileStream> class opened.</span></span> <span data-ttu-id="12dbc-127">Notez que les appels asynchrones sont plus rapides dans les applications d’interface utilisateur même si un thread est bloqué, car le thread d’interface utilisateur n’est pas bloquée pendant l’attente.</span><span class="sxs-lookup"><span data-stu-id="12dbc-127">Note that asynchronous calls are faster in UI apps even if a ThreadPool thread is blocked, because the UI thread isn’t blocked during the wait.</span></span>  
  
## <a name="writing-text"></a><span data-ttu-id="12dbc-128">Écriture de texte</span><span class="sxs-lookup"><span data-stu-id="12dbc-128">Writing Text</span></span>  
 <span data-ttu-id="12dbc-129">L’exemple suivant écrit du texte dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="12dbc-129">The following example writes text to a file.</span></span> <span data-ttu-id="12dbc-130">À chaque instruction await, la méthode se termine immédiatement.</span><span class="sxs-lookup"><span data-stu-id="12dbc-130">At each await statement, the method immediately exits.</span></span> <span data-ttu-id="12dbc-131">Lorsque le fichier d’e/s est terminé, la méthode reprend à l’instruction qui suit l’instruction await.</span><span class="sxs-lookup"><span data-stu-id="12dbc-131">When the file I/O is complete, the method resumes at the statement that follows the await statement.</span></span> <span data-ttu-id="12dbc-132">Notez que le modificateur async est la définition des méthodes qui utilisent l’instruction await.</span><span class="sxs-lookup"><span data-stu-id="12dbc-132">Note that the async modifier is in the definition of methods that use the await statement.</span></span>  
  
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
  
 <span data-ttu-id="12dbc-133">L’exemple d’origine comporte l’instruction `Await sourceStream.WriteAsync(encodedText, 0, encodedText.Length)`, qui est une contraction des deux instructions suivantes :</span><span class="sxs-lookup"><span data-stu-id="12dbc-133">The original example has the statement `Await sourceStream.WriteAsync(encodedText, 0, encodedText.Length)`, which is a contraction of the following two statements:</span></span>  
  
```vb  
Dim theTask As Task = sourceStream.WriteAsync(encodedText, 0, encodedText.Length)  
Await theTask  
```  
  
 <span data-ttu-id="12dbc-134">La première instruction retourne une tâche et entraîne le traitement de fichier Démarrer.</span><span class="sxs-lookup"><span data-stu-id="12dbc-134">The first statement returns a task and causes file processing to start.</span></span> <span data-ttu-id="12dbc-135">La deuxième instruction avec l’expression await entraîne la méthode immédiatement quitter et retourner une autre tâche.</span><span class="sxs-lookup"><span data-stu-id="12dbc-135">The second statement with the await causes the method to immediately exit and return a different task.</span></span> <span data-ttu-id="12dbc-136">Lorsque le fichier de traitement ultérieur est terminée, l’exécution retourne à l’instruction qui suit await.</span><span class="sxs-lookup"><span data-stu-id="12dbc-136">When the file processing later completes, execution returns to the statement that follows the await.</span></span> <span data-ttu-id="12dbc-137">Pour plus d’informations, consultez [flux de contrôle dans les programmes Async (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md).</span><span class="sxs-lookup"><span data-stu-id="12dbc-137">For more information, see  [Control Flow in Async Programs (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md).</span></span>  
  
## <a name="reading-text"></a><span data-ttu-id="12dbc-138">Lire du texte</span><span class="sxs-lookup"><span data-stu-id="12dbc-138">Reading Text</span></span>  
 <span data-ttu-id="12dbc-139">L’exemple suivant lit un fichier texte.</span><span class="sxs-lookup"><span data-stu-id="12dbc-139">The following example reads text from a file.</span></span> <span data-ttu-id="12dbc-140">Le texte est mis en mémoire tampon et, dans ce cas, placé dans un <xref:System.Text.StringBuilder>.</xref:System.Text.StringBuilder></span><span class="sxs-lookup"><span data-stu-id="12dbc-140">The text is buffered and, in this case, placed into a <xref:System.Text.StringBuilder>.</span></span> <span data-ttu-id="12dbc-141">Contrairement à l’exemple précédent, l’évaluation de l’expression await génère une valeur.</span><span class="sxs-lookup"><span data-stu-id="12dbc-141">Unlike in the previous example, the evaluation of the await produces a value.</span></span> <span data-ttu-id="12dbc-142">Le <xref:System.IO.Stream.ReadAsync%2A>méthode renvoie un <xref:System.Threading.Tasks.Task> \< <xref:System.Int32>>, de sorte que l’évaluation de l’expression await génère une `Int32` valeur (`numRead`) une fois l’opération terminée.</xref:System.Int32> </xref:System.Threading.Tasks.Task> </xref:System.IO.Stream.ReadAsync%2A></span><span class="sxs-lookup"><span data-stu-id="12dbc-142">The <xref:System.IO.Stream.ReadAsync%2A> method returns a <xref:System.Threading.Tasks.Task>\<<xref:System.Int32>>, so the evaluation of the await produces an `Int32` value (`numRead`) after the operation completes.</span></span> <span data-ttu-id="12dbc-143">Pour plus d’informations, consultez [les Types de retour Async (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="12dbc-143">For more information, see [Async Return Types (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
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
  
## <a name="parallel-asynchronous-io"></a><span data-ttu-id="12dbc-144">E/s asynchrones parallèles</span><span class="sxs-lookup"><span data-stu-id="12dbc-144">Parallel Asynchronous I/O</span></span>  
 <span data-ttu-id="12dbc-145">L’exemple suivant montre le traitement en parallèle en écrivant 10 fichiers texte.</span><span class="sxs-lookup"><span data-stu-id="12dbc-145">The following example demonstrates parallel processing by writing 10 text files.</span></span> <span data-ttu-id="12dbc-146">Pour chaque fichier, la <xref:System.IO.Stream.WriteAsync%2A>méthode retourne une tâche qui est ensuite ajoutée à une liste de tâches.</xref:System.IO.Stream.WriteAsync%2A></span><span class="sxs-lookup"><span data-stu-id="12dbc-146">For each file, the <xref:System.IO.Stream.WriteAsync%2A> method returns a task that is then added to a list of tasks.</span></span> <span data-ttu-id="12dbc-147">La `Await Task.WhenAll(tasks)` instruction quitte la méthode et reprend au sein de la méthode lorsque le traitement du fichier est terminé pour toutes les tâches.</span><span class="sxs-lookup"><span data-stu-id="12dbc-147">The `Await Task.WhenAll(tasks)` statement exits the method and resumes within the method when file processing is complete for all of the tasks.</span></span>  
  
 <span data-ttu-id="12dbc-148">L’exemple ferme tous les <xref:System.IO.FileStream>instances dans un `Finally` bloquer une fois les tâches terminées.</xref:System.IO.FileStream></span><span class="sxs-lookup"><span data-stu-id="12dbc-148">The example closes all <xref:System.IO.FileStream> instances in a `Finally` block after the tasks are complete.</span></span> <span data-ttu-id="12dbc-149">Si chaque `FileStream` a été créé à la place dans un `Imports` instruction, le `FileStream` peut être supprimé avant que la tâche a été effectuée.</span><span class="sxs-lookup"><span data-stu-id="12dbc-149">If each `FileStream` was instead created in a `Imports` statement, the `FileStream` might be disposed of before the task was complete.</span></span>  
  
 <span data-ttu-id="12dbc-150">Notez que toute amélioration des performances est presque entièrement à partir du traitement parallèle et pas le traitement asynchrone.</span><span class="sxs-lookup"><span data-stu-id="12dbc-150">Note that any performance boost is almost entirely from the parallel processing and not the asynchronous processing.</span></span> <span data-ttu-id="12dbc-151">Les avantages d’asynchronie sont qu’il n’occuper plusieurs threads, et qu’il ne bloquer le thread d’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="12dbc-151">The advantages of asynchrony are that it doesn’t tie up multiple threads, and that it doesn’t tie up the user interface thread.</span></span>  
  
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
  
 <span data-ttu-id="12dbc-152">Lorsque vous utilisez le <xref:System.IO.Stream.WriteAsync%2A>et <xref:System.IO.Stream.ReadAsync%2A>méthodes, vous pouvez spécifier un <xref:System.Threading.CancellationToken>, qui vous permet d’annuler le flux de l’opération intermédiaire.</xref:System.Threading.CancellationToken> </xref:System.IO.Stream.ReadAsync%2A> </xref:System.IO.Stream.WriteAsync%2A></span><span class="sxs-lookup"><span data-stu-id="12dbc-152">When using the <xref:System.IO.Stream.WriteAsync%2A> and <xref:System.IO.Stream.ReadAsync%2A> methods, you can specify a <xref:System.Threading.CancellationToken>, which you can use to cancel the operation mid-stream.</span></span> <span data-ttu-id="12dbc-153">Pour plus d’informations, consultez [réglage (Visual Basic) de votre Application Async](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md) et [l’annulation dans les Threads managés](http://msdn.microsoft.com/library/eea11fe5-d8b0-4314-bb5d-8a58166fb1c3).</span><span class="sxs-lookup"><span data-stu-id="12dbc-153">For more information, see [Fine-Tuning Your Async Application (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md) and [Cancellation in Managed Threads](http://msdn.microsoft.com/library/eea11fe5-d8b0-4314-bb5d-8a58166fb1c3).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12dbc-154">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="12dbc-154">See Also</span></span>  
 <span data-ttu-id="12dbc-155">[Programmation asynchrone avec Async et Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md) </span><span class="sxs-lookup"><span data-stu-id="12dbc-155">[Asynchronous Programming with Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md) </span></span>  
<span data-ttu-id="12dbc-156"> [Types de retour Async (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md) </span><span class="sxs-lookup"><span data-stu-id="12dbc-156"> [Async Return Types (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md) </span></span>  
<span data-ttu-id="12dbc-157"> [Flux de contrôle dans les programmes Async (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)</span><span class="sxs-lookup"><span data-stu-id="12dbc-157"> [Control Flow in Async Programs (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)</span></span>
