---
title: Application console
description: "Ce didacticiel vous présente un certain nombre de fonctionnalités dans .NET Core et le langage C#."
keywords: .NET, .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 883cd93d-50ce-4144-b7c9-2df28d9c11a0
ms.translationtype: Human Translation
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 360e93af03e00547116d1af1816c2b9b29524881
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---

# <a name="console-application"></a><span data-ttu-id="8e8f7-104">Application console</span><span class="sxs-lookup"><span data-stu-id="8e8f7-104">Console Application</span></span>

## <a name="introduction"></a><span data-ttu-id="8e8f7-105">Introduction</span><span class="sxs-lookup"><span data-stu-id="8e8f7-105">Introduction</span></span>
<span data-ttu-id="8e8f7-106">Ce didacticiel vous présente un certain nombre de fonctionnalités de .NET Core et du langage C#.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-106">This tutorial teaches you a number of features in .NET Core and the C# language.</span></span> <span data-ttu-id="8e8f7-107">Vous apprendrez à :</span><span class="sxs-lookup"><span data-stu-id="8e8f7-107">You’ll learn:</span></span>
*   <span data-ttu-id="8e8f7-108">Principes de base de l’interface de ligne de commande (CLI) de .NET Core</span><span class="sxs-lookup"><span data-stu-id="8e8f7-108">The basics of the .NET Core Command Line Interface (CLI)</span></span>
*   <span data-ttu-id="8e8f7-109">La structure d’une application de console C#</span><span class="sxs-lookup"><span data-stu-id="8e8f7-109">The structure of a C# Console Application</span></span>
*   <span data-ttu-id="8e8f7-110">E/S console</span><span class="sxs-lookup"><span data-stu-id="8e8f7-110">Console I/O</span></span>
*   <span data-ttu-id="8e8f7-111">Les principes fondamentaux de l’API d’E/S de fichier dans .NET Core</span><span class="sxs-lookup"><span data-stu-id="8e8f7-111">The basics of File I/O APIs in .NET Core</span></span>
*   <span data-ttu-id="8e8f7-112">Les principes fondamentaux du modèle de programmation asynchrone des tâches dans .NET Core</span><span class="sxs-lookup"><span data-stu-id="8e8f7-112">The basics of the Task Asynchronous Programming Model in .NET Core</span></span>

<span data-ttu-id="8e8f7-113">Vous allez générer une application qui lit un fichier texte et retourne le contenu du fichier texte dans la console.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-113">You’ll build an application that reads a text file, and echoes the contents of that text file to the console.</span></span> <span data-ttu-id="8e8f7-114">La sortie sur la console se fera à un rythme permettant de la lire à haute voix.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-114">The output to the console will be paced to match reading it aloud.</span></span> <span data-ttu-id="8e8f7-115">Vous pouvez accélérer ou ralentir la vitesse en appuyant sur les touches '<’ ou ’>'.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-115">You can speed up or slow down the pace by pressing the ‘<’ or ‘>’ keys.</span></span>

<span data-ttu-id="8e8f7-116">Il existe un grand nombre de fonctionnalités dans ce didacticiel.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-116">There are a lot of features in this tutorial.</span></span> <span data-ttu-id="8e8f7-117">Nous allons les construire une par une.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-117">Let’s build them one by one.</span></span> 
## <a name="prerequisites"></a><span data-ttu-id="8e8f7-118">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="8e8f7-118">Prerequisites</span></span>
<span data-ttu-id="8e8f7-119">Vous devez configurer votre ordinateur pour exécuter .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-119">You’ll need to setup your machine to run .NET core.</span></span> <span data-ttu-id="8e8f7-120">Vous trouverez les instructions d’installation sur la page de [.NET Core](https://www.microsoft.com/net/core).</span><span class="sxs-lookup"><span data-stu-id="8e8f7-120">You can find the installation instructions on the [.NET Core](https://www.microsoft.com/net/core) page.</span></span> <span data-ttu-id="8e8f7-121">Vous pouvez exécuter cette application sur Windows, Linux, Mac OS ou dans un conteneur Docker.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-121">You can run this application on Windows, Linux, macOS or in a Docker container.</span></span> <span data-ttu-id="8e8f7-122">Vous devez installer l’éditeur de code de votre choix.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-122">You’ll need to install your favorite code editor.</span></span> 
## <a name="create-the-application"></a><span data-ttu-id="8e8f7-123">Création de l’application</span><span class="sxs-lookup"><span data-stu-id="8e8f7-123">Create the Application</span></span>
<span data-ttu-id="8e8f7-124">La première étape consiste à créer une nouvelle application.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-124">The first step is to create a new application.</span></span> <span data-ttu-id="8e8f7-125">Ouvrez une invite de commandes et créez un nouveau répertoire pour votre application.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-125">Open a command prompt and create a new directory for your application.</span></span> <span data-ttu-id="8e8f7-126">Réglez-le comme répertoire actuel.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-126">Make that the current directory.</span></span> <span data-ttu-id="8e8f7-127">Saisissez la commande `dotnet new console` à l’invite.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-127">Type the command `dotnet new console` at the command prompt.</span></span> <span data-ttu-id="8e8f7-128">Elle crée les fichiers de démarrage d’une application « Hello World » de base.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-128">This creates the starter files for a basic "Hello World" application.</span></span>

