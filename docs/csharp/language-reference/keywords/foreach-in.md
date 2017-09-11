---
title: "foreach, in (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- foreach
- foreach_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- foreach keyword [C#]
- foreach statement [C#]
- in keyword [C#]
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
caps.latest.revision: 29
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
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: aed1d4f086f0b1334df750fd912d20d66326a043
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="foreach-in-c-reference"></a><span data-ttu-id="d2a31-102">foreach, in (référence C#)</span><span class="sxs-lookup"><span data-stu-id="d2a31-102">foreach, in (C# Reference)</span></span>
<span data-ttu-id="d2a31-103">L’instruction `foreach` répète un groupe d’instructions incorporées pour chaque élément d’un tableau ou d’une collection d’objets qui implémente l’interface <xref:System.Collections.IEnumerable?displayProperty=fullName> ou <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="d2a31-103">The `foreach` statement repeats a group of embedded statements for each element in an array or an object collection that implements the <xref:System.Collections.IEnumerable?displayProperty=fullName> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName> interface.</span></span> <span data-ttu-id="d2a31-104">L’instruction `foreach` est utilisée pour itérer la collection dans le but d’obtenir les informations dont vous avez besoin. Elle ne peut pas être utilisée pour ajouter ou supprimer des éléments de la collection source pour éviter des effets secondaires imprévisibles.</span><span class="sxs-lookup"><span data-stu-id="d2a31-104">The `foreach` statement is used to iterate through the collection to get the information that you want, but can not be used to add or remove items from the source collection to avoid unpredictable side effects.</span></span> <span data-ttu-id="d2a31-105">Si vous avez besoin d’ajouter ou de supprimer des éléments de la collection source, utilisez une boucle [for](../../../csharp/language-reference/keywords/for.md).</span><span class="sxs-lookup"><span data-stu-id="d2a31-105">If you need to add or remove items from the source collection, use a [for](../../../csharp/language-reference/keywords/for.md) loop.</span></span>  
  
 <span data-ttu-id="d2a31-106">Les instructions incorporées continuent de s’exécuter pour chaque élément de la collection ou du tableau.</span><span class="sxs-lookup"><span data-stu-id="d2a31-106">The embedded statements continue to execute for each element in the array or collection.</span></span> <span data-ttu-id="d2a31-107">Une fois l’itération terminée pour tous les éléments de la collection, le contrôle est transféré à l’instruction qui suit le bloc `foreach`.</span><span class="sxs-lookup"><span data-stu-id="d2a31-107">After the iteration has been completed for all the elements in the collection, control is transferred to the next statement following the `foreach` block.</span></span>  
  
 <span data-ttu-id="d2a31-108">Vous pouvez quitter la boucle à n’importe quel endroit du bloc `foreach` à l’aide du mot clé [break](../../../csharp/language-reference/keywords/break.md), ou passer à l’itération suivante de la boucle à l’aide du mot clé [continue](../../../csharp/language-reference/keywords/continue.md).</span><span class="sxs-lookup"><span data-stu-id="d2a31-108">At any point within the `foreach` block, you can break out of the loop by using the [break](../../../csharp/language-reference/keywords/break.md) keyword, or step to the next iteration in the loop by using the [continue](../../../csharp/language-reference/keywords/continue.md) keyword.</span></span>  
  
 <span data-ttu-id="d2a31-109">Une boucle `foreach` peut également être quittée à l’aide des instructions [goto](../../../csharp/language-reference/keywords/goto.md), [return](../../../csharp/language-reference/keywords/return.md) ou [throw](../../../csharp/language-reference/keywords/throw.md).</span><span class="sxs-lookup"><span data-stu-id="d2a31-109">A `foreach` loop can also be exited by the [goto](../../../csharp/language-reference/keywords/goto.md), [return](../../../csharp/language-reference/keywords/return.md), or [throw](../../../csharp/language-reference/keywords/throw.md) statements.</span></span>  
  
 <span data-ttu-id="d2a31-110">Pour plus d’informations sur le mot clé `foreach` et sur les exemples de code, consultez les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="d2a31-110">For more information about the `foreach` keyword and code samples, see the following topics:</span></span>  
  
 [<span data-ttu-id="d2a31-111">Utilisation de foreach avec des tableaux</span><span class="sxs-lookup"><span data-stu-id="d2a31-111">Using foreach with Arrays</span></span>](../../../csharp/programming-guide/arrays/using-foreach-with-arrays.md)  
  
 [<span data-ttu-id="d2a31-112">Guide pratique pour accéder à une classe de collection à l’aide de foreach</span><span class="sxs-lookup"><span data-stu-id="d2a31-112">How to: Access a Collection Class with foreach</span></span>](../../../csharp/programming-guide/classes-and-structs/how-to-access-a-collection-class-with-foreach.md)  
  
## <a name="example"></a><span data-ttu-id="d2a31-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="d2a31-113">Example</span></span>  
 <span data-ttu-id="d2a31-114">Le code suivant montre trois exemples :</span><span class="sxs-lookup"><span data-stu-id="d2a31-114">The following code shows three examples:</span></span>  
  
-   <span data-ttu-id="d2a31-115">Une boucle `foreach` typique qui affiche le contenu d’un tableau d’entiers</span><span class="sxs-lookup"><span data-stu-id="d2a31-115">a typical `foreach` loop that displays the contents of an array of integers</span></span>  
  
-   <span data-ttu-id="d2a31-116">Une boucle [for](../../../csharp/language-reference/keywords/for.md) qui fait la même chose</span><span class="sxs-lookup"><span data-stu-id="d2a31-116">a [for](../../../csharp/language-reference/keywords/for.md) loop that does the same thing</span></span>  
  
-   <span data-ttu-id="d2a31-117">Une boucle `foreach` qui compte le nombre d’éléments du tableau</span><span class="sxs-lookup"><span data-stu-id="d2a31-117">a `foreach` loop that maintains a count of the number of elements in the array</span></span>  
  
 <span data-ttu-id="d2a31-118">[!code-cs[csrefKeywordsIteration#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/foreach-in_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="d2a31-118">[!code-cs[csrefKeywordsIteration#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/foreach-in_1.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="d2a31-119">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="d2a31-119">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d2a31-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d2a31-120">See Also</span></span>  
 <span data-ttu-id="d2a31-121">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="d2a31-121">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="d2a31-122">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="d2a31-122">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="d2a31-123">[Mots clés C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="d2a31-123">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="d2a31-124">[Instructions d’itération](../../../csharp/language-reference/keywords/iteration-statements.md) </span><span class="sxs-lookup"><span data-stu-id="d2a31-124">[Iteration Statements](../../../csharp/language-reference/keywords/iteration-statements.md) </span></span>  
 [<span data-ttu-id="d2a31-125">for</span><span class="sxs-lookup"><span data-stu-id="d2a31-125">for</span></span>](../../../csharp/language-reference/keywords/for.md)

