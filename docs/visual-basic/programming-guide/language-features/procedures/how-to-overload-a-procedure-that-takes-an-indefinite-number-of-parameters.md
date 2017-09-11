---
title: "Comment : surcharger une procédure qui accepte un nombre indéfini de paramètres (Visual Basic) | Documents Microsoft"
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
- procedures, parameters
- procedure overloading, indefinite number of parameters
- procedures, defining
- Visual Basic code, procedures
- procedure parameters
- procedures, overloading
- procedures, multiple versions
ms.assetid: c7042de2-2422-4039-94e8-ac298896af69
caps.latest.revision: 18
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
ms.openlocfilehash: 3e4ef81049f3b0d3ab1271fb709f07c37f274a88
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters-visual-basic"></a><span data-ttu-id="5125d-102">Comment : surcharger une procédure qui accepte un nombre indéfini de paramètres (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5125d-102">How to: Overload a Procedure that Takes an Indefinite Number of Parameters (Visual Basic)</span></span>
<span data-ttu-id="5125d-103">Si une procédure possède un [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) paramètre, vous ne pouvez pas définir une version surchargée acceptant un tableau unidimensionnel pour le tableau de paramètres.</span><span class="sxs-lookup"><span data-stu-id="5125d-103">If a procedure has a [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parameter, you cannot define an overloaded version taking a one-dimensional array for the parameter array.</span></span> <span data-ttu-id="5125d-104">Pour plus d’informations, consultez « Implicite surcharges pour un paramètre ParamArray » dans [considérations dans les procédures](./considerations-in-overloading-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="5125d-104">For more information, see "Implicit Overloads for a ParamArray Parameter" in [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
### <a name="to-overload-a-procedure-that-takes-a-variable-number-of-parameters"></a><span data-ttu-id="5125d-105">Pour surcharger une procédure qui accepte un nombre variable de paramètres</span><span class="sxs-lookup"><span data-stu-id="5125d-105">To overload a procedure that takes a variable number of parameters</span></span>  
  
1.  <span data-ttu-id="5125d-106">Vérifier que la procédure et les avantages liés au code logique à partir de l’appel surchargées versions plus que d’un `ParamArray` paramètre.</span><span class="sxs-lookup"><span data-stu-id="5125d-106">Ascertain that the procedure and calling code logic benefits from overloaded versions more than from a `ParamArray` parameter.</span></span> <span data-ttu-id="5125d-107">Consultez « Surcharges et ParamArrays » dans [considérations sur les surcharges de procédures](./considerations-in-overloading-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="5125d-107">See "Overloads and ParamArrays" in [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
2.  <span data-ttu-id="5125d-108">Déterminer le nombre de valeurs fournies que la procédure doit accepter dans la partie variable de la liste de paramètres.</span><span class="sxs-lookup"><span data-stu-id="5125d-108">Determine which numbers of supplied values the procedure should accept in the variable part of the parameter list.</span></span> <span data-ttu-id="5125d-109">Cela peut inclure le cas d’aucune valeur, et peut inclure le cas d’un tableau unidimensionnel unique.</span><span class="sxs-lookup"><span data-stu-id="5125d-109">This might include the case of no value, and it might include the case of a single one-dimensional array.</span></span>  
  
3.  <span data-ttu-id="5125d-110">Pour chaque nombre acceptable de valeurs fournies, écrivez une `Sub` ou `Function` instruction de déclaration qui définit la liste de paramètres correspondante.</span><span class="sxs-lookup"><span data-stu-id="5125d-110">For each acceptable number of supplied values, write a `Sub` or `Function` declaration statement that defines the corresponding parameter list.</span></span> <span data-ttu-id="5125d-111">Ne pas utiliser le `Optional` ou `ParamArray` (mot clé) dans la version surchargée.</span><span class="sxs-lookup"><span data-stu-id="5125d-111">Do not use either the `Optional` or the `ParamArray` keyword in this overloaded version.</span></span>  
  
4.  <span data-ttu-id="5125d-112">Dans chaque déclaration, faites précéder le `Sub` ou `Function` mot clé avec le [surcharges](../../../../visual-basic/language-reference/modifiers/overloads.md) (mot clé).</span><span class="sxs-lookup"><span data-stu-id="5125d-112">In each declaration, precede the `Sub` or `Function` keyword with the [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) keyword.</span></span>  
  
5.  <span data-ttu-id="5125d-113">Après chaque déclaration, écrivez le code de procédure à exécuter lorsque le code appelant fournit des valeurs correspondant à la liste de paramètres de cette déclaration.</span><span class="sxs-lookup"><span data-stu-id="5125d-113">Following each declaration, write the procedure code that should execute when the calling code supplies values corresponding to that declaration's parameter list.</span></span>  
  
6.  <span data-ttu-id="5125d-114">Terminez chaque procédure par le `End Sub` ou `End Function` instruction comme il convient.</span><span class="sxs-lookup"><span data-stu-id="5125d-114">Terminate each procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5125d-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="5125d-115">Example</span></span>  
 <span data-ttu-id="5125d-116">L’exemple suivant montre une procédure définie avec un [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) paramètre, puis un jeu équivalent de procédures surchargées.</span><span class="sxs-lookup"><span data-stu-id="5125d-116">The following example shows a procedure defined with a [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parameter, and then an equivalent set of overloaded procedures.</span></span>  
  
 <span data-ttu-id="5125d-117">[!code-vb[VbVbcnProcedures&#69;](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="5125d-117">[!code-vb[VbVbcnProcedures#69](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters_1.vb)]</span></span>  
  
 <span data-ttu-id="5125d-118">[!code-vb[VbVbcnProcedures&#70;](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="5125d-118">[!code-vb[VbVbcnProcedures#70](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters_2.vb)]</span></span>  
  
 <span data-ttu-id="5125d-119">Vous ne pouvez pas surcharger une procédure avec une liste de paramètres qui prend un tableau unidimensionnel pour le tableau de paramètres.</span><span class="sxs-lookup"><span data-stu-id="5125d-119">You cannot overload such a procedure with a parameter list that takes a one-dimensional array for the parameter array.</span></span> <span data-ttu-id="5125d-120">Toutefois, vous pouvez utiliser les signatures des autres surcharges implicites.</span><span class="sxs-lookup"><span data-stu-id="5125d-120">However, you can use the signatures of the other implicit overloads.</span></span> <span data-ttu-id="5125d-121">Les déclarations suivantes illustrent ce principe.</span><span class="sxs-lookup"><span data-stu-id="5125d-121">The following declarations illustrate this.</span></span>  
  
 <span data-ttu-id="5125d-122">[!code-vb[VbVbcnProcedures&#71;](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="5125d-122">[!code-vb[VbVbcnProcedures#71](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters_3.vb)]</span></span>  
  
 <span data-ttu-id="5125d-123">Le code dans les versions surchargées n’a pas à tester si le code appelant a fourni une ou plusieurs valeurs pour le `ParamArray` paramètre, ou si c’est le cas, combien.</span><span class="sxs-lookup"><span data-stu-id="5125d-123">The code in the overloaded versions does not have to test whether the calling code supplied one or more values for the `ParamArray` parameter, or if so, how many.</span></span> [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="5125d-124">transmet le contrôle à la version correspondant à la liste d’arguments appelante.</span><span class="sxs-lookup"><span data-stu-id="5125d-124"> passes control to the version matching the calling argument list.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5125d-125">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="5125d-125">Compiling the Code</span></span>  
 <span data-ttu-id="5125d-126">Comme une procédure avec un `ParamArray` paramètre équivaut à un ensemble de versions surchargées, vous ne pouvez pas surcharger une procédure avec une liste de paramètres correspondant à chacune de ces surcharges implicites.</span><span class="sxs-lookup"><span data-stu-id="5125d-126">Because a procedure with a `ParamArray` parameter is equivalent to a set of overloaded versions, you cannot overload such a procedure with a parameter list corresponding to any of these implicit overloads.</span></span> <span data-ttu-id="5125d-127">Pour plus d’informations, consultez [considérations dans les procédures](./considerations-in-overloading-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="5125d-127">For more information, see [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="5125d-128">Sécurité .NET Framework</span><span class="sxs-lookup"><span data-stu-id="5125d-128">.NET Framework Security</span></span>  
 <span data-ttu-id="5125d-129">Si vous travaillez dans un tableau dont la taille peut être indéfinie, il existe un risque de saturer la capacité interne de votre application.</span><span class="sxs-lookup"><span data-stu-id="5125d-129">Whenever you deal with an array which can be indefinitely large, there is a risk of overrunning some internal capacity of your application.</span></span> <span data-ttu-id="5125d-130">Si vous acceptez un tableau de paramètres, vous devez tester la longueur du tableau passé au code appelant et prendre les mesures appropriées si elle est trop grande pour votre application.</span><span class="sxs-lookup"><span data-stu-id="5125d-130">If you accept a parameter array, you should test for the length of the array the calling code passed to it, and take appropriate steps if it is too large for your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5125d-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5125d-131">See Also</span></span>  
 <span data-ttu-id="5125d-132">[Procédures](./index.md) </span><span class="sxs-lookup"><span data-stu-id="5125d-132">[Procedures](./index.md) </span></span>  
<span data-ttu-id="5125d-133"> [Arguments et paramètres de procédure](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="5125d-133"> [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="5125d-134"> [Paramètres facultatifs](./optional-parameters.md) </span><span class="sxs-lookup"><span data-stu-id="5125d-134"> [Optional Parameters](./optional-parameters.md) </span></span>  
<span data-ttu-id="5125d-135"> [Tableaux de paramètres](./parameter-arrays.md) </span><span class="sxs-lookup"><span data-stu-id="5125d-135"> [Parameter Arrays](./parameter-arrays.md) </span></span>  
<span data-ttu-id="5125d-136"> [Surcharge de procédure](./procedure-overloading.md) </span><span class="sxs-lookup"><span data-stu-id="5125d-136"> [Procedure Overloading](./procedure-overloading.md) </span></span>  
<span data-ttu-id="5125d-137"> [Procédures de dépannage](./troubleshooting-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="5125d-137"> [Troubleshooting Procedures](./troubleshooting-procedures.md) </span></span>  
<span data-ttu-id="5125d-138"> [Comment : définir plusieurs Versions d’une procédure](./how-to-define-multiple-versions-of-a-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="5125d-138"> [How to: Define Multiple Versions of a Procedure](./how-to-define-multiple-versions-of-a-procedure.md) </span></span>  
<span data-ttu-id="5125d-139"> [Comment : appeler une procédure surchargée](./how-to-call-an-overloaded-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="5125d-139"> [How to: Call an Overloaded Procedure](./how-to-call-an-overloaded-procedure.md) </span></span>  
<span data-ttu-id="5125d-140"> [Comment : surcharger une procédure qui accepte des paramètres optionnels](./how-to-overload-a-procedure-that-takes-optional-parameters.md) </span><span class="sxs-lookup"><span data-stu-id="5125d-140"> [How to: Overload a Procedure that Takes Optional Parameters](./how-to-overload-a-procedure-that-takes-optional-parameters.md) </span></span>  
<span data-ttu-id="5125d-141"> [Résolution de surcharge](./overload-resolution.md)</span><span class="sxs-lookup"><span data-stu-id="5125d-141"> [Overload Resolution](./overload-resolution.md)</span></span>
