---
title: "for (référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- for
- for_CSharpKeyword
helpviewer_keywords: for keyword [C#]
ms.assetid: 34041a40-2c87-467a-9ffb-a0417d8f67a8
caps.latest.revision: "39"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: cb7e83733fe026658f502b430975a0f8a27e9df3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="for-c-reference"></a><span data-ttu-id="78883-102">for (référence C#)</span><span class="sxs-lookup"><span data-stu-id="78883-102">for (C# Reference)</span></span>
<span data-ttu-id="78883-103">En utilisant une boucle `for`, vous pouvez exécuter une instruction ou un bloc d’instructions de manière répétée jusqu'à ce qu’une expression spécifiée corresponde à `false`.</span><span class="sxs-lookup"><span data-stu-id="78883-103">By using a `for` loop, you can run a statement or a block of statements repeatedly until a specified expression evaluates to `false`.</span></span> <span data-ttu-id="78883-104">Ce type de boucle est utile pour itérer des tableaux et d’autres applications pour lesquelles vous savez à l’avance combien de fois vous souhaitez effectuer une itération.</span><span class="sxs-lookup"><span data-stu-id="78883-104">This kind of loop is useful for iterating over arrays and for other applications in which you know in advance how many times you want the loop to iterate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="78883-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="78883-105">Example</span></span>  
 <span data-ttu-id="78883-106">Dans l’exemple suivant, la valeur de `i` est écrite dans la console et incrémentée de 1 à chaque itération de la boucle.</span><span class="sxs-lookup"><span data-stu-id="78883-106">In the following example, the value of `i` is written to the console and incremented by 1 during each iteration of the loop.</span></span>  
  
 [!code-csharp[csrefKeywordsIteration#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/for_1.cs)]  
  
 <span data-ttu-id="78883-107">L’instruction `for` de l’exemple précédent effectue les actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="78883-107">The `for` statement in the previous example performs the following actions.</span></span>  
  
1.  <span data-ttu-id="78883-108">Tout d’abord, la valeur initiale de la variable `i` est établie.</span><span class="sxs-lookup"><span data-stu-id="78883-108">First, the initial value of variable `i` is established.</span></span> <span data-ttu-id="78883-109">Cette étape se produit une seule fois, quel que soit le nombre d’itérations de la boucle.</span><span class="sxs-lookup"><span data-stu-id="78883-109">This step happens only once, regardless of how many times the loop repeats.</span></span> <span data-ttu-id="78883-110">Vous pouvez considérer cette initialisation comme survenant en dehors du processus de boucle.</span><span class="sxs-lookup"><span data-stu-id="78883-110">You can think of this initialization as happening outside the looping process.</span></span>  
  
2.  <span data-ttu-id="78883-111">Pour évaluer la condition (`i <= 5`), la valeur de `i` est comparée à 5.</span><span class="sxs-lookup"><span data-stu-id="78883-111">To evaluate the condition (`i <= 5`), the value of `i` is compared to 5.</span></span>  
  
    -   <span data-ttu-id="78883-112">Si `i` est inférieur ou égal à 5, la condition prend la valeur `true`, et les actions suivantes se produisent.</span><span class="sxs-lookup"><span data-stu-id="78883-112">If `i` is less than or equal to 5, the condition evaluates to `true`, and the following actions occur.</span></span>  
  
        1.  <span data-ttu-id="78883-113">L’instruction `Console.WriteLine` dans le corps de la boucle affiche la valeur de `i`.</span><span class="sxs-lookup"><span data-stu-id="78883-113">The `Console.WriteLine` statement in the body of the loop displays the value of `i`.</span></span>  
  
        2.  <span data-ttu-id="78883-114">La valeur de `i` incrémentée de 1.</span><span class="sxs-lookup"><span data-stu-id="78883-114">The value of `i` is incremented by 1.</span></span>  
  
        3.  <span data-ttu-id="78883-115">La boucle retourne au début de l’étape 2 pour évaluer de nouveau la condition.</span><span class="sxs-lookup"><span data-stu-id="78883-115">The loop returns to the start of step 2 to evaluate the condition again.</span></span>  
  
    -   <span data-ttu-id="78883-116">Si `i` est supérieur à 5, la condition prend la valeur `false`, et vous quittez la boucle.</span><span class="sxs-lookup"><span data-stu-id="78883-116">If `i` is greater than 5, the condition evaluates to `false`, and you exit the loop.</span></span>  
  
 <span data-ttu-id="78883-117">Notez que, si la valeur initiale de `i` est supérieure à 5, le corps de la boucle n’est jamais exécuté.</span><span class="sxs-lookup"><span data-stu-id="78883-117">Note that, if the initial value of `i` is greater than 5, the body of the loop doesn't run even once.</span></span>  
  
 <span data-ttu-id="78883-118">Chaque instruction `for` définit les sections Initialiseur, Condition et Itérateur.</span><span class="sxs-lookup"><span data-stu-id="78883-118">Every `for` statement defines initializer, condition, and iterator sections.</span></span> <span data-ttu-id="78883-119">Ces sections déterminent généralement le nombre d’itérations de la boucle.</span><span class="sxs-lookup"><span data-stu-id="78883-119">These sections usually determine how many times the loop iterates.</span></span>  
  
```csharp  
for (initializer; condition; iterator)  
    body  
```  
  
 <span data-ttu-id="78883-120">Ces sections répondent aux objectifs suivants :</span><span class="sxs-lookup"><span data-stu-id="78883-120">The sections serve the following purposes.</span></span>  
  
-   <span data-ttu-id="78883-121">La section Initialiseur définit les conditions initiales.</span><span class="sxs-lookup"><span data-stu-id="78883-121">The initializer section sets the initial conditions.</span></span> <span data-ttu-id="78883-122">Les instructions de cette section ne sont exécutées qu’une seule fois, avant l’entrée dans la boucle.</span><span class="sxs-lookup"><span data-stu-id="78883-122">The statements in this section run only once, before you enter the loop.</span></span> <span data-ttu-id="78883-123">La section peut contenir uniquement l’une des deux options suivantes.</span><span class="sxs-lookup"><span data-stu-id="78883-123">The section can contain only one of the following two options.</span></span>  
  
    -   <span data-ttu-id="78883-124">La déclaration et l’initialisation d’une variable de boucle locale, comme le montre le premier exemple (`int i = 1`).</span><span class="sxs-lookup"><span data-stu-id="78883-124">The declaration and initialization of a local loop variable, as the first example shows (`int i = 1`).</span></span> <span data-ttu-id="78883-125">La variable se trouve dans la boucle et n’est pas accessible en dehors de celle-ci.</span><span class="sxs-lookup"><span data-stu-id="78883-125">The variable is local to the loop and can't be accessed from outside the loop.</span></span>  
  
    -   <span data-ttu-id="78883-126">Zéro ou plusieurs expressions d’instruction de la liste suivante, séparées par des virgules.</span><span class="sxs-lookup"><span data-stu-id="78883-126">Zero or more statement expressons from the following list, separated by commas.</span></span>  
  
        -   <span data-ttu-id="78883-127">Instruction d’[assignation](../../../csharp/language-reference/operators/assignment-operator.md)</span><span class="sxs-lookup"><span data-stu-id="78883-127">[assignment](../../../csharp/language-reference/operators/assignment-operator.md) statement</span></span>  
  
        -   <span data-ttu-id="78883-128">Appel d’une méthode</span><span class="sxs-lookup"><span data-stu-id="78883-128">invocation of a method</span></span>  
  
        -   <span data-ttu-id="78883-129">Expression d’[incrémentation](../../../csharp/language-reference/operators/increment-operator.md) préfixée ou suffixée, telle que `++i` ou `i++`</span><span class="sxs-lookup"><span data-stu-id="78883-129">prefix or postfix [increment](../../../csharp/language-reference/operators/increment-operator.md) expression, such as `++i` or `i++`</span></span>  
  
        -   <span data-ttu-id="78883-130">Expression de [décrémentation](../../../csharp/language-reference/operators/decrement-operator.md) préfixée ou suffixée, telle que `--i` ou `i--`</span><span class="sxs-lookup"><span data-stu-id="78883-130">prefix or postfix [decrement](../../../csharp/language-reference/operators/decrement-operator.md) expression, such as `--i` or `i--`</span></span>  
  
        -   <span data-ttu-id="78883-131">Création d’un objet à l’aide de [new](../../../csharp/language-reference/keywords/new-operator.md)</span><span class="sxs-lookup"><span data-stu-id="78883-131">creation of an object by using [new](../../../csharp/language-reference/keywords/new-operator.md)</span></span>  
  
        -   <span data-ttu-id="78883-132">Expression [await](../../../csharp/language-reference/keywords/await.md)</span><span class="sxs-lookup"><span data-stu-id="78883-132">[await](../../../csharp/language-reference/keywords/await.md) expression</span></span>  
  
-   <span data-ttu-id="78883-133">La section Condition contient une expression booléenne qui est évaluée pour déterminer si la boucle doit s’arrêter ou s’exécuter de nouveau.</span><span class="sxs-lookup"><span data-stu-id="78883-133">The condition section contains a boolean expression that’s evaluated to determine whether the loop should exit or should run again.</span></span>  
  
-   <span data-ttu-id="78883-134">La section Itérateur définit ce qui se produit après chaque itération du corps de la boucle.</span><span class="sxs-lookup"><span data-stu-id="78883-134">The iterator section defines what happens after each iteration of the body of the loop.</span></span> <span data-ttu-id="78883-135">La section Itérateur contient zéro ou plusieurs des expressions d’instruction suivantes, séparées par des virgules :</span><span class="sxs-lookup"><span data-stu-id="78883-135">The iterator section contains zero or more of the following statement expressions, separated by commas:</span></span>  
  
    -   <span data-ttu-id="78883-136">Instruction d’[assignation](../../../csharp/language-reference/operators/assignment-operator.md)</span><span class="sxs-lookup"><span data-stu-id="78883-136">[assignment](../../../csharp/language-reference/operators/assignment-operator.md) statement</span></span>  
  
    -   <span data-ttu-id="78883-137">Appel d’une méthode</span><span class="sxs-lookup"><span data-stu-id="78883-137">invocation of a method</span></span>  
  
    -   <span data-ttu-id="78883-138">Expression d’[incrémentation](../../../csharp/language-reference/operators/increment-operator.md) préfixée ou suffixée, telle que `++i` ou `i++`</span><span class="sxs-lookup"><span data-stu-id="78883-138">prefix or postfix [increment](../../../csharp/language-reference/operators/increment-operator.md) expression, such as `++i` or `i++`</span></span>  
  
    -   <span data-ttu-id="78883-139">Expression de [décrémentation](../../../csharp/language-reference/operators/decrement-operator.md) préfixée ou suffixée, telle que `--i` ou `i--`</span><span class="sxs-lookup"><span data-stu-id="78883-139">prefix or postfix [decrement](../../../csharp/language-reference/operators/decrement-operator.md) expression, such as `--i` or `i--`</span></span>  
  
    -   <span data-ttu-id="78883-140">Création d’un objet à l’aide de [new](../../../csharp/language-reference/keywords/new-operator.md)</span><span class="sxs-lookup"><span data-stu-id="78883-140">creation of an object by using [new](../../../csharp/language-reference/keywords/new-operator.md)</span></span>  
  
    -   <span data-ttu-id="78883-141">Expression [await](../../../csharp/language-reference/keywords/await.md)</span><span class="sxs-lookup"><span data-stu-id="78883-141">[await](../../../csharp/language-reference/keywords/await.md) expression</span></span>  
  
-   <span data-ttu-id="78883-142">Le corps de la boucle se compose d’une instruction, d’une instruction vide ou d’un bloc d’instructions que vous créez en plaçant zéro ou plusieurs instructions entre accolades.</span><span class="sxs-lookup"><span data-stu-id="78883-142">The body of the loop consists of a statement, an empty statement, or a block of statements, which you create by enclosing zero or more statements in braces.</span></span>  
  
     <span data-ttu-id="78883-143">Vous pouvez quitter une boucle `for` à l’aide du mot clé [break](../../../csharp/language-reference/keywords/break.md), ou passer à l’itération suivante de la boucle à l’aide du mot clé [continue](../../../csharp/language-reference/keywords/continue.md).</span><span class="sxs-lookup"><span data-stu-id="78883-143">You can break out of a `for` loop by using the [break](../../../csharp/language-reference/keywords/break.md) keyword, or you can step to the next iteration by using the [continue](../../../csharp/language-reference/keywords/continue.md) keyword.</span></span> <span data-ttu-id="78883-144">Vous pouvez quitter une boucle en utilisant une instruction [goto](../../../csharp/language-reference/keywords/goto.md), [return](../../../csharp/language-reference/keywords/return.md) ou [throw](../../../csharp/language-reference/keywords/throw.md).</span><span class="sxs-lookup"><span data-stu-id="78883-144">You also can exit any loop by using a [goto](../../../csharp/language-reference/keywords/goto.md), [return](../../../csharp/language-reference/keywords/return.md), or [throw](../../../csharp/language-reference/keywords/throw.md) statement.</span></span>  
  
 <span data-ttu-id="78883-145">Le premier exemple de cette rubrique montre le type de boucle `for` le plus courant, qui fait les choix suivants au niveau des sections :</span><span class="sxs-lookup"><span data-stu-id="78883-145">The first example in this topic shows the most typical kind of `for` loop, which makes the following choices for the sections.</span></span>  
  
-   <span data-ttu-id="78883-146">L’initialiseur déclare et initialise une variable de boucle locale, `i`, qui compte le nombre d’itérations de la boucle.</span><span class="sxs-lookup"><span data-stu-id="78883-146">The initializer declares and initializes a local loop variable, `i`, that maintains a count of the iterations of the loop.</span></span>  
  
-   <span data-ttu-id="78883-147">La condition compare la valeur de la variable de boucle par rapport à la valeur finale connue de 5.</span><span class="sxs-lookup"><span data-stu-id="78883-147">The condition checks the value of the loop variable against a known final value, 5.</span></span>  
  
-   <span data-ttu-id="78883-148">La section Itérateur utilise une instruction d’incrémentation suffixée, `i++`, pour calculer chaque itération de la boucle.</span><span class="sxs-lookup"><span data-stu-id="78883-148">The iterator section uses a postfix increment statement, `i++`, to tally each iteration of the loop.</span></span>  
  
 <span data-ttu-id="78883-149">L’exemple suivant montre plusieurs choix moins courants : l’attribution d’une valeur à une variable de boucle externe dans la section Initialiseur, l’appel de la méthode `Console.WriteLine` dans les sections Initialiseur et Itérateur, et la modification des valeurs de deux variables dans la section Itérateur.</span><span class="sxs-lookup"><span data-stu-id="78883-149">The following example illustrates several less common choices: assigning a value to an external loop variable in the initializer section,  invoking the `Console.WriteLine` method in both the initializer and the iterator sections, and changing the values of two variables in the iterator section.</span></span>  
  
 [!code-csharp[csrefKeywordsIteration#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/for_2.cs)]  
  
 <span data-ttu-id="78883-150">Toutes les expressions qui définissent une instruction `for` sont facultatives.</span><span class="sxs-lookup"><span data-stu-id="78883-150">All of the expressions that define a `for` statement are optional.</span></span> <span data-ttu-id="78883-151">Par exemple, l’instruction suivante crée une boucle infinie.</span><span class="sxs-lookup"><span data-stu-id="78883-151">For example, the following statement creates an infinite loop.</span></span>  
  
 [!code-csharp[csrefKeywordsIteration#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/for_3.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="78883-152">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="78883-152">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="78883-153">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="78883-153">See Also</span></span>  
 [<span data-ttu-id="78883-154">Référence C#</span><span class="sxs-lookup"><span data-stu-id="78883-154">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="78883-155">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="78883-155">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="78883-156">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="78883-156">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="78883-157">foreach, in</span><span class="sxs-lookup"><span data-stu-id="78883-157">foreach, in</span></span>](../../../csharp/language-reference/keywords/foreach-in.md)  
 [<span data-ttu-id="78883-158">for, instruction (C++)</span><span class="sxs-lookup"><span data-stu-id="78883-158">for Statement (C++)</span></span>](/cpp/cpp/for-statement-cpp)  
 [<span data-ttu-id="78883-159">Instructions d’itération</span><span class="sxs-lookup"><span data-stu-id="78883-159">Iteration Statements</span></span>](../../../csharp/language-reference/keywords/iteration-statements.md)
