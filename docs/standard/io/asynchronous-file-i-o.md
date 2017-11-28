---
title: E/S sur fichier asynchrones
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
- streams, synchronous streams
- asynchronous I/O
- synchronous I/O
- streams, asynchronous streams
- I/O [.NET Framework], asynchronous I/O
- Stream class, synchronous I/O
- data streams, asynchronous streams
- Stream class, asynchronous I/O
- multiple I/O requests
- data streams, synchronous streams
ms.assetid: dbdd55e7-d6b9-4f9e-8abb-ab0edd4457f7
caps.latest.revision: "23"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d8a461d79ecdcadc3f880f6a813918cf891abd45
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="asynchronous-file-io"></a><span data-ttu-id="f88ee-102">E/S sur fichier asynchrones</span><span class="sxs-lookup"><span data-stu-id="f88ee-102">Asynchronous File I/O</span></span>
<span data-ttu-id="f88ee-103">Les opérations asynchrones vous permettent d'exécuter des opérations d'E/S consommant beaucoup de ressources sans bloquer le thread principal.</span><span class="sxs-lookup"><span data-stu-id="f88ee-103">Asynchronous operations enable you to perform resource-intensive I/O operations without blocking the main thread.</span></span> <span data-ttu-id="f88ee-104">Cette considération de performance est particulièrement importante dans une application [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] ou une application [!INCLUDE[desktop_appname](../../../includes/desktop-appname-md.md)] où une longue opération de flux peut bloquer le thread d'interface utilisateur et faire que l'application s'affiche comme si elle ne fonctionnait pas.</span><span class="sxs-lookup"><span data-stu-id="f88ee-104">This performance consideration is particularly important in a [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] app or [!INCLUDE[desktop_appname](../../../includes/desktop-appname-md.md)] app where a time-consuming stream operation can block the UI thread and make your app appear as if it is not working.</span></span>  
  
 <span data-ttu-id="f88ee-105">Depuis le [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], les types d'E/S incluent des méthodes async pour simplifier les opérations asynchrones.</span><span class="sxs-lookup"><span data-stu-id="f88ee-105">Starting with the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], the I/O types include async methods to simplify asynchronous operations.</span></span> <span data-ttu-id="f88ee-106">Une méthode asynchrone contient `Async` dans son nom, comme <xref:System.IO.Stream.ReadAsync%2A>, <xref:System.IO.Stream.WriteAsync%2A>, <xref:System.IO.Stream.CopyToAsync%2A>, <xref:System.IO.Stream.FlushAsync%2A>, <xref:System.IO.TextReader.ReadLineAsync%2A>, et <xref:System.IO.TextReader.ReadToEndAsync%2A>.</span><span class="sxs-lookup"><span data-stu-id="f88ee-106">An async method contains `Async` in its name, such as <xref:System.IO.Stream.ReadAsync%2A>, <xref:System.IO.Stream.WriteAsync%2A>, <xref:System.IO.Stream.CopyToAsync%2A>, <xref:System.IO.Stream.FlushAsync%2A>, <xref:System.IO.TextReader.ReadLineAsync%2A>, and <xref:System.IO.TextReader.ReadToEndAsync%2A>.</span></span> <span data-ttu-id="f88ee-107">Ces méthodes asynchrones sont implémentées sur les classes de flux, telles que <xref:System.IO.Stream>, <xref:System.IO.FileStream>, <xref:System.IO.MemoryStream>, et les classes qui sont utilisées pour lire ou écrire dans des flux, comme <xref:System.IO.TextReader> et l' <xref:System.IO.TextWriter>.</span><span class="sxs-lookup"><span data-stu-id="f88ee-107">These async methods are implemented on stream classes, such as <xref:System.IO.Stream>, <xref:System.IO.FileStream>, and <xref:System.IO.MemoryStream>, and on classes that are used for reading from or writing to streams, such <xref:System.IO.TextReader> and <xref:System.IO.TextWriter>.</span></span>  
  
 <span data-ttu-id="f88ee-108">Dans .NET Framework 4 et les versions antérieures, on doit utiliser des méthodes telles que <xref:System.IO.Stream.BeginRead%2A> et <xref:System.IO.Stream.EndRead%2A> pour implémenter les opérations d'E/S asynchrones.</span><span class="sxs-lookup"><span data-stu-id="f88ee-108">In the .NET Framework 4 and earlier versions, you have to use methods such as <xref:System.IO.Stream.BeginRead%2A> and <xref:System.IO.Stream.EndRead%2A> to implement asynchronous I/O operations.</span></span> <span data-ttu-id="f88ee-109">Ces méthodes sont toujours disponibles dans [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] pour prendre en charge le code hérité. Toutefois, les méthodes asynchrones vous aident à implémenter les opérations d'E/S asynchrones plus facilement.</span><span class="sxs-lookup"><span data-stu-id="f88ee-109">These methods are still available in the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] to support legacy code; however, the async methods help you implement asynchronous I/O operations more easily.</span></span>  
  
 <span data-ttu-id="f88ee-110">Depuis le [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], Visual Studio fournit deux mots clés pour la programmation asynchrone :</span><span class="sxs-lookup"><span data-stu-id="f88ee-110">Starting with [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], Visual Studio provides two keywords for asynchronous programming:</span></span>  
  
 <span data-ttu-id="f88ee-111">`Async` (Visual Basic) ou `async` modificateur (C#), qui est utilisé pour marquer une méthode contenant une opération asynchrone.</span><span class="sxs-lookup"><span data-stu-id="f88ee-111">`Async` (Visual Basic) or `async` (C#) modifier, which is used to mark a method that contains an asynchronous operation.</span></span>  
  
 <span data-ttu-id="f88ee-112">`Await` (Visual Basic) ou `await` opérateur (C#), qui est appliqué au résultat d'une méthode asynchrone.</span><span class="sxs-lookup"><span data-stu-id="f88ee-112">`Await` (Visual Basic) or `await` (C#) operator, which is applied to the result of an async method.</span></span>  
  
 <span data-ttu-id="f88ee-113">Pour implémenter des opérations d'E/S asynchrones, utilisez ces mots clés conjointement aux méthodes async, comme indiqué dans les exemples suivants.</span><span class="sxs-lookup"><span data-stu-id="f88ee-113">To implement asynchronous I/O operations, use these keywords in conjunction with the async methods, as shown in the following examples.</span></span> <span data-ttu-id="f88ee-114">Pour plus d’informations, consultez [Programmation asynchrone avec async et await](http://msdn.microsoft.com/library/db854f91-ccef-4035-ae4d-0911fde808c7).</span><span class="sxs-lookup"><span data-stu-id="f88ee-114">For more information, see [Asynchronous Programming with Async and Await](http://msdn.microsoft.com/library/db854f91-ccef-4035-ae4d-0911fde808c7).</span></span>  
  
 <span data-ttu-id="f88ee-115">L'exemple suivant montre comment utiliser deux objets <xref:System.IO.FileStream> pour copier des fichiers de façon asynchrone d'un répertoire à un autre.</span><span class="sxs-lookup"><span data-stu-id="f88ee-115">The following example demonstrates how to use two <xref:System.IO.FileStream> objects to copy files asynchronously from one directory to another.</span></span> <span data-ttu-id="f88ee-116">Notez que le gestionnaire d'événements <xref:System.Web.UI.WebControls.Button.Click> pour le contrôle <xref:System.Windows.Controls.Button> est marqué avec le modificateur `async` car il appelle une méthode asynchrone.</span><span class="sxs-lookup"><span data-stu-id="f88ee-116">Notice that the <xref:System.Web.UI.WebControls.Button.Click> event handler for the <xref:System.Windows.Controls.Button> control is marked with the `async` modifier because it calls an asynchronous method.</span></span>  
  
 [!code-csharp[Asynchronous_File_IO_async#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Asynchronous_File_IO_async/cs/example.cs#1)]
 [!code-vb[Asynchronous_File_IO_async#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Asynchronous_File_IO_async/vb/example.vb#1)]  
  
 <span data-ttu-id="f88ee-117">L'exemple suivant est semblable au précédent, mais utilise des objets <xref:System.IO.StreamReader> et <xref:System.IO.StreamWriter> pour lire et écrire le contenu d'un fichier texte de façon asynchrone.</span><span class="sxs-lookup"><span data-stu-id="f88ee-117">The next example is similar to the previous one but uses <xref:System.IO.StreamReader> and <xref:System.IO.StreamWriter> objects to read and write the contents of a text file asynchronously.</span></span>  
  
 [!code-csharp[Asynchronous_File_IO_async#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Asynchronous_File_IO_async/cs/example2.cs#2)]
 [!code-vb[Asynchronous_File_IO_async#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Asynchronous_File_IO_async/vb/example2.vb#2)]  
  
 <span data-ttu-id="f88ee-118">L'exemple suivant montre le fichier code-behind et le fichier XAML utilisés pour ouvrir un fichier comme <xref:System.IO.Stream> dans une application [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] , et lire son contenu en utilisant une instance de la classe <xref:System.IO.StreamReader> .</span><span class="sxs-lookup"><span data-stu-id="f88ee-118">The next example shows the code-behind file and the XAML file that are used to open a file as a <xref:System.IO.Stream> in a [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] app, and read its contents by using an instance of the <xref:System.IO.StreamReader> class.</span></span> <span data-ttu-id="f88ee-119">Il utilise des méthodes asynchrones pour ouvrir le fichier en tant que flux et lire son contenu.</span><span class="sxs-lookup"><span data-stu-id="f88ee-119">It uses asynchronous methods to open the file as a stream and to read its contents.</span></span>  
  
 [!code-csharp[System.IO.WindowsRuntimeStorageExtensions#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestorageextensions/cs/blankpage.xaml.cs#2)]
 [!code-vb[System.IO.WindowsRuntimeStorageExtensions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.windowsruntimestorageextensions/vb/blankpage.xaml.vb#2)]  
  
 [!code-xaml[System.IO.WindowsRuntimeStorageExtensions#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestorageextensions/cs/blankpage.xaml#1)]  
  
## <a name="see-also"></a><span data-ttu-id="f88ee-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f88ee-120">See Also</span></span>  
 <xref:System.IO.Stream>  
 [<span data-ttu-id="f88ee-121">Fichier et flux de données E/S</span><span class="sxs-lookup"><span data-stu-id="f88ee-121">File and Stream I/O</span></span>](../../../docs/standard/io/index.md)  
 [<span data-ttu-id="f88ee-122">Programmation asynchrone avec Async et Await</span><span class="sxs-lookup"><span data-stu-id="f88ee-122">Asynchronous Programming with Async and Await</span></span>](http://msdn.microsoft.com/library/db854f91-ccef-4035-ae4d-0911fde808c7)
