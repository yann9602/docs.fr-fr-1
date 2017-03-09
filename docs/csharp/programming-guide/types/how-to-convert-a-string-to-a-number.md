---
title: "Comment&#160;: convertir une cha&#238;ne en nombre (Guide de programmation&#160;C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "conversions (C#)"
  - "conversions (C#), chaîne en type int"
  - "convertir les chaînes en type int (C#)"
  - "chaînes (C#), convertir en type int"
ms.assetid: 467b9979-86ee-4afd-b734-30299cda91e3
caps.latest.revision: 34
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 34
---
# Comment&#160;: convertir une cha&#238;ne en nombre (Guide de programmation&#160;C#)
Vous pouvez convertir une [chaîne](../../../csharp/language-reference/keywords/string.md) en nombre en utilisant des méthodes dans la classe <xref:System.Convert> ou en utilisant la méthode `TryParse` trouvée sur les différents types numériques \(int, long, float, etc.\).  
  
 Si vous avez une chaîne, il est légèrement plus efficace et direct d'appeler une méthode `TryParse` \(par exemple, `int.TryParse(“11”)`\).  L'utilisation d'une méthode `Convert` s'avère plus utile pour les objets généraux qui implémentent <xref:System.IConvertible>.  
  
 Vous pouvez utiliser les méthodes `Parse` ou `TryParse` sur le type numérique que doit contenir la chaîne, notamment le type <xref:System.Int32?displayProperty=fullName>.  La méthode <xref:System.Convert.ToUInt32%2A?displayProperty=fullName> utilise <xref:System.Int32.Parse%2A> en interne.  Si la chaîne n'est pas dans un format valide, `Parse` lève une exception tandis que `TryParse` retourne [false](../../../csharp/language-reference/keywords/false.md).  
  
## Exemple  
 Les méthodes `Parse` et `TryParse` ignorent l'espace blanc au début et à la fin de la chaîne, mais tous les autres caractères doivent être des caractères qui forment le type numérique approprié \(int, long, ulong, float, decimal, etc.\).  Tout espace blanc entre les caractères qui forment le nombre génère une erreur.  Par exemple, vous pouvez utiliser `decimal.TryParse` pour analyser « 10 », « 10.3 », «   10   », mais vous ne pouvez pas utiliser cette méthode pour analyser 10 à partir de « 10X », « 1 0 » \(notez l'espace\), « 10 .3 » \(notez l'espace\), « 10e1 » \(`float.TryParse` fonctionne ici\), et ainsi de suite.  
  
 Les exemples suivants illustrent des appels à `Parse` et `TryParse` qui ont réussi ou échoué.  
  
 [!code-cs[csProgGuideTypes#5555](../../../csharp/programming-guide/nullable-types/codesnippet/csharp/how-to-convert-a-string-_1_1.cs)]  
[!code-cs[csProgGuideTypes#25](../../../csharp/programming-guide/nullable-types/codesnippet/csharp/how-to-convert-a-string-_1_2.cs)]  
[!code-cs[csProgGuideTypes#26](../../../csharp/programming-guide/nullable-types/codesnippet/csharp/how-to-convert-a-string-_1_3.cs)]  
[!code-cs[csProgGuideTypes#27](../../../csharp/programming-guide/nullable-types/codesnippet/csharp/how-to-convert-a-string-_1_4.cs)]  
[!code-cs[csProgGuideTypes#28](../../../csharp/programming-guide/nullable-types/codesnippet/csharp/how-to-convert-a-string-_1_5.cs)]  
[!code-cs[csProgGuideTypes#100](../../../csharp/programming-guide/nullable-types/codesnippet/csharp/how-to-convert-a-string-_1_6.cs)]  
  
## Exemple  
 Le tableau suivant répertorie quelques unes des méthodes de la classe <xref:System.Convert> que vous pouvez utiliser.  
  
|Type numérique|Méthode|  
|--------------------|-------------|  
|`decimal`|<xref:System.Convert.ToDecimal%28System.String%29>|  
|`float`|<xref:System.Convert.ToSingle%28System.String%29>|  
|`double`|<xref:System.Convert.ToDouble%28System.String%29>|  
|`short`|<xref:System.Convert.ToInt16%28System.String%29>|  
|`int`|<xref:System.Convert.ToInt32%28System.String%29>|  
|`long`|<xref:System.Convert.ToInt64%28System.String%29>|  
|`ushort`|<xref:System.Convert.ToUInt16%28System.String%29>|  
|`uint`|<xref:System.Convert.ToUInt32%28System.String%29>|  
|`ulong`|<xref:System.Convert.ToUInt64%28System.String%29>|  
  
 Cet exemple appelle la méthode <xref:System.Convert.ToInt32%28System.String%29?displayProperty=fullName> pour convertir une entrée de type [chaîne](../../../csharp/language-reference/keywords/string.md) en [int](../../../csharp/language-reference/keywords/int.md).  Le code intercepte les deux exceptions les plus communes qui peuvent être levées par cette méthode, <xref:System.FormatException> et <xref:System.OverflowException>.  Si le nombre peut être incrémenté sans entraîner de dépassement au niveau de l'emplacement de stockage des entiers, le programme ajoute 1 au résultat et imprime la sortie.  
  
 [!code-cs[csProgGuideTypes#5555](../../../csharp/programming-guide/nullable-types/codesnippet/csharp/how-to-convert-a-string-_1_1.cs)]  
[!code-cs[csProgGuideTypes#24](../../../csharp/programming-guide/nullable-types/codesnippet/csharp/how-to-convert-a-string-_1_7.cs)]  
  
## Voir aussi  
 [Types](../../../csharp/programming-guide/types/index.md)   
 [Comment : déterminer si une chaîne représente une valeur numérique](../../../csharp/programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)   
 [Utilitaire de formatage .NET Framework 4](http://code.msdn.microsoft.com/NET-Framework-4-Formatting-9c4dae8d)