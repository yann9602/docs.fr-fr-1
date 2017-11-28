---
title: "Comment : écrire du texte dans un fichier"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- writing text to files
- I/O [.NET Framework], writing text to files
- streams, writing text to files
- data streams, writing text to files
ms.assetid: 060cbe06-2adf-4337-9e7b-961a5c840208
caps.latest.revision: "29"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9605e514be380415d3c8b66ed28ae7de0a52ca1e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-text-to-a-file"></a><span data-ttu-id="282a1-102">Comment : écrire du texte dans un fichier</span><span class="sxs-lookup"><span data-stu-id="282a1-102">How to: Write Text to a File</span></span>
<span data-ttu-id="282a1-103">Cette rubrique présente différentes façons d’écrire du texte dans un fichier pour les applications .NET Framework ou pour les applications du [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="282a1-103">This topic shows different ways you can write text to a file for .NET Framework applications or [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] apps.</span></span> <span data-ttu-id="282a1-104">Les classes et méthodes suivantes sont généralement utilisées pour écrire du texte dans un fichier :</span><span class="sxs-lookup"><span data-stu-id="282a1-104">The following classes and methods are typically used to write text to a file:</span></span>  
  
-   <span data-ttu-id="282a1-105"><xref:System.IO.StreamWriter> : contient des méthodes permettant d’écrire dans un fichier de façon synchrone (<xref:System.IO.StreamWriter.Write%2A> ou <xref:System.IO.TextWriter.WriteLine%2A>) ou asynchrone (<xref:System.IO.StreamWriter.WriteAsync%2A> et <xref:System.IO.StreamWriter.WriteLineAsync%2A>).</span><span class="sxs-lookup"><span data-stu-id="282a1-105"><xref:System.IO.StreamWriter> - it contains methods to write to a file synchronously (<xref:System.IO.StreamWriter.Write%2A> or <xref:System.IO.TextWriter.WriteLine%2A>) or asynchronously (<xref:System.IO.StreamWriter.WriteAsync%2A> and <xref:System.IO.StreamWriter.WriteLineAsync%2A>).</span></span>  
  
-   <span data-ttu-id="282a1-106"><xref:System.IO.File> : à utiliser avec les applications .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="282a1-106"><xref:System.IO.File> – to be used with .NET Framework applications.</span></span> <span data-ttu-id="282a1-107">Elle fournit des méthodes statiques pour écrire du texte dans un fichier, comme <xref:System.IO.File.WriteAllLines%2A> et <xref:System.IO.File.WriteAllText%2A>ou pour ajouter du texte à un fichier (<xref:System.IO.File.AppendAllLines%2A>, <xref:System.IO.File.AppendAllText%2A> ou <xref:System.IO.File.AppendText%2A>).</span><span class="sxs-lookup"><span data-stu-id="282a1-107">It provides static methods to write text to a file such as <xref:System.IO.File.WriteAllLines%2A> and <xref:System.IO.File.WriteAllText%2A>, or to append text to a file (<xref:System.IO.File.AppendAllLines%2A>, <xref:System.IO.File.AppendAllText%2A> or <xref:System.IO.File.AppendText%2A>).</span></span>  
  
-   <span data-ttu-id="282a1-108">[FileIO](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.aspx) à utiliser avec les applications du [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="282a1-108">[FileIO](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.aspx) - to be used with [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] apps.</span></span> <span data-ttu-id="282a1-109">Elle contient des méthodes asynchrones pour écrire du texte dans un fichier ([WriteLinesAsync](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.writelinesasync.aspx) ou [WriteTextAsync](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.writetextasync.aspx)) ou pour ajouter du texte à un fichier ([AppendLinesAsync](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.appendlinesasync.aspx) ou [AppendTextAsync](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.appendtextasync.aspx)).</span><span class="sxs-lookup"><span data-stu-id="282a1-109">It contains asynchronous methods to write text to a file ([WriteLinesAsync](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.writelinesasync.aspx) or [WriteTextAsync](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.writetextasync.aspx)) or to append text to a file ([AppendLinesAsync](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.appendlinesasync.aspx) or [AppendTextAsync](https://msdn.microsoft.com/library/windows/apps/windows.storage.fileio.appendtextasync.aspx)).</span></span>  
  
 <span data-ttu-id="282a1-110">Les exemples sont simples afin de mettre l’accent sur la tâche en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="282a1-110">The samples have been kept simple in order to focus on the task being performed.</span></span> <span data-ttu-id="282a1-111">C’est pourquoi ils effectuent une vérification des erreurs et une gestion des exceptions minimales, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="282a1-111">For this reason, the samples perform minimal error checking and exception handling, if any.</span></span> <span data-ttu-id="282a1-112">Une application réelle fournit généralement une vérification des erreurs et une gestion des exceptions plus robuste.</span><span class="sxs-lookup"><span data-stu-id="282a1-112">A real-world application generally provides more robust error checking and exception handling.</span></span>  
  
## <a name="example"></a><span data-ttu-id="282a1-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="282a1-113">Example</span></span>  
 <span data-ttu-id="282a1-114">L’exemple suivant montre comment écrire, ligne par ligne, du texte de façon synchrone dans un nouveau fichier à l’aide de la classe <xref:System.IO.StreamWriter> .</span><span class="sxs-lookup"><span data-stu-id="282a1-114">The following example shows how to synchronously write text to a new file using the <xref:System.IO.StreamWriter> class, one line at a time.</span></span> <span data-ttu-id="282a1-115">Le nouveau fichier texte est enregistré dans le dossier Mes documents de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="282a1-115">The new text file is saved to the user's My Documents folder.</span></span> <span data-ttu-id="282a1-116">Étant donné que l’objet <xref:System.IO.StreamWriter> est déclaré et instancié dans une instruction `using` , la méthode <xref:System.IO.StreamWriter.Dispose%2A> est appelée, ce qui vide et ferme automatiquement le flux.</span><span class="sxs-lookup"><span data-stu-id="282a1-116">Because the <xref:System.IO.StreamWriter> object is declared and instantiated in a `using` statement, the <xref:System.IO.StreamWriter.Dispose%2A> method is invoked which automatically flushes and closes the stream.</span></span>  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source.cs#writeline)] 
 [!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source.vb#writeline)]  
  
## <a name="example"></a><span data-ttu-id="282a1-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="282a1-117">Example</span></span>  
 <span data-ttu-id="282a1-118">L’exemple suivant montre comment ajouter du texte à un fichier existant à l’aide de la classe <xref:System.IO.StreamWriter> .</span><span class="sxs-lookup"><span data-stu-id="282a1-118">The following example shows how to append text to an existing file using the <xref:System.IO.StreamWriter> class.</span></span> <span data-ttu-id="282a1-119">Il utilise le même fichier texte que l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="282a1-119">It uses the same text file from the previous example.</span></span>  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#AppendText](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source.cs#appendtext)] 
 [!code-vb[Conceptual.BasicIO.TextFiles#AppendText](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source.vb#appendtext)]     
  
## <a name="example"></a><span data-ttu-id="282a1-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="282a1-120">Example</span></span>  
 <span data-ttu-id="282a1-121">L’exemple suivant montre comment écrire du texte de façon asynchrone dans un nouveau fichier à l’aide de la classe <xref:System.IO.StreamWriter> .</span><span class="sxs-lookup"><span data-stu-id="282a1-121">The following example shows how to asynchronously write text to a new file using the <xref:System.IO.StreamWriter> class.</span></span> <span data-ttu-id="282a1-122">Pour appeler la méthode <xref:System.IO.StreamWriter.WriteAsync%2A> , l’appel de méthode doit se trouver dans une méthode `async` .</span><span class="sxs-lookup"><span data-stu-id="282a1-122">In order to invoke the <xref:System.IO.StreamWriter.WriteAsync%2A> method, the method call needs to be within an `async` method.</span></span> <span data-ttu-id="282a1-123">Le nouveau fichier texte est enregistré dans le dossier Mes documents de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="282a1-123">The new text file is saved to the user's My Documents folder.</span></span>  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#WriteAsync](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source.cs#writeasync)] 
 [!code-vb[Conceptual.BasicIO.TextFiles#WriteAsync](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source.vb#writeasync)]  
  
## <a name="example"></a><span data-ttu-id="282a1-124">Exemple</span><span class="sxs-lookup"><span data-stu-id="282a1-124">Example</span></span>  
 <span data-ttu-id="282a1-125">L’exemple suivant montre comment écrire du texte dans un nouveau fichier et ajouter de nouvelles lignes de texte à ce même fichier à l’aide de la classe <xref:System.IO.File> .</span><span class="sxs-lookup"><span data-stu-id="282a1-125">The following example shows how to write text to a new file and append new lines of text to the same file using the <xref:System.IO.File> class.</span></span> <span data-ttu-id="282a1-126">Les méthodes <xref:System.IO.File.WriteAllText%2A> et <xref:System.IO.File.AppendAllLines%2A> ouvrent et ferment automatiquement le fichier.</span><span class="sxs-lookup"><span data-stu-id="282a1-126">The <xref:System.IO.File.WriteAllText%2A> and <xref:System.IO.File.AppendAllLines%2A> methods open and close the file automatically.</span></span> <span data-ttu-id="282a1-127">Si le chemin que vous fournissez à la méthode <xref:System.IO.File.WriteAllText%2A> existe déjà, le fichier est remplacé.</span><span class="sxs-lookup"><span data-stu-id="282a1-127">If the path you provide to the <xref:System.IO.File.WriteAllText%2A> method already exists, the file will be overwritten.</span></span>  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#WriteFile](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source.cs#writefile)] 
 [!code-vb[Conceptual.BasicIO.TextFiles#WriteFile](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source.vb#writefile)]  
  
## <a name="example"></a><span data-ttu-id="282a1-128">Exemple</span><span class="sxs-lookup"><span data-stu-id="282a1-128">Example</span></span>  
 <span data-ttu-id="282a1-129">L'exemple suivant montre comment écrire de façon asynchrone une entrée utilisateur vers un fichier texte dans une application du [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="282a1-129">The following example shows how to asynchronously write user input to a text file in a [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] app.</span></span> <span data-ttu-id="282a1-130">Pour des raisons de sécurité, l’ouverture d’un fichier à partir d’une application du [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] requiert généralement l’utilisation d’un contrôle [FileOpenPicker](http://msdn.microsoft.com/library/windows/apps/windows.storage.pickers.fileopenpicker.aspx) .</span><span class="sxs-lookup"><span data-stu-id="282a1-130">Because of security considerations, opening a file from a [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] app typically requires the use of a [FileOpenPicker](http://msdn.microsoft.com/library/windows/apps/windows.storage.pickers.fileopenpicker.aspx) control.</span></span> <span data-ttu-id="282a1-131">Dans cet exemple, le `FileOpenPicker` est filtré pour afficher les fichiers texte.</span><span class="sxs-lookup"><span data-stu-id="282a1-131">In this example, the `FileOpenPicker` is filtered to show text files.</span></span>  
  
```xaml  
<Page  
    x:Class="OpenFileWindowsStore.MainPage"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    xmlns:local="using:OpenFileWindowsStore"  
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
    mc:Ignorable="d">  
  
    <Grid Background="{ThemeResource ApplicationPageBackgroundThemeBrush}">  
        <Button Content="save text to a file" HorizontalAlignment="Left" Margin="103,417,0,0" VerticalAlignment="Top"   
                Width="329" Height="86" FontSize="35" Click="Button_Click"/>  
        <TextBox Name="UserInputTextBox"  FontSize="18" HorizontalAlignment="Left" Margin="106,146,0,0"   
                 TextWrapping="Wrap" Text="Write some text here, and select a file to write it to." VerticalAlignment="Top"   
                 Height="201" Width="558" AcceptsReturn="True"/>  
        <TextBlock Name="StatusTextBox" HorizontalAlignment="Left" Margin="106,570,0,147" TextWrapping="Wrap" Text="Status:"   
                   VerticalAlignment="Center" Height="51" Width="1074" FontSize="18" />  
    </Grid>  
</Page>  
```  
  
 [!code-csharp[OpenFileWindowsStore#Code](../../../samples/snippets/csharp/VS_Snippets_CLR/openfilewindowsstore/cs/mainpage.xaml.cs#code)]
 [!code-vb[OpenFileWindowsStore#Code](../../../samples/snippets/visualbasic/VS_Snippets_CLR/openfilewindowsstore/vb/mainpage.xaml.vb#code)]  
  
## <a name="see-also"></a><span data-ttu-id="282a1-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="282a1-132">See Also</span></span>  
 <xref:System.IO.StreamWriter>  
 <xref:System.IO.File.CreateText%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="282a1-133">Guide pratique pour énumérer des répertoires et des fichiers</span><span class="sxs-lookup"><span data-stu-id="282a1-133">How to: Enumerate Directories and Files</span></span>](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
 [<span data-ttu-id="282a1-134">Comment : lire et écrire dans un fichier de données créé récemment</span><span class="sxs-lookup"><span data-stu-id="282a1-134">How to: Read and Write to a Newly Created Data File</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
 [<span data-ttu-id="282a1-135">Comment : ouvrir un fichier journal et y ajouter des éléments</span><span class="sxs-lookup"><span data-stu-id="282a1-135">How to: Open and Append to a Log File</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
 [<span data-ttu-id="282a1-136">Comment : lire du texte dans un fichier</span><span class="sxs-lookup"><span data-stu-id="282a1-136">How to: Read Text from a File</span></span>](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
 [<span data-ttu-id="282a1-137">Fichier et flux de données E/S</span><span class="sxs-lookup"><span data-stu-id="282a1-137">File and Stream I-O</span></span>](../../../docs/standard/io/index.md)
