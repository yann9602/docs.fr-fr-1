---
title: "Démarrage rapide - Branches et boucles - Guide C#"
description: "Dans ce guide de démarrage rapide sur les branches et les boucles, vous écrivez du code en C# pour explorer la syntaxe de langage qui prend en charge les branches et boucles conditionnelles pour exécuter des instructions de manière répétée."
author: billwagner
ms.author: wiwagn
ms.date: 10/31/2017
ms.topic: get-started-article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.custom: mvc
ms.openlocfilehash: 609c8625b19025a20c1da1e767870eafbab4c4a0
ms.sourcegitcommit: 8bde7a3432f30fc771079744955c75c58c4eb393
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/20/2018
---
# <a name="branches-and-loops"></a><span data-ttu-id="9ec95-103">Branches et boucles</span><span class="sxs-lookup"><span data-stu-id="9ec95-103">Branches and loops</span></span>

<span data-ttu-id="9ec95-104">Ce guide de démarrage rapide vous explique comment écrire un code qui examine des variables et modifie un chemin d’exécution en fonction de ces variables.</span><span class="sxs-lookup"><span data-stu-id="9ec95-104">This quick start teaches you how to write code that examines variables and changes the execution path based on those variables.</span></span> <span data-ttu-id="9ec95-105">Vous allez écrire un code en C# et afficher les résultats de la compilation et de l’exécution du code.</span><span class="sxs-lookup"><span data-stu-id="9ec95-105">You write C# code and see the results of compiling and running it.</span></span> <span data-ttu-id="9ec95-106">Le guide de démarrage rapide contient une série de leçons pour explorer la création de branches et de boucles en C#.</span><span class="sxs-lookup"><span data-stu-id="9ec95-106">The quick start contains a series of lessons that explore branching and looping constructs in C#.</span></span> <span data-ttu-id="9ec95-107">Ces leçons présentent les concepts de base du langage C#.</span><span class="sxs-lookup"><span data-stu-id="9ec95-107">These lessons teach you the fundamentals of the C# language.</span></span>

