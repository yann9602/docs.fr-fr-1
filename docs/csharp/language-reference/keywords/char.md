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
# <a name="char-c-reference"></a>char (référence C#)
Le mot clé `char` permet de déclarer une instance de la structure <xref:System.Char?displayProperty=fullName> utilisée par le .NET Framework pour représenter un caractère Unicode. La valeur d’un objet `Char` est une valeur numérique 16 bits (ordinale).  
  
 Les caractères Unicode sont utilisés pour représenter la plupart des langues écrites dans le monde.  
  
|Type|Plage|Taille|Type .NET Framework|  
|----------|-----------|----------|-------------------------|  
|`char`|U+0000 à U+FFFF|Caractère Unicode 16 bits|<xref:System.Char?displayProperty=fullName>|  
  
## <a name="literals"></a>Littéraux  
 Les constantes de type `char` peuvent être représentées sous la forme de littéraux de caractères, d’une séquence d’échappement hexadécimale ou d’une représentation Unicode. Vous pouvez également effectuer un cast des codes de caractères de type intégral. Dans l’exemple suivant, quatre variables `char` sont initialisées avec le même caractère (`X`) :  
  
 [!code-cs[csrefKeywordsTypes#19](../../../csharp/language-reference/keywords/codesnippet/CSharp/char_1.cs)]  
  
## <a name="conversions"></a>Conversions  
 Vous pouvez convertir implicitement un `char` en [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md) ou [decimal](../../../csharp/language-reference/keywords/decimal.md). Par contre, vous ne pouvez pas convertir implicitement d’autres types en type `char`.  
  
 Le type <xref:System.Char?displayProperty=fullName> fournit plusieurs méthodes statiques à utiliser avec des valeurs `char`.  
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Char>   
 [Informations de référence sur C#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Mots clés C#](../../../csharp/language-reference/keywords/index.md)   
 [Tableau des types intégraux](../../../csharp/language-reference/keywords/integral-types-table.md)   
 [Tableau des types intégrés](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [Tableau des conversions numériques implicites](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)   
 [Tableau des conversions numériques explicites](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)   
 [Types Nullable](../../../csharp/programming-guide/nullable-types/index.md)   
 [Chaînes](../../../csharp/programming-guide/strings/index.md)

