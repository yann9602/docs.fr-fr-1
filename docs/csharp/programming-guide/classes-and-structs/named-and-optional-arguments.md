---
title: "Arguments nommés et facultatifs (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- namedParameter_CSharpKeyword
- cs_namedParameter
dev_langs:
- CSharp
helpviewer_keywords:
- parameters [C#], named
- named arguments [C#]
- arguments [C#], named
- optional arguments [C#]
- arguments [C#], optional
- parameters [C#], optional
- named and optional arguments [C#]
ms.assetid: 839c960c-c2dc-4d05-af4d-ca5428e54008
caps.latest.revision: 43
author: BillWagner
ms.author: wiwagn
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
ms.translationtype: HT
ms.sourcegitcommit: 0dc2fcee3903b80816c98bab47e2b9a2e5ef78b0
ms.openlocfilehash: a7f05e3e0b19bf6457989f8db2b46741cf6b28c1
ms.contentlocale: fr-fr
ms.lasthandoff: 08/28/2017

---
# <a name="named-and-optional-arguments-c-programming-guide"></a><span data-ttu-id="146b0-102">Arguments nommés et facultatifs (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="146b0-102">Named and Optional Arguments (C# Programming Guide)</span></span>
[!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)]<span data-ttu-id="146b0-103"> introduit des arguments nommés et facultatifs.</span><span class="sxs-lookup"><span data-stu-id="146b0-103"> introduces named and optional arguments.</span></span> <span data-ttu-id="146b0-104">Les *arguments nommés* vous permettent de spécifier un argument pour un paramètre particulier en associant l’argument avec le nom du paramètre plutôt qu’avec la position du paramètre dans la liste de paramètres.</span><span class="sxs-lookup"><span data-stu-id="146b0-104">*Named arguments* enable you to specify an argument for a particular parameter by associating the argument with the parameter's name rather than with the parameter's position in the parameter list.</span></span> <span data-ttu-id="146b0-105">Les *arguments facultatifs* vous permettent d’omettre des arguments pour certains paramètres.</span><span class="sxs-lookup"><span data-stu-id="146b0-105">*Optional arguments* enable you to omit arguments for some parameters.</span></span> <span data-ttu-id="146b0-106">Les deux techniques peuvent être utilisées avec les méthodes, les indexeurs, les constructeurs et les délégués.</span><span class="sxs-lookup"><span data-stu-id="146b0-106">Both techniques can be used with methods, indexers, constructors, and delegates.</span></span>  
  
 <span data-ttu-id="146b0-107">Quand vous utilisez des arguments nommés et facultatifs, ils sont évalués selon leur ordre d’affichage dans la liste d’arguments, et non dans la liste de paramètres.</span><span class="sxs-lookup"><span data-stu-id="146b0-107">When you use named and optional arguments, the arguments are evaluated in the order in which they appear in the argument list, not the parameter list.</span></span>  
  
 <span data-ttu-id="146b0-108">La combinaison de paramètres nommés et facultatifs vous permet de fournir des arguments uniquement pour certains paramètres d’une liste de paramètres facultatifs.</span><span class="sxs-lookup"><span data-stu-id="146b0-108">Named and optional parameters, when used together, enable you to supply arguments for only a few parameters from a list of optional parameters.</span></span> <span data-ttu-id="146b0-109">Cette fonctionnalité facilite considérablement les appels aux interfaces COM telles que les API Microsoft Office Automation.</span><span class="sxs-lookup"><span data-stu-id="146b0-109">This capability greatly facilitates calls to COM interfaces such as the Microsoft Office Automation APIs.</span></span>  
  
## <a name="named-arguments"></a><span data-ttu-id="146b0-110">Arguments nommés</span><span class="sxs-lookup"><span data-stu-id="146b0-110">Named Arguments</span></span>  
 <span data-ttu-id="146b0-111">Avec les arguments nommés, vous n’avez plus à mémoriser ou à rechercher l’ordre des paramètres dans les listes de paramètres des méthodes appelées.</span><span class="sxs-lookup"><span data-stu-id="146b0-111">Named arguments free you from the need to remember or to look up the order of parameters in the parameter lists of called methods.</span></span> <span data-ttu-id="146b0-112">Vous pouvez spécifier le paramètre de chaque argument par son nom.</span><span class="sxs-lookup"><span data-stu-id="146b0-112">The parameter for each argument can be specified by parameter name.</span></span> <span data-ttu-id="146b0-113">Par exemple, vous pouvez appeler une fonction qui calcule l’indice de masse corporelle (IMC) à l’aide de la méthode standard consistant à envoyer les arguments du poids et de la taille par position, dans l’ordre défini par la fonction.</span><span class="sxs-lookup"><span data-stu-id="146b0-113">For example, a function that calculates body mass index (BMI) can be called in the standard way by sending arguments for weight and height by position, in the order defined by the function.</span></span>  
  
 `CalculateBMI(123, 64);`  
  
 <span data-ttu-id="146b0-114">Si vous ne vous souvenez pas de l’ordre des paramètres, mais que vous connaissez leur nom, vous pouvez envoyer les arguments dans l’ordre que vous voulez (le poids ou la taille en premier).</span><span class="sxs-lookup"><span data-stu-id="146b0-114">If you do not remember the order of the parameters but you do know their names, you can send the arguments in either order, weight first or height first.</span></span>  
  
 `CalculateBMI(weight: 123, height: 64);`  
  
 `CalculateBMI(height: 64, weight: 123);`  
  
 <span data-ttu-id="146b0-115">Les arguments nommés améliorent également la lisibilité de votre code en identifiant ce que chaque argument représente.</span><span class="sxs-lookup"><span data-stu-id="146b0-115">Named arguments also improve the readability of your code by identifying what each argument represents.</span></span>  
  
 <span data-ttu-id="146b0-116">Un argument nommé peut suivre des arguments de position, comme illustré ici.</span><span class="sxs-lookup"><span data-stu-id="146b0-116">A named argument can follow positional arguments, as shown here.</span></span>  
  
 `CalculateBMI(123, height: 64);`  
  
 <span data-ttu-id="146b0-117">À l’inverse, un argument de position ne peut pas suivre un argument nommé.</span><span class="sxs-lookup"><span data-stu-id="146b0-117">However, a positional argument cannot follow a named argument.</span></span> <span data-ttu-id="146b0-118">Par exemple, l’instruction suivante provoque une erreur du compilateur.</span><span class="sxs-lookup"><span data-stu-id="146b0-118">The following statement causes a compiler error.</span></span>  
  
 `//CalculateBMI(weight: 123, 64);`  
  
## <a name="example"></a><span data-ttu-id="146b0-119">Exemple</span><span class="sxs-lookup"><span data-stu-id="146b0-119">Example</span></span>  
 <span data-ttu-id="146b0-120">Le code suivant implémente les exemples de cette section.</span><span class="sxs-lookup"><span data-stu-id="146b0-120">The following code implements the examples from this section.</span></span>  
  
 <span data-ttu-id="146b0-121">[!code-cs[csProgGuideNamedAndOptional#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="146b0-121">[!code-cs[csProgGuideNamedAndOptional#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_1.cs)]</span></span>  
  
## <a name="optional-arguments"></a><span data-ttu-id="146b0-122">Arguments facultatifs</span><span class="sxs-lookup"><span data-stu-id="146b0-122">Optional Arguments</span></span>  
 <span data-ttu-id="146b0-123">La définition d’une méthode, d’un constructeur, d’un indexeur ou d’un délégué peut spécifier que ses paramètres sont obligatoires ou facultatifs.</span><span class="sxs-lookup"><span data-stu-id="146b0-123">The definition of a method, constructor, indexer, or delegate can specify that its parameters are required or that they are optional.</span></span> <span data-ttu-id="146b0-124">Chaque appel doit fournir des arguments pour tous les paramètres obligatoires, mais peut omettre les arguments des paramètres facultatifs.</span><span class="sxs-lookup"><span data-stu-id="146b0-124">Any call must provide arguments for all required parameters, but can omit arguments for optional parameters.</span></span>  
  
 <span data-ttu-id="146b0-125">Dans sa définition, chaque paramètre facultatif a une valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="146b0-125">Each optional parameter has a default value as part of its definition.</span></span> <span data-ttu-id="146b0-126">Si aucun argument n’est envoyé pour ce paramètre, la valeur par défaut est utilisée.</span><span class="sxs-lookup"><span data-stu-id="146b0-126">If no argument is sent for that parameter, the default value is used.</span></span> <span data-ttu-id="146b0-127">Une valeur par défaut doit être l’un des types d’expressions suivants :</span><span class="sxs-lookup"><span data-stu-id="146b0-127">A default value must be one of the following types of expressions:</span></span>  
  
-   <span data-ttu-id="146b0-128">une expression constante ;</span><span class="sxs-lookup"><span data-stu-id="146b0-128">a constant expression;</span></span>  
  
-   <span data-ttu-id="146b0-129">une expression de la forme `new ValType()`, où `ValType` est un type valeur (par exemple, [enum](../../../csharp/language-reference/keywords/enum.md) ou [struct](../../../csharp/programming-guide/classes-and-structs/structs.md)) ;</span><span class="sxs-lookup"><span data-stu-id="146b0-129">an expression of the form `new ValType()`, where `ValType` is a value type, such as an [enum](../../../csharp/language-reference/keywords/enum.md) or a [struct](../../../csharp/programming-guide/classes-and-structs/structs.md);</span></span>  
  
-   <span data-ttu-id="146b0-130">une expression de la forme [default(ValType)](../../../csharp/programming-guide/statements-expressions-operators/default-value-expressions.md), où `ValType` est un type valeur.</span><span class="sxs-lookup"><span data-stu-id="146b0-130">an expression of the form [default(ValType)](../../../csharp/programming-guide/statements-expressions-operators/default-value-expressions.md),  where `ValType` is a value type.</span></span>  
  
 <span data-ttu-id="146b0-131">Les paramètres facultatifs sont définis à la fin de la liste de paramètres, après tous les paramètres obligatoires.</span><span class="sxs-lookup"><span data-stu-id="146b0-131">Optional parameters are defined at the end of the parameter list, after any required parameters.</span></span> <span data-ttu-id="146b0-132">Si l’appelant fournit un argument pour l’un des paramètres d’une série de paramètres facultatifs, il doit fournir des arguments pour tous les paramètres facultatifs précédents.</span><span class="sxs-lookup"><span data-stu-id="146b0-132">If the caller provides an argument for any one of a succession of optional parameters, it must provide arguments for all preceding optional parameters.</span></span> <span data-ttu-id="146b0-133">Les intervalles séparés par des virgules ne sont pas autorisés dans la liste d’arguments.</span><span class="sxs-lookup"><span data-stu-id="146b0-133">Comma-separated gaps in the argument list are not supported.</span></span> <span data-ttu-id="146b0-134">Par exemple, dans le code suivant, la méthode d’instance `ExampleMethod` est définie avec un paramètre obligatoire et deux paramètres facultatifs.</span><span class="sxs-lookup"><span data-stu-id="146b0-134">For example, in the following code, instance method `ExampleMethod` is defined with one required and two optional parameters.</span></span>  
  
 <span data-ttu-id="146b0-135">[!code-cs[csProgGuideNamedAndOptional#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="146b0-135">[!code-cs[csProgGuideNamedAndOptional#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_2.cs)]</span></span>  
  
 <span data-ttu-id="146b0-136">L’appel suivant à `ExampleMethod` provoque une erreur du compilateur, car un argument est fourni pour le troisième paramètre, mais pas pour le deuxième.</span><span class="sxs-lookup"><span data-stu-id="146b0-136">The following call to `ExampleMethod` causes a compiler error, because an argument is provided for the third parameter but not for the second.</span></span>  
  
 `//anExample.ExampleMethod(3, ,4);`  
  
 <span data-ttu-id="146b0-137">Toutefois, si vous connaissez le nom du troisième paramètre, vous pouvez utiliser un argument nommé pour effectuer la tâche.</span><span class="sxs-lookup"><span data-stu-id="146b0-137">However, if you know the name of the third parameter, you can use a named argument to accomplish the task.</span></span>  
  
 `anExample.ExampleMethod(3, optionalint: 4);`  
  
 <span data-ttu-id="146b0-138">IntelliSense indique les paramètres facultatifs par des crochets, comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="146b0-138">IntelliSense uses brackets to indicate optional parameters, as shown in the following illustration.</span></span>  
  
 <span data-ttu-id="146b0-139">![Info express IntelliSense pour la méthode ExampleMethod.](../../../csharp/programming-guide/classes-and-structs/media/optional_parameters.png "Optional_Parameters")</span><span class="sxs-lookup"><span data-stu-id="146b0-139">![IntelliSense Quick Info for method ExampleMethod.](../../../csharp/programming-guide/classes-and-structs/media/optional_parameters.png "Optional_Parameters")</span></span>  
<span data-ttu-id="146b0-140">Paramètres facultatifs dans ExampleMethod</span><span class="sxs-lookup"><span data-stu-id="146b0-140">Optional parameters in ExampleMethod</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="146b0-141">Vous pouvez aussi déclarer des paramètres facultatifs à l’aide de la classe <xref:System.Runtime.InteropServices.OptionalAttribute> .NET.</span><span class="sxs-lookup"><span data-stu-id="146b0-141">You can also declare optional parameters by using the .NET <xref:System.Runtime.InteropServices.OptionalAttribute> class.</span></span> <span data-ttu-id="146b0-142">Les paramètres `OptionalAttribute` ne nécessitent pas de valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="146b0-142">`OptionalAttribute` parameters do not require a default value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="146b0-143">Exemple</span><span class="sxs-lookup"><span data-stu-id="146b0-143">Example</span></span>  
 <span data-ttu-id="146b0-144">Dans l’exemple suivant, le constructeur associé à `ExampleClass` a un seul paramètre, qui est facultatif.</span><span class="sxs-lookup"><span data-stu-id="146b0-144">In the following example, the constructor for `ExampleClass` has one parameter, which is optional.</span></span> <span data-ttu-id="146b0-145">La méthode d’instance `ExampleMethod` a un paramètre obligatoire (`required`) et deux paramètres facultatifs (`optionalstr` et `optionalint`).</span><span class="sxs-lookup"><span data-stu-id="146b0-145">Instance method `ExampleMethod` has one required parameter, `required`, and two optional parameters, `optionalstr` and `optionalint`.</span></span> <span data-ttu-id="146b0-146">Le code dans `Main` montre les différentes façons dont le constructeur et la méthode peuvent être appelés.</span><span class="sxs-lookup"><span data-stu-id="146b0-146">The code in `Main` shows the different ways in which the constructor and method can be invoked.</span></span>  
  
 <span data-ttu-id="146b0-147">[!code-cs[csProgGuideNamedAndOptional#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="146b0-147">[!code-cs[csProgGuideNamedAndOptional#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_3.cs)]</span></span>  
  
## <a name="com-interfaces"></a><span data-ttu-id="146b0-148">Interfaces COM</span><span class="sxs-lookup"><span data-stu-id="146b0-148">COM Interfaces</span></span>  
 <span data-ttu-id="146b0-149">Avec la prise en charge des objets dynamiques et d’autres améliorations, les arguments nommés et facultatifs améliorent nettement l’interopérabilité avec les API COM, telles que les API Office Automation.</span><span class="sxs-lookup"><span data-stu-id="146b0-149">Named and optional arguments, along with support for dynamic objects and other enhancements, greatly improve interoperability with COM APIs, such as Office Automation APIs.</span></span>  
  
 <span data-ttu-id="146b0-150">Par exemple, la méthode [AutoFormat](http://go.microsoft.com/fwlink/?LinkId=148201) dans l’interface [Range](http://go.microsoft.com/fwlink/?LinkId=148196) de Microsoft Office Excel comporte sept paramètres, qui sont tous facultatifs.</span><span class="sxs-lookup"><span data-stu-id="146b0-150">For example, the [AutoFormat](http://go.microsoft.com/fwlink/?LinkId=148201) method in the Microsoft Office Excel [Range](http://go.microsoft.com/fwlink/?LinkId=148196) interface has seven parameters, all of which are optional.</span></span> <span data-ttu-id="146b0-151">Ces paramètres sont indiqués dans l’illustration suivante.</span><span class="sxs-lookup"><span data-stu-id="146b0-151">These parameters are shown in the following illustration.</span></span>  
  
 <span data-ttu-id="146b0-152">![Info express IntelliSense pour la méthode AutoFormat.](../../../csharp/programming-guide/classes-and-structs/media/autoformat_parameters.png "AutoFormat_Parameters")</span><span class="sxs-lookup"><span data-stu-id="146b0-152">![IntelliSense Quick Info for the AutoFormat method.](../../../csharp/programming-guide/classes-and-structs/media/autoformat_parameters.png "AutoFormat_Parameters")</span></span>  
<span data-ttu-id="146b0-153">Paramètres AutoFormat</span><span class="sxs-lookup"><span data-stu-id="146b0-153">AutoFormat parameters</span></span>  
  
 <span data-ttu-id="146b0-154">Dans C# 3.0 et les versions antérieures, un argument est obligatoire pour chaque paramètre, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="146b0-154">In C# 3.0 and earlier versions, an argument is required for each parameter, as shown in the following example.</span></span>  
  
 <span data-ttu-id="146b0-155">[!code-cs[csProgGuideNamedAndOptional#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="146b0-155">[!code-cs[csProgGuideNamedAndOptional#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_4.cs)]</span></span>  
  
 <span data-ttu-id="146b0-156">Toutefois, vous pouvez considérablement simplifier l’appel à `AutoFormat` en utilisant les arguments nommés et facultatifs introduits dans C# 4.0.</span><span class="sxs-lookup"><span data-stu-id="146b0-156">However, you can greatly simplify the call to `AutoFormat` by using named and optional arguments, introduced in C# 4.0.</span></span> <span data-ttu-id="146b0-157">Les paramètres nommés et facultatifs vous permettent d’omettre l’argument d’un paramètre obligatoire si vous ne souhaitez pas modifier la valeur par défaut du paramètre.</span><span class="sxs-lookup"><span data-stu-id="146b0-157">Named and optional arguments enable you to omit the argument for an optional parameter if you do not want to change the parameter's default value.</span></span> <span data-ttu-id="146b0-158">Dans l’appel suivant, une valeur est spécifiée pour un seul des sept paramètres.</span><span class="sxs-lookup"><span data-stu-id="146b0-158">In the following call, a value is specified for only one of the seven parameters.</span></span>  
  
 <span data-ttu-id="146b0-159">[!code-cs[csProgGuideNamedAndOptional#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="146b0-159">[!code-cs[csProgGuideNamedAndOptional#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/named-and-optional-arguments_5.cs)]</span></span>  
  
 <span data-ttu-id="146b0-160">Pour plus d’informations et obtenir des exemples, consultez [Guide pratique pour utiliser des arguments nommés et facultatifs dans la programmation Office](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md) et [Guide pratique pour accéder aux objets Office Interop à l’aide des fonctionnalités Visual C#](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md).</span><span class="sxs-lookup"><span data-stu-id="146b0-160">For more information and examples, see [How to: Use Named and Optional Arguments in Office Programming](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md) and [How to: Access Office Interop Objects by Using Visual C# Features](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md).</span></span>  
  
## <a name="overload-resolution"></a><span data-ttu-id="146b0-161">Résolution de surcharge</span><span class="sxs-lookup"><span data-stu-id="146b0-161">Overload Resolution</span></span>  
 <span data-ttu-id="146b0-162">L’utilisation d’arguments nommés et facultatifs affecte la résolution de surcharge des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="146b0-162">Use of named and optional arguments affects overload resolution in the following ways:</span></span>  
  
-   <span data-ttu-id="146b0-163">Une méthode, un indexeur ou un constructeur est un candidat pour l’exécution si chacun de ses paramètres est facultatif ou correspond, par son nom ou sa position, à un seul argument dans l’instruction appelante, et que cet argument peut être converti vers le type du paramètre.</span><span class="sxs-lookup"><span data-stu-id="146b0-163">A method, indexer, or constructor is a candidate for execution if each of its parameters either is optional or corresponds, by name or by position, to a single argument in the calling statement, and that argument can be converted to the type of the parameter.</span></span>  
  
-   <span data-ttu-id="146b0-164">Si plusieurs candidats sont trouvés, les règles de résolution de surcharge des conversions préférées sont appliquées aux arguments qui sont explicitement spécifiés.</span><span class="sxs-lookup"><span data-stu-id="146b0-164">If more than one candidate is found, overload resolution rules for preferred conversions are applied to the arguments that are explicitly specified.</span></span> <span data-ttu-id="146b0-165">Les arguments omis pour les paramètres facultatifs sont ignorés.</span><span class="sxs-lookup"><span data-stu-id="146b0-165">Omitted arguments for optional parameters are ignored.</span></span>  
  
-   <span data-ttu-id="146b0-166">Si deux candidats sont jugés de qualité équivalente, la préférence va à celui qui n’a pas de paramètres facultatifs pour lesquels des arguments ont été omis dans l’appel.</span><span class="sxs-lookup"><span data-stu-id="146b0-166">If two candidates are judged to be equally good, preference goes to a candidate that does not have optional parameters for which arguments were omitted in the call.</span></span> <span data-ttu-id="146b0-167">Ceci s’explique par l’application d’une préférence générale dans la résolution de surcharge en faveur des candidats qui ont le moins de paramètres.</span><span class="sxs-lookup"><span data-stu-id="146b0-167">This is a consequence of a general preference in overload resolution for candidates that have fewer parameters.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="146b0-168">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="146b0-168">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="146b0-169">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="146b0-169">See Also</span></span>  
 <span data-ttu-id="146b0-170">[Guide pratique pour utiliser des arguments nommés et facultatifs dans la programmation Office](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md) </span><span class="sxs-lookup"><span data-stu-id="146b0-170">[How to: Use Named and Optional Arguments in Office Programming](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md) </span></span>  
 <span data-ttu-id="146b0-171">[Utilisation du type dynamic](../../../csharp/programming-guide/types/using-type-dynamic.md) </span><span class="sxs-lookup"><span data-stu-id="146b0-171">[Using Type dynamic](../../../csharp/programming-guide/types/using-type-dynamic.md) </span></span>  
 <span data-ttu-id="146b0-172">[Utilisation de constructeurs](../../../csharp/programming-guide/classes-and-structs/using-constructors.md) </span><span class="sxs-lookup"><span data-stu-id="146b0-172">[Using Constructors](../../../csharp/programming-guide/classes-and-structs/using-constructors.md) </span></span>  
 [<span data-ttu-id="146b0-173">Utilisation d’indexeurs</span><span class="sxs-lookup"><span data-stu-id="146b0-173">Using Indexers</span></span>](../../../csharp/programming-guide/indexers/using-indexers.md)

