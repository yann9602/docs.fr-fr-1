---
title: "Nom ou numéro de fichier incorrect"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID52
ms.assetid: d0e96aea-7621-48f6-a78b-5d37d18aaa4e
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3d7c8bae3df0e75a1c4f9afacdff681a553503d2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="bad-file-name-or-number"></a><span data-ttu-id="7cf45-102">Nom ou numéro de fichier incorrect</span><span class="sxs-lookup"><span data-stu-id="7cf45-102">Bad file name or number</span></span>
<span data-ttu-id="7cf45-103">Une erreur s’est produite lors de la tentative d’accès au fichier spécifié.</span><span class="sxs-lookup"><span data-stu-id="7cf45-103">An error occurred while trying to access the specified file.</span></span> <span data-ttu-id="7cf45-104">Parmi les causes possibles de cette erreur sont :</span><span class="sxs-lookup"><span data-stu-id="7cf45-104">Among the possible causes for this error are:</span></span>  
  
-   <span data-ttu-id="7cf45-105">Une instruction fait référence à un fichier avec un nom de fichier ou d’un nombre qui n’a pas été spécifié dans le `FileOpen` instruction ou qui a été spécifié dans un `FileOpen` instruction mais a ensuite fermé.</span><span class="sxs-lookup"><span data-stu-id="7cf45-105">A statement refers to a file with a file name or number that was not specified in the `FileOpen` statement or that was specified in a `FileOpen` statement but was subsequently closed.</span></span>  
  
-   <span data-ttu-id="7cf45-106">Une instruction fait référence à un fichier avec un nombre qui est en dehors de la plage des numéros de fichier.</span><span class="sxs-lookup"><span data-stu-id="7cf45-106">A statement refers to a file with a number that is out of the range of file numbers.</span></span>  
  
-   <span data-ttu-id="7cf45-107">Une instruction fait référence à un nom de fichier ou un nombre qui n’est pas valide.</span><span class="sxs-lookup"><span data-stu-id="7cf45-107">A statement refers to a file name or number that is not valid.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7cf45-108">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="7cf45-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="7cf45-109">Assurez-vous que le nom de fichier est spécifié dans un `FileOpen` instruction.</span><span class="sxs-lookup"><span data-stu-id="7cf45-109">Make sure the file name is specified in a `FileOpen` statement.</span></span> <span data-ttu-id="7cf45-110">Notez que si vous avez appelé la `FileClose` instruction sans arguments, vous avez peut-être fermé accidentellement tous les fichiers ouverts.</span><span class="sxs-lookup"><span data-stu-id="7cf45-110">Note that if you invoked the `FileClose` statement without arguments, you may have inadvertently closed all open files.</span></span>  
  
2.  <span data-ttu-id="7cf45-111">Si votre code génère des nombres de fichier par algorithme, vérifiez que les nombres sont valides.</span><span class="sxs-lookup"><span data-stu-id="7cf45-111">If your code is generating file numbers algorithmically, make sure the numbers are valid.</span></span>  
  
3.  <span data-ttu-id="7cf45-112">Vérifiez les noms de fichiers pour vous assurer qu’elles sont conformes aux conventions du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="7cf45-112">Check the file names to make sure they conform to operating system conventions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cf45-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7cf45-113">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileSystem.FileOpen%2A>  
 [<span data-ttu-id="7cf45-114">Conventions d’affectation de noms de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7cf45-114">Visual Basic Naming Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
