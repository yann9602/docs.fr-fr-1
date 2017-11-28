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
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a5602a4e227f3cd17e4a7c9a086bee69d3e3e506
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-copy-directories"></a>Comment : copier des répertoires
Cet exemple montre comment utiliser les classes d’E/S pour copier de manière synchrone le contenu d’un répertoire vers un autre emplacement. Dans cet exemple, l’utilisateur peut spécifier s’il veut aussi copier les sous-répertoires. Si les sous-répertoires sont copiés, la méthode utilisée dans cet exemple le fait de manière récursive en s’appelant elle-même sur chaque sous-répertoire suivant jusqu’à ce qu’il n’y ait plus rien à copier.  
  
 Pour obtenir un exemple de copie de fichiers de manière asynchrone, consultez [Asynchronous File I/O](../../../docs/standard/io/asynchronous-file-i-o.md).  
  
## <a name="example"></a>Exemple  
 [!code-csharp[System.IO.Directory_Copy#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Directory_Copy/cs/program.cs#1)]
 [!code-vb[System.IO.Directory_Copy#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Directory_Copy/vb/Program.vb#1)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.IO.FileInfo>  
 <xref:System.IO.DirectoryInfo>  
 <xref:System.IO.FileStream>  
 [Fichier et flux de données E/S](../../../docs/standard/io/index.md)  
 [Tâches d’E/S courantes](../../../docs/standard/io/common-i-o-tasks.md)  
 [E/S sur fichier asynchrones](../../../docs/standard/io/asynchronous-file-i-o.md)
