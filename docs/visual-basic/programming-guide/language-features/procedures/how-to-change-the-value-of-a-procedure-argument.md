---
title: "Comment : modifier la valeur d’un Argument de procédure (Visual Basic) | Documents Microsoft"
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
- procedures, arguments
- procedures, parameters
- procedure arguments
- arguments [Visual Basic], passing by reference
- Visual Basic code, procedures
- arguments [Visual Basic], ByVal
- arguments [Visual Basic], passing by value
- procedure parameters
- arguments [Visual Basic], ByRef
- arguments [Visual Basic], changing value
ms.assetid: 6fad2368-5da7-4c07-8bf8-0f4e65a1be67
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 3f192d738ca2753cd12b6fffca1f4f94a606a42c
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-change-the-value-of-a-procedure-argument-visual-basic"></a><span data-ttu-id="3cc2d-102">Comment : modifier la valeur d’un argument de la procédure (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3cc2d-102">How to: Change the Value of a Procedure Argument (Visual Basic)</span></span>
<span data-ttu-id="3cc2d-103">Lorsque vous appelez une procédure, chaque argument que vous fournissez correspond à l’un des paramètres définis dans la procédure.</span><span class="sxs-lookup"><span data-stu-id="3cc2d-103">When you call a procedure, each argument you supply corresponds to one of the parameters defined in the procedure.</span></span> <span data-ttu-id="3cc2d-104">Dans certains cas, le code de procédure peut modifier la valeur sous-jacente à un argument dans le code appelant.</span><span class="sxs-lookup"><span data-stu-id="3cc2d-104">In some cases, the procedure code can change the value underlying an argument in the calling code.</span></span> <span data-ttu-id="3cc2d-105">Dans d’autres cas, la procédure peut modifier uniquement sa copie locale d’un argument.</span><span class="sxs-lookup"><span data-stu-id="3cc2d-105">In other cases, the procedure can change only its local copy of an argument.</span></span>  
  
 <span data-ttu-id="3cc2d-106">Lorsque vous appelez la procédure, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] fait une copie locale de chaque argument est passé [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).</span><span class="sxs-lookup"><span data-stu-id="3cc2d-106">When you call the procedure, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] makes a local copy of every argument that is passed [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).</span></span> <span data-ttu-id="3cc2d-107">Pour chaque argument passé [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] donne le code de procédure une référence directe à l’élément de programmation sous-jacent à l’argument dans le code appelant.</span><span class="sxs-lookup"><span data-stu-id="3cc2d-107">For each argument passed [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] gives the procedure code a direct reference to the programming element underlying the argument in the calling code.</span></span>  
  
 <span data-ttu-id="3cc2d-108">Si l’élément sous-jacent dans le code appelant est un élément modifiable et que l’argument est passé `ByRef`, le code de procédure peut utiliser la référence directe pour modifier la valeur de l’élément dans le code appelant.</span><span class="sxs-lookup"><span data-stu-id="3cc2d-108">If the underlying element in the calling code is a modifiable element and the argument is passed `ByRef`, the procedure code can use the direct reference to change the element's value in the calling code.</span></span>  
  
## <a name="changing-the-underlying-value"></a><span data-ttu-id="3cc2d-109">Modification de la valeur sous-jacente</span><span class="sxs-lookup"><span data-stu-id="3cc2d-109">Changing the Underlying Value</span></span>  
  
#### <a name="to-change-the-underlying-value-of-a-procedure-argument-in-the-calling-code"></a><span data-ttu-id="3cc2d-110">Pour modifier la valeur sous-jacente d’un argument de procédure dans le code appelant</span><span class="sxs-lookup"><span data-stu-id="3cc2d-110">To change the underlying value of a procedure argument in the calling code</span></span>  
  
1.  <span data-ttu-id="3cc2d-111">Dans la déclaration de procédure, spécifiez [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) pour le paramètre correspondant à l’argument.</span><span class="sxs-lookup"><span data-stu-id="3cc2d-111">In the procedure declaration, specify [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) for the parameter corresponding to the argument.</span></span>  
  
2.  <span data-ttu-id="3cc2d-112">Dans le code appelant, passez un élément de programmation modifiable comme argument.</span><span class="sxs-lookup"><span data-stu-id="3cc2d-112">In the calling code, pass a modifiable programming element as the argument.</span></span>  
  
