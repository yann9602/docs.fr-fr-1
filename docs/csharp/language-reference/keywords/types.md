---
title: "Types (référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- types [C#]
- data types [C#], type system
ms.assetid: 16b984df-f417-4e02-b1e6-4589d4a614ea
caps.latest.revision: "13"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2c7285e237b04c1290391c4bba3e62886dceb83c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="types-c-reference"></a><span data-ttu-id="a3df9-102">Types (référence C#)</span><span class="sxs-lookup"><span data-stu-id="a3df9-102">Types (C# Reference)</span></span>
<span data-ttu-id="a3df9-103">Le système de types C# comporte les catégories suivantes :</span><span class="sxs-lookup"><span data-stu-id="a3df9-103">The C# typing system contains the following categories:</span></span>  
  
-   [<span data-ttu-id="a3df9-104">Types valeur</span><span class="sxs-lookup"><span data-stu-id="a3df9-104">Value types</span></span>](../../../csharp/language-reference/keywords/value-types.md)  
  
-   [<span data-ttu-id="a3df9-105">Types référence</span><span class="sxs-lookup"><span data-stu-id="a3df9-105">Reference types</span></span>](../../../csharp/language-reference/keywords/reference-types.md)  
  
-   [<span data-ttu-id="a3df9-106">Types de pointeur</span><span class="sxs-lookup"><span data-stu-id="a3df9-106">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
  
 <span data-ttu-id="a3df9-107">Les variables de types valeur stockent des données alors que les variables de types référence stockent les références aux données réelles.</span><span class="sxs-lookup"><span data-stu-id="a3df9-107">Variables that are value types store data, and those that are reference types store references to the actual data.</span></span> <span data-ttu-id="a3df9-108">Les types référence sont également considérés comme des objets.</span><span class="sxs-lookup"><span data-stu-id="a3df9-108">Reference types are also referred to as objects.</span></span> <span data-ttu-id="a3df9-109">Les types pointeur ne peuvent être utilisés qu’en mode [unsafe](../../../csharp/language-reference/keywords/unsafe.md).</span><span class="sxs-lookup"><span data-stu-id="a3df9-109">Pointer types can be used only in [unsafe](../../../csharp/language-reference/keywords/unsafe.md) mode.</span></span>  
  
 <span data-ttu-id="a3df9-110">Il est possible de convertir un type valeur en type référence, puis de revenir en type valeur, en effectuant une conversion [boxing et unboxing](../../../csharp/programming-guide/types/boxing-and-unboxing.md).</span><span class="sxs-lookup"><span data-stu-id="a3df9-110">It is possible to convert a value type to a reference type, and back again to a value type, by using [boxing and unboxing](../../../csharp/programming-guide/types/boxing-and-unboxing.md).</span></span> <span data-ttu-id="a3df9-111">Vous ne pouvez pas convertir un type référence en type valeur, sauf s’il s’agit d’un type valeur boxed.</span><span class="sxs-lookup"><span data-stu-id="a3df9-111">With the exception of a boxed value type, you cannot convert a reference type to a value type.</span></span>  
  
 <span data-ttu-id="a3df9-112">Cette section présente également [void](../../../csharp/language-reference/keywords/void.md).</span><span class="sxs-lookup"><span data-stu-id="a3df9-112">This section also introduces [void](../../../csharp/language-reference/keywords/void.md).</span></span>  
  
 <span data-ttu-id="a3df9-113">Les types valeur sont également Nullable, ce qui signifie qu’ils peuvent stocker un état de non-valeur supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="a3df9-113">Value types are also nullable, which means they can store an additional non-value state.</span></span> <span data-ttu-id="a3df9-114">Pour plus d’informations, consultez [Types Nullable](../../../csharp/programming-guide/nullable-types/index.md).</span><span class="sxs-lookup"><span data-stu-id="a3df9-114">For more information, see [Nullable Types](../../../csharp/programming-guide/nullable-types/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3df9-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a3df9-115">See Also</span></span>  
 [<span data-ttu-id="a3df9-116">Référence C#</span><span class="sxs-lookup"><span data-stu-id="a3df9-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="a3df9-117">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="a3df9-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="a3df9-118">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="a3df9-118">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="a3df9-119">Tableaux de référence des types</span><span class="sxs-lookup"><span data-stu-id="a3df9-119">Reference Tables for Types</span></span>](../../../csharp/language-reference/keywords/reference-tables-for-types.md)  
 [<span data-ttu-id="a3df9-120">Cast et conversions de types</span><span class="sxs-lookup"><span data-stu-id="a3df9-120">Casting and Type Conversions</span></span>](../../../csharp/programming-guide/types/casting-and-type-conversions.md)  
 [<span data-ttu-id="a3df9-121">Types</span><span class="sxs-lookup"><span data-stu-id="a3df9-121">Types</span></span>](../../../csharp/programming-guide/types/index.md)
