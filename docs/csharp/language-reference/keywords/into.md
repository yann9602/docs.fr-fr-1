---
title: "into (Référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- into_CSharpKeyword
- into
helpviewer_keywords: into keyword [C#]
ms.assetid: 81ec62c1-f0b1-4755-8a31-959876e77f65
caps.latest.revision: "18"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7f2400143e66c68942cdec3ebfa04cfdd8cfe983
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="into-c-reference"></a><span data-ttu-id="2912c-102">into (Référence C#)</span><span class="sxs-lookup"><span data-stu-id="2912c-102">into (C# Reference)</span></span>
<span data-ttu-id="2912c-103">Le mot clé contextuel `into` permet de créer un identificateur temporaire pour stocker les résultats d’une clause [group](../../../csharp/language-reference/keywords/group-clause.md), [join](../../../csharp/language-reference/keywords/join-clause.md) ou [select](../../../csharp/language-reference/keywords/select-clause.md) dans un nouvel identificateur.</span><span class="sxs-lookup"><span data-stu-id="2912c-103">The `into` contextual keyword can be used to create a temporary identifier to store the results of a [group](../../../csharp/language-reference/keywords/group-clause.md), [join](../../../csharp/language-reference/keywords/join-clause.md) or [select](../../../csharp/language-reference/keywords/select-clause.md) clause into a new identifier.</span></span> <span data-ttu-id="2912c-104">Cet identificateur peut lui-même être un générateur pour d’autres commandes de requête.</span><span class="sxs-lookup"><span data-stu-id="2912c-104">This identifier can itself be a generator for additional query commands.</span></span> <span data-ttu-id="2912c-105">Quand il est utilisé dans une clause `group` ou `select`, le nouvel identificateur est parfois appelé *continuation*.</span><span class="sxs-lookup"><span data-stu-id="2912c-105">When used in a `group` or `select` clause, the use of the new identifier is sometimes referred to as a *continuation*.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2912c-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="2912c-106">Example</span></span>  
 <span data-ttu-id="2912c-107">L’exemple suivant illustre l’utilisation du mot clé `into` pour activer un identificateur temporaire `fruitGroup` dont le type déduit est `IGrouping`.</span><span class="sxs-lookup"><span data-stu-id="2912c-107">The following example shows the use of the `into` keyword to enable a temporary identifier `fruitGroup` which has an inferred type of `IGrouping`.</span></span> <span data-ttu-id="2912c-108">En utilisant l’identificateur, vous pouvez appeler la méthode <xref:System.Linq.Enumerable.Count%2A> dans chaque groupe et sélectionner uniquement les groupes qui contiennent deux mots ou plus.</span><span class="sxs-lookup"><span data-stu-id="2912c-108">By using the identifier, you can invoke the <xref:System.Linq.Enumerable.Count%2A> method on each group and select only those groups that contain two or more words.</span></span>  
  
 [!code-csharp[cscsrefQueryKeywords#18](../../../csharp/language-reference/keywords/codesnippet/CSharp/into_1.cs)]  
  
 <span data-ttu-id="2912c-109">L’utilisation de `into` dans une clause `group` n’est nécessaire que si vous voulez effectuer des opérations de requête supplémentaires dans chaque groupe.</span><span class="sxs-lookup"><span data-stu-id="2912c-109">The use of `into` in a `group` clause is only necessary when you want to perform additional query operations on each group.</span></span> <span data-ttu-id="2912c-110">Pour plus d’informations, consultez [group, clause](../../../csharp/language-reference/keywords/group-clause.md).</span><span class="sxs-lookup"><span data-stu-id="2912c-110">For more information, see [group clause](../../../csharp/language-reference/keywords/group-clause.md).</span></span>  
  
 <span data-ttu-id="2912c-111">Pour obtenir un exemple d’utilisation de `into` dans une clause `join`, consultez [join, clause](../../../csharp/language-reference/keywords/join-clause.md).</span><span class="sxs-lookup"><span data-stu-id="2912c-111">For an example of the use of `into` in a `join` clause, see [join clause](../../../csharp/language-reference/keywords/join-clause.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2912c-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2912c-112">See Also</span></span>  
 [<span data-ttu-id="2912c-113">Mots clés de requête (LINQ)</span><span class="sxs-lookup"><span data-stu-id="2912c-113">Query Keywords (LINQ)</span></span>](../../../csharp/language-reference/keywords/query-keywords.md)  
 [<span data-ttu-id="2912c-114">Expressions de requête LINQ</span><span class="sxs-lookup"><span data-stu-id="2912c-114">LINQ Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [<span data-ttu-id="2912c-115">group, clause</span><span class="sxs-lookup"><span data-stu-id="2912c-115">group clause</span></span>](../../../csharp/language-reference/keywords/group-clause.md)
