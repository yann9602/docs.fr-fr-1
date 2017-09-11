---
title: "Passage des Arguments par valeur et par référence (Visual Basic) | Documents Microsoft"
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
- ByRef keyword, passing arguments by reference
- Visual Basic code, procedures
- passing arguments, by value or by reference
- ByVal keyword, passing arguments by value
- arguments [Visual Basic], passing by value or by reference
- argument passing, by value or by reference
ms.assetid: fd8a9de6-7178-44d5-a9bf-458d4ad907c2
caps.latest.revision: 23
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
ms.openlocfilehash: 44107171d6f24e22614788470c65cf7ad8d28640
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="passing-arguments-by-value-and-by-reference-visual-basic"></a><span data-ttu-id="b99e1-102">Passage d’un argument par valeur et par référence (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b99e1-102">Passing Arguments by Value and by Reference (Visual Basic)</span></span>
<span data-ttu-id="b99e1-103">Dans [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], vous pouvez passer un argument à une procédure *par valeur* ou *par référence*.</span><span class="sxs-lookup"><span data-stu-id="b99e1-103">In [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], you can pass an argument to a procedure *by value* or *by reference*.</span></span> <span data-ttu-id="b99e1-104">Il s’agit du *mécanisme de transmission*, et détermine si la procédure peut modifier l’élément de programmation sous-jacent à l’argument dans le code appelant.</span><span class="sxs-lookup"><span data-stu-id="b99e1-104">This is known as the *passing mechanism*, and it determines whether the procedure can modify the programming element underlying the argument in the calling code.</span></span> <span data-ttu-id="b99e1-105">La déclaration de procédure détermine le mécanisme de passage pour chaque paramètre en spécifiant le [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) ou [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) (mot clé).</span><span class="sxs-lookup"><span data-stu-id="b99e1-105">The procedure declaration determines the passing mechanism for each parameter by specifying the [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) keyword.</span></span>  
  
## <a name="distinctions"></a><span data-ttu-id="b99e1-106">Distinctions</span><span class="sxs-lookup"><span data-stu-id="b99e1-106">Distinctions</span></span>  
 <span data-ttu-id="b99e1-107">Lors du passage d’un argument à une procédure, tenez compte des diverses distinctions qui interagissent entre eux :</span><span class="sxs-lookup"><span data-stu-id="b99e1-107">When passing an argument to a procedure, be aware of several different distinctions that interact with each other:</span></span>  
  
-   <span data-ttu-id="b99e1-108">Si l’élément de programmation sous-jacent est modifiable ou non modifiable</span><span class="sxs-lookup"><span data-stu-id="b99e1-108">Whether the underlying programming element is modifiable or nonmodifiable</span></span>  
  
-   <span data-ttu-id="b99e1-109">Si l’argument lui-même est modifiable ou non modifiable</span><span class="sxs-lookup"><span data-stu-id="b99e1-109">Whether the argument itself is modifiable or nonmodifiable</span></span>  
  
-   <span data-ttu-id="b99e1-110">Si l’argument est passé par valeur ou par référence</span><span class="sxs-lookup"><span data-stu-id="b99e1-110">Whether the argument is being passed by value or by reference</span></span>  
  
-   <span data-ttu-id="b99e1-111">Si le type de données d’argument est un type valeur ou un type référence</span><span class="sxs-lookup"><span data-stu-id="b99e1-111">Whether the argument data type is a value type or a reference type</span></span>  
  
 <span data-ttu-id="b99e1-112">Pour plus d’informations, consultez [différences entre modifiables et non modifiables Arguments](./differences-between-modifiable-and-nonmodifiable-arguments.md) et [différences entre passage d’un Argument par valeur et par référence](./differences-between-passing-an-argument-by-value-and-by-reference.md).</span><span class="sxs-lookup"><span data-stu-id="b99e1-112">For more information, see [Differences Between Modifiable and Nonmodifiable Arguments](./differences-between-modifiable-and-nonmodifiable-arguments.md) and [Differences Between Passing an Argument By Value and By Reference](./differences-between-passing-an-argument-by-value-and-by-reference.md).</span></span>  
  
## <a name="choice-of-passing-mechanism"></a><span data-ttu-id="b99e1-113">Choix du mécanisme de transmission</span><span class="sxs-lookup"><span data-stu-id="b99e1-113">Choice of Passing Mechanism</span></span>  
 <span data-ttu-id="b99e1-114">Vous devez choisir avec soin pour chaque argument, le mécanisme de passage.</span><span class="sxs-lookup"><span data-stu-id="b99e1-114">You should choose the passing mechanism carefully for each argument.</span></span>  
  
-   <span data-ttu-id="b99e1-115">**Protection**.</span><span class="sxs-lookup"><span data-stu-id="b99e1-115">**Protection**.</span></span> <span data-ttu-id="b99e1-116">Dans le choix entre les deux mécanismes de transfert, le critère le plus important est l’exposition de l’appel de variables à modifier.</span><span class="sxs-lookup"><span data-stu-id="b99e1-116">In choosing between the two passing mechanisms, the most important criterion is the exposure of calling variables to change.</span></span> <span data-ttu-id="b99e1-117">L’avantage de passage d’un argument `ByRef` est que la procédure peut retourner une valeur au code appelant via cet argument.</span><span class="sxs-lookup"><span data-stu-id="b99e1-117">The advantage of passing an argument `ByRef` is that the procedure can return a value to the calling code through that argument.</span></span> <span data-ttu-id="b99e1-118">L’avantage de passage d’un argument `ByVal` permet d’empêcher une variable d’être modifiée par la procédure.</span><span class="sxs-lookup"><span data-stu-id="b99e1-118">The advantage of passing an argument `ByVal` is that it protects a variable from being changed by the procedure.</span></span>  
  
-   <span data-ttu-id="b99e1-119">**Performances**.</span><span class="sxs-lookup"><span data-stu-id="b99e1-119">**Performance**.</span></span> <span data-ttu-id="b99e1-120">Bien que le mécanisme de passage peut affecter les performances de votre code, la différence est généralement insignifiante.</span><span class="sxs-lookup"><span data-stu-id="b99e1-120">Although the passing mechanism can affect the performance of your code, the difference is usually insignificant.</span></span> <span data-ttu-id="b99e1-121">Une exception à cela est un type de valeur passé `ByVal`.</span><span class="sxs-lookup"><span data-stu-id="b99e1-121">One exception to this is a value type passed `ByVal`.</span></span> <span data-ttu-id="b99e1-122">Dans ce cas, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] copie le contenu de l’ensemble des données de l’argument.</span><span class="sxs-lookup"><span data-stu-id="b99e1-122">In this case, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] copies the entire data contents of the argument.</span></span> <span data-ttu-id="b99e1-123">Par conséquent, pour un type de valeur volumineux comme une structure, il peut être plus efficace de passer `ByRef`.</span><span class="sxs-lookup"><span data-stu-id="b99e1-123">Therefore, for a large value type such as a structure, it can be more efficient to pass it `ByRef`.</span></span>  
  
     <span data-ttu-id="b99e1-124">Pour les types référence, seul le pointeur vers les données est copié (quatre octets sur les plateformes 32 bits, huit octets sur les plateformes 64 bits).</span><span class="sxs-lookup"><span data-stu-id="b99e1-124">For reference types, only the pointer to the data is copied (four bytes on 32-bit platforms, eight bytes on 64-bit platforms).</span></span> <span data-ttu-id="b99e1-125">Par conséquent, vous pouvez passer des arguments de type `String` ou `Object` par valeur sans nuire aux performances.</span><span class="sxs-lookup"><span data-stu-id="b99e1-125">Therefore, you can pass arguments of type `String` or `Object` by value without harming performance.</span></span>  
  
