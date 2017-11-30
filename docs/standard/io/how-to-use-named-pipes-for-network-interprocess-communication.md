---
title: "Comment : utiliser des canaux nommés pour la communication entre processus en réseau"
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
- message-based communication [.NET Framework], named pipes
- named pipes [.NET Framework]
- pipes [.NET Framework]
- multiple connections via named pipes
- network communications [.NET Framework], named pipes
- impersonation [.NET Framework], named pipes
- full duplex communcation [.NET Framework], named pipes
ms.assetid: 4e4d7e64-9f1b-4026-98f7-20488ac7b42b
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 952600e71311184c4a4f906734addbf335d0358a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-named-pipes-for-network-interprocess-communication"></a><span data-ttu-id="85be0-102">Comment : utiliser des canaux nommés pour la communication entre processus en réseau</span><span class="sxs-lookup"><span data-stu-id="85be0-102">How to: Use Named Pipes for Network Interprocess Communication</span></span>
<span data-ttu-id="85be0-103">Canaux nommés fournissent la communication entre un serveur de canaux et un ou plusieurs clients de canal.</span><span class="sxs-lookup"><span data-stu-id="85be0-103">Named pipes provide interprocess communication between a pipe server and one or more pipe clients.</span></span> <span data-ttu-id="85be0-104">Ils offrent plus de fonctionnalités que les canaux anonymes, qui fournissent la communication entre processus sur un ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="85be0-104">They offer more functionality than anonymous pipes, which provide interprocess communication on a local computer.</span></span> <span data-ttu-id="85be0-105">Canaux nommés prennent en charge la communication en duplex intégral sur un réseau et plusieurs instances de serveur, communication basée sur le message et emprunt d’identité du client, ce qui permet le processus de connexion d’utiliser leur propre jeu d’autorisations sur des serveurs distants.</span><span class="sxs-lookup"><span data-stu-id="85be0-105">Named pipes support full duplex communication over a network and multiple server instances, message-based communication, and client impersonation, which enables connecting processes to use their own set of permissions on remote servers.</span></span>  
  
 <span data-ttu-id="85be0-106">Pour implémenter des canaux nommés, utilisez le <xref:System.IO.Pipes.NamedPipeServerStream> et <xref:System.IO.Pipes.NamedPipeClientStream> classes.</span><span class="sxs-lookup"><span data-stu-id="85be0-106">To implement name pipes, use the <xref:System.IO.Pipes.NamedPipeServerStream> and <xref:System.IO.Pipes.NamedPipeClientStream> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="85be0-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="85be0-107">Example</span></span>  
 <span data-ttu-id="85be0-108">L’exemple suivant montre comment créer un canal nommé à l’aide de la <xref:System.IO.Pipes.NamedPipeServerStream> classe.</span><span class="sxs-lookup"><span data-stu-id="85be0-108">The following example demonstrates how to create a named pipe by using the <xref:System.IO.Pipes.NamedPipeServerStream> class.</span></span> <span data-ttu-id="85be0-109">Dans cet exemple, le processus serveur crée quatre threads.</span><span class="sxs-lookup"><span data-stu-id="85be0-109">In this example, the server process creates four threads.</span></span> <span data-ttu-id="85be0-110">Chaque thread peut accepter une connexion cliente.</span><span class="sxs-lookup"><span data-stu-id="85be0-110">Each thread can accept a client connection.</span></span> <span data-ttu-id="85be0-111">Le processus client connecté fournit ensuite le serveur avec un nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="85be0-111">The connected client process then supplies the server with a file name.</span></span> <span data-ttu-id="85be0-112">Si le client dispose des autorisations suffisantes, le processus serveur ouvre le fichier et renvoie son contenu au client.</span><span class="sxs-lookup"><span data-stu-id="85be0-112">If the client has sufficient permissions, the server process opens the file and sends its contents back to the client.</span></span>  
  
 [!code-cpp[System.IO.Pipes.NamedPipeServerStream_ImpersonationSample1#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeServerStream_ImpersonationSample1/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.NamedPipeServerStream_ImpersonationSample1#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeServerStream_ImpersonationSample1/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.NamedPipeServerStream_ImpersonationSample1#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeServerStream_ImpersonationSample1/vb/program.vb#01)]  
  
## <a name="example"></a><span data-ttu-id="85be0-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="85be0-113">Example</span></span>  
 <span data-ttu-id="85be0-114">L’exemple suivant montre le processus client qui utilise le <xref:System.IO.Pipes.NamedPipeClientStream> classe.</span><span class="sxs-lookup"><span data-stu-id="85be0-114">The following example shows the client process, which uses the <xref:System.IO.Pipes.NamedPipeClientStream> class.</span></span> <span data-ttu-id="85be0-115">Le client se connecte au processus serveur et envoie un nom de fichier sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="85be0-115">The client connects to the server process and sends a file name to the server.</span></span> <span data-ttu-id="85be0-116">L’exemple utilise l’emprunt d’identité, l’identité de l’application cliente est en cours d’exécution doit avoir l’autorisation d’accès au fichier.</span><span class="sxs-lookup"><span data-stu-id="85be0-116">The example uses impersonation, so the identity that is running the client application must have permission to access the file.</span></span> <span data-ttu-id="85be0-117">Le serveur envoie ensuite le contenu du fichier vers le client.</span><span class="sxs-lookup"><span data-stu-id="85be0-117">The server then sends the contents of the file back to the client.</span></span> <span data-ttu-id="85be0-118">Le contenu du fichier est ensuite affiché sur la console.</span><span class="sxs-lookup"><span data-stu-id="85be0-118">The file contents are then displayed to the console.</span></span>  
  
 [!code-csharp[System.IO.Pipes.NamedPipeClientStream_ImpersonationSample1#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeClientStream_ImpersonationSample1/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.NamedPipeClientStream_ImpersonationSample1#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.NamedPipeClientStream_ImpersonationSample1/vb/program.vb#01)]  
  
## <a name="robust-programming"></a><span data-ttu-id="85be0-119">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="85be0-119">Robust Programming</span></span>  
 <span data-ttu-id="85be0-120">Les processus client et serveur dans cet exemple sont censés être exécutés sur le même ordinateur, le nom du serveur fourni à la <xref:System.IO.Pipes.NamedPipeClientStream> objet est `"."`.</span><span class="sxs-lookup"><span data-stu-id="85be0-120">The client and server processes in this example are intended to run on the same computer, so the server name provided to the <xref:System.IO.Pipes.NamedPipeClientStream> object is `"."`.</span></span> <span data-ttu-id="85be0-121">Si les processus client et serveur étaient sur des ordinateurs distincts, `"."` aurait été remplacé par le nom réseau de l’ordinateur qui exécute le processus serveur.</span><span class="sxs-lookup"><span data-stu-id="85be0-121">If the client and server processes were on separate computers, `"."` would be replaced with the network name of the computer that runs the server process.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85be0-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="85be0-122">See Also</span></span>  
 <xref:System.Security.Principal.TokenImpersonationLevel>  
 <xref:System.IO.Pipes.NamedPipeServerStream.GetImpersonationUserName%2A>  
 [<span data-ttu-id="85be0-123">Canaux</span><span class="sxs-lookup"><span data-stu-id="85be0-123">Pipes</span></span>](../../../docs/standard/io/pipe-operations.md)  
 [<span data-ttu-id="85be0-124">Guide pratique pour utiliser des canaux anonymes pour la communication entre processus en local</span><span class="sxs-lookup"><span data-stu-id="85be0-124">How to: Use Anonymous Pipes for Local Interprocess Communication</span></span>](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md)
