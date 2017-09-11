---
title: Guide pratique pour supprimer un fichier dans Visual Basic
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
- Delete method
- files, deleting
- files, manipulating
- File object
ms.assetid: 4b721769-3e45-4be7-b7fe-b08dc4141b44
caps.latest.revision: 24
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
ms.openlocfilehash: e4b0b87fd403556777e0ab5a1edd517687360374
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-delete-a-file-in-visual-basic"></a><span data-ttu-id="86b13-102">Guide pratique pour supprimer un fichier dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="86b13-102">How to: Delete a File in Visual Basic</span></span>
<span data-ttu-id="86b13-103">La méthode `DeleteFile` de l’objet `My.Computer.FileSystem` vous permet de supprimer un fichier.</span><span class="sxs-lookup"><span data-stu-id="86b13-103">The `DeleteFile` method of the `My.Computer.FileSystem` object allows you to delete a file.</span></span> <span data-ttu-id="86b13-104">Elle offre entre autres les options suivantes : envoyer ou non le fichier supprimé à la **Corbeille**, demander ou non à l’utilisateur de confirmer que le fichier doit être supprimé et l’action à effectuer quand l’utilisateur annule l’opération.</span><span class="sxs-lookup"><span data-stu-id="86b13-104">Among the options it offers are: whether to send the deleted file to the **Recycle Bin**, whether to ask the user to confirm that the file should be deleted, and what to do when the user cancels the operation.</span></span>  
  
### <a name="to-delete-a-text-file"></a><span data-ttu-id="86b13-105">Pour supprimer un fichier texte</span><span class="sxs-lookup"><span data-stu-id="86b13-105">To delete a text file</span></span>  
  
