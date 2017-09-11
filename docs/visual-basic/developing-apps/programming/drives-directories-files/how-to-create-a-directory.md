---
title: "Guide pratique pour créer un répertoire en Visual Basic"
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
- directories [Visual Basic], creating
- folders [Visual Basic], creating
ms.assetid: 0351a2ca-24d8-43b5-bb39-9b99e6401cff
caps.latest.revision: 19
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
ms.openlocfilehash: 1a45a785916b480dcee6e36fd295390266eaa0a0
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-create-a-directory-in-visual-basic"></a><span data-ttu-id="d453d-102">Guide pratique pour créer un répertoire en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d453d-102">How to: Create a Directory in Visual Basic</span></span>
<span data-ttu-id="d453d-103">Utilisez la méthode `CreateDirectory` de l’objet `My.Computer.FileSystem` pour créer des répertoires.</span><span class="sxs-lookup"><span data-stu-id="d453d-103">Use the `CreateDirectory` method of the `My.Computer.FileSystem` object to create directories.</span></span>  
  
 <span data-ttu-id="d453d-104">Si le répertoire existe déjà, aucune exception n’est levée.</span><span class="sxs-lookup"><span data-stu-id="d453d-104">If the directory already exists, no exception is thrown.</span></span>  
  
### <a name="to-create-a-directory"></a><span data-ttu-id="d453d-105">Pour créer un répertoire</span><span class="sxs-lookup"><span data-stu-id="d453d-105">To create a directory</span></span>  
  
-   <span data-ttu-id="d453d-106">Utilisez la méthode `CreateDirectory`, en spécifiant le chemin complet de l’emplacement où le répertoire doit être créé.</span><span class="sxs-lookup"><span data-stu-id="d453d-106">Use the `CreateDirectory` method by specifying the full path of the location where the directory should be created.</span></span> <span data-ttu-id="d453d-107">Cet exemple crée le répertoire `NewDirectory` dans `C:\Documents and Settings\All Users\Documents`.</span><span class="sxs-lookup"><span data-stu-id="d453d-107">This example creates the directory `NewDirectory` in `C:\Documents and Settings\All Users\Documents`.</span></span>  
  
     <span data-ttu-id="d453d-108">[!code-vb[VbVbcnMyFileSystem#2](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-create-a-directory_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="d453d-108">[!code-vb[VbVbcnMyFileSystem#2](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-create-a-directory_1.vb)]</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="d453d-109">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="d453d-109">Robust Programming</span></span>  
 <span data-ttu-id="d453d-110">Les conditions ci-dessous peuvent générer une exception.</span><span class="sxs-lookup"><span data-stu-id="d453d-110">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="d453d-111">Le format du nom du répertoire est incorrect.</span><span class="sxs-lookup"><span data-stu-id="d453d-111">The directory name is malformed.</span></span> <span data-ttu-id="d453d-112">Par exemple, il contient des caractères non conformes ou uniquement des espaces blancs (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="d453d-112">For example, it contains illegal characters or is only white space (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="d453d-113">Le répertoire parent du répertoire à créer est en lecture seule (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="d453d-113">The parent directory of the directory to be created is read-only (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="d453d-114">Le nom du répertoire est `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="d453d-114">The directory name is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="d453d-115">Le nom du répertoire est trop long (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="d453d-115">The directory name is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="d453d-116">Le nom du répertoire est un signe deux-points (:) (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="d453d-116">The directory name is a colon ":" (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="d453d-117">L’utilisateur n’a pas l’autorisation de créer le répertoire (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="d453d-117">The user does not have permission to create the directory (<xref:System.UnauthorizedAccessException>).</span></span>  
  
-   <span data-ttu-id="d453d-118">L’utilisateur ne dispose pas des autorisations dans une situation de confiance partielle (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="d453d-118">The user lacks permissions in a partial-trust situation (<xref:System.Security.SecurityException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d453d-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d453d-119">See Also</span></span>  
 <span data-ttu-id="d453d-120"><xref:Microsoft.VisualBasic.FileIO.FileSystem.CreateDirectory%2A></span><span class="sxs-lookup"><span data-stu-id="d453d-120"><xref:Microsoft.VisualBasic.FileIO.FileSystem.CreateDirectory%2A></span></span>   
 [<span data-ttu-id="d453d-121">Création, suppression et déplacement de fichiers et de répertoires</span><span class="sxs-lookup"><span data-stu-id="d453d-121">Creating, Deleting, and Moving Files and Directories</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/creating-deleting-and-moving-files-and-directories.md)

