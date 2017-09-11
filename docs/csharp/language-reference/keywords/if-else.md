---
title: "if-else (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- if_CSharpKeyword
- else
- else_CSharpKeyword
- if
dev_langs:
- CSharp
helpviewer_keywords:
- else keyword [C#]
- if keyword [C#]
ms.assetid: d9a1d562-8cf5-4bd4-9ba7-8ad970cd25b2
caps.latest.revision: 32
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
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 694761a9b03fadf2dff97e61e37c0af52658f9e4
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="if-else-c-reference"></a><span data-ttu-id="f5c00-102">if-else (référence C#)</span><span class="sxs-lookup"><span data-stu-id="f5c00-102">if-else (C# Reference)</span></span>
<span data-ttu-id="f5c00-103">Une instruction `if` identifie l’instruction à exécuter en fonction de la valeur d’une expression `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="f5c00-103">An `if` statement identifies which statement to run based on the value of a `Boolean` expression.</span></span> <span data-ttu-id="f5c00-104">Dans l’exemple suivant, la variable `Boolean` `result` est définie sur `true` puis archivé dans l’instruction `if` .</span><span class="sxs-lookup"><span data-stu-id="f5c00-104">In the following example, the `Boolean` variable `result` is set to `true` and then checked in the `if` statement.</span></span> <span data-ttu-id="f5c00-105">Le résultat est `The condition is true`.</span><span class="sxs-lookup"><span data-stu-id="f5c00-105">The output is `The condition is true`.</span></span>  
  
 <span data-ttu-id="f5c00-106">[!code-cs[csrefKeywordsSelection#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/if-else_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="f5c00-106">[!code-cs[csrefKeywordsSelection#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/if-else_1.cs)]</span></span>  
  
 <span data-ttu-id="f5c00-107">Vous pouvez exécuter les exemples de cette rubrique en les plaçant dans la méthode `Main` d’une application console.</span><span class="sxs-lookup"><span data-stu-id="f5c00-107">You can run the examples in this topic by placing them in the `Main` method of a console app.</span></span>  
  
 <span data-ttu-id="f5c00-108">En C#, une instruction `if` peut prendre deux formes, comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="f5c00-108">An `if` statement in C# can take two forms, as the following example shows.</span></span>  
  
```csharp  
// if-else statement  
if (condition)  
{  
    then-statement;  
}  
else  
{  
    else-statement;  
}  
// Next statement in the program.  
  
// if statement without an else  
if (condition)  
{  
    then-statement;  
}  
// Next statement in the program.  
```  
  
 <span data-ttu-id="f5c00-109">Dans une instruction `if-else` , si `condition` a la valeur true, `then-statement` s’exécute.</span><span class="sxs-lookup"><span data-stu-id="f5c00-109">In an `if-else` statement, if `condition` evaluates to true, the `then-statement` runs.</span></span> <span data-ttu-id="f5c00-110">Si `condition` a la valeur false, `else-statement` s’exécute.</span><span class="sxs-lookup"><span data-stu-id="f5c00-110">If `condition` is false, the `else-statement` runs.</span></span> <span data-ttu-id="f5c00-111">Sachant que `condition` ne peut pas avoir simultanément les valeurs true et false, `then-statement` et `else-statement` d’une instruction `if-else` ne peuvent jamais s’exécuter.</span><span class="sxs-lookup"><span data-stu-id="f5c00-111">Because `condition` can’t be simultaneously true and false, the `then-statement` and the `else-statement` of an `if-else` statement can never both run.</span></span> <span data-ttu-id="f5c00-112">Une fois que `then-statement` ou `else-statement` s’est exécuté, le contrôle est transféré à l’instruction suivante après l’instruction `if` .</span><span class="sxs-lookup"><span data-stu-id="f5c00-112">After the `then-statement` or the `else-statement` runs, control is transferred to the next statement after the `if` statement.</span></span>  
  
 <span data-ttu-id="f5c00-113">Dans une instruction `if` qui n’inclut pas d’instruction `else` , si `condition` a la valeur true, `then-statement` s’exécute.</span><span class="sxs-lookup"><span data-stu-id="f5c00-113">In an `if` statement that doesn’t include an `else` statement, if `condition` is true, the `then-statement` runs.</span></span> <span data-ttu-id="f5c00-114">Si `condition` a la valeur false, le contrôle est transféré à l’instruction suivante après l’instruction `if` .</span><span class="sxs-lookup"><span data-stu-id="f5c00-114">If `condition` is false, control is transferred to the next statement after the `if` statement.</span></span>  
  
 <span data-ttu-id="f5c00-115">`then-statement` et `else-statement` peuvent tous deux être constitués d’une ou plusieurs instructions placées entre accolades (`{}`).</span><span class="sxs-lookup"><span data-stu-id="f5c00-115">Both the `then-statement` and the `else-statement` can consist of a single statement or multiple statements that are enclosed in braces (`{}`).</span></span> <span data-ttu-id="f5c00-116">Pour une seule instruction, les accolades sont facultatives, mais recommandées.</span><span class="sxs-lookup"><span data-stu-id="f5c00-116">For a single statement, the braces are optional but recommended.</span></span>  
  
 <span data-ttu-id="f5c00-117">La ou les instructions contenues dans `then-statement` et `else-statement` peuvent être de n’importe quel type, y compris une autre instruction `if` imbriquée à l’intérieur de l’instruction `if` d’origine.</span><span class="sxs-lookup"><span data-stu-id="f5c00-117">The statement or statements in the `then-statement` and the `else-statement` can be of any kind, including another `if` statement nested inside the original `if` statement.</span></span> <span data-ttu-id="f5c00-118">Dans les instructions `if` imbriquées, chaque clause `else` appartient à la dernière instruction `if` qui n’a pas d’instruction `else`correspondante.</span><span class="sxs-lookup"><span data-stu-id="f5c00-118">In nested `if` statements, each `else` clause belongs to the last `if` that doesn’t have a corresponding `else`.</span></span> <span data-ttu-id="f5c00-119">Dans l’exemple suivant, `Result1` s’affiche si `m > 10` et `n > 20` ont tous deux la valeur true.</span><span class="sxs-lookup"><span data-stu-id="f5c00-119">In the following example, `Result1` appears if both `m > 10` and `n > 20` evaluate to true.</span></span> <span data-ttu-id="f5c00-120">Si `m > 10` a la valeur true, mais que `n > 20` a la valeur false, `Result2` s’affiche.</span><span class="sxs-lookup"><span data-stu-id="f5c00-120">If `m > 10` is true but `n > 20` is false, `Result2` appears.</span></span>  
  
 <span data-ttu-id="f5c00-121">[!code-cs[csrefKeywordsSelection#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/if-else_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="f5c00-121">[!code-cs[csrefKeywordsSelection#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/if-else_2.cs)]</span></span>  
  
 <span data-ttu-id="f5c00-122">Si vous préférez que `Result2` s’affiche quand `(m > 10)` a la valeur false, vous pouvez spécifier cette association au moyen d’accolades pour établir le début et la fin de l’instruction `if` imbriquée, comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="f5c00-122">If, instead, you want `Result2` to appear when `(m > 10)` is false, you can specify that association by using braces to establish the start and end of the nested `if` statement, as the following example shows.</span></span>  
  
 <span data-ttu-id="f5c00-123">[!code-cs[csrefKeywordsSelection#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/if-else_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="f5c00-123">[!code-cs[csrefKeywordsSelection#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/if-else_3.cs)]</span></span>  
  
 <span data-ttu-id="f5c00-124">`Result2` s’affiche si la condition `(m > 10)` a la valeur false.</span><span class="sxs-lookup"><span data-stu-id="f5c00-124">`Result2` appears if the condition `(m > 10)` evaluates to false.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f5c00-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="f5c00-125">Example</span></span>  
 <span data-ttu-id="f5c00-126">Dans l’exemple suivant, vous entrez un caractère au clavier et le programme utilise une instruction `if` imbriquée pour déterminer si le caractère d’entrée est un caractère alphabétique.</span><span class="sxs-lookup"><span data-stu-id="f5c00-126">In the following example, you enter a character from the keyboard, and the program uses a nested `if` statement to determine whether the input character is an alphabetic character.</span></span> <span data-ttu-id="f5c00-127">Si le caractère d’entrée est un caractère alphabétique, le programme vérifie si c’est une minuscule ou une majuscule.</span><span class="sxs-lookup"><span data-stu-id="f5c00-127">If the input character is an alphabetic character, the program checks whether the input character is lowercase or uppercase.</span></span> <span data-ttu-id="f5c00-128">Un message s’affiche dans chaque cas.</span><span class="sxs-lookup"><span data-stu-id="f5c00-128">A message appears for each case.</span></span>  
  
 <span data-ttu-id="f5c00-129">[!code-cs[csrefKeywordsSelection#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/if-else_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="f5c00-129">[!code-cs[csrefKeywordsSelection#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/if-else_4.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="f5c00-130">Exemple</span><span class="sxs-lookup"><span data-stu-id="f5c00-130">Example</span></span>  
 <span data-ttu-id="f5c00-131">Vous pouvez aussi imbriquer une instruction `if` à l’intérieur d’un bloc « else », comme le montre l’extrait de code suivant.</span><span class="sxs-lookup"><span data-stu-id="f5c00-131">You also can nest an `if` statement inside an else block, as the following partial code shows.</span></span> <span data-ttu-id="f5c00-132">L’exemple imbrique des instructions `if` à l’intérieur de deux blocs « else » et d’un bloc « then ».</span><span class="sxs-lookup"><span data-stu-id="f5c00-132">The example nests `if` statements inside two else blocks and one then block.</span></span> <span data-ttu-id="f5c00-133">Les commentaires précisent les conditions qui sont vraies (true) et celles qui sont fausses (false) dans chaque bloc.</span><span class="sxs-lookup"><span data-stu-id="f5c00-133">The comments specify which conditions are true or false in each block.</span></span>  
  
 <span data-ttu-id="f5c00-134">[!code-cs[csrefKeywordsSelection#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/if-else_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="f5c00-134">[!code-cs[csrefKeywordsSelection#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/if-else_5.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="f5c00-135">Exemple</span><span class="sxs-lookup"><span data-stu-id="f5c00-135">Example</span></span>  
 <span data-ttu-id="f5c00-136">L’exemple suivant détermine si un caractère d’entrée est une lettre minuscule, une lettre majuscule ou un nombre.</span><span class="sxs-lookup"><span data-stu-id="f5c00-136">The following example determines whether an input character is a lowercase letter, an uppercase letter, or a number.</span></span> <span data-ttu-id="f5c00-137">Si ces trois conditions ont la valeur false, le caractère n’est pas un caractère alphanumérique.</span><span class="sxs-lookup"><span data-stu-id="f5c00-137">If all three conditions are false, the character isn’t an alphanumeric character.</span></span> <span data-ttu-id="f5c00-138">L’exemple affiche un message dans chaque cas.</span><span class="sxs-lookup"><span data-stu-id="f5c00-138">The example displays a message for each case.</span></span>  
  
 <span data-ttu-id="f5c00-139">[!code-cs[csrefKeywordsSelection#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/if-else_6.cs)]</span><span class="sxs-lookup"><span data-stu-id="f5c00-139">[!code-cs[csrefKeywordsSelection#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/if-else_6.cs)]</span></span>  
  
 <span data-ttu-id="f5c00-140">De la même manière que le bloc « else » ou le bloc « then » peuvent contenir n’importe quelle instruction valide, vous pouvez utiliser n’importe quelle expression booléenne valide pour la condition.</span><span class="sxs-lookup"><span data-stu-id="f5c00-140">Just as a statement in the else block or the then block can be any valid statement, you can use any valid Boolean expression for the condition.</span></span> <span data-ttu-id="f5c00-141">Vous pouvez utiliser des opérateurs logiques tels que [&&](../../../csharp/language-reference/operators/conditional-and-operator.md), [&](../../../csharp/language-reference/operators/and-operator.md), [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md), [&#124;](../../../csharp/language-reference/operators/or-operator.md) et [!](../../../csharp/language-reference/operators/logical-negation-operator.md)</span><span class="sxs-lookup"><span data-stu-id="f5c00-141">You can use logical operators such as [&&](../../../csharp/language-reference/operators/conditional-and-operator.md), [&](../../../csharp/language-reference/operators/and-operator.md), [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md), [&#124;](../../../csharp/language-reference/operators/or-operator.md) and [!](../../../csharp/language-reference/operators/logical-negation-operator.md)</span></span> <span data-ttu-id="f5c00-142">pour former des conditions composées.</span><span class="sxs-lookup"><span data-stu-id="f5c00-142">to make compound conditions.</span></span> <span data-ttu-id="f5c00-143">Le code suivant présente des exemples.</span><span class="sxs-lookup"><span data-stu-id="f5c00-143">The following code shows examples.</span></span>  
  
```csharp  
// NOT  
bool result = true;  
if (!result)  
{  
    Console.WriteLine("The condition is true (result is false).");  
}  
else  
{  
    Console.WriteLine("The condition is false (result is true).");  
}  
  
// Short-circuit AND  
int m = 9;  
int n = 7;  
int p = 5;  
if (m >= n && m >= p)  
{  
    Console.WriteLine("Nothing is larger than m.");  
}  
  
// AND and NOT  
if (m >= n && !(p > m))  
{  
    Console.WriteLine("Nothing is larger than m.");  
}  
  
// Short-circuit OR  
if (m > n || m > p)  
{  
    Console.WriteLine("m isn't the smallest.");  
}  
  
// NOT and OR  
m = 4;  
if (!(m >= n || m >= p))  
{  
    Console.WriteLine("Now m is the smallest.");  
}  
// Output:  
// The condition is false (result is true).  
// Nothing is larger than m.  
// Nothing is larger than m.  
// m isn't the smallest.  
// Now m is the smallest.  
```  
  
## <a name="c-language-specification"></a><span data-ttu-id="f5c00-144">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="f5c00-144">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f5c00-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f5c00-145">See Also</span></span>  
 <span data-ttu-id="f5c00-146">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="f5c00-146">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="f5c00-147">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="f5c00-147">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="f5c00-148">[Mots clés C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="f5c00-148">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="f5c00-149">[?, opérateur](../../../csharp/language-reference/operators/conditional-operator.md) </span><span class="sxs-lookup"><span data-stu-id="f5c00-149">[?: Operator](../../../csharp/language-reference/operators/conditional-operator.md) </span></span>  
 <span data-ttu-id="f5c00-150">[if-else, instruction (C++)](/cpp/cpp/if-else-statement-cpp) </span><span class="sxs-lookup"><span data-stu-id="f5c00-150">[if-else Statement (C++)](/cpp/cpp/if-else-statement-cpp) </span></span>  
 [<span data-ttu-id="f5c00-151">switch</span><span class="sxs-lookup"><span data-stu-id="f5c00-151">switch</span></span>](../../../csharp/language-reference/keywords/switch.md)

