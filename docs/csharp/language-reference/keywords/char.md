---
title: "char (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- char
- char_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- char data type [C#]
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
caps.latest.revision: 27
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
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: c6601a58804d6ecfcbedbc19da09560884e54e7f
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="char-c-reference"></a><span data-ttu-id="beb20-102">char (référence C#)</span><span class="sxs-lookup"><span data-stu-id="beb20-102">char (C# Reference)</span></span>
<span data-ttu-id="beb20-103">Le mot clé `char` permet de déclarer une instance de la structure <xref:System.Char?displayProperty=fullName> utilisée par le .NET Framework pour représenter un caractère Unicode.</span><span class="sxs-lookup"><span data-stu-id="beb20-103">The `char` keyword is used to declare an instance of the <xref:System.Char?displayProperty=fullName> structure that the .NET Framework uses to represent a Unicode character.</span></span> <span data-ttu-id="beb20-104">La valeur d’un objet `Char` est une valeur numérique 16 bits (ordinale).</span><span class="sxs-lookup"><span data-stu-id="beb20-104">The value of a `Char` object is a 16-bit numeric (ordinal) value.</span></span>  
  
 <span data-ttu-id="beb20-105">Les caractères Unicode sont utilisés pour représenter la plupart des langues écrites dans le monde.</span><span class="sxs-lookup"><span data-stu-id="beb20-105">Unicode characters are used to represent most of the written languages throughout the world.</span></span>  
  
|<span data-ttu-id="beb20-106">Type</span><span class="sxs-lookup"><span data-stu-id="beb20-106">Type</span></span>|<span data-ttu-id="beb20-107">Plage</span><span class="sxs-lookup"><span data-stu-id="beb20-107">Range</span></span>|<span data-ttu-id="beb20-108">Taille</span><span class="sxs-lookup"><span data-stu-id="beb20-108">Size</span></span>|<span data-ttu-id="beb20-109">Type .NET Framework</span><span class="sxs-lookup"><span data-stu-id="beb20-109">.NET Framework type</span></span>|  
|----------|-----------|----------|-------------------------|  
|`char`|<span data-ttu-id="beb20-110">U+0000 à U+FFFF</span><span class="sxs-lookup"><span data-stu-id="beb20-110">U+0000 to U+FFFF</span></span>|<span data-ttu-id="beb20-111">Caractère Unicode 16 bits</span><span class="sxs-lookup"><span data-stu-id="beb20-111">Unicode 16-bit character</span></span>|<xref:System.Char?displayProperty=fullName>|  
  
## <a name="literals"></a><span data-ttu-id="beb20-112">Littéraux</span><span class="sxs-lookup"><span data-stu-id="beb20-112">Literals</span></span>  
 <span data-ttu-id="beb20-113">Les constantes de type `char` peuvent être représentées sous la forme de littéraux de caractères, d’une séquence d’échappement hexadécimale ou d’une représentation Unicode.</span><span class="sxs-lookup"><span data-stu-id="beb20-113">Constants of the `char` type can be written as character literals, hexadecimal escape sequence, or Unicode representation.</span></span> <span data-ttu-id="beb20-114">Vous pouvez également effectuer un cast des codes de caractères de type intégral.</span><span class="sxs-lookup"><span data-stu-id="beb20-114">You can also cast the integral character codes.</span></span> <span data-ttu-id="beb20-115">Dans l’exemple suivant, quatre variables `char` sont initialisées avec le même caractère (`X`) :</span><span class="sxs-lookup"><span data-stu-id="beb20-115">In the following example four `char` variables are initialized with the same character `X`:</span></span>  
  
 <span data-ttu-id="beb20-116">[!code-cs[csrefKeywordsTypes#19](../../../csharp/language-reference/keywords/codesnippet/CSharp/char_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="beb20-116">[!code-cs[csrefKeywordsTypes#19](../../../csharp/language-reference/keywords/codesnippet/CSharp/char_1.cs)]</span></span>  
  
## <a name="conversions"></a><span data-ttu-id="beb20-117">Conversions</span><span class="sxs-lookup"><span data-stu-id="beb20-117">Conversions</span></span>  
 <span data-ttu-id="beb20-118">Vous pouvez convertir implicitement un `char` en [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md) ou [decimal](../../../csharp/language-reference/keywords/decimal.md).</span><span class="sxs-lookup"><span data-stu-id="beb20-118">A `char` can be implicitly converted to [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span> <span data-ttu-id="beb20-119">Par contre, vous ne pouvez pas convertir implicitement d’autres types en type `char`.</span><span class="sxs-lookup"><span data-stu-id="beb20-119">However, there are no implicit conversions from other types to the `char` type.</span></span>  
  
 <span data-ttu-id="beb20-120">Le type <xref:System.Char?displayProperty=fullName> fournit plusieurs méthodes statiques à utiliser avec des valeurs `char`.</span><span class="sxs-lookup"><span data-stu-id="beb20-120">The <xref:System.Char?displayProperty=fullName> type provides several static methods for working with `char` values.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="beb20-121">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="beb20-121">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="beb20-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="beb20-122">See Also</span></span>  
 <span data-ttu-id="beb20-123"><xref:System.Char></span><span class="sxs-lookup"><span data-stu-id="beb20-123"><xref:System.Char></span></span>   
 <span data-ttu-id="beb20-124">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="beb20-124">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="beb20-125">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="beb20-125">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="beb20-126">[Mots clés C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="beb20-126">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="beb20-127">[Tableau des types intégraux](../../../csharp/language-reference/keywords/integral-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="beb20-127">[Integral Types Table](../../../csharp/language-reference/keywords/integral-types-table.md) </span></span>  
 <span data-ttu-id="beb20-128">[Tableau des types intégrés](../../../csharp/language-reference/keywords/built-in-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="beb20-128">[Built-In Types Table](../../../csharp/language-reference/keywords/built-in-types-table.md) </span></span>  
 <span data-ttu-id="beb20-129">[Tableau des conversions numériques implicites](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md) </span><span class="sxs-lookup"><span data-stu-id="beb20-129">[Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md) </span></span>  
 <span data-ttu-id="beb20-130">[Tableau des conversions numériques explicites](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md) </span><span class="sxs-lookup"><span data-stu-id="beb20-130">[Explicit Numeric Conversions Table](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md) </span></span>  
 <span data-ttu-id="beb20-131">[Types Nullable](../../../csharp/programming-guide/nullable-types/index.md) </span><span class="sxs-lookup"><span data-stu-id="beb20-131">[Nullable Types](../../../csharp/programming-guide/nullable-types/index.md) </span></span>  
 [<span data-ttu-id="beb20-132">Chaînes</span><span class="sxs-lookup"><span data-stu-id="beb20-132">Strings</span></span>](../../../csharp/programming-guide/strings/index.md)

