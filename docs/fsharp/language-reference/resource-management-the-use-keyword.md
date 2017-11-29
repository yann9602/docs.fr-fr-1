---
title: "Gestion des ressources : mot clé « use » (F#)"
description: "Découvrez le F # mot-clé 'use' et la fonction « à l’aide », qui peut contrôler l’initialisation et la libération des ressources."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 00c3040e-859f-4dad-a7b5-7b8d44dc232c
ms.openlocfilehash: d4e8626f07f1c77e52e8fabd5ccc07dbf1fa8ddd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="resource-management-the-use-keyword"></a><span data-ttu-id="8f119-104">Gestion des ressources : mot clé « use »</span><span class="sxs-lookup"><span data-stu-id="8f119-104">Resource Management: The use Keyword</span></span>

<span data-ttu-id="8f119-105">Cette rubrique décrit le mot clé `use` et `using` (fonction), qui peut contrôler l’initialisation et la libération de ressources.</span><span class="sxs-lookup"><span data-stu-id="8f119-105">This topic describes the keyword `use` and the `using` function, which can control the initialization and release of resources.</span></span>

## <a name="resources"></a><span data-ttu-id="8f119-106">Ressources</span><span class="sxs-lookup"><span data-stu-id="8f119-106">Resources</span></span>
<span data-ttu-id="8f119-107">Le terme *ressource* est utilisé dans plusieurs façons.</span><span class="sxs-lookup"><span data-stu-id="8f119-107">The term *resource* is used in more than one way.</span></span> <span data-ttu-id="8f119-108">Oui, les ressources peuvent être des données qu’une application utilise, tels que des chaînes, des graphiques et autres, mais dans ce contexte, *ressources* fait référence aux ressources de système d’exploitation ou des logiciels, tels que les contextes de périphérique de graphiques, des descripteurs de fichiers, réseau base de données et les connexions, les objets d’accès concurrentiel tels que les handles d’attente et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="8f119-108">Yes, resources can be data that an application uses, such as strings, graphics, and the like, but in this context, *resources* refers to software or operating system resources, such as graphics device contexts, file handles, network and database connections, concurrency objects such as wait handles, and so on.</span></span> <span data-ttu-id="8f119-109">L’utilisation de ces ressources par les applications implique l’acquisition de la ressource à partir du système d’exploitation ou d’autre fournisseur de ressources, suivie de la libération de la ressource pour le pool afin qu’il peut être fourni à une autre application.</span><span class="sxs-lookup"><span data-stu-id="8f119-109">The use of these resources by applications involves the acquisition of the resource from the operating system or other resource provider, followed by the later release of the resource to the pool so that it can be provided to another application.</span></span> <span data-ttu-id="8f119-110">Des problèmes se produisent lorsque les applications ne libèrent pas de ressources vers le pool commun.</span><span class="sxs-lookup"><span data-stu-id="8f119-110">Problems occur when applications do not release resources back to the common pool.</span></span>

## <a name="managing-resources"></a><span data-ttu-id="8f119-111">Gestion des ressources</span><span class="sxs-lookup"><span data-stu-id="8f119-111">Managing Resources</span></span>
<span data-ttu-id="8f119-112">Pour gérer efficacement et de façon responsable les ressources dans une application, vous devez libérer les ressources rapidement et de manière prévisible.</span><span class="sxs-lookup"><span data-stu-id="8f119-112">To efficiently and responsibly manage resources in an application, you must release resources promptly and in a predictable manner.</span></span> <span data-ttu-id="8f119-113">Le .NET Framework vous permet de faire cela en fournissant le `System.IDisposable` interface.</span><span class="sxs-lookup"><span data-stu-id="8f119-113">The .NET Framework helps you do this by providing the `System.IDisposable` interface.</span></span> <span data-ttu-id="8f119-114">Un type qui implémente `System.IDisposable` a le `System.IDisposable.Dispose` (méthode), ce qui libère les ressources correctement.</span><span class="sxs-lookup"><span data-stu-id="8f119-114">A type that implements `System.IDisposable` has the `System.IDisposable.Dispose` method, which correctly frees resources.</span></span> <span data-ttu-id="8f119-115">Applications bien écrites garantissent que `System.IDisposable.Dispose` est appelé rapidement lorsqu’un objet qui contient une ressource limitée n’est plus nécessaire.</span><span class="sxs-lookup"><span data-stu-id="8f119-115">Well-written applications guarantee that `System.IDisposable.Dispose` is called promptly when any object that holds a limited resource is no longer needed.</span></span> <span data-ttu-id="8f119-116">Heureusement, la plupart des langages .NET fournissent la prise en charge pour ce faire, et F # ne fait pas exception.</span><span class="sxs-lookup"><span data-stu-id="8f119-116">Fortunately, most .NET languages provide support to make this easier, and F# is no exception.</span></span> <span data-ttu-id="8f119-117">Il existe deux constructions de langage utiles qui prennent en charge le modèle de suppression : le `use` liaison et la `using` (fonction).</span><span class="sxs-lookup"><span data-stu-id="8f119-117">There are two useful language constructs that support the dispose pattern: the `use` binding and the `using` function.</span></span>

