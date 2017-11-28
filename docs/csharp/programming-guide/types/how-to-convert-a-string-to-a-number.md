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
# <a name="how-to-convert-a-string-to-a-number-c-programming-guide"></a>Guide pratique pour convertir une chaîne en nombre (Guide de programmation C#)
Vous pouvez convertir une [chaîne](../../../csharp/language-reference/keywords/string.md) en nombre en utilisant des méthodes dans la classe <xref:System.Convert> ou en utilisant la méthode `TryParse` des différents types numériques (int, long, float, etc.).  
  
 Si vous avez une chaîne, il est légèrement plus efficace et direct d'appeler une méthode `TryParse` (par exemple, `int.TryParse("11")`).  L'utilisation d'une méthode `Convert` s'avère plus utile pour les objets généraux qui implémentent <xref:System.IConvertible>.  
  
 Vous pouvez utiliser les méthodes `Parse` ou `TryParse` sur le type numérique que doit contenir la chaîne, notamment le type <xref:System.Int32?displayProperty=nameWithType>.  La méthode <xref:System.Convert.ToUInt32%2A?displayProperty=nameWithType> utilise <xref:System.Int32.Parse%2A> en interne.  Si le format de la chaîne n’est pas valide, `Parse` lève une exception, tandis que `TryParse` retourne [false](../../../csharp/language-reference/keywords/false.md).  
  
## <a name="example"></a>Exemple  
 Les méthodes `Parse` et `TryParse` ignorent l'espace blanc au début et à la fin de la chaîne, mais tous les autres caractères doivent être des caractères qui forment le type numérique approprié (int, long, ulong, float, decimal, etc.).  Tout espace blanc entre les caractères qui forment le nombre génère une erreur.  Par exemple, vous pouvez utiliser `decimal.TryParse` pour analyser « 10 », « 10.3 », «   10   », mais vous ne pouvez pas utiliser cette méthode pour analyser 10 à partir de « 10X », « 1 0 » (notez l’espace), « 10 .3 » (notez l’espace), « 10e1 » (`float.TryParse` fonctionne ici), et ainsi de suite.  
  
 Les exemples suivants illustrent des appels à `Parse` et `TryParse` qui ont réussi ou échoué.  
  
 [!code-csharp[csProgGuideTypes#5555](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_1.cs)]  
[!code-csharp[csProgGuideTypes#25](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_2.cs)]  
[!code-csharp[csProgGuideTypes#26](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_3.cs)]  
[!code-csharp[csProgGuideTypes#27](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_4.cs)]  
[!code-csharp[csProgGuideTypes#28](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_5.cs)]  
[!code-csharp[csProgGuideTypes#100](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_6.cs)]  
  
## <a name="example"></a>Exemple  
 Le tableau suivant répertorie quelques unes des méthodes de la classe <xref:System.Convert> que vous pouvez utiliser.  
  
|Type numérique|Méthode|  
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
  
 Cet exemple appelle la méthode <xref:System.Convert.ToInt32%28System.String%29?displayProperty=nameWithType> pour convertir une entrée de type [chaîne](../../../csharp/language-reference/keywords/string.md) en [int](../../../csharp/language-reference/keywords/int.md). Le code intercepte les deux exceptions les plus communes qui peuvent être levées par cette méthode, <xref:System.FormatException> et <xref:System.OverflowException>. Si le nombre peut être incrémenté sans entraîner de dépassement au niveau de l'emplacement de stockage des entiers, le programme ajoute 1 au résultat et imprime la sortie.  
  
 [!code-csharp[csProgGuideTypes#5555](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_1.cs)]  
[!code-csharp[csProgGuideTypes#24](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_7.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 [Types](../../../csharp/programming-guide/types/index.md)  
 [Guide pratique pour déterminer si une chaîne représente une valeur numérique](../../../csharp/programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)  
 [Utilitaire de mise en forme .NET Framework 4](http://code.msdn.microsoft.com/NET-Framework-4-Formatting-9c4dae8d)
