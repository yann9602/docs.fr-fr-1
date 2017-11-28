---
title: "get (référence C#)"
ms.date: 03/10/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- get_CSharpKeyword
- get
helpviewer_keywords: get keyword [C#]
ms.assetid: a52de048-fbe0-41b0-82ec-8e4ac04d3a71
caps.latest.revision: "11"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a2e8426e5c5be16be0114b5ccc66f30793ce7dda
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="get-c-reference"></a><span data-ttu-id="ccda6-102">get (référence C#)</span><span class="sxs-lookup"><span data-stu-id="ccda6-102">get (C# Reference)</span></span>

<span data-ttu-id="ccda6-103">Le mot clé `get` définit une méthode *Accessor* dans une propriété ou un indexeur qui retourne la valeur de la propriété ou l’élément de l’indexeur.</span><span class="sxs-lookup"><span data-stu-id="ccda6-103">The `get` keyword defines an *accessor* method in a property or indexer that returns the property value or the indexer element.</span></span> <span data-ttu-id="ccda6-104">Pour plus d’informations, consultez [Propriétés](../../../csharp/programming-guide/classes-and-structs/properties.md), [Propriétés implémentées automatiquement](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md) et [Indexeurs](../../../csharp/programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="ccda6-104">For more information, see [Properties](../../../csharp/programming-guide/classes-and-structs/properties.md), [Auto-Implemented Properties](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md) and [Indexers](../../../csharp/programming-guide/indexers/index.md).</span></span>  
  
<span data-ttu-id="ccda6-105">L’exemple suivant définit un accesseur `get` et un accesseur `set` pour une propriété nommée `Seconds`.</span><span class="sxs-lookup"><span data-stu-id="ccda6-105">The following example defines both a `get` and a `set` accessor for a property named `Seconds`.</span></span> <span data-ttu-id="ccda6-106">Il utilise un champ privé nommé `_seconds` pour stocker la valeur de la propriété.</span><span class="sxs-lookup"><span data-stu-id="ccda6-106">It uses a private field named `_seconds` to back the property value.</span></span>  
 
 [!code-csharp[get#1](../../../../samples/snippets/csharp/language-reference/keywords/get/get-1.cs)]  
  
<span data-ttu-id="ccda6-107">Souvent, l’accesseur `get` se compose d’une seule instruction qui retourne une valeur, comme dans l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="ccda6-107">Often, the `get` accessor consists of a single statement that returns a value, as it did in the previous example.</span></span> <span data-ttu-id="ccda6-108">À partir de C# 7, il est possible d’implémenter l’accesseur `get` en tant que membre expression-bodied.</span><span class="sxs-lookup"><span data-stu-id="ccda6-108">Starting with C# 7, you can implement the `get` accessor as an expression-bodied member.</span></span> <span data-ttu-id="ccda6-109">L’exemple suivant implémente l’accesseur `get` et l’accesseur `set` en tant que membres expression-bodied.</span><span class="sxs-lookup"><span data-stu-id="ccda6-109">The following example implements both the `get` and the `set` accessor as expression-bodied members.</span></span>

 [!code-csharp[get#3](../../../../samples/snippets/csharp/language-reference/keywords/get/get-3.cs)]   
 
<span data-ttu-id="ccda6-110">Pour les cas simples dans lesquels les accesseurs `get` et `set` d’une propriété n’effectuent aucune autre opération que la définition ou la récupération d’une valeur dans un champ de stockage privé, vous pouvez tirer parti de la prise en charge par le compilateur C# des propriétés implémentées automatiquement.</span><span class="sxs-lookup"><span data-stu-id="ccda6-110">For simple cases in which a property's `get` and `set` accessors perform no other operation than setting or retrieving a value in a private backing field, you can take advantage of the C# compiler's support for auto-implemented properties.</span></span> <span data-ttu-id="ccda6-111">L’exemple suivant implémente `Hours` en tant que propriété implémentée automatiquement.</span><span class="sxs-lookup"><span data-stu-id="ccda6-111">The following example implements `Hours` as an auto-implemented property.</span></span> 
  
 [!code-csharp[get#2](../../../../samples/snippets/csharp/language-reference/keywords/get/get-2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="ccda6-112">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="ccda6-112">C# Language Specification</span></span>

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ccda6-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ccda6-113">See Also</span></span>  
 [<span data-ttu-id="ccda6-114">Référence C#</span><span class="sxs-lookup"><span data-stu-id="ccda6-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="ccda6-115">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="ccda6-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 <span data-ttu-id="ccda6-116">[Mots clés C#](../../../csharp/language-reference/keywords/index.md) [Propriétés](../../../csharp/programming-guide/classes-and-structs/properties.md)</span><span class="sxs-lookup"><span data-stu-id="ccda6-116">[C# Keywords](../../../csharp/language-reference/keywords/index.md) [Properties](../../../csharp/programming-guide/classes-and-structs/properties.md)</span></span>
