---
title: "Comment&#160;: compresser et extraire des fichiers | Microsoft Docs"
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
  - "E/S (.NET Framework), compression"
  - "compression"
  - "compresser des fichiers"
ms.assetid: e9876165-3c60-4c84-a272-513e47acf579
caps.latest.revision: 19
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 19
---
# Comment&#160;: compresser et extraire des fichiers
L'espace de noms <xref:System.IO.Compression> contient les types suivants compresser et décompresser vos fichiers et vos flux.  Vous pouvez également utiliser ces types pour lire et modifier le contenu d'un fichier compressé :  
  
-   <xref:System.IO.Compression.ZipFile>  
  
-   <xref:System.IO.Compression.ZipArchive>  
  
-   <xref:System.IO.Compression.ZipArchiveEntry>  
  
-   <xref:System.IO.Compression.DeflateStream>  
  
-   <xref:System.IO.Compression.GZipStream>  
  
 Les exemples suivants illustrent certaines fonctions que vous pouvez remplir lorsque vous utilisez des fichiers compressés.  
  
## Exemple  
 Cet exemple montre comment créer et extraire un fichier compressé avec une extension de nom de fichier .zip à l'aide de la classe <xref:System.IO.Compression.ZipFile>.  Il compresse le contenu d'un dossier dans une nouvelle archive zip, puis extrait ce contenu dans un nouveau dossier.  Pour utiliser la classe <xref:System.IO.Compression.ZipFile>, vous devez référencer l'assembly de `System.IO.Compression.FileSystem` dans votre projet.  
  
 [!code-csharp[System.IO.Compression.ZipFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.zipfile/cs/program1.cs#1)]
 [!code-vb[System.IO.Compression.ZipFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.zipfile/vb/program1.vb#1)]  
  
## Exemple  
 L'exemple suivant indique comment itérer au sein du contenu d'une archive zip existante et récupérer les fichiers qui ont l'extension .txt.  Il utilise la classe <xref:System.IO.Compression.ZipArchive> pour accéder à un fichier existant .zip, et la classe <xref:System.IO.Compression.ZipArchiveEntry> pour inspecter des entrées dans le fichier compressé.  Il utilise une méthode d'extension \(<xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A>\) de l'objet <xref:System.IO.Compression.ZipArchiveEntry>.  La méthode d'extension est disponible dans la classe <xref:System.IO.Compression.ZipFileExtensions?displayProperty=fullName>.  Pour utiliser la classe <xref:System.IO.Compression.ZipFileExtensions>, vous devez référencer l'assembly de `System.IO.Compression.FileSystem` dans votre projet.  
  
 [!code-csharp[System.IO.Compression.ZipArchive#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchive/cs/program1.cs#1)]
 [!code-vb[System.IO.Compression.ZipArchive#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchive/vb/program1.vb#1)]  
  
## Exemple  
 L'exemple suivant utilise la classe <xref:System.IO.Compression.ZipArchive> pour accéder à un fichier existant .zip, puis ajoute un nouveau fichier au fichier compressé.  Le fichier est compressé lorsque vous l'ajoutez au fichier existant .zip.  
  
 [!code-csharp[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/cs/program1.cs#1)]
 [!code-vb[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/vb/program1.vb#1)]  
  
## Exemple  
 Vous pouvez également utiliser des classes <xref:System.IO.Compression.GZipStream> et <xref:System.IO.Compression.DeflateStream> pour compresser et décompresser des données.  Ils font appel au même algorithme de compression.  Les objets à compression de <xref:System.IO.Compression.GZipStream> écrits dans un fichier avec une extension .gz peuvent être décompressés à l'aide de nombreux outils courants en plus de les méthodes fournies par <xref:System.IO.Compression.GZipStream>.  L'exemple suivant montre comment compresser et décompresser un répertoire de fichiers à l'aide de la classe <xref:System.IO.Compression.GZipStream>.  
  
 [!code-csharp[IO.Compression.GZip1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.Compression.GZip1/CS/gziptest.cs#1)]
 [!code-vb[IO.Compression.GZip1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.Compression.GZip1/VB/gziptest.vb#1)]  
  
## Voir aussi  
 <xref:System.IO.Compression.ZipArchive>   
 <xref:System.IO.Compression.ZipFile>   
 <xref:System.IO.Compression.ZipArchiveEntry>   
 <xref:System.IO.Compression.DeflateStream>   
 <xref:System.IO.Compression.GZipStream>   
 [Fichier et flux de données E\/S](../../../docs/standard/io/index.md)