---
title: "Opérations de canal dans le .NET Framework"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipes [.NET Framework]
- pipe operations [.NET Framework]
- interprocess communication [.NET Framework], pipes
- I/O [.NET Framework], pipes
ms.assetid: 7b964ebd-7a4f-4d28-8194-7841f9e4c702
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 879e5a73417f9347224bc22b397814b83972751c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="pipe-operations-in-the-net-framework"></a><span data-ttu-id="be77c-102">Opérations de canal dans le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="be77c-102">Pipe Operations in the .NET Framework</span></span>
<span data-ttu-id="be77c-103">Les canaux fournissent un moyen de communication entre processus.</span><span class="sxs-lookup"><span data-stu-id="be77c-103">Pipes provide a means for interprocess communication.</span></span> <span data-ttu-id="be77c-104">Il existe deux types de canaux :</span><span class="sxs-lookup"><span data-stu-id="be77c-104">There are two types of pipes:</span></span>  
  
-   <span data-ttu-id="be77c-105">Canaux anonymes.</span><span class="sxs-lookup"><span data-stu-id="be77c-105">Anonymous pipes.</span></span>  
  
     <span data-ttu-id="be77c-106">Les canaux anonymes fournissent une communication interprocessuse sur un ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="be77c-106">Anonymous pipes provide interprocess communication on a local computer.</span></span> <span data-ttu-id="be77c-107">Les canaux anonymes nécessitent moins de traitement que les canaux nommés, mais ils offrent des services limités.</span><span class="sxs-lookup"><span data-stu-id="be77c-107">Anonymous pipes require less overhead than named pipes but offer limited services.</span></span> <span data-ttu-id="be77c-108">Les canaux anonymes sont unidirectionnels et ne peut pas être utilisés sur un réseau.</span><span class="sxs-lookup"><span data-stu-id="be77c-108">Anonymous pipes are one-way and cannot be used over a network.</span></span> <span data-ttu-id="be77c-109">Ils prennent en charge uniquement une seule instance de serveur.</span><span class="sxs-lookup"><span data-stu-id="be77c-109">They support only a single server instance.</span></span> <span data-ttu-id="be77c-110">Les canaux anonymes sont utiles pour la communication entre les threads ou entre processus parent et enfant où les handles de canaux peuvent être facilement passés au processus enfant lors de sa création.</span><span class="sxs-lookup"><span data-stu-id="be77c-110">Anonymous pipes are useful for communication between threads, or between parent and child processes where the pipe handles can be easily passed to the child process when it is created.</span></span>  
  
     <span data-ttu-id="be77c-111">Dans le .NET Framework, vous implémentez les canaux anonymes à l’aide de la <xref:System.IO.Pipes.AnonymousPipeServerStream> et <xref:System.IO.Pipes.AnonymousPipeClientStream> classes.</span><span class="sxs-lookup"><span data-stu-id="be77c-111">In the .NET Framework, you implement anonymous pipes by using the <xref:System.IO.Pipes.AnonymousPipeServerStream> and <xref:System.IO.Pipes.AnonymousPipeClientStream> classes.</span></span>  
  
     <span data-ttu-id="be77c-112">Consultez [Comment : utiliser des canaux anonymes pour la Communication interprocessus Local](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md).</span><span class="sxs-lookup"><span data-stu-id="be77c-112">See [How to: Use Anonymous Pipes for Local Interprocess Communication](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md).</span></span>  
  
-   <span data-ttu-id="be77c-113">Canaux nommés.</span><span class="sxs-lookup"><span data-stu-id="be77c-113">Named pipes.</span></span>  
  
     <span data-ttu-id="be77c-114">Canaux nommés fournissent la communication entre un serveur de canaux et un ou plusieurs clients de canal.</span><span class="sxs-lookup"><span data-stu-id="be77c-114">Named pipes provide interprocess communication between a pipe server and one or more pipe clients.</span></span> <span data-ttu-id="be77c-115">Canaux nommés peuvent être unidirectionnels ou en duplex.</span><span class="sxs-lookup"><span data-stu-id="be77c-115">Named pipes can be one-way or duplex.</span></span> <span data-ttu-id="be77c-116">Ils prennent en charge la communication basée sur le message et permettent à plusieurs clients à se connecter simultanément au processus serveur à l’aide du même nom de canal.</span><span class="sxs-lookup"><span data-stu-id="be77c-116">They support message-based communication and allow multiple clients to connect simultaneously to the server process using the same pipe name.</span></span> <span data-ttu-id="be77c-117">Canaux nommés prennent également en charge l’emprunt d’identité, ce qui permet le processus de connexion d’utiliser leurs propres autorisations sur des serveurs distants.</span><span class="sxs-lookup"><span data-stu-id="be77c-117">Named pipes also support impersonation, which enables connecting processes to use their own permissions on remote servers.</span></span>  
  
     <span data-ttu-id="be77c-118">Dans le .NET Framework, vous implémentez des canaux nommés à l’aide de la <xref:System.IO.Pipes.NamedPipeServerStream> et <xref:System.IO.Pipes.NamedPipeClientStream> classes.</span><span class="sxs-lookup"><span data-stu-id="be77c-118">In the .NET Framework, you implement named pipes by using the <xref:System.IO.Pipes.NamedPipeServerStream> and <xref:System.IO.Pipes.NamedPipeClientStream> classes.</span></span>  
  
     <span data-ttu-id="be77c-119">Consultez [Comment : utiliser des canaux nommés pour la Communication de réseau](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md).</span><span class="sxs-lookup"><span data-stu-id="be77c-119">See [How to: Use Named Pipes for Network Interprocess Communication](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be77c-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="be77c-120">See Also</span></span>  
 [<span data-ttu-id="be77c-121">Fichier et flux de données E/S</span><span class="sxs-lookup"><span data-stu-id="be77c-121">File and Stream I-O</span></span>](../../../docs/standard/io/index.md)  
 [<span data-ttu-id="be77c-122">Guide pratique pour utiliser des canaux anonymes pour la communication entre processus en local</span><span class="sxs-lookup"><span data-stu-id="be77c-122">How to: Use Anonymous Pipes for Local Interprocess Communication</span></span>](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md)  
 [<span data-ttu-id="be77c-123">Guide pratique pour utiliser des canaux nommés pour la communication entre processus en réseau</span><span class="sxs-lookup"><span data-stu-id="be77c-123">How to: Use Named Pipes for Network Interprocess Communication</span></span>](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md)
