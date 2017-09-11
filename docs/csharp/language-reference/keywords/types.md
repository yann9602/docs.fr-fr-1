---
title: "Types (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- types [C#]
- data types [C#], type system
ms.assetid: 16b984df-f417-4e02-b1e6-4589d4a614ea
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
ms.openlocfilehash: 2816a5dd86e71641198a340b3a72094dffc93bdf
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="types-c-reference"></a><span data-ttu-id="6437d-102">Types (référence C#)</span><span class="sxs-lookup"><span data-stu-id="6437d-102">Types (C# Reference)</span></span>
<span data-ttu-id="6437d-103">Le système de types C# comporte les catégories suivantes :</span><span class="sxs-lookup"><span data-stu-id="6437d-103">The C# typing system contains the following categories:</span></span>  
  
-   [<span data-ttu-id="6437d-104">Types valeur</span><span class="sxs-lookup"><span data-stu-id="6437d-104">Value types</span></span>](../../../csharp/language-reference/keywords/value-types.md)  
  
-   [<span data-ttu-id="6437d-105">Types référence</span><span class="sxs-lookup"><span data-stu-id="6437d-105">Reference types</span></span>](../../../csharp/language-reference/keywords/reference-types.md)  
  
-   [<span data-ttu-id="6437d-106">Types pointeur</span><span class="sxs-lookup"><span data-stu-id="6437d-106">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
  
 <span data-ttu-id="6437d-107">Les variables de types valeur stockent des données alors que les variables de types référence stockent les références aux données réelles.</span><span class="sxs-lookup"><span data-stu-id="6437d-107">Variables that are value types store data, and those that are reference types store references to the actual data.</span></span> <span data-ttu-id="6437d-108">Les types référence sont également considérés comme des objets.</span><span class="sxs-lookup"><span data-stu-id="6437d-108">Reference types are also referred to as objects.</span></span> <span data-ttu-id="6437d-109">Les types pointeur ne peuvent être utilisés qu’en mode [unsafe](../../../csharp/language-reference/keywords/unsafe.md).</span><span class="sxs-lookup"><span data-stu-id="6437d-109">Pointer types can be used only in [unsafe](../../../csharp/language-reference/keywords/unsafe.md) mode.</span></span>  
  
 <span data-ttu-id="6437d-110">Il est possible de convertir un type valeur en type référence, puis de revenir en type valeur, en effectuant une conversion [boxing et unboxing](../../../csharp/programming-guide/types/boxing-and-unboxing.md).</span><span class="sxs-lookup"><span data-stu-id="6437d-110">It is possible to convert a value type to a reference type, and back again to a value type, by using [boxing and unboxing](../../../csharp/programming-guide/types/boxing-and-unboxing.md).</span></span> <span data-ttu-id="6437d-111">Vous ne pouvez pas convertir un type référence en type valeur, sauf s’il s’agit d’un type valeur boxed.</span><span class="sxs-lookup"><span data-stu-id="6437d-111">With the exception of a boxed value type, you cannot convert a reference type to a value type.</span></span>  
  
 <span data-ttu-id="6437d-112">Cette section présente également [void](../../../csharp/language-reference/keywords/void.md).</span><span class="sxs-lookup"><span data-stu-id="6437d-112">This section also introduces [void](../../../csharp/language-reference/keywords/void.md).</span></span>  
  
 <span data-ttu-id="6437d-113">Les types valeur sont également Nullable, ce qui signifie qu’ils peuvent stocker un état de non-valeur supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="6437d-113">Value types are also nullable, which means they can store an additional non-value state.</span></span> <span data-ttu-id="6437d-114">Pour plus d’informations, consultez [Types Nullable](../../../csharp/programming-guide/nullable-types/index.md).</span><span class="sxs-lookup"><span data-stu-id="6437d-114">For more information, see [Nullable Types](../../../csharp/programming-guide/nullable-types/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6437d-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6437d-115">See Also</span></span>  
 <span data-ttu-id="6437d-116">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="6437d-116">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="6437d-117">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="6437d-117">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="6437d-118">[Mots clés C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="6437d-118">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="6437d-119">[Tableaux de référence des types](../../../csharp/language-reference/keywords/reference-tables-for-types.md) </span><span class="sxs-lookup"><span data-stu-id="6437d-119">[Reference Tables for Types](../../../csharp/language-reference/keywords/reference-tables-for-types.md) </span></span>  
 <span data-ttu-id="6437d-120">[Cast et conversions de types](../../../csharp/programming-guide/types/casting-and-type-conversions.md) </span><span class="sxs-lookup"><span data-stu-id="6437d-120">[Casting and Type Conversions](../../../csharp/programming-guide/types/casting-and-type-conversions.md) </span></span>  
 [<span data-ttu-id="6437d-121">Types</span><span class="sxs-lookup"><span data-stu-id="6437d-121">Types</span></span>](../../../csharp/programming-guide/types/index.md)

