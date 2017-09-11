---
title: "sizeof (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- sizeof_CSharpKeyword
- sizeof
dev_langs:
- CSharp
helpviewer_keywords:
- sizeof keyword [C#]
ms.assetid: c548592c-677c-4f40-a4ce-e613f7529141
caps.latest.revision: 20
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
ms.openlocfilehash: 15d11071c369fad398d40cfef301e462c006d5e4
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="sizeof-c-reference"></a><span data-ttu-id="9e1d8-102">sizeof (référence C#)</span><span class="sxs-lookup"><span data-stu-id="9e1d8-102">sizeof (C# Reference)</span></span>
<span data-ttu-id="9e1d8-103">Permet d’obtenir la taille en octets d’un type non managé.</span><span class="sxs-lookup"><span data-stu-id="9e1d8-103">Used to obtain the size in bytes for an unmanaged type.</span></span> <span data-ttu-id="9e1d8-104">Les types non managés incluent les types intégrés qui sont répertoriés dans le tableau ci-dessous, ainsi que les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="9e1d8-104">Unmanaged types include the built-in types that are listed in the table that follows, and also the following:</span></span>  
  
-   <span data-ttu-id="9e1d8-105">Types d'enum</span><span class="sxs-lookup"><span data-stu-id="9e1d8-105">Enum types</span></span>  
  
-   <span data-ttu-id="9e1d8-106">Types de pointeur</span><span class="sxs-lookup"><span data-stu-id="9e1d8-106">Pointer types</span></span>  
  
-   <span data-ttu-id="9e1d8-107">Les structs définis par l'utilisateur qui ne contiennent pas de champs ou de propriétés qui sont de type référence</span><span class="sxs-lookup"><span data-stu-id="9e1d8-107">User-defined structs that do not contain any fields or properties that are reference types</span></span>  
  
 <span data-ttu-id="9e1d8-108">L’exemple suivant montre comment extraire la taille d’un `int` :</span><span class="sxs-lookup"><span data-stu-id="9e1d8-108">The following example shows how to retrieve the size of an `int`:</span></span>  
  
```csharp  
// Constant value 4:  
int intSize = sizeof(int);   
```  
  
## <a name="remarks"></a><span data-ttu-id="9e1d8-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="9e1d8-109">Remarks</span></span>  
 <span data-ttu-id="9e1d8-110">Depuis la version 2.0 de C#, l’application de `sizeof` à des types intégrés ne nécessite plus l’utilisation du mode [unsafe](../../../csharp/language-reference/keywords/unsafe.md).</span><span class="sxs-lookup"><span data-stu-id="9e1d8-110">Starting with version 2.0 of C#, applying `sizeof` to built-in types no longer requires that [unsafe](../../../csharp/language-reference/keywords/unsafe.md) mode be used.</span></span>  
  
 <span data-ttu-id="9e1d8-111">L’opérateur `sizeof` ne peut pas être surchargé.</span><span class="sxs-lookup"><span data-stu-id="9e1d8-111">The `sizeof` operator cannot be overloaded.</span></span> <span data-ttu-id="9e1d8-112">Les valeurs retournées par l’opérateur `sizeof` sont du type `int`.</span><span class="sxs-lookup"><span data-stu-id="9e1d8-112">The values returned by the `sizeof` operator are of type `int`.</span></span> <span data-ttu-id="9e1d8-113">Le tableau suivant indique les valeurs constantes qui sont substituées aux expressions `sizeof` qui ont certains types intégrés comme opérandes.</span><span class="sxs-lookup"><span data-stu-id="9e1d8-113">The following table shows the constant values that are substituted for `sizeof` expressions that have certain built-in types as operands.</span></span>  
  
|<span data-ttu-id="9e1d8-114">Expression</span><span class="sxs-lookup"><span data-stu-id="9e1d8-114">Expression</span></span>|<span data-ttu-id="9e1d8-115">Valeur constante</span><span class="sxs-lookup"><span data-stu-id="9e1d8-115">Constant value</span></span>|  
|----------------|--------------------|  
|`sizeof(sbyte)`|<span data-ttu-id="9e1d8-116">1</span><span class="sxs-lookup"><span data-stu-id="9e1d8-116">1</span></span>|  
|`sizeof(byte)`|<span data-ttu-id="9e1d8-117">1</span><span class="sxs-lookup"><span data-stu-id="9e1d8-117">1</span></span>|  
|`sizeof(short)`|<span data-ttu-id="9e1d8-118">2</span><span class="sxs-lookup"><span data-stu-id="9e1d8-118">2</span></span>|  
|`sizeof(ushort)`|<span data-ttu-id="9e1d8-119">2</span><span class="sxs-lookup"><span data-stu-id="9e1d8-119">2</span></span>|  
|`sizeof(int)`|<span data-ttu-id="9e1d8-120">4</span><span class="sxs-lookup"><span data-stu-id="9e1d8-120">4</span></span>|  
|`sizeof(uint)`|<span data-ttu-id="9e1d8-121">4</span><span class="sxs-lookup"><span data-stu-id="9e1d8-121">4</span></span>|  
|`sizeof(long)`|<span data-ttu-id="9e1d8-122">8</span><span class="sxs-lookup"><span data-stu-id="9e1d8-122">8</span></span>|  
|`sizeof(ulong)`|<span data-ttu-id="9e1d8-123">8</span><span class="sxs-lookup"><span data-stu-id="9e1d8-123">8</span></span>|  
|`sizeof(char)`|<span data-ttu-id="9e1d8-124">2 (Unicode)</span><span class="sxs-lookup"><span data-stu-id="9e1d8-124">2 (Unicode)</span></span>|  
|`sizeof(float)`|<span data-ttu-id="9e1d8-125">4</span><span class="sxs-lookup"><span data-stu-id="9e1d8-125">4</span></span>|  
|`sizeof(double)`|<span data-ttu-id="9e1d8-126">8</span><span class="sxs-lookup"><span data-stu-id="9e1d8-126">8</span></span>|  
|`sizeof(decimal)`|<span data-ttu-id="9e1d8-127">16</span><span class="sxs-lookup"><span data-stu-id="9e1d8-127">16</span></span>|  
|`sizeof(bool)`|<span data-ttu-id="9e1d8-128">1</span><span class="sxs-lookup"><span data-stu-id="9e1d8-128">1</span></span>|  
  
 <span data-ttu-id="9e1d8-129">Pour tous les autres types, y compris les structs, l’opérateur `sizeof` peut être utilisé uniquement dans les blocs de code unsafe.</span><span class="sxs-lookup"><span data-stu-id="9e1d8-129">For all other types, including structs, the `sizeof` operator can be used only in unsafe code blocks.</span></span> <span data-ttu-id="9e1d8-130">Bien que vous puissiez utiliser la méthode <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=fullName>, la valeur retournée par cette méthode n’est pas toujours identique à celle retournée par `sizeof`.</span><span class="sxs-lookup"><span data-stu-id="9e1d8-130">Although you can use the <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=fullName> method, the value returned by this method is not always the same as the value returned by `sizeof`.</span></span> <span data-ttu-id="9e1d8-131"><xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=fullName> retourne la taille après que le type a été marshalé, alors que `sizeof` retourne la taille telle qu’elle a été allouée par le Common Language Runtime, dont la marge intérieure.</span><span class="sxs-lookup"><span data-stu-id="9e1d8-131"><xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=fullName> returns the size after the type has been marshaled, whereas `sizeof` returns the size as it has been allocated by the common language runtime, including any padding.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9e1d8-132">Exemple</span><span class="sxs-lookup"><span data-stu-id="9e1d8-132">Example</span></span>  
 <span data-ttu-id="9e1d8-133">[!code-cs[csrefKeywordsOperator#11](../../../csharp/language-reference/keywords/codesnippet/CSharp/sizeof_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="9e1d8-133">[!code-cs[csrefKeywordsOperator#11](../../../csharp/language-reference/keywords/codesnippet/CSharp/sizeof_1.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="9e1d8-134">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="9e1d8-134">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9e1d8-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9e1d8-135">See Also</span></span>  
 <span data-ttu-id="9e1d8-136">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="9e1d8-136">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="9e1d8-137">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="9e1d8-137">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="9e1d8-138">[Mots clés C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="9e1d8-138">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="9e1d8-139">[Mots clés des opérateurs](../../../csharp/language-reference/keywords/operator-keywords.md) </span><span class="sxs-lookup"><span data-stu-id="9e1d8-139">[Operator Keywords](../../../csharp/language-reference/keywords/operator-keywords.md) </span></span>  
 <span data-ttu-id="9e1d8-140">[enum](../../../csharp/language-reference/keywords/enum.md) </span><span class="sxs-lookup"><span data-stu-id="9e1d8-140">[enum](../../../csharp/language-reference/keywords/enum.md) </span></span>  
 <span data-ttu-id="9e1d8-141">[Pointeurs et code unsafe](../../../csharp/programming-guide/unsafe-code-pointers/index.md) </span><span class="sxs-lookup"><span data-stu-id="9e1d8-141">[Unsafe Code and Pointers](../../../csharp/programming-guide/unsafe-code-pointers/index.md) </span></span>  
 <span data-ttu-id="9e1d8-142">[Structs](../../../csharp/programming-guide/classes-and-structs/structs.md) </span><span class="sxs-lookup"><span data-stu-id="9e1d8-142">[Structs](../../../csharp/programming-guide/classes-and-structs/structs.md) </span></span>  
 [<span data-ttu-id="9e1d8-143">Constantes</span><span class="sxs-lookup"><span data-stu-id="9e1d8-143">Constants</span></span>](../../../csharp/programming-guide/classes-and-structs/constants.md)

