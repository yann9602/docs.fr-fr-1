---
title: "Comment : analyser des chemins d'accès dans Visual Basic"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- file names, parsing [Visual Basic]
- parsing, file paths [Visual Basic]
ms.assetid: c1bd99c9-8160-456a-b5ab-60a49139b923
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 6327d661c6f1fe7647cc64b56d7f72f1f3455467
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-parse-file-paths-in-visual-basic"></a><span data-ttu-id="7e2a7-102">Comment : analyser des chemins d'accès dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7e2a7-102">How to: Parse File Paths in Visual Basic</span></span>
<span data-ttu-id="7e2a7-103">L’objet <xref:Microsoft.VisualBasic.FileIO.FileSystem> fournit plusieurs méthodes qui facilitent l’analyse des chemins de fichier.</span><span class="sxs-lookup"><span data-stu-id="7e2a7-103">The <xref:Microsoft.VisualBasic.FileIO.FileSystem> object offers a number of useful methods when parsing file paths.</span></span>  
  
-   <span data-ttu-id="7e2a7-104">La méthode <xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A> combine deux chemins et affiche un chemin combiné au format correct.</span><span class="sxs-lookup"><span data-stu-id="7e2a7-104">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A> method takes two paths and returns a properly formatted combined path.</span></span>  
  
-   <span data-ttu-id="7e2a7-105">La méthode <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetParentPath%2A> retourne le chemin absolu du parent du chemin fourni.</span><span class="sxs-lookup"><span data-stu-id="7e2a7-105">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetParentPath%2A> method returns the absolute path of the parent of the provided path.</span></span>  
  
-   <span data-ttu-id="7e2a7-106">La méthode <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> retourne un objet <xref:System.IO.FileInfo> qui peut être interrogé pour déterminer les propriétés du fichier, telles que son nom et son chemin.</span><span class="sxs-lookup"><span data-stu-id="7e2a7-106">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> method returns a <xref:System.IO.FileInfo> object that can be queried to determine the file's properties, such as its name and path.</span></span>  
  
 <span data-ttu-id="7e2a7-107">Ne vous basez pas sur l’extension de nom de fichier pour déterminer le contenu d’un fichier.</span><span class="sxs-lookup"><span data-stu-id="7e2a7-107">Do not make decisions about the contents of the file based on the file name extension.</span></span> <span data-ttu-id="7e2a7-108">Par exemple, le fichier Form1.vb peut ne pas être un fichier source Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="7e2a7-108">For example, the file Form1.vb may not be a Visual Basic source file.</span></span>  
  
### <a name="to-determine-a-files-name-and-path"></a><span data-ttu-id="7e2a7-109">Pour déterminer le nom et le chemin d’un fichier</span><span class="sxs-lookup"><span data-stu-id="7e2a7-109">To determine a file's name and path</span></span>  
  
-   <span data-ttu-id="7e2a7-110">Utilisez les propriétés <xref:System.IO.FileInfo.DirectoryName%2A> et <xref:System.IO.FileInfo.Name%2A> de l’objet <xref:System.IO.FileInfo> pour déterminer le nom et le chemin d’un fichier.</span><span class="sxs-lookup"><span data-stu-id="7e2a7-110">Use the <xref:System.IO.FileInfo.DirectoryName%2A> and <xref:System.IO.FileInfo.Name%2A> properties of the <xref:System.IO.FileInfo> object to determine a file's name and path.</span></span> <span data-ttu-id="7e2a7-111">Cet exemple détermine le nom et le chemin d’un fichier, puis les affiche.</span><span class="sxs-lookup"><span data-stu-id="7e2a7-111">This example determines the name and path and displays them.</span></span>  
  
     <span data-ttu-id="7e2a7-112">[!code-vb[VbVbcnMyFileSystem#54](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-parse-file-paths_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="7e2a7-112">[!code-vb[VbVbcnMyFileSystem#54](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-parse-file-paths_1.vb)]</span></span>  
  
### <a name="to-combine-a-files-name-and-directory-to-create-the-full-path"></a><span data-ttu-id="7e2a7-113">Pour combiner le nom et le répertoire d’un fichier en un chemin complet</span><span class="sxs-lookup"><span data-stu-id="7e2a7-113">To combine a file's name and directory to create the full path</span></span>  
  
-   <span data-ttu-id="7e2a7-114">Utilisez la méthode `CombinePath` , en spécifiant le répertoire et le nom du fichier.</span><span class="sxs-lookup"><span data-stu-id="7e2a7-114">Use the `CombinePath` method, supplying the directory and name.</span></span> <span data-ttu-id="7e2a7-115">Cet exemple combine les chaînes `folderPath` et `fileName` créées dans l’exemple précédent, puis affiche le résultat.</span><span class="sxs-lookup"><span data-stu-id="7e2a7-115">This example takes the strings `folderPath` and `fileName` created in the previous example, combines them, and displays the result.</span></span>  
  
     <span data-ttu-id="7e2a7-116">[!code-vb[VbVbcnMyFileSystem#55](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-parse-file-paths_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="7e2a7-116">[!code-vb[VbVbcnMyFileSystem#55](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-parse-file-paths_2.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e2a7-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7e2a7-117">See Also</span></span>  
 <span data-ttu-id="7e2a7-118"><xref:Microsoft.VisualBasic.FileIO.FileSystem></span><span class="sxs-lookup"><span data-stu-id="7e2a7-118"><xref:Microsoft.VisualBasic.FileIO.FileSystem></span></span>   
 <span data-ttu-id="7e2a7-119"><xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A></span><span class="sxs-lookup"><span data-stu-id="7e2a7-119"><xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A></span></span>   
 <span data-ttu-id="7e2a7-120"><xref:System.IO.FileInfo></span><span class="sxs-lookup"><span data-stu-id="7e2a7-120"><xref:System.IO.FileInfo></span></span>   
 <span data-ttu-id="7e2a7-121"><xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A></span><span class="sxs-lookup"><span data-stu-id="7e2a7-121"><xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A></span></span>   
 [<span data-ttu-id="7e2a7-122">Guide pratique pour placer la collection de fichiers dans un répertoire</span><span class="sxs-lookup"><span data-stu-id="7e2a7-122">How to: Get the Collection of Files in a Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)

