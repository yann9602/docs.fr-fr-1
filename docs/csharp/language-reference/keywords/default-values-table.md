---
title: "Tableau des valeurs par défaut (référence C#)"
descripton: Learn what are the default values of value types returned by the default constructors.
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
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
caps.latest.revision: "12"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d034c1daf495c50e299fec4c5bf399652dad08ce
ms.sourcegitcommit: 425524461530f020f9747492b42f8cd72b011ae7
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2017
---
# <a name="default-values-table-c-reference"></a><span data-ttu-id="ffb19-102">Tableau des valeurs par défaut (référence C#)</span><span class="sxs-lookup"><span data-stu-id="ffb19-102">Default values table (C# Reference)</span></span>
<span data-ttu-id="ffb19-103">Le tableau suivant indique les valeurs par défaut de types valeur qui sont retournées par les constructeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="ffb19-103">The following table shows the default values of value types returned by the default constructors.</span></span> <span data-ttu-id="ffb19-104">Les constructeurs par défaut sont appelés au moyen de l’opérateur `new`, comme suit :</span><span class="sxs-lookup"><span data-stu-id="ffb19-104">Default constructors are invoked by using the `new` operator, as follows:</span></span>

```csharp
int myInt = new int();
```

<span data-ttu-id="ffb19-105">L’instruction qui précède produit le même résultat que la suivante :</span><span class="sxs-lookup"><span data-stu-id="ffb19-105">The preceding statement has the same effect as the following statement:</span></span>

```csharp
int myInt = 0;
```

<span data-ttu-id="ffb19-106">Pour rappel, il n’est pas possible d’utiliser en C# des variables qui n’ont pas été initialisées.</span><span class="sxs-lookup"><span data-stu-id="ffb19-106">Remember that using uninitialized variables in C# is not allowed.</span></span>