## <a name="determination-of-the-passing-mechanism"></a><span data-ttu-id="b99e1-126">Détermination du mécanisme de transmission</span><span class="sxs-lookup"><span data-stu-id="b99e1-126">Determination of the Passing Mechanism</span></span>  
 <span data-ttu-id="b99e1-127">La déclaration de procédure spécifie le mécanisme de passage pour chaque paramètre.</span><span class="sxs-lookup"><span data-stu-id="b99e1-127">The procedure declaration specifies the passing mechanism for each parameter.</span></span> <span data-ttu-id="b99e1-128">Le code appelant ne peut pas remplacer un `ByVal` mécanisme.</span><span class="sxs-lookup"><span data-stu-id="b99e1-128">The calling code can't override a `ByVal` mechanism.</span></span>  
  
 <span data-ttu-id="b99e1-129">Si un paramètre est déclaré avec `ByRef`, le code appelant peut forcer le mécanisme à `ByVal` en mettant le nom de l’argument entre parenthèses dans l’appel.</span><span class="sxs-lookup"><span data-stu-id="b99e1-129">If a parameter is declared with `ByRef`, the calling code can force the mechanism to `ByVal` by enclosing the argument name in parentheses in the call.</span></span> <span data-ttu-id="b99e1-130">Pour plus d’informations, consultez [Comment : forcer un Argument à passer par valeur](./how-to-force-an-argument-to-be-passed-by-value.md).</span><span class="sxs-lookup"><span data-stu-id="b99e1-130">For more information, see [How to: Force an Argument to Be Passed by Value](./how-to-force-an-argument-to-be-passed-by-value.md).</span></span>  
  
 <span data-ttu-id="b99e1-131">La valeur par défaut dans [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] consiste à passer des arguments par valeur.</span><span class="sxs-lookup"><span data-stu-id="b99e1-131">The default in [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] is to pass arguments by value.</span></span>  
  
