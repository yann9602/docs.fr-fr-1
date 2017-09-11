---
title: "get (référence C#)"
ms.date: 2017-03-10
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- get_CSharpKeyword
- get
dev_langs:
- CSharp
helpviewer_keywords:
- get keyword [C#]
ms.assetid: a52de048-fbe0-41b0-82ec-8e4ac04d3a71
caps.latest.revision: 11
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
ms.openlocfilehash: 88603864ae0a31a193cab211b8ce8061ec63c169
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="get-c-reference"></a><span data-ttu-id="b200b-102">get (référence C#)</span><span class="sxs-lookup"><span data-stu-id="b200b-102">get (C# Reference)</span></span>

<span data-ttu-id="b200b-103">Le mot clé `get` définit une méthode *Accessor* dans une propriété ou un indexeur qui retourne la valeur de la propriété ou l’élément de l’indexeur.</span><span class="sxs-lookup"><span data-stu-id="b200b-103">The `get` keyword defines an *accessor* method in a property or indexer that returns the property value or the indexer element.</span></span> <span data-ttu-id="b200b-104">Pour plus d’informations, consultez [Propriétés](../../../csharp/programming-guide/classes-and-structs/properties.md), [Propriétés implémentées automatiquement](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md) et [Indexeurs](../../../csharp/programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="b200b-104">For more information, see [Properties](../../../csharp/programming-guide/classes-and-structs/properties.md), [Auto-Implemented Properties](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md) and [Indexers](../../../csharp/programming-guide/indexers/index.md).</span></span>  
  
<span data-ttu-id="b200b-105">L’exemple suivant définit un accesseur `get` et un accesseur `set` pour une propriété nommée `Seconds`.</span><span class="sxs-lookup"><span data-stu-id="b200b-105">The following example defines both a `get` and a `set` accessor for a property named `Seconds`.</span></span> <span data-ttu-id="b200b-106">Il utilise un champ privé nommé `_seconds` pour stocker la valeur de la propriété.</span><span class="sxs-lookup"><span data-stu-id="b200b-106">It uses a private field named `_seconds` to back the property value.</span></span>  
 
 <span data-ttu-id="b200b-107">[!code-cs[get#1](../../../../samples/snippets/csharp/language-reference/keywords/get/get-1.cs)]</span><span class="sxs-lookup"><span data-stu-id="b200b-107">[!code-cs[get#1](../../../../samples/snippets/csharp/language-reference/keywords/get/get-1.cs)]</span></span>  
  
<span data-ttu-id="b200b-108">Souvent, l’accesseur `get` se compose d’une seule instruction qui retourne une valeur, comme dans l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="b200b-108">Often, the `get` accessor consists of a single statement that returns a value, as it did in the previous example.</span></span> <span data-ttu-id="b200b-109">À partir de C# 7, il est possible d’implémenter l’accesseur `get` en tant que membre expression-bodied.</span><span class="sxs-lookup"><span data-stu-id="b200b-109">Starting with C# 7, you can implement the `get` accessor as an expression-bodied member.</span></span> <span data-ttu-id="b200b-110">L’exemple suivant implémente l’accesseur `get` et l’accesseur `set` en tant que membres expression-bodied.</span><span class="sxs-lookup"><span data-stu-id="b200b-110">The following example implements both the `get` and the `set` accessor as expression-bodied members.</span></span>

 <span data-ttu-id="b200b-111">[!code-cs[get#3](../../../../samples/snippets/csharp/language-reference/keywords/get/get-3.cs)]</span><span class="sxs-lookup"><span data-stu-id="b200b-111">[!code-cs[get#3](../../../../samples/snippets/csharp/language-reference/keywords/get/get-3.cs)]</span></span>   
 
<span data-ttu-id="b200b-112">Pour les cas simples dans lesquels les accesseurs `get` et `set` de la propriété n’effectuent aucune autre opération que la définition ou la récupération d’une valeur dans un champ de stockage privé, vous pouvez tirer parti de la prise en charge des propriétés implémentées automatiquement fournies par le compilateur C#.</span><span class="sxs-lookup"><span data-stu-id="b200b-112">For simple cases in which a property's `get` and `set` accessors perform no other operation than setting or retrieving a value in a private backing field, you can take advantage of the C# compiler's support for auto-implemented properties.</span></span> <span data-ttu-id="b200b-113">L’exemple suivant implémente `Hours` en tant que propriété implémentée automatiquement.</span><span class="sxs-lookup"><span data-stu-id="b200b-113">The following example implements `Hours` as an auto-implemented property.</span></span> 
  
 <span data-ttu-id="b200b-114">[!code-cs[get#2](../../../../samples/snippets/csharp/language-reference/keywords/get/get-2.cs)]</span><span class="sxs-lookup"><span data-stu-id="b200b-114">[!code-cs[get#2](../../../../samples/snippets/csharp/language-reference/keywords/get/get-2.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="b200b-115">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="b200b-115">C# Language Specification</span></span>

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b200b-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b200b-116">See Also</span></span>  
 <span data-ttu-id="b200b-117">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="b200b-117">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="b200b-118">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="b200b-118">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="b200b-119">[Mots clés C#](../../../csharp/language-reference/keywords/index.md) [Propriétés](../../../csharp/programming-guide/classes-and-structs/properties.md)</span><span class="sxs-lookup"><span data-stu-id="b200b-119">[C# Keywords](../../../csharp/language-reference/keywords/index.md) [Properties](../../../csharp/programming-guide/classes-and-structs/properties.md)</span></span>

