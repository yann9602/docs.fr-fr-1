---
title: "Guide pratique pour créer une copie d'un fichier dans le même répertoire en Visual Basic"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- File.Copy
dev_langs:
- VB
helpviewer_keywords:
- My.Computer.FileSystem.CopyFile method, copying files [Visual Basic]
- files, copying
- CopyFile method, copying files in Visual Basic
- I/O [Visual Basic], copying files
ms.assetid: b2fdda86-e666-42c2-9706-9527e9fa68ff
caps.latest.revision: 21
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
ms.openlocfilehash: 7e15b85a72c9b2504551174f5b104bdbb01cf3f3
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-create-a-copy-of-a-file-in-the-same-directory-in-visual-basic"></a><span data-ttu-id="3caae-102">Guide pratique pour créer une copie d'un fichier dans le même répertoire en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3caae-102">How to: Create a Copy of a File in the Same Directory in Visual Basic</span></span>
<span data-ttu-id="3caae-103">Utilisez la méthode `My.Computer.FileSystem.CopyFile` pour copier des fichiers.</span><span class="sxs-lookup"><span data-stu-id="3caae-103">Use the `My.Computer.FileSystem.CopyFile` method to copy files.</span></span> <span data-ttu-id="3caae-104">Les paramètres permettent de remplacer les fichiers existants, de renommer le fichier, d’afficher la progression de l’opération et d’autoriser l’utilisateur à annuler l’opération.</span><span class="sxs-lookup"><span data-stu-id="3caae-104">The parameters allow you to overwrite existing files, rename the file, show the progress of the operation, and allow the user to cancel the operation.</span></span>  
  
### <a name="to-create-a-copy-of-a-file-in-the-same-folder"></a><span data-ttu-id="3caae-105">Pour créer une copie d’un fichier dans le même dossier</span><span class="sxs-lookup"><span data-stu-id="3caae-105">To create a copy of a file in the same folder</span></span>  
  
