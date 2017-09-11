---
title: "Génériques et attributs (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- generics [C#], attributes
- attributes [C#], with generics
ms.assetid: da9fc326-4648-454a-8e13-3911a2edefd7
caps.latest.revision: 13
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
ms.openlocfilehash: 5136ae928a3a4b6f8ec4d86100d695f958d55858
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="generics-and-attributes-c-programming-guide"></a><span data-ttu-id="215e8-102">Génériques et attributs (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="215e8-102">Generics and Attributes (C# Programming Guide)</span></span>
<span data-ttu-id="215e8-103">Les attributs peuvent être appliqués aux types génériques de la même manière qu’aux types non génériques.</span><span class="sxs-lookup"><span data-stu-id="215e8-103">Attributes can be applied to generic types in the same way as non-generic types.</span></span> <span data-ttu-id="215e8-104">Pour plus d’informations sur l’application des attributs, consultez [Attributs](../../../csharp/programming-guide/concepts/attributes/index.md).</span><span class="sxs-lookup"><span data-stu-id="215e8-104">For more information on applying attributes, see [Attributes](../../../csharp/programming-guide/concepts/attributes/index.md).</span></span>  
  
 <span data-ttu-id="215e8-105">Les attributs personnalisés sont uniquement autorisés à référencer des types génériques ouverts, qui sont des types génériques pour lesquels aucun argument de type n’est fourni, et des types génériques construits fermés, qui fournissent des arguments pour tous les paramètres de type.</span><span class="sxs-lookup"><span data-stu-id="215e8-105">Custom attributes are only permitted to reference open generic types, which are generic types for which no type arguments are supplied, and closed constructed generic types, which supply arguments for all type parameters.</span></span>  
  
 <span data-ttu-id="215e8-106">Les exemples suivants utilisent cet attribut personnalisé :</span><span class="sxs-lookup"><span data-stu-id="215e8-106">The following examples use this custom attribute:</span></span>  
  
 <span data-ttu-id="215e8-107">[!code-cs[csProgGuideGenerics#48](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="215e8-107">[!code-cs[csProgGuideGenerics#48](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_1.cs)]</span></span>  
  
 <span data-ttu-id="215e8-108">Un attribut peut référencer un type générique ouvert :</span><span class="sxs-lookup"><span data-stu-id="215e8-108">An attribute can reference an open generic type:</span></span>  
  
 <span data-ttu-id="215e8-109">[!code-cs[csProgGuideGenerics#49](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="215e8-109">[!code-cs[csProgGuideGenerics#49](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_2.cs)]</span></span>  
  
 <span data-ttu-id="215e8-110">Spécifiez plusieurs paramètres de type à l’aide du nombre approprié de virgules.</span><span class="sxs-lookup"><span data-stu-id="215e8-110">Specify multiple type parameters using the appropriate number of commas.</span></span> <span data-ttu-id="215e8-111">Dans cet exemple, `GenericClass2` a deux paramètres de type :</span><span class="sxs-lookup"><span data-stu-id="215e8-111">In this example, `GenericClass2` has two type parameters:</span></span>  
  
 <span data-ttu-id="215e8-112">[!code-cs[csProgGuideGenerics#50](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="215e8-112">[!code-cs[csProgGuideGenerics#50](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_3.cs)]</span></span>  
  
 <span data-ttu-id="215e8-113">Un attribut peut référencer un type générique construit fermé :</span><span class="sxs-lookup"><span data-stu-id="215e8-113">An attribute can reference a closed constructed generic type:</span></span>  
  
 <span data-ttu-id="215e8-114">[!code-cs[csProgGuideGenerics#51](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="215e8-114">[!code-cs[csProgGuideGenerics#51](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_4.cs)]</span></span>  
  
 <span data-ttu-id="215e8-115">Un attribut qui référence un paramètre de type générique entraîne une erreur de compilation :</span><span class="sxs-lookup"><span data-stu-id="215e8-115">An attribute that references a generic type parameter will cause a compile-time error:</span></span>  
  
 <span data-ttu-id="215e8-116">[!code-cs[csProgGuideGenerics#52](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="215e8-116">[!code-cs[csProgGuideGenerics#52](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_5.cs)]</span></span>  
  
 <span data-ttu-id="215e8-117">Un type générique ne peut pas hériter d’<xref:System.Attribute> :</span><span class="sxs-lookup"><span data-stu-id="215e8-117">A generic type cannot inherit from <xref:System.Attribute>:</span></span>  
  
 <span data-ttu-id="215e8-118">[!code-cs[csProgGuideGenerics#53](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_6.cs)]</span><span class="sxs-lookup"><span data-stu-id="215e8-118">[!code-cs[csProgGuideGenerics#53](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_6.cs)]</span></span>  
  
 <span data-ttu-id="215e8-119">Pour obtenir des informations sur un type générique ou un paramètre de type au moment de l’exécution, vous pouvez utiliser les méthodes de <xref:System.Reflection>.</span><span class="sxs-lookup"><span data-stu-id="215e8-119">To obtain information about a generic type or type parameter at run time, you can use the methods of <xref:System.Reflection>.</span></span> <span data-ttu-id="215e8-120">Pour plus d’informations, consultez [Génériques et réflexion](../../../csharp/programming-guide/generics/generics-and-reflection.md)</span><span class="sxs-lookup"><span data-stu-id="215e8-120">For more information, see [Generics and Reflection](../../../csharp/programming-guide/generics/generics-and-reflection.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="215e8-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="215e8-121">See Also</span></span>  
 <span data-ttu-id="215e8-122">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="215e8-122">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="215e8-123">[Génériques](../../../csharp/programming-guide/generics/index.md) </span><span class="sxs-lookup"><span data-stu-id="215e8-123">[Generics](../../../csharp/programming-guide/generics/index.md) </span></span>  
 [<span data-ttu-id="215e8-124">Attributs</span><span class="sxs-lookup"><span data-stu-id="215e8-124">Attributes</span></span>](https://msdn.microsoft.com/library/5x6cd29c)

