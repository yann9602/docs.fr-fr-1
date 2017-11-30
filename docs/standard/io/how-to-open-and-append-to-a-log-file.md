---
title: "Comment : ouvrir un fichier journal et y ajouter des éléments"
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
- log files, opening
- streams, opening and appending to log file
- log files, appending to
- I/O [.NET Framework], log files
ms.assetid: 74423362-1721-49cb-aa0a-e04005f72a06
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 60c31339231405a1cbbb98dae37d36ad3c3709c1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-open-and-append-to-a-log-file"></a><span data-ttu-id="8b828-102">Comment : ouvrir un fichier journal et y ajouter des éléments</span><span class="sxs-lookup"><span data-stu-id="8b828-102">How to: Open and Append to a Log File</span></span>
<span data-ttu-id="8b828-103"><xref:System.IO.StreamWriter>et <xref:System.IO.StreamReader> écrire des caractères à et lire des caractères à partir de flux.</span><span class="sxs-lookup"><span data-stu-id="8b828-103"><xref:System.IO.StreamWriter> and <xref:System.IO.StreamReader> write characters to and read characters from streams.</span></span> <span data-ttu-id="8b828-104">Le code suivant exemple ouvre le `log.txt` du fichier d’entrée, ou crée le fichier s’il n’existe pas déjà et ajoute les informations à la fin du fichier.</span><span class="sxs-lookup"><span data-stu-id="8b828-104">The following code example opens the `log.txt` file for input, or creates the file if it does not already exist, and appends information to the end of the file.</span></span> <span data-ttu-id="8b828-105">Le contenu du fichier est ensuite écrites vers la sortie standard pour l’affichage.</span><span class="sxs-lookup"><span data-stu-id="8b828-105">The contents of the file are then written to standard output for display.</span></span> <span data-ttu-id="8b828-106">Comme alternative à cet exemple, les informations peut être stockées en tant que chaîne unique ou tableau de chaînes et le <xref:System.IO.File.WriteAllText%2A> ou <xref:System.IO.File.WriteAllLines%2A> méthode peut servir à obtenir la même fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="8b828-106">As an alternative to this example, the information could be stored as a single string or string array, and the <xref:System.IO.File.WriteAllText%2A> or <xref:System.IO.File.WriteAllLines%2A> method could be used to achieve the same functionality.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8b828-107">Les utilisateurs de Visual Basic peuvent choisir d’utiliser les méthodes et les propriétés fournies par le <xref:Microsoft.VisualBasic.Logging.Log> classe ou <xref:Microsoft.VisualBasic.FileIO.FileSystem> classe pour la création ou l’écriture dans des fichiers journaux.</span><span class="sxs-lookup"><span data-stu-id="8b828-107">Visual Basic users may choose to use the methods and properties provided by the <xref:Microsoft.VisualBasic.Logging.Log> class or <xref:Microsoft.VisualBasic.FileIO.FileSystem> class for creating or writing to log files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8b828-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="8b828-108">Example</span></span>  
 [!code-csharp[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source2.cs#2)]
 [!code-vb[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="8b828-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8b828-109">See Also</span></span>  
 <xref:System.IO.StreamWriter>  
 <xref:System.IO.StreamReader>  
 <xref:System.IO.File.AppendText%2A?displayProperty=nameWithType>  
 <xref:System.IO.File.OpenText%2A?displayProperty=nameWithType>  
 <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="8b828-110">Guide pratique pour énumérer des répertoires et des fichiers</span><span class="sxs-lookup"><span data-stu-id="8b828-110">How to: Enumerate Directories and Files</span></span>](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
 [<span data-ttu-id="8b828-111">Comment : lire et écrire dans un fichier de données créé récemment</span><span class="sxs-lookup"><span data-stu-id="8b828-111">How to: Read and Write to a Newly Created Data File</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
 [<span data-ttu-id="8b828-112">Comment : lire du texte dans un fichier</span><span class="sxs-lookup"><span data-stu-id="8b828-112">How to: Read Text from a File</span></span>](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
 [<span data-ttu-id="8b828-113">Comment : écrire du texte dans un fichier</span><span class="sxs-lookup"><span data-stu-id="8b828-113">How to: Write Text to a File</span></span>](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
 [<span data-ttu-id="8b828-114">Comment : lire les caractères d’une chaîne</span><span class="sxs-lookup"><span data-stu-id="8b828-114">How to: Read Characters from a String</span></span>](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
 [<span data-ttu-id="8b828-115">Comment : écrire des caractères dans une chaîne</span><span class="sxs-lookup"><span data-stu-id="8b828-115">How to: Write Characters to a String</span></span>](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
 [<span data-ttu-id="8b828-116">Fichier et flux de données E/S</span><span class="sxs-lookup"><span data-stu-id="8b828-116">File and Stream I-O</span></span>](../../../docs/standard/io/index.md)
