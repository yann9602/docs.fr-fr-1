---
title: 'Comment : compresser et extraire des fichiers'
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
- I/O [.NET Framework], compression
- compression
- compress files
ms.assetid: e9876165-3c60-4c84-a272-513e47acf579
caps.latest.revision: "19"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 22a95ce18b602d4e329499c5d36557213e08a8b5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-compress-and-extract-files"></a>Comment : compresser et extraire des fichiers
Le <xref:System.IO.Compression> espace de noms contient les types suivants pour compresser et décompresser des fichiers et flux. Vous pouvez également utiliser ces types pour lire et modifier le contenu d’un fichier compressé :  
  
-   <xref:System.IO.Compression.ZipFile>  
  
-   <xref:System.IO.Compression.ZipArchive>  
  
-   <xref:System.IO.Compression.ZipArchiveEntry>  
  
-   <xref:System.IO.Compression.DeflateStream>  
  
-   <xref:System.IO.Compression.GZipStream>  
  
 Les exemples suivants illustrent certaines des fonctions que vous pouvez effectuer lorsque vous travaillez avec des fichiers compressés.  
  
## <a name="example"></a>Exemple  
 Cet exemple montre comment créer et d’extraire un fichier compressé qui a une extension de nom de fichier .zip à l’aide de la <xref:System.IO.Compression.ZipFile> classe. Il compresse le contenu d’un dossier dans un nouveau fichier .zip et extrait ensuite ce contenu vers un nouveau dossier. Pour utiliser le <xref:System.IO.Compression.ZipFile> (classe), vous devez référencer le `System.IO.Compression.FileSystem` assembly dans votre projet.  
  
 [!code-csharp[System.IO.Compression.ZipFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.zipfile/cs/program1.cs#1)]
 [!code-vb[System.IO.Compression.ZipFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.zipfile/vb/program1.vb#1)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment parcourir le contenu d’un fichier .zip existant et extraire les fichiers qui ont une extension .txt. Elle utilise le <xref:System.IO.Compression.ZipArchive> classe pour accéder à un fichier .zip existant et la <xref:System.IO.Compression.ZipArchiveEntry> classe pour inspecter les entrées individuelles dans le fichier compressé. Il utilise une méthode d’extension (<xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A>) pour le <xref:System.IO.Compression.ZipArchiveEntry> objet. La méthode d’extension est disponible dans le <xref:System.IO.Compression.ZipFileExtensions?displayProperty=nameWithType> classe. Pour utiliser le <xref:System.IO.Compression.ZipFileExtensions> (classe), vous devez référencer le `System.IO.Compression.FileSystem` assembly dans votre projet.  
  
 [!code-csharp[System.IO.Compression.ZipArchive#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchive/cs/program1.cs#1)]
 [!code-vb[System.IO.Compression.ZipArchive#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchive/vb/program1.vb#1)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise la <xref:System.IO.Compression.ZipArchive> classe pour accéder à un fichier .zip existant et ajoute un nouveau fichier au fichier compressé. Le nouveau fichier obtient compressé lorsque vous l’ajoutez au fichier .zip existant.  
  
 [!code-csharp[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/cs/program1.cs#1)]
 [!code-vb[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/vb/program1.vb#1)]  
  
## <a name="example"></a>Exemple  
 Vous pouvez également utiliser le <xref:System.IO.Compression.GZipStream> et <xref:System.IO.Compression.DeflateStream> classes pour compresser et décompresser les données. Ils utilisent le même algorithme de compression. Compressé <xref:System.IO.Compression.GZipStream> les objets qui sont écrits dans un fichier ayant une extension .gz peuvent être décompressés à l’aide de nombreux outils courants, outre les méthodes fournies par <xref:System.IO.Compression.GZipStream>. Cet exemple montre comment compresser et décompresser un répertoire de fichiers à l’aide de la <xref:System.IO.Compression.GZipStream> classe.  
  
 [!code-csharp[IO.Compression.GZip1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.Compression.GZip1/CS/gziptest.cs#1)]
 [!code-vb[IO.Compression.GZip1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.Compression.GZip1/VB/gziptest.vb#1)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.IO.Compression.ZipArchive>  
 <xref:System.IO.Compression.ZipFile>  
 <xref:System.IO.Compression.ZipArchiveEntry>  
 <xref:System.IO.Compression.DeflateStream>  
 <xref:System.IO.Compression.GZipStream>  
 [Fichier et flux de données E/S](../../../docs/standard/io/index.md)