## <a name="use-binding"></a><span data-ttu-id="8f119-118">Utilisez la liaison</span><span class="sxs-lookup"><span data-stu-id="8f119-118">use Binding</span></span>
<span data-ttu-id="8f119-119">Le `use` (mot clé) a un écran semblable à celle de la `let` liaison :</span><span class="sxs-lookup"><span data-stu-id="8f119-119">The `use` keyword has a form that resembles that of the `let` binding:</span></span>

<span data-ttu-id="8f119-120">Utilisez *valeur* = *expression*</span><span class="sxs-lookup"><span data-stu-id="8f119-120">use *value* = *expression*</span></span>

<span data-ttu-id="8f119-121">Il fournit les mêmes fonctionnalités qu’un `let` de liaison, mais ajoute un appel à `Dispose` sur la valeur lorsque la valeur est hors de portée.</span><span class="sxs-lookup"><span data-stu-id="8f119-121">It provides the same functionality as a `let` binding but adds a call to `Dispose` on the value when the value goes out of scope.</span></span> <span data-ttu-id="8f119-122">Notez que le compilateur insère un contrôle de valeur null sur la valeur, afin que si la valeur est `null`, l’appel à `Dispose` n’est pas tentée.</span><span class="sxs-lookup"><span data-stu-id="8f119-122">Note that the compiler inserts a null check on the value, so that if the value is `null`, the call to `Dispose` is not attempted.</span></span>

<span data-ttu-id="8f119-123">L’exemple suivant montre comment fermer automatiquement un fichier à l’aide de la `use` (mot clé).</span><span class="sxs-lookup"><span data-stu-id="8f119-123">The following example shows how to close a file automatically by using the `use` keyword.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6301.fs)]

