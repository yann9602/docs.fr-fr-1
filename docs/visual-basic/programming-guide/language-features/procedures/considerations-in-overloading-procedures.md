---
title: "Considérations sur les surcharges de procédures (Visual Basic) | Documents Microsoft"
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
- signatures, ParamArray arguments
- ParamArray keyword, parameter arrays
- ParamArray keyword, arguments and signatures
- function overloading, implicit overloads for ParamArray
- ParamArray keyword, signatures
- Visual Basic code, procedures
- arguments [Visual Basic], parameter arrays
- procedures, overloading
- parameters, lists
- function overloading, typeless programming
- typeless programming
- function overloading, restrictions
- arguments [Visual Basic], optional
- optional arguments, overloading
- signatures, procedure
- parameter lists
- parameter arrays, overloading arguments
- Visual Basic code, parameter lists
- procedure overloading, considerations
- Option Explicit statement
- restrictions, overloading procedures
- procedures, parameter lists
ms.assetid: a2001248-10d0-42c5-b0ce-eeedc987319f
caps.latest.revision: 26
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
ms.openlocfilehash: 486e6c08fe6284cc9b5856fb848f7307a5651120
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="considerations-in-overloading-procedures-visual-basic"></a><span data-ttu-id="a3c2f-102">Considérations sur les surcharges de procédures (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a3c2f-102">Considerations in Overloading Procedures (Visual Basic)</span></span>
<span data-ttu-id="a3c2f-103">Lorsque vous surchargez une procédure, vous devez utiliser une autre *signature* pour chaque version surchargée.</span><span class="sxs-lookup"><span data-stu-id="a3c2f-103">When you overload a procedure, you must use a different *signature* for each overloaded version.</span></span> <span data-ttu-id="a3c2f-104">Cela signifie généralement que chaque version doit spécifier une liste de paramètres différente.</span><span class="sxs-lookup"><span data-stu-id="a3c2f-104">This usually means each version must specify a different parameter list.</span></span> <span data-ttu-id="a3c2f-105">Pour plus d’informations, consultez « Signature différente » dans [surcharge de procédure](./procedure-overloading.md).</span><span class="sxs-lookup"><span data-stu-id="a3c2f-105">For more information, see "Different Signature" in [Procedure Overloading](./procedure-overloading.md).</span></span>  
  
 <span data-ttu-id="a3c2f-106">Vous pouvez surcharger une `Function` procédure avec un `Sub` procédure et inversement, à condition qu’ils ont des signatures différentes.</span><span class="sxs-lookup"><span data-stu-id="a3c2f-106">You can overload a `Function` procedure with a `Sub` procedure, and vice versa, provided they have different signatures.</span></span> <span data-ttu-id="a3c2f-107">Deux surcharges ne peuvent pas différer uniquement car une a une valeur de retournée et l’autre non.</span><span class="sxs-lookup"><span data-stu-id="a3c2f-107">Two overloads cannot differ only in that one has a return value and the other does not.</span></span>  
  
 <span data-ttu-id="a3c2f-108">Vous pouvez surcharger une propriété de la même manière que vous surchargez une procédure et avec les mêmes restrictions.</span><span class="sxs-lookup"><span data-stu-id="a3c2f-108">You can overload a property the same way you overload a procedure, and with the same restrictions.</span></span> <span data-ttu-id="a3c2f-109">Toutefois, vous ne pouvez pas surcharger une procédure avec une propriété, ou vice versa.</span><span class="sxs-lookup"><span data-stu-id="a3c2f-109">However, you cannot overload a procedure with a property, or vice versa.</span></span>  
  
## <a name="alternatives-to-overloaded-versions"></a><span data-ttu-id="a3c2f-110">Alternatives aux Versions surchargées</span><span class="sxs-lookup"><span data-stu-id="a3c2f-110">Alternatives to Overloaded Versions</span></span>  
 <span data-ttu-id="a3c2f-111">Vous devez parfois d’alternatives aux versions surchargées, en particulier lorsque la présence d’arguments est facultative ou que leur nombre est variable.</span><span class="sxs-lookup"><span data-stu-id="a3c2f-111">You sometimes have alternatives to overloaded versions, particularly when the presence of arguments is optional or their number is variable.</span></span>  
  
 <span data-ttu-id="a3c2f-112">N’oubliez pas que les arguments facultatifs ne sont pas nécessairement pris en charge par tous les langages et les tableaux de paramètres sont limités à [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span><span class="sxs-lookup"><span data-stu-id="a3c2f-112">Keep in mind that optional arguments are not necessarily supported by all languages, and parameter arrays are limited to [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span> <span data-ttu-id="a3c2f-113">Si vous écrivez une procédure qui est susceptible d’être appelée à partir du code écrit dans un des différents langages, les versions surchargées offrent la plus grande flexibilité.</span><span class="sxs-lookup"><span data-stu-id="a3c2f-113">If you are writing a procedure that is likely to be called from code written in any of several different languages, overloaded versions offer the greatest flexibility.</span></span>  
  
### <a name="overloads-and-optional-arguments"></a><span data-ttu-id="a3c2f-114">Surcharges et Arguments facultatifs</span><span class="sxs-lookup"><span data-stu-id="a3c2f-114">Overloads and Optional Arguments</span></span>  
 <span data-ttu-id="a3c2f-115">Lorsque le code appelant peut éventuellement fournir ou omettre un ou plusieurs arguments, vous pouvez définir plusieurs versions surchargées ou utiliser des paramètres facultatifs.</span><span class="sxs-lookup"><span data-stu-id="a3c2f-115">When the calling code can optionally supply or omit one or more arguments, you can define multiple overloaded versions or use optional parameters.</span></span>  
  
#### <a name="when-to-use-overloaded-versions"></a><span data-ttu-id="a3c2f-116">Quand utiliser des Versions surchargées</span><span class="sxs-lookup"><span data-stu-id="a3c2f-116">When to Use Overloaded Versions</span></span>  
 <span data-ttu-id="a3c2f-117">Vous pouvez envisager de définir une série de versions surchargées dans les cas suivants :</span><span class="sxs-lookup"><span data-stu-id="a3c2f-117">You can consider defining a series of overloaded versions in the following cases:</span></span>  
  
-   <span data-ttu-id="a3c2f-118">La logique dans le code de procédure est très différente selon que le code appelant fournit un argument facultatif ou pas.</span><span class="sxs-lookup"><span data-stu-id="a3c2f-118">The logic in the procedure code is significantly different depending on whether the calling code supplies an optional argument or not.</span></span>  
  
-   <span data-ttu-id="a3c2f-119">Le code de procédure ne peut pas tester de manière fiable si le code appelant a fourni un argument facultatif.</span><span class="sxs-lookup"><span data-stu-id="a3c2f-119">The procedure code cannot reliably test whether the calling code has supplied an optional argument.</span></span> <span data-ttu-id="a3c2f-120">C’est le cas, par exemple, s’il n’existe aucun candidat possible pour une valeur par défaut que le code appelant ne peut pas censé fournir.</span><span class="sxs-lookup"><span data-stu-id="a3c2f-120">This is the case, for example, if there is no possible candidate for a default value that the calling code could not be expected to supply.</span></span>  
  
#### <a name="when-to-use-optional-parameters"></a><span data-ttu-id="a3c2f-121">Quand utiliser les paramètres facultatifs</span><span class="sxs-lookup"><span data-stu-id="a3c2f-121">When to Use Optional Parameters</span></span>  
 <span data-ttu-id="a3c2f-122">Vous préférerez peut-être un ou plusieurs paramètres facultatifs dans les cas suivants :</span><span class="sxs-lookup"><span data-stu-id="a3c2f-122">You might prefer one or more optional parameters in the following cases:</span></span>  
  
-   <span data-ttu-id="a3c2f-123">La seule action requise lorsque le code appelant ne fournit pas un argument facultatif consiste à définir le paramètre à une valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="a3c2f-123">The only required action when the calling code does not supply an optional argument is to set the parameter to a default value.</span></span> <span data-ttu-id="a3c2f-124">Dans ce cas, le code de procédure peut être moins compliqué si vous définissez une version unique avec un ou plusieurs `Optional` paramètres.</span><span class="sxs-lookup"><span data-stu-id="a3c2f-124">In such a case, the procedure code can be less complicated if you define a single version with one or more `Optional` parameters.</span></span>  
  
 <span data-ttu-id="a3c2f-125">Pour plus d’informations, consultez [paramètres facultatifs](./optional-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="a3c2f-125">For more information, see [Optional Parameters](./optional-parameters.md).</span></span>  
  
### <a name="overloads-and-paramarrays"></a><span data-ttu-id="a3c2f-126">Overloads and ParamArrays</span><span class="sxs-lookup"><span data-stu-id="a3c2f-126">Overloads and ParamArrays</span></span>  
 <span data-ttu-id="a3c2f-127">Lorsque le code appelant peut passer un nombre variable d’arguments, vous pouvez définir plusieurs versions surchargées ou utiliser un tableau de paramètres.</span><span class="sxs-lookup"><span data-stu-id="a3c2f-127">When the calling code can pass a variable number of arguments, you can define multiple overloaded versions or use a parameter array.</span></span>  
  
#### <a name="when-to-use-overloaded-versions"></a><span data-ttu-id="a3c2f-128">Quand utiliser des Versions surchargées</span><span class="sxs-lookup"><span data-stu-id="a3c2f-128">When to Use Overloaded Versions</span></span>  
 <span data-ttu-id="a3c2f-129">Vous pouvez envisager de définir une série de versions surchargées dans les cas suivants :</span><span class="sxs-lookup"><span data-stu-id="a3c2f-129">You can consider defining a series of overloaded versions in the following cases:</span></span>  
  
-   <span data-ttu-id="a3c2f-130">Vous savez que le code appelant passe jamais plus qu’un petit nombre de valeurs au tableau de paramètres.</span><span class="sxs-lookup"><span data-stu-id="a3c2f-130">You know that the calling code never passes more than a small number of values to the parameter array.</span></span>  
  
-   <span data-ttu-id="a3c2f-131">La logique dans le code de procédure est très différente selon le nombre de valeurs le code appelant passe.</span><span class="sxs-lookup"><span data-stu-id="a3c2f-131">The logic in the procedure code is significantly different depending on how many values the calling code passes.</span></span>  
  
-   <span data-ttu-id="a3c2f-132">Le code appelant peut passer des valeurs de différents types de données.</span><span class="sxs-lookup"><span data-stu-id="a3c2f-132">The calling code can pass values of different data types.</span></span>  
  
#### <a name="when-to-use-a-parameter-array"></a><span data-ttu-id="a3c2f-133">Quand utiliser un tableau de paramètres</span><span class="sxs-lookup"><span data-stu-id="a3c2f-133">When to Use a Parameter Array</span></span>  
 <span data-ttu-id="a3c2f-134">Il est préférable à une `ParamArray` paramètre dans les cas suivants :</span><span class="sxs-lookup"><span data-stu-id="a3c2f-134">You are better served by a `ParamArray` parameter in the following cases:</span></span>  
  
-   <span data-ttu-id="a3c2f-135">Vous n’êtes pas en mesure de prévoir combien de valeurs le code appelant peut passer au tableau de paramètres, et il peut être un grand nombre.</span><span class="sxs-lookup"><span data-stu-id="a3c2f-135">You are not able to predict how many values the calling code can pass to the parameter array, and it could be a large number.</span></span>  
  
-   <span data-ttu-id="a3c2f-136">La logique de la procédure se prête à l’itération sur toutes les valeurs que le code appelant passe, en exécutant essentiellement les mêmes opérations sur chaque valeur.</span><span class="sxs-lookup"><span data-stu-id="a3c2f-136">The procedure logic lends itself to iterating through all the values the calling code passes, performing essentially the same operations on every value.</span></span>  
  
 <span data-ttu-id="a3c2f-137">Pour plus d’informations, consultez [tableaux de paramètres](./parameter-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="a3c2f-137">For more information, see [Parameter Arrays](./parameter-arrays.md).</span></span>  
  
## <a name="implicit-overloads-for-optional-parameters"></a><span data-ttu-id="a3c2f-138">Surcharges implicites pour les paramètres optionnels</span><span class="sxs-lookup"><span data-stu-id="a3c2f-138">Implicit Overloads for Optional Parameters</span></span>  
 <span data-ttu-id="a3c2f-139">Une procédure avec un [facultatif](../../../../visual-basic/language-reference/modifiers/optional.md) paramètre équivaut à deux procédures surchargées, une avec le paramètre facultatif et l’autre sans.</span><span class="sxs-lookup"><span data-stu-id="a3c2f-139">A procedure with an [Optional](../../../../visual-basic/language-reference/modifiers/optional.md) parameter is equivalent to two overloaded procedures, one with the optional parameter and one without it.</span></span> <span data-ttu-id="a3c2f-140">Vous ne pouvez pas surcharger une procédure avec une liste de paramètres correspondant à ces.</span><span class="sxs-lookup"><span data-stu-id="a3c2f-140">You cannot overload such a procedure with a parameter list corresponding to either of these.</span></span> <span data-ttu-id="a3c2f-141">Les déclarations suivantes illustrent ce principe.</span><span class="sxs-lookup"><span data-stu-id="a3c2f-141">The following declarations illustrate this.</span></span>  
  
 <span data-ttu-id="a3c2f-142">[!code-vb[VbVbcnProcedures&#58;](./codesnippet/VisualBasic/considerations-in-overloading-procedures_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="a3c2f-142">[!code-vb[VbVbcnProcedures#58](./codesnippet/VisualBasic/considerations-in-overloading-procedures_1.vb)]</span></span>  
  
 <span data-ttu-id="a3c2f-143">[!code-vb[VbVbcnProcedures&#60;](./codesnippet/VisualBasic/considerations-in-overloading-procedures_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="a3c2f-143">[!code-vb[VbVbcnProcedures#60](./codesnippet/VisualBasic/considerations-in-overloading-procedures_2.vb)]</span></span>  
  
 <span data-ttu-id="a3c2f-144">[!code-vb[VbVbcnProcedures&#61;](./codesnippet/VisualBasic/considerations-in-overloading-procedures_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="a3c2f-144">[!code-vb[VbVbcnProcedures#61](./codesnippet/VisualBasic/considerations-in-overloading-procedures_3.vb)]</span></span>  
  
 <span data-ttu-id="a3c2f-145">Pour une procédure avec plus d’un paramètre facultatif, il existe un ensemble de surcharges implicites, déterminé par la logique, comme dans l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="a3c2f-145">For a procedure with more than one optional parameter, there is a set of implicit overloads, arrived at by logic similar to that in the preceding example.</span></span>  
  
## <a name="implicit-overloads-for-a-paramarray-parameter"></a><span data-ttu-id="a3c2f-146">Surcharges implicites pour un paramètre ParamArray</span><span class="sxs-lookup"><span data-stu-id="a3c2f-146">Implicit Overloads for a ParamArray Parameter</span></span>  
 <span data-ttu-id="a3c2f-147">Le compilateur considère qu’une procédure avec un [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) paramètre possède un nombre infini de surcharges, qui se différencient selon ce que le code appelant passe au tableau de paramètres, comme suit :</span><span class="sxs-lookup"><span data-stu-id="a3c2f-147">The compiler considers a procedure with a [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parameter to have an infinite number of overloads, differing from each other in what the calling code passes to the parameter array, as follows:</span></span>  
  
-   <span data-ttu-id="a3c2f-148">Une surcharge lorsque le code appelant ne fournit pas un argument à la`ParamArray`</span><span class="sxs-lookup"><span data-stu-id="a3c2f-148">One overload for when the calling code does not supply an argument to the `ParamArray`</span></span>  
  
-   <span data-ttu-id="a3c2f-149">Une surcharge lorsque le code appelant fournit un tableau unidimensionnel de le `ParamArray` le type d’élément</span><span class="sxs-lookup"><span data-stu-id="a3c2f-149">One overload for when the calling code supplies a one-dimensional array of the `ParamArray` element type</span></span>  
  
-   <span data-ttu-id="a3c2f-150">Pour chaque entier positif, une surcharge lorsque le code appelant fournit ce nombre d’arguments de le `ParamArray` le type d’élément</span><span class="sxs-lookup"><span data-stu-id="a3c2f-150">For every positive integer, one overload for when the calling code supplies that number of arguments, each of the `ParamArray` element type</span></span>  
  
 <span data-ttu-id="a3c2f-151">Les déclarations suivantes illustrent ces surcharges implicites.</span><span class="sxs-lookup"><span data-stu-id="a3c2f-151">The following declarations illustrate these implicit overloads.</span></span>  
  
 <span data-ttu-id="a3c2f-152">[!code-vb[VbVbcnProcedures&#68;](./codesnippet/VisualBasic/considerations-in-overloading-procedures_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="a3c2f-152">[!code-vb[VbVbcnProcedures#68](./codesnippet/VisualBasic/considerations-in-overloading-procedures_4.vb)]</span></span>  
  
 <span data-ttu-id="a3c2f-153">[!code-vb[VbVbcnProcedures&#70;](./codesnippet/VisualBasic/considerations-in-overloading-procedures_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="a3c2f-153">[!code-vb[VbVbcnProcedures#70](./codesnippet/VisualBasic/considerations-in-overloading-procedures_5.vb)]</span></span>  
  
 <span data-ttu-id="a3c2f-154">Vous ne pouvez pas surcharger une procédure avec une liste de paramètres qui prend un tableau unidimensionnel pour le tableau de paramètres.</span><span class="sxs-lookup"><span data-stu-id="a3c2f-154">You cannot overload such a procedure with a parameter list that takes a one-dimensional array for the parameter array.</span></span> <span data-ttu-id="a3c2f-155">Toutefois, vous pouvez utiliser les signatures des autres surcharges implicites.</span><span class="sxs-lookup"><span data-stu-id="a3c2f-155">However, you can use the signatures of the other implicit overloads.</span></span> <span data-ttu-id="a3c2f-156">Les déclarations suivantes illustrent ce principe.</span><span class="sxs-lookup"><span data-stu-id="a3c2f-156">The following declarations illustrate this.</span></span>  
  
 <span data-ttu-id="a3c2f-157">[!code-vb[VbVbcnProcedures&#71;](./codesnippet/VisualBasic/considerations-in-overloading-procedures_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="a3c2f-157">[!code-vb[VbVbcnProcedures#71](./codesnippet/VisualBasic/considerations-in-overloading-procedures_6.vb)]</span></span>  
  
## <a name="typeless-programming-as-an-alternative-to-overloading"></a><span data-ttu-id="a3c2f-158">Programmation sans type comme une Alternative à la surcharge</span><span class="sxs-lookup"><span data-stu-id="a3c2f-158">Typeless Programming as an Alternative to Overloading</span></span>  
 <span data-ttu-id="a3c2f-159">Si vous souhaitez autoriser le code appelant à passer différents types de données à un paramètre, une autre approche consiste à la programmation sans type.</span><span class="sxs-lookup"><span data-stu-id="a3c2f-159">If you want to allow the calling code to pass different data types to a parameter, an alternative approach is typeless programming.</span></span> <span data-ttu-id="a3c2f-160">Vous pouvez définir le type de commutateur à la vérification de la `Off` avec soit le [Option Strict, instruction](../../../../visual-basic/language-reference/statements/option-strict-statement.md) ou [/optionstrict](../../../../visual-basic/reference/command-line-compiler/optionstrict.md) option du compilateur.</span><span class="sxs-lookup"><span data-stu-id="a3c2f-160">You can set the type checking switch to `Off` with either the [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md) or the [/optionstrict](../../../../visual-basic/reference/command-line-compiler/optionstrict.md) compiler option.</span></span> <span data-ttu-id="a3c2f-161">Puis vous n’êtes pas obligé de déclarer le type de données du paramètre.</span><span class="sxs-lookup"><span data-stu-id="a3c2f-161">Then you do not have to declare the parameter's data type.</span></span> <span data-ttu-id="a3c2f-162">Toutefois, cette approche présente les inconvénients suivants par rapport à la surcharge :</span><span class="sxs-lookup"><span data-stu-id="a3c2f-162">However, this approach has the following disadvantages compared to overloading:</span></span>  
  
-   <span data-ttu-id="a3c2f-163">Programmation sans type génère un code d’exécution moins efficace.</span><span class="sxs-lookup"><span data-stu-id="a3c2f-163">Typeless programming produces less efficient execution code.</span></span>  
  
-   <span data-ttu-id="a3c2f-164">La procédure doit tester chaque type de données que pouvant être passés.</span><span class="sxs-lookup"><span data-stu-id="a3c2f-164">The procedure must test for every data type it anticipates being passed.</span></span>  
  
-   <span data-ttu-id="a3c2f-165">Le compilateur ne peut pas signaler d’erreur si le code appelant passe un type de données par la procédure ne prend pas en charge.</span><span class="sxs-lookup"><span data-stu-id="a3c2f-165">The compiler cannot signal an error if the calling code passes a data type that the procedure does not support.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3c2f-166">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a3c2f-166">See Also</span></span>  
 <span data-ttu-id="a3c2f-167">[Procédures](./index.md) </span><span class="sxs-lookup"><span data-stu-id="a3c2f-167">[Procedures](./index.md) </span></span>  
<span data-ttu-id="a3c2f-168"> [Arguments et paramètres de procédure](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="a3c2f-168"> [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="a3c2f-169"> [Procédures de dépannage](./troubleshooting-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="a3c2f-169"> [Troubleshooting Procedures](./troubleshooting-procedures.md) </span></span>  
<span data-ttu-id="a3c2f-170"> [Comment : définir plusieurs Versions d’une procédure](./how-to-define-multiple-versions-of-a-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="a3c2f-170"> [How to: Define Multiple Versions of a Procedure](./how-to-define-multiple-versions-of-a-procedure.md) </span></span>  
<span data-ttu-id="a3c2f-171"> [Comment : appeler une procédure surchargée](./how-to-call-an-overloaded-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="a3c2f-171"> [How to: Call an Overloaded Procedure](./how-to-call-an-overloaded-procedure.md) </span></span>  
<span data-ttu-id="a3c2f-172"> [Comment : surcharger une procédure qui accepte des paramètres optionnels](./how-to-overload-a-procedure-that-takes-optional-parameters.md) </span><span class="sxs-lookup"><span data-stu-id="a3c2f-172"> [How to: Overload a Procedure that Takes Optional Parameters](./how-to-overload-a-procedure-that-takes-optional-parameters.md) </span></span>  
<span data-ttu-id="a3c2f-173"> [Comment : surcharger une procédure qui accepte un nombre indéfini de paramètres](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md) </span><span class="sxs-lookup"><span data-stu-id="a3c2f-173"> [How to: Overload a Procedure that Takes an Indefinite Number of Parameters](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md) </span></span>  
<span data-ttu-id="a3c2f-174"> [Résolution de surcharge](./overload-resolution.md) </span><span class="sxs-lookup"><span data-stu-id="a3c2f-174"> [Overload Resolution](./overload-resolution.md) </span></span>  
<span data-ttu-id="a3c2f-175"> [Surcharges](../../../../visual-basic/language-reference/modifiers/overloads.md)</span><span class="sxs-lookup"><span data-stu-id="a3c2f-175"> [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md)</span></span>
