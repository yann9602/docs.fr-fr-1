---
title: "Tableau des valeurs par défaut (référence C#)"
descripton: Learn what are the default values of value types returned by the default constructors.
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- constructors [C#], return values
- keywords [C#], new
- default constructor [C#]
- defaults [C#]
- value types [C#], initializing
- variables [C#], value types
- constructors [C#], default constructor
- types [C#], default constructor return values
ms.assetid: 4af2c1df-9e3a-48c1-83ac-b192986fc5bc
caps.latest.revision: 12
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: f8cf12317f1f0163028db003ff31604480da5d1c
ms.openlocfilehash: 975d416259778e0741347829d8a9c79aaa6cfc8c
ms.contentlocale: fr-fr
ms.lasthandoff: 08/12/2017

---
# <a name="default-values-table-c-reference"></a><span data-ttu-id="05c5e-102">Tableau des valeurs par défaut (référence C#)</span><span class="sxs-lookup"><span data-stu-id="05c5e-102">Default values table (C# Reference)</span></span>
<span data-ttu-id="05c5e-103">Le tableau suivant indique les valeurs par défaut de types valeur qui sont retournées par les constructeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="05c5e-103">The following table shows the default values of value types returned by the default constructors.</span></span> <span data-ttu-id="05c5e-104">Les constructeurs par défaut sont appelés au moyen de l’opérateur `new`, comme suit :</span><span class="sxs-lookup"><span data-stu-id="05c5e-104">Default constructors are invoked by using the `new` operator, as follows:</span></span>

```csharp
int myInt = new int();
```

<span data-ttu-id="05c5e-105">L’instruction qui précède produit le même résultat que la suivante :</span><span class="sxs-lookup"><span data-stu-id="05c5e-105">The preceding statement has the same effect as the following statement:</span></span>

```csharp
int myInt = 0;
```

<span data-ttu-id="05c5e-106">Pour rappel, il n’est pas possible d’utiliser en C# des variables qui n’ont pas été initialisées.</span><span class="sxs-lookup"><span data-stu-id="05c5e-106">Remember that using uninitialized variables in C# is not allowed.</span></span>

|<span data-ttu-id="05c5e-107">Type de valeur</span><span class="sxs-lookup"><span data-stu-id="05c5e-107">Value type</span></span>|<span data-ttu-id="05c5e-108">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="05c5e-108">Default value</span></span>|
|----------------|-------------------|
|[<span data-ttu-id="05c5e-109">bool</span><span class="sxs-lookup"><span data-stu-id="05c5e-109">bool</span></span>](../../../csharp/language-reference/keywords/bool.md)|`false`|
|[<span data-ttu-id="05c5e-110">byte</span><span class="sxs-lookup"><span data-stu-id="05c5e-110">byte</span></span>](../../../csharp/language-reference/keywords/byte.md)|<span data-ttu-id="05c5e-111">0</span><span class="sxs-lookup"><span data-stu-id="05c5e-111">0</span></span>|
|[<span data-ttu-id="05c5e-112">char</span><span class="sxs-lookup"><span data-stu-id="05c5e-112">char</span></span>](../../../csharp/language-reference/keywords/char.md)|<span data-ttu-id="05c5e-113">'\0'</span><span class="sxs-lookup"><span data-stu-id="05c5e-113">'\0'</span></span>|
|[<span data-ttu-id="05c5e-114">decimal</span><span class="sxs-lookup"><span data-stu-id="05c5e-114">decimal</span></span>](../../../csharp/language-reference/keywords/decimal.md)|<span data-ttu-id="05c5e-115">0.0M</span><span class="sxs-lookup"><span data-stu-id="05c5e-115">0.0M</span></span>|
|[<span data-ttu-id="05c5e-116">double</span><span class="sxs-lookup"><span data-stu-id="05c5e-116">double</span></span>](../../../csharp/language-reference/keywords/double.md)|<span data-ttu-id="05c5e-117">0.0D</span><span class="sxs-lookup"><span data-stu-id="05c5e-117">0.0D</span></span>|
|[<span data-ttu-id="05c5e-118">enum</span><span class="sxs-lookup"><span data-stu-id="05c5e-118">enum</span></span>](../../../csharp/language-reference/keywords/enum.md)|<span data-ttu-id="05c5e-119">Valeur produite par l’expression (E)0, où E est l’identificateur de l’enum.</span><span class="sxs-lookup"><span data-stu-id="05c5e-119">The value produced by the expression (E)0, where E is the enum identifier.</span></span>|
|[<span data-ttu-id="05c5e-120">float</span><span class="sxs-lookup"><span data-stu-id="05c5e-120">float</span></span>](../../../csharp/language-reference/keywords/float.md)|<span data-ttu-id="05c5e-121">0.0F</span><span class="sxs-lookup"><span data-stu-id="05c5e-121">0.0F</span></span>|
|[<span data-ttu-id="05c5e-122">int</span><span class="sxs-lookup"><span data-stu-id="05c5e-122">int</span></span>](../../../csharp/language-reference/keywords/int.md)|<span data-ttu-id="05c5e-123">0</span><span class="sxs-lookup"><span data-stu-id="05c5e-123">0</span></span>|
|[<span data-ttu-id="05c5e-124">long</span><span class="sxs-lookup"><span data-stu-id="05c5e-124">long</span></span>](../../../csharp/language-reference/keywords/long.md)|<span data-ttu-id="05c5e-125">0L</span><span class="sxs-lookup"><span data-stu-id="05c5e-125">0L</span></span>|
|[<span data-ttu-id="05c5e-126">sbyte</span><span class="sxs-lookup"><span data-stu-id="05c5e-126">sbyte</span></span>](../../../csharp/language-reference/keywords/sbyte.md)|<span data-ttu-id="05c5e-127">0</span><span class="sxs-lookup"><span data-stu-id="05c5e-127">0</span></span>|
|[<span data-ttu-id="05c5e-128">short</span><span class="sxs-lookup"><span data-stu-id="05c5e-128">short</span></span>](../../../csharp/language-reference/keywords/short.md)|<span data-ttu-id="05c5e-129">0</span><span class="sxs-lookup"><span data-stu-id="05c5e-129">0</span></span>|
|[<span data-ttu-id="05c5e-130">struct</span><span class="sxs-lookup"><span data-stu-id="05c5e-130">struct</span></span>](../../../csharp/language-reference/keywords/struct.md)|<span data-ttu-id="05c5e-131">Valeur produite en affectant à tous les champs de type valeur leur valeur par défaut et à tous les champs de type référence la valeur `null`.</span><span class="sxs-lookup"><span data-stu-id="05c5e-131">The value produced by setting all value-type fields to their default values and all reference-type fields to `null`.</span></span>|
|[<span data-ttu-id="05c5e-132">uint</span><span class="sxs-lookup"><span data-stu-id="05c5e-132">uint</span></span>](../../../csharp/language-reference/keywords/uint.md)|<span data-ttu-id="05c5e-133">0</span><span class="sxs-lookup"><span data-stu-id="05c5e-133">0</span></span>|
|[<span data-ttu-id="05c5e-134">ulong</span><span class="sxs-lookup"><span data-stu-id="05c5e-134">ulong</span></span>](../../../csharp/language-reference/keywords/ulong.md)|<span data-ttu-id="05c5e-135">0</span><span class="sxs-lookup"><span data-stu-id="05c5e-135">0</span></span>|
|[<span data-ttu-id="05c5e-136">ushort</span><span class="sxs-lookup"><span data-stu-id="05c5e-136">ushort</span></span>](../../../csharp/language-reference/keywords/ushort.md)|<span data-ttu-id="05c5e-137">0</span><span class="sxs-lookup"><span data-stu-id="05c5e-137">0</span></span>|

## <a name="see-also"></a><span data-ttu-id="05c5e-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="05c5e-138">See also</span></span>
 <span data-ttu-id="05c5e-139">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="05c5e-139">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="05c5e-140">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="05c5e-140">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="05c5e-141">[Tableau des types valeur](../../../csharp/language-reference/keywords/value-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="05c5e-141">[Value Types Table](../../../csharp/language-reference/keywords/value-types-table.md) </span></span>  
 <span data-ttu-id="05c5e-142">[Types valeur](../../../csharp/language-reference/keywords/value-types.md) </span><span class="sxs-lookup"><span data-stu-id="05c5e-142">[Value Types](../../../csharp/language-reference/keywords/value-types.md) </span></span>  
 <span data-ttu-id="05c5e-143">[Tableau des types intégrés](../../../csharp/language-reference/keywords/built-in-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="05c5e-143">[Built-In Types Table](../../../csharp/language-reference/keywords/built-in-types-table.md) </span></span>  
 [<span data-ttu-id="05c5e-144">Tableaux de référence des types</span><span class="sxs-lookup"><span data-stu-id="05c5e-144">Reference Tables for Types</span></span>](../../../csharp/language-reference/keywords/reference-tables-for-types.md)