>[!NOTE]
<span data-ttu-id="8f119-124">Vous pouvez utiliser `use` dans les expressions de calcul, auquel cas une version personnalisée de la `use` expression est utilisée.</span><span class="sxs-lookup"><span data-stu-id="8f119-124">You can use `use` in computation expressions, in which case a customized version of the `use` expression is used.</span></span> <span data-ttu-id="8f119-125">Pour plus d’informations, consultez [séquences](sequences.md), [Workflows asynchrones](asynchronous-workflows.md), et [Expressions de calcul](computation-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="8f119-125">For more information, see [Sequences](sequences.md), [Asynchronous Workflows](asynchronous-workflows.md), and [Computation Expressions](computation-expressions.md).</span></span>


## <a name="using-function"></a><span data-ttu-id="8f119-126">à l’aide de la fonction</span><span class="sxs-lookup"><span data-stu-id="8f119-126">using Function</span></span>
<span data-ttu-id="8f119-127">Le `using` fonction a la forme suivante :</span><span class="sxs-lookup"><span data-stu-id="8f119-127">The `using` function has the following form:</span></span>

<span data-ttu-id="8f119-128">`using`(*expression1*) *fonction ou expression lambda*</span><span class="sxs-lookup"><span data-stu-id="8f119-128">`using` (*expression1*) *function-or-lambda*</span></span>

<span data-ttu-id="8f119-129">Dans un `using` expression, *expression1* crée l’objet doit être supprimé.</span><span class="sxs-lookup"><span data-stu-id="8f119-129">In a `using` expression, *expression1* creates the object that must be disposed.</span></span> <span data-ttu-id="8f119-130">Le résultat de *expression1* (l’objet qui doit être supprimé) devienne un argument, *valeur*à *fonction ou lambda*, qui est soit une fonction qui attend un seul argument d’un type qui correspond à la valeur restant produits par *expression1*, ou une expression lambda qui attend un argument de ce type.</span><span class="sxs-lookup"><span data-stu-id="8f119-130">The result of *expression1* (the object that must be disposed) becomes an argument, *value*, to *function-or-lambda*, which is either a function that expects a single remaining argument of a type that matches the value produced by *expression1*, or a lambda expression that expects an argument of that type.</span></span> <span data-ttu-id="8f119-131">À la fin de l’exécution de la fonction, le runtime appelle `Dispose` et libère les ressources (sauf si la valeur est `null`, auquel cas l’appel à Dispose n’est pas tentée).</span><span class="sxs-lookup"><span data-stu-id="8f119-131">At the end of the execution of the function, the runtime calls `Dispose` and frees the resources (unless the value is `null`, in which case the call to Dispose is not attempted).</span></span>

<span data-ttu-id="8f119-132">L’exemple suivant illustre la `using` expression avec une expression lambda.</span><span class="sxs-lookup"><span data-stu-id="8f119-132">The following example demonstrates the `using` expression with a lambda expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6302.fs)]

<span data-ttu-id="8f119-133">L’exemple suivant montre la `using` expression avec une fonction.</span><span class="sxs-lookup"><span data-stu-id="8f119-133">The next example shows the `using` expression with a function.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6303.fs)]

<span data-ttu-id="8f119-134">Notez que la fonction peut être une fonction qui a des arguments déjà appliqués.</span><span class="sxs-lookup"><span data-stu-id="8f119-134">Note that the function could be a function that has some arguments applied already.</span></span> <span data-ttu-id="8f119-135">L’exemple de code suivant illustre cela.</span><span class="sxs-lookup"><span data-stu-id="8f119-135">The following code example demonstrates this.</span></span> <span data-ttu-id="8f119-136">Il crée un fichier qui contient la chaîne `XYZ`.</span><span class="sxs-lookup"><span data-stu-id="8f119-136">It creates a file that contains the string `XYZ`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6304.fs)]

<span data-ttu-id="8f119-137">Le `using` (fonction) et le `use` liaison sont de façon presque équivalente pour accomplir la même chose.</span><span class="sxs-lookup"><span data-stu-id="8f119-137">The `using` function and the `use` binding are nearly equivalent ways to accomplish the same thing.</span></span> <span data-ttu-id="8f119-138">Le `using` (mot clé) permet de contrôler quand `Dispose` est appelée.</span><span class="sxs-lookup"><span data-stu-id="8f119-138">The `using` keyword provides more control over when `Dispose` is called.</span></span> <span data-ttu-id="8f119-139">Lorsque vous utilisez `using`, `Dispose` est appelée à la fin de la fonction ou une expression lambda ; lorsque vous utilisez la `use` (mot clé), `Dispose` est appelée à la fin du bloc de code contenant.</span><span class="sxs-lookup"><span data-stu-id="8f119-139">When you use `using`, `Dispose` is called at the end of the function or lambda expression; when you use the `use` keyword, `Dispose` is called at the end of the containing code block.</span></span> <span data-ttu-id="8f119-140">En règle générale, vous préférez utiliser `use` au lieu du `using` (fonction).</span><span class="sxs-lookup"><span data-stu-id="8f119-140">In general, you should prefer to use `use` instead of the `using` function.</span></span>


## <a name="see-also"></a><span data-ttu-id="8f119-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8f119-141">See Also</span></span>
[<span data-ttu-id="8f119-142">Informations de référence du langage F#</span><span class="sxs-lookup"><span data-stu-id="8f119-142">F# Language Reference</span></span>](index.md)