-   <span data-ttu-id="86b13-106">Utilisez la méthode `DeleteFile` pour supprimer le fichier.</span><span class="sxs-lookup"><span data-stu-id="86b13-106">Use the `DeleteFile` method to delete the file.</span></span> <span data-ttu-id="86b13-107">Le code suivant illustre comment supprimer le fichier nommé `test.txt`.</span><span class="sxs-lookup"><span data-stu-id="86b13-107">The following code demonstrates how to delete the file named `test.txt`.</span></span>  
  
     <span data-ttu-id="86b13-108">[!code-vb[VbVbcnMyFileSystem#22](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-delete-a-file_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="86b13-108">[!code-vb[VbVbcnMyFileSystem#22](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-delete-a-file_1.vb)]</span></span>  
  
### <a name="to-delete-a-text-file-and-ask-the-user-to-confirm-that-the-file-should-be-deleted"></a><span data-ttu-id="86b13-109">Pour supprimer un fichier texte et demander à l’utilisateur de confirmer que le fichier doit être supprimé</span><span class="sxs-lookup"><span data-stu-id="86b13-109">To delete a text file and ask the user to confirm that the file should be deleted</span></span>  
  
-   <span data-ttu-id="86b13-110">Utilisez la méthode `DeleteFile` pour supprimer le fichier en affectant `showUI` à `AllDialogs`.</span><span class="sxs-lookup"><span data-stu-id="86b13-110">Use the `DeleteFile` method to delete the file, setting `showUI` to `AllDialogs`.</span></span> <span data-ttu-id="86b13-111">Le code suivant illustre comment supprimer le fichier nommé `test.txt` et permettre à l’utilisateur de confirmer que le fichier doit être supprimé.</span><span class="sxs-lookup"><span data-stu-id="86b13-111">The following code demonstrates how to delete the file named `test.txt` and allow the user to confirm that the file should be deleted.</span></span>  
  
     <span data-ttu-id="86b13-112">[!code-vb[VbFileIOMisc#9](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-delete-a-file_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="86b13-112">[!code-vb[VbFileIOMisc#9](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-delete-a-file_2.vb)]</span></span>  
  
### <a name="to-delete-a-text-file-and-send-it-to-the-recycle-bin"></a><span data-ttu-id="86b13-113">Pour supprimer un fichier texte et l’envoyer à la Corbeille</span><span class="sxs-lookup"><span data-stu-id="86b13-113">To delete a text file and send it to the Recycle Bin</span></span>  
  
-   <span data-ttu-id="86b13-114">Utilisez la méthode `DeleteFile` pour supprimer le fichier en spécifiant `SendToRecycleBin` pour le paramètre `recycle`.</span><span class="sxs-lookup"><span data-stu-id="86b13-114">Use the `DeleteFile` method to delete the file, specifying `SendToRecycleBin` for the `recycle` parameter.</span></span> <span data-ttu-id="86b13-115">Le code suivant illustre comment supprimer le fichier nommé `test.txt` et l’envoyer à la **Corbeille**.</span><span class="sxs-lookup"><span data-stu-id="86b13-115">The following code demonstrates how to delete the file named `test.txt` and send it to the **Recycle Bin**.</span></span>  
  
     <span data-ttu-id="86b13-116">[!code-vb[VbFileIOMisc#10](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-delete-a-file_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="86b13-116">[!code-vb[VbFileIOMisc#10](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-delete-a-file_3.vb)]</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="86b13-117">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="86b13-117">Robust Programming</span></span>  
 <span data-ttu-id="86b13-118">Les conditions ci-dessous peuvent générer une exception.</span><span class="sxs-lookup"><span data-stu-id="86b13-118">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="86b13-119">Le chemin n’est pas valide pour l’une des raisons suivantes : il s’agit d’une chaîne de longueur nulle, il ne contient que des espaces blancs, il contient des caractères non valides ou il s’agit d’un chemin d’appareil (il commence par \\\\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="86b13-119">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="86b13-120">Le chemin n’est pas valide, car il a la valeur `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="86b13-120">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="86b13-121">Le chemin d'accès dépasse la longueur maximale définie par le système (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="86b13-121">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="86b13-122">Un nom de fichier ou de dossier dans le chemin contient un signe deux-points (:) ou n’a pas un format correct (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="86b13-122">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="86b13-123">Le fichier est en cours d’utilisation (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="86b13-123">The file is in use (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="86b13-124">L'utilisateur n'a pas les autorisations nécessaires pour afficher le chemin d'accès (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="86b13-124">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="86b13-125">Le fichier n'existe pas (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="86b13-125">The file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
-   <span data-ttu-id="86b13-126">L’utilisateur n’a pas l’autorisation de supprimer le fichier ou le fichier est en lecture seule (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="86b13-126">The user does not have permission to delete the file, or the file is read-only (<xref:System.UnauthorizedAccessException>).</span></span>  
  
-   <span data-ttu-id="86b13-127">Une situation de confiance partielle dans laquelle l’utilisateur ne dispose pas des autorisations suffisantes existe (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="86b13-127">A partial-trust situation exists in which the user does not have sufficient permissions (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="86b13-128">L’utilisateur a annulé l’opération et `onUserCancel` a la valeur `ThrowException` (<xref:System.OperationCanceledException>).</span><span class="sxs-lookup"><span data-stu-id="86b13-128">The user cancelled the operation and `onUserCancel` is set to `ThrowException` (<xref:System.OperationCanceledException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86b13-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="86b13-129">See Also</span></span>  
 <span data-ttu-id="86b13-130"><xref:Microsoft.VisualBasic.FileIO.UICancelOption></span><span class="sxs-lookup"><span data-stu-id="86b13-130"><xref:Microsoft.VisualBasic.FileIO.UICancelOption></span></span>   
 <span data-ttu-id="86b13-131"><xref:Microsoft.VisualBasic.FileIO.FileSystem></span><span class="sxs-lookup"><span data-stu-id="86b13-131"><xref:Microsoft.VisualBasic.FileIO.FileSystem></span></span>   
 <span data-ttu-id="86b13-132"><xref:Microsoft.VisualBasic.FileIO.UIOption></span><span class="sxs-lookup"><span data-stu-id="86b13-132"><xref:Microsoft.VisualBasic.FileIO.UIOption></span></span>   
 <span data-ttu-id="86b13-133"><xref:Microsoft.VisualBasic.FileIO.RecycleOption></span><span class="sxs-lookup"><span data-stu-id="86b13-133"><xref:Microsoft.VisualBasic.FileIO.RecycleOption></span></span>   
 [<span data-ttu-id="86b13-134">Guide pratique pour placer la collection de fichiers dans un répertoire</span><span class="sxs-lookup"><span data-stu-id="86b13-134">How to: Get the Collection of Files in a Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)

