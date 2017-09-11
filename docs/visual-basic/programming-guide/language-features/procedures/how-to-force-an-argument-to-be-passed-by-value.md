---
title: "Comment : forcer un Argument est passé par valeur (Visual Basic) | Documents Microsoft"
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
- Visual Basic code, procedures
- arguments [Visual Basic], ByVal
- arguments [Visual Basic], passing by value
- procedure parameters
- procedures, calling
- arguments [Visual Basic], in parentheses
- procedure arguments, in parentheses
- arguments [Visual Basic], changing value
ms.assetid: 77b4f2d2-1055-4c2f-a521-874d1db86946
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
ms.openlocfilehash: b151c319489ccda357faa082ce0b3c1addad0458
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-force-an-argument-to-be-passed-by-value-visual-basic"></a><span data-ttu-id="45fff-102">Comment : forcer le passage d’un argument par valeur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="45fff-102">How to: Force an Argument to Be Passed by Value (Visual Basic)</span></span>
<span data-ttu-id="45fff-103">La déclaration de procédure détermine le mécanisme de passage.</span><span class="sxs-lookup"><span data-stu-id="45fff-103">The procedure declaration determines the passing mechanism.</span></span> <span data-ttu-id="45fff-104">Si un paramètre est déclaré [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] doit passer l’argument correspondant par référence.</span><span class="sxs-lookup"><span data-stu-id="45fff-104">If a parameter is declared [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] expects to pass the corresponding argument by reference.</span></span> <span data-ttu-id="45fff-105">Cela permet à la procédure modifier la valeur de l’élément de programmation sous-jacent à l’argument dans le code appelant.</span><span class="sxs-lookup"><span data-stu-id="45fff-105">This allows the procedure to change the value of the programming element underlying the argument in the calling code.</span></span> <span data-ttu-id="45fff-106">Si vous souhaitez protéger l’élément sous-jacent contre une telle modification, vous pouvez remplacer le `ByRef` mécanisme de passage de la procédure appeler en mettant le nom de l’argument entre parenthèses.</span><span class="sxs-lookup"><span data-stu-id="45fff-106">If you wish to protect the underlying element against such change, you can override the `ByRef` passing mechanism in the procedure call by enclosing the argument name in parentheses.</span></span> <span data-ttu-id="45fff-107">Ces parenthèses sont ajoutent les parenthèses entourant la liste d’arguments de l’appel.</span><span class="sxs-lookup"><span data-stu-id="45fff-107">These parentheses are in addition to the parentheses enclosing the argument list in the call.</span></span>  
  
 <span data-ttu-id="45fff-108">Le code appelant ne peut pas remplacer un [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) mécanisme.</span><span class="sxs-lookup"><span data-stu-id="45fff-108">The calling code cannot override a [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) mechanism.</span></span>  
  
### <a name="to-force-an-argument-to-be-passed-by-value"></a><span data-ttu-id="45fff-109">Pour forcer un argument à passer par valeur</span><span class="sxs-lookup"><span data-stu-id="45fff-109">To force an argument to be passed by value</span></span>  
  
