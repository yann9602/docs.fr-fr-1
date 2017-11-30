---
title: "Comment : forcer le passage d’un argument par valeur (Visual Basic)"
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
- Visual Basic code, procedures
- arguments [Visual Basic], ByVal
- arguments [Visual Basic], passing by value
- procedure parameters
- procedures [Visual Basic], calling
- arguments [Visual Basic], in parentheses
- procedure arguments [Visual Basic], in parentheses
- arguments [Visual Basic], changing value
ms.assetid: 77b4f2d2-1055-4c2f-a521-874d1db86946
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fdb2df7e114f49c23db9f5b322ca9dd32135ac88
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-force-an-argument-to-be-passed-by-value-visual-basic"></a><span data-ttu-id="d77d0-102">Comment : forcer le passage d’un argument par valeur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d77d0-102">How to: Force an Argument to Be Passed by Value (Visual Basic)</span></span>
<span data-ttu-id="d77d0-103">La déclaration de procédure détermine le mécanisme de passage.</span><span class="sxs-lookup"><span data-stu-id="d77d0-103">The procedure declaration determines the passing mechanism.</span></span> <span data-ttu-id="d77d0-104">Si un paramètre est déclaré [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] doit passer l’argument correspondant par référence.</span><span class="sxs-lookup"><span data-stu-id="d77d0-104">If a parameter is declared [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] expects to pass the corresponding argument by reference.</span></span> <span data-ttu-id="d77d0-105">Cela permet à la procédure modifier la valeur de l’élément de programmation sous-jacent à l’argument dans le code appelant.</span><span class="sxs-lookup"><span data-stu-id="d77d0-105">This allows the procedure to change the value of the programming element underlying the argument in the calling code.</span></span> <span data-ttu-id="d77d0-106">Si vous souhaitez protéger l’élément sous-jacent contre une telle modification, vous pouvez remplacer le `ByRef` mécanisme de passage de la procédure appeler en mettant le nom de l’argument entre parenthèses.</span><span class="sxs-lookup"><span data-stu-id="d77d0-106">If you wish to protect the underlying element against such change, you can override the `ByRef` passing mechanism in the procedure call by enclosing the argument name in parentheses.</span></span> <span data-ttu-id="d77d0-107">Ces parenthèses sont ajoutent les parenthèses entourant la liste d’arguments dans l’appel.</span><span class="sxs-lookup"><span data-stu-id="d77d0-107">These parentheses are in addition to the parentheses enclosing the argument list in the call.</span></span>  
  
 <span data-ttu-id="d77d0-108">Le code appelant ne peut pas remplacer un [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) mécanisme.</span><span class="sxs-lookup"><span data-stu-id="d77d0-108">The calling code cannot override a [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) mechanism.</span></span>  
  
### <a name="to-force-an-argument-to-be-passed-by-value"></a><span data-ttu-id="d77d0-109">Pour forcer un argument à passer par valeur</span><span class="sxs-lookup"><span data-stu-id="d77d0-109">To force an argument to be passed by value</span></span>  
  
