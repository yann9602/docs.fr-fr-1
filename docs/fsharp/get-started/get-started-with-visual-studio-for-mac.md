---
title: 'Prise en main) (F # dans Visual Studio pour Mac'
description: "Découvrez comment utiliser F # avec Visual Studio pour Mac."
keywords: visual f#, f#, programmation fonctionnelle
author: mizzle-mo
ms.author: phcart
ms.date: 02/13/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 8db75596-19a9-4eda-b20d-a12d517c8cc1
ms.openlocfilehash: beee874e3a549531b520d4ac2150bc10dcab7725
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="get-started-with-f-in-visual-studio-for-mac"></a><span data-ttu-id="2bd9b-104">Prise en main) (F # dans Visual Studio pour Mac</span><span class="sxs-lookup"><span data-stu-id="2bd9b-104">Get started with F# in Visual Studio for Mac</span></span>

<span data-ttu-id="2bd9b-105">F # et les outils Visual F # sont pris en charge dans Visual Studio pour Mac IDE.</span><span class="sxs-lookup"><span data-stu-id="2bd9b-105">F# and the Visual F# tooling are supported in the Visual Studio for Mac IDE.</span></span>  <span data-ttu-id="2bd9b-106">Pour commencer, vous devez [télécharger Visual Studio pour Mac](https://www.visualstudio.com/downloads/download-visual-studio-vs), si vous n’avez pas encore.</span><span class="sxs-lookup"><span data-stu-id="2bd9b-106">To begin, you should [download Visual Studio for Mac](https://www.visualstudio.com/downloads/download-visual-studio-vs), if you haven't already.</span></span>  <span data-ttu-id="2bd9b-107">Cet article utilise la 2017 de communauté Visual Studio pour Mac, mais vous pouvez utiliser F # avec la version de votre choix.</span><span class="sxs-lookup"><span data-stu-id="2bd9b-107">This article uses the Visual Studio Community 2017 for Mac, but you can use F# with the version of your choice.</span></span>

## <a name="installing-f"></a><span data-ttu-id="2bd9b-108">Lors de l’installation) (F #</span><span class="sxs-lookup"><span data-stu-id="2bd9b-108">Installing F#</span></span> #

<span data-ttu-id="2bd9b-109">Après avoir téléchargé Visual Studio pour Mac, vous êtes invité à choisir ce que vous souhaitez installer.</span><span class="sxs-lookup"><span data-stu-id="2bd9b-109">After downloading Visual Studio for Mac, it will prompt you to choose what you want to install.</span></span>  <span data-ttu-id="2bd9b-110">Dans le cadre de cet article nous laissant les valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="2bd9b-110">For the purposes of this article we will be leaving the defaults.</span></span>  <span data-ttu-id="2bd9b-111">Contrairement à Visual Studio pour Windows, vous n’avez pas besoin de spécifiquement installer prise en charge F #.</span><span class="sxs-lookup"><span data-stu-id="2bd9b-111">In contrast to Visual Studio for Windows, you do not need to specifically install F# support.</span></span>  <span data-ttu-id="2bd9b-112">Appuyez sur « Installer » pour continuer.</span><span class="sxs-lookup"><span data-stu-id="2bd9b-112">Press "Install" to proceed.</span></span>

<span data-ttu-id="2bd9b-113">Une fois l’installation terminée, cliquez sur « Démarrer Visual Studio ».</span><span class="sxs-lookup"><span data-stu-id="2bd9b-113">After the install completes, choose "Start Visual Studio".</span></span>  <span data-ttu-id="2bd9b-114">Vous pouvez également lancer il via Finder sur macOS.</span><span class="sxs-lookup"><span data-stu-id="2bd9b-114">You can also launch it through Finder on macOS.</span></span>

## <a name="creating-a-console-application"></a><span data-ttu-id="2bd9b-115">Création d’une application console</span><span class="sxs-lookup"><span data-stu-id="2bd9b-115">Creating a console application</span></span>

<span data-ttu-id="2bd9b-116">Un des projets dans Visual Studio pour Mac plus simples est de l’Application Console.</span><span class="sxs-lookup"><span data-stu-id="2bd9b-116">One of the most basic projects in Visual Studio for Mac is the Console Application.</span></span>  <span data-ttu-id="2bd9b-117">Voici comment faire.</span><span class="sxs-lookup"><span data-stu-id="2bd9b-117">Here's how to do it.</span></span>  <span data-ttu-id="2bd9b-118">Une fois ouvert Visual Studio pour Mac :</span><span class="sxs-lookup"><span data-stu-id="2bd9b-118">Once Visual Studio for Mac is open:</span></span>

1. <span data-ttu-id="2bd9b-119">Sur le **fichier** menu, pointez sur **nouvelle Solution**.</span><span class="sxs-lookup"><span data-stu-id="2bd9b-119">On the **File** menu, point to **New Solution**.</span></span>

2.  <span data-ttu-id="2bd9b-120">Dans la boîte de dialogue Nouveau projet, il existe 2 différents modèles pour une Application Console.</span><span class="sxs-lookup"><span data-stu-id="2bd9b-120">In the New Project dialog, there are 2 different templates for Console Application.</span></span>  <span data-ttu-id="2bd9b-121">Il y a un sous d’autres -> .NET qui cible le .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2bd9b-121">There is one under Other -> .NET which targets the .NET Framework.</span></span>  <span data-ttu-id="2bd9b-122">L’autre modèle est sous .NET Core -> application qui cible le .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2bd9b-122">The other template is under .NET Core -> App which targets .NET Core.</span></span>  <span data-ttu-id="2bd9b-123">Un modèle doit fonctionner pour les besoins de cet article.</span><span class="sxs-lookup"><span data-stu-id="2bd9b-123">Either template should work for the purpose of this article.</span></span>

3. <span data-ttu-id="2bd9b-124">Sous l’application de console, changez c# à F #.</span><span class="sxs-lookup"><span data-stu-id="2bd9b-124">Under console app, change C# to F# if needed.</span></span>  <span data-ttu-id="2bd9b-125">Choisissez le **suivant** bouton Déplacer vers l’avant.</span><span class="sxs-lookup"><span data-stu-id="2bd9b-125">Choose the **Next** button to move forward!</span></span>  

4. <span data-ttu-id="2bd9b-126">Donnez un nom à votre projet et choisissez les options souhaitées pour l’application.</span><span class="sxs-lookup"><span data-stu-id="2bd9b-126">Give your project a name, and choose the options you want for the app.</span></span>  <span data-ttu-id="2bd9b-127">Notez, le volet de visualisation sur le côté de l’écran qui affiche la structure de répertoire qui sera créée en fonction des options sélectionnées.</span><span class="sxs-lookup"><span data-stu-id="2bd9b-127">Notice, the preview pane to the side of the screen that will show the directory structure that will be created based on the options selected.</span></span>  

5. <span data-ttu-id="2bd9b-128">Cliquez sur **Créer**.</span><span class="sxs-lookup"><span data-stu-id="2bd9b-128">Click **Create**.</span></span>  <span data-ttu-id="2bd9b-129">Vous devez maintenant voir un projet F # dans l’Explorateur de solutions.</span><span class="sxs-lookup"><span data-stu-id="2bd9b-129">You should now see an F# project in the Solution Explorer.</span></span>

## <a name="writing-your-code"></a><span data-ttu-id="2bd9b-130">L’écriture de votre code.</span><span class="sxs-lookup"><span data-stu-id="2bd9b-130">Writing your code</span></span>

<span data-ttu-id="2bd9b-131">Nous pouvons commencer à écrire du code tout d’abord.</span><span class="sxs-lookup"><span data-stu-id="2bd9b-131">Let's get started by writing some code first.</span></span>  <span data-ttu-id="2bd9b-132">Assurez-vous que le `Program.fs` fichier est ouvert, puis remplacez son contenu par les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="2bd9b-132">Make sure that the `Program.fs` file is open, and then replace its contents with the following:</span></span>

[!code-fsharp[HelloSquare](../../../samples/snippets/fsharp/getting-started/hello-square.fs)]

<span data-ttu-id="2bd9b-133">Dans l’exemple de code précédent, une fonction `square` a été défini qui accepte une entrée nommée `x` et multiplie par lui-même.</span><span class="sxs-lookup"><span data-stu-id="2bd9b-133">In the previous code sample, a function `square` has been defined which takes an input named `x` and multiplies it by itself.</span></span>  <span data-ttu-id="2bd9b-134">Étant donné que F # utilise [l’inférence de Type](../language-reference/type-inference.md), le type de `x` n’a pas besoin d’être spécifiés.</span><span class="sxs-lookup"><span data-stu-id="2bd9b-134">Because F# uses [Type Inference](../language-reference/type-inference.md), the type of `x` doesn't need to be specified.</span></span>  <span data-ttu-id="2bd9b-135">Le compilateur F # comprend les types où la multiplication est valide et affectera un type à `x` selon la façon dont `square` est appelée.</span><span class="sxs-lookup"><span data-stu-id="2bd9b-135">The F# compiler understands the types where multiplication is valid, and will assign a type to `x` based on how `square` is called.</span></span>  <span data-ttu-id="2bd9b-136">Si vous pointez sur `square`, vous devez voir les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="2bd9b-136">If you hover over `square`, you should see the following:</span></span>

```
val square: x:int -> int
```

<span data-ttu-id="2bd9b-137">C’est ce que l'on appelle la signature de type de la fonction.</span><span class="sxs-lookup"><span data-stu-id="2bd9b-137">This is what is known as the function's type signature.</span></span>  <span data-ttu-id="2bd9b-138">Il peut être lu comme suit : « carrée est une fonction qui accepte un entier nommé x et produit un entier ».</span><span class="sxs-lookup"><span data-stu-id="2bd9b-138">It can be read like this: "Square is a function which takes an integer named x and produces an integer".</span></span>  <span data-ttu-id="2bd9b-139">Notez que le compilateur a donné `square` le `int` type pour le moment - il s’agit, car la multiplication n’est pas générique sur *tous les* types, mais plutôt générique entre un ensemble fermé de types.</span><span class="sxs-lookup"><span data-stu-id="2bd9b-139">Note that the compiler gave `square` the `int` type for now - this is because multiplication is not generic across *all* types, but rather is generic across a closed set of types.</span></span>  <span data-ttu-id="2bd9b-140">Le compilateur F # prélevé `int` sur ce point, mais il ajuste la signature de type si vous appelez `square` avec un autre type d’entrée, comme un `float`.</span><span class="sxs-lookup"><span data-stu-id="2bd9b-140">The F# compiler picked `int` at this point, but it will adjust the type signature if you call `square` with a different input type, such as a `float`.</span></span>

<span data-ttu-id="2bd9b-141">Une autre fonction, `main`, est défini, ce qui est décoré avec le `EntryPoint` attribut pour indiquer au compilateur F # que l’exécution du programme doit commencer de là.</span><span class="sxs-lookup"><span data-stu-id="2bd9b-141">Another function, `main`, is defined, which is decorated with the `EntryPoint` attribute to tell the F# compiler that program execution should start there.</span></span>  <span data-ttu-id="2bd9b-142">Il suit la même convention que les autres [les langages de programmation de style C](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), où les arguments de ligne de commande peuvent être passés à cette fonction, et un code d’entier est retourné (généralement `0`).</span><span class="sxs-lookup"><span data-stu-id="2bd9b-142">It follows the same convention as other [C-style programming languages](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), where command-line arguments can be passed to this function, and an integer code is returned (typically `0`).</span></span>

<span data-ttu-id="2bd9b-143">Il se trouve dans cette fonction que nous appelons le `square` fonction avec un argument de `12`.</span><span class="sxs-lookup"><span data-stu-id="2bd9b-143">It is in this function that we call the `square` function with an argument of `12`.</span></span>  <span data-ttu-id="2bd9b-144">Le compilateur F # puis assigne le type de `square` être `int -> int` (autrement dit, une fonction qui prend un `int` et produit un `int`).</span><span class="sxs-lookup"><span data-stu-id="2bd9b-144">The F# compiler then assigns the type of `square` to be `int -> int` (that is, a function which takes an `int` and produces an `int`).</span></span>  <span data-ttu-id="2bd9b-145">L’appel à `printfn` est une fonction d’impression mis en forme qui utilise une chaîne de format, semblable aux langages de programmation de style C, les paramètres qui correspondent à celles spécifiées dans la chaîne de format, puis imprime le résultat et une nouvelle ligne.</span><span class="sxs-lookup"><span data-stu-id="2bd9b-145">The call to `printfn` is a formatted printing function which uses a format string, similar to C-style programming languages, parameters which correspond to those specified in the format string, and then prints the result and a new line.</span></span>

## <a name="running-your-code"></a><span data-ttu-id="2bd9b-146">Exécution de votre code</span><span class="sxs-lookup"><span data-stu-id="2bd9b-146">Running your code</span></span>

<span data-ttu-id="2bd9b-147">Vous pouvez exécuter le code et afficher les résultats en cliquant sur **exécuter** à partir du menu de niveau supérieur, puis **démarrer sans débogage**.</span><span class="sxs-lookup"><span data-stu-id="2bd9b-147">You can run the code and see results by clicking on **Run** from the top level menu and then **Start Without Debugging**.</span></span>  <span data-ttu-id="2bd9b-148">Il exécute le programme sans débogage et vous permet de voir les résultats.</span><span class="sxs-lookup"><span data-stu-id="2bd9b-148">This will run the program without debugging and allows you to see the results.</span></span>

<span data-ttu-id="2bd9b-149">Vous devez maintenant voir imprimés dans la fenêtre de console Visual Studio pour Mac s’affichaient suivantes :</span><span class="sxs-lookup"><span data-stu-id="2bd9b-149">You should now see the following printed to the console window that Visual Studio for Mac popped up:</span></span>

```
12 squared is 144!
```

<span data-ttu-id="2bd9b-150">Félicitations !</span><span class="sxs-lookup"><span data-stu-id="2bd9b-150">Congratulations!</span></span>  <span data-ttu-id="2bd9b-151">Vous avez créé votre premier projet F # dans Visual Studio pour Mac, écrit qu'une fonction) (F # imprimer les résultats de l’appel de cette fonction et exécutez le projet pour afficher certains résultats.</span><span class="sxs-lookup"><span data-stu-id="2bd9b-151">You've created your first F# project in Visual Studio for Mac, written an F# function printed the results of calling that function, and run the project to see some results.</span></span>

## <a name="using-f-interactive"></a><span data-ttu-id="2bd9b-152">À l’aide de F # Interactive</span><span class="sxs-lookup"><span data-stu-id="2bd9b-152">Using F# Interactive</span></span>

<span data-ttu-id="2bd9b-153">L’une des meilleures fonctionnalités de la Visual F # pour les outils dans Visual Studio pour Mac est la fenêtre F # Interactive.</span><span class="sxs-lookup"><span data-stu-id="2bd9b-153">One of the best features of the Visual F# tooling in Visual Studio for Mac is the F# Interactive Window.</span></span>  <span data-ttu-id="2bd9b-154">Il vous permet d’envoyer le code sur un processus dans lequel vous pouvez appeler ce code et afficher le résultat de manière interactive.</span><span class="sxs-lookup"><span data-stu-id="2bd9b-154">It allows you to send code over to a process where you can call that code and see the result interactively.</span></span>

<span data-ttu-id="2bd9b-155">Pour commencer à l’utiliser, mettez en surbrillance le `square` fonction définie dans votre code.</span><span class="sxs-lookup"><span data-stu-id="2bd9b-155">To begin using it, highlight the `square` function defined in your code.</span></span>  <span data-ttu-id="2bd9b-156">Cliquez ensuite sur **modifier** à partir du menu de niveau supérieur.</span><span class="sxs-lookup"><span data-stu-id="2bd9b-156">Next, click on **Edit** from the top level menu.</span></span>  <span data-ttu-id="2bd9b-157">Ensuite, sélectionnez **envoyer la sélection à F # Interactive**.</span><span class="sxs-lookup"><span data-stu-id="2bd9b-157">Next select **Send selection to F# Interactive**.</span></span>  <span data-ttu-id="2bd9b-158">Il exécute le code dans la fenêtre F # Interactive.</span><span class="sxs-lookup"><span data-stu-id="2bd9b-158">This executes the code in the F# Interactive Window.</span></span>  <span data-ttu-id="2bd9b-159">Ou bien, vous pouvez cliquez avec le bouton droit sur la sélection et choisissez **envoyer la sélection à F # Interactive**.</span><span class="sxs-lookup"><span data-stu-id="2bd9b-159">Alternatively, you can right click on the selection and choose **Send selection to F# Interactive**.</span></span>  <span data-ttu-id="2bd9b-160">Vous devriez voir la fenêtre F # Interactive par le code suivant dans celui-ci :</span><span class="sxs-lookup"><span data-stu-id="2bd9b-160">You should see the F# Interactive Window appear with the following in it:</span></span>

```
>

val square : x:int -> int

>
```

<span data-ttu-id="2bd9b-161">Cela montre la même signature de fonction pour le `square` (fonction), vous l’avez vu précédemment lorsque vous pointez sur la fonction.</span><span class="sxs-lookup"><span data-stu-id="2bd9b-161">This shows the same function signature for the `square` function, which you saw earlier when you hovered over the function.</span></span>  <span data-ttu-id="2bd9b-162">Étant donné que `square` est maintenant défini dans le processus interactif F #, vous pouvez l’appeler avec des valeurs différentes :</span><span class="sxs-lookup"><span data-stu-id="2bd9b-162">Because `square` is now defined in the F# Interactive process, you can call it with different values:</span></span>

```
> square 12;;
val it : int = 144
>square 13;;
val it : int = 169
```

<span data-ttu-id="2bd9b-163">Cela exécute la fonction, lie le résultat à un nouveau nom `it`et affiche le type et la valeur de `it`.</span><span class="sxs-lookup"><span data-stu-id="2bd9b-163">This executes the function, binds the result to a new name `it`, and displays the type and value of `it`.</span></span>  <span data-ttu-id="2bd9b-164">Notez que vous devez mettre fin à chaque ligne avec `;;`.</span><span class="sxs-lookup"><span data-stu-id="2bd9b-164">Note that you must terminate each line with `;;`.</span></span>  <span data-ttu-id="2bd9b-165">Voici comment F # Interactive sait quand votre appel de fonction est terminée.</span><span class="sxs-lookup"><span data-stu-id="2bd9b-165">This is how F# Interactive knows when your function call is finished.</span></span>  <span data-ttu-id="2bd9b-166">Vous pouvez également définir de nouvelles fonctions dans F # Interactive :</span><span class="sxs-lookup"><span data-stu-id="2bd9b-166">You can also define new functions in F# Interactive:</span></span>

```
> let isOdd x = x % 2 <> 0;;

val isOdd : x:int -> bool

> isOdd 12;;
val it : bool = false
```

<span data-ttu-id="2bd9b-167">Ci-dessus définit une nouvelle fonction, `isOdd`, qui prend un `int` et vérifie s’il est impair !</span><span class="sxs-lookup"><span data-stu-id="2bd9b-167">The above defines a new function, `isOdd`, which takes an `int` and checks to see if it's odd!</span></span>  <span data-ttu-id="2bd9b-168">Vous pouvez appeler cette fonction pour afficher sa valeur de retour avec des entrées différentes.</span><span class="sxs-lookup"><span data-stu-id="2bd9b-168">You can call this function to see what it returns with different inputs.</span></span>  <span data-ttu-id="2bd9b-169">Vous pouvez appeler des fonctions dans les appels de fonction :</span><span class="sxs-lookup"><span data-stu-id="2bd9b-169">You can call functions within function calls:</span></span>

```
> isOdd (square 15);;
val it : bool = true
```

<span data-ttu-id="2bd9b-170">Vous pouvez également utiliser le [avant de canal opérateur](../language-reference/symbol-and-operator-reference/index.md) à la valeur de pipeline dans les deux fonctions :</span><span class="sxs-lookup"><span data-stu-id="2bd9b-170">You can also use the [pipe-forward operator](../language-reference/symbol-and-operator-reference/index.md) to pipeline the value into the two functions:</span></span>

```
> 15 |> square |> isOdd;;
val it : bool = true
```

<span data-ttu-id="2bd9b-171">L’opérateur avant de canal et bien plus encore, sont traités dans des didacticiels ultérieurs.</span><span class="sxs-lookup"><span data-stu-id="2bd9b-171">The pipe-forward operator, and more, are covered in later tutorials.</span></span>

<span data-ttu-id="2bd9b-172">Il s’agit uniquement d’un aperçu en ce que vous pouvez faire avec F # Interactive.</span><span class="sxs-lookup"><span data-stu-id="2bd9b-172">This is only a glimpse into what you can do with F# Interactive.</span></span>  <span data-ttu-id="2bd9b-173">Pour plus d’informations, consultez [de programmation Interactive avec F #](../tutorials/fsharp-interactive/index.md).</span><span class="sxs-lookup"><span data-stu-id="2bd9b-173">To learn more, check out [Interactive Programming with F#](../tutorials/fsharp-interactive/index.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="2bd9b-174">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="2bd9b-174">Next steps</span></span>

<span data-ttu-id="2bd9b-175">Si vous n’avez pas encore, consultez le [visite guidée de F #](../tour.md), qui traite de certaines fonctionnalités de base du langage F #.</span><span class="sxs-lookup"><span data-stu-id="2bd9b-175">If you haven't already, check out the [Tour of F#](../tour.md), which covers some of the core features of the F# language.</span></span>  <span data-ttu-id="2bd9b-176">Il vous donner une vue d’ensemble de certaines des fonctionnalités de F # et fournissent des exemples de code suffisamment que vous pouvez copier dans Visual Studio pour Mac et les exécuter.</span><span class="sxs-lookup"><span data-stu-id="2bd9b-176">It will give you an overview of some of the capabilities of F#, and provide ample code samples that you can copy into Visual Studio for Mac and run.</span></span>  <span data-ttu-id="2bd9b-177">Il existe également des ressources utiles externes, vous pouvez utiliser, a dans le [Guide F #](../index.md).</span><span class="sxs-lookup"><span data-stu-id="2bd9b-177">There are also some great external resources you can use, showcased in the [F# Guide](../index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2bd9b-178">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2bd9b-178">See also</span></span>
 [<span data-ttu-id="2bd9b-179">Visual F#</span><span class="sxs-lookup"><span data-stu-id="2bd9b-179">Visual F#</span></span>](../index.md)  
 [<span data-ttu-id="2bd9b-180">Présentation de F#</span><span class="sxs-lookup"><span data-stu-id="2bd9b-180">Tour of F#</span></span>](../tour.md)  
 [<span data-ttu-id="2bd9b-181">Référence du langage F #</span><span class="sxs-lookup"><span data-stu-id="2bd9b-181">F# language reference</span></span>](../language-reference/index.md)  
 [<span data-ttu-id="2bd9b-182">Inférence de type</span><span class="sxs-lookup"><span data-stu-id="2bd9b-182">Type inference</span></span>](../language-reference/type-inference.md)  
 [<span data-ttu-id="2bd9b-183">Référence des symboles et l’opérateur</span><span class="sxs-lookup"><span data-stu-id="2bd9b-183">Symbol and operator reference</span></span>](../language-reference/symbol-and-operator-reference/index.md)  