3.  <span data-ttu-id="3cc2d-113">Dans le code appelant, ne placez pas l’argument entre parenthèses dans la liste d’arguments.</span><span class="sxs-lookup"><span data-stu-id="3cc2d-113">In the calling code, do not enclose the argument in parentheses in the argument list.</span></span>  
  
4.  <span data-ttu-id="3cc2d-114">Dans le code de procédure, utilisez le nom de paramètre pour assigner une valeur à l’élément sous-jacent dans le code appelant.</span><span class="sxs-lookup"><span data-stu-id="3cc2d-114">In the procedure code, use the parameter name to assign a value to the underlying element in the calling code.</span></span>  
  
 <span data-ttu-id="3cc2d-115">Consultez l’exemple ci-dessous pour une démonstration.</span><span class="sxs-lookup"><span data-stu-id="3cc2d-115">See the example further down for a demonstration.</span></span>  
  
## <a name="changing-local-copies"></a><span data-ttu-id="3cc2d-116">Modification de Copies locales</span><span class="sxs-lookup"><span data-stu-id="3cc2d-116">Changing Local Copies</span></span>  
 <span data-ttu-id="3cc2d-117">Si l’élément sous-jacent dans le code appelant est un élément non modifiable, ou si l’argument est passé `ByVal`, la procédure ne peut pas modifier sa valeur dans le code appelant.</span><span class="sxs-lookup"><span data-stu-id="3cc2d-117">If the underlying element in the calling code is a nonmodifiable element, or if the argument is passed `ByVal`, the procedure cannot change its value in the calling code.</span></span> <span data-ttu-id="3cc2d-118">Toutefois, la procédure peut modifier sa copie locale de l’argument.</span><span class="sxs-lookup"><span data-stu-id="3cc2d-118">However, the procedure can change its local copy of such an argument.</span></span>  
  
#### <a name="to-change-the-copy-of-a-procedure-argument-in-the-procedure-code"></a><span data-ttu-id="3cc2d-119">Pour modifier la copie d’un argument de procédure dans le code de procédure</span><span class="sxs-lookup"><span data-stu-id="3cc2d-119">To change the copy of a procedure argument in the procedure code</span></span>  
  
1.  <span data-ttu-id="3cc2d-120">Dans la déclaration de procédure, spécifiez [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) pour le paramètre correspondant à l’argument.</span><span class="sxs-lookup"><span data-stu-id="3cc2d-120">In the procedure declaration, specify [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) for the parameter corresponding to the argument.</span></span>  
  
     <span data-ttu-id="3cc2d-121">ou</span><span class="sxs-lookup"><span data-stu-id="3cc2d-121">-or-</span></span>  
  
     <span data-ttu-id="3cc2d-122">Dans le code appelant, mettez l’argument entre parenthèses dans la liste d’arguments.</span><span class="sxs-lookup"><span data-stu-id="3cc2d-122">In the calling code, enclose the argument in parentheses in the argument list.</span></span> <span data-ttu-id="3cc2d-123">Cette option force [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] pour passer l’argument par valeur, même si le paramètre correspondant spécifie `ByRef`.</span><span class="sxs-lookup"><span data-stu-id="3cc2d-123">This forces [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] to pass the argument by value, even if the corresponding parameter specifies `ByRef`.</span></span>  
  
