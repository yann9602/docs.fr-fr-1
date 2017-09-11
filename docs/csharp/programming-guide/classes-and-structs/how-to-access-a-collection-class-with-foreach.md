---
title: "Guide pratique pour accéder à une classe de collection à l’aide de foreach (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- collection classes [C#], foreach statement
ms.assetid: a6b9cf5c-6c8d-4223-b12c-288949434493
caps.latest.revision: 21
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
ms.openlocfilehash: 2ad81ab699b079f4aabb04a886211e94a937335d
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-access-a-collection-class-with-foreach-c-programming-guide"></a><span data-ttu-id="53b4c-102">Guide pratique pour accéder à une classe de collection à l’aide de foreach (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="53b4c-102">How to: Access a Collection Class with foreach (C# Programming Guide)</span></span>
<span data-ttu-id="53b4c-103">L’exemple de code suivant montre comment écrire une classe de collection non générique qui peut être utilisée avec [foreach](../../../csharp/language-reference/keywords/foreach-in.md).</span><span class="sxs-lookup"><span data-stu-id="53b4c-103">The following code example illustrates how to write a non-generic collection class that can be used with [foreach](../../../csharp/language-reference/keywords/foreach-in.md).</span></span> <span data-ttu-id="53b4c-104">L’exemple définit une classe de générateurs de jetons de chaînes.</span><span class="sxs-lookup"><span data-stu-id="53b4c-104">The example defines a string tokenizer class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="53b4c-105">Cet exemple représente la méthode recommandée uniquement quand vous ne pouvez pas utiliser une classe de collection générique.</span><span class="sxs-lookup"><span data-stu-id="53b4c-105">This example represents recommended practice only when you cannot use a generic collection class.</span></span> <span data-ttu-id="53b4c-106">Pour obtenir un exemple montrant comment implémenter une classe de collection générique de type sécurisé qui prend en charge <xref:System.Collections.Generic.IEnumerable%601>, consultez [Itérateurs](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).</span><span class="sxs-lookup"><span data-stu-id="53b4c-106">For an example of how to implement a type-safe generic collection class that supports <xref:System.Collections.Generic.IEnumerable%601>, see [Iterators](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).</span></span>  
  
 <span data-ttu-id="53b4c-107">Dans l’exemple, le segment de code suivant utilise la classe `Tokens` pour décomposer la phrase « This is a sample sentence. »</span><span class="sxs-lookup"><span data-stu-id="53b4c-107">In the example, the following code segment uses the `Tokens` class to break the sentence "This is a sample sentence."</span></span> <span data-ttu-id="53b4c-108">en jetons en utilisant ' ' et '-' comme séparateurs.</span><span class="sxs-lookup"><span data-stu-id="53b4c-108">into tokens by using ' ' and '-' as separators.</span></span> <span data-ttu-id="53b4c-109">Le code affiche ensuite ces jetons à l’aide d’une instruction `foreach`.</span><span class="sxs-lookup"><span data-stu-id="53b4c-109">The code then displays those tokens by using a `foreach` statement.</span></span>  
  
 <span data-ttu-id="53b4c-110">[!code-cs[csProgGuideCollections#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-access-a-collection-class-with-foreach_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="53b4c-110">[!code-cs[csProgGuideCollections#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-access-a-collection-class-with-foreach_1.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="53b4c-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="53b4c-111">Example</span></span>  
 <span data-ttu-id="53b4c-112">En interne, la classe `Tokens` utilise un tableau pour stocker les jetons.</span><span class="sxs-lookup"><span data-stu-id="53b4c-112">Internally, the `Tokens` class uses an array to store the tokens.</span></span> <span data-ttu-id="53b4c-113">Étant donné que les tableaux implémentent <xref:System.Collections.IEnumerator> et <xref:System.Collections.IEnumerable>, l’exemple de code aurait pu utiliser les méthodes d’énumération du tableau (<xref:System.Collections.IEnumerable.GetEnumerator%2A>, <xref:System.Collections.IEnumerator.MoveNext%2A>, <xref:System.Collections.IEnumerator.Reset%2A> et <xref:System.Collections.IEnumerator.Current%2A>) au lieu de les définir dans la classe `Tokens`.</span><span class="sxs-lookup"><span data-stu-id="53b4c-113">Because arrays implement <xref:System.Collections.IEnumerator> and <xref:System.Collections.IEnumerable>, the code example could have used the array's enumeration methods (<xref:System.Collections.IEnumerable.GetEnumerator%2A>, <xref:System.Collections.IEnumerator.MoveNext%2A>, <xref:System.Collections.IEnumerator.Reset%2A>, and <xref:System.Collections.IEnumerator.Current%2A>) instead of defining them in the `Tokens` class.</span></span> <span data-ttu-id="53b4c-114">Les définitions de méthode sont incluses dans l’exemple pour clarifier la façon dont elles sont définies et ce que chacune d’elles fait.</span><span class="sxs-lookup"><span data-stu-id="53b4c-114">The method definitions are included in the example to clarify how they are defined and what each does.</span></span>  
  
 <span data-ttu-id="53b4c-115">[!code-cs[csProgGuideCollections#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-access-a-collection-class-with-foreach_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="53b4c-115">[!code-cs[csProgGuideCollections#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-access-a-collection-class-with-foreach_2.cs)]</span></span>  
  
 <span data-ttu-id="53b4c-116">En C#, une classe de collection n’est pas obligée d’implémenter <xref:System.Collections.IEnumerable> et <xref:System.Collections.IEnumerator> pour être compatible avec `foreach`.</span><span class="sxs-lookup"><span data-stu-id="53b4c-116">In C#, it is not necessary for a collection class to implement <xref:System.Collections.IEnumerable> and <xref:System.Collections.IEnumerator> to be compatible with `foreach`.</span></span> <span data-ttu-id="53b4c-117">Si la classe a les membres <xref:System.Collections.IEnumerable.GetEnumerator%2A>, <xref:System.Collections.IEnumerator.MoveNext%2A>, <xref:System.Collections.IEnumerator.Reset%2A> et <xref:System.Collections.IEnumerator.Current%2A> nécessaires, elle fonctionnera avec `foreach`.</span><span class="sxs-lookup"><span data-stu-id="53b4c-117">If the class has the required <xref:System.Collections.IEnumerable.GetEnumerator%2A>, <xref:System.Collections.IEnumerator.MoveNext%2A>, <xref:System.Collections.IEnumerator.Reset%2A>, and <xref:System.Collections.IEnumerator.Current%2A> members, it will work with `foreach`.</span></span> <span data-ttu-id="53b4c-118">L’omission des interfaces vous permet de définir un type de retour pour `Current` qui est plus spécifique qu’<xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="53b4c-118">Omitting the interfaces has the advantage of enabling you to define a return type for `Current` that is more specific than <xref:System.Object>.</span></span> <span data-ttu-id="53b4c-119">Cela garantit la sécurité de type.</span><span class="sxs-lookup"><span data-stu-id="53b4c-119">This provides type safety.</span></span>  
  
 <span data-ttu-id="53b4c-120">Par exemple, changez les lignes suivantes dans l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="53b4c-120">For example, change the following lines in the previous example.</span></span>  
  
```csharp  
// Change the Tokens class so that it no longer implements IEnumerable.  
public class Tokens  
{  
    // . . .  
  
    // Change the return type for the GetEnumerator method.  
    public TokenEnumerator GetEnumerator()  
    {   }  
  
    // Change TokenEnumerator so that it no longer implements IEnumerator.  
    public class TokenEnumerator  
    {  
        // . . .  
  
        // Change the return type of method Current to string.  
        public string Current  
        {   }  
    }  
 }  
```  
  
 <span data-ttu-id="53b4c-121">Étant donné que `Current` retourne une chaîne, le compilateur peut détecter quand un type incompatible est utilisé dans une instruction `foreach`, comme illustré dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="53b4c-121">Because `Current` returns a string, the compiler can detect when an incompatible type is used in a `foreach` statement, as shown in the following code.</span></span>  
  
```csharp  
// Error: Cannot convert type string to int.  
foreach (int item in f)    
```  
  
 <span data-ttu-id="53b4c-122">L’omission d’<xref:System.Collections.IEnumerable> et d’<xref:System.Collections.IEnumerator> a toutefois un inconvénient : la classe de collection n’est plus interopérable avec les instructions `foreach` (ou instructions équivalentes) d’autres langages du common language runtime.</span><span class="sxs-lookup"><span data-stu-id="53b4c-122">The disadvantage of omitting <xref:System.Collections.IEnumerable> and <xref:System.Collections.IEnumerator> is that the collection class is no longer interoperable with the `foreach` statements, or equivalent statements, of other common language runtime languages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53b4c-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="53b4c-123">See Also</span></span>  
 <span data-ttu-id="53b4c-124"><xref:System.Collections.Generic></span><span class="sxs-lookup"><span data-stu-id="53b4c-124"><xref:System.Collections.Generic></span></span>   
 <span data-ttu-id="53b4c-125">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="53b4c-125">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="53b4c-126">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="53b4c-126">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="53b4c-127">[Tableaux](../../../csharp/programming-guide/arrays/index.md) </span><span class="sxs-lookup"><span data-stu-id="53b4c-127">[Arrays](../../../csharp/programming-guide/arrays/index.md) </span></span>  
 [<span data-ttu-id="53b4c-128">Collections</span><span class="sxs-lookup"><span data-stu-id="53b4c-128">Collections</span></span>](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b)

