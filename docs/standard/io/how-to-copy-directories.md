---
title: "Comment : copier des répertoires"
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
- directory copying
- I/O [.NET Framework], copying directories
- subdirectory copying
- copying directories
- directories [.NET Framework], copying
ms.assetid: 5a969765-e5f8-4b4e-977e-90e2b0a1fe3c
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 43e9027c1dbfc831f598991374c22434e01fe7ff
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-copy-directories"></a><span data-ttu-id="0e4c7-102">Comment : copier des répertoires</span><span class="sxs-lookup"><span data-stu-id="0e4c7-102">How to: Copy Directories</span></span>
<span data-ttu-id="0e4c7-103">Cet exemple montre comment utiliser les classes d’E/S pour copier de manière synchrone le contenu d’un répertoire vers un autre emplacement.</span><span class="sxs-lookup"><span data-stu-id="0e4c7-103">This example demonstrates how to use I/O classes to synchronously copy the contents of a directory to another location.</span></span> <span data-ttu-id="0e4c7-104">Dans cet exemple, l’utilisateur peut spécifier s’il veut aussi copier les sous-répertoires.</span><span class="sxs-lookup"><span data-stu-id="0e4c7-104">In this example, the user can specify whether to also copy the subdirectories.</span></span> <span data-ttu-id="0e4c7-105">Si les sous-répertoires sont copiés, la méthode utilisée dans cet exemple le fait de manière récursive en s’appelant elle-même sur chaque sous-répertoire suivant jusqu’à ce qu’il n’y ait plus rien à copier.</span><span class="sxs-lookup"><span data-stu-id="0e4c7-105">If the subdirectories are copied, the method in this example recursively copies them by calling itself on each subsequent subdirectory until there are no more to copy.</span></span>  
  
 <span data-ttu-id="0e4c7-106">Pour obtenir un exemple de copie de fichiers de manière asynchrone, consultez [Asynchronous File I/O](../../../docs/standard/io/asynchronous-file-i-o.md).</span><span class="sxs-lookup"><span data-stu-id="0e4c7-106">For an example of copying files asynchronously, see [Asynchronous File I/O](../../../docs/standard/io/asynchronous-file-i-o.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0e4c7-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="0e4c7-107">Example</span></span>  
 [!code-csharp[System.IO.Directory_Copy#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Directory_Copy/cs/program.cs#1)]
 [!code-vb[System.IO.Directory_Copy#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Directory_Copy/vb/Program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="0e4c7-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0e4c7-108">See Also</span></span>  
 <xref:System.IO.FileInfo>  
 <xref:System.IO.DirectoryInfo>  
 <xref:System.IO.FileStream>  
 [<span data-ttu-id="0e4c7-109">Fichier et flux de données E/S</span><span class="sxs-lookup"><span data-stu-id="0e4c7-109">File and Stream I/O</span></span>](../../../docs/standard/io/index.md)  
 [<span data-ttu-id="0e4c7-110">Tâches d’E/S courantes</span><span class="sxs-lookup"><span data-stu-id="0e4c7-110">Common I/O Tasks</span></span>](../../../docs/standard/io/common-i-o-tasks.md)  
 [<span data-ttu-id="0e4c7-111">E/S sur fichier asynchrones</span><span class="sxs-lookup"><span data-stu-id="0e4c7-111">Asynchronous File I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)