<span data-ttu-id="8e8f7-129">Avant d’apporter des modifications, examinons les étapes nécessaires pour exécuter l’application simple Hello World.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-129">Before you start making modifications, let’s go through the steps to run the simple Hello World application.</span></span> <span data-ttu-id="8e8f7-130">Après avoir créé l’application, saisissez `dotnet restore` à l’invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-130">After creating the application, type `dotnet restore` at the command prompt.</span></span> <span data-ttu-id="8e8f7-131">Cette commande exécute le processus de restauration de package NuGet.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-131">This command runs the NuGet package restore process.</span></span> <span data-ttu-id="8e8f7-132">NuGet est un gestionnaire de packages .NET.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-132">NuGet is a .NET package manager.</span></span> <span data-ttu-id="8e8f7-133">Cette commande télécharge les dépendances manquantes pour votre projet.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-133">This command downloads any of the missing dependencies for your project.</span></span> <span data-ttu-id="8e8f7-134">Comme il s’agit d’un nouveau projet, aucune des dépendances n’est en place, donc la première exécution téléchargera le framework .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-134">As this is a new project, none of the dependencies are in place, so the first run will download the .NET Core framework.</span></span> <span data-ttu-id="8e8f7-135">Après cette étape initiale, vous devrez exécuter `dotnet restore` lorsque vous ajoutez de nouveaux packages dépendants ou mettez à jour les versions de vos dépendances.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-135">After this initial step, you will only need to run `dotnet restore` when you add new dependent packages, or update the versions of any of your dependencies.</span></span> <span data-ttu-id="8e8f7-136">Ce processus crée également le fichier de verrouillage du projet (project.lock.json) dans votre répertoire de projet.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-136">This process also creates the project lock file (project.lock.json) in your project directory.</span></span> <span data-ttu-id="8e8f7-137">Ce fichier permet de gérer les dépendances du projet.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-137">This file helps to manage the project dependencies.</span></span> <span data-ttu-id="8e8f7-138">Il contient l’emplacement local de toutes les dépendances du projet.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-138">It contains the local location of all the project dependencies.</span></span> <span data-ttu-id="8e8f7-139">Vous n’avez pas besoin de placer le fichier dans le contrôle de code source, car Il est généré lorsque vous exécutez `dotnet restore`.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-139">You do not need to put the file in source control; it will be generated when you run `dotnet restore`.</span></span> 

<span data-ttu-id="8e8f7-140">Après la restauration des packages, vous exécutez `dotnet build`.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-140">After restoring packages, you run `dotnet build`.</span></span> <span data-ttu-id="8e8f7-141">Cela exécute le moteur de génération et crée l’exécutable de votre application.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-141">This executes the build engine and creates your application executable.</span></span> <span data-ttu-id="8e8f7-142">Enfin, vous exécutez `dotnet run` pour lancer votre application.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-142">Finally, you execute `dotnet run` to run your application.</span></span>  

<span data-ttu-id="8e8f7-143">Le code d’application Hello World simple se trouve intégralement dans le fichier Program.cs.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-143">The simple Hello World application code is all in Program.cs.</span></span> <span data-ttu-id="8e8f7-144">Ouvrez ce fichier avec votre éditeur de texte préféré.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-144">Open that file with your favorite text editor.</span></span> <span data-ttu-id="8e8f7-145">Nous allons apporter nos premières modifications.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-145">We’re about to make our first changes.</span></span>
<span data-ttu-id="8e8f7-146">En haut du fichier, remarquez l’instruction using :</span><span class="sxs-lookup"><span data-stu-id="8e8f7-146">At the top of the file, see a using statement:</span></span>

```csharp
using System;
```

<span data-ttu-id="8e8f7-147">Cette instruction indique au compilateur que tous les types de l’espace de noms `System` sont dans la portée.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-147">This statement tells the compiler that any types from the `System` namespace are in scope.</span></span> <span data-ttu-id="8e8f7-148">Comme d’autres langages orientés objet que vous avez peut-être utilisés, C# utilise des espaces de noms pour organiser les types.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-148">Like other Object Oriented languages you may have used, C# uses namespaces to organize types.</span></span> <span data-ttu-id="8e8f7-149">Ce programme hello world ne fait pas exception.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-149">This hello world program is no different.</span></span> <span data-ttu-id="8e8f7-150">Vous pouvez voir que le programme est placé dans l’espace de noms `ConsoleApplication`.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-150">You can see that the program is enclosed in the `ConsoleApplication` namespace.</span></span> <span data-ttu-id="8e8f7-151">Ce qui n’est pas un nom très descriptif, donc modifiez-le en `TeleprompterConsole` :</span><span class="sxs-lookup"><span data-stu-id="8e8f7-151">That’s not a very descriptive name, so change it to `TeleprompterConsole`:</span></span>

