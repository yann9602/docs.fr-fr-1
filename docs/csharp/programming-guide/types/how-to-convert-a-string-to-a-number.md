---
title: "Guide pratique pour convertir une chaîne en nombre (Guide de programmation C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- conversions [C#]
- conversions [C#], string to int
- converting strings to int [C#]
- strings [C#], converting to int
ms.assetid: 467b9979-86ee-4afd-b734-30299cda91e3
caps.latest.revision: "34"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 3dc67bc2f25bba14df0e3ce6859bb8bc9094871c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-convert-a-string-to-a-number-c-programming-guide"></a><span data-ttu-id="19cec-102">Guide pratique pour convertir une chaîne en nombre (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="19cec-102">How to: Convert a String to a Number (C# Programming Guide)</span></span>
<span data-ttu-id="19cec-103">Vous pouvez convertir une [chaîne](../../../csharp/language-reference/keywords/string.md) en nombre en utilisant des méthodes dans la classe <xref:System.Convert> ou en utilisant la méthode `TryParse` des différents types numériques (int, long, float, etc.).</span><span class="sxs-lookup"><span data-stu-id="19cec-103">You can convert a [string](../../../csharp/language-reference/keywords/string.md) to a number by using methods in the <xref:System.Convert> class or by using the `TryParse` method found on the various numeric types (int, long, float, etc.).</span></span>  
  
 <span data-ttu-id="19cec-104">Si vous avez une chaîne, il est légèrement plus efficace et direct d'appeler une méthode `TryParse` (par exemple, `int.TryParse("11")`).</span><span class="sxs-lookup"><span data-stu-id="19cec-104">If you have a string, it is slightly more efficient and straightforward to call a `TryParse` method (for example, `int.TryParse("11")`).</span></span>  <span data-ttu-id="19cec-105">L'utilisation d'une méthode `Convert` s'avère plus utile pour les objets généraux qui implémentent <xref:System.IConvertible>.</span><span class="sxs-lookup"><span data-stu-id="19cec-105">Using a `Convert` method is more useful for general objects that implement <xref:System.IConvertible>.</span></span>  
  
 <span data-ttu-id="19cec-106">Vous pouvez utiliser les méthodes `Parse` ou `TryParse` sur le type numérique que doit contenir la chaîne, notamment le type <xref:System.Int32?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="19cec-106">You can use `Parse` or `TryParse` methods on the numeric type you expect the string contains, such as the <xref:System.Int32?displayProperty=nameWithType> type.</span></span>  <span data-ttu-id="19cec-107">La méthode <xref:System.Convert.ToUInt32%2A?displayProperty=nameWithType> utilise <xref:System.Int32.Parse%2A> en interne.</span><span class="sxs-lookup"><span data-stu-id="19cec-107">The <xref:System.Convert.ToUInt32%2A?displayProperty=nameWithType> method uses <xref:System.Int32.Parse%2A> internally.</span></span>  <span data-ttu-id="19cec-108">Si le format de la chaîne n’est pas valide, `Parse` lève une exception, tandis que `TryParse` retourne [false](../../../csharp/language-reference/keywords/false.md).</span><span class="sxs-lookup"><span data-stu-id="19cec-108">If the string is not in a valid format, `Parse` throws an exception whereas `TryParse` returns [false](../../../csharp/language-reference/keywords/false.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="19cec-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="19cec-109">Example</span></span>  
 <span data-ttu-id="19cec-110">Les méthodes `Parse` et `TryParse` ignorent l'espace blanc au début et à la fin de la chaîne, mais tous les autres caractères doivent être des caractères qui forment le type numérique approprié (int, long, ulong, float, decimal, etc.).</span><span class="sxs-lookup"><span data-stu-id="19cec-110">The `Parse` and `TryParse` methods ignore whitespace at the beginning and at the end of the string, but all other characters must be characters that form the appropriate numeric type (int, long, ulong, float, decimal, etc.).</span></span>  <span data-ttu-id="19cec-111">Tout espace blanc entre les caractères qui forment le nombre génère une erreur.</span><span class="sxs-lookup"><span data-stu-id="19cec-111">Any whitespace within the characters that form the number cause an error.</span></span>  <span data-ttu-id="19cec-112">Par exemple, vous pouvez utiliser `decimal.TryParse` pour analyser « 10 », « 10.3 », «   10   », mais vous ne pouvez pas utiliser cette méthode pour analyser 10 à partir de « 10X », « 1 0 » (notez l’espace), « 10 .3 » (notez l’espace), « 10e1 » (`float.TryParse` fonctionne ici), et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="19cec-112">For example, you can use `decimal.TryParse` to parse "10", "10.3", "  10  ", but you cannot use this method to parse 10 from "10X", "1 0" (note space), "10 .3" (note space), "10e1" (`float.TryParse` works here), and so on.</span></span>  
  
 <span data-ttu-id="19cec-113">Les exemples suivants illustrent des appels à `Parse` et `TryParse` qui ont réussi ou échoué.</span><span class="sxs-lookup"><span data-stu-id="19cec-113">The examples below demonstrate both successful and unsuccessful calls to `Parse` and `TryParse`.</span></span>  
  
 [!code-csharp[csProgGuideTypes#5555](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_1.cs)]  
[!code-csharp[csProgGuideTypes#25](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_2.cs)]  
[!code-csharp[csProgGuideTypes#26](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_3.cs)]  
[!code-csharp[csProgGuideTypes#27](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_4.cs)]  
[!code-csharp[csProgGuideTypes#28](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_5.cs)]  
[!code-csharp[csProgGuideTypes#100](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_6.cs)]  
  
## <a name="example"></a><span data-ttu-id="19cec-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="19cec-114">Example</span></span>  
 <span data-ttu-id="19cec-115">Le tableau suivant répertorie quelques unes des méthodes de la classe <xref:System.Convert> que vous pouvez utiliser.</span><span class="sxs-lookup"><span data-stu-id="19cec-115">The following table lists some of the methods from the <xref:System.Convert> class that you can use.</span></span>  
  
|<span data-ttu-id="19cec-116">Type numérique</span><span class="sxs-lookup"><span data-stu-id="19cec-116">Numeric Type</span></span>|<span data-ttu-id="19cec-117">Méthode</span><span class="sxs-lookup"><span data-stu-id="19cec-117">Method</span></span>|  
|------------------|------------|  
|`decimal`|<xref:System.Convert.ToDecimal%28System.String%29>|  
|`float`|<xref:System.Convert.ToSingle%28System.String%29>|  
|`double`|<xref:System.Convert.ToDouble%28System.String%29>|  
|`short`|<xref:System.Convert.ToInt16%28System.String%29>|  
|`int`|<xref:System.Convert.ToInt32%28System.String%29>|  
|`long`|<xref:System.Convert.ToInt64%28System.String%29>|  
|`ushort`|<xref:System.Convert.ToUInt16%28System.String%29>|  
|`uint`|<xref:System.Convert.ToUInt32%28System.String%29>|  
|`ulong`|<xref:System.Convert.ToUInt64%28System.String%29>|  
  
 <span data-ttu-id="19cec-118">Cet exemple appelle la méthode <xref:System.Convert.ToInt32%28System.String%29?displayProperty=nameWithType> pour convertir une entrée de type [chaîne](../../../csharp/language-reference/keywords/string.md) en [int](../../../csharp/language-reference/keywords/int.md).</span><span class="sxs-lookup"><span data-stu-id="19cec-118">This example calls the <xref:System.Convert.ToInt32%28System.String%29?displayProperty=nameWithType> method to convert an input [string](../../../csharp/language-reference/keywords/string.md) to an [int](../../../csharp/language-reference/keywords/int.md) .</span></span> <span data-ttu-id="19cec-119">Le code intercepte les deux exceptions les plus communes qui peuvent être levées par cette méthode, <xref:System.FormatException> et <xref:System.OverflowException>.</span><span class="sxs-lookup"><span data-stu-id="19cec-119">The code catches the two most common exceptions that can be thrown by this method, <xref:System.FormatException> and <xref:System.OverflowException>.</span></span> <span data-ttu-id="19cec-120">Si le nombre peut être incrémenté sans entraîner de dépassement au niveau de l'emplacement de stockage des entiers, le programme ajoute 1 au résultat et imprime la sortie.</span><span class="sxs-lookup"><span data-stu-id="19cec-120">If the number can be incremented without overflowing the integer storage location, the program adds 1 to the result and prints the output.</span></span>  
  
 [!code-csharp[csProgGuideTypes#5555](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_1.cs)]  
[!code-csharp[csProgGuideTypes#24](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_7.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="19cec-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="19cec-121">See Also</span></span>  
 [<span data-ttu-id="19cec-122">Types</span><span class="sxs-lookup"><span data-stu-id="19cec-122">Types</span></span>](../../../csharp/programming-guide/types/index.md)  
 [<span data-ttu-id="19cec-123">Guide pratique pour déterminer si une chaîne représente une valeur numérique</span><span class="sxs-lookup"><span data-stu-id="19cec-123">How to: Determine Whether a String Represents a Numeric Value</span></span>](../../../csharp/programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)  
 [<span data-ttu-id="19cec-124">Utilitaire de mise en forme .NET Framework 4</span><span class="sxs-lookup"><span data-stu-id="19cec-124">.NET Framework 4 Formatting Utility</span></span>](http://code.msdn.microsoft.com/NET-Framework-4-Formatting-9c4dae8d)
