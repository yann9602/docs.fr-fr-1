---
title: "switch, mot clé (référence C#)"
ms.date: 2017-03-07
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- switch_CSharpKeyword
- switch
- case
- case_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- switch statement [C#]
- switch keyword [C#]
- case statement [C#]
- default keyword [C#]
ms.assetid: 44bae8b8-8841-4d85-826b-8a94277daecb
caps.latest.revision: 47
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 387c8c7e44ab818ca97e686330746f50df091bb9
ms.openlocfilehash: 5c151e3bbd46212f1234d46ff05d389f2384ca0e
ms.contentlocale: fr-fr
ms.lasthandoff: 08/01/2017

---
# <a name="switch-c-reference"></a><span data-ttu-id="8606c-102">switch (référence C#)</span><span class="sxs-lookup"><span data-stu-id="8606c-102">switch (C# Reference)</span></span>
<span data-ttu-id="8606c-103">`switch` est une instruction de sélection qui choisit une *section de commutation* unique à exécuter à partir d’une liste de candidats en fonction d’une mise en correspondance de modèle avec l’*expression de correspondance*.</span><span class="sxs-lookup"><span data-stu-id="8606c-103">`switch` is a selection statement that chooses a single *switch section* to execute from a list of candidates based on a pattern match with the *match expression*.</span></span> 
  
 <span data-ttu-id="8606c-104">[!code-cs[switch#1](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch1.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="8606c-104">[!code-cs[switch#1](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch1.cs#1)]</span></span>  

<span data-ttu-id="8606c-105">L’instruction `switch` est souvent utilisée comme alternative à une construction [if-else](if-else.md) si une expression unique est testée en fonction de trois conditions ou plus.</span><span class="sxs-lookup"><span data-stu-id="8606c-105">The `switch` statement is often used as an alternative to an [if-else](if-else.md) construct if a single expression is tested against three or more conditions.</span></span> <span data-ttu-id="8606c-106">Par exemple, l’instruction `switch` suivante détermine laquelle des trois valeurs possibles a été affectée à une variable de type `Color` :</span><span class="sxs-lookup"><span data-stu-id="8606c-106">For example, the following `switch` statement determines whether a variable of type `Color` has one of three values:</span></span> 

<span data-ttu-id="8606c-107">[!code-cs[switch#3](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch3.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="8606c-107">[!code-cs[switch#3](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch3.cs#1)]</span></span> 

<span data-ttu-id="8606c-108">Il est équivalent à l’exemple suivant qui utilise une construction `if` -`else`.</span><span class="sxs-lookup"><span data-stu-id="8606c-108">It is equivalent to the following example that uses an `if`-`else` construct.</span></span> 

<span data-ttu-id="8606c-109">[!code-cs[switch#3a](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch3a.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="8606c-109">[!code-cs[switch#3a](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch3a.cs#1)]</span></span> 

## <a name="the-match-expression"></a><span data-ttu-id="8606c-110">Expression de correspondance</span><span class="sxs-lookup"><span data-stu-id="8606c-110">The match expression</span></span>

<span data-ttu-id="8606c-111">L’expression de correspondance fournit la valeur à mettre en correspondance avec les modèles dans les étiquettes `case`.</span><span class="sxs-lookup"><span data-stu-id="8606c-111">The match expression provides the value to match against the patterns in `case` labels.</span></span> <span data-ttu-id="8606c-112">Sa syntaxe est la suivante :</span><span class="sxs-lookup"><span data-stu-id="8606c-112">Its syntax is:</span></span>

```csharp
   switch (expr)
```

<span data-ttu-id="8606c-113">En C# 6, l’expression de correspondance doit être une expression qui retourne une valeur d’un des types suivants :</span><span class="sxs-lookup"><span data-stu-id="8606c-113">In C# 6, the match expression must be an expression that returns a value of the following types:</span></span>

- <span data-ttu-id="8606c-114">[char](char.md),</span><span class="sxs-lookup"><span data-stu-id="8606c-114">a [char](char.md).</span></span>
- <span data-ttu-id="8606c-115">[string](string.md),</span><span class="sxs-lookup"><span data-stu-id="8606c-115">a [string](string.md).</span></span>
- <span data-ttu-id="8606c-116">[bool](bool.md),</span><span class="sxs-lookup"><span data-stu-id="8606c-116">a [bool](bool.md).</span></span> 
- <span data-ttu-id="8606c-117">valeur intégrale, telle que [int](int.md) ou [long](long.md),</span><span class="sxs-lookup"><span data-stu-id="8606c-117">an integral value, such as an [int](int.md) or a [long](long.md).</span></span>
- <span data-ttu-id="8606c-118">ou valeur [enum](enum.md).</span><span class="sxs-lookup"><span data-stu-id="8606c-118">an [enum](enum.md) value.</span></span>

<span data-ttu-id="8606c-119">À compter de C# 7, l’expression de correspondance peut être toute expression non Null.</span><span class="sxs-lookup"><span data-stu-id="8606c-119">Starting with C# 7, the match expression can be any non-null expression.</span></span>
 
## <a name="the-switch-section"></a><span data-ttu-id="8606c-120">Section de commutation</span><span class="sxs-lookup"><span data-stu-id="8606c-120">The switch section</span></span>
 
 <span data-ttu-id="8606c-121">Une instruction `switch` inclut une ou plusieurs sections de commutation.</span><span class="sxs-lookup"><span data-stu-id="8606c-121">A `switch` statement includes one or more switch sections.</span></span> <span data-ttu-id="8606c-122">Chaque section de commutation contient une ou plusieurs *étiquettes case* suivies d’une ou de plusieurs instructions.</span><span class="sxs-lookup"><span data-stu-id="8606c-122">Each switch section contains one or more *case labels* followed by one or more statements.</span></span> <span data-ttu-id="8606c-123">L'exemple suivant montre une instruction `switch` simple qui a trois sections switch.</span><span class="sxs-lookup"><span data-stu-id="8606c-123">The following example shows a simple `switch` statement that has three switch sections.</span></span> <span data-ttu-id="8606c-124">Chaque section switch a un nom de cas, tel que `case 1:` et une liste de deux instructions.</span><span class="sxs-lookup"><span data-stu-id="8606c-124">Each switch section has one case label, such as `case 1:`, and two statements.</span></span>
 
  <span data-ttu-id="8606c-125">Une instruction `switch` peut inclure un nombre quelconque de sections de commutation, et chaque section peut contenir une ou plusieurs étiquettes case, comme dans l’exemple ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="8606c-125">A `switch` statement can include any number of switch sections, and each section can have one or more case labels, as shown in the following example.</span></span> <span data-ttu-id="8606c-126">Toutefois, deux étiquettes case ne doivent pas contenir la même expression.</span><span class="sxs-lookup"><span data-stu-id="8606c-126">However, no two case labels may contain the same expression.</span></span>  

 <span data-ttu-id="8606c-127">[!code-cs[switch#2](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch2.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="8606c-127">[!code-cs[switch#2](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch2.cs#1)]</span></span>  

 <span data-ttu-id="8606c-128">Une seule section de commutation s’exécute dans une instruction switch.</span><span class="sxs-lookup"><span data-stu-id="8606c-128">Only one switch section in a switch statement executes.</span></span> <span data-ttu-id="8606c-129">C# ne permet pas à l’exécution de passer d’une section switch à la suivante.</span><span class="sxs-lookup"><span data-stu-id="8606c-129">C# does not allow execution to continue from one switch section to the next.</span></span> <span data-ttu-id="8606c-130">Pour cette raison, le code suivant génère une erreur du compilateur, CS0163 : « Le contrôle ne peut pas passer d’une étiquette case (<case label>) à une autre ».</span><span class="sxs-lookup"><span data-stu-id="8606c-130">Because of this, the following code generates a compiler error, CS0163: "Control cannot fall through from one case label (<case label>) to another."</span></span>   

```csharp  
switch (caseSwitch)  
{  
    // The following switch section causes an error.  
    case 1:  
        Console.WriteLine("Case 1...");  
        // Add a break or other jump statement here.  
    case 2:  
        Console.WriteLine("... and/or Case 2");  
        break;  
}  
```  
<span data-ttu-id="8606c-131">Si cela est nécessaire, il est possible de procéder en quittant explicitement la section de commutation à l’aide d’une instruction [break](break.md), [goto](goto.md) ou [return](return.md).</span><span class="sxs-lookup"><span data-stu-id="8606c-131">This requirement is usually met by explicitly exiting the switch section by using a [break](break.md), [goto](goto.md), or [return](return.md) statement.</span></span> <span data-ttu-id="8606c-132">Toutefois, le code suivant est également valide, car il garantit que le contrôle du programme ne peut pas passer à la section de commutation `default`.</span><span class="sxs-lookup"><span data-stu-id="8606c-132">However, the following code is also valid, because it ensures that program control cannot fall through to the `default` switch section.</span></span>
  
 <span data-ttu-id="8606c-133">[!code-cs[switch#4](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch4.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="8606c-133">[!code-cs[switch#4](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch4.cs#1)]</span></span>    
  
 <span data-ttu-id="8606c-134">L’exécution de la liste d’instructions dans la section de commutation avec une étiquette case qui correspond à l’expression de correspondance commence avec la première instruction et continue en suivant la liste d’instructions, en général jusqu’à ce qu’une instruction de saut, telle que `break`, `goto case`, `goto label`, `return` ou `throw`, soit atteinte.</span><span class="sxs-lookup"><span data-stu-id="8606c-134">Execution of the statement list in the switch section with a case label that matches the match expression begins with the first statement and proceeds through the statement list, typically until a jump statement, such as a `break`, `goto case`, `goto label`, `return`, or `throw`, is reached.</span></span> <span data-ttu-id="8606c-135">À ce stade, le contrôle est transféré hors de l'instruction `switch` ou vers un autre nom de cas.</span><span class="sxs-lookup"><span data-stu-id="8606c-135">At that point, control is transferred outside the `switch` statement or to another case label.</span></span> <span data-ttu-id="8606c-136">Si une instruction `goto` est utilisée, elle doit transférer le contrôle à une étiquette constante.</span><span class="sxs-lookup"><span data-stu-id="8606c-136">A `goto` statement, if it is used, must transfer control to a constant label.</span></span> <span data-ttu-id="8606c-137">Cette restriction est nécessaire, car tenter de transférer le contrôle à une étiquette non constante peut avoir des effets indésirables, tels que le transfert du contrôle à un emplacement inattendu dans le code ou la création d’une boucle sans fin.</span><span class="sxs-lookup"><span data-stu-id="8606c-137">This restriction is necessary, since attempting to transfer control to a non-constant label can have undesirable side-effects, such transferring control to an unintended location in code or creating an endless loop.</span></span>

## <a name="case-labels"></a><span data-ttu-id="8606c-138">Étiquettes case</span><span class="sxs-lookup"><span data-stu-id="8606c-138">Case labels</span></span>

 <span data-ttu-id="8606c-139">Chaque étiquette case spécifie un modèle à comparer à l’expression de correspondance (la variable `caseSwitch` dans les exemples précédents).</span><span class="sxs-lookup"><span data-stu-id="8606c-139">Each case label specifies a pattern to compare to the match expression (the `caseSwitch` variable in the previous examples).</span></span> <span data-ttu-id="8606c-140">S’ils correspondent, le contrôle est transféré à la section de commutation qui contient la **première** étiquette case correspondante.</span><span class="sxs-lookup"><span data-stu-id="8606c-140">If they match, control is transferred to the switch section that contains the **first** matching case label.</span></span> <span data-ttu-id="8606c-141">Si aucun modèle d’étiquette case ne correspond à l’expression de correspondance, le contrôle est transféré à la section avec l’étiquette case `default`, si une telle section existe.</span><span class="sxs-lookup"><span data-stu-id="8606c-141">If no case label pattern matches the match expression, control is transfered to the section with the `default` case label, if there is one.</span></span> <span data-ttu-id="8606c-142">En l’absence d’étiquette case `default`, aucune instruction d’aucune section de commutation n’est exécutée et le contrôle est transféré hors de l’instruction `switch`.</span><span class="sxs-lookup"><span data-stu-id="8606c-142">If there is no `default` case, no statements in any switch section are executed, and control is transferred outside the `switch` statement.</span></span>

 <span data-ttu-id="8606c-143">Pour plus d’informations sur l’instruction `switch` et les critères spéciaux, consultez la section [Critères spéciaux avec l’instruction `switch`](#pattern).</span><span class="sxs-lookup"><span data-stu-id="8606c-143">For information on the `switch` statement and pattern matching, see the [Pattern matching with the `switch` statement](#pattern) section.</span></span>

 <span data-ttu-id="8606c-144">Étant donné que C# 6 prend en charge uniquement le modèle de constante et n’autorise pas la répétition des valeurs constantes, les étiquettes case définissent des valeurs qui s’excluent mutuellement, et un seul modèle peut correspondre à l’expression de correspondance.</span><span class="sxs-lookup"><span data-stu-id="8606c-144">Because C# 6 supports only the constant pattern and does not allow the repetition of constant values, case labels define mutually exclusive values, and only one pattern can match the match expression.</span></span> <span data-ttu-id="8606c-145">Par conséquent, l’ordre dans lequel les instructions `case` apparaissent n’a pas d’importance.</span><span class="sxs-lookup"><span data-stu-id="8606c-145">As a result, the order in which `case` statements appear is unimportant.</span></span>

 <span data-ttu-id="8606c-146">Dans C# 7, toutefois, comme d’autres modèles sont pris en charge, les étiquettes case ne sont pas tenues de définir des valeurs s’excluant mutuellement et plusieurs modèles peuvent correspondre à l’expression de correspondance.</span><span class="sxs-lookup"><span data-stu-id="8606c-146">In C# 7, however, because other patterns are supported, case labels need not define mutually exclusive values, and multiple patterns can match the match expression.</span></span> <span data-ttu-id="8606c-147">Comme seules les instructions de la section de commutation contenant le premier modèle correspondant sont exécutées, l’ordre dans lequel les instructions `case` apparaissent est désormais important.</span><span class="sxs-lookup"><span data-stu-id="8606c-147">Because only the statements in the switch section that contains the first matching pattern are executed, the order in which `case` statements appear is now important.</span></span> <span data-ttu-id="8606c-148">Si C# détecte une section de commutation dont la ou les instructions case sont équivalentes aux instructions précédentes, ou en sont des sous-ensembles, C# génère une erreur du compilateur, CS8120, « Le switch case a déjà été pris en charge par un case antérieur ».</span><span class="sxs-lookup"><span data-stu-id="8606c-148">If C# detects a switch section whose case statement or statements are equivalent to or are subsets of previous statements, it generates a compiler error, CS8120, "The switch case has already been handled by a previous case."</span></span> 

 <span data-ttu-id="8606c-149">L’exemple suivant illustre une instruction `switch` qui utilise divers modèles ne s’excluant pas mutuellement.</span><span class="sxs-lookup"><span data-stu-id="8606c-149">The following example illustrates a `switch` statement that uses a variety of non-mutually exclusive patterns.</span></span> <span data-ttu-id="8606c-150">Si vous déplacez la section de commutation `case 0:` pour qu’elle ne soit plus la première section dans l’instruction `switch`, C# génère une erreur du compilateur, car un entier dont la valeur est égale à zéro est un sous-ensemble de tous les entiers, ce qui est le modèle défini par l’instruction `case int val`.</span><span class="sxs-lookup"><span data-stu-id="8606c-150">If you move the `case 0:` switch section so that it is no longer the first section in the `switch` statement, C# generates a compiler error because an integer whose value is zero is a subset of all integers, which is the pattern defined by the `case int val` statement.</span></span>

 <span data-ttu-id="8606c-151">[!code-cs[switch#5](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch5.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="8606c-151">[!code-cs[switch#5](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch5.cs#1)]</span></span>    

<span data-ttu-id="8606c-152">Vous pouvez corriger ce problème et éliminer l’avertissement du compilateur de deux façons :</span><span class="sxs-lookup"><span data-stu-id="8606c-152">You can correct this issue and eliminate the compiler warning in one of two ways:</span></span>

- <span data-ttu-id="8606c-153">en modifiant l’ordre des sections de commutation ;</span><span class="sxs-lookup"><span data-stu-id="8606c-153">By changing the order of the switch sections.</span></span> 
 
- <span data-ttu-id="8606c-154">en utilisant une clause </a name="when">when</a> dans l’étiquette `case`.</span><span class="sxs-lookup"><span data-stu-id="8606c-154">By using a </a name="when">when clause</a> in the `case` label.</span></span>
 
## <a name="the-default-case"></a><span data-ttu-id="8606c-155">Étiquette case `default`</span><span class="sxs-lookup"><span data-stu-id="8606c-155">The `default` case</span></span>

<span data-ttu-id="8606c-156">L’étiquette case `default` spécifie la section de commutation à exécuter si l’expression de correspondance ne correspond à aucune autre étiquette `case`.</span><span class="sxs-lookup"><span data-stu-id="8606c-156">The `default` case specifies the switch section to execute if the match expression does not match any other `case` label.</span></span> <span data-ttu-id="8606c-157">En l’absence d’une étiquette case `default`, si l’expression de correspondance ne correspond à aucune autre étiquette `case`, le flux de programme traverse l’instruction `switch`.</span><span class="sxs-lookup"><span data-stu-id="8606c-157">If a `default` case is not present and the match expression does not match any other `case` label, program flow falls through the `switch` statement.</span></span>

<span data-ttu-id="8606c-158">L’étiquette case `default` peut apparaître à n’importe quelle position dans l’instruction `switch`.</span><span class="sxs-lookup"><span data-stu-id="8606c-158">The `default` case can appear in any order in the `switch` statement.</span></span> <span data-ttu-id="8606c-159">Quelle que soit sa position dans le code source, elle est toujours évaluée en dernier, une fois que toutes les étiquettes `case` ont été évaluées.</span><span class="sxs-lookup"><span data-stu-id="8606c-159">Regardless of its order in the source code, it is always evaluated last, after all `case` labels have been evaluated.</span></span>

## <a name="a-namepattern--pattern-matching-with-the-switch-statement"></a><span data-ttu-id="8606c-160"><a name="pattern" /> Critères spéciaux avec l’instruction `switch`</span><span class="sxs-lookup"><span data-stu-id="8606c-160"><a name="pattern" /> Pattern matching with the `switch` statement</span></span>
  
<span data-ttu-id="8606c-161">Chaque instruction `case` définit un modèle qui, s’il correspond à l’expression de correspondance, entraîne l’exécution de la section de commutation qui le contient.</span><span class="sxs-lookup"><span data-stu-id="8606c-161">Each `case` statement defines a pattern that, if it matches the match expression, causes its  containing switch section to be executed.</span></span> <span data-ttu-id="8606c-162">Toutes les versions de C# prennent en charge le modèle de constante.</span><span class="sxs-lookup"><span data-stu-id="8606c-162">All versions of C# support the constant pattern.</span></span> <span data-ttu-id="8606c-163">Les autres modèles sont pris en charge à compter de C# 7.</span><span class="sxs-lookup"><span data-stu-id="8606c-163">The remaining patterns are supported beginning with C# 7.</span></span> 
  
### <a name="constant-pattern"></a><span data-ttu-id="8606c-164">Modèle de constante</span><span class="sxs-lookup"><span data-stu-id="8606c-164">Constant pattern</span></span> 

<span data-ttu-id="8606c-165">Le modèle de constante teste si l’expression de correspondance est égale à une constante spécifiée.</span><span class="sxs-lookup"><span data-stu-id="8606c-165">The constant pattern tests whether the match expression equals a specified constant.</span></span> <span data-ttu-id="8606c-166">Sa syntaxe est la suivante :</span><span class="sxs-lookup"><span data-stu-id="8606c-166">Its syntax is:</span></span>

```csharp
   case constant:
```

<span data-ttu-id="8606c-167">où *constant* est la valeur à tester.</span><span class="sxs-lookup"><span data-stu-id="8606c-167">where *constant* is the value to test for.</span></span> <span data-ttu-id="8606c-168">*constant* peut être l’une quelconque des expressions constantes suivantes :</span><span class="sxs-lookup"><span data-stu-id="8606c-168">*constant* can be any of the following constant expressions:</span></span> 

- <span data-ttu-id="8606c-169">Un littéral de [valeur booléenne](bool.md), `true` ou `false`</span><span class="sxs-lookup"><span data-stu-id="8606c-169">A [bool](bool.md) literal, either `true` or `false`.</span></span>
- <span data-ttu-id="8606c-170">Toute constante intégrale, de type [int](int.md), [long](long.md) ou [byte](byte.md)</span><span class="sxs-lookup"><span data-stu-id="8606c-170">Any integral constant, such as an [int](int.md), a [long](long.md), or a [byte](byte.md).</span></span> 
- <span data-ttu-id="8606c-171">Le nom d’une variable `const` déclarée</span><span class="sxs-lookup"><span data-stu-id="8606c-171">The name of a declared `const` variable.</span></span>
- <span data-ttu-id="8606c-172">Une constante d’énumération</span><span class="sxs-lookup"><span data-stu-id="8606c-172">An enumeration constant.</span></span>
- <span data-ttu-id="8606c-173">Un littéral de type [char](char.md)</span><span class="sxs-lookup"><span data-stu-id="8606c-173">A [char](char.md) literal.</span></span>
- <span data-ttu-id="8606c-174">Un littéral de type [string](string.md)</span><span class="sxs-lookup"><span data-stu-id="8606c-174">A [string](string.md) literal.</span></span>

<span data-ttu-id="8606c-175">L’expression constante est évaluée de la manière suivante :</span><span class="sxs-lookup"><span data-stu-id="8606c-175">The constant expression is evaluated as follows:</span></span>

- <span data-ttu-id="8606c-176">Si *expr* et *constant* sont des types intégraux, l’opérateur d’égalité C# détermine si l’expression retourne `true` (autrement dit, si `expr == constant`).</span><span class="sxs-lookup"><span data-stu-id="8606c-176">If *expr* and *constant* are integral types, the C# equality operator determines whether the expression returns `true` (that is, whether `expr == constant`).</span></span>

- <span data-ttu-id="8606c-177">Sinon, la valeur de l’expression est déterminée par un appel à la méthode statique [Object.Equals(expr, constant)](xref:System.Object.Equals(System.Object,System.Object)).</span><span class="sxs-lookup"><span data-stu-id="8606c-177">Otherwise, the value of the expression is determined by a call to the static [Object.Equals(expr, constant)](xref:System.Object.Equals(System.Object,System.Object)) method.</span></span>  

<span data-ttu-id="8606c-178">L’exemple suivant utilise le modèle de constante pour déterminer si une date particulière correspond à un jour de week-end, au premier jour de la semaine, au dernier jour de la semaine de travail ou au milieu de la semaine de travail.</span><span class="sxs-lookup"><span data-stu-id="8606c-178">The following example uses the constant pattern to determine whether a particular date is a weekend, the first day of the work week, the last day of the work week, or the middle of the work week.</span></span> <span data-ttu-id="8606c-179">Il évalue la propriété [DateTime.DayOfWeek](xref:System.DateTime.DayOfWeek) du jour actuel par rapport aux membres de l’énumération @System.DayOfWeek.</span><span class="sxs-lookup"><span data-stu-id="8606c-179">It evaluates the [DateTime.DayOfWeek](xref:System.DateTime.DayOfWeek) property of the current day against the members of the @System.DayOfWeek enumeration.</span></span> 

<span data-ttu-id="8606c-180">[!code-cs[switch#7](../../../../samples/snippets/csharp/language-reference/keywords/switch/const-pattern.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="8606c-180">[!code-cs[switch#7](../../../../samples/snippets/csharp/language-reference/keywords/switch/const-pattern.cs#1)]</span></span>

<span data-ttu-id="8606c-181">L’exemple suivant utilise le modèle de constante pour gérer l’entrée d’utilisateur dans une application console qui simule une machine à café automatique.</span><span class="sxs-lookup"><span data-stu-id="8606c-181">The following example uses the constant pattern to handle user input in a console application that simulates an automatic coffee machine.</span></span>
  
 <span data-ttu-id="8606c-182">[!code-cs[switch#6](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch6.cs)]</span><span class="sxs-lookup"><span data-stu-id="8606c-182">[!code-cs[switch#6](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch6.cs)]</span></span>  

### <a name="type-pattern"></a><span data-ttu-id="8606c-183">Modèle de type</span><span class="sxs-lookup"><span data-stu-id="8606c-183">Type pattern</span></span>

<span data-ttu-id="8606c-184">Le modèle de type permet une évaluation et une conversion rapides de type.</span><span class="sxs-lookup"><span data-stu-id="8606c-184">The type pattern enables concise type evaluation and conversion.</span></span> <span data-ttu-id="8606c-185">Lorsqu’il est utilisé avec l’instruction `switch` pour effectuer une mise en correspondance de modèle, il permet de tester si une expression peut être convertie en un type spécifié et, si tel est le cas, il effectue un cast de l’expression en une variable de ce type.</span><span class="sxs-lookup"><span data-stu-id="8606c-185">When used with the `switch` statement to perform pattern matching, it tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.</span></span> <span data-ttu-id="8606c-186">Sa syntaxe est la suivante :</span><span class="sxs-lookup"><span data-stu-id="8606c-186">Its syntax is:</span></span>

```csharp
   case type varname 
```
<span data-ttu-id="8606c-187">où *type* est le nom du type vers lequel le résultat de *expr* doit être converti, et *varname* est l’objet vers lequel le résultat de *expr* est converti si la correspondance est établie.</span><span class="sxs-lookup"><span data-stu-id="8606c-187">where *type* is the name of the type to which the result of *expr* is to be converted, and *varname* is the object to which the result of *expr* is converted if the match succeeds.</span></span> 

<span data-ttu-id="8606c-188">L’expression `case` est `true` si l’une quelconque des affirmations suivantes est vraie :</span><span class="sxs-lookup"><span data-stu-id="8606c-188">The `case` expression is `true` if any of the following is true:</span></span>

- <span data-ttu-id="8606c-189">*expr* est une instance du même type que *type*.</span><span class="sxs-lookup"><span data-stu-id="8606c-189">*expr* is an instance of the same type as *type*.</span></span>

- <span data-ttu-id="8606c-190">*expr* est une instance d’un type qui dérive de *type*.</span><span class="sxs-lookup"><span data-stu-id="8606c-190">*expr* is an instance of a type that derives from *type*.</span></span> <span data-ttu-id="8606c-191">En d’autres termes, le résultat de *expr* peut être upcasté en une instance de *type*.</span><span class="sxs-lookup"><span data-stu-id="8606c-191">In other words, the result of *expr* can be upcast to an instance of *type*.</span></span>

- <span data-ttu-id="8606c-192">*expr* a un type au moment de la compilation qui est une classe de base de *type* et *expr* a un type au moment de l’exécution égal à *type* ou dérivé de *type*.</span><span class="sxs-lookup"><span data-stu-id="8606c-192">*expr* has a compile-time type that is a base class of *type*, and *expr* has a runtime type that is *type* or is derived from *type*.</span></span> <span data-ttu-id="8606c-193">Le *type au moment de la compilation* d’une variable est le type de la variable, tel qu’il est défini dans sa déclaration de type.</span><span class="sxs-lookup"><span data-stu-id="8606c-193">The *compile-time type* of a variable is the variable's type as defined in its type declaration.</span></span> <span data-ttu-id="8606c-194">Le *type au moment de l’exécution* d’une variable est le type de l’instance qui est assignée à cette variable.</span><span class="sxs-lookup"><span data-stu-id="8606c-194">The *runtime type* of a variable is the type of the instance that is assigned to that variable.</span></span>

- <span data-ttu-id="8606c-195">*expr* est une instance d’un type qui implémente l’interface *type*.</span><span class="sxs-lookup"><span data-stu-id="8606c-195">*expr* is an instance of a type that implements the *type* interface.</span></span>

<span data-ttu-id="8606c-196">Si l’expression case est true, *varname* est définitivement assigné et a une portée locale au sein de la section de commutation uniquement.</span><span class="sxs-lookup"><span data-stu-id="8606c-196">If the case expression is true, *varname* is definitely assigned and has local scope within the switch section only.</span></span>

<span data-ttu-id="8606c-197">Notez que `null` ne correspond pas à un type.</span><span class="sxs-lookup"><span data-stu-id="8606c-197">Note that `null` does not match a type.</span></span> <span data-ttu-id="8606c-198">Pour mettre en correspondance `null`, vous utilisez l’étiquette `case` suivante :</span><span class="sxs-lookup"><span data-stu-id="8606c-198">To match a `null`, you use the following `case` label:</span></span>

```csharp
case null:
```
 
<span data-ttu-id="8606c-199">L’exemple suivant utilise le modèle de type pour fournir des informations sur différentes sortes de types de collection.</span><span class="sxs-lookup"><span data-stu-id="8606c-199">The following example uses the type pattern to provide information about various kinds of collection types.</span></span>

<span data-ttu-id="8606c-200">[!code-cs[switch#5](../../../../samples/snippets/csharp/language-reference/keywords/switch/type-pattern.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="8606c-200">[!code-cs[switch#5](../../../../samples/snippets/csharp/language-reference/keywords/switch/type-pattern.cs#1)]</span></span>

<span data-ttu-id="8606c-201">Sans critères spéciaux, ce code peut être écrit comme suit.</span><span class="sxs-lookup"><span data-stu-id="8606c-201">Without pattern matching, this code might be written as follows.</span></span> <span data-ttu-id="8606c-202">L’utilisation de critères spéciaux de type génère un code plus compact et lisible en éliminant la nécessité de tester si le résultat d’une conversion est un `null` et d’effectuer des casts répétés.</span><span class="sxs-lookup"><span data-stu-id="8606c-202">The use of type pattern matching produces more compact, readable code by eliminating the need to test whether the result of a conversion is a `null` or to perform repeated casts.</span></span>  

<span data-ttu-id="8606c-203">[!code-cs[switch#6](../../../../samples/snippets/csharp/language-reference/keywords/switch/type-pattern2.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="8606c-203">[!code-cs[switch#6](../../../../samples/snippets/csharp/language-reference/keywords/switch/type-pattern2.cs#1)]</span></span>

## <a name="the-case-statement-and-the-when-clause"></a><span data-ttu-id="8606c-204">Instruction `case` et clause `when`</span><span class="sxs-lookup"><span data-stu-id="8606c-204">The `case` statement and the `when` clause</span></span>

<span data-ttu-id="8606c-205">À compter de C# 7, comme les instructions case ne s’excluent pas nécessairement mutuellement, vous pouvez ajouter une clause `when` pour spécifier une condition supplémentaire qui doit être satisfaite pour que l’instruction case soit évaluée à true.</span><span class="sxs-lookup"><span data-stu-id="8606c-205">Starting with C# 7, because case statements need not be mutually exclusive, you can use add a `when` clause to specify an additional condition that must be satisfied for the case statement to evaluate to true.</span></span> <span data-ttu-id="8606c-206">La clause `when` peut être toute expression qui retourne une valeur booléenne.</span><span class="sxs-lookup"><span data-stu-id="8606c-206">The `when` clause can be any expression that returns a Boolean value.</span></span> <span data-ttu-id="8606c-207">Le plus souvent, la clause `when` est utilisée pour empêcher l’exécution d’une section de commutation quand la valeur d’une expression de correspondance est `null`.</span><span class="sxs-lookup"><span data-stu-id="8606c-207">One of the more common uses for the `when` clause is used to prevent a switch section from executing when the value of a match expression is `null`.</span></span> 

 <span data-ttu-id="8606c-208">L’exemple suivant définit une classe `Shape` de base, une classe `Rectangle` qui dérive de `Shape` et une classe `Square` qui dérive de `Rectangle`.</span><span class="sxs-lookup"><span data-stu-id="8606c-208">The following example defines a base `Shape` class, a `Rectangle` class that derives from `Shape`, and a `Square` class that derives from `Rectangle`.</span></span> <span data-ttu-id="8606c-209">Il utilise la clause `when` pour garantir que le `ShowShapeInfo` traite un objet `Rectangle` qui s’est vu assigner des longueurs et des largeurs égales comme celles d’un objet `Square` même s’il n’a pas été instancié comme objet `Square`.</span><span class="sxs-lookup"><span data-stu-id="8606c-209">It uses the `when` clause to ensure that the `ShowShapeInfo` treats a `Rectangle` object that has been assigned equal lengths and widths as a `Square` even if is has not been instantiated as a `Square` object.</span></span> <span data-ttu-id="8606c-210">La méthode ne tente pas d’afficher des informations sur un objet `null` ou sur une forme dont l’aire est nulle.</span><span class="sxs-lookup"><span data-stu-id="8606c-210">The method does not attempt to display information either about an object that is `null` or a shape whose area is zero.</span></span> 

<span data-ttu-id="8606c-211">[!code-cs[switch#8](../../../../samples/snippets/csharp/language-reference/keywords/switch/when-clause.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="8606c-211">[!code-cs[switch#8](../../../../samples/snippets/csharp/language-reference/keywords/switch/when-clause.cs#1)]</span></span>
  
<span data-ttu-id="8606c-212">Notez que la clause `when` dans l’exemple qui tente de tester si un objet `Shape` est `null` ne s’exécute pas.</span><span class="sxs-lookup"><span data-stu-id="8606c-212">Note that the `when` clause in the example that attempts to test whether a `Shape` object is `null` does not execute.</span></span> <span data-ttu-id="8606c-213">Le modèle de type correct à utiliser pour tester un `null` est `case null:`.</span><span class="sxs-lookup"><span data-stu-id="8606c-213">The correct type pattern to test for a `null` is `case null:`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="8606c-214">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="8606c-214">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8606c-215">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8606c-215">See Also</span></span>  

 <span data-ttu-id="8606c-216">[Informations de référence sur C#](../index.md) </span><span class="sxs-lookup"><span data-stu-id="8606c-216">[C# Reference](../index.md) </span></span>  
 <span data-ttu-id="8606c-217">[Guide de programmation C#](../../programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="8606c-217">[C# Programming Guide](../../programming-guide/index.md) </span></span>  
 <span data-ttu-id="8606c-218">[Mots clés C#](index.md) </span><span class="sxs-lookup"><span data-stu-id="8606c-218">[C# Keywords](index.md) </span></span>  
 <span data-ttu-id="8606c-219">[if-else](if-else.md) </span><span class="sxs-lookup"><span data-stu-id="8606c-219">[if-else](if-else.md) </span></span>  
 [<span data-ttu-id="8606c-220">Critères spéciaux</span><span class="sxs-lookup"><span data-stu-id="8606c-220">Pattern Matching</span></span>](../../pattern-matching.md)   
 

 

