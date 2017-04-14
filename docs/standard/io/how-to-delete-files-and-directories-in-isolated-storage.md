---
title: "Comment&#160;: supprimer des fichiers et des r&#233;pertoires dans un stockage isol&#233; | Microsoft Docs"
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
  - "stockage de données à l’aide du stockage isolé, suppression de fichiers et de répertoires"
  - "répertoires (.NET Framework), stockage isolé"
  - "fichiers (.NET Framework), stockage isolé"
  - "stockage isolé, suppression de fichiers et de répertoires"
  - "magasins de données, suppression de fichiers et de répertoires"
  - "magasins, création de fichiers et de répertoires"
  - "supprimer des fichiers dans un fichier de stockage isolé"
  - "stockage de données à l’aide du stockage isolé, suppression de fichiers et de répertoires"
  - "supprimer des répertoires dans un fichier de stockage isolé"
ms.assetid: 8fcc0dea-435b-4d40-ba4d-ba056265c202
caps.latest.revision: 12
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 12
---
# Comment&#160;: supprimer des fichiers et des r&#233;pertoires dans un stockage isol&#233;
Vous pouvez supprimer des répertoires et des fichiers dans un fichier de stockage isolé.  Dans un magasin, le fichier et le répertoire du temps du système d'exploitation et sont spécifiés comme relatif à la racine du système de fichiers virtuels.  Ils ne respectent pas la casse sur les systèmes d'exploitation Windows.  
  
 La classe <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=fullName> propose deux méthodes d'instance pour supprimer des répertoires et des fichiers : <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> et <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A>.  Une exception <xref:System.IO.IsolatedStorage.IsolatedStorageException> est levée si vous tentez de supprimer un fichier ou un répertoire qui n'existe pas.  Si vous incluez un caractère générique dans nom, <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> lève une exception <xref:System.IO.IsolatedStorage.IsolatedStorageException>, ainsi que <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteFile%2A> lève une exception <xref:System.ArgumentException>.  
  
 La méthode <xref:System.IO.IsolatedStorage.IsolatedStorageFile.DeleteDirectory%2A> échoue si le répertoire contient des fichiers ou des sous\-répertoires.  Vous pouvez utiliser les méthodes <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> et <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> pour récupérer les fichiers existants et les répertoires.  Pour plus d'informations sur la recherche le système de fichiers virtuel d'un magasin, consultez [Comment : rechercher des fichiers et des répertoires existants dans un stockage isolé](../../../docs/standard/io/how-to-find-existing-files-and-directories-in-isolated-storage.md).  
  
## Exemple  
 L'exemple de code suivant crée, puis supprime plusieurs répertoires et fichiers.  
  
 [!code-cpp[Conceptual.IsolatedStorage#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source4.cpp#4)]
 [!code-csharp[Conceptual.IsolatedStorage#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source4.cs#4)]
 [!code-vb[Conceptual.IsolatedStorage#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source4.vb#4)]  
  
## Voir aussi  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile?displayProperty=fullName>   
 [Stockage isolé](../../../docs/standard/io/isolated-storage.md)