---
title: Optional (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Optional
- vb.optional
helpviewer_keywords:
- Optional keyword [Visual Basic], contexts
- Optional keyword [Visual Basic]
ms.assetid: 4571ce88-a539-4115-b230-54eb277c6aa7
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3aa01c2c1ae731c8fe00fdee24521760db69e624
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="optional-visual-basic"></a><span data-ttu-id="59405-102">Optional (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="59405-102">Optional (Visual Basic)</span></span>
<span data-ttu-id="59405-103">Spécifie qu’un argument de procédure peut être omis lorsque la procédure est appelée.</span><span class="sxs-lookup"><span data-stu-id="59405-103">Specifies that a procedure argument can be omitted when the procedure is called.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="59405-104">Remarques</span><span class="sxs-lookup"><span data-stu-id="59405-104">Remarks</span></span>  
 <span data-ttu-id="59405-105">Pour chaque paramètre facultatif, vous devez spécifier une expression constante comme valeur par défaut de ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="59405-105">For each optional parameter, you must specify a constant expression as the default value of that parameter.</span></span> <span data-ttu-id="59405-106">Si l’expression prend la valeur [rien](../../../visual-basic/language-reference/nothing.md), la valeur par défaut la valeur du type de données est utilisée comme valeur par défaut du paramètre.</span><span class="sxs-lookup"><span data-stu-id="59405-106">If the expression evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), the default value of the value data type is used as the default value of the parameter.</span></span>  
  
 <span data-ttu-id="59405-107">Si la liste de paramètres contient un paramètre facultatif, chaque paramètre qui le suit doit également être facultatif.</span><span class="sxs-lookup"><span data-stu-id="59405-107">If the parameter list contains an optional parameter, every parameter that follows it must also be optional.</span></span>  
  
 <span data-ttu-id="59405-108">Le modificateur `Optional` peut être utilisé dans les contextes suivants :</span><span class="sxs-lookup"><span data-stu-id="59405-108">The `Optional` modifier can be used in these contexts:</span></span>  
  
-   [<span data-ttu-id="59405-109">Declare (instruction)</span><span class="sxs-lookup"><span data-stu-id="59405-109">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
-   [<span data-ttu-id="59405-110">Function (instruction)</span><span class="sxs-lookup"><span data-stu-id="59405-110">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
-   [<span data-ttu-id="59405-111">Property (instruction)</span><span class="sxs-lookup"><span data-stu-id="59405-111">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
-   [<span data-ttu-id="59405-112">Sub (instruction)</span><span class="sxs-lookup"><span data-stu-id="59405-112">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
> [!NOTE]
>  <span data-ttu-id="59405-113">Lorsque vous appelez une procédure avec ou sans paramètres facultatifs, vous pouvez passer des arguments par position ou par nom.</span><span class="sxs-lookup"><span data-stu-id="59405-113">When calling a procedure with or without optional parameters, you can pass arguments by position or by name.</span></span> <span data-ttu-id="59405-114">Pour plus d’informations, consultez [en passant les Arguments par Position et par nom](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md).</span><span class="sxs-lookup"><span data-stu-id="59405-114">For more information, see [Passing Arguments by Position and by Name](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="59405-115">Vous pouvez également définir une procédure avec des paramètres facultatifs à l’aide de la surcharge.</span><span class="sxs-lookup"><span data-stu-id="59405-115">You can also define a procedure with optional parameters by using overloading.</span></span> <span data-ttu-id="59405-116">Si vous avez un seul paramètre facultatif, vous pouvez définir deux versions surchargées de la procédure, un qui accepte le paramètre et un autre.</span><span class="sxs-lookup"><span data-stu-id="59405-116">If you have one optional parameter, you can define two overloaded versions of the procedure, one that accepts the parameter and one that doesn’t.</span></span> <span data-ttu-id="59405-117">Pour plus d’informations, consultez [surcharge de procédure](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md).</span><span class="sxs-lookup"><span data-stu-id="59405-117">For more information, see [Procedure Overloading](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="59405-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="59405-118">Example</span></span>  
 <span data-ttu-id="59405-119">L’exemple suivant définit une procédure qui possède un paramètre facultatif.</span><span class="sxs-lookup"><span data-stu-id="59405-119">The following example defines a procedure that has an optional parameter.</span></span>  
  
```  
Public Function FindMatches(ByRef values As List(Of String),  
                            ByVal searchString As String,  
                            Optional ByVal matchCase As Boolean = False) As List(Of String)  
  
    Dim results As IEnumerable(Of String)  
  
    If matchCase Then  
        results = From v In values  
                  Where v.Contains(searchString)  
    Else  
        results = From v In values  
                  Where UCase(v).Contains(UCase(searchString))  
    End If  
  
    Return results.ToList()  
End Function  
```  
  
## <a name="example"></a><span data-ttu-id="59405-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="59405-120">Example</span></span>  
 <span data-ttu-id="59405-121">L’exemple suivant montre comment appeler une procédure avec des arguments passés par position et avec des arguments passés par nom.</span><span class="sxs-lookup"><span data-stu-id="59405-121">The following example demonstrates how to call a procedure with arguments passed by position and with arguments passed by name.</span></span> <span data-ttu-id="59405-122">La procédure comporte deux paramètres facultatifs.</span><span class="sxs-lookup"><span data-stu-id="59405-122">The procedure has two optional parameters.</span></span>  
  
 [!code-vb[VbVbalrKeywords#21](../../../visual-basic/language-reference/codesnippet/VisualBasic/optional_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="59405-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="59405-123">See Also</span></span>  
 [<span data-ttu-id="59405-124">Liste de paramètres</span><span class="sxs-lookup"><span data-stu-id="59405-124">Parameter List</span></span>](../../../visual-basic/language-reference/statements/parameter-list.md)  
 [<span data-ttu-id="59405-125">Paramètres facultatifs</span><span class="sxs-lookup"><span data-stu-id="59405-125">Optional Parameters</span></span>](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)  
 [<span data-ttu-id="59405-126">Mots clés</span><span class="sxs-lookup"><span data-stu-id="59405-126">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
