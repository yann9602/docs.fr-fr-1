---
title: 'Prise en main) (F # dans Visual Studio'
description: "Découvrez comment utiliser F # avec Visual Studio."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 02/13/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 8db75596-19a9-4eda-b20d-a12d517c8cc1
ms.openlocfilehash: 944bbbba6a26634ace269d86cbbdde9ef9de7bcd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="get-started-with-f-in-visual-studio"></a><span data-ttu-id="fcd1e-104">Prise en main) (F # dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="fcd1e-104">Get started with F# in Visual Studio</span></span>

<span data-ttu-id="fcd1e-105">F # et les outils Visual F # sont pris en charge dans l’IDE de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="fcd1e-105">F# and the Visual F# tooling are supported in the Visual Studio IDE.</span></span>  <span data-ttu-id="fcd1e-106">Pour commencer, vous devez [télécharger Visual Studio](https://www.visualstudio.com/downloads/download-visual-studio-vs), si vous n’avez pas encore.</span><span class="sxs-lookup"><span data-stu-id="fcd1e-106">To begin, you should [download Visual Studio](https://www.visualstudio.com/downloads/download-visual-studio-vs), if you haven't already.</span></span>  <span data-ttu-id="fcd1e-107">Cet article utilise Visual Studio 2017 Community Edition, mais vous pouvez utiliser F # avec la version de votre choix.</span><span class="sxs-lookup"><span data-stu-id="fcd1e-107">This article uses the Visual Studio 2017 Community Edition, but you can use F# with the version of your choice.</span></span>

## <a name="installing-f"></a><span data-ttu-id="fcd1e-108">Lors de l’installation) (F #</span><span class="sxs-lookup"><span data-stu-id="fcd1e-108">Installing F#</span></span> #

<span data-ttu-id="fcd1e-109">Si vous téléchargez Visual Studio pour la première fois, il sera tout d’abord installer le programme d’installation de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="fcd1e-109">If you're downloading Visual Studio for the first time, it will first install the Visual Studio installer.</span></span>  <span data-ttu-id="fcd1e-110">Installer une version de Visual Studio 2017 du programme d’installation.</span><span class="sxs-lookup"><span data-stu-id="fcd1e-110">Install any version of Visual Studio 2017 from the installer.</span></span> <span data-ttu-id="fcd1e-111">Si vous avez déjà installé, cliquez sur **modifier**.</span><span class="sxs-lookup"><span data-stu-id="fcd1e-111">If you already have it installed, click **Modify**.</span></span>

<span data-ttu-id="fcd1e-112">Vous verrez ensuite une liste de charges de travail.</span><span class="sxs-lookup"><span data-stu-id="fcd1e-112">You'll next see a list of Workloads.</span></span> <span data-ttu-id="fcd1e-113">Vous pouvez installer F # par le biais des charges de travail suivants :</span><span class="sxs-lookup"><span data-stu-id="fcd1e-113">You can install F# through any of the following workloads:</span></span>

|<span data-ttu-id="fcd1e-114">Charge de travail</span><span class="sxs-lookup"><span data-stu-id="fcd1e-114">Workload</span></span>|<span data-ttu-id="fcd1e-115">Action</span><span class="sxs-lookup"><span data-stu-id="fcd1e-115">Action</span></span>|
|--------|------|
| <span data-ttu-id="fcd1e-116">Développement multiplateforme .NET Core</span><span class="sxs-lookup"><span data-stu-id="fcd1e-116">.NET Core cross-platform development</span></span> | <span data-ttu-id="fcd1e-117">Aucune action - F # n’est installée par défaut</span><span class="sxs-lookup"><span data-stu-id="fcd1e-117">No action - F# is installed by default</span></span> |
| <span data-ttu-id="fcd1e-118">Développement web et ASP.NET</span><span class="sxs-lookup"><span data-stu-id="fcd1e-118">ASP.NET and web development</span></span> | <span data-ttu-id="fcd1e-119">Aucune action - F # n’est installée par défaut</span><span class="sxs-lookup"><span data-stu-id="fcd1e-119">No action - F# is installed by default</span></span> |
| <span data-ttu-id="fcd1e-120">Développement Azure</span><span class="sxs-lookup"><span data-stu-id="fcd1e-120">Azure development</span></span> | <span data-ttu-id="fcd1e-121">Aucune action - F # n’est installée par défaut</span><span class="sxs-lookup"><span data-stu-id="fcd1e-121">No action - F# is installed by default</span></span> |
| <span data-ttu-id="fcd1e-122">Développement mobile en .NET</span><span class="sxs-lookup"><span data-stu-id="fcd1e-122">Mobile development with .NET</span></span> | <span data-ttu-id="fcd1e-123">Aucune action - F # n’est installée par défaut</span><span class="sxs-lookup"><span data-stu-id="fcd1e-123">No action - F# is installed by default</span></span> |
| <span data-ttu-id="fcd1e-124">Applications de science des données et analytiques</span><span class="sxs-lookup"><span data-stu-id="fcd1e-124">Data science and analytical applications</span></span> | <span data-ttu-id="fcd1e-125">Aucune action - F # n’est installée par défaut</span><span class="sxs-lookup"><span data-stu-id="fcd1e-125">No action - F# is installed by default</span></span> |
| <span data-ttu-id="fcd1e-126">Développement .NET Desktop</span><span class="sxs-lookup"><span data-stu-id="fcd1e-126">.NET desktop development</span></span> | <span data-ttu-id="fcd1e-127">Sélectionnez **prise en charge de bureau langage F #** à partir de la droite</span><span class="sxs-lookup"><span data-stu-id="fcd1e-127">Select **F# desktop language support** from the right-hand side</span></span> |
| <span data-ttu-id="fcd1e-128">Traitement et stockage de données</span><span class="sxs-lookup"><span data-stu-id="fcd1e-128">Data storage and processing</span></span> | <span data-ttu-id="fcd1e-129">Sélectionnez **prise en charge de bureau langage F #** à partir de la droite</span><span class="sxs-lookup"><span data-stu-id="fcd1e-129">Select **F# desktop language support** from the right-hand side</span></span> |

<span data-ttu-id="fcd1e-130">Ensuite, cliquez sur **modifier** dans l’angle inférieur droit.</span><span class="sxs-lookup"><span data-stu-id="fcd1e-130">Next, click **Modify** in the lower right-hand side.</span></span>  <span data-ttu-id="fcd1e-131">Ceci installe tout ce dont vous avez sélectionné.</span><span class="sxs-lookup"><span data-stu-id="fcd1e-131">This will install everything you have selected.</span></span>  <span data-ttu-id="fcd1e-132">Vous pouvez ensuite ouvrir Visual Studio 2017 avec prise en charge linguistique F # en cliquant sur **lancer**.</span><span class="sxs-lookup"><span data-stu-id="fcd1e-132">You can then open Visual Studio 2017 with F# language support by clicking **Launch**.</span></span>

## <a name="creating-a-console-application"></a><span data-ttu-id="fcd1e-133">Création d’une application console</span><span class="sxs-lookup"><span data-stu-id="fcd1e-133">Creating a console application</span></span>

<span data-ttu-id="fcd1e-134">Un des projets dans Visual Studio plus simples est de l’Application Console.</span><span class="sxs-lookup"><span data-stu-id="fcd1e-134">One of the most basic projects in Visual Studio is the Console Application.</span></span>  <span data-ttu-id="fcd1e-135">Voici comment faire.</span><span class="sxs-lookup"><span data-stu-id="fcd1e-135">Here's how to do it.</span></span>  <span data-ttu-id="fcd1e-136">Une fois Visual Studio ouvert :</span><span class="sxs-lookup"><span data-stu-id="fcd1e-136">Once Visual Studio is open:</span></span>

1. <span data-ttu-id="fcd1e-137">Sur le **fichier** menu, pointez sur **nouveau**, puis choisissez **projet**.</span><span class="sxs-lookup"><span data-stu-id="fcd1e-137">On the **File** menu, point to **New**, and then choose **Project**.</span></span>

2.  <span data-ttu-id="fcd1e-138">Dans le nouveau projet de boîte de dialogue, sous **modèles**, vous devez voir **Visual F #**.</span><span class="sxs-lookup"><span data-stu-id="fcd1e-138">In the New Project dialog, under **Templates**, you should see **Visual F#**.</span></span>  <span data-ttu-id="fcd1e-139">Choisissez cette option pour afficher les modèles F #.</span><span class="sxs-lookup"><span data-stu-id="fcd1e-139">Choose this to show the F# templates.</span></span>

3. <span data-ttu-id="fcd1e-140">Sélectionnez **.NET Core application Console** ou **application Console**.</span><span class="sxs-lookup"><span data-stu-id="fcd1e-140">Select either **.NET Core Console app** or **Console app**.</span></span>

3. <span data-ttu-id="fcd1e-141">Choisissez le **OK** bouton permettant de créer le projet F # !</span><span class="sxs-lookup"><span data-stu-id="fcd1e-141">Choose the **Okay** button to create the F# project!</span></span>  <span data-ttu-id="fcd1e-142">Vous devez maintenant voir un projet F # dans l’Explorateur de solutions.</span><span class="sxs-lookup"><span data-stu-id="fcd1e-142">You should now see an F# project in the Solution Explorer.</span></span>

## <a name="writing-your-code"></a><span data-ttu-id="fcd1e-143">L’écriture de votre code.</span><span class="sxs-lookup"><span data-stu-id="fcd1e-143">Writing your code</span></span>

<span data-ttu-id="fcd1e-144">Nous pouvons commencer à écrire du code tout d’abord.</span><span class="sxs-lookup"><span data-stu-id="fcd1e-144">Let's get started by writing some code first.</span></span>  <span data-ttu-id="fcd1e-145">Assurez-vous que le `Program.fs` fichier est ouvert, puis remplacez son contenu par les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="fcd1e-145">Make sure that the `Program.fs` file is open, and then replace its contents with the following:</span></span>

[!code-fsharp[HelloSquare](../../../samples/snippets/fsharp/getting-started/hello-square.fs)]

<span data-ttu-id="fcd1e-146">Dans l’exemple de code précédent, une fonction `square` a été défini qui accepte une entrée nommée `x` et multiplie par lui-même.</span><span class="sxs-lookup"><span data-stu-id="fcd1e-146">In the previous code sample, a function `square` has been defined which takes an input named `x` and multiplies it by itself.</span></span>  <span data-ttu-id="fcd1e-147">Étant donné que F # utilise [l’inférence de Type](../language-reference/type-inference.md), le type de `x` n’a pas besoin d’être spécifiés.</span><span class="sxs-lookup"><span data-stu-id="fcd1e-147">Because F# uses [Type Inference](../language-reference/type-inference.md), the type of `x` doesn't need to be specified.</span></span>  <span data-ttu-id="fcd1e-148">Le compilateur F # comprend les types où la multiplication est valide et affectera un type à `x` selon la façon dont `square` est appelée.</span><span class="sxs-lookup"><span data-stu-id="fcd1e-148">The F# compiler understands the types where multiplication is valid, and will assign a type to `x` based on how `square` is called.</span></span>  <span data-ttu-id="fcd1e-149">Si vous pointez sur `square`, vous devez voir les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="fcd1e-149">If you hover over `square`, you should see the following:</span></span>

```
val square: x:int -> int
```

<span data-ttu-id="fcd1e-150">C’est ce que l'on appelle la signature de type de la fonction.</span><span class="sxs-lookup"><span data-stu-id="fcd1e-150">This is what is known as the function's type signature.</span></span>  <span data-ttu-id="fcd1e-151">Il peut être lu comme suit : « carrée est une fonction qui accepte un entier nommé x et produit un entier ».</span><span class="sxs-lookup"><span data-stu-id="fcd1e-151">It can be read like this: "Square is a function which takes an integer named x and produces an integer".</span></span>  <span data-ttu-id="fcd1e-152">Notez que le compilateur a donné `square` le `int` type pour le moment - il s’agit, car la multiplication n’est pas générique sur *tous les* types, mais plutôt générique entre un ensemble fermé de types.</span><span class="sxs-lookup"><span data-stu-id="fcd1e-152">Note that the compiler gave `square` the `int` type for now - this is because multiplication is not generic across *all* types, but rather is generic across a closed set of types.</span></span>  <span data-ttu-id="fcd1e-153">Le compilateur F # prélevé `int` sur ce point, mais il ajuste la signature de type si vous appelez `square` avec un autre type d’entrée, comme un `float`.</span><span class="sxs-lookup"><span data-stu-id="fcd1e-153">The F# compiler picked `int` at this point, but it will adjust the type signature if you call `square` with a different input type, such as a `float`.</span></span>

<span data-ttu-id="fcd1e-154">Une autre fonction, `main`, est défini, ce qui est décoré avec le `EntryPoint` attribut pour indiquer au compilateur F # que l’exécution du programme doit commencer de là.</span><span class="sxs-lookup"><span data-stu-id="fcd1e-154">Another function, `main`, is defined, which is decorated with the `EntryPoint` attribute to tell the F# compiler that program execution should start there.</span></span>  <span data-ttu-id="fcd1e-155">Il suit la même convention que les autres [les langages de programmation de style C](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), où les arguments de ligne de commande peuvent être passés à cette fonction, et un code d’entier est retourné (généralement `0`).</span><span class="sxs-lookup"><span data-stu-id="fcd1e-155">It follows the same convention as other [C-style programming languages](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), where command-line arguments can be passed to this function, and an integer code is returned (typically `0`).</span></span>

<span data-ttu-id="fcd1e-156">Il se trouve dans cette fonction que nous appelons le `square` fonction avec un argument de `12`.</span><span class="sxs-lookup"><span data-stu-id="fcd1e-156">It is in this function that we call the `square` function with an argument of `12`.</span></span>  <span data-ttu-id="fcd1e-157">Le compilateur F # puis assigne le type de `square` être `int -> int` (autrement dit, une fonction qui prend un `int` et produit un `int`).</span><span class="sxs-lookup"><span data-stu-id="fcd1e-157">The F# compiler then assigns the type of `square` to be `int -> int` (that is, a function which takes an `int` and produces an `int`).</span></span>  <span data-ttu-id="fcd1e-158">L’appel à `printfn` est une fonction d’impression mis en forme qui utilise une chaîne de format, semblable aux langages de programmation de style C, les paramètres qui correspondent à celles spécifiées dans la chaîne de format, puis imprime le résultat et une nouvelle ligne.</span><span class="sxs-lookup"><span data-stu-id="fcd1e-158">The call to `printfn` is a formatted printing function which uses a format string, similar to C-style programming languages, parameters which correspond to those specified in the format string, and then prints the result and a new line.</span></span>

## <a name="running-your-code"></a><span data-ttu-id="fcd1e-159">Exécution de votre code</span><span class="sxs-lookup"><span data-stu-id="fcd1e-159">Running your code</span></span>

<span data-ttu-id="fcd1e-160">Vous pouvez exécuter le code et afficher les résultats en appuyant sur **ctrl-f5**.</span><span class="sxs-lookup"><span data-stu-id="fcd1e-160">You can run the code and see results by pressing **ctrl-f5**.</span></span>  <span data-ttu-id="fcd1e-161">Il exécute le programme sans débogage et vous permet de voir les résultats.</span><span class="sxs-lookup"><span data-stu-id="fcd1e-161">This will run the program without debugging and allows you to see the results.</span></span>  <span data-ttu-id="fcd1e-162">Vous pouvez également choisir la **déboguer** menu de niveau supérieur d’élément dans Visual Studio et choisissez **démarrer sans débogage**.</span><span class="sxs-lookup"><span data-stu-id="fcd1e-162">Alternatively, you can choose the **Debug** top-level menu item in Visual Studio and choose **Start Without Debugging**.</span></span>

<span data-ttu-id="fcd1e-163">Vous devez maintenant voir ce qui suit imprimé dans la fenêtre de console Visual Studio de s’afficher :</span><span class="sxs-lookup"><span data-stu-id="fcd1e-163">You should now see the following printed to the console window that Visual Studio popped up:</span></span>

```
12 squared is 144!
```

<span data-ttu-id="fcd1e-164">Félicitations !</span><span class="sxs-lookup"><span data-stu-id="fcd1e-164">Congratulations!</span></span>  <span data-ttu-id="fcd1e-165">Vous avez créé votre premier projet F # dans Visual Studio, écrit qu'une fonction) (F # imprimer les résultats de l’appel de cette fonction et exécutez le projet pour afficher certains résultats.</span><span class="sxs-lookup"><span data-stu-id="fcd1e-165">You've created your first F# project in Visual Studio, written an F# function printed the results of calling that function, and run the project to see some results.</span></span>

## <a name="using-f-interactive"></a><span data-ttu-id="fcd1e-166">À l’aide de F # Interactive</span><span class="sxs-lookup"><span data-stu-id="fcd1e-166">Using F# Interactive</span></span>

<span data-ttu-id="fcd1e-167">L’une des meilleures fonctionnalités de la Visual F # pour les outils dans Visual Studio est la fenêtre F # Interactive.</span><span class="sxs-lookup"><span data-stu-id="fcd1e-167">One of the best features of the Visual F# tooling in Visual Studio is the F# Interactive Window.</span></span>  <span data-ttu-id="fcd1e-168">Il vous permet d’envoyer le code sur un processus dans lequel vous pouvez appeler ce code et afficher le résultat de manière interactive.</span><span class="sxs-lookup"><span data-stu-id="fcd1e-168">It allows you to send code over to a process where you can call that code and see the result interactively.</span></span>

<span data-ttu-id="fcd1e-169">Pour commencer à l’utiliser, mettez en surbrillance le `square` fonction définie dans votre code.</span><span class="sxs-lookup"><span data-stu-id="fcd1e-169">To begin using it, highlight the `square` function defined in your code.</span></span>  <span data-ttu-id="fcd1e-170">Ensuite, maintenez la **Alt** clé et appuyez sur **entrée**.</span><span class="sxs-lookup"><span data-stu-id="fcd1e-170">Next, hold the **Alt** key and press **Enter**.</span></span>  <span data-ttu-id="fcd1e-171">Il exécute le code dans la fenêtre F # Interactive.</span><span class="sxs-lookup"><span data-stu-id="fcd1e-171">This executes the code in the F# Interactive Window.</span></span>  <span data-ttu-id="fcd1e-172">Vous devriez voir la fenêtre F # Interactive par le code suivant dans celui-ci :</span><span class="sxs-lookup"><span data-stu-id="fcd1e-172">You should see the F# Interactive Window appear with the following in it:</span></span>

```
>

val square : x:int -> int

>
```

<span data-ttu-id="fcd1e-173">Cela montre la même signature de fonction pour le `square` (fonction), vous l’avez vu précédemment lorsque vous pointez sur la fonction.</span><span class="sxs-lookup"><span data-stu-id="fcd1e-173">This shows the same function signature for the `square` function, which you saw earlier when you hovered over the function.</span></span>  <span data-ttu-id="fcd1e-174">Étant donné que `square` est maintenant défini dans le processus interactif F #, vous pouvez l’appeler avec des valeurs différentes :</span><span class="sxs-lookup"><span data-stu-id="fcd1e-174">Because `square` is now defined in the F# Interactive process, you can call it with different values:</span></span>

```
> square 12;;
val it : int = 144
>square 13;;
val it : int = 169
```

<span data-ttu-id="fcd1e-175">Cela exécute la fonction, lie le résultat à un nouveau nom `it`et affiche le type et la valeur de `it`.</span><span class="sxs-lookup"><span data-stu-id="fcd1e-175">This executes the function, binds the result to a new name `it`, and displays the type and value of `it`.</span></span>  <span data-ttu-id="fcd1e-176">Notez que vous devez mettre fin à chaque ligne avec `;;`.</span><span class="sxs-lookup"><span data-stu-id="fcd1e-176">Note that you must terminate each line with `;;`.</span></span>  <span data-ttu-id="fcd1e-177">Voici comment F # Interactive sait quand votre appel de fonction est terminée.</span><span class="sxs-lookup"><span data-stu-id="fcd1e-177">This is how F# Interactive knows when your function call is finished.</span></span>  <span data-ttu-id="fcd1e-178">Vous pouvez également définir de nouvelles fonctions dans F # Interactive :</span><span class="sxs-lookup"><span data-stu-id="fcd1e-178">You can also define new functions in F# Interactive:</span></span>

```
> let isOdd x = x % 2 <> 0;;

val isOdd : x:int -> bool

> isOdd 12;;
val it : bool = false
```

<span data-ttu-id="fcd1e-179">Ci-dessus définit une nouvelle fonction, `isOdd`, qui prend un `int` et vérifie s’il est impair !</span><span class="sxs-lookup"><span data-stu-id="fcd1e-179">The above defines a new function, `isOdd`, which takes an `int` and checks to see if it's odd!</span></span> <span data-ttu-id="fcd1e-180">Vous pouvez appeler cette fonction pour afficher sa valeur de retour avec des entrées différentes.</span><span class="sxs-lookup"><span data-stu-id="fcd1e-180">You can call this function to see what it returns with different inputs.</span></span>  <span data-ttu-id="fcd1e-181">Vous pouvez appeler des fonctions dans les appels de fonction :</span><span class="sxs-lookup"><span data-stu-id="fcd1e-181">You can call functions within function calls:</span></span>

```
> isOdd (square 15);;
val it : bool = true
```

<span data-ttu-id="fcd1e-182">Vous pouvez également utiliser le [avant de canal opérateur](../language-reference/symbol-and-operator-reference/index.md) à la valeur de pipeline dans les deux fonctions :</span><span class="sxs-lookup"><span data-stu-id="fcd1e-182">You can also use the [pipe-forward operator](../language-reference/symbol-and-operator-reference/index.md) to pipeline the value into the two functions:</span></span>

```
> 15 |> square |> isOdd;;
val it : bool = true
```

<span data-ttu-id="fcd1e-183">L’opérateur avant de canal et bien plus encore, sont traités dans des didacticiels ultérieurs.</span><span class="sxs-lookup"><span data-stu-id="fcd1e-183">The pipe-forward operator, and more, are covered in later tutorials.</span></span>

<span data-ttu-id="fcd1e-184">Il s’agit uniquement d’un aperçu en ce que vous pouvez faire avec F # Interactive.</span><span class="sxs-lookup"><span data-stu-id="fcd1e-184">This is only a glimpse into what you can do with F# Interactive.</span></span> <span data-ttu-id="fcd1e-185">Pour plus d’informations, consultez [de programmation Interactive avec F #](../tutorials/fsharp-interactive/index.md).</span><span class="sxs-lookup"><span data-stu-id="fcd1e-185">To learn more, check out [Interactive Programming with F#](../tutorials/fsharp-interactive/index.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="fcd1e-186">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="fcd1e-186">Next steps</span></span>

<span data-ttu-id="fcd1e-187">Si vous n’avez pas encore, consultez le [visite guidée de F #](../tour.md), qui traite de certaines fonctionnalités de base du langage F #.</span><span class="sxs-lookup"><span data-stu-id="fcd1e-187">If you haven't already, check out the [Tour of F#](../tour.md), which covers some of the core features of the F# language.</span></span>  <span data-ttu-id="fcd1e-188">Il vous donner une vue d’ensemble de certaines des fonctionnalités de F # et fournissent des exemples de code suffisamment que vous pouvez copier dans Visual Studio et exécuter.</span><span class="sxs-lookup"><span data-stu-id="fcd1e-188">It will give you an overview of some of the capabilities of F#, and provide ample code samples that you can copy into Visual Studio and run.</span></span>  <span data-ttu-id="fcd1e-189">Il existe également des ressources utiles externes, vous pouvez utiliser, a dans le [Guide F #](../index.md).</span><span class="sxs-lookup"><span data-stu-id="fcd1e-189">There are also some great external resources you can use, showcased in the [F# Guide](../index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="fcd1e-190">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fcd1e-190">See also</span></span>
 [<span data-ttu-id="fcd1e-191">Visual F#</span><span class="sxs-lookup"><span data-stu-id="fcd1e-191">Visual F#</span></span>](index.md)  
 [<span data-ttu-id="fcd1e-192">Présentation de F#</span><span class="sxs-lookup"><span data-stu-id="fcd1e-192">Tour of F#</span></span>](../tour.md)  
 [<span data-ttu-id="fcd1e-193">Référence du langage F #</span><span class="sxs-lookup"><span data-stu-id="fcd1e-193">F# language reference</span></span>](../language-reference/index.md)  
 [<span data-ttu-id="fcd1e-194">Inférence de type</span><span class="sxs-lookup"><span data-stu-id="fcd1e-194">Type inference</span></span>](../language-reference/type-inference.md)  
 [<span data-ttu-id="fcd1e-195">Référence des symboles et l’opérateur</span><span class="sxs-lookup"><span data-stu-id="fcd1e-195">Symbol and operator reference</span></span>](../language-reference/symbol-and-operator-reference/index.md)  
