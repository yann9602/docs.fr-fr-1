---
title: "Exécution d’arborescences d’expressions"
description: "En savoir plus sur l’exécution des arborescences d’expressions en les convertissant en instructions de langage intermédiaire exécutables."
keywords: .NET, .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 109e0ac5-2a9c-48b4-ac68-9b6219cdbccf
ms.openlocfilehash: db481c18a79f55b079ec2558b884ce288e2a9933
ms.sourcegitcommit: 6a9030eb5bd0f00e1d144f81958adb195cfb1f6f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/10/2018
---
# <a name="executing-expression-trees"></a><span data-ttu-id="25f1e-104">Exécution d’arborescences d’expressions</span><span class="sxs-lookup"><span data-stu-id="25f1e-104">Executing Expression Trees</span></span>

[<span data-ttu-id="25f1e-105">Précédent -- Types de frameworks prenant en charge les arborescences d’expressions</span><span class="sxs-lookup"><span data-stu-id="25f1e-105">Previous -- Framework Types Supporting Expression Trees</span></span>](expression-classes.md)

<span data-ttu-id="25f1e-106">Une *arborescence d’expressions* est une structure de données qui représente du code.</span><span class="sxs-lookup"><span data-stu-id="25f1e-106">An *expression tree* is a data structure that represents some code.</span></span>
<span data-ttu-id="25f1e-107">Il ne s’agit pas de code compilé et exécutable.</span><span class="sxs-lookup"><span data-stu-id="25f1e-107">It is not compiled and executable code.</span></span> <span data-ttu-id="25f1e-108">Si vous souhaitez exécuter le code .NET représenté par une arborescence d’expressions, vous devez le convertir en instructions de langage intermédiaire exécutables.</span><span class="sxs-lookup"><span data-stu-id="25f1e-108">If you want to execute the .NET code that is represented by an expression tree, you must convert it into executable IL instructions.</span></span> 
## <a name="lambda-expressions-to-functions"></a><span data-ttu-id="25f1e-109">Des expressions lambda aux fonctions</span><span class="sxs-lookup"><span data-stu-id="25f1e-109">Lambda Expressions to Functions</span></span>
<span data-ttu-id="25f1e-110">Vous pouvez convertir n’importe quelle LambdaExpression ou n’importe quel type dérivé de LambdaExpression en langage intermédiaire exécutable.</span><span class="sxs-lookup"><span data-stu-id="25f1e-110">You can convert any LambdaExpression, or any type derived from LambdaExpression into executable IL.</span></span> <span data-ttu-id="25f1e-111">Les autres types d’expressions ne peuvent pas être convertis directement en code.</span><span class="sxs-lookup"><span data-stu-id="25f1e-111">Other expression types cannot be directly converted into code.</span></span> <span data-ttu-id="25f1e-112">Cette restriction a peu d’effet dans la pratique.</span><span class="sxs-lookup"><span data-stu-id="25f1e-112">This restriction has little effect in practice.</span></span> <span data-ttu-id="25f1e-113">Les expressions lambda sont les seuls types d’expressions que vous pourriez souhaiter exécuter par l’intermédiaire d’une conversion en langage intermédiaire exécutable.</span><span class="sxs-lookup"><span data-stu-id="25f1e-113">Lambda expressions are the only types of expressions that you would want to execute by converting to executable intermediate language (IL).</span></span> <span data-ttu-id="25f1e-114">(Pensez à ce que cela signifierait d’exécuter directement une `ConstantExpression`.</span><span class="sxs-lookup"><span data-stu-id="25f1e-114">(Think about what it would mean to directly execute a `ConstantExpression`.</span></span> <span data-ttu-id="25f1e-115">Serait-ce utile ?) Toute arborescence d’expressions qui est une `LamdbaExpression` ou un type dérivé de `LambdaExpression` peut être convertie en langage intermédiaire.</span><span class="sxs-lookup"><span data-stu-id="25f1e-115">Would it mean anything useful?) Any expression tree that is a `LamdbaExpression`, or a type derived from `LambdaExpression` can be converted to IL.</span></span>
<span data-ttu-id="25f1e-116">Le type d’expression `Expression<TDelegate>` est le seul exemple concret dans les bibliothèques .NET Core.</span><span class="sxs-lookup"><span data-stu-id="25f1e-116">The expression type `Expression<TDelegate>` is the only concrete example in the .NET Core libraries.</span></span> <span data-ttu-id="25f1e-117">Il sert à représenter une expression mappée à un type délégué quelconque.</span><span class="sxs-lookup"><span data-stu-id="25f1e-117">It's used to represent an expression that maps to any delegate type.</span></span> <span data-ttu-id="25f1e-118">Ce type étant mappé à un type délégué, .NET peut examiner l’expression et générer le langage intermédiaire pour un délégué approprié qui correspond à la signature de l’expression lambda.</span><span class="sxs-lookup"><span data-stu-id="25f1e-118">Because this type maps to a delegate type, .NET can examine the expression, and generate IL for an appropriate delegate that matches the signature of the lambda expression.</span></span> 

