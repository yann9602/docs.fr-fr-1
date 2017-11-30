---
title: "Comment : utiliser des canaux anonymes pour la communication entre processus en local"
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
- cpp
helpviewer_keywords:
- anonymous pipes [.NET Framework]
- parent-child communication [.NET Framework]
- pipes [.NET Framework]
- one-way communication [.NET Framework]
- local computer communication [.NET Framework], pipes
ms.assetid: e7773c77-c646-4a01-8a96-a003d59fc4c9
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: f457cc91e6fbfc118e5363d1b0a8e8c2ad800748
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-anonymous-pipes-for-local-interprocess-communication"></a><span data-ttu-id="0eab9-102">Comment : utiliser des canaux anonymes pour la communication entre processus en local</span><span class="sxs-lookup"><span data-stu-id="0eab9-102">How to: Use Anonymous Pipes for Local Interprocess Communication</span></span>
<span data-ttu-id="0eab9-103">Les canaux anonymes fournissent une communication interprocessuse sur un ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="0eab9-103">Anonymous pipes provide interprocess communication on a local computer.</span></span> <span data-ttu-id="0eab9-104">Ils offrent moins de fonctionnalités que les canaux nommés, mais également nécessitent moins de surcharge.</span><span class="sxs-lookup"><span data-stu-id="0eab9-104">They offer less functionality than named pipes, but also require less overhead.</span></span> <span data-ttu-id="0eab9-105">Vous pouvez utiliser des canaux anonymes pour faciliter la communication entre processus sur un ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="0eab9-105">You can use anonymous pipes to make interprocess communication on a local computer easier.</span></span> <span data-ttu-id="0eab9-106">Vous ne pouvez pas utiliser des canaux anonymes pour la communication sur un réseau.</span><span class="sxs-lookup"><span data-stu-id="0eab9-106">You cannot use anonymous pipes for communication over a network.</span></span>  
  
 <span data-ttu-id="0eab9-107">Pour implémenter des canaux anonymes, utilisez le <xref:System.IO.Pipes.AnonymousPipeServerStream> et <xref:System.IO.Pipes.AnonymousPipeClientStream> classes.</span><span class="sxs-lookup"><span data-stu-id="0eab9-107">To implement anonymous pipes, use the <xref:System.IO.Pipes.AnonymousPipeServerStream> and <xref:System.IO.Pipes.AnonymousPipeClientStream> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0eab9-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="0eab9-108">Example</span></span>  
 <span data-ttu-id="0eab9-109">L’exemple suivant montre une façon de pour envoyer une chaîne à partir d’un processus parent à un processus enfant à l’aide de canaux anonymes.</span><span class="sxs-lookup"><span data-stu-id="0eab9-109">The following example demonstrates a way to send a string from a parent process to a child process using anonymous pipes.</span></span> <span data-ttu-id="0eab9-110">Cet exemple crée un <xref:System.IO.Pipes.AnonymousPipeServerStream> objet dans un processus parent avec un <xref:System.IO.Pipes.PipeDirection> valeur <xref:System.IO.Pipes.PipeDirection.Out>.</span><span class="sxs-lookup"><span data-stu-id="0eab9-110">This example creates an <xref:System.IO.Pipes.AnonymousPipeServerStream> object in a parent process with a <xref:System.IO.Pipes.PipeDirection> value of <xref:System.IO.Pipes.PipeDirection.Out>.</span></span> <span data-ttu-id="0eab9-111">Le processus parent crée ensuite un processus enfant à l’aide d’un handle de client pour créer un <xref:System.IO.Pipes.AnonymousPipeClientStream> objet.</span><span class="sxs-lookup"><span data-stu-id="0eab9-111">The parent process then creates a child process by using a client handle to create an <xref:System.IO.Pipes.AnonymousPipeClientStream> object.</span></span> <span data-ttu-id="0eab9-112">Le processus enfant a un <xref:System.IO.Pipes.PipeDirection> valeur <xref:System.IO.Pipes.PipeDirection.In>.</span><span class="sxs-lookup"><span data-stu-id="0eab9-112">The child process has a <xref:System.IO.Pipes.PipeDirection> value of <xref:System.IO.Pipes.PipeDirection.In>.</span></span>  
  
 <span data-ttu-id="0eab9-113">Le processus parent envoie ensuite une chaîne fournie par l’utilisateur au processus enfant.</span><span class="sxs-lookup"><span data-stu-id="0eab9-113">The parent process then sends a user-supplied string to the child process.</span></span> <span data-ttu-id="0eab9-114">La chaîne est affichée sur la console dans le processus enfant.</span><span class="sxs-lookup"><span data-stu-id="0eab9-114">The string is displayed to the console in the child process.</span></span>  
  
 <span data-ttu-id="0eab9-115">L’exemple suivant montre le processus du serveur.</span><span class="sxs-lookup"><span data-stu-id="0eab9-115">The following example shows the server process.</span></span>  
  
 [!code-cpp[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/vb/program.vb#01)]  
  
## <a name="example"></a><span data-ttu-id="0eab9-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="0eab9-116">Example</span></span>  
 <span data-ttu-id="0eab9-117">L’exemple suivant montre le processus client.</span><span class="sxs-lookup"><span data-stu-id="0eab9-117">The following example shows the client process.</span></span> <span data-ttu-id="0eab9-118">Le processus serveur démarre le processus client ainsi que ce processus un handle de client.</span><span class="sxs-lookup"><span data-stu-id="0eab9-118">The server process starts the client process and gives that process a client handle.</span></span> <span data-ttu-id="0eab9-119">Le fichier exécutable obtenu à partir du code client doit être nommé `pipeClient.exe` et être copié dans le même répertoire que l’exécutable avant d’exécuter le processus du serveur du serveur.</span><span class="sxs-lookup"><span data-stu-id="0eab9-119">The resulting executable from the client code should be named `pipeClient.exe` and be copied to the same directory as the server executable before running the server process.</span></span>  
  
 [!code-cpp[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/vb/program.vb#01)]  
  
## <a name="see-also"></a><span data-ttu-id="0eab9-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0eab9-120">See Also</span></span>  
 [<span data-ttu-id="0eab9-121">Canaux</span><span class="sxs-lookup"><span data-stu-id="0eab9-121">Pipes</span></span>](../../../docs/standard/io/pipe-operations.md)  
 [<span data-ttu-id="0eab9-122">Guide pratique pour utiliser des canaux nommés pour la communication entre processus en réseau</span><span class="sxs-lookup"><span data-stu-id="0eab9-122">How to: Use Named Pipes for Network Interprocess Communication</span></span>](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md)
