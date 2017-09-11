---
title: "Génériques et tableaux (guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- generics [C#], arrays
- arrays [C#], generics
ms.assetid: 7d956536-3851-41b5-94ad-3e7c0a5fe485
caps.latest.revision: 17
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
ms.openlocfilehash: 46cea2733504e56aec5e65a4c9a8b655bc9431cf
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="generics-and-arrays-c-programming-guide"></a><span data-ttu-id="57fec-102">Génériques et tableaux (guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="57fec-102">Generics and Arrays (C# Programming Guide)</span></span>
<span data-ttu-id="57fec-103">En C# 2.0 et versions ultérieures, les tableaux unidimensionnels qui ont une limite inférieure de zéro implémentent automatiquement <xref:System.Collections.Generic.IList%601>.</span><span class="sxs-lookup"><span data-stu-id="57fec-103">In C# 2.0 and later, single-dimensional arrays that have a lower bound of zero automatically implement <xref:System.Collections.Generic.IList%601>.</span></span> <span data-ttu-id="57fec-104">Cela vous permet de créer des méthodes génériques qui peuvent utiliser le même code pour itérer au sein de tableaux et d’autres types de collections.</span><span class="sxs-lookup"><span data-stu-id="57fec-104">This enables you to create generic methods that can use the same code to iterate through arrays and other collection types.</span></span> <span data-ttu-id="57fec-105">Cette technique est essentiellement utile pour lire les données dans des collections.</span><span class="sxs-lookup"><span data-stu-id="57fec-105">This technique is primarily useful for reading data in collections.</span></span> <span data-ttu-id="57fec-106">L’interface <xref:System.Collections.Generic.IList%601> ne peut pas être utilisée pour ajouter ni supprimer des éléments dans un tableau.</span><span class="sxs-lookup"><span data-stu-id="57fec-106">The <xref:System.Collections.Generic.IList%601> interface cannot be used to add or remove elements from an array.</span></span> <span data-ttu-id="57fec-107">Une exception est levée si vous essayez d’appeler une méthode <xref:System.Collections.Generic.IList%601> telle que <xref:System.Collections.Generic.IList%601.RemoveAt%2A> sur un tableau dans ce contexte.</span><span class="sxs-lookup"><span data-stu-id="57fec-107">An exception will be thrown if you try to call an <xref:System.Collections.Generic.IList%601> method such as <xref:System.Collections.Generic.IList%601.RemoveAt%2A> on an array in this context.</span></span>  
  
 <span data-ttu-id="57fec-108">L’exemple de code suivant montre comment une méthode générique seule qui prend un paramètre d’entrée <xref:System.Collections.Generic.IList%601> peut itérer à la fois au sein d’une liste et d’un tableau (en l’occurrence un tableau d’entiers).</span><span class="sxs-lookup"><span data-stu-id="57fec-108">The following code example demonstrates how a single generic method that takes an <xref:System.Collections.Generic.IList%601> input parameter can iterate through both a list and an array, in this case an array of integers.</span></span>  
  
 <span data-ttu-id="57fec-109">[!code-cs[csProgGuideGenerics#35](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-arrays_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="57fec-109">[!code-cs[csProgGuideGenerics#35](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-arrays_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57fec-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="57fec-110">See Also</span></span>  
 <span data-ttu-id="57fec-111"><xref:System.Collections.Generic></span><span class="sxs-lookup"><span data-stu-id="57fec-111"><xref:System.Collections.Generic></span></span>   
 <span data-ttu-id="57fec-112">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="57fec-112">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="57fec-113">[Génériques](../../../csharp/programming-guide/generics/index.md) </span><span class="sxs-lookup"><span data-stu-id="57fec-113">[Generics](../../../csharp/programming-guide/generics/index.md) </span></span>  
 <span data-ttu-id="57fec-114">[Tableaux](../../../csharp/programming-guide/arrays/index.md) </span><span class="sxs-lookup"><span data-stu-id="57fec-114">[Arrays](../../../csharp/programming-guide/arrays/index.md) </span></span>  
 [<span data-ttu-id="57fec-115">Génériques</span><span class="sxs-lookup"><span data-stu-id="57fec-115">Generics</span></span>](~/docs/standard/generics/index.md)