<span data-ttu-id="25f1e-119">Dans la plupart des cas, cela crée un mappage simple entre une expression et son délégué correspondant.</span><span class="sxs-lookup"><span data-stu-id="25f1e-119">In most cases, this creates a simple mapping between an expression, and its corresponding delegate.</span></span> <span data-ttu-id="25f1e-120">Par exemple, une arborescence d’expressions représentée par `Expression<Func<int>>` serait convertie en un délégué du type `Func<int>`.</span><span class="sxs-lookup"><span data-stu-id="25f1e-120">For example, an expression tree that is represented by `Expression<Func<int>>` would be converted to a delegate of the type `Func<int>`.</span></span> <span data-ttu-id="25f1e-121">Pour une expression lambda avec tout type de retour et liste d’arguments, il existe un type délégué qui est le type cible pour le code exécutable représenté par cette expression lambda.</span><span class="sxs-lookup"><span data-stu-id="25f1e-121">For a lambda expression with any return type and argument list, there exists a delegate type that is the target type for the executable code represented by that lamdba expression.</span></span>

<span data-ttu-id="25f1e-122">Le type `LamdbaExpression` contient des membres `Compile` et `CompileToMethod` que vous utiliseriez pour convertir une arborescence d’expressions en code exécutable.</span><span class="sxs-lookup"><span data-stu-id="25f1e-122">The `LamdbaExpression` type contains `Compile` and `CompileToMethod` members that you would use to convert an expression tree to executable code.</span></span> <span data-ttu-id="25f1e-123">La méthode `Compile` crée un délégué.</span><span class="sxs-lookup"><span data-stu-id="25f1e-123">The `Compile` method creates a delegate.</span></span> <span data-ttu-id="25f1e-124">La méthode `CompileToMethod` met à jour un objet `MethodBuilder` avec le langage intermédiaire qui représente la sortie compilée de l’arborescence d’expressions.</span><span class="sxs-lookup"><span data-stu-id="25f1e-124">The `CompileToMethod` method updates a `MethodBuilder` object with the IL that represents the compiled output of the expression tree.</span></span> <span data-ttu-id="25f1e-125">Notez que `CompileToMethod` n’est disponible que sur le framework de bureau complet, et non sur le framework .NET Core.</span><span class="sxs-lookup"><span data-stu-id="25f1e-125">Note that `CompileToMethod` is only available on the full desktop framework, not on the .NET Core framework.</span></span>

