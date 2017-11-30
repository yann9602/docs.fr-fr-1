---
title: "Exceptions : expression try...with (F#)"
description: "Découvrez comment utiliser l’expression F # 'try... with' pour la gestion des exceptions."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 36721076-95cd-4636-ae43-79dd512bee6c
ms.openlocfilehash: 163dfab49d4aaf23123800246fae2cad33e2257c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="exceptions-the-trywith-expression"></a><span data-ttu-id="165d9-104">Exceptions : expression try...with</span><span class="sxs-lookup"><span data-stu-id="165d9-104">Exceptions: The try...with Expression</span></span>

<span data-ttu-id="165d9-105">Cette rubrique décrit la `try...with` expression, l’expression qui est utilisée pour la gestion des exceptions dans le langage F #.</span><span class="sxs-lookup"><span data-stu-id="165d9-105">This topic describes the `try...with` expression, the expression that is used for exception handling in the F# language.</span></span>


## <a name="syntax"></a><span data-ttu-id="165d9-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="165d9-106">Syntax</span></span>

```fsharp
try
    expression1
with
| pattern1 -> expression2
| pattern2 -> expression3
...
```

## <a name="remarks"></a><span data-ttu-id="165d9-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="165d9-107">Remarks</span></span>
<span data-ttu-id="165d9-108">Le `try...with` expression est utilisée pour gérer les exceptions en F #.</span><span class="sxs-lookup"><span data-stu-id="165d9-108">The `try...with` expression is used to handle exceptions in F#.</span></span> <span data-ttu-id="165d9-109">Il est similaire à la `try...catch` instruction en langage c#.</span><span class="sxs-lookup"><span data-stu-id="165d9-109">It is similar to the `try...catch` statement in C#.</span></span> <span data-ttu-id="165d9-110">Dans la syntaxe précédente, le code dans *expression1* peut générer une exception.</span><span class="sxs-lookup"><span data-stu-id="165d9-110">In the preceding syntax, the code in *expression1* might generate an exception.</span></span> <span data-ttu-id="165d9-111">Le `try...with` expression retourne une valeur.</span><span class="sxs-lookup"><span data-stu-id="165d9-111">The `try...with` expression returns a value.</span></span> <span data-ttu-id="165d9-112">Si aucune exception n’est levée, l’expression entière retourne la valeur de *expression1*.</span><span class="sxs-lookup"><span data-stu-id="165d9-112">If no exception is thrown, the whole expression returns the value of *expression1*.</span></span> <span data-ttu-id="165d9-113">Si une exception est levée, chaque *modèle* est ensuite comparé avec l’exception et pour le premier modèle correspondant, correspondant *expression*, appelé le *Gestionnaire d’exceptions*, pour cette branche est exécutée, et l’expression globale retourne la valeur de l’expression dans ce gestionnaire d’exceptions.</span><span class="sxs-lookup"><span data-stu-id="165d9-113">If an exception is thrown, each *pattern* is compared in turn with the exception, and for the first matching pattern, the corresponding *expression*, known as the *exception handler*, for that branch is executed, and the overall expression returns the value of the expression in that exception handler.</span></span> <span data-ttu-id="165d9-114">Si aucun modèle ne correspond, l’exception se propage la pile des appels jusqu'à ce qu’un gestionnaire correspondant est trouvé.</span><span class="sxs-lookup"><span data-stu-id="165d9-114">If no pattern matches, the exception propagates up the call stack until a matching handler is found.</span></span> <span data-ttu-id="165d9-115">Les types des valeurs retournées de chaque expression dans les gestionnaires d’exceptions doivent correspondre au type retourné de l’expression dans le `try` bloc.</span><span class="sxs-lookup"><span data-stu-id="165d9-115">The types of the values returned from each expression in the exception handlers must match the type returned from the expression in the `try` block.</span></span>

<span data-ttu-id="165d9-116">Souvent, le fait qu’une erreur s’est produite également signifie qu’il n’existe aucune valeur valide pouvant être renvoyées par les expressions dans chaque gestionnaire d’exceptions.</span><span class="sxs-lookup"><span data-stu-id="165d9-116">Frequently, the fact that an error occurred also means that there is no valid value that can be returned from the expressions in each exception handler.</span></span> <span data-ttu-id="165d9-117">Un modèle fréquent consiste à avoir le type de l’expression à être un type d’option.</span><span class="sxs-lookup"><span data-stu-id="165d9-117">A frequent pattern is to have the type of the expression be an option type.</span></span> <span data-ttu-id="165d9-118">L’exemple de code suivant illustre ce modèle.</span><span class="sxs-lookup"><span data-stu-id="165d9-118">The following code example illustrates this pattern.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5601.fs)]

<span data-ttu-id="165d9-119">Les exceptions peuvent être des exceptions .NET, ou ils peuvent être des exceptions F #.</span><span class="sxs-lookup"><span data-stu-id="165d9-119">Exceptions can be .NET exceptions, or they can be F# exceptions.</span></span> <span data-ttu-id="165d9-120">Vous pouvez définir des exceptions F # à l’aide de la `exception` (mot clé).</span><span class="sxs-lookup"><span data-stu-id="165d9-120">You can define F# exceptions by using the `exception` keyword.</span></span>

<span data-ttu-id="165d9-121">Vous pouvez utiliser divers modèles de filtrer sur le type d’exception et d’autres conditions ; les options sont résumées dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="165d9-121">You can use a variety of patterns to filter on the exception type and other conditions; the options are summarized in the following table.</span></span>


