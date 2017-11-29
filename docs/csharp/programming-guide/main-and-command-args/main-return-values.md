---
title: Valeurs de retour de Main() (Guide de programmation C#)
ms.date: 08/02/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: Main method [C#], return values
ms.assetid: c2f5a1d8-1676-4bea-bc7e-44a97e72d5bc
caps.latest.revision: "20"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 9f317879a4941adfd3d125c7697226f8a510254c
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="main-return-values-c-programming-guide"></a><span data-ttu-id="c6604-102">Valeurs de retour de Main() (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="c6604-102">Main() return values (C# Programming Guide)</span></span>

<span data-ttu-id="c6604-103">La méthode `Main` peut retourner `void` :</span><span class="sxs-lookup"><span data-stu-id="c6604-103">The `Main` method can return `void`:</span></span>

[!code-csharp[csProgGuideMain#12](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/main-return-values_1.cs)]

<span data-ttu-id="c6604-104">Elle peut également retourner un `int` :</span><span class="sxs-lookup"><span data-stu-id="c6604-104">It can also return an `int`:</span></span>

[!code-csharp[csProgGuideMain#13](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/main-return-values_2.cs)]

<span data-ttu-id="c6604-105">Si la valeur de retour de `Main` n’est pas utilisée, retourner `void` permet d’avoir un code un peu plus simple.</span><span class="sxs-lookup"><span data-stu-id="c6604-105">If the return value from `Main` is not used, returning `void` allows for slightly simpler code.</span></span> <span data-ttu-id="c6604-106">Cependant, retourner un entier permet au programme de communiquer des informations d’état à d’autres programmes ou scripts qui appellent le fichier exécutable.</span><span class="sxs-lookup"><span data-stu-id="c6604-106">However, returning an integer enables the program to communicate status information to other programs or scripts that invoke the executable file.</span></span> <span data-ttu-id="c6604-107">La valeur de retour de `Main` est traitée comme le code de sortie du processus.</span><span class="sxs-lookup"><span data-stu-id="c6604-107">The return value from `Main` is treated as the exit code for the process.</span></span> <span data-ttu-id="c6604-108">L’exemple suivant montre comment accéder à la valeur de retour de `Main`.</span><span class="sxs-lookup"><span data-stu-id="c6604-108">The following example shows how the return value from `Main` can be accessed.</span></span>

## <a name="example"></a><span data-ttu-id="c6604-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="c6604-109">Example</span></span>

<span data-ttu-id="c6604-110">Cet exemple utilise les outils de ligne de commande [.NET Core](../../../core/index.md).</span><span class="sxs-lookup"><span data-stu-id="c6604-110">This example uses [.NET Core](../../../core/index.md) command line tools.</span></span> <span data-ttu-id="c6604-111">Si vous ne connaissez pas les outils de ligne de commande .NET Core, vous pouvez les découvrir dans cette [rubrique Bien démarrer](../../../core/tutorials/using-with-xplat-cli.md).</span><span class="sxs-lookup"><span data-stu-id="c6604-111">If you are unfamilar with .NET Core command line tools, you can learn about them in this [Get started topic](../../../core/tutorials/using-with-xplat-cli.md).</span></span>

<span data-ttu-id="c6604-112">Modifiez la méthode `Main` dans *program.cs* comme suit :</span><span class="sxs-lookup"><span data-stu-id="c6604-112">Modify the `Main` method in *program.cs* as follows:</span></span>

[!code-csharp[csProgGuideMain#14](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/main-return-values_3.cs)]

<span data-ttu-id="c6604-113">Quand un programme est exécuté dans Windows, toute valeur retournée par la fonction `Main` est stockée dans une variable d’environnement.</span><span class="sxs-lookup"><span data-stu-id="c6604-113">When a program is executed in Windows, any value returned from the `Main` function is stored in an environment variable.</span></span> <span data-ttu-id="c6604-114">Cette variable d’environnement peut être récupérée à l’aide de `ERRORLEVEL` dans un fichier de commandes ou de `$LastExitCode` dans PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c6604-114">This environment variable can be retrieved using `ERRORLEVEL` from a batch file, or `$LastExitCode` from powershell.</span></span>

<span data-ttu-id="c6604-115">Vous pouvez générer l’application à l’aide de la commande [dotnet CLI](../../../core/tools/dotnet.md) `dotnet build`.</span><span class="sxs-lookup"><span data-stu-id="c6604-115">You can build the application using the [dotnet CLI](../../../core/tools/dotnet.md) `dotnet build` command.</span></span>

<span data-ttu-id="c6604-116">Ensuite, créez un script PowerShell pour exécuter l’application et afficher le résultat.</span><span class="sxs-lookup"><span data-stu-id="c6604-116">Next, create a Powershell script to run the application and display the result.</span></span> <span data-ttu-id="c6604-117">Collez le code suivant dans un fichier texte et enregistrez-le sous `test.ps1` dans le dossier qui contient le projet.</span><span class="sxs-lookup"><span data-stu-id="c6604-117">Paste the following code into a text file and save it as `test.ps1` in the folder that contains the project.</span></span> <span data-ttu-id="c6604-118">Exécutez le script PowerShell en tapant `test.ps1` à l’invite de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c6604-118">Run the powershell script by typing `test.ps1` at the powershell prompt.</span></span>

<span data-ttu-id="c6604-119">Comme le code retourne zéro, le fichier de commandes indique la réussite.</span><span class="sxs-lookup"><span data-stu-id="c6604-119">Because the code returns zero, the batch file will report success.</span></span> <span data-ttu-id="c6604-120">Toutefois, si vous modifiez MainReturnValTest.cs pour qu’il retourne une valeur différente de zéro, puis que vous recompilez le programme, l’exécution suivante du script PowerShell indique un échec.</span><span class="sxs-lookup"><span data-stu-id="c6604-120">However, if you change MainReturnValTest.cs to return a non-zero value and then re-compile the program, subsequent execution of the powershell script will report failure.</span></span>

```powershell
dotnet run
if ($LastExitCode -eq 0) {
    Write-Host "Execution succeeded"
} else
{
    Write-Host "Execution Failed"
}
Write-Host "Return value = " $LastExitCode
```

## <a name="sample-output"></a><span data-ttu-id="c6604-121">Résultat de l'exemple</span><span class="sxs-lookup"><span data-stu-id="c6604-121">Sample output</span></span>

```txt
Execution succeeded
Return value = 0
```

## <a name="async-main-return-values"></a><span data-ttu-id="c6604-122">Valeurs de retour d’Async Main</span><span class="sxs-lookup"><span data-stu-id="c6604-122">Async Main return values</span></span>

<span data-ttu-id="c6604-123">Les valeurs de retour d’Async Main déplacent le code réutilisable nécessaire pour appeler les méthodes asynchrones dans `Main` vers le code généré par le compilateur.</span><span class="sxs-lookup"><span data-stu-id="c6604-123">Async Main return values move the boilerplate code necessary for calling asynchronous methods in `Main` to code generated by the compiler.</span></span> <span data-ttu-id="c6604-124">Avant, vous auriez dû écrire cette construction pour appeler du code asynchrone et vérifier que votre programme s’est exécuté jusqu’à la fin de l’opération asynchrone :</span><span class="sxs-lookup"><span data-stu-id="c6604-124">Previously, you would need to write this construct to call asynchronous code and ensure your program ran until the asynchronous operation completed:</span></span>

```csharp
public static void Main()
{
    AsyncConsoleWork().GetAwaiter().GetResult();
}

private static async Task<int> AsyncConsoleWork()
{
    // Main body here
    return 0;
}
```

<span data-ttu-id="c6604-125">Maintenant, vous pouvez la remplacer par :</span><span class="sxs-lookup"><span data-stu-id="c6604-125">Now, this can be replaced by:</span></span>

[!code-csharp[AsyncMain](../../../../samples/snippets/csharp/main-arguments/program.cs#AsyncMain)]

<span data-ttu-id="c6604-126">L’avantage de la nouvelle syntaxe est que le compilateur génère toujours un code correct.</span><span class="sxs-lookup"><span data-stu-id="c6604-126">The advantage of the new syntax is that the compiler always generates the correct code.</span></span>

## <a name="compiler-generated-code"></a><span data-ttu-id="c6604-127">Code généré par le compilateur</span><span class="sxs-lookup"><span data-stu-id="c6604-127">Compiler generated code</span></span>

<span data-ttu-id="c6604-128">Quand le point d’entrée de l’application retourne `Task` ou `Task<int>`, le compilateur génère un nouveau point d’entrée qui appelle la méthode de point d’entrée déclarée dans le code d’application.</span><span class="sxs-lookup"><span data-stu-id="c6604-128">When the application entry point returns a `Task` or `Task<int>`, the compiler generates a new entry point that calls the entry point method declared in the application code.</span></span> <span data-ttu-id="c6604-129">En supposant que ce point d’entrée est appelé `$GeneratedMain`, le compilateur génère le code suivant pour ces points d’entrée :</span><span class="sxs-lookup"><span data-stu-id="c6604-129">Assuming that this entry point is called `$GeneratedMain`, the compiler generates the following code for these entry points:</span></span>

- <span data-ttu-id="c6604-130">`static Task Main()` permet au compilateur d’émettre l’équivalent de `private static void $GeneratedMain() => Main().GetAwaiter().GetResult();`</span><span class="sxs-lookup"><span data-stu-id="c6604-130">`static Task Main()` results in the compiler emitting the equivalent of `private static void $GeneratedMain() => Main().GetAwaiter().GetResult();`</span></span>
- <span data-ttu-id="c6604-131">`static Task Main(string[])` permet au compilateur d’émettre l’équivalent de `private static void $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span><span class="sxs-lookup"><span data-stu-id="c6604-131">`static Task Main(string[])` results in the compiler emitting the equivalent of `private static void $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span></span>
- <span data-ttu-id="c6604-132">`static Task<int> Main()` permet au compilateur d’émettre l’équivalent de `private static int $GeneratedMain() => Main().GetAwaiter().GetResult();`</span><span class="sxs-lookup"><span data-stu-id="c6604-132">`static Task<int> Main()` results in the compiler emitting the equivalent of `private static int $GeneratedMain() => Main().GetAwaiter().GetResult();`</span></span>
- <span data-ttu-id="c6604-133">`static Task<int> Main(string[])` permet au compilateur d’émettre l’équivalent de `private static int $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span><span class="sxs-lookup"><span data-stu-id="c6604-133">`static Task<int> Main(string[])` results in the compiler emitting the equivalent of `private static int $GeneratedMain(string[] args) => Main(args).GetAwaiter().GetResult();`</span></span>

> [!NOTE]
><span data-ttu-id="c6604-134">Si les exemples ont utilisé le modificateur `async` sur la méthode `Main`, le compilateur génère le même code.</span><span class="sxs-lookup"><span data-stu-id="c6604-134">If the examples used `async` modifier on the `Main` method, the compiler would generate the same code.</span></span>

## <a name="see-also"></a><span data-ttu-id="c6604-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c6604-135">See also</span></span>
<span data-ttu-id="c6604-136">[Guide de programmation C#](../../programming-guide/index.md)
[Informations de référence sur C#](../index.md)
[Main() et arguments de ligne de commande](index.md)
[Guide pratique pour afficher les arguments de ligne de commande](../../programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)
[Guide pratique pour accéder aux arguments de ligne de commande à l’aide de foreach](../../programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)</span><span class="sxs-lookup"><span data-stu-id="c6604-136">[C# Programming Guide](../../programming-guide/index.md)
[C# Reference](../index.md)
[Main() and Command-Line Arguments](index.md)
[How to: Display Command Line Arguments](../../programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)
[How to: Access Command-Line Arguments Using foreach](../../programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)</span></span>
