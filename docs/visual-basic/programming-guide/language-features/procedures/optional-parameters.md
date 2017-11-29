---
title: "Paramètres facultatifs (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- parameters [Visual Basic], optional
- Visual Basic code, procedures
- procedures [Visual Basic], optional arguments
- optional arguments
- named arguments [Visual Basic], and optional arguments
- optional parameters
- Optional keyword [Visual Basic], optional arguments
- arguments [Visual Basic], optional
- optional arguments [Visual Basic], and named arguments
ms.assetid: 398d2845-1069-4e94-b934-a73b545c8b87
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e57023f594cfe4cd79d59cc8541fcf18018de0ee
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="optional-parameters-visual-basic"></a><span data-ttu-id="4e318-102">Paramètres facultatifs (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4e318-102">Optional Parameters (Visual Basic)</span></span>
<span data-ttu-id="4e318-103">Vous pouvez spécifier qu’un paramètre de procédure est facultatif et qu’il n’est pas nécessaire de fournir un argument lorsque la procédure est appelée.</span><span class="sxs-lookup"><span data-stu-id="4e318-103">You can specify that a procedure parameter is optional and no argument has to be supplied for it when the procedure is called.</span></span> <span data-ttu-id="4e318-104">*Paramètres facultatifs* sont indiquées par le `Optional` mot clé dans la définition de procédure.</span><span class="sxs-lookup"><span data-stu-id="4e318-104">*Optional parameters* are indicated by the `Optional` keyword in the procedure definition.</span></span> <span data-ttu-id="4e318-105">Les règles suivantes s'appliquent :</span><span class="sxs-lookup"><span data-stu-id="4e318-105">The following rules apply:</span></span>  
  
-   <span data-ttu-id="4e318-106">Chaque paramètre facultatif dans la définition de la procédure doit spécifier une valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="4e318-106">Every optional parameter in the procedure definition must specify a default value.</span></span>  
  
-   <span data-ttu-id="4e318-107">La valeur par défaut d'un paramètre facultatif doit être une expression constante.</span><span class="sxs-lookup"><span data-stu-id="4e318-107">The default value for an optional parameter must be a constant expression.</span></span>  
  
-   <span data-ttu-id="4e318-108">Tous les paramètres qui suivent un paramètre facultatif dans la définition de la procédure doivent également être facultatifs.</span><span class="sxs-lookup"><span data-stu-id="4e318-108">Every parameter following an optional parameter in the procedure definition must also be optional.</span></span>  
  
 <span data-ttu-id="4e318-109">La syntaxe suivante montre une déclaration de procédure comprenant un paramètre facultatif :</span><span class="sxs-lookup"><span data-stu-id="4e318-109">The following syntax shows a procedure declaration with an optional parameter:</span></span>  
  
```vb  
Sub name(ByVal parameter1 As datatype1, Optional ByVal parameter2 As datatype2 = defaultvalue)  
```  
  
## <a name="calling-procedures-with-optional-parameters"></a><span data-ttu-id="4e318-110">Appel de procédures à l'aide de paramètres facultatifs</span><span class="sxs-lookup"><span data-stu-id="4e318-110">Calling Procedures with Optional Parameters</span></span>  
 <span data-ttu-id="4e318-111">Lorsque vous appelez une procédure à l'aide d'un paramètre facultatif, vous pouvez choisir de fournir l'argument ou non.</span><span class="sxs-lookup"><span data-stu-id="4e318-111">When you call a procedure with an optional parameter, you can choose whether to supply the argument.</span></span> <span data-ttu-id="4e318-112">Dans le cas contraire, la procédure utilise la valeur par défaut déclarée pour ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="4e318-112">If you do not, the procedure uses the default value declared for that parameter.</span></span>  
  
 <span data-ttu-id="4e318-113">Pour omettre un ou plusieurs arguments facultatifs dans la liste des arguments, utilisez des virgules successives afin de marquer leurs positions.</span><span class="sxs-lookup"><span data-stu-id="4e318-113">When you omit one or more optional arguments in the argument list, you use successive commas to mark their positions.</span></span> <span data-ttu-id="4e318-114">L'exemple d'appel suivant fournit le premier et le quatrième argument, mais pas le deuxième ni le troisième :</span><span class="sxs-lookup"><span data-stu-id="4e318-114">The following example call supplies the first and fourth arguments but not the second or third:</span></span>  
  
```vb  
Sub name(argument 1, , , argument 4)  
```  
  
 <span data-ttu-id="4e318-115">L'exemple suivant effectue plusieurs appels à la fonction `MsgBox`.</span><span class="sxs-lookup"><span data-stu-id="4e318-115">The following example makes several calls to the `MsgBox` function.</span></span> <span data-ttu-id="4e318-116">`MsgBox` comporte un paramètre obligatoire et deux paramètres facultatifs.</span><span class="sxs-lookup"><span data-stu-id="4e318-116">`MsgBox` has one required parameter and two optional parameters.</span></span>  
  
 <span data-ttu-id="4e318-117">Le premier appel à `MsgBox` fournit les trois arguments dans l'ordre dans lequel `MsgBox` les définit.</span><span class="sxs-lookup"><span data-stu-id="4e318-117">The first call to `MsgBox` supplies all three arguments in the order that `MsgBox` defines them.</span></span> <span data-ttu-id="4e318-118">Le deuxième appel fournit uniquement l'argument requis.</span><span class="sxs-lookup"><span data-stu-id="4e318-118">The second call supplies only the required argument.</span></span> <span data-ttu-id="4e318-119">Le troisième et le quatrième appel fournissent le premier et le troisième argument.</span><span class="sxs-lookup"><span data-stu-id="4e318-119">The third and fourth calls supply the first and third arguments.</span></span> <span data-ttu-id="4e318-120">Le troisième appel le fait par position et le quatrième appel le fait par nom.</span><span class="sxs-lookup"><span data-stu-id="4e318-120">The third call does this by position, and the fourth call does it by name.</span></span>  
  
 [!code-vb[VbVbcnProcedures#47](./codesnippet/VisualBasic/optional-parameters_1.vb)]  
  
## <a name="determining-whether-an-optional-argument-is-present"></a><span data-ttu-id="4e318-121">Détermination de la présence d’un argument facultatif</span><span class="sxs-lookup"><span data-stu-id="4e318-121">Determining Whether an Optional Argument Is Present</span></span>  
 <span data-ttu-id="4e318-122">Une procédure ne peut pas détecter au moment de l'exécution si un argument donné a été omis ou si le code appelant a explicitement fourni la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="4e318-122">A procedure cannot detect at run time whether a given argument has been omitted or the calling code has explicitly supplied the default value.</span></span> <span data-ttu-id="4e318-123">Pour établir cette distinction, vous pouvez définir une valeur improbable comme valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="4e318-123">If you need to make this distinction, you can set an unlikely value as the default.</span></span> <span data-ttu-id="4e318-124">La procédure suivante définit le paramètre facultatif `office`et sa valeur par défaut, les tests `QJZ`, pour voir s’il a été omis dans l’appel :</span><span class="sxs-lookup"><span data-stu-id="4e318-124">The following procedure defines the optional parameter `office`, and tests for its default value, `QJZ`, to see if it has been omitted in the call:</span></span>  
  
 [!code-vb[VbVbcnProcedures#46](./codesnippet/VisualBasic/optional-parameters_2.vb)]  
  
 <span data-ttu-id="4e318-125">Si le paramètre facultatif est un type référence tel que `String`, vous pouvez utiliser `Nothing` comme valeur par défaut, à condition qu'il ne s'agisse pas d'une valeur attendue pour l'argument.</span><span class="sxs-lookup"><span data-stu-id="4e318-125">If the optional parameter is a reference type such as a `String`, you can use `Nothing` as the default value, provided this is not an expected value for the argument.</span></span>  
  
## <a name="optional-parameters-and-overloading"></a><span data-ttu-id="4e318-126">Paramètres facultatifs et surcharge</span><span class="sxs-lookup"><span data-stu-id="4e318-126">Optional Parameters and Overloading</span></span>  
 <span data-ttu-id="4e318-127">La surcharge est une autre méthode permettant de définir une procédure à l'aide de paramètres facultatifs.</span><span class="sxs-lookup"><span data-stu-id="4e318-127">Another way to define a procedure with optional parameters is to use overloading.</span></span> <span data-ttu-id="4e318-128">Si vous disposez d'un seul paramètre facultatif, vous pouvez définir deux versions surchargées de la procédure, l'une avec le paramètre et l'autre sans.</span><span class="sxs-lookup"><span data-stu-id="4e318-128">If you have one optional parameter, you can define two overloaded versions of the procedure, one accepting the parameter and one without it.</span></span> <span data-ttu-id="4e318-129">Cette approche se complique au fur et à mesure que le nombre de paramètres facultatifs augmente.</span><span class="sxs-lookup"><span data-stu-id="4e318-129">This approach becomes more complicated as the number of optional parameters increases.</span></span> <span data-ttu-id="4e318-130">Cependant, vous avez l’avantage de savoir avec certitude si le programme appelant a fourni chaque argument facultatif.</span><span class="sxs-lookup"><span data-stu-id="4e318-130">However, its advantage is that you can be absolutely sure whether the calling program supplied each optional argument.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e318-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4e318-131">See Also</span></span>  
 [<span data-ttu-id="4e318-132">Procédures</span><span class="sxs-lookup"><span data-stu-id="4e318-132">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="4e318-133">Paramètres et arguments d’une procédure</span><span class="sxs-lookup"><span data-stu-id="4e318-133">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="4e318-134">Passage d’un argument par valeur et par référence</span><span class="sxs-lookup"><span data-stu-id="4e318-134">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)  
 [<span data-ttu-id="4e318-135">Passage des arguments par position et par nom</span><span class="sxs-lookup"><span data-stu-id="4e318-135">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)  
 [<span data-ttu-id="4e318-136">tableaux de paramètres</span><span class="sxs-lookup"><span data-stu-id="4e318-136">Parameter Arrays</span></span>](./parameter-arrays.md)  
 [<span data-ttu-id="4e318-137">Surcharge de procédure</span><span class="sxs-lookup"><span data-stu-id="4e318-137">Procedure Overloading</span></span>](./procedure-overloading.md)  
 [<span data-ttu-id="4e318-138">Optional</span><span class="sxs-lookup"><span data-stu-id="4e318-138">Optional</span></span>](../../../../visual-basic/language-reference/modifiers/optional.md)  
 [<span data-ttu-id="4e318-139">ParamArray</span><span class="sxs-lookup"><span data-stu-id="4e318-139">ParamArray</span></span>](../../../../visual-basic/language-reference/modifiers/paramarray.md)
