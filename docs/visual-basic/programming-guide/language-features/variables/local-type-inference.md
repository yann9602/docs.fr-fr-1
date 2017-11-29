---
title: "Inférence de type local (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- local type inference
- vb.TypeInfer
helpviewer_keywords:
- Option Infer statement [Visual Basic]
- local type inference [Visual Basic]
- implicitly-typed local variables [Visual Basic]
- variables [Visual Basic], type inference
- inference [Visual Basic]
- type inference [Visual Basic]
ms.assetid: b8307f18-2e56-4ab3-a45a-826873f400f6
caps.latest.revision: "43"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d753d1fbdc60f70dcf0513d809f28a112243c111
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="local-type-inference-visual-basic"></a><span data-ttu-id="594c8-102">Inférence de type local (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="594c8-102">Local Type Inference (Visual Basic)</span></span>
<span data-ttu-id="594c8-103">Le compilateur Visual Basic utilise *l’inférence de type* pour déterminer les types de données des variables locales déclarées sans un `As` clause.</span><span class="sxs-lookup"><span data-stu-id="594c8-103">The Visual Basic compiler uses *type inference* to determine the data types of local variables declared without an `As` clause.</span></span> <span data-ttu-id="594c8-104">Le compilateur déduit le type de la variable du type de l’expression d’initialisation.</span><span class="sxs-lookup"><span data-stu-id="594c8-104">The compiler infers the type of the variable from the type of the initialization expression.</span></span> <span data-ttu-id="594c8-105">Cela vous permet de déclarer des variables sans déclarer explicitement un type, comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="594c8-105">This enables you to declare variables without explicitly stating a type, as shown in the following example.</span></span> <span data-ttu-id="594c8-106">À la suite les déclarations, les deux `num1` et `num2` sont fortement typées en tant qu’entiers.</span><span class="sxs-lookup"><span data-stu-id="594c8-106">As a result of the declarations, both `num1` and `num2` are strongly typed as integers.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#1](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_1.vb)]  
 
> [!NOTE]
>  <span data-ttu-id="594c8-107">Si vous ne souhaitez pas `num2` dans l’exemple précédent typé comme un `Integer`, vous pouvez spécifier un autre type à l’aide d’une déclaration comme `Dim num3 As Object = 3` ou `Dim num4 As Double = 3`.</span><span class="sxs-lookup"><span data-stu-id="594c8-107">If you do not want `num2` in the previous example to be typed as an `Integer`, you can specify another type by using a declaration like `Dim num3 As Object = 3` or `Dim num4 As Double = 3`.</span></span>  

> [!NOTE]
>  <span data-ttu-id="594c8-108">L’inférence de type peut être utilisé uniquement pour les variables locales non statiques ; Il ne peut pas être utilisé pour déterminer le type des champs de la classe, des propriétés ou des fonctions.</span><span class="sxs-lookup"><span data-stu-id="594c8-108">Type inference can be used only for non-static local variables; it cannot be used to determine the type of class fields, properties, or functions.</span></span>
 
 <span data-ttu-id="594c8-109">Inférence de type local s’applique au niveau de la procédure.</span><span class="sxs-lookup"><span data-stu-id="594c8-109">Local type inference applies at procedure level.</span></span> <span data-ttu-id="594c8-110">Il ne peut pas être utilisé pour déclarer des variables au niveau du module (dans une classe, une structure, un module ou une interface, mais pas dans une procédure ou un bloc).</span><span class="sxs-lookup"><span data-stu-id="594c8-110">It cannot be used to declare variables at module level (within a class, structure, module, or interface but not within a procedure or block).</span></span> <span data-ttu-id="594c8-111">Si `num2` dans l’exemple précédent est un champ d’une classe au lieu d’une variable locale dans une procédure, la déclaration génère une erreur avec `Option Strict` et classe `num2` comme un `Object` avec `Option Strict` désactivé.</span><span class="sxs-lookup"><span data-stu-id="594c8-111">If `num2` in the previous example were a field of a class instead of a local variable in a procedure, the declaration would cause an error with `Option Strict` on, and would classify `num2` as an `Object` with `Option Strict` off.</span></span> <span data-ttu-id="594c8-112">De même, l’inférence de type local ne s’applique pas aux variables de niveau procédure déclarées en tant que `Static`.</span><span class="sxs-lookup"><span data-stu-id="594c8-112">Similarly, local type inference does not apply to procedure level variables declared as `Static`.</span></span>  
  
## <a name="type-inference-vs-late-binding"></a><span data-ttu-id="594c8-113">Visual Studio de l’inférence de type. Liaison tardive</span><span class="sxs-lookup"><span data-stu-id="594c8-113">Type Inference vs. Late Binding</span></span>  
 <span data-ttu-id="594c8-114">Code qui utilise l’inférence de type ressemble au code qui s’appuie sur la liaison tardive.</span><span class="sxs-lookup"><span data-stu-id="594c8-114">Code that uses type inference resembles code that relies on late binding.</span></span> <span data-ttu-id="594c8-115">Toutefois, l’inférence de type type fort à la variable au lieu de laisser sous la forme `Object`.</span><span class="sxs-lookup"><span data-stu-id="594c8-115">However, type inference strongly types the variable instead of leaving it as `Object`.</span></span> <span data-ttu-id="594c8-116">Le compilateur utilise l’initialiseur de variable pour déterminer le type de variable au moment de la compilation pour produire un code à liaison anticipée.</span><span class="sxs-lookup"><span data-stu-id="594c8-116">The compiler uses a variable's initializer to determine the variable's type at compile time to produce early-bound code.</span></span> <span data-ttu-id="594c8-117">Dans l’exemple précédent, `num2`, comme `num1`, est typé comme un `Integer`.</span><span class="sxs-lookup"><span data-stu-id="594c8-117">In the previous example, `num2`, like `num1`, is typed as an `Integer`.</span></span>  
  
 <span data-ttu-id="594c8-118">Le comportement de variables à liaison anticipée diffère de celui des variables à liaison tardive, pour lequel le type est connu uniquement au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="594c8-118">The behavior of early-bound variables differs from that of late-bound variables, for which the type is known only at run time.</span></span> <span data-ttu-id="594c8-119">Connaître que le type tôt permet au compilateur d’identifier les problèmes avant l’exécution, allouer la mémoire précisément et effectuer d’autres optimisations.</span><span class="sxs-lookup"><span data-stu-id="594c8-119">Knowing the type early enables the compiler to identify problems before execution, allocate memory precisely, and perform other optimizations.</span></span> <span data-ttu-id="594c8-120">Liaison anticipée permet également de l’environnement de développement intégré (IDE) pour fournir l’aide d’IntelliSense sur les membres d’un objet Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="594c8-120">Early binding also enables the Visual Basic integrated development environment (IDE) to provide IntelliSense Help about the members of an object.</span></span> <span data-ttu-id="594c8-121">Liaison anticipée est également recommandée pour les performances.</span><span class="sxs-lookup"><span data-stu-id="594c8-121">Early binding is also preferred for performance.</span></span> <span data-ttu-id="594c8-122">C’est parce que toutes les données stockées dans une variable à liaison tardive doivent être encapsulées en tant que type `Object`, ainsi que l’accès aux membres du type au moment de l’exécution ralentit le programme.</span><span class="sxs-lookup"><span data-stu-id="594c8-122">This is because all data stored in a late-bound variable must be wrapped as type `Object`, and accessing members of the type at run time makes the program slower.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="594c8-123">Exemples</span><span class="sxs-lookup"><span data-stu-id="594c8-123">Examples</span></span>  
 <span data-ttu-id="594c8-124">L’inférence de type se produit lorsqu’une variable locale est déclarée sans un `As` clause et initialisé.</span><span class="sxs-lookup"><span data-stu-id="594c8-124">Type inference occurs when a local variable is declared without an `As` clause and initialized.</span></span> <span data-ttu-id="594c8-125">Le compilateur utilise le type de la valeur initiale assignée en tant que le type de la variable.</span><span class="sxs-lookup"><span data-stu-id="594c8-125">The compiler uses the type of the assigned initial value as the type of the variable.</span></span> <span data-ttu-id="594c8-126">Par exemple, chacune des lignes de code suivants déclare une variable de type `String`.</span><span class="sxs-lookup"><span data-stu-id="594c8-126">For example, each of the following lines of code declares a variable of type `String`.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#2](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_2.vb)]  
  
 <span data-ttu-id="594c8-127">Le code suivant illustre deux méthodes pour créer un tableau d’entiers.</span><span class="sxs-lookup"><span data-stu-id="594c8-127">The following code demonstrates two equivalent ways to create an array of integers.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#3](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_3.vb)]  
  
 <span data-ttu-id="594c8-128">Il est pratique d’utiliser l’inférence de type pour déterminer le type d’une variable de contrôle de boucle.</span><span class="sxs-lookup"><span data-stu-id="594c8-128">It is convenient to use type inference to determine the type of a loop control variable.</span></span> <span data-ttu-id="594c8-129">Dans le code suivant, le compilateur déduit que `number` est un `Integer` car `someNumbers2` à partir de l’exemple précédent est un tableau d’entiers.</span><span class="sxs-lookup"><span data-stu-id="594c8-129">In the following code, the compiler infers that `number` is an `Integer` because `someNumbers2` from the previous example is an array of integers.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#4](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_4.vb)]  
  
 <span data-ttu-id="594c8-130">Inférence de type local peut être utilisé dans `Using` instructions pour établir le type de nom de la ressource, comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="594c8-130">Local type inference can be used in `Using` statements to establish the type of the resource name, as the following example demonstrates.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#7](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_5.vb)]  
  
 <span data-ttu-id="594c8-131">Le type d’une variable peut également être déduit à partir des valeurs de retour des fonctions, comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="594c8-131">The type of a variable can also be inferred from the return values of functions, as the following example demonstrates.</span></span> <span data-ttu-id="594c8-132">Les deux `pList1` et `pList2` sont des tableaux de processus, car `Process.GetProcesses` retourne un tableau de processus.</span><span class="sxs-lookup"><span data-stu-id="594c8-132">Both `pList1` and `pList2` are arrays of processes because `Process.GetProcesses` returns an array of processes.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#5](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_6.vb)]  
  
## <a name="option-infer"></a><span data-ttu-id="594c8-133">Option Infer</span><span class="sxs-lookup"><span data-stu-id="594c8-133">Option Infer</span></span>  
 <span data-ttu-id="594c8-134">`Option Infer`vous permet de que spécifier si l’inférence de type local est autorisée dans un fichier particulier.</span><span class="sxs-lookup"><span data-stu-id="594c8-134">`Option Infer` enables you specify whether local type inference is allowed in a particular file.</span></span> <span data-ttu-id="594c8-135">Pour activer ou bloquer l’option, tapez les instructions suivantes au début du fichier.</span><span class="sxs-lookup"><span data-stu-id="594c8-135">To enable or to block the option, type one of the following statements at the start of the file.</span></span>  
  
 `Option Infer On`  
  
 `Option Infer Off`  
  
 <span data-ttu-id="594c8-136">Si vous ne spécifiez pas une valeur pour `Option Infer` dans votre code, la valeur par défaut du compilateur est `Option Infer On`.</span><span class="sxs-lookup"><span data-stu-id="594c8-136">If you do not specify a value for `Option Infer` in your code, the compiler default is `Option Infer On`.</span></span> <span data-ttu-id="594c8-137">Pour les projets mis à niveau à partir de [!INCLUDE[vb_orcas_long](~/includes/vb-orcas-long-md.md)] ou version antérieure, la valeur par défaut du compilateur est `Option Infer Off`.</span><span class="sxs-lookup"><span data-stu-id="594c8-137">For projects upgraded from [!INCLUDE[vb_orcas_long](~/includes/vb-orcas-long-md.md)] or earlier, the compiler default is `Option Infer Off`.</span></span>  
  
 <span data-ttu-id="594c8-138">Si la valeur définie pour `Option Infer` dans un fichier est en conflit avec la valeur définie dans l'IDE ou sur la ligne de commande, la valeur contenue dans le fichier est prioritaire.</span><span class="sxs-lookup"><span data-stu-id="594c8-138">If the value set for `Option Infer` in a file conflicts with the value set in the IDE or on the command line, the value in the file has precedence.</span></span>  
  
 <span data-ttu-id="594c8-139">Pour plus d’informations, consultez [Option Infer, instruction](../../../../visual-basic/language-reference/statements/option-infer-statement.md) et [Page Compiler, Concepteur de projets (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="594c8-139">For more information, see [Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md) and [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="594c8-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="594c8-140">See Also</span></span>  
 [<span data-ttu-id="594c8-141">Types anonymes</span><span class="sxs-lookup"><span data-stu-id="594c8-141">Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [<span data-ttu-id="594c8-142">Liaison anticipée et liaison tardive</span><span class="sxs-lookup"><span data-stu-id="594c8-142">Early and Late Binding</span></span>](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)  
 [<span data-ttu-id="594c8-143">For Each...Next (instruction)</span><span class="sxs-lookup"><span data-stu-id="594c8-143">For Each...Next Statement</span></span>](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)  
 [<span data-ttu-id="594c8-144">For...Next (instruction)</span><span class="sxs-lookup"><span data-stu-id="594c8-144">For...Next Statement</span></span>](../../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [<span data-ttu-id="594c8-145">Option Infer (instruction)</span><span class="sxs-lookup"><span data-stu-id="594c8-145">Option Infer Statement</span></span>](../../../../visual-basic/language-reference/statements/option-infer-statement.md)  
 [<span data-ttu-id="594c8-146">/optioninfer</span><span class="sxs-lookup"><span data-stu-id="594c8-146">/optioninfer</span></span>](../../../../visual-basic/reference/command-line-compiler/optioninfer.md)  
 [<span data-ttu-id="594c8-147">Introduction à LINQ en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="594c8-147">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