<span data-ttu-id="25f1e-126">Si vous le souhaitez, vous pouvez également fournir un `DebugInfoGenerator` qui recevra les informations de débogage de symbole pour l’objet délégué généré.</span><span class="sxs-lookup"><span data-stu-id="25f1e-126">Optionally, you can also provide a `DebugInfoGenerator` that will receive the symbol debugging information for the generated delegate object.</span></span> <span data-ttu-id="25f1e-127">Cela vous permet de convertir l’arborescence d’expressions en objet délégué et de disposer d’informations de débogage complètes sur le délégué généré.</span><span class="sxs-lookup"><span data-stu-id="25f1e-127">This enables you to convert the expression tree into a delegate object, and have full debugging information about the generated delegate.</span></span>

<span data-ttu-id="25f1e-128">Vous pouvez convertir une expression en délégué à l’aide du code suivant :</span><span class="sxs-lookup"><span data-stu-id="25f1e-128">You would convert an expression into a delegate using the following code:</span></span>

```csharp
Expression<Func<int>> add = () => 1 + 2;
var func = add.Compile(); // Create Delegate
var answer = func(); // Invoke Delegate
Console.WriteLine(answer);
```

<span data-ttu-id="25f1e-129">Notez que le type délégué est basé sur le type d’expression.</span><span class="sxs-lookup"><span data-stu-id="25f1e-129">Notice that the delegate type is based on the expression type.</span></span> <span data-ttu-id="25f1e-130">Si vous souhaitez utiliser l’objet délégué d’une manière fortement typée, vous devez connaître le type de retour et la liste d’arguments.</span><span class="sxs-lookup"><span data-stu-id="25f1e-130">You must know the return type and the argument list if you want to use the delegate object in a strongly typed manner.</span></span> <span data-ttu-id="25f1e-131">La méthode `LambdaExpression.Compile()` retourne le type `Delegate`.</span><span class="sxs-lookup"><span data-stu-id="25f1e-131">The `LambdaExpression.Compile()` method returns the `Delegate` type.</span></span> <span data-ttu-id="25f1e-132">Vous devrez effectuer un cast sur le type délégué approprié pour que les outils de compilation puissent vérifier la liste d’arguments de type de retour.</span><span class="sxs-lookup"><span data-stu-id="25f1e-132">You will have to cast it to the correct delegate type to have any compile-time tools check the argument list of return type.</span></span>

## <a name="execution-and-lifetimes"></a><span data-ttu-id="25f1e-133">Exécution et durées de vie</span><span class="sxs-lookup"><span data-stu-id="25f1e-133">Execution and Lifetimes</span></span>

<span data-ttu-id="25f1e-134">Vous exécutez le code en appelant le délégué créé quand vous avez appelé `LamdbaExpression.Compile()`.</span><span class="sxs-lookup"><span data-stu-id="25f1e-134">You execute the code by invoking the delegate created when you called `LamdbaExpression.Compile()`.</span></span> <span data-ttu-id="25f1e-135">Vous pouvez l’observer ci-dessus, où `add.Compile()` retourne un délégué.</span><span class="sxs-lookup"><span data-stu-id="25f1e-135">You can see this above where `add.Compile()` returns a delegate.</span></span> <span data-ttu-id="25f1e-136">L’appel de ce délégué en appelant `func()` exécute le code.</span><span class="sxs-lookup"><span data-stu-id="25f1e-136">Invoking that delegate, by calling `func()` executes the code.</span></span>

<span data-ttu-id="25f1e-137">Ce délégué représente le code dans l’arborescence d’expressions.</span><span class="sxs-lookup"><span data-stu-id="25f1e-137">That delegate represents the code in the expression tree.</span></span> <span data-ttu-id="25f1e-138">Vous pouvez conserver le handle de ce délégué et l’appeler ultérieurement.</span><span class="sxs-lookup"><span data-stu-id="25f1e-138">You can retain the handle to that delegate and invoke it later.</span></span> <span data-ttu-id="25f1e-139">Vous n’avez pas besoin de compiler l’arborescence d’expressions chaque fois que vous souhaitez exécuter le code qu’elle représente.</span><span class="sxs-lookup"><span data-stu-id="25f1e-139">You don't need to compile the expression tree each time you want to execute the code it represents.</span></span> <span data-ttu-id="25f1e-140">(N’oubliez pas que les arborescences d’expressions sont immuables ; compiler la même arborescence d’expressions ultérieurement crée un délégué qui exécute le même code.)</span><span class="sxs-lookup"><span data-stu-id="25f1e-140">(Remember that expression trees are immutable, and compiling the same expression tree later will create a delegate that executes the same code.)</span></span>

