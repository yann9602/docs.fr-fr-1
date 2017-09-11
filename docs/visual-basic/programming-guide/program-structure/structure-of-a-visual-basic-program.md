---
title: "Structure d’un programme Visual Basic | Documents Microsoft"
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
- conditional compilation, Visual Basic
- program structure, Visual Basic
- procedures, structure
- Visual Basic code, program structure
ms.assetid: ad0c6531-d762-4c77-a700-de16b07b6119
caps.latest.revision: 17
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
ms.openlocfilehash: 3e16ea51d0f766fcb5866cde89e5384a153ac050
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="structure-of-a-visual-basic-program"></a><span data-ttu-id="62c5e-102">Structure d'un programme Visual Basic</span><span class="sxs-lookup"><span data-stu-id="62c5e-102">Structure of a Visual Basic Program</span></span>
<span data-ttu-id="62c5e-103">Un [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] programme est développé à partir de blocs de construction standard.</span><span class="sxs-lookup"><span data-stu-id="62c5e-103">A [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] program is built up from standard building blocks.</span></span> <span data-ttu-id="62c5e-104">A *solution* comprend un ou plusieurs projets.</span><span class="sxs-lookup"><span data-stu-id="62c5e-104">A *solution* comprises one or more projects.</span></span> <span data-ttu-id="62c5e-105">A *projet* à son tour peut contenir un ou plusieurs assemblys.</span><span class="sxs-lookup"><span data-stu-id="62c5e-105">A *project* in turn can contain one or more assemblies.</span></span> <span data-ttu-id="62c5e-106">Chaque *assembly* est compilé à partir d’un ou plusieurs fichiers source.</span><span class="sxs-lookup"><span data-stu-id="62c5e-106">Each *assembly* is compiled from one or more source files.</span></span> <span data-ttu-id="62c5e-107">A *fichier source* fournit la définition et l’implémentation de classes, structures, modules et interfaces qui contiennent l’ensemble de votre code.</span><span class="sxs-lookup"><span data-stu-id="62c5e-107">A *source file* provides the definition and implementation of classes, structures, modules, and interfaces, which ultimately contain all your code.</span></span>  
  
 <span data-ttu-id="62c5e-108">Pour plus d’informations sur ces blocs de construction d’un [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] programme, voir [Solutions et projets](https://docs.microsoft.com/visualstudio/ide/solutions-and-projects-in-visual-studio) et [assemblys et le Global Assembly Cache](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md).</span><span class="sxs-lookup"><span data-stu-id="62c5e-108">For more information about these building blocks of a [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] program, see [Solutions and Projects](https://docs.microsoft.com/visualstudio/ide/solutions-and-projects-in-visual-studio) and [Assemblies and the Global Assembly Cache](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md).</span></span>  
  
## <a name="file-level-programming-elements"></a><span data-ttu-id="62c5e-109">Éléments de programmation au niveau des fichiers</span><span class="sxs-lookup"><span data-stu-id="62c5e-109">File-Level Programming Elements</span></span>  
 <span data-ttu-id="62c5e-110">Lorsque vous démarrez un projet ou un fichier et que vous ouvrez l’éditeur de code, vous consultez du code déjà en place et dans l’ordre correct.</span><span class="sxs-lookup"><span data-stu-id="62c5e-110">When you start a project or file and open the code editor, you see some code already in place and in the correct order.</span></span> <span data-ttu-id="62c5e-111">Tout code que vous écrivez doit respecter la séquence suivante :</span><span class="sxs-lookup"><span data-stu-id="62c5e-111">Any code that you write should follow the following sequence:</span></span>  
  
1.  <span data-ttu-id="62c5e-112">`Option`instructions</span><span class="sxs-lookup"><span data-stu-id="62c5e-112">`Option` statements</span></span>  
  
2.  <span data-ttu-id="62c5e-113">`Imports`instructions</span><span class="sxs-lookup"><span data-stu-id="62c5e-113">`Imports` statements</span></span>  
  
3.  <span data-ttu-id="62c5e-114">`Namespace`instructions et les éléments de niveau de l’espace de noms</span><span class="sxs-lookup"><span data-stu-id="62c5e-114">`Namespace` statements and namespace-level elements</span></span>  
  
 <span data-ttu-id="62c5e-115">Si vous entrez les instructions dans un ordre différent, peuvent entraîner des erreurs de compilation.</span><span class="sxs-lookup"><span data-stu-id="62c5e-115">If you enter statements in a different order, compilation errors can result.</span></span>  
  
 <span data-ttu-id="62c5e-116">Un programme peut également contenir des instructions de compilation conditionnelle.</span><span class="sxs-lookup"><span data-stu-id="62c5e-116">A program can also contain conditional compilation statements.</span></span> <span data-ttu-id="62c5e-117">Vous pouvez séparer ces éléments dans le fichier source entre les instructions de la séquence précédente.</span><span class="sxs-lookup"><span data-stu-id="62c5e-117">You can intersperse these in the source file among the statements of the preceding sequence.</span></span>  
  
### <a name="option-statements"></a><span data-ttu-id="62c5e-118">Instructions option</span><span class="sxs-lookup"><span data-stu-id="62c5e-118">Option Statements</span></span>  
 <span data-ttu-id="62c5e-119">`Option`les instructions définissent les règles de base pour le code suivant, ce qui évite les erreurs de syntaxe et de logique.</span><span class="sxs-lookup"><span data-stu-id="62c5e-119">`Option` statements establish ground rules for subsequent code, helping prevent syntax and logic errors.</span></span> <span data-ttu-id="62c5e-120">Le [Option Explicit, instruction](../../../visual-basic/language-reference/statements/option-explicit-statement.md) garantit que toutes les variables sont déclarées et orthographiés correctement, ce qui réduit le temps de débogage.</span><span class="sxs-lookup"><span data-stu-id="62c5e-120">The [Option Explicit Statement](../../../visual-basic/language-reference/statements/option-explicit-statement.md) ensures that all variables are declared and spelled correctly, which reduces debugging time.</span></span> <span data-ttu-id="62c5e-121">Le [Option Strict, instruction](../../../visual-basic/language-reference/statements/option-strict-statement.md) contribue à minimiser les pertes de données et les erreurs logique qui peuvent se produire lorsque vous travaillez avec des variables de différents types de données.</span><span class="sxs-lookup"><span data-stu-id="62c5e-121">The [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md) helps to minimize logic errors and data loss that can occur when you work between variables of different data types.</span></span> <span data-ttu-id="62c5e-122">Le [instruction Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md) spécifie les façon dont les chaînes sont comparées aux autres, en fonction de leur `Binary` ou `Text` valeurs.</span><span class="sxs-lookup"><span data-stu-id="62c5e-122">The [Option Compare Statement](../../../visual-basic/language-reference/statements/option-compare-statement.md) specifies the way strings are compared to each other, based on either their `Binary` or `Text` values.</span></span>  
  
### <a name="imports-statements"></a><span data-ttu-id="62c5e-123">Instructions Imports</span><span class="sxs-lookup"><span data-stu-id="62c5e-123">Imports Statements</span></span>  
 <span data-ttu-id="62c5e-124">Vous pouvez inclure un [Imports, instruction (.NET Namespace et Type)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) pour importer des noms définis à l’extérieur de votre projet.</span><span class="sxs-lookup"><span data-stu-id="62c5e-124">You can include an [Imports Statement (.NET Namespace and Type)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) to import names defined outside your project.</span></span> <span data-ttu-id="62c5e-125">Un `Imports` instruction permet à votre code faire référence à des classes et d’autres types définis dans l’espace de noms importé sans devoir les qualifier.</span><span class="sxs-lookup"><span data-stu-id="62c5e-125">An `Imports` statement allows your code to refer to classes and other types defined within the imported namespace, without having to qualify them.</span></span> <span data-ttu-id="62c5e-126">Vous pouvez utiliser autant `Imports` instructions selon le cas.</span><span class="sxs-lookup"><span data-stu-id="62c5e-126">You can use as many `Imports` statements as appropriate.</span></span> <span data-ttu-id="62c5e-127">Pour plus d’informations, consultez [références et l’instruction Imports](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md).</span><span class="sxs-lookup"><span data-stu-id="62c5e-127">For more information, see [References and the Imports Statement](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md).</span></span>  
  
### <a name="namespace-statements"></a><span data-ttu-id="62c5e-128">Instructions Namespace</span><span class="sxs-lookup"><span data-stu-id="62c5e-128">Namespace Statements</span></span>  
 <span data-ttu-id="62c5e-129">Espaces de noms vous aident à organisez et classer vos éléments de programmation pour faciliter leur regroupement et l’accès à.</span><span class="sxs-lookup"><span data-stu-id="62c5e-129">Namespaces help you organize and classify your programming elements for ease of grouping and accessing.</span></span> <span data-ttu-id="62c5e-130">Vous utilisez la [Namespace instruction](../../../visual-basic/language-reference/statements/namespace-statement.md) pour classer les instructions suivantes dans un espace de noms particulier.</span><span class="sxs-lookup"><span data-stu-id="62c5e-130">You use the [Namespace Statement](../../../visual-basic/language-reference/statements/namespace-statement.md) to classify the following statements within a particular namespace.</span></span> <span data-ttu-id="62c5e-131">Pour plus d’informations, consultez [espaces de noms dans Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="62c5e-131">For more information, see [Namespaces in Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md).</span></span>  
  
### <a name="conditional-compilation-statements"></a><span data-ttu-id="62c5e-132">Instructions de Compilation conditionnelle</span><span class="sxs-lookup"><span data-stu-id="62c5e-132">Conditional Compilation Statements</span></span>  
 <span data-ttu-id="62c5e-133">Instructions de compilation conditionnelles peuvent apparaître quasiment n’importe où dans votre fichier source.</span><span class="sxs-lookup"><span data-stu-id="62c5e-133">Conditional compilation statements can appear almost anywhere in your source file.</span></span> <span data-ttu-id="62c5e-134">Elles entraînent des parties de votre code doit être inclus ou exclu au moment de la compilation en fonction de certaines conditions.</span><span class="sxs-lookup"><span data-stu-id="62c5e-134">They cause parts of your code to be included or excluded at compile time depending on certain conditions.</span></span> <span data-ttu-id="62c5e-135">Vous pouvez également les utiliser pour déboguer votre application, car le code conditionnel s’exécute uniquement en mode débogage.</span><span class="sxs-lookup"><span data-stu-id="62c5e-135">You can also use them for debugging your application, because conditional code runs in debugging mode only.</span></span> <span data-ttu-id="62c5e-136">Pour plus d’informations, consultez [Compilation conditionnelle](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md).</span><span class="sxs-lookup"><span data-stu-id="62c5e-136">For more information, see [Conditional Compilation](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md).</span></span>  
  
## <a name="namespace-level-programming-elements"></a><span data-ttu-id="62c5e-137">Éléments de programmation au niveau du Namespace</span><span class="sxs-lookup"><span data-stu-id="62c5e-137">Namespace-Level Programming Elements</span></span>  
 <span data-ttu-id="62c5e-138">Classes, structures et modules contient tout le code dans votre fichier source.</span><span class="sxs-lookup"><span data-stu-id="62c5e-138">Classes, structures, and modules contain all the code in your source file.</span></span> <span data-ttu-id="62c5e-139">Ils sont *au niveau de l’espace de noms* éléments qui peuvent apparaître dans un espace de noms ou au niveau du fichier source.</span><span class="sxs-lookup"><span data-stu-id="62c5e-139">They are *namespace-level* elements, which can appear within a namespace or at the source file level.</span></span> <span data-ttu-id="62c5e-140">Ils contiennent les déclarations de tous les autres éléments de programmation.</span><span class="sxs-lookup"><span data-stu-id="62c5e-140">They hold the declarations of all other programming elements.</span></span> <span data-ttu-id="62c5e-141">Les interfaces, qui définissent les signatures d’élément mais ne fournissent aucune implémentation, apparaissent également au niveau du module.</span><span class="sxs-lookup"><span data-stu-id="62c5e-141">Interfaces, which define element signatures but provide no implementation, also appear at module level.</span></span> <span data-ttu-id="62c5e-142">Pour plus d’informations sur les éléments au niveau du module, consultez les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="62c5e-142">For more information on the module-level elements, see the following:</span></span>  
  
-   [<span data-ttu-id="62c5e-143">Class (instruction)</span><span class="sxs-lookup"><span data-stu-id="62c5e-143">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
-   [<span data-ttu-id="62c5e-144">Structure (instruction)</span><span class="sxs-lookup"><span data-stu-id="62c5e-144">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
-   [<span data-ttu-id="62c5e-145">Module (instruction)</span><span class="sxs-lookup"><span data-stu-id="62c5e-145">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)  
  
-   [<span data-ttu-id="62c5e-146">Interface (instruction)</span><span class="sxs-lookup"><span data-stu-id="62c5e-146">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 <span data-ttu-id="62c5e-147">Les éléments de données au niveau de l’espace de noms sont les énumérations et les délégués.</span><span class="sxs-lookup"><span data-stu-id="62c5e-147">Data elements at namespace level are enumerations and delegates.</span></span>  
  
## <a name="module-level-programming-elements"></a><span data-ttu-id="62c5e-148">Éléments de programmation au niveau du module</span><span class="sxs-lookup"><span data-stu-id="62c5e-148">Module-Level Programming Elements</span></span>  
 <span data-ttu-id="62c5e-149">Les procédures, les opérateurs, les propriétés et les événements sont les seuls éléments de programmation qui peuvent contenir du code exécutable (instructions qui effectuent des actions en cours d’exécution).</span><span class="sxs-lookup"><span data-stu-id="62c5e-149">Procedures, operators, properties, and events are the only programming elements that can hold executable code (statements that perform actions at run time).</span></span> <span data-ttu-id="62c5e-150">Ils sont le *au niveau du module* éléments de votre programme.</span><span class="sxs-lookup"><span data-stu-id="62c5e-150">They are the *module-level* elements of your program.</span></span> <span data-ttu-id="62c5e-151">Pour plus d’informations sur les éléments au niveau de la procédure, consultez les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="62c5e-151">For more information on the procedure-level elements, see the following:</span></span>  
  
-   [<span data-ttu-id="62c5e-152">Function (instruction)</span><span class="sxs-lookup"><span data-stu-id="62c5e-152">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
-   [<span data-ttu-id="62c5e-153">Sub (instruction)</span><span class="sxs-lookup"><span data-stu-id="62c5e-153">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
-   [<span data-ttu-id="62c5e-154">Declare (instruction)</span><span class="sxs-lookup"><span data-stu-id="62c5e-154">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
-   [<span data-ttu-id="62c5e-155">Operator (instruction)</span><span class="sxs-lookup"><span data-stu-id="62c5e-155">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
-   [<span data-ttu-id="62c5e-156">Property (instruction)</span><span class="sxs-lookup"><span data-stu-id="62c5e-156">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
-   [<span data-ttu-id="62c5e-157">Event (instruction)</span><span class="sxs-lookup"><span data-stu-id="62c5e-157">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 <span data-ttu-id="62c5e-158">Les éléments de données au niveau du module sont les variables, de constantes, énumérations et délégués.</span><span class="sxs-lookup"><span data-stu-id="62c5e-158">Data elements at module level are variables, constants, enumerations, and delegates.</span></span>  
  
## <a name="procedure-level-programming-elements"></a><span data-ttu-id="62c5e-159">Éléments de programmation au niveau procédure</span><span class="sxs-lookup"><span data-stu-id="62c5e-159">Procedure-Level Programming Elements</span></span>  
 <span data-ttu-id="62c5e-160">La plupart du contenu de *au niveau procédure* éléments sont des instructions exécutables qui constituent le code d’exécution de votre programme.</span><span class="sxs-lookup"><span data-stu-id="62c5e-160">Most of the contents of *procedure-level* elements are executable statements, which constitute the run-time code of your program.</span></span> <span data-ttu-id="62c5e-161">Tout le code exécutable doit être dans une procédure (`Function`, `Sub`, `Operator`, `Get`, `Set`, `AddHandler`, `RemoveHandler`, `RaiseEvent`).</span><span class="sxs-lookup"><span data-stu-id="62c5e-161">All executable code must be in some procedure (`Function`, `Sub`, `Operator`, `Get`, `Set`, `AddHandler`, `RemoveHandler`, `RaiseEvent`).</span></span> <span data-ttu-id="62c5e-162">Pour plus d’informations, consultez [instructions](../../../visual-basic/programming-guide/language-features/statements.md).</span><span class="sxs-lookup"><span data-stu-id="62c5e-162">For more information, see [Statements](../../../visual-basic/programming-guide/language-features/statements.md).</span></span>  
  
 <span data-ttu-id="62c5e-163">Éléments de données au niveau de la procédure sont limités aux constantes et variables locales.</span><span class="sxs-lookup"><span data-stu-id="62c5e-163">Data elements at procedure level are limited to local variables and constants.</span></span>  
  
## <a name="the-main-procedure"></a><span data-ttu-id="62c5e-164">La procédure principale</span><span class="sxs-lookup"><span data-stu-id="62c5e-164">The Main Procedure</span></span>  
 <span data-ttu-id="62c5e-165">Le `Main` procédure est le premier code à exécuter lorsque votre application a été chargée.</span><span class="sxs-lookup"><span data-stu-id="62c5e-165">The `Main` procedure is the first code to run when your application has been loaded.</span></span> <span data-ttu-id="62c5e-166">`Main`sert de point de départ et de contrôle général pour votre application.</span><span class="sxs-lookup"><span data-stu-id="62c5e-166">`Main` serves as the starting point and overall control for your application.</span></span> <span data-ttu-id="62c5e-167">Il existe quatre types de `Main`:</span><span class="sxs-lookup"><span data-stu-id="62c5e-167">There are four varieties of `Main`:</span></span>  
  
-   `Sub Main()`  
  
-   `Sub Main(ByVal cmdArgs() As String)`  
  
-   `Function Main() As Integer`  
  
-   `Function Main(ByVal cmdArgs() As String) As Integer`  
  
 <span data-ttu-id="62c5e-168">Le plus courant de cette procédure est `Sub Main()`.</span><span class="sxs-lookup"><span data-stu-id="62c5e-168">The most common variety of this procedure is `Sub Main()`.</span></span> <span data-ttu-id="62c5e-169">Pour plus d’informations, consultez [procédure Main dans Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md).</span><span class="sxs-lookup"><span data-stu-id="62c5e-169">For more information, see [Main Procedure in Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62c5e-170">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="62c5e-170">See Also</span></span>  
 <span data-ttu-id="62c5e-171">[Procédure Main dans Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="62c5e-171">[Main Procedure in Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md) </span></span>  
<span data-ttu-id="62c5e-172"> [Conventions d’affectation de noms de Visual Basic](../../../visual-basic/programming-guide/program-structure/naming-conventions.md) </span><span class="sxs-lookup"><span data-stu-id="62c5e-172"> [Visual Basic Naming Conventions](../../../visual-basic/programming-guide/program-structure/naming-conventions.md) </span></span>  
<span data-ttu-id="62c5e-173"> [Restrictions liées à Visual Basic](../../../visual-basic/programming-guide/program-structure/limitations.md)</span><span class="sxs-lookup"><span data-stu-id="62c5e-173"> [Visual Basic Limitations](../../../visual-basic/programming-guide/program-structure/limitations.md)</span></span>