## <a name="when-to-pass-an-argument-by-value"></a><span data-ttu-id="b99e1-132">Quand passer un Argument par valeur</span><span class="sxs-lookup"><span data-stu-id="b99e1-132">When to Pass an Argument by Value</span></span>  
  
-   <span data-ttu-id="b99e1-133">Si l’élément de code appelant sous-jacent à l’argument est un élément non modifiable, déclarez le paramètre correspondant [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).</span><span class="sxs-lookup"><span data-stu-id="b99e1-133">If the calling code element underlying the argument is a nonmodifiable element, declare the corresponding parameter [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).</span></span> <span data-ttu-id="b99e1-134">Aucun code ne peut modifier la valeur d’un élément non modifiable.</span><span class="sxs-lookup"><span data-stu-id="b99e1-134">No code can change the value of a nonmodifiable element.</span></span>  
  
-   <span data-ttu-id="b99e1-135">Si l’élément sous-jacent est modifiable, mais vous ne souhaitez pas que la procédure puisse modifier sa valeur, déclarez le paramètre `ByVal`.</span><span class="sxs-lookup"><span data-stu-id="b99e1-135">If the underlying element is modifiable, but you do not want the procedure to be able to change its value, declare the parameter `ByVal`.</span></span> <span data-ttu-id="b99e1-136">Seul le code appelant peut modifier la valeur d’un élément modifiable passée par valeur.</span><span class="sxs-lookup"><span data-stu-id="b99e1-136">Only the calling code can change the value of a modifiable element passed by value.</span></span>  
  
## <a name="when-to-pass-an-argument-by-reference"></a><span data-ttu-id="b99e1-137">Quand passer un Argument par référence</span><span class="sxs-lookup"><span data-stu-id="b99e1-137">When to Pass an Argument by Reference</span></span>  
  
-   <span data-ttu-id="b99e1-138">Si la procédure nécessite véritablement à modifier l’élément sous-jacent dans le code appelant, déclarez le paramètre correspondant [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md).</span><span class="sxs-lookup"><span data-stu-id="b99e1-138">If the procedure has a genuine need to change the underlying element in the calling code, declare the corresponding parameter [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md).</span></span>  
  
