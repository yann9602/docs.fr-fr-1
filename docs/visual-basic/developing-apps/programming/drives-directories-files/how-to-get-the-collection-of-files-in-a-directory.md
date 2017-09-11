---
title: "Guide pratique pour obtenir la collection de fichiers dans un répertoire en Visual Basic"
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
- folders, working with
- files, accessing
ms.assetid: 6c8ba7e8-dd37-4853-92bf-762b67c98160
caps.latest.revision: 23
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 023fb90622b45fe0067cd146f62bc3edb326b5ef
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-get-the-collection-of-files-in-a-directory-in-visual-basic"></a><span data-ttu-id="f51b2-102">Guide pratique pour obtenir la collection de fichiers dans un répertoire en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f51b2-102">How to: Get the Collection of Files in a Directory in Visual Basic</span></span>
<span data-ttu-id="f51b2-103">Les surcharges de la méthode <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=fullName> retournent une collection en lecture seule de chaînes représentant les noms des fichiers contenus dans un répertoire :</span><span class="sxs-lookup"><span data-stu-id="f51b2-103">The overloads of the <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=fullName> method return a read-only collection of strings representing the names of the files within a directory:</span></span>  
  
-   <span data-ttu-id="f51b2-104">Utilisez la surcharge <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%28System.String%29> pour effectuer une recherche de fichier simple dans un répertoire spécifié, sans rechercher dans les sous-répertoires.</span><span class="sxs-lookup"><span data-stu-id="f51b2-104">Use the <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%28System.String%29> overload for a simple file search in a specified directory, without searching subdirectories.</span></span>  
  
-   <span data-ttu-id="f51b2-105">Utilisez la surcharge <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles(System.String,Microsoft.VisualBasic.FileIO.SearchOption,System.String[])> pour spécifier des options supplémentaires pour votre recherche.</span><span class="sxs-lookup"><span data-stu-id="f51b2-105">Use the <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles(System.String,Microsoft.VisualBasic.FileIO.SearchOption,System.String[])> overload to specify additional options for your search.</span></span> <span data-ttu-id="f51b2-106">Vous pouvez utiliser le paramètre `wildCards` pour spécifier un modèle de recherche.</span><span class="sxs-lookup"><span data-stu-id="f51b2-106">You can use the `wildCards` parameter to specify a search pattern.</span></span> <span data-ttu-id="f51b2-107">Pour inclure des sous-répertoires dans la recherche, affectez la valeur `searchType` au paramètre <xref:Microsoft.VisualBasic.FileIO.SearchOption.SearchAllSubDirectories?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="f51b2-107">To include subdirectories in the search, set the `searchType` parameter to <xref:Microsoft.VisualBasic.FileIO.SearchOption.SearchAllSubDirectories?displayProperty=fullName>.</span></span>  
  
 <span data-ttu-id="f51b2-108">Une collection vide est retournée si aucun fichier correspondant au modèle spécifié n'est détecté.</span><span class="sxs-lookup"><span data-stu-id="f51b2-108">An empty collection is returned if no files matching the specified pattern are found.</span></span>  
  
### <a name="to-list-files-in-a-directory"></a><span data-ttu-id="f51b2-109">Pour énumérer les fichiers contenus dans un répertoire</span><span class="sxs-lookup"><span data-stu-id="f51b2-109">To list files in a directory</span></span>  
  
-   <span data-ttu-id="f51b2-110">Utilisez l'une des surcharges de méthode <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=fullName>, en fournissant le nom et le chemin d'accès au répertoire dans lequel effectuer la recherche dans le paramètre `directory`.</span><span class="sxs-lookup"><span data-stu-id="f51b2-110">Use one of the <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=fullName> method overloads, supplying the name and path of the directory to search in the `directory` parameter.</span></span> <span data-ttu-id="f51b2-111">L’exemple suivant retourne tous les fichiers contenus dans le répertoire et les ajoute à `ListBox1`.</span><span class="sxs-lookup"><span data-stu-id="f51b2-111">The following example returns all files in the directory and adds them to `ListBox1`.</span></span>  
  
     <span data-ttu-id="f51b2-112">[!code-vb[VbVbcnMyFileSystem#32](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-get-the-collection-of-files-in-a-directory_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="f51b2-112">[!code-vb[VbVbcnMyFileSystem#32](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-get-the-collection-of-files-in-a-directory_1.vb)]</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="f51b2-113">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="f51b2-113">Robust Programming</span></span>  
 <span data-ttu-id="f51b2-114">Les conditions ci-dessous peuvent générer une exception.</span><span class="sxs-lookup"><span data-stu-id="f51b2-114">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="f51b2-115">Le chemin n’est pas valide pour l’une des raisons suivantes : il s’agit d’une chaîne de longueur nulle, il ne contient que des espaces blancs, il contient des caractères non valides ou il s’agit d’un chemin d’appareil (il commence par \\\\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="f51b2-115">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="f51b2-116">Le chemin d'accès n'est pas valide, car il a la valeur `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="f51b2-116">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="f51b2-117">`directory` n'existe pas (<xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="f51b2-117">`directory` does not exist (<xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
-   <span data-ttu-id="f51b2-118">`directory` pointe vers un fichier existant (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="f51b2-118">`directory` points to an existing file (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="f51b2-119">Le chemin d'accès dépasse la longueur maximale définie par le système (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="f51b2-119">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="f51b2-120">Un nom de fichier ou de répertoire du chemin contient un signe deux-points (:) ou n'a pas un format correct (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="f51b2-120">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="f51b2-121">L'utilisateur n'a pas les autorisations nécessaires pour afficher le chemin (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="f51b2-121">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="f51b2-122">L'utilisateur ne dispose pas des autorisations nécessaires (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="f51b2-122">The user lacks necessary permissions (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f51b2-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f51b2-123">See Also</span></span>  
 <span data-ttu-id="f51b2-124"><xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A></span><span class="sxs-lookup"><span data-stu-id="f51b2-124"><xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A></span></span>   
 <span data-ttu-id="f51b2-125">[Guide pratique pour rechercher des fichiers avec un modèle spécifique](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-files-with-a-specific-pattern.md) </span><span class="sxs-lookup"><span data-stu-id="f51b2-125">[How to: Find Files with a Specific Pattern](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-files-with-a-specific-pattern.md) </span></span>  
 [<span data-ttu-id="f51b2-126">Guide pratique pour rechercher des sous-répertoires avec un modèle spécifique</span><span class="sxs-lookup"><span data-stu-id="f51b2-126">How to: Find Subdirectories with a Specific Pattern</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)

