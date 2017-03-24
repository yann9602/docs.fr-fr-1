---
title: "char (r&#233;f&#233;rence C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "char"
  - "char_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "char (type de données C#)"
ms.assetid: b51cf4fb-124c-4067-af48-afbac122b228
caps.latest.revision: 27
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 27
---
# char (r&#233;f&#233;rence C#)
Le mot clé d' `char` est utilisé pour déclarer une instance de la structure d' <xref:System.Char?displayProperty=fullName> que le.NET Framework utilise pour représenter un caractère Unicode.  La valeur d'un objet d' `Char` est une valeur numérique 16 bits \(ordinal\).  
  
 Les caractères Unicode sont utilisés pour représenter la plupart des langues écrites dans le monde.  
  
|Type|Plage|Taille|Type .NET Framework|  
|----------|-----------|------------|-------------------------|  
|`char`|U\+0000 à U\+FFFF|Caractère Unicode 16 bits|<xref:System.Char?displayProperty=fullName>|  
  
## Littéraux  
 Les constantes de type `char` peuvent être représentées sous la forme de littéraux de caractères, d'une séquence d'échappement hexadécimal ou de caractères Unicode.  Vous pouvez également convertir les codes de caractères de type intégral.  Dans l'exemple suivant, quatre variables `char` sont initialisées avec le même caractère \(`X`\) :  
  
 [!code-cs[csrefKeywordsTypes#19](../../../csharp/language-reference/keywords/codesnippet/CSharp/char_1.cs)]  
  
## Conversions  
 Un `char` peut être converti implicitement en [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md) ou [decimal](../../../csharp/language-reference/keywords/decimal.md).  En revanche, il n'y a pas de conversion implicite des autres types en type `char`.  
  
 Le type <xref:System.Char?displayProperty=fullName> fournit plusieurs méthodes statiques à utiliser avec les valeurs `char`.  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## Voir aussi  
 <xref:System.Char>   
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Mots clés C\#](../../../csharp/language-reference/keywords/index.md)   
 [Tableau des types intégraux](../../../csharp/language-reference/keywords/integral-types-table.md)   
 [Tableau des types intégrés](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [Tableau des conversions numériques implicites](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)   
 [Tableau des conversions numériques explicites](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)   
 [Types Nullable](../../../csharp/programming-guide/nullable-types/index.md)   
 [Chaînes](../../../csharp/programming-guide/strings/index.md)