---
title: "Paramètres et arguments d’une procédure (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], argument lists
- values [Visual Basic], passing to procedures
- arguments [Visual Basic], passing
- procedures [Visual Basic], parameters
- Visual Basic code, argument lists
- Visual Basic code, procedures
- parameters [Visual Basic], Visual Basic procedures
- parameters [Visual Basic], lists
- arguments [Visual Basic], Visual Basic procedures
- arguments [Visual Basic], procedures
- parameter lists [Visual Basic]
- Visual Basic code, parameter lists
- argument lists [Visual Basic]
- procedures [Visual Basic], parameter lists
ms.assetid: ff275aff-aa13-40df-bd4c-63486db8c1e9
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 726667950cfb227a0359bd6238c202883561749c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="procedure-parameters-and-arguments-visual-basic"></a><span data-ttu-id="b3344-102">Paramètres et arguments d’une procédure (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b3344-102">Procedure Parameters and Arguments (Visual Basic)</span></span>
<span data-ttu-id="b3344-103">Dans la plupart des cas, une procédure a besoin des informations sur les circonstances dans lesquelles elle a été appelée.</span><span class="sxs-lookup"><span data-stu-id="b3344-103">In most cases, a procedure needs some information about the circumstances in which it has been called.</span></span> <span data-ttu-id="b3344-104">Une procédure qui exécute des tâches répétitives ou partagées utilise des informations différentes pour chaque appel.</span><span class="sxs-lookup"><span data-stu-id="b3344-104">A procedure that performs repeated or shared tasks uses different information for each call.</span></span> <span data-ttu-id="b3344-105">Ces informations se composent des variables, des constantes et des expressions que vous passez à la procédure lorsque vous appelez.</span><span class="sxs-lookup"><span data-stu-id="b3344-105">This information consists of variables, constants, and expressions that you pass to the procedure when you call it.</span></span>  
  
 <span data-ttu-id="b3344-106">A *paramètre* représente une valeur de la procédure que vous devez fournir lorsque vous appelez.</span><span class="sxs-lookup"><span data-stu-id="b3344-106">A *parameter* represents a value that the procedure expects you to supply when you call it.</span></span> <span data-ttu-id="b3344-107">Déclaration de la procédure définit ses paramètres.</span><span class="sxs-lookup"><span data-stu-id="b3344-107">The procedure's declaration defines its parameters.</span></span>  
  
 <span data-ttu-id="b3344-108">Vous pouvez définir une procédure sans paramètres, un seul paramètre, ou plusieurs.</span><span class="sxs-lookup"><span data-stu-id="b3344-108">You can define a procedure with no parameters, one parameter, or more than one.</span></span> <span data-ttu-id="b3344-109">La partie de la définition de procédure qui spécifie les paramètres est appelée la *liste de paramètres*.</span><span class="sxs-lookup"><span data-stu-id="b3344-109">The part of the procedure definition that specifies the parameters is called the *parameter list*.</span></span>  
  
 <span data-ttu-id="b3344-110">Un *argument* représente la valeur que vous fournissez à un paramètre de procédure lorsque vous appelez la procédure.</span><span class="sxs-lookup"><span data-stu-id="b3344-110">An *argument* represents the value you supply to a procedure parameter when you call the procedure.</span></span> <span data-ttu-id="b3344-111">Le code appelant fournit les arguments lorsqu’il appelle la procédure.</span><span class="sxs-lookup"><span data-stu-id="b3344-111">The calling code supplies the arguments when it calls the procedure.</span></span> <span data-ttu-id="b3344-112">La partie de l’appel de procédure qui spécifie les arguments est appelée la *liste d’arguments*.</span><span class="sxs-lookup"><span data-stu-id="b3344-112">The part of the procedure call that specifies the arguments is called the *argument list*.</span></span>  
  
 <span data-ttu-id="b3344-113">L’illustration suivante montre le code appelant la procédure `safeSquareRoot` à partir de deux emplacements différents.</span><span class="sxs-lookup"><span data-stu-id="b3344-113">The following illustration shows code calling the procedure `safeSquareRoot` from two different places.</span></span> <span data-ttu-id="b3344-114">Le premier appel passe la valeur de la variable `x` (4.0) au paramètre `number`et la valeur de retour dans `root` (2.0) est assignée à la variable `y`.</span><span class="sxs-lookup"><span data-stu-id="b3344-114">The first call passes the value of the variable `x` (4.0) to the parameter `number`, and the return value in `root` (2.0) is assigned to the variable `y`.</span></span> <span data-ttu-id="b3344-115">Le deuxième appel passe la valeur de littéral 9.0 à `number`et affecte la valeur de retour (3.0) à la variable `z`.</span><span class="sxs-lookup"><span data-stu-id="b3344-115">The second call passes the literal value 9.0 to `number`, and assigns the return value (3.0) to variable `z`.</span></span>  
  
 <span data-ttu-id="b3344-116">![Diagramme graphique du passage d’argument au paramètre](./media/parametersargue.gif "ParametersArgue")</span><span class="sxs-lookup"><span data-stu-id="b3344-116">![Graphic diagram of passing argument to parameter](./media/parametersargue.gif "ParametersArgue")</span></span>  
<span data-ttu-id="b3344-117">Passage d’un argument à un paramètre</span><span class="sxs-lookup"><span data-stu-id="b3344-117">Passing an argument to a parameter</span></span>  
  
 <span data-ttu-id="b3344-118">Pour plus d’informations, consultez [les différences entre les paramètres et Arguments](./differences-between-parameters-and-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="b3344-118">For more information, see [Differences Between Parameters and Arguments](./differences-between-parameters-and-arguments.md).</span></span>  
  
## <a name="parameter-data-type"></a><span data-ttu-id="b3344-119">Type de données de paramètre</span><span class="sxs-lookup"><span data-stu-id="b3344-119">Parameter Data Type</span></span>  
 <span data-ttu-id="b3344-120">Vous définissez un type de données pour un paramètre à l’aide de la `As` clause dans sa déclaration.</span><span class="sxs-lookup"><span data-stu-id="b3344-120">You define a data type for a parameter by using the `As` clause in its declaration.</span></span> <span data-ttu-id="b3344-121">Par exemple, la fonction suivante accepte une chaîne et un entier.</span><span class="sxs-lookup"><span data-stu-id="b3344-121">For example, the following function accepts a string and an integer.</span></span>  
  
 [!code-vb[VbVbcnProcedures#32](./codesnippet/VisualBasic/procedure-parameters-and-arguments_1.vb)]  
  
 <span data-ttu-id="b3344-122">Si le commutateur de la vérification de type ([Option Strict, instruction](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) est `Off,` le `As` clause est facultative, sauf si un paramètre l’utilise, tous les paramètres doivent l’utiliser.</span><span class="sxs-lookup"><span data-stu-id="b3344-122">If the type checking switch ([Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) is `Off,` the `As` clause is optional, except that if any one parameter uses it, all parameters must use it.</span></span> <span data-ttu-id="b3344-123">Si la vérification de type est `On`, le `As` clause est requise pour tous les paramètres de procédure.</span><span class="sxs-lookup"><span data-stu-id="b3344-123">If type checking is `On`, the `As` clause is required for all procedure parameters.</span></span>  
  
 <span data-ttu-id="b3344-124">Si le code appelant s’attend à fournir un argument avec un type de données différent de celui de son paramètre correspondant, tel que `Byte` à un `String` paramètre, il doit exécuter l’une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="b3344-124">If the calling code expects to supply an argument with a data type different from that of its corresponding parameter, such as `Byte` to a `String` parameter, it must do one of the following:</span></span>  
  
-   <span data-ttu-id="b3344-125">Fournissez uniquement des arguments avec les types de données qui s’étendent au type de données du paramètre ;</span><span class="sxs-lookup"><span data-stu-id="b3344-125">Supply only arguments with data types that widen to the parameter data type;</span></span>  
  
-   <span data-ttu-id="b3344-126">Définissez `Option Strict Off` pour autoriser les conversions restrictives implicites ; ou</span><span class="sxs-lookup"><span data-stu-id="b3344-126">Set `Option Strict Off` to allow implicit narrowing conversions; or</span></span>  
  
-   <span data-ttu-id="b3344-127">Utilisez un mot clé de conversion pour convertir explicitement le type de données.</span><span class="sxs-lookup"><span data-stu-id="b3344-127">Use a conversion keyword to explicitly convert the data type.</span></span>  
  
### <a name="type-parameters"></a><span data-ttu-id="b3344-128">Paramètres de type</span><span class="sxs-lookup"><span data-stu-id="b3344-128">Type Parameters</span></span>  
 <span data-ttu-id="b3344-129">A *procédure générique* définit également un ou plusieurs *les paramètres de type* en plus de ses paramètres normaux.</span><span class="sxs-lookup"><span data-stu-id="b3344-129">A *generic procedure* also defines one or more *type parameters* in addition to its normal parameters.</span></span> <span data-ttu-id="b3344-130">Une procédure générique permet au code appelant à passer différents types de données chaque fois qu’il appelle la procédure, il peut adapter les types de données sur les exigences de chaque appel individuel.</span><span class="sxs-lookup"><span data-stu-id="b3344-130">A generic procedure allows the calling code to pass different data types each time it calls the procedure, so it can tailor the data types to the requirements of each individual call.</span></span> <span data-ttu-id="b3344-131">Consultez [Generic Procedures in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="b3344-131">See [Generic Procedures in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3344-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b3344-132">See Also</span></span>  
 [<span data-ttu-id="b3344-133">Procédures</span><span class="sxs-lookup"><span data-stu-id="b3344-133">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="b3344-134">Procédures Sub</span><span class="sxs-lookup"><span data-stu-id="b3344-134">Sub Procedures</span></span>](./sub-procedures.md)  
 [<span data-ttu-id="b3344-135">Procédures Function</span><span class="sxs-lookup"><span data-stu-id="b3344-135">Function Procedures</span></span>](./function-procedures.md)  
 [<span data-ttu-id="b3344-136">Procédures de propriété</span><span class="sxs-lookup"><span data-stu-id="b3344-136">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="b3344-137">Procédures d’opérateur</span><span class="sxs-lookup"><span data-stu-id="b3344-137">Operator Procedures</span></span>](./operator-procedures.md)  
 [<span data-ttu-id="b3344-138">Guide pratique : définir un paramètre pour une procédure</span><span class="sxs-lookup"><span data-stu-id="b3344-138">How to: Define a Parameter for a Procedure</span></span>](./how-to-define-a-parameter-for-a-procedure.md)  
 [<span data-ttu-id="b3344-139">Guide pratique : passer des arguments à une procédure</span><span class="sxs-lookup"><span data-stu-id="b3344-139">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)  
 [<span data-ttu-id="b3344-140">Passage d’un argument par valeur et par référence</span><span class="sxs-lookup"><span data-stu-id="b3344-140">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)  
 [<span data-ttu-id="b3344-141">Surcharge de procédure</span><span class="sxs-lookup"><span data-stu-id="b3344-141">Procedure Overloading</span></span>](./procedure-overloading.md)  
 [<span data-ttu-id="b3344-142">Conversions de type dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b3344-142">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
