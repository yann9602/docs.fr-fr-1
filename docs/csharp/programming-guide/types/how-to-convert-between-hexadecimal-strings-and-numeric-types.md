---
title: "Guide pratique pour effectuer une conversion entre des chaînes hexadécimales et des types numériques (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- hexadecimal strings [C#], converting to numeric type
- conversions [C#], hexidecimal strings
- strings [C#], converting hexadecimal strings
- hexadecimal strings [C#]
ms.assetid: 7115c49f-7d1d-40c3-8bd9-aae0cc1d46b6
caps.latest.revision: 19
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
ms.openlocfilehash: 312b18e6bf30ace166435e51b1b83937b5c6bf38
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-convert-between-hexadecimal-strings-and-numeric-types-c-programming-guide"></a><span data-ttu-id="6d7d5-102">Guide pratique pour effectuer une conversion entre des chaînes hexadécimales et des types numériques (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="6d7d5-102">How to: Convert Between Hexadecimal Strings and Numeric Types (C# Programming Guide)</span></span>
<span data-ttu-id="6d7d5-103">Ces exemples montrent comment effectuer les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="6d7d5-103">These examples show you how to perform the following tasks:</span></span>  
  
-   <span data-ttu-id="6d7d5-104">Obtenir la valeur hexadécimale de chaque caractère dans une chaîne ([string](../../../csharp/language-reference/keywords/string.md)).</span><span class="sxs-lookup"><span data-stu-id="6d7d5-104">Obtain the hexadecimal value of each character in a [string](../../../csharp/language-reference/keywords/string.md).</span></span>  
  
-   <span data-ttu-id="6d7d5-105">Obtenir la valeur [char](../../../csharp/language-reference/keywords/char.md) qui correspond à chaque valeur d’une chaîne hexadécimale.</span><span class="sxs-lookup"><span data-stu-id="6d7d5-105">Obtain the [char](../../../csharp/language-reference/keywords/char.md) that corresponds to each value in a hexadecimal string.</span></span>  
  
-   <span data-ttu-id="6d7d5-106">Convertir une `string` hexadécimale en [int](../../../csharp/language-reference/keywords/int.md).</span><span class="sxs-lookup"><span data-stu-id="6d7d5-106">Convert a hexadecimal `string` to an [int](../../../csharp/language-reference/keywords/int.md).</span></span>  
  
-   <span data-ttu-id="6d7d5-107">Convertir une `string` hexadécimale en [float](../../../csharp/language-reference/keywords/float.md).</span><span class="sxs-lookup"><span data-stu-id="6d7d5-107">Convert a hexadecimal `string` to a [float](../../../csharp/language-reference/keywords/float.md).</span></span>  
  
-   <span data-ttu-id="6d7d5-108">Convertir un tableau d’[octets](../../../csharp/language-reference/keywords/byte.md) en `string` hexadécimale.</span><span class="sxs-lookup"><span data-stu-id="6d7d5-108">Convert a [byte](../../../csharp/language-reference/keywords/byte.md) array to a hexadecimal `string`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d7d5-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="6d7d5-109">Example</span></span>  
 <span data-ttu-id="6d7d5-110">Cet exemple génère la valeur hexadécimale de chaque caractère dans une `string`.</span><span class="sxs-lookup"><span data-stu-id="6d7d5-110">This example outputs the hexadecimal value of each character in a `string`.</span></span> <span data-ttu-id="6d7d5-111">Il convertit d’abord la `string` en un tableau de caractères.</span><span class="sxs-lookup"><span data-stu-id="6d7d5-111">First it parses the `string` to an array of characters.</span></span> <span data-ttu-id="6d7d5-112">Ensuite, il appelle <xref:System.Convert.ToInt32%28System.Char%29> sur chaque caractère afin d’obtenir sa valeur numérique.</span><span class="sxs-lookup"><span data-stu-id="6d7d5-112">Then it calls <xref:System.Convert.ToInt32%28System.Char%29> on each character to obtain its numeric value.</span></span> <span data-ttu-id="6d7d5-113">Pour finir, il représente le nombre sous forme hexadécimale dans une `string`.</span><span class="sxs-lookup"><span data-stu-id="6d7d5-113">Finally, it formats the number as its hexadecimal representation in a `string`.</span></span>  
  
 <span data-ttu-id="6d7d5-114">[!code-cs[csProgGuideTypes#30](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-between-hexadecimal-strings-and-numeric-types_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="6d7d5-114">[!code-cs[csProgGuideTypes#30](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-between-hexadecimal-strings-and-numeric-types_1.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d7d5-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="6d7d5-115">Example</span></span>  
 <span data-ttu-id="6d7d5-116">Cet exemple analyse une `string` de valeurs hexadécimales et génère le caractère correspondant à chacune d’elles.</span><span class="sxs-lookup"><span data-stu-id="6d7d5-116">This example parses a `string` of hexadecimal values and outputs the character corresponding to each hexadecimal value.</span></span> <span data-ttu-id="6d7d5-117">Il appelle d’abord la méthode [Split(Char\[\])](xref:System.String.Split(System.Char[])) pour obtenir chaque valeur hexadécimale sous la forme d’une `string` individuelle dans un tableau.</span><span class="sxs-lookup"><span data-stu-id="6d7d5-117">First it calls the [Split(Char\[\])](xref:System.String.Split(System.Char[])) method to obtain each hexadecimal value as an individual `string` in an array.</span></span> <span data-ttu-id="6d7d5-118">Ensuite, il appelle <xref:System.Convert.ToInt32%28System.String%2CSystem.Int32%29> pour convertir la valeur hexadécimale en valeur décimale représentée sous forme d’objet [int](../../../csharp/language-reference/keywords/int.md).</span><span class="sxs-lookup"><span data-stu-id="6d7d5-118">Then it calls <xref:System.Convert.ToInt32%28System.String%2CSystem.Int32%29> to convert the hexadecimal value to a decimal value represented as an [int](../../../csharp/language-reference/keywords/int.md).</span></span> <span data-ttu-id="6d7d5-119">Il illustre deux manières d’obtenir le caractère correspondant à ce code de caractère.</span><span class="sxs-lookup"><span data-stu-id="6d7d5-119">It shows two different ways to obtain the character corresponding to that character code.</span></span> <span data-ttu-id="6d7d5-120">La première technique utilise `string`, qui retourne le caractère correspondant à l’argument entier sous forme de <xref:System.Char.ConvertFromUtf32%28System.Int32%29>.</span><span class="sxs-lookup"><span data-stu-id="6d7d5-120">The first technique uses <xref:System.Char.ConvertFromUtf32%28System.Int32%29>, which returns the character corresponding to the integer argument as a `string`.</span></span> <span data-ttu-id="6d7d5-121">La deuxième technique effectue un cast explicite de l’`int` en [char](../../../csharp/language-reference/keywords/char.md).</span><span class="sxs-lookup"><span data-stu-id="6d7d5-121">The second technique explicitly casts the `int` to a [char](../../../csharp/language-reference/keywords/char.md).</span></span>  
  
 <span data-ttu-id="6d7d5-122">[!code-cs[csProgGuideTypes#31](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-between-hexadecimal-strings-and-numeric-types_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="6d7d5-122">[!code-cs[csProgGuideTypes#31](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-between-hexadecimal-strings-and-numeric-types_2.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d7d5-123">Exemple</span><span class="sxs-lookup"><span data-stu-id="6d7d5-123">Example</span></span>  
 <span data-ttu-id="6d7d5-124">Cet exemple montre une autre façon de convertir un `string` hexadécimal en entier, en appelant la méthode <xref:System.Int32.Parse%28System.String%2CSystem.Globalization.NumberStyles%29>.</span><span class="sxs-lookup"><span data-stu-id="6d7d5-124">This example shows another way to convert a hexadecimal `string` to an integer, by calling the <xref:System.Int32.Parse%28System.String%2CSystem.Globalization.NumberStyles%29> method.</span></span>  
  
 <span data-ttu-id="6d7d5-125">[!code-cs[csProgGuideTypes#32](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-between-hexadecimal-strings-and-numeric-types_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="6d7d5-125">[!code-cs[csProgGuideTypes#32](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-between-hexadecimal-strings-and-numeric-types_3.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d7d5-126">Exemple</span><span class="sxs-lookup"><span data-stu-id="6d7d5-126">Example</span></span>  
 <span data-ttu-id="6d7d5-127">L’exemple suivant montre comment convertir un `string` hexadécimal en [float](../../../csharp/language-reference/keywords/float.md) à l’aide de la classe <xref:System.BitConverter?displayProperty=fullName> et de la méthode <xref:System.Int32.Parse%2A?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="6d7d5-127">The following example shows how to convert a hexadecimal `string` to a [float](../../../csharp/language-reference/keywords/float.md) by using the <xref:System.BitConverter?displayProperty=fullName> class and the <xref:System.Int32.Parse%2A?displayProperty=fullName> method.</span></span>  
  
 <span data-ttu-id="6d7d5-128">[!code-cs[csProgGuideTypes#39](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-between-hexadecimal-strings-and-numeric-types_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="6d7d5-128">[!code-cs[csProgGuideTypes#39](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-between-hexadecimal-strings-and-numeric-types_4.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d7d5-129">Exemple</span><span class="sxs-lookup"><span data-stu-id="6d7d5-129">Example</span></span>  
 <span data-ttu-id="6d7d5-130">L’exemple suivant montre comment convertir un tableau d’[octets](../../../csharp/language-reference/keywords/byte.md) en chaîne hexadécimale à l’aide de la classe <xref:System.BitConverter?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="6d7d5-130">The following example shows how to convert a [byte](../../../csharp/language-reference/keywords/byte.md) array to a hexadecimal string by using the <xref:System.BitConverter?displayProperty=fullName> class.</span></span>  
  
 <span data-ttu-id="6d7d5-131">[!code-cs[csProgGuideTypes#38](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-between-hexadecimal-strings-and-numeric-types_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="6d7d5-131">[!code-cs[csProgGuideTypes#38](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-between-hexadecimal-strings-and-numeric-types_5.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d7d5-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6d7d5-132">See Also</span></span>  
 <span data-ttu-id="6d7d5-133">[Chaînes de format numériques standard](../../../standard/base-types/standard-numeric-format-strings.md) </span><span class="sxs-lookup"><span data-stu-id="6d7d5-133">[Standard Numeric Format Strings](../../../standard/base-types/standard-numeric-format-strings.md) </span></span>  
 <span data-ttu-id="6d7d5-134">[Types](../../../csharp/programming-guide/types/index.md) </span><span class="sxs-lookup"><span data-stu-id="6d7d5-134">[Types](../../../csharp/programming-guide/types/index.md) </span></span>  
 [<span data-ttu-id="6d7d5-135">Guide pratique pour déterminer si une chaîne représente une valeur numérique</span><span class="sxs-lookup"><span data-stu-id="6d7d5-135">How to: Determine Whether a String Represents a Numeric Value</span></span>](../../../csharp/programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)

