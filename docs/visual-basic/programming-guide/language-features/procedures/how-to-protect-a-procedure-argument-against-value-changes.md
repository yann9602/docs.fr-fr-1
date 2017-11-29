---
title: "Comment : protéger un argument de procédure contre les modifications de valeur (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- procedure arguments
- arguments [Visual Basic], passing by reference
- Visual Basic code, procedures
- arguments [Visual Basic], ByVal
- arguments [Visual Basic], passing by value
- procedure parameters
- procedures [Visual Basic], calling
- arguments [Visual Basic], ByRef
- arguments [Visual Basic], changing value
ms.assetid: d2b7c766-ce16-4d2c-8d79-3fc0e7ba2227
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7975cbbc38c39223a4af5c87ac6bb090be548f2d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-protect-a-procedure-argument-against-value-changes-visual-basic"></a><span data-ttu-id="8d385-102">Comment : protéger un argument de procédure contre les modifications de valeur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8d385-102">How to: Protect a Procedure Argument Against Value Changes (Visual Basic)</span></span>
<span data-ttu-id="8d385-103">Si une procédure déclare un paramètre comme [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] donne le code de procédure une référence directe à l’élément de programmation sous-jacent à l’argument dans le code appelant.</span><span class="sxs-lookup"><span data-stu-id="8d385-103">If a procedure declares a parameter as [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] gives the procedure code a direct reference to the programming element underlying the argument in the calling code.</span></span> <span data-ttu-id="8d385-104">Cela permet à la procédure pour modifier la valeur sous-jacente à l’argument dans le code appelant.</span><span class="sxs-lookup"><span data-stu-id="8d385-104">This permits the procedure to change the value underlying the argument in the calling code.</span></span> <span data-ttu-id="8d385-105">Dans certains cas, le code appelant souhaiteriez pour vous protéger contre une telle modification.</span><span class="sxs-lookup"><span data-stu-id="8d385-105">In some cases the calling code might want to protect against such a change.</span></span>  
  
 <span data-ttu-id="8d385-106">Vous pouvez toujours protéger un argument de modification en déclarant le paramètre correspondant [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) dans la procédure.</span><span class="sxs-lookup"><span data-stu-id="8d385-106">You can always protect an argument from change by declaring the corresponding parameter [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) in the procedure.</span></span> <span data-ttu-id="8d385-107">Si vous souhaitez être en mesure de modifier un argument donné dans certains cas, mais pas d’autres, vous pouvez la déclarer `ByRef` et laisser le code appelant déterminer le mécanisme de passage dans chaque appel.</span><span class="sxs-lookup"><span data-stu-id="8d385-107">If you want to be able to change a given argument in some cases but not others, you can declare it `ByRef` and let the calling code determine the passing mechanism in each call.</span></span> <span data-ttu-id="8d385-108">Cela en mettant l’argument correspondant entre parenthèses pour le passer par valeur, ou en mettant ne pas entre parenthèses pour le passer par référence.</span><span class="sxs-lookup"><span data-stu-id="8d385-108">It does this by enclosing the corresponding argument in parentheses to pass it by value, or not enclosing it in parentheses to pass it by reference.</span></span> <span data-ttu-id="8d385-109">Pour plus d’informations, consultez [Comment : forcer un Argument à passer par valeur](./how-to-force-an-argument-to-be-passed-by-value.md).</span><span class="sxs-lookup"><span data-stu-id="8d385-109">For more information, see [How to: Force an Argument to Be Passed by Value](./how-to-force-an-argument-to-be-passed-by-value.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8d385-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="8d385-110">Example</span></span>  
 <span data-ttu-id="8d385-111">L’exemple suivant illustre deux procédures qui acceptent une variable tableau et opèrent sur ses éléments.</span><span class="sxs-lookup"><span data-stu-id="8d385-111">The following example shows two procedures that take an array variable and operate on its elements.</span></span> <span data-ttu-id="8d385-112">Le `increase` procédure ajoute simplement la valeur 1 à chaque élément.</span><span class="sxs-lookup"><span data-stu-id="8d385-112">The `increase` procedure simply adds one to each element.</span></span> <span data-ttu-id="8d385-113">Le `replace` procédure assigne un nouveau tableau au paramètre `a()` , puis ajoute 1 à chaque élément.</span><span class="sxs-lookup"><span data-stu-id="8d385-113">The `replace` procedure assigns a new array to the parameter `a()` and then adds one to each element.</span></span> <span data-ttu-id="8d385-114">Toutefois, la réaffectation n’affecte pas la variable tableau sous-jacente dans le code appelant.</span><span class="sxs-lookup"><span data-stu-id="8d385-114">However, the reassignment does not affect the underlying array variable in the calling code.</span></span>  
  
 [!code-vb[VbVbcnProcedures#35](./codesnippet/VisualBasic/how-to-protect-a-procedure-argument-against-value-changes_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#38](./codesnippet/VisualBasic/how-to-protect-a-procedure-argument-against-value-changes_2.vb)]  
  
 [!code-vb[VbVbcnProcedures#37](./codesnippet/VisualBasic/how-to-protect-a-procedure-argument-against-value-changes_3.vb)]  
  
 <span data-ttu-id="8d385-115">Le premier `MsgBox` appel affiche « après Increase (n) : 11, 21, 31, 41 ».</span><span class="sxs-lookup"><span data-stu-id="8d385-115">The first `MsgBox` call displays "After increase(n): 11, 21, 31, 41".</span></span> <span data-ttu-id="8d385-116">Étant donné que le tableau `n` est un type référence, `replace` peut modifier ses membres, même si le mécanisme de passage est `ByVal`.</span><span class="sxs-lookup"><span data-stu-id="8d385-116">Because the array `n` is a reference type, `replace` can change its members, even though the passing mechanism is `ByVal`.</span></span>  
  
 <span data-ttu-id="8d385-117">La seconde `MsgBox` appel affiche « après Replace (n) : 11, 21, 31, 41 ».</span><span class="sxs-lookup"><span data-stu-id="8d385-117">The second `MsgBox` call displays "After replace(n): 11, 21, 31, 41".</span></span> <span data-ttu-id="8d385-118">Étant donné que `n` est passé `ByVal`, `replace` ne peut pas modifier la variable `n` dans le code appelant en lui assignant un nouveau tableau.</span><span class="sxs-lookup"><span data-stu-id="8d385-118">Because `n` is passed `ByVal`, `replace` cannot modify the variable `n` in the calling code by assigning a new array to it.</span></span> <span data-ttu-id="8d385-119">Lorsque `replace` crée la nouvelle instance de tableau `k` et l’assigne à la variable locale `a`, il perd la référence à `n` transmis par le code appelant.</span><span class="sxs-lookup"><span data-stu-id="8d385-119">When `replace` creates the new array instance `k` and assigns it to the local variable `a`, it loses the reference to `n` passed in by the calling code.</span></span> <span data-ttu-id="8d385-120">Lorsqu’il modifie les membres de `a`, seul le tableau local `k` est affectée.</span><span class="sxs-lookup"><span data-stu-id="8d385-120">When it changes the members of `a`, only the local array `k` is affected.</span></span> <span data-ttu-id="8d385-121">Par conséquent, `replace` n’incrémente pas les valeurs du tableau `n` dans le code appelant.</span><span class="sxs-lookup"><span data-stu-id="8d385-121">Therefore, `replace` does not increment the values of array `n` in the calling code.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8d385-122">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="8d385-122">Compiling the Code</span></span>  
 <span data-ttu-id="8d385-123">La valeur par défaut dans [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] consiste à passer des arguments par valeur.</span><span class="sxs-lookup"><span data-stu-id="8d385-123">The default in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] is to pass arguments by value.</span></span> <span data-ttu-id="8d385-124">Toutefois, il est conseillé pour inclure la [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) ou [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) mot clé with chaque paramètre déclaré.</span><span class="sxs-lookup"><span data-stu-id="8d385-124">However, it is good programming practice to include either the [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) keyword with every declared parameter.</span></span> <span data-ttu-id="8d385-125">Cela rend votre code plus facile à lire.</span><span class="sxs-lookup"><span data-stu-id="8d385-125">This makes your code easier to read.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d385-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8d385-126">See Also</span></span>  
 [<span data-ttu-id="8d385-127">Procédures</span><span class="sxs-lookup"><span data-stu-id="8d385-127">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="8d385-128">Paramètres et arguments d’une procédure</span><span class="sxs-lookup"><span data-stu-id="8d385-128">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="8d385-129">Guide pratique : passer des arguments à une procédure</span><span class="sxs-lookup"><span data-stu-id="8d385-129">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)  
 [<span data-ttu-id="8d385-130">Passage d’un argument par valeur et par référence</span><span class="sxs-lookup"><span data-stu-id="8d385-130">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)  
 [<span data-ttu-id="8d385-131">Différences entre les arguments modifiables et non modifiables</span><span class="sxs-lookup"><span data-stu-id="8d385-131">Differences Between Modifiable and Nonmodifiable Arguments</span></span>](./differences-between-modifiable-and-nonmodifiable-arguments.md)  
 [<span data-ttu-id="8d385-132">Différences entre le passage d’un argument par valeur et par référence</span><span class="sxs-lookup"><span data-stu-id="8d385-132">Differences Between Passing an Argument By Value and By Reference</span></span>](./differences-between-passing-an-argument-by-value-and-by-reference.md)  
 [<span data-ttu-id="8d385-133">Guide pratique : modifier la valeur d’un argument de la procédure</span><span class="sxs-lookup"><span data-stu-id="8d385-133">How to: Change the Value of a Procedure Argument</span></span>](./how-to-change-the-value-of-a-procedure-argument.md)  
 [<span data-ttu-id="8d385-134">Guide pratique : forcer le passage d’un argument par valeur</span><span class="sxs-lookup"><span data-stu-id="8d385-134">How to: Force an Argument to Be Passed by Value</span></span>](./how-to-force-an-argument-to-be-passed-by-value.md)  
 [<span data-ttu-id="8d385-135">Passage des arguments par position et par nom</span><span class="sxs-lookup"><span data-stu-id="8d385-135">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)  
 [<span data-ttu-id="8d385-136">Types valeur et types référence</span><span class="sxs-lookup"><span data-stu-id="8d385-136">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
