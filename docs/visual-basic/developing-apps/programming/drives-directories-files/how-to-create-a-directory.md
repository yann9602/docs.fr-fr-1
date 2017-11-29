---
title: "Guide pratique pour créer un répertoire en Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- directories [Visual Basic], creating
- folders [Visual Basic], creating
ms.assetid: 0351a2ca-24d8-43b5-bb39-9b99e6401cff
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2e4cd94113d77b2f4ff8127c80174107966ef360
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-directory-in-visual-basic"></a><span data-ttu-id="48273-102">Guide pratique pour créer un répertoire en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="48273-102">How to: Create a Directory in Visual Basic</span></span>
<span data-ttu-id="48273-103">Utilisez la méthode `CreateDirectory` de l’objet `My.Computer.FileSystem` pour créer des répertoires.</span><span class="sxs-lookup"><span data-stu-id="48273-103">Use the `CreateDirectory` method of the `My.Computer.FileSystem` object to create directories.</span></span>  
  
 <span data-ttu-id="48273-104">Si le répertoire existe déjà, aucune exception n’est levée.</span><span class="sxs-lookup"><span data-stu-id="48273-104">If the directory already exists, no exception is thrown.</span></span>  
  
### <a name="to-create-a-directory"></a><span data-ttu-id="48273-105">Pour créer un répertoire</span><span class="sxs-lookup"><span data-stu-id="48273-105">To create a directory</span></span>  
  
-   <span data-ttu-id="48273-106">Utilisez la méthode `CreateDirectory`, en spécifiant le chemin complet de l’emplacement où le répertoire doit être créé.</span><span class="sxs-lookup"><span data-stu-id="48273-106">Use the `CreateDirectory` method by specifying the full path of the location where the directory should be created.</span></span> <span data-ttu-id="48273-107">Cet exemple crée le répertoire `NewDirectory` dans `C:\Documents and Settings\All Users\Documents`.</span><span class="sxs-lookup"><span data-stu-id="48273-107">This example creates the directory `NewDirectory` in `C:\Documents and Settings\All Users\Documents`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#2](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-create-a-directory_1.vb)]  
  
## <a name="robust-programming"></a><span data-ttu-id="48273-108">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="48273-108">Robust Programming</span></span>  
 <span data-ttu-id="48273-109">Les conditions ci-dessous peuvent générer une exception.</span><span class="sxs-lookup"><span data-stu-id="48273-109">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="48273-110">Le format du nom du répertoire est incorrect.</span><span class="sxs-lookup"><span data-stu-id="48273-110">The directory name is malformed.</span></span> <span data-ttu-id="48273-111">Par exemple, il contient des caractères non conformes ou uniquement des espaces blancs (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="48273-111">For example, it contains illegal characters or is only white space (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="48273-112">Le répertoire parent du répertoire à créer est en lecture seule (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="48273-112">The parent directory of the directory to be created is read-only (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="48273-113">Le nom du répertoire est `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="48273-113">The directory name is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="48273-114">Le nom du répertoire est trop long (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="48273-114">The directory name is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="48273-115">Le nom du répertoire est un signe deux-points (:) (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="48273-115">The directory name is a colon ":" (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="48273-116">L’utilisateur n’a pas l’autorisation de créer le répertoire (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="48273-116">The user does not have permission to create the directory (<xref:System.UnauthorizedAccessException>).</span></span>  
  
-   <span data-ttu-id="48273-117">L’utilisateur ne dispose pas des autorisations dans une situation de confiance partielle (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="48273-117">The user lacks permissions in a partial-trust situation (<xref:System.Security.SecurityException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48273-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="48273-118">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CreateDirectory%2A>  
 [<span data-ttu-id="48273-119">Création, suppression et déplacement de fichiers et de répertoires</span><span class="sxs-lookup"><span data-stu-id="48273-119">Creating, Deleting, and Moving Files and Directories</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/creating-deleting-and-moving-files-and-directories.md)
