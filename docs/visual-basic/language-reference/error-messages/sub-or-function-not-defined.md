---
title: "Sub ou Function non défini (Visual Basic) | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID35
dev_langs:
- VB
ms.assetid: 661fdb90-ee7d-40ce-b30b-5e7267bd957a
caps.latest.revision: 12
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 837beec039e1fb8f8a796b2781d93de6d4cfb33a
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="sub-or-function-not-defined-visual-basic"></a><span data-ttu-id="14473-102">Sub ou Function non défini (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="14473-102">Sub or Function not defined (Visual Basic)</span></span>
<span data-ttu-id="14473-103">A `Sub` ou `Function` doit être définie pour être appelée.</span><span class="sxs-lookup"><span data-stu-id="14473-103">A `Sub` or `Function` must be defined in order to be called.</span></span> <span data-ttu-id="14473-104">Cette erreur peut avoir plusieurs causes :</span><span class="sxs-lookup"><span data-stu-id="14473-104">Possible causes of this error include:</span></span>  
  
-   <span data-ttu-id="14473-105">Faute d’orthographe du nom de la procédure.</span><span class="sxs-lookup"><span data-stu-id="14473-105">Misspelling the procedure name.</span></span>  
  
-   <span data-ttu-id="14473-106">Essayez d’appeler une procédure depuis un autre projet sans ajouter explicitement une référence au projet dans le **références** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="14473-106">Trying to call a procedure from another project without explicitly adding a reference to that project in the **References** dialog box.</span></span>  
  
-   <span data-ttu-id="14473-107">Spécification d’une procédure qui n’est pas visible pour la procédure appelante.</span><span class="sxs-lookup"><span data-stu-id="14473-107">Specifying a procedure that is not visible to the calling procedure.</span></span>  
  
-   <span data-ttu-id="14473-108">La déclaration d’une routine de bibliothèque de liens dynamiques (DLL) de Windows ou d’une routine de ressource de code Macintosh qui n’est pas dans la ressource de bibliothèque ou de code spécifiée.</span><span class="sxs-lookup"><span data-stu-id="14473-108">Declaring a Windows dynamic-link library (DLL) routine or Macintosh code-resource routine that is not in the specified library or code resource.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="14473-109">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="14473-109">To correct this error</span></span>  
  
1.  <span data-ttu-id="14473-110">Assurez-vous que le nom de la procédure est correctement orthographié.</span><span class="sxs-lookup"><span data-stu-id="14473-110">Make sure that the procedure name is spelled correctly.</span></span>  
  
2.  <span data-ttu-id="14473-111">Recherchez le nom du projet contenant la procédure que vous voulez appeler dans le **références** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="14473-111">Find the name of the project containing the procedure you want to call in the **References** dialog box.</span></span> <span data-ttu-id="14473-112">Si elle n’apparaît pas, cliquez sur le **Parcourir** bouton de recherche.</span><span class="sxs-lookup"><span data-stu-id="14473-112">If it does not appear, click the **Browse** button to search for it.</span></span> <span data-ttu-id="14473-113">Activez la case à cocher à gauche du nom du projet, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="14473-113">Select the check box to the left of the project name, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="14473-114">Vérifiez le nom de la routine.</span><span class="sxs-lookup"><span data-stu-id="14473-114">Check the name of the routine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14473-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="14473-115">See Also</span></span>  
 <span data-ttu-id="14473-116">[Types d’erreurs](../../../visual-basic/programming-guide/language-features/error-types.md) </span><span class="sxs-lookup"><span data-stu-id="14473-116">[Error Types](../../../visual-basic/programming-guide/language-features/error-types.md) </span></span>  
<span data-ttu-id="14473-117"> [Gestion des références dans un projet](https://docs.microsoft.com/visualstudio/ide/managing-references-in-a-project) </span><span class="sxs-lookup"><span data-stu-id="14473-117"> [Managing references in a project](https://docs.microsoft.com/visualstudio/ide/managing-references-in-a-project) </span></span>  
<span data-ttu-id="14473-118"> [Sub (instruction)](../../../visual-basic/language-reference/statements/sub-statement.md) </span><span class="sxs-lookup"><span data-stu-id="14473-118"> [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md) </span></span>  
<span data-ttu-id="14473-119"> [Function (instruction)](../../../visual-basic/language-reference/statements/function-statement.md)</span><span class="sxs-lookup"><span data-stu-id="14473-119"> [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md)</span></span>
