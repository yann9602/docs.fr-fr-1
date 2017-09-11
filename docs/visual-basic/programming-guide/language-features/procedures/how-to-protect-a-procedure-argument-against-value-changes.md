---
title: "Comment : protéger un Argument de procédure contre les modifications de valeur (Visual Basic) | Documents Microsoft"
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
- procedures, calling
- arguments [Visual Basic], ByRef
- arguments [Visual Basic], changing value
ms.assetid: d2b7c766-ce16-4d2c-8d79-3fc0e7ba2227
caps.latest.revision: 14
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
ms.openlocfilehash: db40b3426256e7789a5273ab4d0afc8d5b47c8a7
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-protect-a-procedure-argument-against-value-changes-visual-basic"></a><span data-ttu-id="2ad24-102">Comment : protéger un argument de procédure contre les modifications de valeur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2ad24-102">How to: Protect a Procedure Argument Against Value Changes (Visual Basic)</span></span>
<span data-ttu-id="2ad24-103">Si une procédure déclare un paramètre comme [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] donne le code de procédure une référence directe à l’élément de programmation sous-jacent à l’argument dans le code appelant.</span><span class="sxs-lookup"><span data-stu-id="2ad24-103">If a procedure declares a parameter as [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] gives the procedure code a direct reference to the programming element underlying the argument in the calling code.</span></span> <span data-ttu-id="2ad24-104">Cela permet à la procédure pour modifier la valeur sous-jacente à l’argument dans le code appelant.</span><span class="sxs-lookup"><span data-stu-id="2ad24-104">This permits the procedure to change the value underlying the argument in the calling code.</span></span> <span data-ttu-id="2ad24-105">Dans certains cas, le code appelant souhaiteriez pour vous protéger contre une telle modification.</span><span class="sxs-lookup"><span data-stu-id="2ad24-105">In some cases the calling code might want to protect against such a change.</span></span>  
  
 <span data-ttu-id="2ad24-106">Vous pouvez toujours protéger un argument d’une modification en déclarant le paramètre correspondant [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) dans la procédure.</span><span class="sxs-lookup"><span data-stu-id="2ad24-106">You can always protect an argument from change by declaring the corresponding parameter [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) in the procedure.</span></span> <span data-ttu-id="2ad24-107">Si vous souhaitez être en mesure de modifier un argument donné dans certains cas, mais pas d’autres, vous pouvez le déclarer `ByRef` et laisser le code appelant déterminer le mécanisme de passage pour chaque appel.</span><span class="sxs-lookup"><span data-stu-id="2ad24-107">If you want to be able to change a given argument in some cases but not others, you can declare it `ByRef` and let the calling code determine the passing mechanism in each call.</span></span> <span data-ttu-id="2ad24-108">Cela en mettant l’argument correspondant entre parenthèses pour le passer par valeur, ou en mettant ne pas entre parenthèses pour le passer par référence.</span><span class="sxs-lookup"><span data-stu-id="2ad24-108">It does this by enclosing the corresponding argument in parentheses to pass it by value, or not enclosing it in parentheses to pass it by reference.</span></span> <span data-ttu-id="2ad24-109">Pour plus d’informations, consultez [Comment : forcer un Argument à passer par valeur](./how-to-force-an-argument-to-be-passed-by-value.md).</span><span class="sxs-lookup"><span data-stu-id="2ad24-109">For more information, see [How to: Force an Argument to Be Passed by Value](./how-to-force-an-argument-to-be-passed-by-value.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2ad24-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="2ad24-110">Example</span></span>  
 <span data-ttu-id="2ad24-111">L’exemple suivant illustre deux procédures qui acceptent une variable tableau et opèrent sur ses éléments.</span><span class="sxs-lookup"><span data-stu-id="2ad24-111">The following example shows two procedures that take an array variable and operate on its elements.</span></span> <span data-ttu-id="2ad24-112">Le `increase` procédure ajoute simplement la valeur&1; à chaque élément.</span><span class="sxs-lookup"><span data-stu-id="2ad24-112">The `increase` procedure simply adds one to each element.</span></span> <span data-ttu-id="2ad24-113">Le `replace` procédure assigne un nouveau tableau au paramètre `a()` , puis l’ajoute à chaque élément.</span><span class="sxs-lookup"><span data-stu-id="2ad24-113">The `replace` procedure assigns a new array to the parameter `a()` and then adds one to each element.</span></span> <span data-ttu-id="2ad24-114">Toutefois, la réaffectation n’affecte pas la variable tableau sous-jacente dans le code appelant.</span><span class="sxs-lookup"><span data-stu-id="2ad24-114">However, the reassignment does not affect the underlying array variable in the calling code.</span></span>  
  
 <span data-ttu-id="2ad24-115">[!code-vb[VbVbcnProcedures&#35;](./codesnippet/VisualBasic/how-to-protect-a-procedure-argument-against-value-changes_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="2ad24-115">[!code-vb[VbVbcnProcedures#35](./codesnippet/VisualBasic/how-to-protect-a-procedure-argument-against-value-changes_1.vb)]</span></span>  
  
 <span data-ttu-id="2ad24-116">[!code-vb[VbVbcnProcedures&#38;](./codesnippet/VisualBasic/how-to-protect-a-procedure-argument-against-value-changes_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="2ad24-116">[!code-vb[VbVbcnProcedures#38](./codesnippet/VisualBasic/how-to-protect-a-procedure-argument-against-value-changes_2.vb)]</span></span>  
  
 <span data-ttu-id="2ad24-117">[!code-vb[VbVbcnProcedures&#37;](./codesnippet/VisualBasic/how-to-protect-a-procedure-argument-against-value-changes_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="2ad24-117">[!code-vb[VbVbcnProcedures#37](./codesnippet/VisualBasic/how-to-protect-a-procedure-argument-against-value-changes_3.vb)]</span></span>  
  
 <span data-ttu-id="2ad24-118">Le premier `MsgBox` appel affiche « après Increase (n) : 11, 21, 31, 41 ».</span><span class="sxs-lookup"><span data-stu-id="2ad24-118">The first `MsgBox` call displays "After increase(n): 11, 21, 31, 41".</span></span> <span data-ttu-id="2ad24-119">Étant donné que le tableau `n` est un type référence, `replace` peut modifier ses membres, même si le mécanisme de passage est `ByVal`.</span><span class="sxs-lookup"><span data-stu-id="2ad24-119">Because the array `n` is a reference type, `replace` can change its members, even though the passing mechanism is `ByVal`.</span></span>  
  
 <span data-ttu-id="2ad24-120">La seconde `MsgBox` appel affiche « après Replace (n) : 11, 21, 31, 41 ».</span><span class="sxs-lookup"><span data-stu-id="2ad24-120">The second `MsgBox` call displays "After replace(n): 11, 21, 31, 41".</span></span> <span data-ttu-id="2ad24-121">Étant donné que `n` est passée `ByVal`, `replace` ne peut pas modifier la variable `n` dans le code appelant en lui assignant un nouveau tableau.</span><span class="sxs-lookup"><span data-stu-id="2ad24-121">Because `n` is passed `ByVal`, `replace` cannot modify the variable `n` in the calling code by assigning a new array to it.</span></span> <span data-ttu-id="2ad24-122">Lors de la `replace` crée la nouvelle instance de tableau `k` et l’assigne à la variable locale `a`, il perd la référence à `n` passée par le code appelant.</span><span class="sxs-lookup"><span data-stu-id="2ad24-122">When `replace` creates the new array instance `k` and assigns it to the local variable `a`, it loses the reference to `n` passed in by the calling code.</span></span> <span data-ttu-id="2ad24-123">Lorsqu’il modifie les membres de `a`, seul le tableau local `k` est affecté.</span><span class="sxs-lookup"><span data-stu-id="2ad24-123">When it changes the members of `a`, only the local array `k` is affected.</span></span> <span data-ttu-id="2ad24-124">Par conséquent, `replace` n’incrémente pas les valeurs du tableau `n` dans le code appelant.</span><span class="sxs-lookup"><span data-stu-id="2ad24-124">Therefore, `replace` does not increment the values of array `n` in the calling code.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2ad24-125">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="2ad24-125">Compiling the Code</span></span>  
 <span data-ttu-id="2ad24-126">La valeur par défaut dans [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] consiste à passer des arguments par valeur.</span><span class="sxs-lookup"><span data-stu-id="2ad24-126">The default in [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] is to pass arguments by value.</span></span> <span data-ttu-id="2ad24-127">Toutefois, il est conseillé de comprennent le [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) ou [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) mot-clé avec chaque paramètre déclaré.</span><span class="sxs-lookup"><span data-stu-id="2ad24-127">However, it is good programming practice to include either the [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) keyword with every declared parameter.</span></span> <span data-ttu-id="2ad24-128">Cela rend votre code plus facile à lire.</span><span class="sxs-lookup"><span data-stu-id="2ad24-128">This makes your code easier to read.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ad24-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2ad24-129">See Also</span></span>  
 <span data-ttu-id="2ad24-130">[Procédures](./index.md) </span><span class="sxs-lookup"><span data-stu-id="2ad24-130">[Procedures](./index.md) </span></span>  
<span data-ttu-id="2ad24-131"> [Arguments et paramètres de procédure](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="2ad24-131"> [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="2ad24-132"> [Comment : passer des Arguments à une procédure](./how-to-pass-arguments-to-a-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="2ad24-132"> [How to: Pass Arguments to a Procedure](./how-to-pass-arguments-to-a-procedure.md) </span></span>  
<span data-ttu-id="2ad24-133"> [Passage des Arguments par valeur et par référence](./passing-arguments-by-value-and-by-reference.md) </span><span class="sxs-lookup"><span data-stu-id="2ad24-133"> [Passing Arguments by Value and by Reference](./passing-arguments-by-value-and-by-reference.md) </span></span>  
<span data-ttu-id="2ad24-134"> [Différences entre les Arguments modifiables et non modifiables](./differences-between-modifiable-and-nonmodifiable-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="2ad24-134"> [Differences Between Modifiable and Nonmodifiable Arguments](./differences-between-modifiable-and-nonmodifiable-arguments.md) </span></span>  
<span data-ttu-id="2ad24-135"> [Différences entre le passage d’un Argument par valeur et par référence](./differences-between-passing-an-argument-by-value-and-by-reference.md) </span><span class="sxs-lookup"><span data-stu-id="2ad24-135"> [Differences Between Passing an Argument By Value and By Reference](./differences-between-passing-an-argument-by-value-and-by-reference.md) </span></span>  
<span data-ttu-id="2ad24-136"> [Comment : modifier la valeur d’un Argument de procédure](./how-to-change-the-value-of-a-procedure-argument.md) </span><span class="sxs-lookup"><span data-stu-id="2ad24-136"> [How to: Change the Value of a Procedure Argument](./how-to-change-the-value-of-a-procedure-argument.md) </span></span>  
<span data-ttu-id="2ad24-137"> [Comment : forcer un Argument à passer par valeur](./how-to-force-an-argument-to-be-passed-by-value.md) </span><span class="sxs-lookup"><span data-stu-id="2ad24-137"> [How to: Force an Argument to Be Passed by Value](./how-to-force-an-argument-to-be-passed-by-value.md) </span></span>  
<span data-ttu-id="2ad24-138"> [Passage des Arguments par Position et par nom](./passing-arguments-by-position-and-by-name.md) </span><span class="sxs-lookup"><span data-stu-id="2ad24-138"> [Passing Arguments by Position and by Name](./passing-arguments-by-position-and-by-name.md) </span></span>  
<span data-ttu-id="2ad24-139"> [Types valeur et types référence](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)</span><span class="sxs-lookup"><span data-stu-id="2ad24-139"> [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)</span></span>
