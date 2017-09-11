---
title: "Comment : déplacer un fichier dans Visual Basic"
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
- files, moving
ms.assetid: 53a7457b-5815-41ad-b37d-28537c1fb77a
caps.latest.revision: 20
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
ms.openlocfilehash: 5a2623ec7e440e8fdf85138cd0b3de9ab18b773c
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-move-a-file-in-visual-basic"></a><span data-ttu-id="45862-102">Comment : déplacer un fichier dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="45862-102">How to: Move a File in Visual Basic</span></span>
<span data-ttu-id="45862-103">Vous pouvez utiliser la méthode `My.Computer.FileSystem.MoveFile` pour déplacer un fichier vers un autre dossier.</span><span class="sxs-lookup"><span data-stu-id="45862-103">The `My.Computer.FileSystem.MoveFile` method can be used to move a file to another folder.</span></span> <span data-ttu-id="45862-104">Si la structure cible n’existe pas, elle est créée.</span><span class="sxs-lookup"><span data-stu-id="45862-104">If the target structure does not exist, it will be created.</span></span>  
  
### <a name="to-move-a-file"></a><span data-ttu-id="45862-105">Pour déplacer un fichier</span><span class="sxs-lookup"><span data-stu-id="45862-105">To move a file</span></span>  
  
-   <span data-ttu-id="45862-106">Utilisez la méthode `MoveFile` pour déplacer le fichier, en spécifiant le nom et l’emplacement du fichier source et du fichier cible.</span><span class="sxs-lookup"><span data-stu-id="45862-106">Use the `MoveFile` method to move the file, specifying the file name and location for both the source file and the target file.</span></span> <span data-ttu-id="45862-107">Dans cet exemple, le fichier nommé `test.txt` est déplacé de `TestDir1` vers `TestDir2`.</span><span class="sxs-lookup"><span data-stu-id="45862-107">This example moves the file named `test.txt` from `TestDir1` to `TestDir2`.</span></span> <span data-ttu-id="45862-108">Notez que le nom du fichier cible est spécifié même s’il est identique à celui du fichier source.</span><span class="sxs-lookup"><span data-stu-id="45862-108">Note that the target file name is specified even though it is the same as the source file name.</span></span>  
  
     <span data-ttu-id="45862-109">[!code-vb[VbVbcnMyFileSystem#24](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-move-a-file_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="45862-109">[!code-vb[VbVbcnMyFileSystem#24](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-move-a-file_1.vb)]</span></span>  
  
### <a name="to-move-a-file-and-rename-it"></a><span data-ttu-id="45862-110">Pour déplacer et renommer un fichier</span><span class="sxs-lookup"><span data-stu-id="45862-110">To move a file and rename it</span></span>  
  
-   <span data-ttu-id="45862-111">Utilisez la méthode `MoveFile` pour déplacer le fichier, en spécifiant le nom et l’emplacement du fichier source, l’emplacement cible et le nouveau nom du fichier à l’emplacement cible.</span><span class="sxs-lookup"><span data-stu-id="45862-111">Use the `MoveFile` method to move the file, specifying the source file name and location, the target location, and the new name at the target location.</span></span> <span data-ttu-id="45862-112">Dans cet exemple, le fichier nommé `test.txt` est déplacé de `TestDir1` vers `TestDir2` , puis renommé en `nexttest.txt`.</span><span class="sxs-lookup"><span data-stu-id="45862-112">This example moves the file named `test.txt` from `TestDir1` to `TestDir2` and renames it `nexttest.txt`.</span></span>  
  
     <span data-ttu-id="45862-113">[!code-vb[VbVbcnMyFileSystem#25](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-move-a-file_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="45862-113">[!code-vb[VbVbcnMyFileSystem#25](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-move-a-file_2.vb)]</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="45862-114">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="45862-114">Robust Programming</span></span>  
 <span data-ttu-id="45862-115">Les conditions ci-dessous peuvent générer une exception.</span><span class="sxs-lookup"><span data-stu-id="45862-115">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="45862-116">Le chemin n’est pas valide pour l’une des raisons suivantes : il s’agit d’une chaîne de longueur nulle, il ne contient que des espaces blancs, il contient des caractères non valides ou il s’agit d’un chemin d’appareil (il commence par \\\\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="45862-116">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="45862-117">Le chemin n’est pas valide, car il a la valeur `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="45862-117">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="45862-118">`destinationFileName` est `Nothing` ou une chaîne vide (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="45862-118">`destinationFileName` is `Nothing` or an empty string (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="45862-119">Le fichier source n’est pas valide ou n’existe pas (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="45862-119">The source file is not valid or does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
-   <span data-ttu-id="45862-120">Le chemin combiné pointe vers un répertoire existant, le fichier de destination existe et `overwrite` a la valeur `False`, un fichier du répertoire cible portant le même nom est actuellement utilisé, ou l’utilisateur ne dispose pas des autorisations suffisantes pour accéder au fichier (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="45862-120">The combined path points to an existing directory, the destination file exists and `overwrite` is set to `False`, a file in the target directory with the same name is in use, or the user does not have sufficient permissions to access the file (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="45862-121">Un nom de fichier ou de répertoire du chemin contient un signe deux-points (:) ou n'a pas un format correct (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="45862-121">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="45862-122">`showUI` a la valeur `True`, `onUserCancel` a la valeur `ThrowException`et l’utilisateur a annulé l’opération ou une erreur d’E/S non spécifiée s’est produite (<xref:System.OperationCanceledException>).</span><span class="sxs-lookup"><span data-stu-id="45862-122">`showUI` is set to `True`, `onUserCancel` is set to `ThrowException`, and either the user has cancelled the operation or an unspecified I/O error occurs (<xref:System.OperationCanceledException>).</span></span>  
  
-   <span data-ttu-id="45862-123">Le chemin dépasse la longueur maximale définie par le système (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="45862-123">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="45862-124">L'utilisateur n'a pas les autorisations nécessaires pour afficher le chemin (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="45862-124">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="45862-125">L’utilisateur ne dispose pas de l’autorisation nécessaire (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="45862-125">The user does not have required permission (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45862-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="45862-126">See Also</span></span>  
 <span data-ttu-id="45862-127"><xref:Microsoft.VisualBasic.FileIO.FileSystem.MoveFile%2A></span><span class="sxs-lookup"><span data-stu-id="45862-127"><xref:Microsoft.VisualBasic.FileIO.FileSystem.MoveFile%2A></span></span>   
 <span data-ttu-id="45862-128">[Guide pratique pour renommer un fichier](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md) </span><span class="sxs-lookup"><span data-stu-id="45862-128">[How to: Rename a File](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md) </span></span>  
 <span data-ttu-id="45862-129">[Guide pratique pour créer une copie d’un fichier dans un autre répertoire](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-a-different-directory.md) </span><span class="sxs-lookup"><span data-stu-id="45862-129">[How to: Create a Copy of a File in a Different Directory](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-a-different-directory.md) </span></span>  
 [<span data-ttu-id="45862-130">Guide pratique pour analyser des chemins</span><span class="sxs-lookup"><span data-stu-id="45862-130">How to: Parse File Paths</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)

