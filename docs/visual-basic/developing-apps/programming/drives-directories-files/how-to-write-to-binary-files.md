---
title: "Guide pratique pour écrire dans des fichiers binaires en Visual Basic"
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
- files, binary access
- WriteAllBytes method
- binary files, writing in Visual Basic
ms.assetid: 59fae125-de5b-4c96-883c-209f4a55112c
caps.latest.revision: 16
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
ms.openlocfilehash: ae6f275dd86a53c6b6251feb08210a775adba0b0
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-write-to-binary-files-in-visual-basic"></a><span data-ttu-id="eae88-102">Guide pratique pour écrire dans des fichiers binaires en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="eae88-102">How to: Write to Binary Files in Visual Basic</span></span>
<span data-ttu-id="eae88-103">La méthode <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A> écrit des données dans un fichier binaire.</span><span class="sxs-lookup"><span data-stu-id="eae88-103">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A> method writes data to a binary file.</span></span> <span data-ttu-id="eae88-104">Si le paramètre `append` est `True`, elle ajoute les données au fichier ; sinon, les données dans le fichier sont remplacées.</span><span class="sxs-lookup"><span data-stu-id="eae88-104">If the `append` parameter is `True`, it will append the data to the file; otherwise data in the file is overwritten.</span></span>  
  
 <span data-ttu-id="eae88-105">Si le chemin spécifié (nom de fichier exclu) n’est pas valide, une exception <xref:System.IO.DirectoryNotFoundException> est levée.</span><span class="sxs-lookup"><span data-stu-id="eae88-105">If the specified path excluding the file name is not valid, a <xref:System.IO.DirectoryNotFoundException> exception will be thrown.</span></span> <span data-ttu-id="eae88-106">Si le chemin est valide mais que le fichier n’existe pas, le fichier est créé.</span><span class="sxs-lookup"><span data-stu-id="eae88-106">If the path is valid but the file does not exist, the file will be created.</span></span>  
  
### <a name="to-write-to-a-binary-file"></a><span data-ttu-id="eae88-107">Pour écrire dans un fichier binaire</span><span class="sxs-lookup"><span data-stu-id="eae88-107">To write to a binary file</span></span>  
  
-   <span data-ttu-id="eae88-108">Utilisez la méthode `WriteAllBytes` en fournissant le chemin et le nom du fichier, ainsi que les octets à écrire.</span><span class="sxs-lookup"><span data-stu-id="eae88-108">Use the `WriteAllBytes` method, supplying the file path and name and the bytes to be written.</span></span> <span data-ttu-id="eae88-109">Cet exemple ajoute le tableau de données `CustomerData` au fichier nommé `CollectedData.dat`.</span><span class="sxs-lookup"><span data-stu-id="eae88-109">This example appends the data array `CustomerData` to the file named `CollectedData.dat`.</span></span>  
  
     <span data-ttu-id="eae88-110">[!code-vb[VbVbcnMyFileSystem#27](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-to-binary-files_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="eae88-110">[!code-vb[VbVbcnMyFileSystem#27](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-to-binary-files_1.vb)]</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="eae88-111">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="eae88-111">Robust Programming</span></span>  
 <span data-ttu-id="eae88-112">Les conditions ci-dessous peuvent générer une exception :</span><span class="sxs-lookup"><span data-stu-id="eae88-112">The following conditions may create an exception:</span></span>  
  
-   <span data-ttu-id="eae88-113">Le chemin n’est pas valide pour l’une des raisons suivantes : il s’agit d’une chaîne de longueur nulle, il ne contient que des espaces blancs ou il contient des caractères non valides.</span><span class="sxs-lookup"><span data-stu-id="eae88-113">The path is not valid for one of the following reasons: it is a zero-length string; it contains only white space; or it contains invalid characters.</span></span> <span data-ttu-id="eae88-114">(<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="eae88-114">(<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="eae88-115">Le chemin d'accès n'est pas valide, car il a la valeur `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="eae88-115">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="eae88-116">`File` pointe vers un chemin qui n’existe pas (<xref:System.IO.FileNotFoundException> ou <xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="eae88-116">`File` points to a path that does not exist (<xref:System.IO.FileNotFoundException> or <xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
-   <span data-ttu-id="eae88-117">Le fichier est utilisé par un autre processus, ou une erreur E/S se produit (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="eae88-117">The file is in use by another process, or an I/O error occurs (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="eae88-118">Le chemin d'accès dépasse la longueur maximale définie par le système (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="eae88-118">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="eae88-119">Un nom de fichier ou de répertoire du chemin contient un signe deux-points (:) ou n'a pas un format correct (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="eae88-119">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="eae88-120">L'utilisateur n'a pas les autorisations nécessaires pour afficher le chemin (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="eae88-120">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eae88-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eae88-121">See Also</span></span>  
 <span data-ttu-id="eae88-122"><xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A></span><span class="sxs-lookup"><span data-stu-id="eae88-122"><xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A></span></span>   
 [<span data-ttu-id="eae88-123">Guide pratique : insérer du texte dans des fichiers</span><span class="sxs-lookup"><span data-stu-id="eae88-123">How to: Write Text to Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-write-text-to-files.md)

