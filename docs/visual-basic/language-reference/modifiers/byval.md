---
title: Byval (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.ByVal
- ByVal
helpviewer_keywords:
- ByVal keyword [Visual Basic], contexts
- ByVal keyword [Visual Basic]
ms.assetid: 1eaf4e58-b305-4785-9e3d-e416b9c75598
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c192cdb4ac43ad614fbfb663079c03ddc6c358c5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="byval-visual-basic"></a><span data-ttu-id="f9f27-102">Byval (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f9f27-102">ByVal (Visual Basic)</span></span>
<span data-ttu-id="f9f27-103">Spécifie qu’un argument est passé de sorte que la procédure ou propriété appelée ne peut pas modifier la valeur d’une variable sous-jacente à l’argument dans le code appelant.</span><span class="sxs-lookup"><span data-stu-id="f9f27-103">Specifies that an argument is passed in such a way that the called procedure or property cannot change the value of a variable underlying the argument in the calling code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f9f27-104">Remarques</span><span class="sxs-lookup"><span data-stu-id="f9f27-104">Remarks</span></span>  
 <span data-ttu-id="f9f27-105">Le modificateur `ByVal` peut être utilisé dans les contextes suivants :</span><span class="sxs-lookup"><span data-stu-id="f9f27-105">The `ByVal` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="f9f27-106">Declare (instruction)</span><span class="sxs-lookup"><span data-stu-id="f9f27-106">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="f9f27-107">Function (instruction)</span><span class="sxs-lookup"><span data-stu-id="f9f27-107">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="f9f27-108">Operator (instruction)</span><span class="sxs-lookup"><span data-stu-id="f9f27-108">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [<span data-ttu-id="f9f27-109">Property (instruction)</span><span class="sxs-lookup"><span data-stu-id="f9f27-109">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="f9f27-110">Sub (instruction)</span><span class="sxs-lookup"><span data-stu-id="f9f27-110">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="example"></a><span data-ttu-id="f9f27-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="f9f27-111">Example</span></span>  
 <span data-ttu-id="f9f27-112">L’exemple suivant illustre l’utilisation de la `ByVal` mécanisme avec un argument de type référence de passage de paramètres.</span><span class="sxs-lookup"><span data-stu-id="f9f27-112">The following example demonstrates the use of the `ByVal` parameter passing mechanism with a reference type argument.</span></span> <span data-ttu-id="f9f27-113">Dans l’exemple, l’argument est `c1`, une instance de la classe `Class1`.</span><span class="sxs-lookup"><span data-stu-id="f9f27-113">In the example, the argument is `c1`, an instance of class `Class1`.</span></span> <span data-ttu-id="f9f27-114">`ByVal`empêche le code dans les procédures de modification de la valeur sous-jacente de l’argument de référence, `c1`, mais ne protège ne pas les champs accessibles et les propriétés de `c1`.</span><span class="sxs-lookup"><span data-stu-id="f9f27-114">`ByVal` prevents the code in the procedures from changing the underlying value of the reference argument, `c1`, but does not protect the accessible fields and properties of `c1`.</span></span>  
  
 [!code-vb[VbVbalrKeywords#10](../../../visual-basic/language-reference/codesnippet/VisualBasic/byval_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="f9f27-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f9f27-115">See Also</span></span>  
 [<span data-ttu-id="f9f27-116">Mots clés</span><span class="sxs-lookup"><span data-stu-id="f9f27-116">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)  
 [<span data-ttu-id="f9f27-117">Passage d’un argument par valeur et par référence</span><span class="sxs-lookup"><span data-stu-id="f9f27-117">Passing Arguments by Value and by Reference</span></span>](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
