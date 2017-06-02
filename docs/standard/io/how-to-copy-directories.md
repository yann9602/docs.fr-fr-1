---
title: "Comment&#160;: copier des r&#233;pertoires | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "copier des répertoires"
  - "répertoires (.NET Framework), copier"
  - "copie de répertoires"
  - "E/S (.NET Framework), copier des répertoires"
  - "copier des sous-répertoires"
ms.assetid: 5a969765-e5f8-4b4e-977e-90e2b0a1fe3c
caps.latest.revision: 11
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 11
---
# Comment&#160;: copier des r&#233;pertoires
Cet exemple montre comment utiliser les classes d’E\/S pour copier de manière synchrone le contenu d’un répertoire vers un autre emplacement. Dans cet exemple, l’utilisateur peut spécifier s’il veut aussi copier les sous\-répertoires. Si les sous\-répertoires sont copiés, la méthode utilisée dans cet exemple le fait de manière récursive en s’appelant elle\-même sur chaque sous\-répertoire suivant jusqu’à ce qu’il n’y ait plus rien à copier.  
  
 Pour obtenir un exemple de copie de fichiers de manière asynchrone, consultez [E\/S sur fichier asynchrones](../../../docs/standard/io/e-s-sur-fichier-asynchrones.md).  
  
## Exemple  
 [!code-csharp[System.IO.Directory_Copy#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Directory_Copy/cs/program.cs#1)]
 [!code-vb[System.IO.Directory_Copy#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Directory_Copy/vb/Program.vb#1)]  
  
## Voir aussi  
 <xref:System.IO.FileInfo>   
 <xref:System.IO.DirectoryInfo>   
 <xref:System.IO.FileStream>   
 [Fichier et flux de données E\/S](../../../docs/standard/io/index.md)   
 [Tâches d'E\/S courantes](../../../docs/standard/io/commons-tasks.md)   
 [E\/S sur fichier asynchrones](../../../docs/standard/io/e-s-sur-fichier-asynchrones.md)