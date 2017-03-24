---
title: "Comment&#160;: effectuer une conversion entre des cha&#238;nes hexad&#233;cimales et des types num&#233;riques (Guide de programmation C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "conversions (C#), chaînes hexadécimales"
  - "chaînes hexadécimales (C#)"
  - "chaînes hexadécimales (C#), convertir en type numérique"
  - "chaînes (C#), convertir en chaînes hexadécimales"
ms.assetid: 7115c49f-7d1d-40c3-8bd9-aae0cc1d46b6
caps.latest.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 19
---
# Comment&#160;: effectuer une conversion entre des cha&#238;nes hexad&#233;cimales et des types num&#233;riques (Guide de programmation C#)
Ces exemples vous montrent comment effectuer les tâches suivantes :  
  
-   Obtenir la valeur hexadécimale de chaque caractère dans une chaîne \([string](../../../csharp/language-reference/keywords/string.md)\).  
  
-   Obtenir la valeur [char](../../../csharp/language-reference/keywords/char.md) qui correspond à chaque valeur d'une chaîne hexadécimale.  
  
-   Convertir une `string` hexadécimale en [int](../../../csharp/language-reference/keywords/int.md).  
  
-   Convertir une `string` hexadécimale en [float](../../../csharp/language-reference/keywords/float.md).  
  
-   Convertir un tableau d'[octets](../../../csharp/language-reference/keywords/byte.md) en `string` hexadécimale.  
  
## Exemple  
 Cet exemple génère la valeur hexadécimale de chaque caractère dans une `string`.  La `string` est d'abord convertie en un tableau de caractères.  <xref:System.Convert.ToInt32%28System.Char%29> est ensuite appelé sur chaque caractère afin d'obtenir sa valeur numérique.  Enfin, le nombre est représenté sous sa forme hexadécimale dans une `string`.  
  
 [!code-cs[csProgGuideTypes#30](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-between-hexadecimal-strings-and-numeric-types_1.cs)]  
  
## Exemple  
 Cet exemple analyse une `string` de valeurs hexadécimales et génère le caractère correspondant à chacune d'elles.  La méthode [Split\(Char\<xref:System.String.Split%28System.Char%5B%5D%29> est d'abord appelée pour obtenir chaque valeur hexadécimale sous la forme d'une `string` individuelle dans un tableau.  <xref:System.Convert.ToInt32%28System.String%2CSystem.Int32%29> est ensuite appelé pour convertir la valeur hexadécimale en valeur décimale représentée par un entier \([int](../../../csharp/language-reference/keywords/int.md)\).  Deux techniques permettant d'obtenir le caractère correspondant à ce code de caractère sont illustrées dans cet exemple.  La première utilise <xref:System.Char.ConvertFromUtf32%28System.Int32%29>, qui retourne le caractère correspondant à l'argument entier sous forme de `string`.  La deuxième effectue un cast explicite de l'`int` vers un [char](../../../csharp/language-reference/keywords/char.md) \(caractère\).  
  
 [!code-cs[csProgGuideTypes#31](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-between-hexadecimal-strings-and-numeric-types_2.cs)]  
  
## Exemple  
 Cet exemple montre une autre façon de convertir une `string` hexadécimale en nombre entier à l'aide de la méthode <xref:System.Int32.Parse%28System.String%2CSystem.Globalization.NumberStyles%29>.  
  
 [!code-cs[csProgGuideTypes#32](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-between-hexadecimal-strings-and-numeric-types_3.cs)]  
  
## Exemple  
 L'exemple suivant indique comment convertir une `string` hexadécimale en [float](../../../csharp/language-reference/keywords/float.md) à l'aide de la classe <xref:System.BitConverter?displayProperty=fullName> et de la méthode <xref:System.Int32.Parse%2A?displayProperty=fullName>.  
  
 [!code-cs[csProgGuideTypes#39](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-between-hexadecimal-strings-and-numeric-types_4.cs)]  
  
## Exemple  
 L'exemple suivant indique comment convertir un tableau d'[octets](../../../csharp/language-reference/keywords/byte.md) en chaîne hexadécimale en utilisant la classe <xref:System.BitConverter?displayProperty=fullName>.  
  
 [!code-cs[csProgGuideTypes#38](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-between-hexadecimal-strings-and-numeric-types_5.cs)]  
  
## Voir aussi  
 [Chaînes de format numériques standard](../Topic/Standard%20Numeric%20Format%20Strings.md)   
 [Types](../../../csharp/programming-guide/types/index.md)   
 [Comment : déterminer si une chaîne représente une valeur numérique](../../../csharp/programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)