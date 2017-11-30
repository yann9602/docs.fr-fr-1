---
title: "Tableaux C# - Visite guidée du langage C#"
description: Les tableaux sont le type de collection le plus simple dans le langage c#
keywords: .NET, csharp, tableau, collection
author: BillWagner
ms.author: wiwagn
ms.date: 08/10/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: a440704c-9e88-4c75-97dd-bfe30ca0fb97
ms.openlocfilehash: d7d5ae9f99ba1629a6f0aec57bebf74853cab27f
ms.sourcegitcommit: a19548e5167cbe7e9e58df4ffd8c3b23f17d5c7a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/02/2017
---
# <a name="arrays"></a><span data-ttu-id="b9fed-104">Tableaux</span><span class="sxs-lookup"><span data-stu-id="b9fed-104">Arrays</span></span>

<span data-ttu-id="b9fed-105">Un ***tableau*** est une structure de données qui contient un certain nombre de variables qui sont accessibles par des indices calculés.</span><span class="sxs-lookup"><span data-stu-id="b9fed-105">An ***array*** is a data structure that contains a number of variables that are accessed through computed indices.</span></span> <span data-ttu-id="b9fed-106">Les variables contenues dans un tableau, également appelé ***éléments*** du tableau, sont tous du même type, et ce type est appelé ***type d’élément*** du tableau.</span><span class="sxs-lookup"><span data-stu-id="b9fed-106">The variables contained in an array, also called the ***elements*** of the array, are all of the same type, and this type is called the ***element type*** of the array.</span></span>

<span data-ttu-id="b9fed-107">Les types tableau sont des types référence, et la déclaration d’une variable tableau réserve simplement un espace pour une référence à une instance de tableau.</span><span class="sxs-lookup"><span data-stu-id="b9fed-107">Array types are reference types, and the declaration of an array variable simply sets aside space for a reference to an array instance.</span></span> <span data-ttu-id="b9fed-108">Les instances de tableau réelles sont créées dynamiquement lors de l’exécution à l’aide de l’opérateur new.</span><span class="sxs-lookup"><span data-stu-id="b9fed-108">Actual array instances are created dynamically at runtime using the new operator.</span></span> <span data-ttu-id="b9fed-109">La nouvelle opération spécifie la ***longueur*** de la nouvelle instance de tableau, qui est ensuite fixée pour la durée de vie de l’instance.</span><span class="sxs-lookup"><span data-stu-id="b9fed-109">The new operation specifies the ***length*** of the new array instance, which is then fixed for the lifetime of the instance.</span></span> <span data-ttu-id="b9fed-110">Les indices des éléments d’un tableau vont de `0` à `Length - 1`.</span><span class="sxs-lookup"><span data-stu-id="b9fed-110">The indices of the elements of an array range from `0` to `Length - 1`.</span></span> <span data-ttu-id="b9fed-111">L’opérateur `new` initialise automatiquement les éléments d’un tableau à leur valeur par défaut, c'est-à-dire, par exemple, zéro pour tous les types numériques et `null` pour tous les types référence.</span><span class="sxs-lookup"><span data-stu-id="b9fed-111">The `new` operator automatically initializes the elements of an array to their default value, which, for example, is zero for all numeric types and `null` for all reference types.</span></span>

<span data-ttu-id="b9fed-112">L’exemple suivant crée un tableau de `int` éléments, initialise le tableau et imprime le contenu du tableau.</span><span class="sxs-lookup"><span data-stu-id="b9fed-112">The following example creates an array of `int` elements, initializes the array, and prints out the contents of the array.</span></span>

