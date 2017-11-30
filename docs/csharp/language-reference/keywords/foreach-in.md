---
title: "foreach, in (référence C#)"
ms.date: 10/11/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- foreach
- foreach_CSharpKeyword
helpviewer_keywords:
- foreach keyword [C#]
- foreach statement [C#]
- in keyword [C#]
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
caps.latest.revision: "29"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d5601682d53a01ff07aba7e416aa81ded4c03e4e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="foreach-in-c-reference"></a><span data-ttu-id="a179c-102">foreach, in (référence C#)</span><span class="sxs-lookup"><span data-stu-id="a179c-102">foreach, in (C# Reference)</span></span>
<span data-ttu-id="a179c-103">L’instruction `foreach` répète un groupe d’instructions incorporées pour chaque élément d’un tableau ou d’une collection d’objets qui implémente l’interface <xref:System.Collections.IEnumerable?displayProperty=nameWithType> ou <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a179c-103">The `foreach` statement repeats a group of embedded statements for each element in an array or an object collection that implements the <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="a179c-104">L’instruction `foreach` est utilisée pour itérer la collection dans le but d’obtenir les informations dont vous avez besoin. Elle ne peut pas être utilisée pour ajouter ou supprimer des éléments de la collection source pour éviter des effets secondaires imprévisibles.</span><span class="sxs-lookup"><span data-stu-id="a179c-104">The `foreach` statement is used to iterate through the collection to get the information that you want, but can not be used to add or remove items from the source collection to avoid unpredictable side effects.</span></span> <span data-ttu-id="a179c-105">Si vous avez besoin d’ajouter ou de supprimer des éléments de la collection source, utilisez une boucle [for](for.md).</span><span class="sxs-lookup"><span data-stu-id="a179c-105">If you need to add or remove items from the source collection, use a [for](for.md) loop.</span></span>
  
 <span data-ttu-id="a179c-106">Les instructions incorporées continuent de s’exécuter pour chaque élément de la collection ou du tableau.</span><span class="sxs-lookup"><span data-stu-id="a179c-106">The embedded statements continue to execute for each element in the array or collection.</span></span> <span data-ttu-id="a179c-107">Une fois l’itération terminée pour tous les éléments de la collection, le contrôle est transféré à l’instruction qui suit le bloc `foreach`.</span><span class="sxs-lookup"><span data-stu-id="a179c-107">After the iteration has been completed for all the elements in the collection, control is transferred to the next statement following the `foreach` block.</span></span>
  
 <span data-ttu-id="a179c-108">Vous pouvez quitter la boucle à n’importe quel endroit du bloc `foreach` à l’aide du mot clé [break](break.md), ou passer à l’itération suivante de la boucle à l’aide du mot clé [continue](continue.md).</span><span class="sxs-lookup"><span data-stu-id="a179c-108">At any point within the `foreach` block, you can break out of the loop by using the [break](break.md) keyword, or step to the next iteration in the loop by using the [continue](continue.md) keyword.</span></span>

 <span data-ttu-id="a179c-109">Une boucle `foreach` peut également être quittée à l’aide des instructions [goto](goto.md), [return](return.md) ou [throw](throw.md).</span><span class="sxs-lookup"><span data-stu-id="a179c-109">A `foreach` loop can also be exited by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

 <span data-ttu-id="a179c-110">Pour plus d’informations sur le mot clé `foreach` et sur les exemples de code, consultez les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="a179c-110">For more information about the `foreach` keyword and code samples, see the following topics:</span></span>  

 [<span data-ttu-id="a179c-111">Utilisation de foreach avec des tableaux</span><span class="sxs-lookup"><span data-stu-id="a179c-111">Using foreach with Arrays</span></span>](../../programming-guide/arrays/using-foreach-with-arrays.md)  

 [<span data-ttu-id="a179c-112">Guide pratique pour accéder à une classe de collection à l’aide de foreach</span><span class="sxs-lookup"><span data-stu-id="a179c-112">How to: Access a Collection Class with foreach</span></span>](../../programming-guide/classes-and-structs/how-to-access-a-collection-class-with-foreach.md)  

## <a name="example"></a><span data-ttu-id="a179c-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="a179c-113">Example</span></span>
 <span data-ttu-id="a179c-114">Le code suivant présente trois exemples.</span><span class="sxs-lookup"><span data-stu-id="a179c-114">The following code shows three examples.</span></span>

> [!TIP]
> <span data-ttu-id="a179c-115">Vous pouvez modifier les exemples pour faire des essais avec la syntaxe et essayez différentes utilisations qui ressemblent plus à votre cas d’usage.</span><span class="sxs-lookup"><span data-stu-id="a179c-115">You can modify the examples to experiment with the syntax and try different usages that are more similar to your use case.</span></span> <span data-ttu-id="a179c-116">Appuyez sur « Exécuter » pour exécuter le code, puis modifier et appuyez à nouveau sur « Exécuter ».</span><span class="sxs-lookup"><span data-stu-id="a179c-116">Press "Run" to run the code, then edit and press "Run" again.</span></span>

-   <span data-ttu-id="a179c-117">Une boucle `foreach` typique qui affiche le contenu d’un tableau d’entiers</span><span class="sxs-lookup"><span data-stu-id="a179c-117">a typical `foreach` loop that displays the contents of an array of integers</span></span>

[!code-csharp-interactive[csrefKeywordsIteration#4](./codesnippet/CSharp/foreach-in_1.cs#L12-L26)]

-   <span data-ttu-id="a179c-118">Une boucle [for](../../../csharp/language-reference/keywords/for.md) qui fait la même chose</span><span class="sxs-lookup"><span data-stu-id="a179c-118">a [for](../../../csharp/language-reference/keywords/for.md) loop that does the same thing</span></span>

[!code-csharp-interactive[csrefKeywordsIteration#4](./codesnippet/CSharp/foreach-in_1.cs#L31-L46)]

-   <span data-ttu-id="a179c-119">Une boucle `foreach` qui compte le nombre d’éléments du tableau</span><span class="sxs-lookup"><span data-stu-id="a179c-119">a `foreach` loop that maintains a count of the number of elements in the array</span></span>

[!code-csharp-interactive[csrefKeywordsIteration#4](./codesnippet/CSharp/foreach-in_1.cs#L51-L69)]
 
## <a name="c-language-specification"></a><span data-ttu-id="a179c-120">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="a179c-120">C# Language Specification</span></span>
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="a179c-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a179c-121">See Also</span></span>  

[<span data-ttu-id="a179c-122">Référence C#</span><span class="sxs-lookup"><span data-stu-id="a179c-122">C# Reference</span></span>](../index.md)

[<span data-ttu-id="a179c-123">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="a179c-123">C# Programming Guide</span></span>](../../programming-guide/index.md)

[<span data-ttu-id="a179c-124">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="a179c-124">C# Keywords</span></span>](index.md)

[<span data-ttu-id="a179c-125">Instructions d’itération</span><span class="sxs-lookup"><span data-stu-id="a179c-125">Iteration Statements</span></span>](iteration-statements.md)

[<span data-ttu-id="a179c-126">for</span><span class="sxs-lookup"><span data-stu-id="a179c-126">for</span></span>](for.md)
