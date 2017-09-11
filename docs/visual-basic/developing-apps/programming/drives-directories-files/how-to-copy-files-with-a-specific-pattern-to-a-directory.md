---
title: "Comment : copier des fichiers avec un modèle spécifique dans un répertoire dans Visual Basic"
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
- My.Computer.FileSystem.CopyFile method, copying files [Visual Basic]
- files, copying
- CopyFile method, copying files in Visual Basic
- I/O [Visual Basic], copying files
ms.assetid: f205d2ad-bbe5-4d55-8a40-acda21aa82dd
caps.latest.revision: 15
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
ms.openlocfilehash: 812fd59769da386f8d0b81eb80a4cd93c9764534
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-copy-files-with-a-specific-pattern-to-a-directory-in-visual-basic"></a><span data-ttu-id="b3660-102">Comment : copier des fichiers avec un modèle spécifique dans un répertoire dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b3660-102">How to: Copy Files with a Specific Pattern to a Directory in Visual Basic</span></span>
<span data-ttu-id="b3660-103">La méthode <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A> retourne une collection en lecture seule de chaînes représentant les noms de chemin des fichiers.</span><span class="sxs-lookup"><span data-stu-id="b3660-103">The <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A> method returns a read-only collection of strings representing the path names for the files.</span></span> <span data-ttu-id="b3660-104">Vous pouvez utiliser le paramètre `wildCards` pour indiquer un modèle spécifique.</span><span class="sxs-lookup"><span data-stu-id="b3660-104">You can use the `wildCards` parameter to specify a specific pattern.</span></span>  
  
 <span data-ttu-id="b3660-105">Une collection vide est retournée si aucun fichier correspondant n’est trouvé.</span><span class="sxs-lookup"><span data-stu-id="b3660-105">An empty collection is returned if no matching files are found.</span></span>  
  
 <span data-ttu-id="b3660-106">Vous pouvez utiliser la méthode <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A> pour copier les fichiers dans un répertoire.</span><span class="sxs-lookup"><span data-stu-id="b3660-106">You can use the <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A> method to copy the files to a directory.</span></span>  
  
### <a name="to-copy-files-with-a-specific-pattern-to-a-directory"></a><span data-ttu-id="b3660-107">Pour copier des fichiers avec un modèle spécifique dans un répertoire</span><span class="sxs-lookup"><span data-stu-id="b3660-107">To copy files with a specific pattern to a directory</span></span>  
  