[!code-csharp[ArraySample](../../../samples/snippets/csharp/tour/arrays/Program.cs#L3-L18)]

<span data-ttu-id="b9fed-113">Cet exemple crée et utilise un ***tableau unidimensionnel***.</span><span class="sxs-lookup"><span data-stu-id="b9fed-113">This example creates and operates on a ***single-dimensional array***.</span></span> <span data-ttu-id="b9fed-114">C# prend également en charge les ***tableaux multidimensionnels***.</span><span class="sxs-lookup"><span data-stu-id="b9fed-114">C# also supports ***multi-dimensional arrays***.</span></span> <span data-ttu-id="b9fed-115">Le nombre de dimensions d’un type tableau, également appelé ***rang*** du type tableau, est de un plus le nombre de virgules entre les crochets du type tableau.</span><span class="sxs-lookup"><span data-stu-id="b9fed-115">The number of dimensions of an array type, also known as the ***rank*** of the array type, is one plus the number of commas written between the square brackets of the array type.</span></span> <span data-ttu-id="b9fed-116">L’exemple suivant alloue respectivement des tableaux à une seule, deux et trois dimensions, respectivement.</span><span class="sxs-lookup"><span data-stu-id="b9fed-116">The following example allocates a single-dimensional, a two-dimensional, and a three-dimensional array, respectively.</span></span>

[!code-csharp[ArrayRank](../../../samples/snippets/csharp/tour/arrays/Program.cs#L24-L26)]

<span data-ttu-id="b9fed-117">Le tableau `a1` contient 10 éléments, le tableau `a2` en contient 50 (10 x 5) et le tableau `a3` en contient 100 (10 × 5 × 2).</span><span class="sxs-lookup"><span data-stu-id="b9fed-117">The `a1` array contains 10 elements, the `a2` array contains 50 (10 × 5) elements, and the `a3` array contains 100 (10 × 5 × 2) elements.</span></span>
<span data-ttu-id="b9fed-118">Le type d’élément d’un tableau peut être de n’importe quel type, y compris un type tableau.</span><span class="sxs-lookup"><span data-stu-id="b9fed-118">The element type of an array can be any type, including an array type.</span></span> <span data-ttu-id="b9fed-119">Un tableau avec des éléments d’un type tableau est parfois appelé un ***tableau en escalier***, car les longueurs des tableaux d’éléments ne sont pas nécessairement pas les mêmes.</span><span class="sxs-lookup"><span data-stu-id="b9fed-119">An array with elements of an array type is sometimes called a ***jagged array*** because the lengths of the element arrays do not all have to be the same.</span></span> <span data-ttu-id="b9fed-120">L’exemple suivant alloue un tableau de tableaux de `int` :</span><span class="sxs-lookup"><span data-stu-id="b9fed-120">The following example allocates an array of arrays of `int`:</span></span>

[!code-csharp[ArrayAllocation](../../../samples/snippets/csharp/tour/arrays/Program.cs#L31-L34)]

<span data-ttu-id="b9fed-121">La première ligne crée un tableau avec trois éléments, chacun de type `int[]` et chacun avec une valeur initiale de `null`.</span><span class="sxs-lookup"><span data-stu-id="b9fed-121">The first line creates an array with three elements, each of type `int[]` and each with an initial value of `null`.</span></span> <span data-ttu-id="b9fed-122">Les lignes suivantes initialisent ensuite les trois éléments avec des références aux instances individuelles de tableau de longueur variable.</span><span class="sxs-lookup"><span data-stu-id="b9fed-122">The subsequent lines then initialize the three elements with references to individual array instances of varying lengths.</span></span>

<span data-ttu-id="b9fed-123">L’opérateur new autorise la spécification des valeurs initiales des éléments du tableau en utilisant un ***initialiseur de tableau***, qui est une liste d’expressions écrites entre les délimiteurs `{` et `}`.</span><span class="sxs-lookup"><span data-stu-id="b9fed-123">The new operator permits the initial values of the array elements to be specified using an ***array initializer***, which is a list of expressions written between the delimiters `{` and `}`.</span></span> <span data-ttu-id="b9fed-124">L’exemple suivant alloue et initialise un `int[]` avec trois éléments.</span><span class="sxs-lookup"><span data-stu-id="b9fed-124">The following example allocates and initializes an `int[]` with three elements.</span></span>

[!code-csharp[ArrayInitialization](../../../samples/snippets/csharp/tour/arrays/Program.cs#L39-L39)]

<span data-ttu-id="b9fed-125">Notez que la longueur du tableau est déduite à partir du nombre d’expressions entre { et }.</span><span class="sxs-lookup"><span data-stu-id="b9fed-125">Note that the length of the array is inferred from the number of expressions between { and }.</span></span> <span data-ttu-id="b9fed-126">Les déclarations locales des champs et variables peuvent être abrégées davantage afin de ne pas avoir à redéclarer le type tableau.</span><span class="sxs-lookup"><span data-stu-id="b9fed-126">Local variable and field declarations can be shortened further such that the array type does not have to be restated.</span></span>

[!code-csharp[ArrayInitialization](../../../samples/snippets/csharp/tour/arrays/Program.cs#L44-L44)]

<span data-ttu-id="b9fed-127">Les deux exemples précédents sont équivalents à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="b9fed-127">Both of the previous examples are equivalent to the following:</span></span>

[!code-csharp[ArrayAssignment](../../../samples/snippets/csharp/tour/arrays/Program.cs#L49-L53)]

>[!div class="step-by-step"]
<span data-ttu-id="b9fed-128">[Précédent](structs.md)
[Suivant](interfaces.md)</span><span class="sxs-lookup"><span data-stu-id="b9fed-128">[Previous](structs.md)
[Next](interfaces.md)</span></span>