<span data-ttu-id="9ec95-108">Ce guide de démarrage rapide suppose que vous disposez d’un ordinateur que vous pouvez utiliser pour le développement.</span><span class="sxs-lookup"><span data-stu-id="9ec95-108">This quick start expects you to have a machine you can use for development.</span></span> <span data-ttu-id="9ec95-109">La rubrique .NET [Bien démarrer en 10 minutes](https://www.microsoft.com/net/core) contient des instructions pour configurer votre environnement de développement local sur Mac, PC ou Linux.</span><span class="sxs-lookup"><span data-stu-id="9ec95-109">The .NET topic [Get Started in 10 minutes](https://www.microsoft.com/net/core) has instructions for setting up your local development environment on Mac, PC or Linux.</span></span> <span data-ttu-id="9ec95-110">Une brève vue d’ensemble des commandes que vous utiliserez est disponible dans la [présentation des guides de démarrage rapide locaux](local-environment.md) avec des liens pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="9ec95-110">A quick overview of the commands you'll use is in the [introduction to the local quick starts](local-environment.md) with links to more details.</span></span>

## <a name="make-decisions-using-the-if-statement"></a><span data-ttu-id="9ec95-111">Prendre des décisions à l’aide de l’instruction `if`</span><span class="sxs-lookup"><span data-stu-id="9ec95-111">Make decisions using the `if` statement</span></span>

<span data-ttu-id="9ec95-112">Créez un répertoire nommé **branches-quickstart**.</span><span class="sxs-lookup"><span data-stu-id="9ec95-112">Create a directory named **branches-quickstart**.</span></span> <span data-ttu-id="9ec95-113">Faites-en le répertoire actuel et exécutez `dotnet new console -n BranchesAndLoops -o .`.</span><span class="sxs-lookup"><span data-stu-id="9ec95-113">Make that the current directory and run `dotnet new console -n BranchesAndLoops -o .`.</span></span> <span data-ttu-id="9ec95-114">Cette commande crée une nouvelle application console .NET Core dans le répertoire actuel.</span><span class="sxs-lookup"><span data-stu-id="9ec95-114">This command creates a new .NET Core console application in the current directory.</span></span> 

<span data-ttu-id="9ec95-115">Ouvrez **Program.cs** dans votre éditeur favori, puis remplacez la ligne `Console.Writeline("Hello World!");` par le code qui suit :</span><span class="sxs-lookup"><span data-stu-id="9ec95-115">Open **Program.cs** in your favorite editor, and replace the line `Console.Writeline("Hello World!");` with the following code:</span></span>

```csharp
int a = 5;
int b = 6;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10.");
```

<span data-ttu-id="9ec95-116">Essayez ce code en tapant `dotnet run` dans la fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="9ec95-116">Try this code by typing `dotnet run` in the your console window.</span></span> <span data-ttu-id="9ec95-117">Le message « La réponse est supérieure à 10 » doit s’afficher</span><span class="sxs-lookup"><span data-stu-id="9ec95-117">You should see the message "The answer is greater than 10."</span></span> <span data-ttu-id="9ec95-118">dans votre console.</span><span class="sxs-lookup"><span data-stu-id="9ec95-118">printed to your console.</span></span>

<span data-ttu-id="9ec95-119">Modifiez la déclaration de `b` pour que la somme soit inférieure à 10 :</span><span class="sxs-lookup"><span data-stu-id="9ec95-119">Modify the declaration of `b` so that the sum is less than 10:</span></span> 

```csharp
int b = 3;
```

<span data-ttu-id="9ec95-120">Tapez `dotnet run` à nouveau.</span><span class="sxs-lookup"><span data-stu-id="9ec95-120">Type `dotnet run` again.</span></span> <span data-ttu-id="9ec95-121">La réponse étant inférieure à 10, rien ne s’affiche.</span><span class="sxs-lookup"><span data-stu-id="9ec95-121">Because the answer is less than 10, nothing is printed.</span></span> <span data-ttu-id="9ec95-122">La **condition** que vous testez a une valeur false.</span><span class="sxs-lookup"><span data-stu-id="9ec95-122">The **condition** you're testing is false.</span></span> <span data-ttu-id="9ec95-123">Vous n’avez pas de code à exécuter, car vous avez uniquement écrit l’une des branches possibles pour une instruction `if` : la branche true.</span><span class="sxs-lookup"><span data-stu-id="9ec95-123">You don't have any code to execute because you've only written one of the possible branches for an `if` statement: the true branch.</span></span>

> [!TIP]
> <span data-ttu-id="9ec95-124">Durant votre exploration de C# (ou de tout autre langage de programmation), vous commettrez des erreurs d’écriture du code.</span><span class="sxs-lookup"><span data-stu-id="9ec95-124">As you explore C# (or any programming language), you'll make mistakes when you write code.</span></span> <span data-ttu-id="9ec95-125">Le compilateur détectera et signalera les erreurs.</span><span class="sxs-lookup"><span data-stu-id="9ec95-125">The compiler will find and report the errors.</span></span> <span data-ttu-id="9ec95-126">Observez attentivement la sortie d’erreur et le code ayant généré l’erreur.</span><span class="sxs-lookup"><span data-stu-id="9ec95-126">Look closely at the error output and the code that generated the error.</span></span> <span data-ttu-id="9ec95-127">L’erreur du compilateur peut en général vous aider à trouver le problème.</span><span class="sxs-lookup"><span data-stu-id="9ec95-127">The compler error can usually help you find the problem.</span></span> 

<span data-ttu-id="9ec95-128">Le premier exemple montre la puissance de l’instruction `if` et des types booléens.</span><span class="sxs-lookup"><span data-stu-id="9ec95-128">This first sample shows the power of `if` and Boolean types.</span></span> <span data-ttu-id="9ec95-129">Un *booléen* est une variable qui peut avoir l’une des deux valeurs suivantes : `true` ou `false`.</span><span class="sxs-lookup"><span data-stu-id="9ec95-129">A *Boolean* is a variable that can have one of two values: `true` or `false`.</span></span> <span data-ttu-id="9ec95-130">C# définit un type spécial, `bool`, pour les variables booléennes.</span><span class="sxs-lookup"><span data-stu-id="9ec95-130">C# defines a special type, `bool` for Boolean variables.</span></span> <span data-ttu-id="9ec95-131">L’instruction `if` vérifie la valeur d’un `bool`.</span><span class="sxs-lookup"><span data-stu-id="9ec95-131">The `if` statement checks the value of a `bool`.</span></span> <span data-ttu-id="9ec95-132">Quand la valeur est `true`, l’instruction qui suit `if` s’exécute.</span><span class="sxs-lookup"><span data-stu-id="9ec95-132">When the value is `true`, the statement following the `if` executes.</span></span> <span data-ttu-id="9ec95-133">Dans le cas contraire, elle est ignorée.</span><span class="sxs-lookup"><span data-stu-id="9ec95-133">Otherwise, it is skipped.</span></span> 

<span data-ttu-id="9ec95-134">Ce processus de vérification des conditions et d’exécution des instructions en fonction de ces conditions est très performant.</span><span class="sxs-lookup"><span data-stu-id="9ec95-134">This process of checking conditions and executing statements based on those conditions is very powerful.</span></span>


## <a name="make-if-and-else-work-together"></a><span data-ttu-id="9ec95-135">Utiliser if et else ensemble</span><span class="sxs-lookup"><span data-stu-id="9ec95-135">Make if and else work together</span></span>

<span data-ttu-id="9ec95-136">Pour exécuter un code différent dans les branches true et false, vous créez une branche `else` qui s’exécute quand la condition a une valeur false.</span><span class="sxs-lookup"><span data-stu-id="9ec95-136">To execute different code in both the true and false branches, you create an `else` branch that executes when the condition is false.</span></span> <span data-ttu-id="9ec95-137">Essayez ceci.</span><span class="sxs-lookup"><span data-stu-id="9ec95-137">Try this.</span></span> <span data-ttu-id="9ec95-138">Ajoutez les deux dernières lignes dans le code ci-dessous à votre méthode `Main` (vous devriez déjà avoir les quatre premières lignes) :</span><span class="sxs-lookup"><span data-stu-id="9ec95-138">Add the last two lines in the code below to your `Main` method (you should already have the first four):</span></span>

```csharp
int a = 5;
int b = 3;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10");
else
    Console.WriteLine("The answer is not greater than 10");
```

<span data-ttu-id="9ec95-139">L’instruction qui suit le mot clé `else` s’exécute uniquement quand la condition testée a une valeur `false`.</span><span class="sxs-lookup"><span data-stu-id="9ec95-139">The statement following the `else` keyword executes only when the condition being tested is `false`.</span></span> <span data-ttu-id="9ec95-140">La combinaison de `if` et `else` avec des conditions booléennes offre les hautes performances dont vous avez besoin pour traiter une condition `true` et une condition `false`.</span><span class="sxs-lookup"><span data-stu-id="9ec95-140">Combining `if` and `else` with Boolean conditions provides all the power you need to handle both a `true` and a `false` condition.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9ec95-141">La mise en retrait sous les instructions `if` et `else` a simplement pour but de faciliter la lecture.</span><span class="sxs-lookup"><span data-stu-id="9ec95-141">The indentation under the `if` and `else` statements is for human readers.</span></span>
> <span data-ttu-id="9ec95-142">Le langage C# ne considère pas la mise en retrait ou les espaces blancs comme des éléments significatifs.</span><span class="sxs-lookup"><span data-stu-id="9ec95-142">The C# language doesn't treat indentation or whitespace as significant.</span></span> <span data-ttu-id="9ec95-143">L’instruction qui suit le mot clé `if` ou `else` sera exécutée en fonction de la condition.</span><span class="sxs-lookup"><span data-stu-id="9ec95-143">The statement following the `if` or `else` keyword will be executed based on the condition.</span></span> <span data-ttu-id="9ec95-144">Tous les exemples de ce guide de démarrage rapide suivent une pratique courante pour mettre en retrait les lignes en fonction du flux de contrôle des instructions.</span><span class="sxs-lookup"><span data-stu-id="9ec95-144">All the samples in this quick start follow a common practice to indent lines based on the control flow of statements.</span></span>

<span data-ttu-id="9ec95-145">Étant donné que la mise en retrait n’est pas significative, vous devez utiliser `{` et `}` pour indiquer quand vous souhaitez inclure plus d’une instruction dans le bloc qui s’exécute de manière conditionnelle.</span><span class="sxs-lookup"><span data-stu-id="9ec95-145">Because indentation is not significant, you need to use `{` and `}` to indicate when you want more than one statement to be part of the block that executes conditionally.</span></span> <span data-ttu-id="9ec95-146">Les programmeurs C# utilisent généralement les accolades pour toutes les clauses `if` et `else`.</span><span class="sxs-lookup"><span data-stu-id="9ec95-146">C# programmers typically use those braces on all `if` and `else` clauses.</span></span> <span data-ttu-id="9ec95-147">L’exemple suivant est identique à celui que vous venez de créer.</span><span class="sxs-lookup"><span data-stu-id="9ec95-147">The following example is the same as the one you just created.</span></span> <span data-ttu-id="9ec95-148">Modifiez votre code ci-dessus pour qu’il corresponde au code suivant :</span><span class="sxs-lookup"><span data-stu-id="9ec95-148">Modify your code above to match the following code:</span></span>

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
> <span data-ttu-id="9ec95-149">Dans le reste de ce guide de démarrage rapide, tous les exemples de code incluent les accolades, conformément aux pratiques acceptées.</span><span class="sxs-lookup"><span data-stu-id="9ec95-149">Through the rest of this quick start, the code samples all include the braces, following accepted practices.</span></span>

<span data-ttu-id="9ec95-150">Vous pouvez tester des conditions plus complexes.</span><span class="sxs-lookup"><span data-stu-id="9ec95-150">You can test more complicated conditions.</span></span> <span data-ttu-id="9ec95-151">Ajoutez le code suivant à votre méthode `Main` après le code que vous avez écrit jusque-là :</span><span class="sxs-lookup"><span data-stu-id="9ec95-151">Add the following code in your `Main` method after the code you've written so far:</span></span>

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

<span data-ttu-id="9ec95-152">`&&` représente « et ».</span><span class="sxs-lookup"><span data-stu-id="9ec95-152">The `&&` represents "and".</span></span> <span data-ttu-id="9ec95-153">Cela signifie que les deux conditions doivent être true pour que l’instruction s’exécute dans la branche true.</span><span class="sxs-lookup"><span data-stu-id="9ec95-153">It means both conditions must be true to execute the statement in the true branch.</span></span>  <span data-ttu-id="9ec95-154">Ces exemples montrent également que vous pouvez avoir plusieurs instructions dans chaque branche conditionnelle, à condition de les mettre entre `{` et `}`.</span><span class="sxs-lookup"><span data-stu-id="9ec95-154">These examples also show that you can have multiple statements in each conditional branch, provided you enclose them in `{` and `}`.</span></span>

<span data-ttu-id="9ec95-155">Vous pouvez également utiliser `||` pour représenter « ou ».</span><span class="sxs-lookup"><span data-stu-id="9ec95-155">You can also use  `||` to represent "or".</span></span> <span data-ttu-id="9ec95-156">Ajoutez le code suivant après ce que vous avez écrit jusque-là :</span><span class="sxs-lookup"><span data-stu-id="9ec95-156">Add the following code after what you've written so far:</span></span>

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

<span data-ttu-id="9ec95-157">Vous avez terminé la première étape.</span><span class="sxs-lookup"><span data-stu-id="9ec95-157">You've finished the first step.</span></span> <span data-ttu-id="9ec95-158">Avant de passer à la section suivante, déplaçons le code actuel dans une méthode distincte.</span><span class="sxs-lookup"><span data-stu-id="9ec95-158">Before you start the next section, let's move the current code into a separate method.</span></span> <span data-ttu-id="9ec95-159">Cela nous permettra de travailler plus facilement avec un nouvel exemple.</span><span class="sxs-lookup"><span data-stu-id="9ec95-159">That makes it easier to start working with a new example.</span></span> <span data-ttu-id="9ec95-160">Renommez votre méthode `Main` `ExploreIf` et écrivez une nouvelle méthode `Main` qui appelle `ExploreIf`.</span><span class="sxs-lookup"><span data-stu-id="9ec95-160">Rename your `Main` method to `ExploreIf` and write a new `Main` method that calls `ExploreIf`.</span></span> <span data-ttu-id="9ec95-161">Une fois terminé, votre code doit ressembler au code suivant :</span><span class="sxs-lookup"><span data-stu-id="9ec95-161">When you have finished, your code should look like this:</span></span>

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

<span data-ttu-id="9ec95-162">Commentez l’appel à `ExploreIf()`.</span><span class="sxs-lookup"><span data-stu-id="9ec95-162">Comment out the call to `ExploreIf()`.</span></span> <span data-ttu-id="9ec95-163">La sortie est ainsi moins encombrée lorsque vous travaillez dans cette section :</span><span class="sxs-lookup"><span data-stu-id="9ec95-163">It will make the output less cluttered as you work in this section:</span></span>

```csharp
//ExploreIf();
```

<span data-ttu-id="9ec95-164">`//` démarre un **commentaire** dans C#.</span><span class="sxs-lookup"><span data-stu-id="9ec95-164">The `//` starts a **comment** in C#.</span></span> <span data-ttu-id="9ec95-165">Les commentaires correspondent à du texte que vous voulez conserver dans votre code source sans l’exécuter en tant que code.</span><span class="sxs-lookup"><span data-stu-id="9ec95-165">Comments are any text you want to keep in your source code but not execute as code.</span></span> <span data-ttu-id="9ec95-166">Le compilateur ne génère aucun fichier exécutable à partir des commentaires.</span><span class="sxs-lookup"><span data-stu-id="9ec95-166">The compiler does not generate any executable code from comments.</span></span>

## <a name="use-loops-to-repeat-operations"></a><span data-ttu-id="9ec95-167">Utiliser des boucles pour répéter des opérations</span><span class="sxs-lookup"><span data-stu-id="9ec95-167">Use loops to repeat operations</span></span>

<span data-ttu-id="9ec95-168">Dans cette section vous utilisez des **boucles** pour répéter des instructions.</span><span class="sxs-lookup"><span data-stu-id="9ec95-168">In this section you use **loops** to repeat statements.</span></span> <span data-ttu-id="9ec95-169">Essayez ce code dans votre méthode `Main` :</span><span class="sxs-lookup"><span data-stu-id="9ec95-169">Try this code in your `Main` method:</span></span>

```csharp
int counter = 0;
while (counter < 10)
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
}
```

<span data-ttu-id="9ec95-170">L’instruction `while` vérifie une condition et exécute l’instruction ou le bloc d’instructions qui suit `while`.</span><span class="sxs-lookup"><span data-stu-id="9ec95-170">The `while` statement checks a condition and executes the statement or statement block following the `while`.</span></span> <span data-ttu-id="9ec95-171">Elle répète la vérification de la condition et l’exécution de ces instructions jusqu'à ce que la condition soit false.</span><span class="sxs-lookup"><span data-stu-id="9ec95-171">It repeatedly checks the condition and executing those statements until the condition is false.</span></span>

<span data-ttu-id="9ec95-172">Cet exemple contient un nouvel opérateur.</span><span class="sxs-lookup"><span data-stu-id="9ec95-172">There's one other new operator in this example.</span></span> <span data-ttu-id="9ec95-173">`++` après la variable `counter` est l’opérateur d’**incrémentation**.</span><span class="sxs-lookup"><span data-stu-id="9ec95-173">The `++` after the `counter` variable is the **increment** operator.</span></span> <span data-ttu-id="9ec95-174">Il ajoute 1 à la valeur de `counter` et stocke cette valeur dans la variable de `counter`.</span><span class="sxs-lookup"><span data-stu-id="9ec95-174">It adds 1 to the value of `counter` and stores that value in the `counter` variable.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9ec95-175">Assurez-vous que la condition de boucle `while` devient false quand vous exécutez le code.</span><span class="sxs-lookup"><span data-stu-id="9ec95-175">Make sure that the `while` loop condition changes to false as you execute the code.</span></span> <span data-ttu-id="9ec95-176">Dans le cas contraire, vous allez créer une **boucle infinie** dans laquelle votre programme ne se terminera jamais.</span><span class="sxs-lookup"><span data-stu-id="9ec95-176">Otherwise, you create an **infinite loop** where your program never ends.</span></span> <span data-ttu-id="9ec95-177">Ceci n’est pas démontré dans cet exemple, car vous devez forcer la fermeture de votre programme avec **CTRL-C** ou à l’aide d’autres moyens.</span><span class="sxs-lookup"><span data-stu-id="9ec95-177">That is not demonstrated in this sample, because you have to force your program to quit using **CTRL-C** or other means.</span></span>

<span data-ttu-id="9ec95-178">La boucle `while` teste la condition avant d’exécuter le code qui suit `while`.</span><span class="sxs-lookup"><span data-stu-id="9ec95-178">The `while` loop tests the condition before executing the code following the `while`.</span></span> <span data-ttu-id="9ec95-179">La boucle `do` ... `while` exécute d’abord le code, puis vérifie la condition.</span><span class="sxs-lookup"><span data-stu-id="9ec95-179">The `do` ... `while` loop executes the code first, and then checks the condition.</span></span> <span data-ttu-id="9ec95-180">La boucle do while est illustrée dans l’exemple de code suivant :</span><span class="sxs-lookup"><span data-stu-id="9ec95-180">The do while loop is shown in the following code:</span></span>

```csharp
counter = 0;
do
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
} while (counter < 10);
```

<span data-ttu-id="9ec95-181">Cette boucle `do` et la boucle antérieure `while` produisent la même sortie.</span><span class="sxs-lookup"><span data-stu-id="9ec95-181">This `do` loop and the earlier `while` loop produce the same output.</span></span>

## <a name="work-with-the-for-loop"></a><span data-ttu-id="9ec95-182">Utiliser la boucle for</span><span class="sxs-lookup"><span data-stu-id="9ec95-182">Work with the for loop</span></span>

<span data-ttu-id="9ec95-183">La boucle **for** est couramment utilisée dans C#.</span><span class="sxs-lookup"><span data-stu-id="9ec95-183">The **for** loop is commonly used in C#.</span></span> <span data-ttu-id="9ec95-184">Essayez ce code dans votre méthode Main() :</span><span class="sxs-lookup"><span data-stu-id="9ec95-184">Try this code in your Main() method:</span></span>

```csharp
for(int index = 0; index < 10; index++)
{
    Console.WriteLine($"Hello World! The index is {index}");
} 
```

<span data-ttu-id="9ec95-185">Cette boucle fonctionne de manière identique à la boucle `while` et la boucle `do` que vous avez déjà utilisées.</span><span class="sxs-lookup"><span data-stu-id="9ec95-185">This does the same work as the `while` loop and the `do` loop you've already used.</span></span> <span data-ttu-id="9ec95-186">L’instruction `for` comprend trois parties qui contrôlent son fonctionnement.</span><span class="sxs-lookup"><span data-stu-id="9ec95-186">The `for` statement has three parts that control how it works.</span></span> 

<span data-ttu-id="9ec95-187">La première partie est l’**initialiseur for** : `for index = 0;` déclare que `index` est la variable de boucle et définit sa valeur initiale sur `0`.</span><span class="sxs-lookup"><span data-stu-id="9ec95-187">The first part is the **for initializer**: `for index = 0;` declares that `index` is the loop variable, and sets its initial value to `0`.</span></span>

<span data-ttu-id="9ec95-188">La partie centrale est la **condition for** : `index < 10` déclare que cette boucle `for` continue à s’exécuter tant que la valeur de compteur est inférieure à 10.</span><span class="sxs-lookup"><span data-stu-id="9ec95-188">The middle part is the **for condition**: `index < 10` declares that this `for` loop continues to execute as long as the value of counter is less than 10.</span></span>

<span data-ttu-id="9ec95-189">La dernière partie est l’**itérateur for** : `index++` indique comment modifier la variable de boucle après l’exécution du bloc qui suit l’instruction `for`.</span><span class="sxs-lookup"><span data-stu-id="9ec95-189">The final part is the **for iterator**: `index++` specifies how to modify the loop variable after executing the block following the `for` statement.</span></span> <span data-ttu-id="9ec95-190">Il spécifie ici que `index` doit être incrémenté de 1 chaque fois que le bloc s’exécute.</span><span class="sxs-lookup"><span data-stu-id="9ec95-190">Here, it specifies that `index` should be incremented by 1 each time the block executes.</span></span>

<span data-ttu-id="9ec95-191">Vérifiez-le par vous-même.</span><span class="sxs-lookup"><span data-stu-id="9ec95-191">Experiment with these yourself.</span></span> <span data-ttu-id="9ec95-192">Réalisez les essais suivants :</span><span class="sxs-lookup"><span data-stu-id="9ec95-192">Try each of the following:</span></span>

- <span data-ttu-id="9ec95-193">Modifiez l’initialiseur pour définir le démarrage à une valeur différente.</span><span class="sxs-lookup"><span data-stu-id="9ec95-193">Change the initializer to start at a different value.</span></span>
- <span data-ttu-id="9ec95-194">Modifiez la condition pour définir l’arrêt à une valeur différente.</span><span class="sxs-lookup"><span data-stu-id="9ec95-194">Change the condition to stop at a different value.</span></span>

<span data-ttu-id="9ec95-195">Une fois terminé, vous allez vous-même écrire des codes pour mettre en pratique ce que vous avez appris.</span><span class="sxs-lookup"><span data-stu-id="9ec95-195">When you're done, let's move on to write some code yourself to use what you've learned.</span></span>

## <a name="combine-branches-and-loops"></a><span data-ttu-id="9ec95-196">Combiner des branches et des boucles</span><span class="sxs-lookup"><span data-stu-id="9ec95-196">Combine branches and loops</span></span>

<span data-ttu-id="9ec95-197">Maintenant que vous avez vu l’instruction `if` et la création de boucles en langage C#, vérifiez si vous pouvez écrire un code C# pour obtenir la somme de tous les entiers de 1 à 20 divisibles par 3.</span><span class="sxs-lookup"><span data-stu-id="9ec95-197">Now that you've seen the `if` statement and the looping constructs in the C# language, see if you can write C# code to find the sum of all integers 1 through 20 that are divisible by 3.</span></span>  <span data-ttu-id="9ec95-198">Voici quelques conseils :</span><span class="sxs-lookup"><span data-stu-id="9ec95-198">Here are a few hints:</span></span>

- <span data-ttu-id="9ec95-199">L’opérateur `%` vous donne le reste d’une opération de division.</span><span class="sxs-lookup"><span data-stu-id="9ec95-199">The `%` operator gives you the remainder of a division operation.</span></span>
- <span data-ttu-id="9ec95-200">L’instruction `if` vous donne la condition pour vérifier si un nombre doit être inclus dans la somme.</span><span class="sxs-lookup"><span data-stu-id="9ec95-200">The `if` statement gives you the condition to see if a number should be part of the sum.</span></span>
- <span data-ttu-id="9ec95-201">La boucle `for` peut vous aider à répéter une série d’étapes pour tous les nombres de 1 à 20.</span><span class="sxs-lookup"><span data-stu-id="9ec95-201">The `for` loop can help you repeat a series of steps for all the numbers 1 through 20.</span></span>

<span data-ttu-id="9ec95-202">Essayez par vous-même</span><span class="sxs-lookup"><span data-stu-id="9ec95-202">Try it yourself.</span></span> <span data-ttu-id="9ec95-203">et vérifiez le résultat.</span><span class="sxs-lookup"><span data-stu-id="9ec95-203">Then check how you did.</span></span> <span data-ttu-id="9ec95-204">Vous devriez obtenir 63 comme réponse.</span><span class="sxs-lookup"><span data-stu-id="9ec95-204">You should get 63 for an answer.</span></span> <span data-ttu-id="9ec95-205">Vous pouvez voir une réponse possible en [consultant le code terminé sur GitHub](https://github.com/dotnet/docs/tree/master/samples/csharp/branches-quickstart/Program.cs#L46-L54).</span><span class="sxs-lookup"><span data-stu-id="9ec95-205">You can see one possible answer by [viewing the completed code on GitHub](https://github.com/dotnet/docs/tree/master/samples/csharp/branches-quickstart/Program.cs#L46-L54).</span></span>

<span data-ttu-id="9ec95-206">Vous avez terminé le guide de démarrage rapide « Branches et boucles ».</span><span class="sxs-lookup"><span data-stu-id="9ec95-206">You've completed the "branches and loops" quick start.</span></span>

<span data-ttu-id="9ec95-207">Vous pouvez passer au démarrage rapide [Chaînes interpolées](interpolated-strings-local.md) dans votre propre environnement de développement.</span><span class="sxs-lookup"><span data-stu-id="9ec95-207">You can continue with the [Interpolated strings](interpolated-strings-local.md) quick start in your own development environment.</span></span>

<span data-ttu-id="9ec95-208">Pour en savoir plus sur ces concepts, consultez les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="9ec95-208">You can learn more about these concepts in these topics:</span></span>

<span data-ttu-id="9ec95-209">[Instruction if et else](../language-reference/keywords/if-else.md) </span><span class="sxs-lookup"><span data-stu-id="9ec95-209">[If and else statement](../language-reference/keywords/if-else.md) </span></span>  
<span data-ttu-id="9ec95-210">[Instruction while](../language-reference/keywords/while.md) </span><span class="sxs-lookup"><span data-stu-id="9ec95-210">[While statement](../language-reference/keywords/while.md) </span></span>  
<span data-ttu-id="9ec95-211">[Instruction do](../language-reference/keywords/do.md) </span><span class="sxs-lookup"><span data-stu-id="9ec95-211">[Do statement](../language-reference/keywords/do.md) </span></span>  
[<span data-ttu-id="9ec95-212">Instruction for</span><span class="sxs-lookup"><span data-stu-id="9ec95-212">For statement</span></span>](../language-reference/keywords/for.md)   