<span data-ttu-id="25f1e-141">Je vous déconseille d’essayer de créer des mécanismes de mise en cache plus complexes pour améliorer les performances en évitant les appels de compilation inutiles.</span><span class="sxs-lookup"><span data-stu-id="25f1e-141">I will caution you against trying to create any more sophisticated caching mechanisms to increase performance by avoiding unnecessary compile calls.</span></span> <span data-ttu-id="25f1e-142">Comparer deux arborescences d’expressions arbitraires pour déterminer si elles représentent le même algorithme prend également beaucoup de temps.</span><span class="sxs-lookup"><span data-stu-id="25f1e-142">Comparing two arbitrary expression trees to determine if they represent the same algorithm will also be time consuming to execute.</span></span> <span data-ttu-id="25f1e-143">Vous vous rendrez sans doute compte que le temps de calcul économisé en évitant tout appel supplémentaire à `LambdaExpression.Compile()` sera largement contrebalancé par le temps passé à exécuter le code qui détermine si deux arborescences d’expressions génèrent le même code exécutable.</span><span class="sxs-lookup"><span data-stu-id="25f1e-143">You'll likely find that the compute time you save avoiding any extra calls to `LambdaExpression.Compile()` will be more than consumed by the time executing code that determines of two different expression trees result in the same executable code.</span></span>

## <a name="caveats"></a><span data-ttu-id="25f1e-144">Avertissements</span><span class="sxs-lookup"><span data-stu-id="25f1e-144">Caveats</span></span>

<span data-ttu-id="25f1e-145">Compiler une expression lambda en un délégué et appeler ce délégué sont l’une des opérations les plus simples que vous puissiez effectuer avec une arborescence d’expressions.</span><span class="sxs-lookup"><span data-stu-id="25f1e-145">Compiling a lambda expression to a delegate and invoking that delegate is one of the simplest operations you can perform with an expression tree.</span></span> <span data-ttu-id="25f1e-146">Toutefois, même avec cette simple opération, il existe des pièges dont vous devez être conscient.</span><span class="sxs-lookup"><span data-stu-id="25f1e-146">However, even with this simple operation, there are caveats you must be aware of.</span></span> 

<span data-ttu-id="25f1e-147">Les expressions lambda créent des fermetures sur toutes les variables locales qui sont référencées dans l’expression.</span><span class="sxs-lookup"><span data-stu-id="25f1e-147">Lambda Expressions create closures over any local variables that are referenced in the expression.</span></span> <span data-ttu-id="25f1e-148">Vous devez vérifier que toutes les variables qui font partie du délégué sont utilisables à l’emplacement où vous appelez `Compile` et quand vous exécutez le délégué résultant.</span><span class="sxs-lookup"><span data-stu-id="25f1e-148">You must guarantee that any variables that would be part of the delegate are usable at the location where you call `Compile`, and when you execute the resulting delegate.</span></span>

<span data-ttu-id="25f1e-149">En règle générale, le compilateur s’assure que ce soit le cas.</span><span class="sxs-lookup"><span data-stu-id="25f1e-149">In general, the compiler will ensure that this is true.</span></span> <span data-ttu-id="25f1e-150">Toutefois, si votre expression accède à une variable qui implémente `IDisposable`, il est possible que votre code supprime l’objet alors qu’il est toujours détenu par l’arborescence d’expressions.</span><span class="sxs-lookup"><span data-stu-id="25f1e-150">However, if your expression accesses a variable that implements `IDisposable`, it's possible that your code might dispose of the object while it is still held by the expression tree.</span></span>