```csharp
namespace TeleprompterConsole
```

## <a name="reading-and-echoing-the-file"></a><span data-ttu-id="8e8f7-152">Lecture et affichage du fichier</span><span class="sxs-lookup"><span data-stu-id="8e8f7-152">Reading and Echoing the File</span></span>
<span data-ttu-id="8e8f7-153">La première fonctionnalité à ajouter est la capacité à lire un fichier texte et à afficher tout le texte dans la console.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-153">The first feature to add is the ability to read a text file and display all that text to the console.</span></span> <span data-ttu-id="8e8f7-154">Tout d’abord, nous allons ajouter un fichier texte.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-154">First, let’s add a text file.</span></span> <span data-ttu-id="8e8f7-155">Copiez le fichier [sampleQuotes.txt](https://raw.githubusercontent.com/dotnet/docs/master/samples/csharp/getting-started/console-teleprompter/sampleQuotes.txt) à partir du dépôt GitHub pour cet [exemple](https://github.com/dotnet/docs/tree/master/samples/csharp/getting-started/console-teleprompter) dans votre répertoire de projet.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-155">Copy the [sampleQuotes.txt](https://raw.githubusercontent.com/dotnet/docs/master/samples/csharp/getting-started/console-teleprompter/sampleQuotes.txt) file from the GitHub repository for this [sample](https://github.com/dotnet/docs/tree/master/samples/csharp/getting-started/console-teleprompter) into your project directory.</span></span> <span data-ttu-id="8e8f7-156">Il servira de script pour votre application.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-156">This will serve as the script for your application.</span></span> <span data-ttu-id="8e8f7-157">Si vous voulez des informations sur la façon de télécharger l’exemple d’application de cette rubrique, consultez les instructions de la rubrique [Exemples et didacticiels](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="8e8f7-157">If you would like information on how to download the sample app for this topic, see the instructions in the [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples) topic.</span></span>

<span data-ttu-id="8e8f7-158">Ensuite, ajoutez la méthode suivante dans votre classe Program (juste en dessous de la méthode `Main`) :</span><span class="sxs-lookup"><span data-stu-id="8e8f7-158">Next, add the following method in your Program class (right below the `Main` method):</span></span>

```csharp
static IEnumerable<string> ReadFrom(string file)
{
    string line;
    using (var reader = File.OpenText(file))
    {
        while ((line = reader.ReadLine()) != null)
        {
            yield return line;
        }
    }
}
```

<span data-ttu-id="8e8f7-159">Cette méthode utilise les types de deux nouveaux espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-159">This method uses types from two new namespaces.</span></span> <span data-ttu-id="8e8f7-160">Pour que cela compile, vous devez ajouter les deux lignes suivantes au début du fichier :</span><span class="sxs-lookup"><span data-stu-id="8e8f7-160">For this to compile you’ll need to add the following two lines to the top of the file:</span></span>

```csharp
using System.Collections.Generic;
using System.IO;
```

<span data-ttu-id="8e8f7-161">L'interface `IEnumerable<T>` est définie dans l’espace de noms `System.Collections.Generic`.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-161">The `IEnumerable<T>` interface is defined in the `System.Collections.Generic` namespace.</span></span> <span data-ttu-id="8e8f7-162">La classe @System.IO.File est définie dans l’espace de noms `System.IO`.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-162">The @System.IO.File class is defined in the `System.IO` namespace.</span></span>

<span data-ttu-id="8e8f7-163">Cette méthode est un type spécial de méthode C# appelé *méthode d’énumérateur*.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-163">This method is a special type of C# method called an *Enumerator method*.</span></span> <span data-ttu-id="8e8f7-164">Les méthodes d’énumérateur retournent des séquences qui sont évaluées de manière tardive.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-164">Enumerator methods return sequences that are evaluated lazily.</span></span> <span data-ttu-id="8e8f7-165">Cela signifie que chaque élément de la séquence est généré lorsque cela est demandé par le code utilisant la séquence.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-165">That means each item in the sequence is generated as it is requested by the code consuming the sequence.</span></span> <span data-ttu-id="8e8f7-166">Les méthodes d’énumérateur sont des méthodes qui contiennent une ou plusieurs instructions `yield return`.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-166">Enumerator methods are methods that contain one or more `yield return` statements.</span></span> <span data-ttu-id="8e8f7-167">L’objet retourné par la méthode `ReadFrom` contient le code pour générer chaque élément dans la séquence.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-167">The object returned by the `ReadFrom` method contains the code to generate each item in the sequence.</span></span> <span data-ttu-id="8e8f7-168">Dans cet exemple, cela implique la lecture de la ligne de texte suivante à partir du fichier source et le renvoi de cette chaîne.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-168">In this example, that involves reading the next line of text from the source file, and returning that string.</span></span> <span data-ttu-id="8e8f7-169">Chaque fois que le code appelant demande l’élément suivant de la séquence, le code lit la ligne suivante du texte à partir du fichier et la renvoie.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-169">Each time the calling code requests the next item from the sequence, the code reads the next line of text from the file and returns it.</span></span> <span data-ttu-id="8e8f7-170">Lorsque le fichier a été entièrement lu, la séquence indique qu’il n’y a pas d’autres éléments.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-170">When the file has been completely read, the sequence indicates that there are no more items.</span></span>

<span data-ttu-id="8e8f7-171">Il existe deux autres éléments de syntaxe de C# qui peuvent être nouveaux pour vous.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-171">There are two other C# syntax elements that may be new to you.</span></span> <span data-ttu-id="8e8f7-172">L’instruction `using` dans cette méthode gère le nettoyage des ressources.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-172">The `using` statement in this method manages resource cleanup.</span></span> <span data-ttu-id="8e8f7-173">La variable initialisée dans l’instruction `using` (`reader`, dans cet exemple) doit implémenter l’interface `IDisposable`.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-173">The variable that is initialized in the `using` statement (`reader`, in this example) must implement the `IDisposable` interface.</span></span> <span data-ttu-id="8e8f7-174">L’interface @System.IDisposable définit une méthode unique, `Dispose`, qui doit être appelée lorsque les ressources doivent être libérées.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-174">The @System.IDisposable interface defines a single method, `Dispose`, that should be called when the resource should be released.</span></span> <span data-ttu-id="8e8f7-175">Le compilateur génère l’appel lorsque l’exécution atteint l’accolade fermante de l’instruction `using`.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-175">The compiler generates that call when execution reaches the closing brace of the `using` statement.</span></span> <span data-ttu-id="8e8f7-176">Le code généré par le compilateur garantit que la ressource est libérée même si une exception est levée à partir du code dans le bloc défini par l’instruction using.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-176">The compiler-generated code ensures that the resource is released even if an exception is thrown from the code in the block defined by the using statement.</span></span>

<span data-ttu-id="8e8f7-177">La variable `reader` est définie à l’aide du mot-clé `var`.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-177">The `reader` variable is defined using the `var` keyword.</span></span> <span data-ttu-id="8e8f7-178">`var` définit une *variable locale implicitement typée*.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-178">`var` defines an *implicitly typed local variable*.</span></span> <span data-ttu-id="8e8f7-179">Cela signifie que le type de la variable est déterminé par le type au moment de la compilation de l’objet assigné à la variable.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-179">That means the type of the variable is determined by the compile time type of the object assigned to the variable.</span></span> <span data-ttu-id="8e8f7-180">Ici, c’est la valeur de retour de @System.IO.File.OpenText, qui est un objet @System.IO.StreamReader.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-180">Here, that is the return value from @System.IO.File.OpenText, which is a @System.IO.StreamReader object.</span></span>
 
<span data-ttu-id="8e8f7-181">À présent, nous allons remplir le code pour lire le fichier dans la méthode `Main` :</span><span class="sxs-lookup"><span data-stu-id="8e8f7-181">Now, let’s fill in the code to read the file in the `Main` method:</span></span> 

```csharp
var lines = ReadFrom("sampleQuotes.txt");
foreach (var line in lines)
{
    Console.WriteLine(line); 
}
```

<span data-ttu-id="8e8f7-182">Exécutez le programme (à l’aide de `dotnet run`, chaque ligne est imprimée sur la console).</span><span class="sxs-lookup"><span data-stu-id="8e8f7-182">Run the program (using `dotnet run` and you can see every line printed out to the console).</span></span>  

## <a name="adding-delays-and-formatting-output"></a><span data-ttu-id="8e8f7-183">Ajout de délais et de mise en forme à la sortie</span><span class="sxs-lookup"><span data-stu-id="8e8f7-183">Adding Delays and Formatting output</span></span>
<span data-ttu-id="8e8f7-184">Ce que vous avez s’affiche beaucoup trop rapidement pour le lire à haute voix.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-184">What you have is being displayed far too fast to read aloud.</span></span> <span data-ttu-id="8e8f7-185">Vous devez maintenant ajouter des délais à la sortie.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-185">Now you need to add the delays in the output.</span></span> <span data-ttu-id="8e8f7-186">Lorsque vous commencez, vous créez une partie du code principal qui permet le traitement asynchrone.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-186">As you start, you’ll be building some of the core code that enables asynchronous processing.</span></span> <span data-ttu-id="8e8f7-187">Toutefois, ces premières étapes suivront quelques anti-modèles.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-187">However, these first steps will follow a few anti-patterns.</span></span> <span data-ttu-id="8e8f7-188">Les anti-modèles sont signalés dans les commentaires lorsque vous ajoutez le code, et le code sera actualisé ultérieurement.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-188">The anti-patterns are pointed out in comments as you add the code, and the code will be updated in later steps.</span></span>

<span data-ttu-id="8e8f7-189">Il existe deux étapes dans cette section.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-189">There are two steps to this section.</span></span> <span data-ttu-id="8e8f7-190">Tout d’abord, vous allez mettre à jour la méthode d’itérateur pour retourner des mots uniques au lieu de lignes entières.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-190">First, you’ll update the iterator method to return single words instead of entire lines.</span></span> <span data-ttu-id="8e8f7-191">Vous le faites avec ces modifications.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-191">That’s done with these modifications.</span></span> <span data-ttu-id="8e8f7-192">Remplacez l’instruction `yield return line;` par le code suivant :</span><span class="sxs-lookup"><span data-stu-id="8e8f7-192">Replace the `yield return line;` statement with the following code:</span></span>

```csharp
var words = line.Split(' ');
foreach (var word in words)
{
    yield return word + " ";
}
yield return Environment.NewLine;
```

<span data-ttu-id="8e8f7-193">Ensuite, vous devez modifier la façon dont vous consommez les lignes du fichier, et ajoutez un délai après chaque mot.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-193">Next, you need to modify how you consume the lines of the file, and add a delay after writing each word.</span></span> <span data-ttu-id="8e8f7-194">Remplacez l’instruction `Console.WriteLine(line)` dans la méthode `Main` avec le bloc suivant :</span><span class="sxs-lookup"><span data-stu-id="8e8f7-194">Replace the `Console.WriteLine(line)` statement in the `Main` method with the following block:</span></span>

```csharp
Console.Write(line);
if (!string.IsNullOrWhiteSpace(line))
{
    var pause = Task.Delay(200);
    // Synchronously waiting on a task is an
    // anti-pattern. This will get fixed in later
    // steps.
    pause.Wait();
}
```

<span data-ttu-id="8e8f7-195">La classe `Task` se trouve dans l’espace de noms `System.Threading.Tasks`, vous devez donc ajouter cette instruction `using` au début du fichier :</span><span class="sxs-lookup"><span data-stu-id="8e8f7-195">The `Task` class is in the `System.Threading.Tasks` namespace, so you need to add that `using` statement at the top of file:</span></span>

```csharp
using System.Threading.Tasks;
```

<span data-ttu-id="8e8f7-196">Exécutez l’exemple et vérifiez le résultat.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-196">Run the sample, and check the output.</span></span> <span data-ttu-id="8e8f7-197">À présent, chaque mot unique est affiché séparément, suivi d’un délai de 200 ms.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-197">Now, each single word is printed, followed by a 200 ms delay.</span></span> <span data-ttu-id="8e8f7-198">Toutefois, la sortie affichée présente certains problèmes, car le fichier texte source possède plusieurs lignes qui ont plus de 80 caractères sans saut de ligne.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-198">However, the displayed output shows some issues because the source text file has several lines that have more than 80 characters without a line break.</span></span> <span data-ttu-id="8e8f7-199">Ce qui peut être difficile à lire lors du défilement.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-199">That can be hard to read while it's scrolling by.</span></span> <span data-ttu-id="8e8f7-200">Ce problème est facile à résoudre.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-200">That’s easy to fix.</span></span> <span data-ttu-id="8e8f7-201">Vous allez simplement effectuer le suivi de la longueur de chaque ligne et générer une nouvelle ligne chaque fois que la longueur de ligne atteint un certain seuil.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-201">You’ll just keep track of the length of each line, and generate a new line whenever the line length reaches a certain threshold.</span></span> <span data-ttu-id="8e8f7-202">Déclarez une variable locale après la déclaration de `words` qui contient la longueur de ligne :</span><span class="sxs-lookup"><span data-stu-id="8e8f7-202">Declare a local variable after the declaration of `words` that holds the line length:</span></span>

```csharp
var lineLength = 0;
```
 
<span data-ttu-id="8e8f7-203">Ensuite, ajoutez le code suivant après l’instruction `yield return word + " ";` (avant l’accolade fermante) :</span><span class="sxs-lookup"><span data-stu-id="8e8f7-203">Then, add the following code after the `yield return word + " ";` statement (before the closing brace):</span></span>

```csharp
lineLength += word.Length + 1;
if (lineLength > 70)
{
    yield return Environment.NewLine;
    lineLength = 0;
}
```
 
<span data-ttu-id="8e8f7-204">Exécutez l’exemple et vous serez en mesure de lire à haute voix au rythme préconfiguré.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-204">Run the sample, and you’ll be able to read aloud at its pre-configured pace.</span></span>

## <a name="async-tasks"></a><span data-ttu-id="8e8f7-205">Tâches asynchrones</span><span class="sxs-lookup"><span data-stu-id="8e8f7-205">Async Tasks</span></span>
<span data-ttu-id="8e8f7-206">Dans cette étape, vous allez ajouter le code pour écrire la sortie de façon asynchrone dans une tâche, lorsque vous exécutez également une autre tâche pour lire d’entrée de l’utilisateur s’il souhaite accélérer ou ralentir l’affichage du texte.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-206">In this final step, you’ll add the code to write the output asynchronously in one task, while also running another task to read input from the user if they want to speed up or slow down the text display.</span></span> <span data-ttu-id="8e8f7-207">Cela représente plusieurs étapes et à la fin, vous aurez toutes les mises à jour dont vous avez besoin.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-207">This has a few steps in it and by the end, you’ll have all the updates that you need.</span></span>
<span data-ttu-id="8e8f7-208">La première étape consiste à créer une méthode de retour @System.Threading.Tasks.Task asynchrone qui représente le code que vous avez créé jusqu'à présent pour lire et afficher le fichier.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-208">The first step is to create an asynchronous @System.Threading.Tasks.Task returning method that represents the code you’ve created so far to read and display the file.</span></span>

<span data-ttu-id="8e8f7-209">Ajoutez cette méthode à votre classe `Program` (elle est extraite du corps de votre méthode `Main`) :</span><span class="sxs-lookup"><span data-stu-id="8e8f7-209">Add this method to your `Program` class (it’s taken from the body of your `Main` method):</span></span>

```csharp
private static async Task ShowTeleprompter()
{
    var words = ReadFrom("sampleQuotes.txt");
    foreach (var line in words)
    {
        Console.Write(line);
        if (!string.IsNullOrWhiteSpace(line))
        {
            await Task.Delay(200);
        }
    }
}
```

<span data-ttu-id="8e8f7-210">Vous remarquerez deux modifications.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-210">You’ll notice two changes.</span></span> <span data-ttu-id="8e8f7-211">Tout d’abord, dans le corps de la méthode, au lieu d’appeler @System.Threading.Tasks.Task.Wait pour attendre de manière synchrone qu’une tâche se termine, cette version utilise le mot-clé `await`.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-211">First, in the body of the method, instead of calling @System.Threading.Tasks.Task.Wait to synchronously wait for a task to finish, this version uses the `await` keyword.</span></span> <span data-ttu-id="8e8f7-212">Pour ce faire, vous devez ajouter le modificateur `async` pour la signature de méthode.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-212">In order to do that, you need to add the `async` modifier to the method signature.</span></span> <span data-ttu-id="8e8f7-213">Cette méthode renvoie une `Task`.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-213">This method returns a `Task`.</span></span> <span data-ttu-id="8e8f7-214">Notez qu’il n’y a aucune instruction de retour renvoyant un objet `Task`.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-214">Notice that there are no return statements that return a `Task` object.</span></span> <span data-ttu-id="8e8f7-215">Au lieu de cela, cet objet `Task` est créé par le code que le compilateur génère lorsque vous utilisez l’opérateur `await`.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-215">Instead, that `Task` object is created by code the compiler generates when you use the `await` operator.</span></span> <span data-ttu-id="8e8f7-216">Vous pouvez imaginer que cette méthode renvoie une valeur lorsqu’elle atteint un `await`.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-216">You can imagine that this method returns when it reaches an `await`.</span></span> <span data-ttu-id="8e8f7-217">La `Task` renvoyée indique que la tâche n’a pas été effectuée.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-217">The returned `Task` indicates that the work has not completed.</span></span>
<span data-ttu-id="8e8f7-218">La méthode reprend lorsque la tâche attendue se termine.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-218">The method resumes when the awaited task completes.</span></span> <span data-ttu-id="8e8f7-219">Lorsqu’elle a terminé son exécution, la `Task` renvoyée indique qu’elle est terminée.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-219">When it has executed to completion, the returned `Task` indicates that it is complete.</span></span>
<span data-ttu-id="8e8f7-220">Le code appelant peut surveiller cette `Task` renvoyée pour déterminer si elle est terminée.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-220">Calling code can monitor that returned `Task` to determine when it has completed.</span></span>

<span data-ttu-id="8e8f7-221">Vous pouvez appeler cette nouvelle méthode dans votre méthode `Main` :</span><span class="sxs-lookup"><span data-stu-id="8e8f7-221">You can call this new method in your `Main` method:</span></span>

```csharp
ShowTeleprompter().Wait();
```

<span data-ttu-id="8e8f7-222">Ici, dans `Main`, le code attend de façon synchrone.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-222">Here, in `Main`, the code does synchronously wait.</span></span> <span data-ttu-id="8e8f7-223">Vous devez utiliser l’opérateur `await` au lieu d’attendre de manière synchrone lorsque cela est possible.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-223">You should use the `await` operator instead of synchronously waiting whenever possible.</span></span> <span data-ttu-id="8e8f7-224">Mais, dans une méthode `Main` d’application de console, vous ne pouvez pas utiliser l’opérateur `await`.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-224">But, in a console application’s `Main` method, you cannot use the `await` operator.</span></span> <span data-ttu-id="8e8f7-225">Cela entraînerait la fermeture de l’application avant la fin de toutes les tâches.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-225">That would result in the application exiting before all tasks have completed.</span></span>

<span data-ttu-id="8e8f7-226">Ensuite, vous devez écrire la seconde méthode asynchrone pour lire à partir de la console et chercher les touches '<’ et ’>'.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-226">Next, you need to write the second asynchronous method to read from the Console and watch for the ‘<’ and ‘>’ keys.</span></span> <span data-ttu-id="8e8f7-227">Voici la méthode que vous ajoutez pour cette tâche :</span><span class="sxs-lookup"><span data-stu-id="8e8f7-227">Here’s the method you add for that task:</span></span>

```csharp
private static async Task GetInput()
{
    var delay = 200;
    Action work = () =>
    {
        do {
            var key = Console.ReadKey(true);
            if (key.KeyChar == '>')
            {
                delay -= 10;
            }
            else if (key.KeyChar == '<')
            {
                delay += 10;
            }
        } while (true);
    };
    await Task.Run(work);
}
```

<span data-ttu-id="8e8f7-228">Cela crée une expression lambda pour représenter un délégué @System.Action qui lit une touche de la console et modifie une variable locale représentant le délai lorsque l’utilisateur appuie sur les touches '<’ ou ’>'.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-228">This creates a lambda expression to represent an @System.Action delegate that reads a key from the Console and modifies a local variable representing the delay when the user presses the ‘<’ or ‘>’ keys.</span></span> <span data-ttu-id="8e8f7-229">Cette méthode utilise @System.Console.ReadKey pour bloquer et attendre que l’utilisateur appuie sur une touche.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-229">This method uses @System.Console.ReadKey to block and wait for the user to press a key.</span></span>

<span data-ttu-id="8e8f7-230">Pour terminer cette fonctionnalité, vous devez créer une nouvelle méthode de retour `async Task` qui démarre ces deux tâches (`GetInput` et `ShowTeleprompter`) et gère également les données partagées entre ces deux tâches.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-230">To finish this feature, you need to create a new `async Task` returning method that starts both of these tasks (`GetInput` and `ShowTeleprompter`), and also manages the shared data between these two tasks.</span></span>
 
<span data-ttu-id="8e8f7-231">Il est temps de créer une classe qui peut gérer les données partagées entre ces deux tâches.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-231">It’s time to create a class that can handle the shared data between these two tasks.</span></span> <span data-ttu-id="8e8f7-232">Cette classe contient deux propriétés publiques : le délai et un indicateur pour indiquer que le fichier a été entièrement lu :</span><span class="sxs-lookup"><span data-stu-id="8e8f7-232">This class contains two public properties: the delay, and a flag to indicate that the file has been completely read:</span></span>

```csharp
namespace TeleprompterConsole
{
    internal class TelePrompterConfig
    {
        private object lockHandle = new object();
        public int DelayInMilliseconds { get; private set; } = 200;

        public void UpdateDelay(int increment) // negative to speed up
        {
            var newDelay = Min(DelayInMilliseconds + increment, 1000);
            newDelay = Max(newDelay, 20);
            lock (lockHandle)
            {
                DelayInMilliseconds = newDelay;
            }
        }
    }
}
```

<span data-ttu-id="8e8f7-233">Placez cette classe dans un nouveau fichier et ajoutez-la à l’espace de noms `TeleprompterConsole`, comme indiqué ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-233">Put that class in a new file, and enclose that class in the `TeleprompterConsole` namespace as shown above.</span></span> <span data-ttu-id="8e8f7-234">Vous devrez également ajouter une instruction `using static` pour pouvoir référencer les méthodes `Min` et `Max` sans les noms de la classe ou de l’espace de noms qui les contient.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-234">You’ll also need to add a `using static` statement so that you can reference the `Min` and `Max` method without the enclosing class or namespace names.</span></span> <span data-ttu-id="8e8f7-235">Une instruction `using static` importe les méthodes d’une classe.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-235">A `using static` statement imports the methods from one class.</span></span> <span data-ttu-id="8e8f7-236">Cela est en opposition avec les instructions `using` utilisées jusqu'à présent, et qui avaient importé toutes les classes à partir d’un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-236">This is in contrast with the `using` statements used up to this point that have imported all classes from a namespace.</span></span>

```csharp
using static System.Math;
```

<span data-ttu-id="8e8f7-237">L’autre fonctionnalité de langage qui est une nouveauté est l’instruction `lock`.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-237">The other language feature that’s new is the `lock` statement.</span></span> <span data-ttu-id="8e8f7-238">Cette instruction permet de garantir qu’un seul thread peut se trouver dans ce code à un moment donné.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-238">This statement ensures that only a single thread can be in that code at any given time.</span></span> <span data-ttu-id="8e8f7-239">Si un thread se trouve dans la section verrouillée, les autres threads doivent attendre que le premier thread quitte cette section.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-239">If one thread is in the locked section, other threads must wait for the first thread to exit that section.</span></span> <span data-ttu-id="8e8f7-240">L’instruction `lock` utilise un objet qui assure la protection de la section de verrou.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-240">The `lock` statement uses an object that guards the lock section.</span></span> <span data-ttu-id="8e8f7-241">Cette classe suit un idiome standard pour verrouiller un objet privé dans la classe.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-241">This class follows a standard idiom to lock a private object in the class.</span></span>

<span data-ttu-id="8e8f7-242">Ensuite, vous devez mettre à jour les méthodes `ShowTeleprompter` et `GetInput` pour utiliser le nouvel objet `config`.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-242">Next, you need to update the `ShowTeleprompter` and `GetInput` methods to use the new `config` object.</span></span> <span data-ttu-id="8e8f7-243">Écrivez une dernière `Task` renvoyant une méthode `async` pour démarrer les deux tâches et quitter lorsque la première tâche est terminée :</span><span class="sxs-lookup"><span data-stu-id="8e8f7-243">Write one final `Task` returning `async` method to start both tasks and exit when the first task finishes:</span></span>

```csharp
private static async Task RunTeleprompter()
{
    var config = new TelePrompterConfig();
    var displayTask = ShowTeleprompter(config);

    var speedTask = GetInput(config);
    await Task.WhenAny(displayTask, speedTask);
}
```

<span data-ttu-id="8e8f7-244">La nouvelle méthode ici est l’appel @System.Threading.Tasks.Task.WhenAny(System.Threading.Tasks.Task[]).</span><span class="sxs-lookup"><span data-stu-id="8e8f7-244">The one new method here is the @System.Threading.Tasks.Task.WhenAny(System.Threading.Tasks.Task[]) call.</span></span> <span data-ttu-id="8e8f7-245">Elle crée une `Task` qui se termine dès que les tâches de sa liste d’arguments se terminent.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-245">That creates a `Task` that finishes as soon as any of the tasks in its argument list completes.</span></span>

<span data-ttu-id="8e8f7-246">Ensuite, vous devez mettre à jour les méthodes `ShowTeleprompter` et `GetInput` pour utiliser l’objet `config` pour le délai :</span><span class="sxs-lookup"><span data-stu-id="8e8f7-246">Next, you need to update both the `ShowTeleprompter` and `GetInput` methods to use the `config` object for the delay:</span></span>

```csharp
private static async Task ShowTeleprompter(TelePrompterConfig config)
{
    var words = ReadFrom("sampleQuotes.txt");
    foreach (var line in words)
    {
        Console.Write(line);
        if (!string.IsNullOrWhiteSpace(line))
        {
            await Task.Delay(config.DelayInMilliseconds);
        }
    }
    config.SetDone();
}

private static async Task GetInput(TelePrompterConfig config)
{

    Action work = () =>
    {
        do {
            var key = Console.ReadKey(true);
            if (key.KeyChar == '>')
                config.UpdateDelay(-10);
            else if (key.KeyChar == '<')
                config.UpdateDelay(10);
        } while (!config.Done);
    };
    await Task.Run(work);
}
```

<span data-ttu-id="8e8f7-247">Cette nouvelle version de `ShowTeleprompter` appelle une nouvelle méthode dans la classe `TeleprompterConfig`.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-247">This new version of `ShowTeleprompter` calls a new method in the `TeleprompterConfig` class.</span></span> <span data-ttu-id="8e8f7-248">À présent, vous devez mettre à jour `Main` pour appeler `RunTeleprompter` au lieu de `ShowTeleprompter` :</span><span class="sxs-lookup"><span data-stu-id="8e8f7-248">Now, you need to update `Main` to call `RunTeleprompter` instead of `ShowTeleprompter`:</span></span>

```csharp
RunTeleprompter().Wait();
```

<span data-ttu-id="8e8f7-249">Pour terminer, vous devez ajouter la méthode `SetDone` et la propriété `Done` à la classe `TelePrompterConfig` :</span><span class="sxs-lookup"><span data-stu-id="8e8f7-249">To finish, you'll need to add the `SetDone` method, and the `Done` property to the `TelePrompterConfig` class:</span></span>

```csharp
public bool Done => done;

private bool done;

public void SetDone()
{
    done = true;    
}
```

## <a name="conclusion"></a><span data-ttu-id="8e8f7-250">Conclusion</span><span class="sxs-lookup"><span data-stu-id="8e8f7-250">Conclusion</span></span>
<span data-ttu-id="8e8f7-251">Ce didacticiel vous a montré certaines des fonctionnalités du langage C# et les bibliothèques .NET Core liées au travail dans les applications console.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-251">This tutorial showed you a number of the features around the C# language and the .NET Core libraries related to working in Console applications.</span></span>
<span data-ttu-id="8e8f7-252">Vous pouvez utiliser ces connaissances pour explorer davantage le langage ainsi que les classes présentées ici.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-252">You can build on this knowledge to explore more about the language, and the classes introduced here.</span></span> <span data-ttu-id="8e8f7-253">Vous avez vu les principes de base des E/S de fichiers et de console, l’utilisation bloquante et non bloquante du modèle de programmation asynchrone basé sur les tâches, une présentation du langage C# et de la façon dont les programmes C# sont organisés, et l’interface de ligne de commande et les outils de programmation .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8e8f7-253">You’ve seen the basics of File and Console I/O, blocking and non-blocking use of the Task based Asynchronous programming model, a tour of the C# language and how C# programs are organized and the .NET Core Command Line Interface and tools.</span></span>
 

