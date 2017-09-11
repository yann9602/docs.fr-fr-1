---
title: "into (informations de référence sur C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- into_CSharpKeyword
- into
dev_langs:
- CSharp
helpviewer_keywords:
- into keyword [C#]
ms.assetid: 81ec62c1-f0b1-4755-8a31-959876e77f65
caps.latest.revision: 18
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
ms.openlocfilehash: ef85caf02387432761e5ccbb7e0478b46d32f795
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="into-c-reference"></a><span data-ttu-id="818fe-102">into (informations de référence sur C#)</span><span class="sxs-lookup"><span data-stu-id="818fe-102">into (C# Reference)</span></span>
<span data-ttu-id="818fe-103">Le mot clé contextuel `into` permet de créer un identificateur temporaire pour stocker les résultats d’une clause [group](../../../csharp/language-reference/keywords/group-clause.md), [join](../../../csharp/language-reference/keywords/join-clause.md) ou [select](../../../csharp/language-reference/keywords/select-clause.md) dans un nouvel identificateur.</span><span class="sxs-lookup"><span data-stu-id="818fe-103">The `into` contextual keyword can be used to create a temporary identifier to store the results of a [group](../../../csharp/language-reference/keywords/group-clause.md), [join](../../../csharp/language-reference/keywords/join-clause.md) or [select](../../../csharp/language-reference/keywords/select-clause.md) clause into a new identifier.</span></span> <span data-ttu-id="818fe-104">Cet identificateur peut lui-même être un générateur pour d’autres commandes de requête.</span><span class="sxs-lookup"><span data-stu-id="818fe-104">This identifier can itself be a generator for additional query commands.</span></span> <span data-ttu-id="818fe-105">Quand il est utilisé dans une clause `group` ou `select`, le nouvel identificateur est parfois appelé *continuation*.</span><span class="sxs-lookup"><span data-stu-id="818fe-105">When used in a `group` or `select` clause, the use of the new identifier is sometimes referred to as a *continuation*.</span></span>  
  
## <a name="example"></a><span data-ttu-id="818fe-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="818fe-106">Example</span></span>  
 <span data-ttu-id="818fe-107">L’exemple suivant illustre l’utilisation du mot clé `into` pour activer un identificateur temporaire `fruitGroup` dont le type déduit est `IGrouping`.</span><span class="sxs-lookup"><span data-stu-id="818fe-107">The following example shows the use of the `into` keyword to enable a temporary identifier `fruitGroup` which has an inferred type of `IGrouping`.</span></span> <span data-ttu-id="818fe-108">En utilisant l’identificateur, vous pouvez appeler la méthode <xref:System.Linq.Enumerable.Count%2A> dans chaque groupe et sélectionner uniquement les groupes qui contiennent deux mots ou plus.</span><span class="sxs-lookup"><span data-stu-id="818fe-108">By using the identifier, you can invoke the <xref:System.Linq.Enumerable.Count%2A> method on each group and select only those groups that contain two or more words.</span></span>  
  
 <span data-ttu-id="818fe-109">[!code-cs[cscsrefQueryKeywords#18](../../../csharp/language-reference/keywords/codesnippet/CSharp/into_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="818fe-109">[!code-cs[cscsrefQueryKeywords#18](../../../csharp/language-reference/keywords/codesnippet/CSharp/into_1.cs)]</span></span>  
  
 <span data-ttu-id="818fe-110">L’utilisation de `into` dans une clause `group` n’est nécessaire que si vous voulez effectuer des opérations de requête supplémentaires dans chaque groupe.</span><span class="sxs-lookup"><span data-stu-id="818fe-110">The use of `into` in a `group` clause is only necessary when you want to perform additional query operations on each group.</span></span> <span data-ttu-id="818fe-111">Pour plus d’informations, consultez [group, clause](../../../csharp/language-reference/keywords/group-clause.md).</span><span class="sxs-lookup"><span data-stu-id="818fe-111">For more information, see [group clause](../../../csharp/language-reference/keywords/group-clause.md).</span></span>  
  
 <span data-ttu-id="818fe-112">Pour obtenir un exemple d’utilisation de `into` dans une clause `join`, consultez [join, clause](../../../csharp/language-reference/keywords/join-clause.md).</span><span class="sxs-lookup"><span data-stu-id="818fe-112">For an example of the use of `into` in a `join` clause, see [join clause](../../../csharp/language-reference/keywords/join-clause.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="818fe-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="818fe-113">See Also</span></span>  
 <span data-ttu-id="818fe-114">[Mots clés de requête (LINQ)](../../../csharp/language-reference/keywords/query-keywords.md) </span><span class="sxs-lookup"><span data-stu-id="818fe-114">[Query Keywords (LINQ)](../../../csharp/language-reference/keywords/query-keywords.md) </span></span>  
 <span data-ttu-id="818fe-115">[Expressions de requête LINQ](../../../csharp/programming-guide/linq-query-expressions/index.md) </span><span class="sxs-lookup"><span data-stu-id="818fe-115">[LINQ Query Expressions](../../../csharp/programming-guide/linq-query-expressions/index.md) </span></span>  
 [<span data-ttu-id="818fe-116">group, clause</span><span class="sxs-lookup"><span data-stu-id="818fe-116">group clause</span></span>](../../../csharp/language-reference/keywords/group-clause.md)