1.  <span data-ttu-id="b3660-108">Utilisez la méthode `GetFiles` pour retourner la liste des fichiers.</span><span class="sxs-lookup"><span data-stu-id="b3660-108">Use the `GetFiles` method to return the list of files.</span></span> <span data-ttu-id="b3660-109">Cet exemple retourne tous les fichiers .rtf qui se trouvent dans le répertoire spécifié.</span><span class="sxs-lookup"><span data-stu-id="b3660-109">This example returns all .rtf files in the specified directory.</span></span>  
  
     <span data-ttu-id="b3660-110">[!code-vb[VbFileIOMisc#36](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-copy-files-with-a-specific-pattern-to-a-directory_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="b3660-110">[!code-vb[VbFileIOMisc#36](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-copy-files-with-a-specific-pattern-to-a-directory_1.vb)]</span></span>  
  
2.  <span data-ttu-id="b3660-111">Utilisez la méthode `CopyFile` pour copier les fichiers.</span><span class="sxs-lookup"><span data-stu-id="b3660-111">Use the `CopyFile` method to copy the files.</span></span> <span data-ttu-id="b3660-112">Cet exemple copie les fichiers dans le répertoire nommé `testdirectory`.</span><span class="sxs-lookup"><span data-stu-id="b3660-112">This example copies the files to the directory named `testdirectory`.</span></span>  
  
     <span data-ttu-id="b3660-113">[!code-vb[VbVbcnMyFileSystem#88](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-copy-files-with-a-specific-pattern-to-a-directory_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="b3660-113">[!code-vb[VbVbcnMyFileSystem#88](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-copy-files-with-a-specific-pattern-to-a-directory_2.vb)]</span></span>  
  
3.  <span data-ttu-id="b3660-114">Terminez l’instruction `For` par une instruction `Next` .</span><span class="sxs-lookup"><span data-stu-id="b3660-114">Close the `For` statement with a `Next` statement.</span></span>  
  
     <span data-ttu-id="b3660-115">[!code-vb[VbVbcnMyFileSystem#89](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-copy-files-with-a-specific-pattern-to-a-directory_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="b3660-115">[!code-vb[VbVbcnMyFileSystem#89](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-copy-files-with-a-specific-pattern-to-a-directory_3.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="b3660-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="b3660-116">Example</span></span>  
 <span data-ttu-id="b3660-117">L’exemple suivant, qui présente les extraits de code ci-dessus dans leur intégralité, copie tous les fichiers .rtf du répertoire spécifié dans le répertoire nommé `testdirectory`.</span><span class="sxs-lookup"><span data-stu-id="b3660-117">The following example, which presents the above snippets in complete form, copies all .rtf files in the specified directory to the directory named `testdirectory`.</span></span>  
  
 <span data-ttu-id="b3660-118">[!code-vb[VbFileIOMisc#37](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-copy-files-with-a-specific-pattern-to-a-directory_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="b3660-118">[!code-vb[VbFileIOMisc#37](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-copy-files-with-a-specific-pattern-to-a-directory_4.vb)]</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="b3660-119">Sécurité .NET Framework</span><span class="sxs-lookup"><span data-stu-id="b3660-119">.NET Framework Security</span></span>  
 <span data-ttu-id="b3660-120">Les conditions ci-dessous peuvent générer une exception.</span><span class="sxs-lookup"><span data-stu-id="b3660-120">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="b3660-121">Le chemin n’est pas valide pour l’une des raisons suivantes : il s’agit d’une chaîne de longueur nulle, il ne contient que des espaces blancs, il contient des caractères non valides ou il s’agit d’un chemin d’appareil (il commence par \\\\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="b3660-121">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="b3660-122">Le chemin n’est pas valide, car il a la valeur `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="b3660-122">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="b3660-123">Le répertoire n’existe pas (<xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="b3660-123">The directory does not exist (<xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
-   <span data-ttu-id="b3660-124">Le répertoire pointe vers un fichier existant (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="b3660-124">The directory points to an existing file (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="b3660-125">Le chemin dépasse la longueur maximale définie par le système (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="b3660-125">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="b3660-126">Un nom de fichier ou de répertoire du chemin contient un signe deux-points (:) ou n'a pas un format correct (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="b3660-126">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="b3660-127">L'utilisateur n'a pas les autorisations nécessaires pour afficher le chemin (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="b3660-127">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span> <span data-ttu-id="b3660-128">L'utilisateur ne dispose pas des autorisations nécessaires (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="b3660-128">The user lacks necessary permissions (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3660-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b3660-129">See Also</span></span>  
 <span data-ttu-id="b3660-130"><xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A></span><span class="sxs-lookup"><span data-stu-id="b3660-130"><xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A></span></span>   
 <span data-ttu-id="b3660-131"><xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A></span><span class="sxs-lookup"><span data-stu-id="b3660-131"><xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A></span></span>   
 <span data-ttu-id="b3660-132">[Guide pratique pour rechercher des sous-répertoires avec un modèle spécifique](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md) </span><span class="sxs-lookup"><span data-stu-id="b3660-132">[How to: Find Subdirectories with a Specific Pattern](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md) </span></span>  
 <span data-ttu-id="b3660-133">[Dépannage : lecture et écriture dans des fichiers texte](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md) </span><span class="sxs-lookup"><span data-stu-id="b3660-133">[Troubleshooting: Reading from and Writing to Text Files](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md) </span></span>  
 [<span data-ttu-id="b3660-134">Guide pratique pour placer la collection de fichiers dans un répertoire</span><span class="sxs-lookup"><span data-stu-id="b3660-134">How to: Get the Collection of Files in a Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)

