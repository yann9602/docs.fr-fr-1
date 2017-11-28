---
title: "sizeof (référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- sizeof_CSharpKeyword
- sizeof
helpviewer_keywords: sizeof keyword [C#]
ms.assetid: c548592c-677c-4f40-a4ce-e613f7529141
caps.latest.revision: "20"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0148ae8381804ca9286315251582c8ab40778369
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="sizeof-c-reference"></a><span data-ttu-id="1c3c1-102">sizeof (référence C#)</span><span class="sxs-lookup"><span data-stu-id="1c3c1-102">sizeof (C# Reference)</span></span>
<span data-ttu-id="1c3c1-103">Permet d’obtenir la taille en octets d’un type non managé.</span><span class="sxs-lookup"><span data-stu-id="1c3c1-103">Used to obtain the size in bytes for an unmanaged type.</span></span> <span data-ttu-id="1c3c1-104">Les types non managés incluent les types intégrés qui sont répertoriés dans le tableau ci-dessous, ainsi que les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="1c3c1-104">Unmanaged types include the built-in types that are listed in the table that follows, and also the following:</span></span>  
  
-   <span data-ttu-id="1c3c1-105">Types d'enum</span><span class="sxs-lookup"><span data-stu-id="1c3c1-105">Enum types</span></span>  
  
-   <span data-ttu-id="1c3c1-106">Types de pointeur</span><span class="sxs-lookup"><span data-stu-id="1c3c1-106">Pointer types</span></span>  
  
-   <span data-ttu-id="1c3c1-107">Les structs définis par l'utilisateur qui ne contiennent pas de champs ou de propriétés qui sont de type référence</span><span class="sxs-lookup"><span data-stu-id="1c3c1-107">User-defined structs that do not contain any fields or properties that are reference types</span></span>  
  
 <span data-ttu-id="1c3c1-108">L’exemple suivant montre comment extraire la taille d’un `int` :</span><span class="sxs-lookup"><span data-stu-id="1c3c1-108">The following example shows how to retrieve the size of an `int`:</span></span>  
  
```csharp  
// Constant value 4:  
int intSize = sizeof(int);   
```  
  
## <a name="remarks"></a><span data-ttu-id="1c3c1-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="1c3c1-109">Remarks</span></span>  
 <span data-ttu-id="1c3c1-110">Depuis la version 2.0 de C#, l’application de `sizeof` à des types intégrés ne nécessite plus l’utilisation du mode [unsafe](../../../csharp/language-reference/keywords/unsafe.md).</span><span class="sxs-lookup"><span data-stu-id="1c3c1-110">Starting with version 2.0 of C#, applying `sizeof` to built-in types no longer requires that [unsafe](../../../csharp/language-reference/keywords/unsafe.md) mode be used.</span></span>  
  
 <span data-ttu-id="1c3c1-111">L’opérateur `sizeof` ne peut pas être surchargé.</span><span class="sxs-lookup"><span data-stu-id="1c3c1-111">The `sizeof` operator cannot be overloaded.</span></span> <span data-ttu-id="1c3c1-112">Les valeurs retournées par l’opérateur `sizeof` sont du type `int`.</span><span class="sxs-lookup"><span data-stu-id="1c3c1-112">The values returned by the `sizeof` operator are of type `int`.</span></span> <span data-ttu-id="1c3c1-113">Le tableau suivant indique les valeurs constantes qui sont substituées aux expressions `sizeof` qui ont certains types intégrés comme opérandes.</span><span class="sxs-lookup"><span data-stu-id="1c3c1-113">The following table shows the constant values that are substituted for `sizeof` expressions that have certain built-in types as operands.</span></span>  
  
|<span data-ttu-id="1c3c1-114">Expression</span><span class="sxs-lookup"><span data-stu-id="1c3c1-114">Expression</span></span>|<span data-ttu-id="1c3c1-115">Valeur constante</span><span class="sxs-lookup"><span data-stu-id="1c3c1-115">Constant value</span></span>|  
|----------------|--------------------|  
|`sizeof(sbyte)`|<span data-ttu-id="1c3c1-116">1</span><span class="sxs-lookup"><span data-stu-id="1c3c1-116">1</span></span>|  
|`sizeof(byte)`|<span data-ttu-id="1c3c1-117">1</span><span class="sxs-lookup"><span data-stu-id="1c3c1-117">1</span></span>|  
|`sizeof(short)`|<span data-ttu-id="1c3c1-118">2</span><span class="sxs-lookup"><span data-stu-id="1c3c1-118">2</span></span>|  
|`sizeof(ushort)`|<span data-ttu-id="1c3c1-119">2</span><span class="sxs-lookup"><span data-stu-id="1c3c1-119">2</span></span>|  
|`sizeof(int)`|<span data-ttu-id="1c3c1-120">4</span><span class="sxs-lookup"><span data-stu-id="1c3c1-120">4</span></span>|  
|`sizeof(uint)`|<span data-ttu-id="1c3c1-121">4</span><span class="sxs-lookup"><span data-stu-id="1c3c1-121">4</span></span>|  
|`sizeof(long)`|<span data-ttu-id="1c3c1-122">8</span><span class="sxs-lookup"><span data-stu-id="1c3c1-122">8</span></span>|  
|`sizeof(ulong)`|<span data-ttu-id="1c3c1-123">8</span><span class="sxs-lookup"><span data-stu-id="1c3c1-123">8</span></span>|  
|`sizeof(char)`|<span data-ttu-id="1c3c1-124">2 (Unicode)</span><span class="sxs-lookup"><span data-stu-id="1c3c1-124">2 (Unicode)</span></span>|  
|`sizeof(float)`|<span data-ttu-id="1c3c1-125">4</span><span class="sxs-lookup"><span data-stu-id="1c3c1-125">4</span></span>|  
|`sizeof(double)`|<span data-ttu-id="1c3c1-126">8</span><span class="sxs-lookup"><span data-stu-id="1c3c1-126">8</span></span>|  
|`sizeof(decimal)`|<span data-ttu-id="1c3c1-127">16</span><span class="sxs-lookup"><span data-stu-id="1c3c1-127">16</span></span>|  
|`sizeof(bool)`|<span data-ttu-id="1c3c1-128">1</span><span class="sxs-lookup"><span data-stu-id="1c3c1-128">1</span></span>|  
  
 <span data-ttu-id="1c3c1-129">Pour tous les autres types, y compris les structs, l’opérateur `sizeof` peut être utilisé uniquement dans les blocs de code unsafe.</span><span class="sxs-lookup"><span data-stu-id="1c3c1-129">For all other types, including structs, the `sizeof` operator can be used only in unsafe code blocks.</span></span> <span data-ttu-id="1c3c1-130">Bien que vous puissiez utiliser la méthode <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType>, la valeur retournée par cette méthode n’est pas toujours identique à celle retournée par `sizeof`.</span><span class="sxs-lookup"><span data-stu-id="1c3c1-130">Although you can use the <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> method, the value returned by this method is not always the same as the value returned by `sizeof`.</span></span> <span data-ttu-id="1c3c1-131"><xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> retourne la taille après que le type a été marshalé, alors que `sizeof` retourne la taille telle qu’elle a été allouée par le Common Language Runtime, dont la marge intérieure.</span><span class="sxs-lookup"><span data-stu-id="1c3c1-131"><xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> returns the size after the type has been marshaled, whereas `sizeof` returns the size as it has been allocated by the common language runtime, including any padding.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1c3c1-132">Exemple</span><span class="sxs-lookup"><span data-stu-id="1c3c1-132">Example</span></span>  
 [!code-csharp[csrefKeywordsOperator#11](../../../csharp/language-reference/keywords/codesnippet/CSharp/sizeof_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="1c3c1-133">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="1c3c1-133">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1c3c1-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1c3c1-134">See Also</span></span>  
 [<span data-ttu-id="1c3c1-135">Référence C#</span><span class="sxs-lookup"><span data-stu-id="1c3c1-135">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="1c3c1-136">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="1c3c1-136">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="1c3c1-137">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="1c3c1-137">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="1c3c1-138">Mots clés des opérateurs</span><span class="sxs-lookup"><span data-stu-id="1c3c1-138">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)  
 [<span data-ttu-id="1c3c1-139">enum</span><span class="sxs-lookup"><span data-stu-id="1c3c1-139">enum</span></span>](../../../csharp/language-reference/keywords/enum.md)  
 [<span data-ttu-id="1c3c1-140">Pointeurs et code unsafe</span><span class="sxs-lookup"><span data-stu-id="1c3c1-140">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
 [<span data-ttu-id="1c3c1-141">Structs</span><span class="sxs-lookup"><span data-stu-id="1c3c1-141">Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/structs.md)  
 [<span data-ttu-id="1c3c1-142">Constantes</span><span class="sxs-lookup"><span data-stu-id="1c3c1-142">Constants</span></span>](../../../csharp/programming-guide/classes-and-structs/constants.md)