<span data-ttu-id="25f1e-151">Par exemple, ce code fonctionne bien, car `int` n’implémente pas `IDisposable` :</span><span class="sxs-lookup"><span data-stu-id="25f1e-151">For example, this code works fine, because `int` does not implement `IDisposable`:</span></span>

```csharp
private static Func<int, int> CreateBoundFunc()
{
    var constant = 5; // constant is captured by the expression tree
    Expression<Func<int, int>> expression = (b) => constant + b;
    var rVal = expression.Compile();
    return rVal;
}
```

<span data-ttu-id="25f1e-152">Le délégué a capturé une référence à la variable locale `constant`.</span><span class="sxs-lookup"><span data-stu-id="25f1e-152">The delegate has captured a reference to the local variable `constant`.</span></span>
<span data-ttu-id="25f1e-153">Cette variable est accessible à tout moment ultérieurement, quand la fonction retournée par `CreateBoundFunc` s’exécute.</span><span class="sxs-lookup"><span data-stu-id="25f1e-153">That variable is accessed at any time later, when the function returned by `CreateBoundFunc` executes.</span></span>

<span data-ttu-id="25f1e-154">Maintenant, examinez cette classe qui implémente `IDisposable` :</span><span class="sxs-lookup"><span data-stu-id="25f1e-154">However, consider this (rather contrived) class that implements `IDisposable`:</span></span>

```csharp
public class Resource : IDisposable
{
    private bool isDisposed = false;
    public int Argument
    {
        get
        {
            if (!isDisposed)
                return 5;
            else throw new ObjectDisposedException("Resource");
        }
    }

    public void Dispose()
    {
        isDisposed = true;
    }
}
```

<span data-ttu-id="25f1e-155">Si vous l’utilisez dans une expression comme illustré ci-dessous, vous obtenez une `ObjectDisposedException` quand vous exécutez le code référencé par la propriété `Resource.Argument` :</span><span class="sxs-lookup"><span data-stu-id="25f1e-155">If you use it in an expression as shown below, you'll get an `ObjectDisposedException` when you execute the code referenced by the `Resource.Argument` property:</span></span>

```csharp
private static Func<int, int> CreateBoundResource()
{
    using (var constant = new Resource()) // constant is captured by the expression tree
    {
        Expression<Func<int, int>> expression = (b) => constant.Argument + b;
        var rVal = expression.Compile();
        return rVal;
    }
}
```

