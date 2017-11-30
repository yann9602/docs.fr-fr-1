---
title: "Démarrage rapide - Branches et lops - Guide c#"
description: "Dans ce guide de démarrage rapide sur les branches et des boucles, vous écrivez du code c# pour Explorer la syntaxe du langage qui prend en charge des branches conditionnelles et des boucles pour exécuter des instructions à plusieurs reprises."
author: billwagner
ms.author: wiwagn
ms.date: 10/31/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.custom: mvc
ms.openlocfilehash: 4b077a29cf42072a93b054f50a13a4580ad54304
ms.sourcegitcommit: 43c656811dd38a66a6672084c65d10c0cbbf2015
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2017
---
# <a name="branches-and-loops"></a><span data-ttu-id="39490-103">Branches et boucles</span><span class="sxs-lookup"><span data-stu-id="39490-103">Branches and loops</span></span>

<span data-ttu-id="39490-104">Ce guide de démarrage rapide vous apprend comment écrire du code qui examine les variables et modifie le chemin d’accès de l’exécution en fonction de ces variables.</span><span class="sxs-lookup"><span data-stu-id="39490-104">This quick start teaches you how to write code that examines variables and changes the execution path based on those variables.</span></span> <span data-ttu-id="39490-105">Écrire du code c# et de voir les résultats de la compilation et son exécution.</span><span class="sxs-lookup"><span data-stu-id="39490-105">You write C# code and see the results of compiling and running it.</span></span> <span data-ttu-id="39490-106">Le démarrage rapide contient une série de leçons qui explorent la création de branche et de constructions de boucle dans c#.</span><span class="sxs-lookup"><span data-stu-id="39490-106">The quick start contains a series of lessons that explore branching and looping constructs in C#.</span></span> <span data-ttu-id="39490-107">Ces leçons présentent les concepts de base du langage C#.</span><span class="sxs-lookup"><span data-stu-id="39490-107">These lessons teach you the fundamentals of the C# language.</span></span>