-   <span data-ttu-id="b99e1-139">Si l’exécution correcte du code dépend de la procédure modifiant l’élément sous-jacent dans le code appelant, déclarez le paramètre `ByRef`.</span><span class="sxs-lookup"><span data-stu-id="b99e1-139">If the correct execution of the code depends on the procedure changing the underlying element in the calling code, declare the parameter `ByRef`.</span></span> <span data-ttu-id="b99e1-140">Si vous le passez par valeur ou si le code appelant substitue le `ByRef` mécanisme de transmission en mettant l’argument entre parenthèses, l’appel de procédure peut produire des résultats inattendus.</span><span class="sxs-lookup"><span data-stu-id="b99e1-140">If you pass it by value, or if the calling code overrides the `ByRef` passing mechanism by enclosing the argument in parentheses, the procedure call might produce unexpected results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b99e1-141">Exemple</span><span class="sxs-lookup"><span data-stu-id="b99e1-141">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="b99e1-142">Description</span><span class="sxs-lookup"><span data-stu-id="b99e1-142">Description</span></span>  
 <span data-ttu-id="b99e1-143">L’exemple suivant illustre quand passer des arguments par valeur et les passer par référence.</span><span class="sxs-lookup"><span data-stu-id="b99e1-143">The following example illustrates when to pass arguments by value and when to pass them by reference.</span></span> <span data-ttu-id="b99e1-144">Procédure `Calculate` possède à la fois un `ByVal` et un `ByRef` paramètre.</span><span class="sxs-lookup"><span data-stu-id="b99e1-144">Procedure `Calculate` has both a `ByVal` and a `ByRef` parameter.</span></span> <span data-ttu-id="b99e1-145">Étant donné un taux d’intérêt, `rate`et la somme d’argent, `debt`, la tâche de la procédure consiste à calculer une nouvelle valeur pour `debt` qui est le résultat de l’application du taux d’intérêt à la valeur d’origine de `debt`.</span><span class="sxs-lookup"><span data-stu-id="b99e1-145">Given an interest rate, `rate`, and a sum of money, `debt`, the task of the procedure is to calculate a new value for `debt` that is the result of applying the interest rate to the original value of `debt`.</span></span> <span data-ttu-id="b99e1-146">Étant donné que `debt` est un `ByRef` paramètre, le nouveau total est représenté dans la valeur de l’argument dans le code appelant qui correspond à `debt`.</span><span class="sxs-lookup"><span data-stu-id="b99e1-146">Because `debt` is a `ByRef` parameter, the new total is reflected in the value of the argument in the calling code that corresponds to `debt`.</span></span> <span data-ttu-id="b99e1-147">Paramètre `rate` est un `ByVal` paramètre car `Calculate` ne doit pas modifier sa valeur.</span><span class="sxs-lookup"><span data-stu-id="b99e1-147">Parameter `rate` is a `ByVal` parameter because `Calculate` should not change its value.</span></span>  
  
### <a name="code"></a><span data-ttu-id="b99e1-148">Code</span><span class="sxs-lookup"><span data-stu-id="b99e1-148">Code</span></span>  
 <span data-ttu-id="b99e1-149">[!code-vb[VbVbcnProcedures&#74;](./codesnippet/VisualBasic/passing-arguments-by-value-and-by-reference_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="b99e1-149">[!code-vb[VbVbcnProcedures#74](./codesnippet/VisualBasic/passing-arguments-by-value-and-by-reference_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b99e1-150">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b99e1-150">See Also</span></span>  
 <span data-ttu-id="b99e1-151">[Procédures](./index.md) </span><span class="sxs-lookup"><span data-stu-id="b99e1-151">[Procedures](./index.md) </span></span>  
<span data-ttu-id="b99e1-152"> [Arguments et paramètres de procédure](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="b99e1-152"> [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="b99e1-153"> [Comment : passer des Arguments à une procédure](./how-to-pass-arguments-to-a-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="b99e1-153"> [How to: Pass Arguments to a Procedure](./how-to-pass-arguments-to-a-procedure.md) </span></span>  
<span data-ttu-id="b99e1-154"> [Comment : modifier la valeur d’un Argument de procédure](./how-to-change-the-value-of-a-procedure-argument.md) </span><span class="sxs-lookup"><span data-stu-id="b99e1-154"> [How to: Change the Value of a Procedure Argument](./how-to-change-the-value-of-a-procedure-argument.md) </span></span>  
<span data-ttu-id="b99e1-155"> [Comment : protéger un Argument de procédure contre les modifications de valeur](./how-to-protect-a-procedure-argument-against-value-changes.md) </span><span class="sxs-lookup"><span data-stu-id="b99e1-155"> [How to: Protect a Procedure Argument Against Value Changes](./how-to-protect-a-procedure-argument-against-value-changes.md) </span></span>  
<span data-ttu-id="b99e1-156"> [Comment : forcer un Argument à passer par valeur](./how-to-force-an-argument-to-be-passed-by-value.md) </span><span class="sxs-lookup"><span data-stu-id="b99e1-156"> [How to: Force an Argument to Be Passed by Value](./how-to-force-an-argument-to-be-passed-by-value.md) </span></span>  
<span data-ttu-id="b99e1-157"> [Passage des Arguments par Position et par nom](./passing-arguments-by-position-and-by-name.md) </span><span class="sxs-lookup"><span data-stu-id="b99e1-157"> [Passing Arguments by Position and by Name](./passing-arguments-by-position-and-by-name.md) </span></span>  
<span data-ttu-id="b99e1-158"> [Types valeur et types référence](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)</span><span class="sxs-lookup"><span data-stu-id="b99e1-158"> [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)</span></span>