-   <span data-ttu-id="3caae-106">Utilisez la méthode `CopyFile`, en fournissant le fichier cible et l’emplacement.</span><span class="sxs-lookup"><span data-stu-id="3caae-106">Use the `CopyFile` method, supplying the target file and the location.</span></span> <span data-ttu-id="3caae-107">L’exemple suivant crée une copie de `test.txt` nommée `test2.txt`.</span><span class="sxs-lookup"><span data-stu-id="3caae-107">The following example creates a copy of `test.txt` called `test2.txt`.</span></span>  
  
     <span data-ttu-id="3caae-108">[!code-vb[VbVbcnMyFileSystem#51](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-create-a-copy-of-a-file-in-the-same-directory_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="3caae-108">[!code-vb[VbVbcnMyFileSystem#51](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-create-a-copy-of-a-file-in-the-same-directory_1.vb)]</span></span>  
  
### <a name="to-create-a-copy-of-a-file-in-the-same-folder-overwriting-existing-files"></a><span data-ttu-id="3caae-109">Pour créer une copie d’un fichier dans le même dossier en remplaçant les fichiers existants</span><span class="sxs-lookup"><span data-stu-id="3caae-109">To create a copy of a file in the same folder, overwriting existing files</span></span>  
  
-   <span data-ttu-id="3caae-110">Utilisez la méthode `CopyFile`, en fournissant le fichier cible et l’emplacement, et en affectant la valeur `True` à `overwrite`.</span><span class="sxs-lookup"><span data-stu-id="3caae-110">Use the `CopyFile` method, supplying the target file and location, and setting `overwrite` to `True`.</span></span> <span data-ttu-id="3caae-111">L’exemple suivant crée une copie de `test.txt` nommée `test2.txt` et remplace les fichiers existants portant ce nom.</span><span class="sxs-lookup"><span data-stu-id="3caae-111">The following example creates a copy of `test.txt` called `test2.txt` and overwrites any existing files by that name.</span></span>  
  
     <span data-ttu-id="3caae-112">[!code-vb[VbVbcnMyFileSystem#52](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-create-a-copy-of-a-file-in-the-same-directory_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="3caae-112">[!code-vb[VbVbcnMyFileSystem#52](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-create-a-copy-of-a-file-in-the-same-directory_2.vb)]</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="3caae-113">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="3caae-113">Robust Programming</span></span>  
 <span data-ttu-id="3caae-114">Les conditions ci-dessous peuvent générer une exception :</span><span class="sxs-lookup"><span data-stu-id="3caae-114">The following conditions may cause an exception to be thrown:</span></span>  
  
-   <span data-ttu-id="3caae-115">Le chemin n’est pas valide pour l’une des raisons suivantes : il s’agit d’une chaîne de longueur nulle, il ne contient que des espaces blancs, il contient des caractères non valides ou il s’agit d’un chemin d’appareil (il commence par \\\\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="3caae-115">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="3caae-116">Le système n’a pas pu récupérer le chemin absolu (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="3caae-116">The system could not retrieve the absolute path (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="3caae-117">Le chemin d'accès n'est pas valide, car il a la valeur `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="3caae-117">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="3caae-118">Le fichier source n’est pas valide ou n’existe pas (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="3caae-118">The source file is not valid or does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
-   <span data-ttu-id="3caae-119">Le chemin combiné pointe vers un répertoire existant (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="3caae-119">The combined path points to an existing directory (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="3caae-120">Le fichier de destination existe et `overwrite` a la valeur `False` (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="3caae-120">The destination file exists and `overwrite` is set to `False` (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="3caae-121">L’utilisateur ne dispose pas des autorisations suffisantes pour accéder au fichier (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="3caae-121">The user does not have sufficient permissions to access the file (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="3caae-122">Un fichier du même nom dans le dossier cible est en cours d’utilisation (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="3caae-122">A file in the target folder with the same name is in use (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="3caae-123">Un nom de fichier ou de dossier dans le chemin contient un signe deux-points (:) ou n’a pas un format correct (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="3caae-123">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="3caae-124">`ShowUI` a la valeur `True`, `onUserCancel` a la valeur `ThrowException` et l’utilisateur a annulé l’opération (<xref:System.OperationCanceledException>).</span><span class="sxs-lookup"><span data-stu-id="3caae-124">`ShowUI` is set to `True`, `onUserCancel` is set to `ThrowException`, and the user has cancelled the operation (<xref:System.OperationCanceledException>).</span></span>  
  
-   <span data-ttu-id="3caae-125">`ShowUI`a la valeur `True`, `onUserCancel` a la valeur `ThrowException` et une erreur d’E/S non spécifiée se produit (<xref:System.OperationCanceledException>).</span><span class="sxs-lookup"><span data-stu-id="3caae-125">`ShowUI` is set to `True`, `onUserCancel` is set to `ThrowException`, and an unspecified I/O error occurs (<xref:System.OperationCanceledException>).</span></span>  
  
-   <span data-ttu-id="3caae-126">Le chemin d'accès dépasse la longueur maximale définie par le système (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="3caae-126">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="3caae-127">L’utilisateur ne dispose pas de l’autorisation nécessaire (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="3caae-127">The user does not have required permission (<xref:System.UnauthorizedAccessException>).</span></span>  
  
-   <span data-ttu-id="3caae-128">L'utilisateur n'a pas les autorisations nécessaires pour afficher le chemin (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="3caae-128">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3caae-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3caae-129">See Also</span></span>  
 <span data-ttu-id="3caae-130"><xref:Microsoft.VisualBasic.FileIO.FileSystem></span><span class="sxs-lookup"><span data-stu-id="3caae-130"><xref:Microsoft.VisualBasic.FileIO.FileSystem></span></span>   
 <span data-ttu-id="3caae-131"><xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A></span><span class="sxs-lookup"><span data-stu-id="3caae-131"><xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A></span></span>   
 <span data-ttu-id="3caae-132"><xref:Microsoft.VisualBasic.FileIO.UICancelOption></span><span class="sxs-lookup"><span data-stu-id="3caae-132"><xref:Microsoft.VisualBasic.FileIO.UICancelOption></span></span>   
 <span data-ttu-id="3caae-133">[Guide pratique pour copier des fichiers avec un modèle spécifique dans un répertoire](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-files-with-a-specific-pattern-to-a-directory.md) </span><span class="sxs-lookup"><span data-stu-id="3caae-133">[How to: Copy Files with a Specific Pattern to a Directory](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-files-with-a-specific-pattern-to-a-directory.md) </span></span>  
 <span data-ttu-id="3caae-134">[Guide pratique pour créer une copie d’un fichier dans un autre répertoire](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-a-different-directory.md) </span><span class="sxs-lookup"><span data-stu-id="3caae-134">[How to: Create a Copy of a File in a Different Directory](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-a-different-directory.md) </span></span>  
 <span data-ttu-id="3caae-135">[Guide pratique pour copier un répertoire vers un autre répertoire](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-a-directory-to-another-directory.md) </span><span class="sxs-lookup"><span data-stu-id="3caae-135">[How to: Copy a Directory to Another Directory](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-a-directory-to-another-directory.md) </span></span>  
 [<span data-ttu-id="3caae-136">Guide pratique : renommer un fichier</span><span class="sxs-lookup"><span data-stu-id="3caae-136">How to: Rename a File</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)