-   <span data-ttu-id="d77d0-110">Si le paramètre correspondant est déclaré `ByVal` dans la procédure, vous n’avez pas besoin de prendre des mesures supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="d77d0-110">If the corresponding parameter is declared `ByVal` in the procedure, you do not need to take any additional steps.</span></span> [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="d77d0-111">doit déjà passer l’argument par valeur.</span><span class="sxs-lookup"><span data-stu-id="d77d0-111"> already expects to pass the argument by value.</span></span>  
  
-   <span data-ttu-id="d77d0-112">Si le paramètre correspondant est déclaré `ByRef` dans la procédure, mettez l’argument entre parenthèses dans l’appel de procédure.</span><span class="sxs-lookup"><span data-stu-id="d77d0-112">If the corresponding parameter is declared `ByRef` in the procedure, enclose the argument in parentheses in the procedure call.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d77d0-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="d77d0-113">Example</span></span>  
 <span data-ttu-id="d77d0-114">L’exemple suivant substitue un `ByRef` déclaration de paramètre.</span><span class="sxs-lookup"><span data-stu-id="d77d0-114">The following example overrides a `ByRef` parameter declaration.</span></span> <span data-ttu-id="d77d0-115">Dans l’appel qui force `ByVal`, notez les deux niveaux de parenthèses.</span><span class="sxs-lookup"><span data-stu-id="d77d0-115">In the call that forces `ByVal`, note the two levels of parentheses.</span></span>  
  
 [!code-vb[VbVbcnProcedures#39](./codesnippet/VisualBasic/how-to-force-an-argument-to-be-passed-by-value_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#40](./codesnippet/VisualBasic/how-to-force-an-argument-to-be-passed-by-value_2.vb)]  
  
 <span data-ttu-id="d77d0-116">Lorsque `str` est placée entre parenthèses supplémentaires dans la liste d’arguments, le `setNewString` procédure ne peut pas modifier sa valeur dans le code appelant, et `MsgBox` affiche « Ne peut pas être remplacé si passé ByVal ».</span><span class="sxs-lookup"><span data-stu-id="d77d0-116">When `str` is enclosed in extra parentheses within the argument list, the `setNewString` procedure cannot change its value in the calling code, and `MsgBox` displays "Cannot be replaced if passed ByVal".</span></span> <span data-ttu-id="d77d0-117">Lorsque `str` n’est pas placé entre parenthèses supplémentaires, la procédure peut le modifier, et `MsgBox` affiche « Il s’agit d’une nouvelle valeur pour l’argument inString. »</span><span class="sxs-lookup"><span data-stu-id="d77d0-117">When `str` is not enclosed in extra parentheses, the procedure can change it, and `MsgBox` displays "This is a new value for the inString argument."</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d77d0-118">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="d77d0-118">Compiling the Code</span></span>  
 <span data-ttu-id="d77d0-119">Lorsque vous passez une variable par référence, vous devez utiliser le `ByRef` mot clé pour spécifier ce mécanisme.</span><span class="sxs-lookup"><span data-stu-id="d77d0-119">When you pass a variable by reference, you must use the `ByRef` keyword to specify this mechanism.</span></span>  
  
 <span data-ttu-id="d77d0-120">La valeur par défaut dans [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] consiste à passer des arguments par valeur.</span><span class="sxs-lookup"><span data-stu-id="d77d0-120">The default in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] is to pass arguments by value.</span></span> <span data-ttu-id="d77d0-121">Toutefois, il est conseillé pour inclure la [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) ou [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) mot clé with chaque paramètre déclaré.</span><span class="sxs-lookup"><span data-stu-id="d77d0-121">However, it is good programming practice to include either the [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) keyword with every declared parameter.</span></span> <span data-ttu-id="d77d0-122">Cela rend votre code plus facile à lire.</span><span class="sxs-lookup"><span data-stu-id="d77d0-122">This makes your code easier to read.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="d77d0-123">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="d77d0-123">Robust Programming</span></span>  
 <span data-ttu-id="d77d0-124">Si une procédure déclare un paramètre [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), l’exécution correcte du code peut dépendre de la possibilité de modifier l’élément sous-jacent dans le code appelant.</span><span class="sxs-lookup"><span data-stu-id="d77d0-124">If a procedure declares a parameter [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), the correct execution of the code might depend on being able to change the underlying element in the calling code.</span></span> <span data-ttu-id="d77d0-125">Si le code appelant substitue ce mécanisme appelant en mettant l’argument entre parenthèses, ou si elle passe un argument non modifiable, la procédure ne peut pas modifier l’élément sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="d77d0-125">If the calling code overrides this calling mechanism by enclosing the argument in parentheses, or if it passes a nonmodifiable argument, the procedure cannot change the underlying element.</span></span> <span data-ttu-id="d77d0-126">Cela peut produire des résultats inattendus dans le code appelant.</span><span class="sxs-lookup"><span data-stu-id="d77d0-126">This might produce unexpected results in the calling code.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="d77d0-127">Sécurité .NET Framework</span><span class="sxs-lookup"><span data-stu-id="d77d0-127">.NET Framework Security</span></span>  
 <span data-ttu-id="d77d0-128">Il est toujours un risque potentiel pour autoriser une procédure modifier la valeur sous-jacente à un argument dans le code appelant.</span><span class="sxs-lookup"><span data-stu-id="d77d0-128">There is always a potential risk in allowing a procedure to change the value underlying an argument in the calling code.</span></span> <span data-ttu-id="d77d0-129">Assurez-vous que cette valeur pour être modifiée et préparez-vous à vérifier la validité avant de l’utiliser.</span><span class="sxs-lookup"><span data-stu-id="d77d0-129">Make sure you expect this value to be changed, and be prepared to check it for validity before using it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d77d0-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d77d0-130">See Also</span></span>  
 [<span data-ttu-id="d77d0-131">Procédures</span><span class="sxs-lookup"><span data-stu-id="d77d0-131">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="d77d0-132">Paramètres et arguments d’une procédure</span><span class="sxs-lookup"><span data-stu-id="d77d0-132">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="d77d0-133">Guide pratique : passer des arguments à une procédure</span><span class="sxs-lookup"><span data-stu-id="d77d0-133">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)  
 [<span data-ttu-id="d77d0-134">Passage d’un argument par valeur et par référence</span><span class="sxs-lookup"><span data-stu-id="d77d0-134">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)  
 [<span data-ttu-id="d77d0-135">Différences entre les arguments modifiables et non modifiables</span><span class="sxs-lookup"><span data-stu-id="d77d0-135">Differences Between Modifiable and Nonmodifiable Arguments</span></span>](./differences-between-modifiable-and-nonmodifiable-arguments.md)  
 [<span data-ttu-id="d77d0-136">Différences entre le passage d’un argument par valeur et par référence</span><span class="sxs-lookup"><span data-stu-id="d77d0-136">Differences Between Passing an Argument By Value and By Reference</span></span>](./differences-between-passing-an-argument-by-value-and-by-reference.md)  
 [<span data-ttu-id="d77d0-137">Guide pratique : modifier la valeur d’un argument de la procédure</span><span class="sxs-lookup"><span data-stu-id="d77d0-137">How to: Change the Value of a Procedure Argument</span></span>](./how-to-change-the-value-of-a-procedure-argument.md)  
 [<span data-ttu-id="d77d0-138">Guide pratique : protéger un argument de procédure contre les modifications de valeur</span><span class="sxs-lookup"><span data-stu-id="d77d0-138">How to: Protect a Procedure Argument Against Value Changes</span></span>](./how-to-protect-a-procedure-argument-against-value-changes.md)  
 [<span data-ttu-id="d77d0-139">Passage des arguments par position et par nom</span><span class="sxs-lookup"><span data-stu-id="d77d0-139">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)  
 [<span data-ttu-id="d77d0-140">Types valeur et types référence</span><span class="sxs-lookup"><span data-stu-id="d77d0-140">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