<span data-ttu-id="39490-108">Ce démarrage rapide attend que vous disposiez d’un ordinateur, que vous pouvez utiliser pour le développement.</span><span class="sxs-lookup"><span data-stu-id="39490-108">This quick start expects you to have a machine you can use for development.</span></span> <span data-ttu-id="39490-109">La rubrique .NET [prise en main de 10 minutes](https://www.microsoft.com/net/core) a des instructions pour configurer votre environnement de développement local sur le Mac, PC ou Linux.</span><span class="sxs-lookup"><span data-stu-id="39490-109">The .NET topic [Get Started in 10 minutes](https://www.microsoft.com/net/core) has instructions for setting up your local development environment on Mac, PC or Linux.</span></span>

## <a name="make-decisions-using-the-if-statement"></a><span data-ttu-id="39490-110">Prenez les décisions relatives à l’aide de la `if` instruction</span><span class="sxs-lookup"><span data-stu-id="39490-110">Make decisions using the `if` statement</span></span>

<span data-ttu-id="39490-111">Créez un répertoire nommé **branches-démarrage rapide**.</span><span class="sxs-lookup"><span data-stu-id="39490-111">Create a directory named **branches-quickstart**.</span></span> <span data-ttu-id="39490-112">Faites-en le répertoire actuel et exécutez `dotnet new console -n BranchesAndLoops -o .`.</span><span class="sxs-lookup"><span data-stu-id="39490-112">Make that the current directory and run `dotnet new console -n BranchesAndLoops -o .`.</span></span> <span data-ttu-id="39490-113">Cette commande crée une nouvelle application de console .NET Core dans le répertoire actif.</span><span class="sxs-lookup"><span data-stu-id="39490-113">This command creates a new .NET Core console application in the current directory.</span></span> 

<span data-ttu-id="39490-114">Ouvrez **Program.cs** dans votre éditeur favori, puis remplacez la ligne `Console.Writeline("Hello World!");` par le code suivant :</span><span class="sxs-lookup"><span data-stu-id="39490-114">Open **Program.cs** in your favorite editor, and replace the line `Console.Writeline("Hello World!");` with the following code:</span></span>

```csharp
int a = 5;
int b = 6;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10.");
```

<span data-ttu-id="39490-115">Essayez le code suivant en tapant `dotnet run` dans la fenêtre de la console.</span><span class="sxs-lookup"><span data-stu-id="39490-115">Try this code by typing `dotnet run` in the your console window.</span></span> <span data-ttu-id="39490-116">Vous devez voir le message « la réponse est supérieure à 10 ».</span><span class="sxs-lookup"><span data-stu-id="39490-116">You should see the message "The answer is greater than 10."</span></span> <span data-ttu-id="39490-117">imprimé à votre console.</span><span class="sxs-lookup"><span data-stu-id="39490-117">printed to your console.</span></span>

<span data-ttu-id="39490-118">Modifiez la déclaration de `b` pour que la somme soit inférieure à 10 :</span><span class="sxs-lookup"><span data-stu-id="39490-118">Modify the declaration of `b` so that the sum is less than 10:</span></span> 

```csharp
int b = 3;
```

<span data-ttu-id="39490-119">Type `dotnet run` à nouveau.</span><span class="sxs-lookup"><span data-stu-id="39490-119">Type `dotnet run` again.</span></span> <span data-ttu-id="39490-120">La réponse étant inférieure à 10, rien ne s’affiche.</span><span class="sxs-lookup"><span data-stu-id="39490-120">Because the answer is less than 10, nothing is printed.</span></span> <span data-ttu-id="39490-121">La **condition** que vous testez a une valeur false.</span><span class="sxs-lookup"><span data-stu-id="39490-121">The **condition** you're testing is false.</span></span> <span data-ttu-id="39490-122">Vous n’avez pas de code à exécuter, car vous avez uniquement écrit l’une des branches possibles pour une instruction `if` : la branche true.</span><span class="sxs-lookup"><span data-stu-id="39490-122">You don't have any code to execute because you've only written one of the possible branches for an `if` statement: the true branch.</span></span>

> [!TIP]
> <span data-ttu-id="39490-123">Durant votre exploration de C# (ou de tout autre langage de programmation), vous commettrez des erreurs d’écriture du code.</span><span class="sxs-lookup"><span data-stu-id="39490-123">As you explore C# (or any programming language), you'll make mistakes when you write code.</span></span> <span data-ttu-id="39490-124">Le compilateur détecte et signaler les erreurs.</span><span class="sxs-lookup"><span data-stu-id="39490-124">The compiler will find and report the errors.</span></span> <span data-ttu-id="39490-125">Examinez attentivement la sortie d’erreur et le code qui a généré l’erreur.</span><span class="sxs-lookup"><span data-stu-id="39490-125">Look closely the the error output and the code that generated the error.</span></span> <span data-ttu-id="39490-126">L’erreur compler peut généralement vous aider à identifier le problème.</span><span class="sxs-lookup"><span data-stu-id="39490-126">The compler error can usually help you find the problem.</span></span> 

<span data-ttu-id="39490-127">Le premier exemple montre la puissance de `if` et types booléens.</span><span class="sxs-lookup"><span data-stu-id="39490-127">This first sample shows the power of `if` and Boolean types.</span></span> <span data-ttu-id="39490-128">A *booléenne* est une variable qui peut avoir une des deux valeurs : `true` ou `false`.</span><span class="sxs-lookup"><span data-stu-id="39490-128">A *Boolean* is a variable that can have one of two values: `true` or `false`.</span></span> <span data-ttu-id="39490-129">C# définit un type spécial, `bool` des variables booléennes.</span><span class="sxs-lookup"><span data-stu-id="39490-129">C# defines a special type, `bool` for Boolean variables.</span></span> <span data-ttu-id="39490-130">L’instruction `if` vérifie la valeur d’un `bool`.</span><span class="sxs-lookup"><span data-stu-id="39490-130">The `if` statement checks the value of a `bool`.</span></span> <span data-ttu-id="39490-131">Quand la valeur est `true`, l’instruction qui suit `if` s’exécute.</span><span class="sxs-lookup"><span data-stu-id="39490-131">When the value is `true`, the statement following the `if` executes.</span></span> <span data-ttu-id="39490-132">Dans le cas contraire, elle est ignorée.</span><span class="sxs-lookup"><span data-stu-id="39490-132">Otherwise, it is skipped.</span></span> 

<span data-ttu-id="39490-133">Ce processus de vérification des conditions et d’exécution des instructions en fonction de ces conditions est très performant.</span><span class="sxs-lookup"><span data-stu-id="39490-133">This process of checking conditions and executing statements based on those conditions is very powerful.</span></span>


## <a name="make-if-and-else-work-together"></a><span data-ttu-id="39490-134">Utiliser if et else ensemble</span><span class="sxs-lookup"><span data-stu-id="39490-134">Make if and else work together</span></span>

<span data-ttu-id="39490-135">Pour exécuter un code différent dans les branches true et false, vous créez une branche `else` qui s’exécute quand la condition a une valeur false.</span><span class="sxs-lookup"><span data-stu-id="39490-135">To execute different code in both the true and false branches, you create an `else` branch that executes when the condition is false.</span></span> <span data-ttu-id="39490-136">Sont manquants.</span><span class="sxs-lookup"><span data-stu-id="39490-136">Try this.</span></span> <span data-ttu-id="39490-137">Ajoutez les deux dernières lignes dans le code suivant à votre `Main` (méthode) (vous devez déjà avoir les quatre premiers) :</span><span class="sxs-lookup"><span data-stu-id="39490-137">Add the last two lines in the code below to your `Main` method (you should already have the first four):</span></span>

```csharp
int a = 5;
int b = 3;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10");
else
    Console.WriteLine("The answer is not greater than 10");
```

<span data-ttu-id="39490-138">L’instruction qui suit le mot clé `else` s’exécute uniquement quand la condition testée a une valeur `false`.</span><span class="sxs-lookup"><span data-stu-id="39490-138">The statement following the `else` keyword executes only when the condition being tested is `false`.</span></span> <span data-ttu-id="39490-139">Combinaison de `if` et `else` avec une valeur booléenne conditions fournit toute la puissance dont vous avez besoin pour gérer à la fois un `true` et un `false` condition.</span><span class="sxs-lookup"><span data-stu-id="39490-139">Combining `if` and `else` with Boolean conditions provides all the power you need to handle both a `true` and a `false` condition.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="39490-140">La mise en retrait sous les instructions `if` et `else` a simplement pour but de faciliter la lecture.</span><span class="sxs-lookup"><span data-stu-id="39490-140">The indentation under the `if` and `else` statements is for human readers.</span></span>
> <span data-ttu-id="39490-141">Le langage C# ne considère pas la mise en retrait ou les espaces blancs comme des éléments significatifs.</span><span class="sxs-lookup"><span data-stu-id="39490-141">The C# language doesn't treat indentation or whitespace as significant.</span></span> <span data-ttu-id="39490-142">L’instruction qui suit le mot clé `if` ou `else` sera exécutée en fonction de la condition.</span><span class="sxs-lookup"><span data-stu-id="39490-142">The statement following the `if` or `else` keyword will be executed based on the condition.</span></span> <span data-ttu-id="39490-143">Tous les exemples dans ce démarrage rapide suivent une pratique courante pour mettre en retrait les lignes selon le flux de contrôle d’instructions.</span><span class="sxs-lookup"><span data-stu-id="39490-143">All the samples in this quick start follow a common practice to indent lines based on the control flow of statements.</span></span>

<span data-ttu-id="39490-144">Étant donné que la mise en retrait n’est pas significative, vous devez utiliser `{` et `}` pour indiquer quand vous souhaitez inclure plus d’une instruction dans le bloc qui s’exécute de manière conditionnelle.</span><span class="sxs-lookup"><span data-stu-id="39490-144">Because indentation is not significant, you need to use `{` and `}` to indicate when you want more than one statement to be part of the block that executes conditionally.</span></span> <span data-ttu-id="39490-145">Les programmeurs C# utilisent généralement les accolades pour toutes les clauses `if` et `else`.</span><span class="sxs-lookup"><span data-stu-id="39490-145">C# programmers typically use those braces on all `if` and `else` clauses.</span></span> <span data-ttu-id="39490-146">L’exemple suivant est identique à celui que vous venez de créer.</span><span class="sxs-lookup"><span data-stu-id="39490-146">The following example is the same as the one you just created.</span></span> <span data-ttu-id="39490-147">Modifiez le code ci-dessus pour faire correspondre le code suivant :</span><span class="sxs-lookup"><span data-stu-id="39490-147">Modify your code above to match the following code:</span></span>

```csharp
int a = 5;
int b = 3;
if (a + b > 10)
{
    Console.WriteLine("The answer is greater than 10");
}
else
{
    Console.WriteLine("The answer is not greater than 10");
}
```

> [!TIP]
> <span data-ttu-id="39490-148">Le reste de ce guide de démarrage rapide, tous les exemples de code incluent les accolades suivant accepté pratiques.</span><span class="sxs-lookup"><span data-stu-id="39490-148">Through the rest of this quick start, the code samples all include the braces, following accepted practices.</span></span>

<span data-ttu-id="39490-149">Vous pouvez tester des conditions plus complexes.</span><span class="sxs-lookup"><span data-stu-id="39490-149">You can test more complicated conditions.</span></span> <span data-ttu-id="39490-150">Ajoutez le code suivant dans votre `Main` méthode après le code que vous avez écrits jusqu'à présent :</span><span class="sxs-lookup"><span data-stu-id="39490-150">Add the following code in your `Main` method after the code you've written so far:</span></span>

```csharp
    int c = 4;
    if ((a + b + c > 10) && (a > b))
{
    Console.WriteLine("The answer is greater than 10");
    Console.WriteLine("And the first number is greater than the second");
}
else
{
    Console.WriteLine("The answer is not greater than 10");
    Console.WriteLine("Or the first number is not greater than the second");
}
```

<span data-ttu-id="39490-151">`&&` représente « et ».</span><span class="sxs-lookup"><span data-stu-id="39490-151">The `&&` represents "and".</span></span> <span data-ttu-id="39490-152">Cela signifie que les deux conditions doivent être true pour que l’instruction s’exécute dans la branche true.</span><span class="sxs-lookup"><span data-stu-id="39490-152">It means both conditions must be true to execute the statement in the true branch.</span></span>  <span data-ttu-id="39490-153">Ces exemples montrent également que vous pouvez avoir plusieurs instructions dans chaque branche conditionnelle, à condition de les mettre entre `{` et `}`.</span><span class="sxs-lookup"><span data-stu-id="39490-153">These examples also show that you can have multiple statements in each conditional branch, provided you enclose them in `{` and `}`.</span></span>

<span data-ttu-id="39490-154">Vous pouvez également utiliser `||` pour représenter « ou ».</span><span class="sxs-lookup"><span data-stu-id="39490-154">You can also use  `||` to represent "or".</span></span> <span data-ttu-id="39490-155">Une fois que vous avez écrits jusqu'à présent, ajoutez le code suivant :</span><span class="sxs-lookup"><span data-stu-id="39490-155">Add the following code after what you've written so far:</span></span>

```csharp
if ((a + b + c > 10) || (a > b))
{
    Console.WriteLine("The answer is greater than 10");
    Console.WriteLine("Or the first number is greater than the second");
}
else
{
    Console.WriteLine("The answer is not greater than 10");
    Console.WriteLine("And the first number is not greater than the second");
}
```

<span data-ttu-id="39490-156">Vous avez terminé la première étape.</span><span class="sxs-lookup"><span data-stu-id="39490-156">You've finished the first step.</span></span> <span data-ttu-id="39490-157">Avant de passer à la section suivante, déplaçons le code actuel dans une méthode distincte.</span><span class="sxs-lookup"><span data-stu-id="39490-157">Before you start the next section, let's move the current code into a separate method.</span></span> <span data-ttu-id="39490-158">Cela nous permettra de travailler plus facilement avec un nouvel exemple.</span><span class="sxs-lookup"><span data-stu-id="39490-158">That makes it easier to start working with a new example.</span></span> <span data-ttu-id="39490-159">Renommez votre méthode `Main` `ExploreIf` et écrivez une nouvelle méthode `Main` qui appelle `ExploreIf`.</span><span class="sxs-lookup"><span data-stu-id="39490-159">Rename your `Main` method to `ExploreIf` and write a new `Main` method that calls `ExploreIf`.</span></span> <span data-ttu-id="39490-160">Une fois terminé, votre code doit ressembler au code suivant :</span><span class="sxs-lookup"><span data-stu-id="39490-160">When you have finished, your code should look like this:</span></span>

```csharp
using System;

namespace BranchesAndLoops
{
    class Program
    {
        static void ExploreIf()
        {
            int a = 5;
            int b = 3;
            if (a + b > 10)
            {
                Console.WriteLine("The answer is greater than 10");
            }
            else
            {
                Console.WriteLine("The answer is not greater than 10");
            }

            if ((a + b + c > 10) && (a > b))
            {
                Console.WriteLine("The answer is greater than 10");
                Console.WriteLine("And the first number is greater than the second");
            }
            else
            {
                Console.WriteLine("The answer is not greater than 10");
                Console.WriteLine("Or the first number is not greater than the second");
            }

            if ((a + b + c > 10) || (a > b))
            {
                Console.WriteLine("The answer is greater than 10");
                Console.WriteLine("Or the first number is greater than the second");
            }
            else
            {
                Console.WriteLine("The answer is not greater than 10");
                Console.WriteLine("And the first number is not greater than the second");
            }            
        }

        static void Main(string[] args)
        {
            ExploreIf();
        }
    }
}
```

<span data-ttu-id="39490-161">Commentez l’appel à `ExploreIf()`.</span><span class="sxs-lookup"><span data-stu-id="39490-161">Comment out the call to `ExploreIf()`.</span></span> <span data-ttu-id="39490-162">Il effectue la sortie que moins encombrée lorsque vous travaillez dans cette section :</span><span class="sxs-lookup"><span data-stu-id="39490-162">It will make the output less cluttered as you work in this section:</span></span>

```csharp
//ExploreIf();
```

<span data-ttu-id="39490-163">Le `//` démarre un **commentaire** en c#.</span><span class="sxs-lookup"><span data-stu-id="39490-163">The `//` starts a **comment** in C#.</span></span> <span data-ttu-id="39490-164">Les commentaires sont n’importe quel texte que vous souhaitez conserver dans votre code source, mais pas s’exécuter en tant que code.</span><span class="sxs-lookup"><span data-stu-id="39490-164">Comments are any text you want to keep in your source code but not execute as code.</span></span> <span data-ttu-id="39490-165">Le compilateur ne génère pas de code exécutable à partir de commentaires.</span><span class="sxs-lookup"><span data-stu-id="39490-165">The compiler does not generate any executable code from comments.</span></span>

## <a name="use-loops-to-repeat-operations"></a><span data-ttu-id="39490-166">Utiliser des boucles pour répéter des opérations</span><span class="sxs-lookup"><span data-stu-id="39490-166">Use loops to repeat operations</span></span>

<span data-ttu-id="39490-167">Dans cette section, vous utilisez **boucles** à répéter les instructions.</span><span class="sxs-lookup"><span data-stu-id="39490-167">In this section you use **loops** to repeat statements.</span></span> <span data-ttu-id="39490-168">Essayez le code suivant dans votre `Main` méthode :</span><span class="sxs-lookup"><span data-stu-id="39490-168">Try this code in your `Main` method:</span></span>

```csharp
int counter = 0;
while (counter < 10)
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
}
```

<span data-ttu-id="39490-169">Le `while` instruction vérifie une condition et exécute l’instruction ou le bloc d’instructions suivant le `while`.</span><span class="sxs-lookup"><span data-stu-id="39490-169">The `while` statement checks a condition and executes the statement or statement block following the `while`.</span></span> <span data-ttu-id="39490-170">À plusieurs reprises, il vérifie la condition et l’exécution de ces instructions jusqu'à ce que la condition est false.</span><span class="sxs-lookup"><span data-stu-id="39490-170">It repeatedly checks the condition and executing those statements until the condition is false.</span></span>

<span data-ttu-id="39490-171">Cet exemple contient un nouvel opérateur.</span><span class="sxs-lookup"><span data-stu-id="39490-171">There's one other new operator in this example.</span></span> <span data-ttu-id="39490-172">`++` après la variable `counter` est l’opérateur d’**incrémentation**.</span><span class="sxs-lookup"><span data-stu-id="39490-172">The `++` after the `counter` variable is the **increment** operator.</span></span> <span data-ttu-id="39490-173">Il ajoute 1 à la valeur de `counter` et stocke cette valeur dans la `counter` variable.</span><span class="sxs-lookup"><span data-stu-id="39490-173">It adds 1 to the value of `counter` and stores that value in the `counter` variable.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="39490-174">Assurez-vous que le `while` sur false, les modifications de condition de boucle lorsque vous exécutez le code.</span><span class="sxs-lookup"><span data-stu-id="39490-174">Make sure that the `while` loop condition changes to false as you execute the code.</span></span> <span data-ttu-id="39490-175">Dans le cas contraire, vous allez créer une **boucle infinie** dans laquelle votre programme ne se terminera jamais.</span><span class="sxs-lookup"><span data-stu-id="39490-175">Otherwise, you create an **infinite loop** where your program never ends.</span></span> <span data-ttu-id="39490-176">Qui n’est pas illustrée dans cet exemple, car vous devez forcer votre programme pour cesser d’utiliser **CTRL-C** ou d’autres moyens.</span><span class="sxs-lookup"><span data-stu-id="39490-176">That is not demonstrated in this sample, because you have to force your program to quit using **CTRL-C** or other means.</span></span>

<span data-ttu-id="39490-177">La boucle `while` teste la condition avant d’exécuter le code qui suit `while`.</span><span class="sxs-lookup"><span data-stu-id="39490-177">The `while` loop tests the condition before executing the code following the `while`.</span></span> <span data-ttu-id="39490-178">La boucle `do` ... `while` exécute d’abord le code, puis vérifie la condition.</span><span class="sxs-lookup"><span data-stu-id="39490-178">The `do` ... `while` loop executes the code first, and then checks the condition.</span></span> <span data-ttu-id="39490-179">Faire lors de la boucle est indiquée dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="39490-179">The do while loop is shown in the following code:</span></span>

```csharp
counter = 0;
do
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
} while (counter < 10);
```

<span data-ttu-id="39490-180">Cela `do` boucle et la plus antérieure `while` boucle produisent le même résultat.</span><span class="sxs-lookup"><span data-stu-id="39490-180">This `do` loop and the earlier `while` loop produce the same output.</span></span>

## <a name="work-with-the-for-loop"></a><span data-ttu-id="39490-181">Utiliser la boucle for</span><span class="sxs-lookup"><span data-stu-id="39490-181">Work with the for loop</span></span>

<span data-ttu-id="39490-182">Le **pour** boucle est couramment utilisée dans c#.</span><span class="sxs-lookup"><span data-stu-id="39490-182">The **for** loop is commonly used in C#.</span></span> <span data-ttu-id="39490-183">Essayez ce code dans votre méthode Main() :</span><span class="sxs-lookup"><span data-stu-id="39490-183">Try this code in your Main() method:</span></span>

```csharp
for(int index = 0; index < 10; index++)
{
    Console.WriteLine($"Hello World! The index is {index}");
} 
```

<span data-ttu-id="39490-184">Cette boucle fonctionne de manière identique à la boucle `while` et la boucle `do` que vous avez déjà utilisées.</span><span class="sxs-lookup"><span data-stu-id="39490-184">This does the same work as the `while` loop and the `do` loop you've already used.</span></span> <span data-ttu-id="39490-185">L’instruction `for` comprend trois parties qui contrôlent son fonctionnement.</span><span class="sxs-lookup"><span data-stu-id="39490-185">The `for` statement has three parts that control how it works.</span></span> 

<span data-ttu-id="39490-186">La première partie est l’**initialiseur for** : `for index = 0;` déclare que `index` est la variable de boucle et définit sa valeur initiale sur `0`.</span><span class="sxs-lookup"><span data-stu-id="39490-186">The first part is the **for initializer**: `for index = 0;` declares that `index` is the loop variable, and sets its initial value to `0`.</span></span>

<span data-ttu-id="39490-187">La partie centrale est la **condition for** : `index < 10` déclare que cette boucle `for` continue à s’exécuter tant que la valeur de compteur est inférieure à 10.</span><span class="sxs-lookup"><span data-stu-id="39490-187">The middle part is the **for condition**: `index < 10` declares that this `for` loop continues to execute as long as the value of counter is less than 10.</span></span>

<span data-ttu-id="39490-188">La dernière partie est l’**itérateur for** : `index++` indique comment modifier la variable de boucle après l’exécution du bloc qui suit l’instruction `for`.</span><span class="sxs-lookup"><span data-stu-id="39490-188">The final part is the **for iterator**: `index++` specifies how to modify the loop variable after executing the block following the `for` statement.</span></span> <span data-ttu-id="39490-189">Il spécifie ici que `index` doit être incrémenté de 1 chaque fois que le bloc s’exécute.</span><span class="sxs-lookup"><span data-stu-id="39490-189">Here, it specifies that `index` should be incremented by 1 each time the block executes.</span></span>

<span data-ttu-id="39490-190">Vérifiez-le par vous-même.</span><span class="sxs-lookup"><span data-stu-id="39490-190">Experiment with these yourself.</span></span> <span data-ttu-id="39490-191">Réalisez les essais suivants :</span><span class="sxs-lookup"><span data-stu-id="39490-191">Try each of the following:</span></span>

- <span data-ttu-id="39490-192">Modifiez l’initialiseur pour définir le démarrage à une valeur différente.</span><span class="sxs-lookup"><span data-stu-id="39490-192">Change the initializer to start at a different value.</span></span>
- <span data-ttu-id="39490-193">Modifiez la condition pour définir l’arrêt à une valeur différente.</span><span class="sxs-lookup"><span data-stu-id="39490-193">Change the condition to stop at a different value.</span></span>

<span data-ttu-id="39490-194">Une fois terminé, vous allez vous-même écrire des codes pour mettre en pratique ce que vous avez appris.</span><span class="sxs-lookup"><span data-stu-id="39490-194">When you're done, let's move on to write some code yourself to use what you've learned.</span></span>

## <a name="combine-branches-and-loops"></a><span data-ttu-id="39490-195">Combiner des branches et des boucles</span><span class="sxs-lookup"><span data-stu-id="39490-195">Combine branches and loops</span></span>

<span data-ttu-id="39490-196">Maintenant que vous avez vu l’instruction `if` et la création de boucles en langage C#, vérifiez si vous pouvez écrire un code C# pour obtenir la somme de tous les entiers de 1 à 20 divisibles par 3.</span><span class="sxs-lookup"><span data-stu-id="39490-196">Now that you've seen the `if` statement and the looping constructs in the C# language, see if you can write C# code to find the sum of all integers 1 through 20 that are divisible by 3.</span></span>  <span data-ttu-id="39490-197">Voici quelques conseils :</span><span class="sxs-lookup"><span data-stu-id="39490-197">Here are a few hints:</span></span>

- <span data-ttu-id="39490-198">L’opérateur `%` vous donne le reste d’une opération de division.</span><span class="sxs-lookup"><span data-stu-id="39490-198">The `%` operator gives you the remainder of a division operation.</span></span>
- <span data-ttu-id="39490-199">La `if` instruction vous donne la condition pour voir si un nombre doit être la partie de la somme.</span><span class="sxs-lookup"><span data-stu-id="39490-199">The `if` statement gives you the condition to see if a number should be part of the sum.</span></span>
- <span data-ttu-id="39490-200">La boucle `for` peut vous aider à répéter une série d’étapes pour tous les nombres de 1 à 20.</span><span class="sxs-lookup"><span data-stu-id="39490-200">The `for` loop can help you repeat a series of steps for all the numbers 1 through 20.</span></span>

<span data-ttu-id="39490-201">Essayez par vous-même</span><span class="sxs-lookup"><span data-stu-id="39490-201">Try it yourself.</span></span> <span data-ttu-id="39490-202">et vérifiez le résultat.</span><span class="sxs-lookup"><span data-stu-id="39490-202">Then check how you did.</span></span> <span data-ttu-id="39490-203">Vous pouvez voir une réponse possible par [affichage du code terminé sur GitHub](https://github.com/dotnet/docs/tree/master/samples/csharp/branches-quickstart/Program.cs#L46-L54).</span><span class="sxs-lookup"><span data-stu-id="39490-203">You can see one possible answer by [viewing the completed code on GitHub](https://github.com/dotnet/docs/tree/master/samples/csharp/branches-quickstart/Program.cs#L46-L54).</span></span>

<span data-ttu-id="39490-204">Vous avez terminé le démarrage rapide de « branches et effectue une boucle ».</span><span class="sxs-lookup"><span data-stu-id="39490-204">You've completed the "branches and loops" quick start.</span></span>

<span data-ttu-id="39490-205">Vous pouvez poursuivre la [tableaux et collections](arrays-and-collections.md) démarrage rapide dans votre propre environnement de développement.</span><span class="sxs-lookup"><span data-stu-id="39490-205">You can continue with the [Arrays and collections](arrays-and-collections.md) quick start in your own development environment.</span></span>

<span data-ttu-id="39490-206">Pour en savoir plus sur ces concepts, consultez les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="39490-206">You can learn more about these concepts in these topics:</span></span>

<span data-ttu-id="39490-207">[Instruction if et else](../language-reference/keywords/if-else.md) </span><span class="sxs-lookup"><span data-stu-id="39490-207">[If and else statement](../language-reference/keywords/if-else.md) </span></span>  
<span data-ttu-id="39490-208">[Instruction while](../language-reference/keywords/while.md) </span><span class="sxs-lookup"><span data-stu-id="39490-208">[While statement](../language-reference/keywords/while.md) </span></span>  
<span data-ttu-id="39490-209">[Instruction do](../language-reference/keywords/do.md) </span><span class="sxs-lookup"><span data-stu-id="39490-209">[Do statement](../language-reference/keywords/do.md) </span></span>  
[<span data-ttu-id="39490-210">Instruction for</span><span class="sxs-lookup"><span data-stu-id="39490-210">For statement</span></span>](../language-reference/keywords/for.md)   