2.  <span data-ttu-id="3cc2d-124">Dans le code de procédure, utilisez le nom de paramètre pour assigner une valeur à la copie locale de l’argument.</span><span class="sxs-lookup"><span data-stu-id="3cc2d-124">In the procedure code, use the parameter name to assign a value to the local copy of the argument.</span></span> <span data-ttu-id="3cc2d-125">La valeur sous-jacente dans le code appelant n’est pas modifiée.</span><span class="sxs-lookup"><span data-stu-id="3cc2d-125">The underlying value in the calling code is not changed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3cc2d-126">Exemple</span><span class="sxs-lookup"><span data-stu-id="3cc2d-126">Example</span></span>  
 <span data-ttu-id="3cc2d-127">L’exemple suivant illustre deux procédures qui acceptent une variable tableau et opèrent sur ses éléments.</span><span class="sxs-lookup"><span data-stu-id="3cc2d-127">The following example shows two procedures that take an array variable and operate on its elements.</span></span> <span data-ttu-id="3cc2d-128">Le `increase` procédure ajoute simplement la valeur&1; à chaque élément.</span><span class="sxs-lookup"><span data-stu-id="3cc2d-128">The `increase` procedure simply adds one to each element.</span></span> <span data-ttu-id="3cc2d-129">Le `replace` procédure assigne un nouveau tableau au paramètre `a()` , puis l’ajoute à chaque élément.</span><span class="sxs-lookup"><span data-stu-id="3cc2d-129">The `replace` procedure assigns a new array to the parameter `a()` and then adds one to each element.</span></span>  
  
 <span data-ttu-id="3cc2d-130">[!code-vb[VbVbcnProcedures&#35;](./codesnippet/VisualBasic/how-to-change-the-value-of-a-procedure-argument_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="3cc2d-130">[!code-vb[VbVbcnProcedures#35](./codesnippet/VisualBasic/how-to-change-the-value-of-a-procedure-argument_1.vb)]</span></span>  
  
 <span data-ttu-id="3cc2d-131">[!code-vb[VbVbcnProcedures n °&36;](./codesnippet/VisualBasic/how-to-change-the-value-of-a-procedure-argument_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="3cc2d-131">[!code-vb[VbVbcnProcedures#36](./codesnippet/VisualBasic/how-to-change-the-value-of-a-procedure-argument_2.vb)]</span></span>  
  
 <span data-ttu-id="3cc2d-132">[!code-vb[VbVbcnProcedures&#37;](./codesnippet/VisualBasic/how-to-change-the-value-of-a-procedure-argument_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="3cc2d-132">[!code-vb[VbVbcnProcedures#37](./codesnippet/VisualBasic/how-to-change-the-value-of-a-procedure-argument_3.vb)]</span></span>  
  
 <span data-ttu-id="3cc2d-133">Le premier `MsgBox` appel affiche « après Increase (n) : 11, 21, 31, 41 ».</span><span class="sxs-lookup"><span data-stu-id="3cc2d-133">The first `MsgBox` call displays "After increase(n): 11, 21, 31, 41".</span></span> <span data-ttu-id="3cc2d-134">Étant donné que le tableau `n` est un type référence, `replace` peut modifier ses membres, même si le mécanisme de passage est `ByVal`.</span><span class="sxs-lookup"><span data-stu-id="3cc2d-134">Because the array `n` is a reference type, `replace` can change its members, even though the passing mechanism is `ByVal`.</span></span>  
  
 <span data-ttu-id="3cc2d-135">La seconde `MsgBox` appel affiche « après Replace (n) : 101, 201, 301 ».</span><span class="sxs-lookup"><span data-stu-id="3cc2d-135">The second `MsgBox` call displays "After replace(n): 101, 201, 301".</span></span> <span data-ttu-id="3cc2d-136">Étant donné que `n` est passée `ByRef`, `replace` peut modifier la variable `n` dans le code appelant et affecter un nouveau tableau.</span><span class="sxs-lookup"><span data-stu-id="3cc2d-136">Because `n` is passed `ByRef`, `replace` can modify the variable `n` in the calling code and assign a new array to it.</span></span> <span data-ttu-id="3cc2d-137">Étant donné que `n` est un type référence, `replace` peut également modifier ses membres.</span><span class="sxs-lookup"><span data-stu-id="3cc2d-137">Because `n` is a reference type, `replace` can also change its members.</span></span>  
  
 <span data-ttu-id="3cc2d-138">Vous pouvez empêcher la procédure de modification de la variable elle-même dans le code appelant.</span><span class="sxs-lookup"><span data-stu-id="3cc2d-138">You can prevent the procedure from modifying the variable itself in the calling code.</span></span> <span data-ttu-id="3cc2d-139">Consultez la page [Comment : protéger un Argument de procédure contre les modifications de valeur](./how-to-protect-a-procedure-argument-against-value-changes.md).</span><span class="sxs-lookup"><span data-stu-id="3cc2d-139">See [How to: Protect a Procedure Argument Against Value Changes](./how-to-protect-a-procedure-argument-against-value-changes.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="3cc2d-140">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="3cc2d-140">Compiling the Code</span></span>  
 <span data-ttu-id="3cc2d-141">Lorsque vous passez une variable par référence, vous devez utiliser le `ByRef` (mot clé) pour spécifier ce mécanisme.</span><span class="sxs-lookup"><span data-stu-id="3cc2d-141">When you pass a variable by reference, you must use the `ByRef` keyword to specify this mechanism.</span></span>  
  
 <span data-ttu-id="3cc2d-142">La valeur par défaut dans [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] consiste à passer des arguments par valeur.</span><span class="sxs-lookup"><span data-stu-id="3cc2d-142">The default in [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] is to pass arguments by value.</span></span> <span data-ttu-id="3cc2d-143">Toutefois, il est conseillé de comprennent le [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) ou [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) mot-clé avec chaque paramètre déclaré.</span><span class="sxs-lookup"><span data-stu-id="3cc2d-143">However, it is good programming practice to include either the [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) keyword with every declared parameter.</span></span> <span data-ttu-id="3cc2d-144">Cela rend votre code plus facile à lire.</span><span class="sxs-lookup"><span data-stu-id="3cc2d-144">This makes your code easier to read.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="3cc2d-145">Sécurité .NET Framework</span><span class="sxs-lookup"><span data-stu-id="3cc2d-145">.NET Framework Security</span></span>  
 <span data-ttu-id="3cc2d-146">Il existe toujours un risque potentiel en autorisant une procédure modifier la valeur sous-jacente à un argument dans le code appelant.</span><span class="sxs-lookup"><span data-stu-id="3cc2d-146">There is always a potential risk in allowing a procedure to change the value underlying an argument in the calling code.</span></span> <span data-ttu-id="3cc2d-147">Assurez-vous que cette valeur pour être modifiée et préparez-vous à vérifier la validité avant de l’utiliser.</span><span class="sxs-lookup"><span data-stu-id="3cc2d-147">Make sure you expect this value to be changed, and be prepared to check it for validity before using it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cc2d-148">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3cc2d-148">See Also</span></span>  
 <span data-ttu-id="3cc2d-149">[Procédures](./index.md) </span><span class="sxs-lookup"><span data-stu-id="3cc2d-149">[Procedures](./index.md) </span></span>  
<span data-ttu-id="3cc2d-150"> [Arguments et paramètres de procédure](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="3cc2d-150"> [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="3cc2d-151"> [Comment : passer des Arguments à une procédure](./how-to-pass-arguments-to-a-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="3cc2d-151"> [How to: Pass Arguments to a Procedure](./how-to-pass-arguments-to-a-procedure.md) </span></span>  
<span data-ttu-id="3cc2d-152"> [Passage des Arguments par valeur et par référence](./passing-arguments-by-value-and-by-reference.md) </span><span class="sxs-lookup"><span data-stu-id="3cc2d-152"> [Passing Arguments by Value and by Reference](./passing-arguments-by-value-and-by-reference.md) </span></span>  
<span data-ttu-id="3cc2d-153"> [Différences entre les Arguments modifiables et non modifiables](./differences-between-modifiable-and-nonmodifiable-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="3cc2d-153"> [Differences Between Modifiable and Nonmodifiable Arguments](./differences-between-modifiable-and-nonmodifiable-arguments.md) </span></span>  
<span data-ttu-id="3cc2d-154"> [Différences entre le passage d’un Argument par valeur et par référence](./differences-between-passing-an-argument-by-value-and-by-reference.md) </span><span class="sxs-lookup"><span data-stu-id="3cc2d-154"> [Differences Between Passing an Argument By Value and By Reference](./differences-between-passing-an-argument-by-value-and-by-reference.md) </span></span>  
<span data-ttu-id="3cc2d-155"> [Comment : protéger un Argument de procédure contre les modifications de valeur](./how-to-protect-a-procedure-argument-against-value-changes.md) </span><span class="sxs-lookup"><span data-stu-id="3cc2d-155"> [How to: Protect a Procedure Argument Against Value Changes](./how-to-protect-a-procedure-argument-against-value-changes.md) </span></span>  
<span data-ttu-id="3cc2d-156"> [Comment : forcer un Argument à passer par valeur](./how-to-force-an-argument-to-be-passed-by-value.md) </span><span class="sxs-lookup"><span data-stu-id="3cc2d-156"> [How to: Force an Argument to Be Passed by Value](./how-to-force-an-argument-to-be-passed-by-value.md) </span></span>  
<span data-ttu-id="3cc2d-157"> [Passage des Arguments par Position et par nom](./passing-arguments-by-position-and-by-name.md) </span><span class="sxs-lookup"><span data-stu-id="3cc2d-157"> [Passing Arguments by Position and by Name](./passing-arguments-by-position-and-by-name.md) </span></span>  
<span data-ttu-id="3cc2d-158"> [Types valeur et types référence](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)</span><span class="sxs-lookup"><span data-stu-id="3cc2d-158"> [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)</span></span>
