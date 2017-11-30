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
# <a name="how-to-compress-and-extract-files"></a><span data-ttu-id="bc4b4-102">Comment : compresser et extraire des fichiers</span><span class="sxs-lookup"><span data-stu-id="bc4b4-102">How to: Compress and Extract Files</span></span>
<span data-ttu-id="bc4b4-103">Le <xref:System.IO.Compression> espace de noms contient les types suivants pour compresser et décompresser des fichiers et flux.</span><span class="sxs-lookup"><span data-stu-id="bc4b4-103">The <xref:System.IO.Compression> namespace contains the following types for compressing and decompressing files and streams.</span></span> <span data-ttu-id="bc4b4-104">Vous pouvez également utiliser ces types pour lire et modifier le contenu d’un fichier compressé :</span><span class="sxs-lookup"><span data-stu-id="bc4b4-104">You can also use these types to read and modify the contents of a compressed file:</span></span>  
  
-   <xref:System.IO.Compression.ZipFile>  
  
-   <xref:System.IO.Compression.ZipArchive>  
  
-   <xref:System.IO.Compression.ZipArchiveEntry>  
  
-   <xref:System.IO.Compression.DeflateStream>  
  
-   <xref:System.IO.Compression.GZipStream>  
  
 <span data-ttu-id="bc4b4-105">Les exemples suivants illustrent certaines des fonctions que vous pouvez effectuer lorsque vous travaillez avec des fichiers compressés.</span><span class="sxs-lookup"><span data-stu-id="bc4b4-105">The following examples show some of the functions you can perform when working with compressed files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bc4b4-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="bc4b4-106">Example</span></span>  
 <span data-ttu-id="bc4b4-107">Cet exemple montre comment créer et d’extraire un fichier compressé qui a une extension de nom de fichier .zip à l’aide de la <xref:System.IO.Compression.ZipFile> classe.</span><span class="sxs-lookup"><span data-stu-id="bc4b4-107">This example shows how to create and extract a compressed file that has a .zip file name extension by using the <xref:System.IO.Compression.ZipFile> class.</span></span> <span data-ttu-id="bc4b4-108">Il compresse le contenu d’un dossier dans un nouveau fichier .zip et extrait ensuite ce contenu vers un nouveau dossier.</span><span class="sxs-lookup"><span data-stu-id="bc4b4-108">It compresses the contents of a folder into a new .zip file and then extracts that content to a new folder.</span></span> <span data-ttu-id="bc4b4-109">Pour utiliser le <xref:System.IO.Compression.ZipFile> (classe), vous devez référencer le `System.IO.Compression.FileSystem` assembly dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="bc4b4-109">To use the <xref:System.IO.Compression.ZipFile> class, you must reference the `System.IO.Compression.FileSystem` assembly in your project.</span></span>  
  
 [!code-csharp[System.IO.Compression.ZipFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.zipfile/cs/program1.cs#1)]
 [!code-vb[System.IO.Compression.ZipFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.zipfile/vb/program1.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="bc4b4-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="bc4b4-110">Example</span></span>  
 <span data-ttu-id="bc4b4-111">L’exemple suivant montre comment parcourir le contenu d’un fichier .zip existant et extraire les fichiers qui ont une extension .txt.</span><span class="sxs-lookup"><span data-stu-id="bc4b4-111">The next example shows how to iterate through the contents of an existing .zip file and extract files that have a .txt extension.</span></span> <span data-ttu-id="bc4b4-112">Elle utilise le <xref:System.IO.Compression.ZipArchive> classe pour accéder à un fichier .zip existant et la <xref:System.IO.Compression.ZipArchiveEntry> classe pour inspecter les entrées individuelles dans le fichier compressé.</span><span class="sxs-lookup"><span data-stu-id="bc4b4-112">It uses the <xref:System.IO.Compression.ZipArchive> class to access an existing .zip file, and the <xref:System.IO.Compression.ZipArchiveEntry> class to inspect the individual entries in the compressed file.</span></span> <span data-ttu-id="bc4b4-113">Il utilise une méthode d’extension (<xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A>) pour le <xref:System.IO.Compression.ZipArchiveEntry> objet.</span><span class="sxs-lookup"><span data-stu-id="bc4b4-113">It uses an extension method (<xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A>) for the <xref:System.IO.Compression.ZipArchiveEntry> object.</span></span> <span data-ttu-id="bc4b4-114">La méthode d’extension est disponible dans le <xref:System.IO.Compression.ZipFileExtensions?displayProperty=nameWithType> classe.</span><span class="sxs-lookup"><span data-stu-id="bc4b4-114">The extension method is available in the <xref:System.IO.Compression.ZipFileExtensions?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="bc4b4-115">Pour utiliser le <xref:System.IO.Compression.ZipFileExtensions> (classe), vous devez référencer le `System.IO.Compression.FileSystem` assembly dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="bc4b4-115">To use the <xref:System.IO.Compression.ZipFileExtensions> class, you must reference the `System.IO.Compression.FileSystem` assembly in your project.</span></span>  
  
 [!code-csharp[System.IO.Compression.ZipArchive#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchive/cs/program1.cs#1)]
 [!code-vb[System.IO.Compression.ZipArchive#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchive/vb/program1.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="bc4b4-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="bc4b4-116">Example</span></span>  
 <span data-ttu-id="bc4b4-117">L’exemple suivant utilise la <xref:System.IO.Compression.ZipArchive> classe pour accéder à un fichier .zip existant et ajoute un nouveau fichier au fichier compressé.</span><span class="sxs-lookup"><span data-stu-id="bc4b4-117">The next example uses the <xref:System.IO.Compression.ZipArchive> class to access an existing .zip file, and adds a new file to the compressed file.</span></span> <span data-ttu-id="bc4b4-118">Le nouveau fichier obtient compressé lorsque vous l’ajoutez au fichier .zip existant.</span><span class="sxs-lookup"><span data-stu-id="bc4b4-118">The new file gets compressed when you add it to the existing .zip file.</span></span>  
  
 [!code-csharp[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/cs/program1.cs#1)]
 [!code-vb[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/vb/program1.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="bc4b4-119">Exemple</span><span class="sxs-lookup"><span data-stu-id="bc4b4-119">Example</span></span>  
 <span data-ttu-id="bc4b4-120">Vous pouvez également utiliser le <xref:System.IO.Compression.GZipStream> et <xref:System.IO.Compression.DeflateStream> classes pour compresser et décompresser les données.</span><span class="sxs-lookup"><span data-stu-id="bc4b4-120">You can also use the <xref:System.IO.Compression.GZipStream> and <xref:System.IO.Compression.DeflateStream> classes to compress and decompress data.</span></span> <span data-ttu-id="bc4b4-121">Ils utilisent le même algorithme de compression.</span><span class="sxs-lookup"><span data-stu-id="bc4b4-121">They use the same compression algorithm.</span></span> <span data-ttu-id="bc4b4-122">Compressé <xref:System.IO.Compression.GZipStream> les objets qui sont écrits dans un fichier ayant une extension .gz peuvent être décompressés à l’aide de nombreux outils courants, outre les méthodes fournies par <xref:System.IO.Compression.GZipStream>.</span><span class="sxs-lookup"><span data-stu-id="bc4b4-122">Compressed <xref:System.IO.Compression.GZipStream> objects that are written to a file that has an extension of .gz can be decompressed by using many common tools in addition to the methods provided by <xref:System.IO.Compression.GZipStream>.</span></span> <span data-ttu-id="bc4b4-123">Cet exemple montre comment compresser et décompresser un répertoire de fichiers à l’aide de la <xref:System.IO.Compression.GZipStream> classe.</span><span class="sxs-lookup"><span data-stu-id="bc4b4-123">This example shows how to compress and decompress a directory of files by using the <xref:System.IO.Compression.GZipStream> class.</span></span>  
  
 [!code-csharp[IO.Compression.GZip1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.Compression.GZip1/CS/gziptest.cs#1)]
 [!code-vb[IO.Compression.GZip1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.Compression.GZip1/VB/gziptest.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="bc4b4-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bc4b4-124">See Also</span></span>  
 <xref:System.IO.Compression.ZipArchive>  
 <xref:System.IO.Compression.ZipFile>  
 <xref:System.IO.Compression.ZipArchiveEntry>  
 <xref:System.IO.Compression.DeflateStream>  
 <xref:System.IO.Compression.GZipStream>  
 [<span data-ttu-id="bc4b4-125">Fichier et flux de données E/S</span><span class="sxs-lookup"><span data-stu-id="bc4b4-125">File and Stream I-O</span></span>](../../../docs/standard/io/index.md)
