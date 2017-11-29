---
title: Alias, clause (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Alias
helpviewer_keywords: Alias keyword [Visual Basic]
ms.assetid: 58c06b11-465d-4d87-906a-73200a3d7f19
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f61e738434ea616d751576ef21669545afc41397
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="alias-clause-visual-basic"></a><span data-ttu-id="cee4c-102">Alias, clause (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cee4c-102">Alias Clause (Visual Basic)</span></span>
<span data-ttu-id="cee4c-103">Indique qu’une procédure externe a un autre nom dans sa DLL.</span><span class="sxs-lookup"><span data-stu-id="cee4c-103">Indicates that an external procedure has another name in its DLL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cee4c-104">Remarques</span><span class="sxs-lookup"><span data-stu-id="cee4c-104">Remarks</span></span>  
 <span data-ttu-id="cee4c-105">Le `Alias` mot clé peut être utilisé dans ce contexte :</span><span class="sxs-lookup"><span data-stu-id="cee4c-105">The `Alias` keyword can be used in this context:</span></span>  
  
 [<span data-ttu-id="cee4c-106">Declare (instruction)</span><span class="sxs-lookup"><span data-stu-id="cee4c-106">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 <span data-ttu-id="cee4c-107">Dans l’exemple suivant, la `Alias` est utilisé pour fournir le nom de la fonction dans advapi32.dll, `GetUserNameA`, qui `getUserName` est utilisé à la place de dans cet exemple.</span><span class="sxs-lookup"><span data-stu-id="cee4c-107">In the following example, the `Alias` keyword is used to provide the name of the function in advapi32.dll, `GetUserNameA`, that `getUserName` is used in place of in this example.</span></span> <span data-ttu-id="cee4c-108">Fonction `getUserName` est appelée dans un sub `getUser`, qui affiche le nom de l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="cee4c-108">Function `getUserName` is called in sub `getUser`, which displays the name of the current user.</span></span>  
  
 [!code-vb[VbVbalrStatements#15](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/alias-clause_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="cee4c-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cee4c-109">See Also</span></span>  
 [<span data-ttu-id="cee4c-110">Mots clés</span><span class="sxs-lookup"><span data-stu-id="cee4c-110">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
