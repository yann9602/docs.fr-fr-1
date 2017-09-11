---
title: "Assouplie Conversion des délégués (Visual Basic) | Documents Microsoft"
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
- relaxed delegate conversion [Visual Basic]
- delegates [Visual Basic], relaxed conversion
- conversions, relaxed delegate
ms.assetid: 64f371d0-5416-4f65-b23b-adcbf556e81c
caps.latest.revision: 19
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
ms.openlocfilehash: 016c808145f7faba26a288cd5075f10d7f5279d5
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="relaxed-delegate-conversion-visual-basic"></a><span data-ttu-id="3afc2-102">Conversion simplifiée des délégués (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3afc2-102">Relaxed Delegate Conversion (Visual Basic)</span></span>
<span data-ttu-id="3afc2-103">Conversion simplifiée des délégués permet d’assigner des sous-routines et des fonctions aux délégués ou aux gestionnaires même lorsque leurs signatures ne sont pas identiques.</span><span class="sxs-lookup"><span data-stu-id="3afc2-103">Relaxed delegate conversion enables you to assign subs and functions to delegates or handlers even when their signatures are not identical.</span></span> <span data-ttu-id="3afc2-104">Par conséquent, la liaison aux délégués devient cohérente avec la liaison déjà autorisée pour les appels de méthode.</span><span class="sxs-lookup"><span data-stu-id="3afc2-104">Therefore, binding to delegates becomes consistent with the binding already allowed for method invocations.</span></span>  
  
## <a name="parameters-and-return-type"></a><span data-ttu-id="3afc2-105">Paramètres et Type de retour</span><span class="sxs-lookup"><span data-stu-id="3afc2-105">Parameters and Return Type</span></span>  
 <span data-ttu-id="3afc2-106">À la place d’une correspondance de signature exacte, la conversion simplifiée requiert que les conditions suivantes est remplie lorsque `Option Strict` est défini sur `On`:</span><span class="sxs-lookup"><span data-stu-id="3afc2-106">In place of exact signature match, relaxed conversion requires that the following conditions be met when `Option Strict` is set to `On`:</span></span>  
  
-   <span data-ttu-id="3afc2-107">Une conversion étendue doit avoir le type de données de chaque paramètre de délégué pour le type de données du paramètre correspondant de la fonction attribué ou `Sub`.</span><span class="sxs-lookup"><span data-stu-id="3afc2-107">A widening conversion must exist from the data type of each delegate parameter to the data type of the corresponding parameter of the assigned function or `Sub`.</span></span> <span data-ttu-id="3afc2-108">Dans l’exemple suivant, le délégué `Del1` possède un paramètre, une `Integer`.</span><span class="sxs-lookup"><span data-stu-id="3afc2-108">In the following example, the delegate `Del1` has one parameter, an `Integer`.</span></span> <span data-ttu-id="3afc2-109">Paramètre `m` dans le lambda assignée expressions doivent avoir un type de données pour laquelle il existe une conversion étendue de `Integer`, tel que `Long` ou `Double`.</span><span class="sxs-lookup"><span data-stu-id="3afc2-109">Parameter `m` in the assigned lambda expressions must have a data type for which there is a widening conversion from `Integer`, such as `Long` or `Double`.</span></span>  
  
     <span data-ttu-id="3afc2-110">[!code-vb[VbVbalrRelaxedDelegates n °&1;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="3afc2-110">[!code-vb[VbVbalrRelaxedDelegates#1](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_1.vb)]</span></span>  
  
     <span data-ttu-id="3afc2-111">[!code-vb[VbVbalrRelaxedDelegates n °&2;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="3afc2-111">[!code-vb[VbVbalrRelaxedDelegates#2](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_2.vb)]</span></span>  
  
     <span data-ttu-id="3afc2-112">Les conversions restrictives sont autorisées uniquement lorsque `Option Strict` est défini sur `Off`.</span><span class="sxs-lookup"><span data-stu-id="3afc2-112">Narrowing conversions are permitted only when `Option Strict` is set to `Off`.</span></span>  
  
     <span data-ttu-id="3afc2-113">[!code-vb[VbVbalrRelaxedDelegates n °&8;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="3afc2-113">[!code-vb[VbVbalrRelaxedDelegates#8](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_3.vb)]</span></span>  
  
-   <span data-ttu-id="3afc2-114">Une conversion étendue doit exister dans la direction opposée du type de retour de la fonction attribué ou `Sub` pour le type de retour du délégué.</span><span class="sxs-lookup"><span data-stu-id="3afc2-114">A widening conversion must exist in the opposite direction from the return type of the assigned function or `Sub` to the return type of the delegate.</span></span> <span data-ttu-id="3afc2-115">Dans les exemples suivants, le corps de chaque expression lambda assignée doit avoir un type de données qui s’étend à `Integer` , car le type de retour de `del1` est `Integer`.</span><span class="sxs-lookup"><span data-stu-id="3afc2-115">In the following examples, the body of each assigned lambda expression must evaluate to a data type that widens to `Integer` because the return type of `del1` is `Integer`.</span></span>  
  
     <span data-ttu-id="3afc2-116">[!code-vb[VbVbalrRelaxedDelegates n °&3;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="3afc2-116">[!code-vb[VbVbalrRelaxedDelegates#3](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_4.vb)]</span></span>  
  
 <span data-ttu-id="3afc2-117">Si `Option Strict` est défini sur `Off`, la restriction étendue est supprimée dans les deux sens.</span><span class="sxs-lookup"><span data-stu-id="3afc2-117">If `Option Strict` is set to `Off`, the widening restriction is removed in both directions.</span></span>  
  
 <span data-ttu-id="3afc2-118">[!code-vb[VbVbalrRelaxedDelegates n °&4;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="3afc2-118">[!code-vb[VbVbalrRelaxedDelegates#4](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_5.vb)]</span></span>  
  
## <a name="omitting-parameter-specifications"></a><span data-ttu-id="3afc2-119">L’omission des spécifications de paramètres</span><span class="sxs-lookup"><span data-stu-id="3afc2-119">Omitting Parameter Specifications</span></span>  
 <span data-ttu-id="3afc2-120">Délégués non stricts permettent d’omettre complètement les spécifications de paramètres dans la méthode assignée :</span><span class="sxs-lookup"><span data-stu-id="3afc2-120">Relaxed delegates also allow you to completely omit parameter specifications in the assigned method:</span></span>  
  
 <span data-ttu-id="3afc2-121">[!code-vb[VbVbalrRelaxedDelegates n °&5;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="3afc2-121">[!code-vb[VbVbalrRelaxedDelegates#5](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_6.vb)]</span></span>  
  
 <span data-ttu-id="3afc2-122">[!code-vb[VbVbalrRelaxedDelegates n °&6;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_7.vb)]</span><span class="sxs-lookup"><span data-stu-id="3afc2-122">[!code-vb[VbVbalrRelaxedDelegates#6](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_7.vb)]</span></span>  
  
 <span data-ttu-id="3afc2-123">Notez que vous ne pouvez pas spécifier certains paramètres et omettre d’autres.</span><span class="sxs-lookup"><span data-stu-id="3afc2-123">Note that you cannot specify some parameters and omit others.</span></span>  
  
 <span data-ttu-id="3afc2-124">[!code-vb[VbVbalrRelaxedDelegates&#15;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_8.vb)]</span><span class="sxs-lookup"><span data-stu-id="3afc2-124">[!code-vb[VbVbalrRelaxedDelegates#15](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_8.vb)]</span></span>  
  
 <span data-ttu-id="3afc2-125">La possibilité d’omettre des paramètres est utile dans une situation telles que la définition d’un gestionnaire d’événements, où plusieurs paramètres complexes sont impliqués.</span><span class="sxs-lookup"><span data-stu-id="3afc2-125">The ability to omit parameters is helpful in a situation such as defining an event handler, where several complex parameters are involved.</span></span> <span data-ttu-id="3afc2-126">Les arguments de certains gestionnaires d’événements ne sont pas utilisés.</span><span class="sxs-lookup"><span data-stu-id="3afc2-126">The arguments to some event handlers are not used.</span></span> <span data-ttu-id="3afc2-127">Au lieu de cela, le gestionnaire accède directement à l’état du contrôle sur lequel l’événement est enregistré et ignore les arguments.</span><span class="sxs-lookup"><span data-stu-id="3afc2-127">Instead, the handler directly accesses the state of the control on which the event is registered, and ignores the arguments.</span></span> <span data-ttu-id="3afc2-128">Délégués non stricts permettent d’omettre les arguments dans les déclarations qui ne comprennent aucune ambiguïté.</span><span class="sxs-lookup"><span data-stu-id="3afc2-128">Relaxed delegates allow you to omit the arguments in such declarations when no ambiguities result.</span></span> <span data-ttu-id="3afc2-129">Dans l’exemple suivant, la méthode entièrement spécifiée `OnClick` peut être réécrite sous la forme `RelaxedOnClick`.</span><span class="sxs-lookup"><span data-stu-id="3afc2-129">In the following example, the fully specified method `OnClick` can be rewritten as `RelaxedOnClick`.</span></span>  
  
```vb  
Sub OnClick(ByVal sender As Object, ByVal e As EventArgs) Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
  
Sub RelaxedOnClick() Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
```  
  
## <a name="addressof-examples"></a><span data-ttu-id="3afc2-130">Exemples d’AddressOf</span><span class="sxs-lookup"><span data-stu-id="3afc2-130">AddressOf Examples</span></span>  
 <span data-ttu-id="3afc2-131">Pour faciliter la voir les relations de type, les expressions lambda sont utilisées dans les exemples précédents.</span><span class="sxs-lookup"><span data-stu-id="3afc2-131">Lambda expressions are used in the previous examples to make the type relationships easy to see.</span></span> <span data-ttu-id="3afc2-132">Toutefois, les mêmes simplifications sont autorisées pour les assignations de délégués qui utilisent `AddressOf`, `Handles`, ou `AddHandler`.</span><span class="sxs-lookup"><span data-stu-id="3afc2-132">However, the same relaxations are permitted for delegate assignments that use `AddressOf`, `Handles`, or `AddHandler`.</span></span>  
  
 <span data-ttu-id="3afc2-133">Dans l’exemple suivant, les fonctions `f1`, `f2`, `f3`, et `f4` peuvent être affectés à `Del1`.</span><span class="sxs-lookup"><span data-stu-id="3afc2-133">In the following example, functions `f1`, `f2`, `f3`, and `f4` can all be assigned to `Del1`.</span></span>  
  
 <span data-ttu-id="3afc2-134">[!code-vb[VbVbalrRelaxedDelegates n °&1;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="3afc2-134">[!code-vb[VbVbalrRelaxedDelegates#1](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_1.vb)]</span></span>  
  
 <span data-ttu-id="3afc2-135">[!code-vb[VbVbalrRelaxedDelegates&#7;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_9.vb)]</span><span class="sxs-lookup"><span data-stu-id="3afc2-135">[!code-vb[VbVbalrRelaxedDelegates#7](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_9.vb)]</span></span>  
  
 <span data-ttu-id="3afc2-136">[!code-vb[VbVbalrRelaxedDelegates&#9;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_10.vb)]</span><span class="sxs-lookup"><span data-stu-id="3afc2-136">[!code-vb[VbVbalrRelaxedDelegates#9](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_10.vb)]</span></span>  
  
 <span data-ttu-id="3afc2-137">L’exemple suivant est valide uniquement lorsque `Option Strict` est défini sur `Off`.</span><span class="sxs-lookup"><span data-stu-id="3afc2-137">The following example is valid only when `Option Strict` is set to `Off`.</span></span>  
  
 <span data-ttu-id="3afc2-138">[!code-vb[VbVbalrRelaxedDelegates&#14;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_11.vb)]</span><span class="sxs-lookup"><span data-stu-id="3afc2-138">[!code-vb[VbVbalrRelaxedDelegates#14](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_11.vb)]</span></span>  
  
## <a name="dropping-function-returns"></a><span data-ttu-id="3afc2-139">Suppression de retours de fonction</span><span class="sxs-lookup"><span data-stu-id="3afc2-139">Dropping Function Returns</span></span>  
 <span data-ttu-id="3afc2-140">Conversion simplifiée des délégués vous permet d’assigner une fonction à un `Sub` délégué, en ignorant la valeur de retour de la fonction.</span><span class="sxs-lookup"><span data-stu-id="3afc2-140">Relaxed delegate conversion enables you to assign a function to a `Sub` delegate, effectively ignoring the return value of the function.</span></span> <span data-ttu-id="3afc2-141">Toutefois, vous ne pouvez pas affecter un `Sub` à un délégué de fonction.</span><span class="sxs-lookup"><span data-stu-id="3afc2-141">However, you cannot assign a `Sub` to a function delegate.</span></span> <span data-ttu-id="3afc2-142">Dans l’exemple suivant, l’adresse de fonction `doubler` est affectée à `Sub` délégué `Del3`.</span><span class="sxs-lookup"><span data-stu-id="3afc2-142">In the following example, the address of function `doubler` is assigned to `Sub` delegate `Del3`.</span></span>  
  
 <span data-ttu-id="3afc2-143">[!code-vb[VbVbalrRelaxedDelegates&#10;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_12.vb)]</span><span class="sxs-lookup"><span data-stu-id="3afc2-143">[!code-vb[VbVbalrRelaxedDelegates#10](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_12.vb)]</span></span>  
  
 <span data-ttu-id="3afc2-144">[!code-vb[VbVbalrRelaxedDelegates&#11;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_13.vb)]</span><span class="sxs-lookup"><span data-stu-id="3afc2-144">[!code-vb[VbVbalrRelaxedDelegates#11](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_13.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3afc2-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3afc2-145">See Also</span></span>  
 <span data-ttu-id="3afc2-146">[Expressions lambda](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="3afc2-146">[Lambda Expressions](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md) </span></span>  
<span data-ttu-id="3afc2-147"> [Conversions étendues et restrictives](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) </span><span class="sxs-lookup"><span data-stu-id="3afc2-147"> [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) </span></span>  
<span data-ttu-id="3afc2-148"> [Délégués](../../../../visual-basic/programming-guide/language-features/delegates/index.md) </span><span class="sxs-lookup"><span data-stu-id="3afc2-148"> [Delegates](../../../../visual-basic/programming-guide/language-features/delegates/index.md) </span></span>  
<span data-ttu-id="3afc2-149"> [Comment : passer des procédures à une autre procédure en Visual Basic](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="3afc2-149"> [How to: Pass Procedures to Another Procedure in Visual Basic](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md) </span></span>  
<span data-ttu-id="3afc2-150"> [Inférence de Type local](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) </span><span class="sxs-lookup"><span data-stu-id="3afc2-150"> [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) </span></span>  
<span data-ttu-id="3afc2-151"> [Option Strict (instruction)](../../../../visual-basic/language-reference/statements/option-strict-statement.md)</span><span class="sxs-lookup"><span data-stu-id="3afc2-151"> [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)</span></span>