|<span data-ttu-id="ffb19-107">Type de valeur</span><span class="sxs-lookup"><span data-stu-id="ffb19-107">Value type</span></span>|<span data-ttu-id="ffb19-108">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="ffb19-108">Default value</span></span>|
|----------------|-------------------|
|[<span data-ttu-id="ffb19-109">bool</span><span class="sxs-lookup"><span data-stu-id="ffb19-109">bool</span></span>](../../../csharp/language-reference/keywords/bool.md)|`false`|
|[<span data-ttu-id="ffb19-110">byte</span><span class="sxs-lookup"><span data-stu-id="ffb19-110">byte</span></span>](../../../csharp/language-reference/keywords/byte.md)|<span data-ttu-id="ffb19-111">0</span><span class="sxs-lookup"><span data-stu-id="ffb19-111">0</span></span>|
|[<span data-ttu-id="ffb19-112">char</span><span class="sxs-lookup"><span data-stu-id="ffb19-112">char</span></span>](../../../csharp/language-reference/keywords/char.md)|<span data-ttu-id="ffb19-113">'\0'</span><span class="sxs-lookup"><span data-stu-id="ffb19-113">'\0'</span></span>|
|[<span data-ttu-id="ffb19-114">decimal</span><span class="sxs-lookup"><span data-stu-id="ffb19-114">decimal</span></span>](../../../csharp/language-reference/keywords/decimal.md)|<span data-ttu-id="ffb19-115">M 0</span><span class="sxs-lookup"><span data-stu-id="ffb19-115">0M</span></span>|
|[<span data-ttu-id="ffb19-116">double</span><span class="sxs-lookup"><span data-stu-id="ffb19-116">double</span></span>](../../../csharp/language-reference/keywords/double.md)|<span data-ttu-id="ffb19-117">0.0D</span><span class="sxs-lookup"><span data-stu-id="ffb19-117">0.0D</span></span>|
|[<span data-ttu-id="ffb19-118">enum</span><span class="sxs-lookup"><span data-stu-id="ffb19-118">enum</span></span>](../../../csharp/language-reference/keywords/enum.md)|<span data-ttu-id="ffb19-119">Valeur produite par l’expression (E)0, où E est l’identificateur de l’enum.</span><span class="sxs-lookup"><span data-stu-id="ffb19-119">The value produced by the expression (E)0, where E is the enum identifier.</span></span>|
|[<span data-ttu-id="ffb19-120">float</span><span class="sxs-lookup"><span data-stu-id="ffb19-120">float</span></span>](../../../csharp/language-reference/keywords/float.md)|<span data-ttu-id="ffb19-121">0.0F</span><span class="sxs-lookup"><span data-stu-id="ffb19-121">0.0F</span></span>|
|[<span data-ttu-id="ffb19-122">int</span><span class="sxs-lookup"><span data-stu-id="ffb19-122">int</span></span>](../../../csharp/language-reference/keywords/int.md)|<span data-ttu-id="ffb19-123">0</span><span class="sxs-lookup"><span data-stu-id="ffb19-123">0</span></span>|
|[<span data-ttu-id="ffb19-124">long</span><span class="sxs-lookup"><span data-stu-id="ffb19-124">long</span></span>](../../../csharp/language-reference/keywords/long.md)|<span data-ttu-id="ffb19-125">0L</span><span class="sxs-lookup"><span data-stu-id="ffb19-125">0L</span></span>|
|[<span data-ttu-id="ffb19-126">sbyte</span><span class="sxs-lookup"><span data-stu-id="ffb19-126">sbyte</span></span>](../../../csharp/language-reference/keywords/sbyte.md)|<span data-ttu-id="ffb19-127">0</span><span class="sxs-lookup"><span data-stu-id="ffb19-127">0</span></span>|
|[<span data-ttu-id="ffb19-128">short</span><span class="sxs-lookup"><span data-stu-id="ffb19-128">short</span></span>](../../../csharp/language-reference/keywords/short.md)|<span data-ttu-id="ffb19-129">0</span><span class="sxs-lookup"><span data-stu-id="ffb19-129">0</span></span>|
|[<span data-ttu-id="ffb19-130">struct</span><span class="sxs-lookup"><span data-stu-id="ffb19-130">struct</span></span>](../../../csharp/language-reference/keywords/struct.md)|<span data-ttu-id="ffb19-131">Valeur produite en affectant à tous les champs de type valeur leur valeur par défaut et à tous les champs de type référence la valeur `null`.</span><span class="sxs-lookup"><span data-stu-id="ffb19-131">The value produced by setting all value-type fields to their default values and all reference-type fields to `null`.</span></span>|
|[<span data-ttu-id="ffb19-132">uint</span><span class="sxs-lookup"><span data-stu-id="ffb19-132">uint</span></span>](../../../csharp/language-reference/keywords/uint.md)|<span data-ttu-id="ffb19-133">0</span><span class="sxs-lookup"><span data-stu-id="ffb19-133">0</span></span>|
|[<span data-ttu-id="ffb19-134">ulong</span><span class="sxs-lookup"><span data-stu-id="ffb19-134">ulong</span></span>](../../../csharp/language-reference/keywords/ulong.md)|<span data-ttu-id="ffb19-135">0</span><span class="sxs-lookup"><span data-stu-id="ffb19-135">0</span></span>|
|[<span data-ttu-id="ffb19-136">ushort</span><span class="sxs-lookup"><span data-stu-id="ffb19-136">ushort</span></span>](../../../csharp/language-reference/keywords/ushort.md)|<span data-ttu-id="ffb19-137">0</span><span class="sxs-lookup"><span data-stu-id="ffb19-137">0</span></span>|

## <a name="see-also"></a><span data-ttu-id="ffb19-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ffb19-138">See also</span></span>
 [<span data-ttu-id="ffb19-139">Référence C#</span><span class="sxs-lookup"><span data-stu-id="ffb19-139">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="ffb19-140">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="ffb19-140">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="ffb19-141">Tableau des types valeur</span><span class="sxs-lookup"><span data-stu-id="ffb19-141">Value Types Table</span></span>](../../../csharp/language-reference/keywords/value-types-table.md)  
 [<span data-ttu-id="ffb19-142">Types valeur</span><span class="sxs-lookup"><span data-stu-id="ffb19-142">Value Types</span></span>](../../../csharp/language-reference/keywords/value-types.md)  
 [<span data-ttu-id="ffb19-143">Tableau des types intégrés</span><span class="sxs-lookup"><span data-stu-id="ffb19-143">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [<span data-ttu-id="ffb19-144">Tableaux de référence des types</span><span class="sxs-lookup"><span data-stu-id="ffb19-144">Reference Tables for Types</span></span>](../../../csharp/language-reference/keywords/reference-tables-for-types.md)