<span data-ttu-id="25f1e-156">Le délégué retourné par cette méthode a fermé l’objet `constant`, qui a été supprimé.</span><span class="sxs-lookup"><span data-stu-id="25f1e-156">The delegate returned from this method has closed over the `constant` object, which has been disposed of.</span></span> <span data-ttu-id="25f1e-157">(Il a été supprimé car il a été déclaré dans une instruction `using`.)</span><span class="sxs-lookup"><span data-stu-id="25f1e-157">(It's been disposed, because it was declared in a `using` statement.)</span></span> 

<span data-ttu-id="25f1e-158">Désormais, quand vous exécuterez le délégué retourné par cette méthode, une `ObjecctDisposedException` sera levée au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="25f1e-158">Now, when you execute the delegate returned from this method, you'll have a `ObjecctDisposedException` thrown at the point of execution.</span></span>

<span data-ttu-id="25f1e-159">Cela semble étrange d’avoir une erreur d’exécution qui représente une construction de compilation, mais cela fait partie des éventualités quand nous travaillons avec des arborescences d’expressions.</span><span class="sxs-lookup"><span data-stu-id="25f1e-159">It does seem strange to have a runtime error representing a compile-time construct, but that's the world we enter when we work with expression trees.</span></span>

<span data-ttu-id="25f1e-160">Comme il existe de nombreuses permutations de ce problème, il est difficile de proposer des conseils généraux pour l’éviter.</span><span class="sxs-lookup"><span data-stu-id="25f1e-160">There are a lot of permutations of this problem, so it's hard to offer general guidance to avoid it.</span></span> <span data-ttu-id="25f1e-161">Faites attention si vous accédez à des variables locales quand vous définissez des expressions et faites attention si vous accédez à l’état de l’objet actif (représenté par `this`) quand vous créez une arborescence d’expressions qui peut être retournée par une API publique.</span><span class="sxs-lookup"><span data-stu-id="25f1e-161">Be careful about accessing local variables when defining expressions, and be careful about accessing state in the current object (represented by `this`) when creating an expression tree that can be returned by a public API.</span></span>

<span data-ttu-id="25f1e-162">Le code dans votre expression peut référencer des méthodes ou des propriétés dans d’autres assemblys.</span><span class="sxs-lookup"><span data-stu-id="25f1e-162">The code in your expression may reference methods or properties in other assemblies.</span></span> <span data-ttu-id="25f1e-163">Ces assemblys doivent être accessibles quand l’expression est définie, quand elle est compilée et quand le délégué résultant est appelé.</span><span class="sxs-lookup"><span data-stu-id="25f1e-163">That assembly must be accessible when the expression is defined, and when it is compiled, and when the resulting delegate is invoked.</span></span> <span data-ttu-id="25f1e-164">S’il n’est pas présent, vous recevrez une `ReferencedAssemblyNotFoundException`.</span><span class="sxs-lookup"><span data-stu-id="25f1e-164">You'll be met with a `ReferencedAssemblyNotFoundException` in cases where it is not present.</span></span>

## <a name="summary"></a><span data-ttu-id="25f1e-165">Récapitulatif</span><span class="sxs-lookup"><span data-stu-id="25f1e-165">Summary</span></span>

<span data-ttu-id="25f1e-166">Les arborescences d’expressions qui représentent des expressions lambda peuvent être compilées pour créer un délégué exécutable.</span><span class="sxs-lookup"><span data-stu-id="25f1e-166">Expression Trees that represent lambda expressions can be compiled to create a delegate that you can execute.</span></span> <span data-ttu-id="25f1e-167">Cela fournit un mécanisme pour exécuter le code représenté par une arborescence d’expressions.</span><span class="sxs-lookup"><span data-stu-id="25f1e-167">This provides one mechanism to execute the code represented by an expression tree.</span></span>

<span data-ttu-id="25f1e-168">L’arborescence d’expressions représente le code qui s’exécuterait pour toute construction donnée que vous créez.</span><span class="sxs-lookup"><span data-stu-id="25f1e-168">The Expression Tree does represent the code that would execute for any given construct you create.</span></span> <span data-ttu-id="25f1e-169">Tant que l’environnement dans lequel vous compilez et exécutez le code correspond à celui dans lequel vous créez une expression, tout fonctionne comme prévu.</span><span class="sxs-lookup"><span data-stu-id="25f1e-169">As long as the environment where you compile and execute the code matches the environment where you create the expression, everything works as expected.</span></span> <span data-ttu-id="25f1e-170">Si ce n’est pas le cas, les erreurs sont très prévisibles et seront interceptées lors de vos premiers tests de n’importe quel code utilisant les arborescences d’expressions.</span><span class="sxs-lookup"><span data-stu-id="25f1e-170">When that doesn't happen, the errors are very predictable, and they will be caught in your first tests of any code using the expression trees.</span></span>

[<span data-ttu-id="25f1e-171">Suivant -- Interprétation d’expressions</span><span class="sxs-lookup"><span data-stu-id="25f1e-171">Next -- Interpreting Expressions</span></span>](expression-trees-interpreting.md)