-   <span data-ttu-id="45fff-110">Si le paramètre correspondant est déclaré `ByVal` dans la procédure, vous n’avez pas besoin prendre des mesures supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="45fff-110">If the corresponding parameter is declared `ByVal` in the procedure, you do not need to take any additional steps.</span></span> [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="45fff-111">doit déjà passer l’argument par valeur.</span><span class="sxs-lookup"><span data-stu-id="45fff-111"> already expects to pass the argument by value.</span></span>  
  
-   <span data-ttu-id="45fff-112">Si le paramètre correspondant est déclaré `ByRef` dans la procédure, mettez l’argument entre parenthèses dans l’appel de procédure.</span><span class="sxs-lookup"><span data-stu-id="45fff-112">If the corresponding parameter is declared `ByRef` in the procedure, enclose the argument in parentheses in the procedure call.</span></span>  
  
## <a name="example"></a><span data-ttu-id="45fff-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="45fff-113">Example</span></span>  
 <span data-ttu-id="45fff-114">L’exemple suivant substitue une `ByRef` déclaration de paramètre.</span><span class="sxs-lookup"><span data-stu-id="45fff-114">The following example overrides a `ByRef` parameter declaration.</span></span> <span data-ttu-id="45fff-115">Dans l’appel qui force `ByVal`, notez les deux niveaux de parenthèses.</span><span class="sxs-lookup"><span data-stu-id="45fff-115">In the call that forces `ByVal`, note the two levels of parentheses.</span></span>  
  
 <span data-ttu-id="45fff-116">[!code-vb[VbVbcnProcedures n °&39;](./codesnippet/VisualBasic/how-to-force-an-argument-to-be-passed-by-value_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="45fff-116">[!code-vb[VbVbcnProcedures#39](./codesnippet/VisualBasic/how-to-force-an-argument-to-be-passed-by-value_1.vb)]</span></span>  
  
 <span data-ttu-id="45fff-117">[!code-vb[VbVbcnProcedures numéro&40;](./codesnippet/VisualBasic/how-to-force-an-argument-to-be-passed-by-value_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="45fff-117">[!code-vb[VbVbcnProcedures#40](./codesnippet/VisualBasic/how-to-force-an-argument-to-be-passed-by-value_2.vb)]</span></span>  
  
 <span data-ttu-id="45fff-118">Lors de la `str` est placée entre parenthèses supplémentaires dans la liste d’arguments, les `setNewString` procédure ne peut pas modifier sa valeur dans le code appelant, et `MsgBox` affiche « Ne peut pas être remplacé si passé ByVal ».</span><span class="sxs-lookup"><span data-stu-id="45fff-118">When `str` is enclosed in extra parentheses within the argument list, the `setNewString` procedure cannot change its value in the calling code, and `MsgBox` displays "Cannot be replaced if passed ByVal".</span></span> <span data-ttu-id="45fff-119">Lors de la `str` n’est pas placé entre des parenthèses supplémentaires, la procédure peut le modifier, et `MsgBox` affiche « Il s’agit d’une nouvelle valeur pour l’argument inString. »</span><span class="sxs-lookup"><span data-stu-id="45fff-119">When `str` is not enclosed in extra parentheses, the procedure can change it, and `MsgBox` displays "This is a new value for the inString argument."</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="45fff-120">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="45fff-120">Compiling the Code</span></span>  
 <span data-ttu-id="45fff-121">Lorsque vous passez une variable par référence, vous devez utiliser le `ByRef` (mot clé) pour spécifier ce mécanisme.</span><span class="sxs-lookup"><span data-stu-id="45fff-121">When you pass a variable by reference, you must use the `ByRef` keyword to specify this mechanism.</span></span>  
  
 <span data-ttu-id="45fff-122">La valeur par défaut dans [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] consiste à passer des arguments par valeur.</span><span class="sxs-lookup"><span data-stu-id="45fff-122">The default in [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] is to pass arguments by value.</span></span> <span data-ttu-id="45fff-123">Toutefois, il est conseillé de comprennent le [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) ou [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) mot-clé avec chaque paramètre déclaré.</span><span class="sxs-lookup"><span data-stu-id="45fff-123">However, it is good programming practice to include either the [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) keyword with every declared parameter.</span></span> <span data-ttu-id="45fff-124">Cela rend votre code plus facile à lire.</span><span class="sxs-lookup"><span data-stu-id="45fff-124">This makes your code easier to read.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="45fff-125">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="45fff-125">Robust Programming</span></span>  
 <span data-ttu-id="45fff-126">Si une procédure déclare un paramètre [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), l’exécution correcte du code peut dépendre de la possibilité de modifier l’élément sous-jacent dans le code appelant.</span><span class="sxs-lookup"><span data-stu-id="45fff-126">If a procedure declares a parameter [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), the correct execution of the code might depend on being able to change the underlying element in the calling code.</span></span> <span data-ttu-id="45fff-127">Si le code appelant substitue ce mécanisme appelant en mettant l’argument entre parenthèses, ou si elle passe un argument non modifiable, la procédure ne peut pas modifier l’élément sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="45fff-127">If the calling code overrides this calling mechanism by enclosing the argument in parentheses, or if it passes a nonmodifiable argument, the procedure cannot change the underlying element.</span></span> <span data-ttu-id="45fff-128">Cela peut produire des résultats inattendus dans le code appelant.</span><span class="sxs-lookup"><span data-stu-id="45fff-128">This might produce unexpected results in the calling code.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="45fff-129">Sécurité .NET Framework</span><span class="sxs-lookup"><span data-stu-id="45fff-129">.NET Framework Security</span></span>  
 <span data-ttu-id="45fff-130">Il existe toujours un risque potentiel en autorisant une procédure modifier la valeur sous-jacente à un argument dans le code appelant.</span><span class="sxs-lookup"><span data-stu-id="45fff-130">There is always a potential risk in allowing a procedure to change the value underlying an argument in the calling code.</span></span> <span data-ttu-id="45fff-131">Assurez-vous que cette valeur pour être modifiée et préparez-vous à vérifier la validité avant de l’utiliser.</span><span class="sxs-lookup"><span data-stu-id="45fff-131">Make sure you expect this value to be changed, and be prepared to check it for validity before using it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45fff-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="45fff-132">See Also</span></span>  
 <span data-ttu-id="45fff-133">[Procédures](./index.md) </span><span class="sxs-lookup"><span data-stu-id="45fff-133">[Procedures](./index.md) </span></span>  
<span data-ttu-id="45fff-134"> [Arguments et paramètres de procédure](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="45fff-134"> [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="45fff-135"> [Comment : passer des Arguments à une procédure](./how-to-pass-arguments-to-a-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="45fff-135"> [How to: Pass Arguments to a Procedure](./how-to-pass-arguments-to-a-procedure.md) </span></span>  
<span data-ttu-id="45fff-136"> [Passage des Arguments par valeur et par référence](./passing-arguments-by-value-and-by-reference.md) </span><span class="sxs-lookup"><span data-stu-id="45fff-136"> [Passing Arguments by Value and by Reference](./passing-arguments-by-value-and-by-reference.md) </span></span>  
<span data-ttu-id="45fff-137"> [Différences entre les Arguments modifiables et non modifiables](./differences-between-modifiable-and-nonmodifiable-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="45fff-137"> [Differences Between Modifiable and Nonmodifiable Arguments](./differences-between-modifiable-and-nonmodifiable-arguments.md) </span></span>  
<span data-ttu-id="45fff-138"> [Différences entre le passage d’un Argument par valeur et par référence](./differences-between-passing-an-argument-by-value-and-by-reference.md) </span><span class="sxs-lookup"><span data-stu-id="45fff-138"> [Differences Between Passing an Argument By Value and By Reference](./differences-between-passing-an-argument-by-value-and-by-reference.md) </span></span>  
<span data-ttu-id="45fff-139"> [Comment : modifier la valeur d’un Argument de procédure](./how-to-change-the-value-of-a-procedure-argument.md) </span><span class="sxs-lookup"><span data-stu-id="45fff-139"> [How to: Change the Value of a Procedure Argument](./how-to-change-the-value-of-a-procedure-argument.md) </span></span>  
<span data-ttu-id="45fff-140"> [Comment : protéger un Argument de procédure contre les modifications de valeur](./how-to-protect-a-procedure-argument-against-value-changes.md) </span><span class="sxs-lookup"><span data-stu-id="45fff-140"> [How to: Protect a Procedure Argument Against Value Changes](./how-to-protect-a-procedure-argument-against-value-changes.md) </span></span>  
<span data-ttu-id="45fff-141"> [Passage des Arguments par Position et par nom](./passing-arguments-by-position-and-by-name.md) </span><span class="sxs-lookup"><span data-stu-id="45fff-141"> [Passing Arguments by Position and by Name](./passing-arguments-by-position-and-by-name.md) </span></span>  
<span data-ttu-id="45fff-142"> [Types valeur et types référence](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)</span><span class="sxs-lookup"><span data-stu-id="45fff-142"> [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)</span></span>
