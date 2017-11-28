---
title: "Tableau des types intégrés (référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- types [C#], built-in
- built-in C# types
ms.assetid: 54f901f2-bf2f-472c-ae8d-73e8ecfc57fe
caps.latest.revision: "12"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d9d1e4945526a862074e73e608185696328946be
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="built-in-types-table-c-reference"></a>Tableau des types intégrés (référence C#)
Le tableau suivant liste les mots clés des types C# intégrés, qui sont des alias des types prédéfinis de l’espace de noms <xref:System>.  
  
|Type C#|Type .NET Framework|  
|--------------|-------------------------|  
|[bool](../../../csharp/language-reference/keywords/bool.md)|`System.Boolean`|  
|[byte](../../../csharp/language-reference/keywords/byte.md)|`System.Byte`|  
|[sbyte](../../../csharp/language-reference/keywords/sbyte.md)|`System.SByte`|  
|[char](../../../csharp/language-reference/keywords/char.md)|`System.Char`|  
|[decimal](../../../csharp/language-reference/keywords/decimal.md)|`System.Decimal`|  
|[double](../../../csharp/language-reference/keywords/double.md)|`System.Double`|  
|[float](../../../csharp/language-reference/keywords/float.md)|`System.Single`|  
|[int](../../../csharp/language-reference/keywords/int.md)|`System.Int32`|  
|[uint](../../../csharp/language-reference/keywords/uint.md)|`System.UInt32`|  
|[long](../../../csharp/language-reference/keywords/long.md)|`System.Int64`|  
|[ulong](../../../csharp/language-reference/keywords/ulong.md)|`System.UInt64`|  
|[object](../../../csharp/language-reference/keywords/object.md)|`System.Object`|  
|[short](../../../csharp/language-reference/keywords/short.md)|`System.Int16`|  
|[ushort](../../../csharp/language-reference/keywords/ushort.md)|`System.UInt16`|  
|[string](../../../csharp/language-reference/keywords/string.md)|`System.String`|  
  
## <a name="remarks"></a>Remarques  
 Hormis les types `object` et `string`, tous les types listés dans le tableau sont considérés comme des types simples.  
  
 Les mots clés des types C# et leurs alias sont interchangeables. Par exemple, vous pouvez déclarer une variable de type entier à l’aide de l’une des deux déclarations suivantes :  
  
```  
int x = 123;  
System.Int32 x = 123;  
```  
  
 Pour afficher le type réel d’un type C#, utilisez la méthode système `GetType()`. Par exemple, l’instruction ci-après affiche l’alias système qui représente le type de `myVariable` :  
  
```  
Console.WriteLine(myVariable.GetType());  
```  
  
 Vous pouvez également utiliser l’opérateur [typeof](../../../csharp/language-reference/keywords/typeof.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Référence C#](../../../csharp/language-reference/index.md)  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [Mots clés C#](../../../csharp/language-reference/keywords/index.md)  
 [Types valeur](../../../csharp/language-reference/keywords/value-types.md)  
 [Tableau des valeurs par défaut](../../../csharp/language-reference/keywords/default-values-table.md)  
 [Tableau des formats des résultats numériques](../../../csharp/language-reference/keywords/formatting-numeric-results-table.md)  
 [dynamic](../../../csharp/language-reference/keywords/dynamic.md)  
 [Tableaux de référence des types](../../../csharp/language-reference/keywords/reference-tables-for-types.md)