|<span data-ttu-id="165d9-122">Modèle</span><span class="sxs-lookup"><span data-stu-id="165d9-122">Pattern</span></span>|<span data-ttu-id="165d9-123">Description</span><span class="sxs-lookup"><span data-stu-id="165d9-123">Description</span></span>|
|-------|-----------|
|<span data-ttu-id="165d9-124">:?</span><span class="sxs-lookup"><span data-stu-id="165d9-124">:?</span></span> <span data-ttu-id="165d9-125">*type d’exception*</span><span class="sxs-lookup"><span data-stu-id="165d9-125">*exception-type*</span></span>|<span data-ttu-id="165d9-126">Correspond au type d’exception .NET spécifié.</span><span class="sxs-lookup"><span data-stu-id="165d9-126">Matches the specified .NET exception type.</span></span>|
|<span data-ttu-id="165d9-127">:?</span><span class="sxs-lookup"><span data-stu-id="165d9-127">:?</span></span> <span data-ttu-id="165d9-128">*type d’exception* comme *identificateur*</span><span class="sxs-lookup"><span data-stu-id="165d9-128">*exception-type* as *identifier*</span></span>|<span data-ttu-id="165d9-129">Correspond au type d’exception .NET spécifié, mais donne une valeur nommée à l’exception.</span><span class="sxs-lookup"><span data-stu-id="165d9-129">Matches the specified .NET exception type, but gives the exception a named value.</span></span>|
|<span data-ttu-id="165d9-130">*nom de l’exception*(*arguments*)</span><span class="sxs-lookup"><span data-stu-id="165d9-130">*exception-name*(*arguments*)</span></span>|<span data-ttu-id="165d9-131">Correspond à un type d’exception F # et lie les arguments.</span><span class="sxs-lookup"><span data-stu-id="165d9-131">Matches an F# exception type and binds the arguments.</span></span>|
|<span data-ttu-id="165d9-132">*identifier*</span><span class="sxs-lookup"><span data-stu-id="165d9-132">*identifier*</span></span>|<span data-ttu-id="165d9-133">Correspond à n’importe quelle exception et lie le nom à l’objet exception.</span><span class="sxs-lookup"><span data-stu-id="165d9-133">Matches any exception and binds the name to the exception object.</span></span> <span data-ttu-id="165d9-134">Équivalent à **: ? System.Exception comme***identificateur*</span><span class="sxs-lookup"><span data-stu-id="165d9-134">Equivalent to **:? System.Exception as***identifier*</span></span>|
|<span data-ttu-id="165d9-135">*identificateur* lorsque *condition*</span><span class="sxs-lookup"><span data-stu-id="165d9-135">*identifier* when *condition*</span></span>|<span data-ttu-id="165d9-136">Correspond à une exception si la condition est true.</span><span class="sxs-lookup"><span data-stu-id="165d9-136">Matches any exception if the condition is true.</span></span>|

## <a name="examples"></a><span data-ttu-id="165d9-137">Exemples</span><span class="sxs-lookup"><span data-stu-id="165d9-137">Examples</span></span>
<span data-ttu-id="165d9-138">Les exemples de code suivants illustrent l’utilisation des divers modèles de gestionnaire d’exception.</span><span class="sxs-lookup"><span data-stu-id="165d9-138">The following code examples illustrate the use of the various exception handler patterns.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5602.fs)]
    
>[!NOTE] 
<span data-ttu-id="165d9-139">Le `try...with` construction est une expression séparée de la `try...finally` expression.</span><span class="sxs-lookup"><span data-stu-id="165d9-139">The `try...with` construct is a separate expression from the `try...finally` expression.</span></span> <span data-ttu-id="165d9-140">Par conséquent, si votre code requiert à la fois un `with` bloc et un `finally` bloc, vous devez imbriquer les deux expressions.</span><span class="sxs-lookup"><span data-stu-id="165d9-140">Therefore, if your code requires both a `with` block and a `finally` block, you will have to nest the two expressions.</span></span>

>[!NOTE] 
<span data-ttu-id="165d9-141">Vous pouvez utiliser `try...with` dans les workflows asynchrones et autres expressions de calcul, dans lequel cas une version personnalisée de la `try...with` expression est utilisée.</span><span class="sxs-lookup"><span data-stu-id="165d9-141">You can use `try...with` in asynchronous workflows and other computation expressions, in which case a customized version of the `try...with` expression is used.</span></span> <span data-ttu-id="165d9-142">Pour plus d’informations, consultez [Workflows asynchrones](../asynchronous-workflows.md), et [Expressions de calcul](../computation-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="165d9-142">For more information, see [Asynchronous Workflows](../asynchronous-workflows.md), and [Computation Expressions](../computation-expressions.md).</span></span>


## <a name="see-also"></a><span data-ttu-id="165d9-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="165d9-143">See Also</span></span>
[<span data-ttu-id="165d9-144">Gestion des exceptions</span><span class="sxs-lookup"><span data-stu-id="165d9-144">Exception Handling</span></span>](index.md)

[<span data-ttu-id="165d9-145">Types d'exceptions</span><span class="sxs-lookup"><span data-stu-id="165d9-145">Exception Types</span></span>](exception-types.md)

[<span data-ttu-id="165d9-146">Exceptions : expression `try...finally`</span><span class="sxs-lookup"><span data-stu-id="165d9-146">Exceptions: The `try...finally` Expression</span></span>](the-try-finally-expression.md)
