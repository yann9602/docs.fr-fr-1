---
title: Hello World -- Votre premier programme (guide de programmation C#)
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: get-started-article
f1_keywords:
- cs.program
- vs.csharp.startpage.firstapplication
dev_langs:
- CSharp
helpviewer_keywords:
- examples [C#], Hello World
- Hello World example [C#]
ms.assetid: 6493182a-b0b6-4539-a719-518a168cb730
caps.latest.revision: 39
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
ms.sourcegitcommit: b7cb84362c96dac50ae5136334138b55ed1ce00b
ms.openlocfilehash: 03891f83885cf41ab157ebd78ef7e72767b4b163
ms.contentlocale: fr-fr
ms.lasthandoff: 07/31/2017

---
# <a name="hello-world----your-first-program-c-programming-guide"></a><span data-ttu-id="8e58d-102">Hello World -- Votre premier programme (guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="8e58d-102">Hello World -- Your First Program (C# Programming Guide)</span></span>
<span data-ttu-id="8e58d-103">La procédure suivante crée une version C# du traditionnel programme « Hello World ! »</span><span class="sxs-lookup"><span data-stu-id="8e58d-103">The following procedure creates a C# version of the traditional "Hello World!"</span></span> <span data-ttu-id="8e58d-104">.</span><span class="sxs-lookup"><span data-stu-id="8e58d-104">program.</span></span> <span data-ttu-id="8e58d-105">Le programme affiche la chaîne `Hello World!`</span><span class="sxs-lookup"><span data-stu-id="8e58d-105">The program displays the string `Hello World!`</span></span>  
  
 <span data-ttu-id="8e58d-106">Pour plus d’exemples concernant les concepts de base, consultez [Bien démarrer avec Visual Basic et Visual C#](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="8e58d-106">For more examples of introductory concepts, see [Getting Started with Visual C# and Visual Basic](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-and-run-a-console-application"></a><span data-ttu-id="8e58d-107">Pour créer et exécuter une application console</span><span class="sxs-lookup"><span data-stu-id="8e58d-107">To create and run a console application</span></span>  
  
1.  <span data-ttu-id="8e58d-108">Démarrez Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8e58d-108">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="8e58d-109">Dans la barre de menus, sélectionnez **Fichier**, **Nouveau**, **Projet**.</span><span class="sxs-lookup"><span data-stu-id="8e58d-109">On the menu bar, choose **File**, **New**, **Project**.</span></span>  
  
     <span data-ttu-id="8e58d-110">La boîte de dialogue **Nouveau projet** s'affiche.</span><span class="sxs-lookup"><span data-stu-id="8e58d-110">The **New Project** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="8e58d-111">Développez **Installé**, **Modèles**, **Visual C#**, puis choisissez **Application console**.</span><span class="sxs-lookup"><span data-stu-id="8e58d-111">Expand **Installed**, expand **Templates**, expand **Visual C#**, and then choose **Console Application**.</span></span>  
  
4.  <span data-ttu-id="8e58d-112">Dans la zone de texte **Nom**, entrez un nom pour votre projet, puis choisissez le bouton **OK**.</span><span class="sxs-lookup"><span data-stu-id="8e58d-112">In the **Name** box, specify a name for your project, and then choose the **OK** button.</span></span>  
  
     <span data-ttu-id="8e58d-113">Le nouveau projet s’affiche dans l’**Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="8e58d-113">The new project appears in **Solution Explorer**.</span></span>  
  
5.  <span data-ttu-id="8e58d-114">Si Program.cs n’est pas ouvert dans l’**Éditeur de Code**, ouvrez le menu contextuel de **Program.cs** dans **l’Explorateur de solutions**, puis choisissez **Afficher le code**.</span><span class="sxs-lookup"><span data-stu-id="8e58d-114">If Program.cs isn't open in the **Code Editor**, open the shortcut menu for **Program.cs** in **Solution Explorer**, and then choose **View Code**.</span></span>  
  
6.  <span data-ttu-id="8e58d-115">Remplacez le contenu de Program.cs par le code suivant.</span><span class="sxs-lookup"><span data-stu-id="8e58d-115">Replace the contents of Program.cs with the following code.</span></span>  
  
     <span data-ttu-id="8e58d-116">[!code-cs[csProgGuide#21](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="8e58d-116">[!code-cs[csProgGuide#21](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_1.cs)]</span></span>  
  
7.  <span data-ttu-id="8e58d-117">Appuyez sur la touche F5 pour exécuter le projet.</span><span class="sxs-lookup"><span data-stu-id="8e58d-117">Choose the F5 key to run the project.</span></span> <span data-ttu-id="8e58d-118">Une fenêtre d’invite de commandes s’affiche avec la ligne `Hello World!`</span><span class="sxs-lookup"><span data-stu-id="8e58d-118">A Command Prompt window appears that contains the line `Hello World!`</span></span>  
  
 <span data-ttu-id="8e58d-119">Ensuite, les parties importantes de ce programme sont examinées.</span><span class="sxs-lookup"><span data-stu-id="8e58d-119">Next, the important parts of this program are examined.</span></span>  
  
## <a name="comments"></a><span data-ttu-id="8e58d-120">Commentaires</span><span class="sxs-lookup"><span data-stu-id="8e58d-120">Comments</span></span>  
 <span data-ttu-id="8e58d-121">La première ligne contient un commentaire.</span><span class="sxs-lookup"><span data-stu-id="8e58d-121">The first line contains a comment.</span></span> <span data-ttu-id="8e58d-122">Les caractères `//` convertissent le reste de la ligne en un commentaire.</span><span class="sxs-lookup"><span data-stu-id="8e58d-122">The characters `//` convert the rest of the line to a comment.</span></span>  
  
 <span data-ttu-id="8e58d-123">[!code-cs[csProgGuide#32](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="8e58d-123">[!code-cs[csProgGuide#32](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_2.cs)]</span></span>  
  
 <span data-ttu-id="8e58d-124">Vous pouvez également créer un commentaire à partir d’un bloc de texte en le plaçant entre les caractères `/*` et `*/`.</span><span class="sxs-lookup"><span data-stu-id="8e58d-124">You can also comment out a block of text by enclosing it between the `/*` and `*/` characters.</span></span> <span data-ttu-id="8e58d-125">L'exemple suivant le démontre.</span><span class="sxs-lookup"><span data-stu-id="8e58d-125">This is shown in the following example.</span></span>  
  
 <span data-ttu-id="8e58d-126">[!code-cs[csProgGuide#33](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="8e58d-126">[!code-cs[csProgGuide#33](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_3.cs)]</span></span>  
  
## <a name="main-method"></a><span data-ttu-id="8e58d-127">Méthode Main</span><span class="sxs-lookup"><span data-stu-id="8e58d-127">Main Method</span></span>  
 <span data-ttu-id="8e58d-128">Une application console C# doit contenir une méthode `Main`, dans laquelle le contrôle commence et termine.</span><span class="sxs-lookup"><span data-stu-id="8e58d-128">A C# console application must contain a `Main` method, in which control starts and ends.</span></span> <span data-ttu-id="8e58d-129">C’est dans la méthode `Main` que vous créez des objets et exécutez d’autres méthodes.</span><span class="sxs-lookup"><span data-stu-id="8e58d-129">The `Main` method is where you create objects and execute other methods.</span></span>  
  
 <span data-ttu-id="8e58d-130">La méthode `Main` est une méthode [static](../../../csharp/language-reference/keywords/static.md) qui réside dans une classe ou un struct.</span><span class="sxs-lookup"><span data-stu-id="8e58d-130">The `Main` method is a [static](../../../csharp/language-reference/keywords/static.md) method that resides inside a class or a struct.</span></span> <span data-ttu-id="8e58d-131">Dans l’exemple « Hello World ! »</span><span class="sxs-lookup"><span data-stu-id="8e58d-131">In the previous "Hello World!"</span></span> <span data-ttu-id="8e58d-132">précédent, il réside dans une classe nommée `Hello`.</span><span class="sxs-lookup"><span data-stu-id="8e58d-132">example, it resides in a class named `Hello`.</span></span> <span data-ttu-id="8e58d-133">Vous pouvez déclarer la méthode `Main` de l’une des façons suivantes :</span><span class="sxs-lookup"><span data-stu-id="8e58d-133">You can declare the `Main` method in one of the following ways:</span></span>  
  
-   <span data-ttu-id="8e58d-134">Elle peut retourner `void`.</span><span class="sxs-lookup"><span data-stu-id="8e58d-134">It can return `void`.</span></span>  
  
     <span data-ttu-id="8e58d-135">[!code-cs[csProgGuideMain#12](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="8e58d-135">[!code-cs[csProgGuideMain#12](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_4.cs)]</span></span>  
  
-   <span data-ttu-id="8e58d-136">Elle peut également retourner un entier.</span><span class="sxs-lookup"><span data-stu-id="8e58d-136">It can also return an integer.</span></span>  
  
     <span data-ttu-id="8e58d-137">[!code-cs[csProgGuideMain#13](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="8e58d-137">[!code-cs[csProgGuideMain#13](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_5.cs)]</span></span>  
  
-   <span data-ttu-id="8e58d-138">Elle peut accepter des arguments avec n’importe quel type de retour.</span><span class="sxs-lookup"><span data-stu-id="8e58d-138">With either of the return types, it can take arguments.</span></span>  
  
     <span data-ttu-id="8e58d-139">[!code-cs[csProgGuideMain#19](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_6.cs)]</span><span class="sxs-lookup"><span data-stu-id="8e58d-139">[!code-cs[csProgGuideMain#19](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_6.cs)]</span></span>  
  
     <span data-ttu-id="8e58d-140">ou</span><span class="sxs-lookup"><span data-stu-id="8e58d-140">-or-</span></span>  
  
     <span data-ttu-id="8e58d-141">[!code-cs[csProgGuideMain#18](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_7.cs)]</span><span class="sxs-lookup"><span data-stu-id="8e58d-141">[!code-cs[csProgGuideMain#18](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_7.cs)]</span></span>  
  
 <span data-ttu-id="8e58d-142">Le paramètre `args` de la méthode `Main` est un tableau `string` qui contient les arguments de la ligne de commande utilisés pour appeler le programme.</span><span class="sxs-lookup"><span data-stu-id="8e58d-142">The parameter of the `Main` method, `args`, is a `string` array that contains the command-line arguments used to invoke the program.</span></span> <span data-ttu-id="8e58d-143">Contrairement au langage C++, le tableau n’inclut pas le nom du fichier exécutable (exe).</span><span class="sxs-lookup"><span data-stu-id="8e58d-143">Unlike in C++, the array does not include the name of the executable (exe) file.</span></span>  
  
 <span data-ttu-id="8e58d-144">Pour plus d’informations sur l’utilisation des arguments de ligne de commande, consultez les exemples des rubriques [Main() et arguments de ligne de commande](../../../csharp/programming-guide/main-and-command-args/index.md) et [Guide pratique pour créer et utiliser des assemblys à l’aide de la ligne de commande](http://msdn.microsoft.com/library/70f65026-3687-4e9c-ab79-c18b97dd8be4).</span><span class="sxs-lookup"><span data-stu-id="8e58d-144">For more information about how to use command-line arguments, see the examples in [Main() and Command-Line Arguments](../../../csharp/programming-guide/main-and-command-args/index.md) and [How to: Create and Use Assemblies Using the Command Line](http://msdn.microsoft.com/library/70f65026-3687-4e9c-ab79-c18b97dd8be4).</span></span>  
  
 <span data-ttu-id="8e58d-145">L’appel à <xref:System.Console.ReadKey%2A> à la fin de la méthode `Main` empêche la fenêtre de console de se fermer avant que vous ayez pu lire la sortie quand vous exécutez votre programme en mode débogage, avec la touche F5.</span><span class="sxs-lookup"><span data-stu-id="8e58d-145">The call to <xref:System.Console.ReadKey%2A> at the end of the `Main` method prevents the console window from closing before you have a chance to read the output when you run your program in debug mode, by pressing F5.</span></span>  
  
## <a name="input-and-output"></a><span data-ttu-id="8e58d-146">Entrées et sorties</span><span class="sxs-lookup"><span data-stu-id="8e58d-146">Input and Output</span></span>  
 <span data-ttu-id="8e58d-147">Les programmes C# utilisent généralement les services d’entrée/sortie fournis par la bibliothèque runtime du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8e58d-147">C# programs generally use the input/output services provided by the run-time library of the .NET Framework.</span></span> <span data-ttu-id="8e58d-148">L’instruction `System.Console.WriteLine("Hello World!");` utilise la méthode <xref:System.Console.WriteLine%2A>.</span><span class="sxs-lookup"><span data-stu-id="8e58d-148">The statement `System.Console.WriteLine("Hello World!");` uses the <xref:System.Console.WriteLine%2A> method.</span></span> <span data-ttu-id="8e58d-149">C’est l’une des méthodes de sortie de la classe <xref:System.Console> de la bibliothèque runtime.</span><span class="sxs-lookup"><span data-stu-id="8e58d-149">This is one of the output methods of the <xref:System.Console> class in the run-time library.</span></span> <span data-ttu-id="8e58d-150">Elle affiche son paramètre de chaîne dans le flux de sortie standard suivi d’une nouvelle ligne.</span><span class="sxs-lookup"><span data-stu-id="8e58d-150">It displays its string parameter on the standard output stream followed by a new line.</span></span> <span data-ttu-id="8e58d-151">D’autres méthodes <xref:System.Console> sont disponibles pour différentes opérations d’entrée et de sortie.</span><span class="sxs-lookup"><span data-stu-id="8e58d-151">Other <xref:System.Console> methods are available for different input and output operations.</span></span> <span data-ttu-id="8e58d-152">Si vous incluez la directive `using System;` au début du programme, vous pouvez utiliser directement les classes et les méthodes <xref:System> sans les qualifier complètement.</span><span class="sxs-lookup"><span data-stu-id="8e58d-152">If you include the `using System;` directive at the beginning of the program, you can directly use the <xref:System> classes and methods without fully qualifying them.</span></span> <span data-ttu-id="8e58d-153">Par exemple, vous pouvez appeler `Console.WriteLine` au lieu de `System.Console.WriteLine` :</span><span class="sxs-lookup"><span data-stu-id="8e58d-153">For example, you can call `Console.WriteLine` instead of `System.Console.WriteLine`:</span></span>  
  
 <span data-ttu-id="8e58d-154">[!code-cs[csProgGuide#1](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_8.cs)]</span><span class="sxs-lookup"><span data-stu-id="8e58d-154">[!code-cs[csProgGuide#1](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_8.cs)]</span></span>  
  
 <span data-ttu-id="8e58d-155">[!code-cs[csProgGuide#23](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_9.cs)]</span><span class="sxs-lookup"><span data-stu-id="8e58d-155">[!code-cs[csProgGuide#23](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_9.cs)]</span></span>  
  
 <span data-ttu-id="8e58d-156">Pour plus d’informations sur les méthodes d’entrée/sortie, consultez <xref:System.IO>.</span><span class="sxs-lookup"><span data-stu-id="8e58d-156">For more information about input/output methods, see <xref:System.IO>.</span></span>  
  
## <a name="command-line-compilation-and-execution"></a><span data-ttu-id="8e58d-157">Compilation et exécution en ligne de commande</span><span class="sxs-lookup"><span data-stu-id="8e58d-157">Command-Line Compilation and Execution</span></span>  
 <span data-ttu-id="8e58d-158">Vous pouvez compiler le programme « Hello World ! »</span><span class="sxs-lookup"><span data-stu-id="8e58d-158">You can compile the "Hello World!"</span></span> <span data-ttu-id="8e58d-159">à l’aide de la ligne de commande au lieu de l’environnement de développement intégré (IDE) Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8e58d-159">program by using the command line instead of the Visual Studio Integrated Development Environment (IDE).</span></span>  
  
#### <a name="to-compile-and-run-from-a-command-prompt"></a><span data-ttu-id="8e58d-160">Pour compiler et exécuter à partir d’une invite de commandes</span><span class="sxs-lookup"><span data-stu-id="8e58d-160">To compile and run from a command prompt</span></span>  
  
1.  <span data-ttu-id="8e58d-161">Copiez-collez le code de la procédure précédente dans un éditeur de texte, puis enregistrez le fichier en tant que fichier texte.</span><span class="sxs-lookup"><span data-stu-id="8e58d-161">Paste the code from the preceding procedure into any text editor, and then save the file as a text file.</span></span> <span data-ttu-id="8e58d-162">Nommez le fichier `Hello.cs`.</span><span class="sxs-lookup"><span data-stu-id="8e58d-162">Name the file `Hello.cs`.</span></span> <span data-ttu-id="8e58d-163">Les fichiers de code source C# utilisent l’extension `.cs`.</span><span class="sxs-lookup"><span data-stu-id="8e58d-163">C# source code files use the extension `.cs`.</span></span>  
  
2.  <span data-ttu-id="8e58d-164">Effectuez l’une des opérations suivantes pour ouvrir une fenêtre d’invite de commandes :</span><span class="sxs-lookup"><span data-stu-id="8e58d-164">Perform one of the following steps to open a command-prompt window:</span></span>  
  
    -   <span data-ttu-id="8e58d-165">Dans Windows 10, dans le menu **Démarrer**, recherchez `Developer Command Prompt`, puis choisissez **Invite de commandes développeur pour VS 2017**.</span><span class="sxs-lookup"><span data-stu-id="8e58d-165">In Windows 10, on the **Start** menu, search for `Developer Command Prompt`, and then tap or choose **Developer Command Prompt for VS 2017**.</span></span>  
  
         <span data-ttu-id="8e58d-166">Une fenêtre d’invite de commandes développeur s’affiche.</span><span class="sxs-lookup"><span data-stu-id="8e58d-166">A Developer Command Prompt window appears.</span></span>  
  
    -   <span data-ttu-id="8e58d-167">Dans Windows 7, ouvrez le menu **Démarrer**, développez le dossier de la version actuelle de Visual Studio, ouvrez le menu contextuel de **Visual Studio Tools**, puis choisissez **Invite de commandes de développeur de VS 2017**.</span><span class="sxs-lookup"><span data-stu-id="8e58d-167">In Windows 7, open the **Start** menu, expand the folder for the current version of Visual Studio, open the shortcut menu for **Visual Studio Tools**, and then choose **Developer Command Prompt for VS 2017**.</span></span>  
  
         <span data-ttu-id="8e58d-168">Une fenêtre d’invite de commandes développeur s’affiche.</span><span class="sxs-lookup"><span data-stu-id="8e58d-168">A Developer Command Prompt window appears.</span></span>  
  
    -   <span data-ttu-id="8e58d-169">Activez les générations en mode ligne de commande à partir d’une fenêtre d’invite de commandes standard.</span><span class="sxs-lookup"><span data-stu-id="8e58d-169">Enable command-line builds from a standard Command Prompt window.</span></span>  
  
         <span data-ttu-id="8e58d-170">Consultez [Guide pratique pour définir des variables d’environnement pour la ligne de commande Visual Studio](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md).</span><span class="sxs-lookup"><span data-stu-id="8e58d-170">See [How to: Set Environment Variables for the Visual Studio Command Line](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md).</span></span>  
  
3.  <span data-ttu-id="8e58d-171">Dans la fenêtre d’invite de commandes, accédez au dossier qui contient le fichier `Hello.cs`.</span><span class="sxs-lookup"><span data-stu-id="8e58d-171">In the command-prompt window, navigate to the folder that contains your `Hello.cs` file.</span></span>  
  
4.  <span data-ttu-id="8e58d-172">Entrez la commande suivante pour compiler `Hello.cs`.</span><span class="sxs-lookup"><span data-stu-id="8e58d-172">Enter the following command to compile `Hello.cs`.</span></span>  
  
     `csc Hello.cs`  
  
     <span data-ttu-id="8e58d-173">Si votre programme ne contient pas d’erreurs de compilation, un fichier exécutable nommé `Hello.exe` est créé.</span><span class="sxs-lookup"><span data-stu-id="8e58d-173">If your program has no compilation errors, an executable file that is named `Hello.exe` is created.</span></span>  
  
5.  <span data-ttu-id="8e58d-174">Dans la fenêtre d’invite de commandes, entrez la commande suivante pour exécuter le programme :</span><span class="sxs-lookup"><span data-stu-id="8e58d-174">In the command-prompt window, enter the following command to run the program:</span></span>  
  
     `Hello`  
  
 <span data-ttu-id="8e58d-175">Pour plus d’informations sur le compilateur C# et ses options, consultez [Options du compilateur C #](../../../csharp/language-reference/compiler-options/index.md).</span><span class="sxs-lookup"><span data-stu-id="8e58d-175">For more information about the C# compiler and its options, see [C# Compiler Options](../../../csharp/language-reference/compiler-options/index.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="8e58d-176">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8e58d-176">See Also</span></span>  
 <span data-ttu-id="8e58d-177">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="8e58d-177">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="8e58d-178">[À l’intérieur d’un programme C#](../../../csharp/programming-guide/inside-a-program/index.md) </span><span class="sxs-lookup"><span data-stu-id="8e58d-178">[Inside a C# Program](../../../csharp/programming-guide/inside-a-program/index.md) </span></span>  
 <span data-ttu-id="8e58d-179">[Chaînes](../../../csharp/programming-guide/strings/index.md) </span><span class="sxs-lookup"><span data-stu-id="8e58d-179">[Strings](../../../csharp/programming-guide/strings/index.md) </span></span>  
 <span data-ttu-id="8e58d-180">[\<paveover>Exemples d’applications Visual C#](http://msdn.microsoft.com/en-us/9a9d7aaa-51d3-4224-b564-95409b0f3e15) </span><span class="sxs-lookup"><span data-stu-id="8e58d-180">[\<paveover>C# Sample Applications](http://msdn.microsoft.com/en-us/9a9d7aaa-51d3-4224-b564-95409b0f3e15) </span></span>  
 <span data-ttu-id="8e58d-181">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="8e58d-181">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="8e58d-182">[Main() et arguments de ligne de commande](../../../csharp/programming-guide/main-and-command-args/index.md) </span><span class="sxs-lookup"><span data-stu-id="8e58d-182">[Main() and Command-Line Arguments](../../../csharp/programming-guide/main-and-command-args/index.md) </span></span>  
 [<span data-ttu-id="8e58d-183">Bien démarrer avec Visual Basic et Visual C#</span><span class="sxs-lookup"><span data-stu-id="8e58d-183">Getting Started with Visual C# and Visual Basic</span></span>](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic)

