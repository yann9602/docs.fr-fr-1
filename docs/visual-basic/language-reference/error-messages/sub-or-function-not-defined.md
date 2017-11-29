---
title: "Sub ou Function non défini (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID35
ms.assetid: 661fdb90-ee7d-40ce-b30b-5e7267bd957a
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6237ca26b06bdffa06499607e634b3222725c189
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="sub-or-function-not-defined-visual-basic"></a><span data-ttu-id="d2e66-102">Sub ou Function non défini (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d2e66-102">Sub or Function not defined (Visual Basic)</span></span>
<span data-ttu-id="d2e66-103">A `Sub` ou `Function` doit être défini afin d’être appelée.</span><span class="sxs-lookup"><span data-stu-id="d2e66-103">A `Sub` or `Function` must be defined in order to be called.</span></span> <span data-ttu-id="d2e66-104">Cette erreur peut avoir plusieurs causes :</span><span class="sxs-lookup"><span data-stu-id="d2e66-104">Possible causes of this error include:</span></span>  
  
-   <span data-ttu-id="d2e66-105">Faute d’orthographe dans le nom de la procédure.</span><span class="sxs-lookup"><span data-stu-id="d2e66-105">Misspelling the procedure name.</span></span>  
  
-   <span data-ttu-id="d2e66-106">Essayez d’appeler une procédure à partir d’un autre projet sans ajouter explicitement une référence à ce projet dans le **références** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="d2e66-106">Trying to call a procedure from another project without explicitly adding a reference to that project in the **References** dialog box.</span></span>  
  
-   <span data-ttu-id="d2e66-107">Spécification d’une procédure qui n’est pas visible à la procédure appelante.</span><span class="sxs-lookup"><span data-stu-id="d2e66-107">Specifying a procedure that is not visible to the calling procedure.</span></span>  
  
-   <span data-ttu-id="d2e66-108">Déclaration d’une routine de bibliothèque de liens dynamiques (DLL) de Windows ou d’une routine de ressource de code Macintosh qui n’est pas dans la ressource de bibliothèque ou de code spécifiée.</span><span class="sxs-lookup"><span data-stu-id="d2e66-108">Declaring a Windows dynamic-link library (DLL) routine or Macintosh code-resource routine that is not in the specified library or code resource.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d2e66-109">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="d2e66-109">To correct this error</span></span>  
  
1.  <span data-ttu-id="d2e66-110">Assurez-vous que le nom de la procédure est correctement orthographié.</span><span class="sxs-lookup"><span data-stu-id="d2e66-110">Make sure that the procedure name is spelled correctly.</span></span>  
  
2.  <span data-ttu-id="d2e66-111">Rechercher le nom du projet contenant la procédure que vous voulez appeler dans le **références** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="d2e66-111">Find the name of the project containing the procedure you want to call in the **References** dialog box.</span></span> <span data-ttu-id="d2e66-112">Si elle n’apparaît pas, cliquez sur le **Parcourir** bouton pour le rechercher.</span><span class="sxs-lookup"><span data-stu-id="d2e66-112">If it does not appear, click the **Browse** button to search for it.</span></span> <span data-ttu-id="d2e66-113">Activez la case à cocher à gauche du nom du projet, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="d2e66-113">Select the check box to the left of the project name, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="d2e66-114">Vérifiez le nom de la routine.</span><span class="sxs-lookup"><span data-stu-id="d2e66-114">Check the name of the routine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2e66-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d2e66-115">See Also</span></span>  
 [<span data-ttu-id="d2e66-116">Types d’erreurs</span><span class="sxs-lookup"><span data-stu-id="d2e66-116">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)  
 [<span data-ttu-id="d2e66-117">Gestion des références dans un projet</span><span class="sxs-lookup"><span data-stu-id="d2e66-117">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)  
 [<span data-ttu-id="d2e66-118">Sub (instruction)</span><span class="sxs-lookup"><span data-stu-id="d2e66-118">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="d2e66-119">Function (instruction)</span><span class="sxs-lookup"><span data-stu-id="d2e66-119">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
