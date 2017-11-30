---
title: "Comment : lire et écrire dans un fichier de données créé récemment"
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
- streams, reading and writing data
- BinaryReader class, examples
- I/O [.NET Framework], reading data
- I/O [.NET Framework], writing data
- BinaryWriter class, examples
ms.assetid: e209d949-31e8-44ea-8e38-87f9093f3093
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b547f2c85495a497e5fc384f9a2ea44de7bf861c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-read-and-write-to-a-newly-created-data-file"></a><span data-ttu-id="fe92f-102">Comment : lire et écrire dans un fichier de données créé récemment</span><span class="sxs-lookup"><span data-stu-id="fe92f-102">How to: Read and Write to a Newly Created Data File</span></span>
<span data-ttu-id="fe92f-103">Le <xref:System.IO.BinaryWriter> et <xref:System.IO.BinaryReader?displayProperty=nameWithType> classes sont utilisées pour écrire et lire des données plutôt que des chaînes de caractères.</span><span class="sxs-lookup"><span data-stu-id="fe92f-103">The <xref:System.IO.BinaryWriter> and <xref:System.IO.BinaryReader?displayProperty=nameWithType> classes are used for writing and reading data rather than character strings.</span></span> <span data-ttu-id="fe92f-104">L’exemple suivant montre comment écrire et lire des données à partir d’un flux de fichier vide nommé `Test.data`.</span><span class="sxs-lookup"><span data-stu-id="fe92f-104">The following example demonstrates how to write data to, and read data from, a new, empty file stream called `Test.data`.</span></span> <span data-ttu-id="fe92f-105">Après avoir créé le fichier de données dans le répertoire actif, associé <xref:System.IO.BinaryWriter> et <xref:System.IO.BinaryReader> objets sont créés et le <xref:System.IO.BinaryWriter> objet est utilisé pour écrire les entiers de 0 à 10 pour `Test.data`, qui laisse le pointeur de fichier à la fin de la fichier.</span><span class="sxs-lookup"><span data-stu-id="fe92f-105">After creating the data file in the current directory, the associated <xref:System.IO.BinaryWriter> and <xref:System.IO.BinaryReader> objects are created, and the <xref:System.IO.BinaryWriter> object is used to write the integers 0 through 10 to `Test.data`, which leaves the file pointer at the end of the file.</span></span> <span data-ttu-id="fe92f-106">Après avoir défini le pointeur de fichier à l’origine, le <xref:System.IO.BinaryReader> objet lit le contenu spécifié.</span><span class="sxs-lookup"><span data-stu-id="fe92f-106">After setting the file pointer back to the origin, the <xref:System.IO.BinaryReader> object reads out the specified content.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fe92f-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="fe92f-107">Example</span></span>  
 [!code-cpp[System.IO.BinaryReaderWriter#7](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/CPP/source6.cpp#7)]
 [!code-csharp[System.IO.BinaryReaderWriter#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/CS/source6.cs#7)]
 [!code-vb[System.IO.BinaryReaderWriter#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/VB/source6.vb#7)]  
  
## <a name="robust-programming"></a><span data-ttu-id="fe92f-108">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="fe92f-108">Robust Programming</span></span>  
 <span data-ttu-id="fe92f-109">Si `Test.data` existe déjà dans le répertoire actif, un <xref:System.IO.IOException> exception est levée.</span><span class="sxs-lookup"><span data-stu-id="fe92f-109">If `Test.data` already exists in the current directory, an <xref:System.IO.IOException> exception is thrown.</span></span> <span data-ttu-id="fe92f-110">Utilisez l’option de mode de fichier <xref:System.IO.FileMode.Create?displayProperty=nameWithType> lors de l’initialisation du flux de fichier pour créer un nouveau fichier sans lever d’exception.</span><span class="sxs-lookup"><span data-stu-id="fe92f-110">Use the file mode option <xref:System.IO.FileMode.Create?displayProperty=nameWithType> when you initialize the file stream to always create a new file without throwing an  exception.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe92f-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fe92f-111">See Also</span></span>  
 <xref:System.IO.BinaryReader>  
 <xref:System.IO.BinaryWriter>  
 <xref:System.IO.FileStream>  
 <xref:System.IO.FileStream.Seek%2A?displayProperty=nameWithType>  
 <xref:System.IO.SeekOrigin>  
 [<span data-ttu-id="fe92f-112">Guide pratique pour énumérer des répertoires et des fichiers</span><span class="sxs-lookup"><span data-stu-id="fe92f-112">How to: Enumerate Directories and Files</span></span>](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
 [<span data-ttu-id="fe92f-113">Comment : ouvrir un fichier journal et y ajouter des éléments</span><span class="sxs-lookup"><span data-stu-id="fe92f-113">How to: Open and Append to a Log File</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
 [<span data-ttu-id="fe92f-114">Comment : lire du texte dans un fichier</span><span class="sxs-lookup"><span data-stu-id="fe92f-114">How to: Read Text from a File</span></span>](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
 [<span data-ttu-id="fe92f-115">Comment : écrire du texte dans un fichier</span><span class="sxs-lookup"><span data-stu-id="fe92f-115">How to: Write Text to a File</span></span>](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
 [<span data-ttu-id="fe92f-116">Comment : lire les caractères d’une chaîne</span><span class="sxs-lookup"><span data-stu-id="fe92f-116">How to: Read Characters from a String</span></span>](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
 [<span data-ttu-id="fe92f-117">Comment : écrire des caractères dans une chaîne</span><span class="sxs-lookup"><span data-stu-id="fe92f-117">How to: Write Characters to a String</span></span>](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
 [<span data-ttu-id="fe92f-118">Fichier et flux de données E/S</span><span class="sxs-lookup"><span data-stu-id="fe92f-118">File and Stream I-O</span></span>](../../../docs/standard/io/index.md)
