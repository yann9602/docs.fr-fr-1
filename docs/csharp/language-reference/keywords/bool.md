---
title: "bool (référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- bool_CSharpKeyword
- bool
helpviewer_keywords: bool keyword [C#]
ms.assetid: 551cfe35-2632-4343-af49-33ad12da08e2
caps.latest.revision: "30"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1d52955d64a6c8063e4ea93ceb096459c1c5e984
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="bool-c-reference"></a>bool (référence C#)
Le mot clé `bool` est un alias de <xref:System.Boolean?displayProperty=nameWithType>. Il s’utilise pour déclarer des variables qui stockent les valeurs booléennes [true](../../../csharp/language-reference/keywords/true.md) et [false](../../../csharp/language-reference/keywords/false.md).  
  
> [!NOTE]
>  Si vous avez besoin d’une variable booléenne qui peut également avoir la valeur `null`, utilisez `bool?`. Pour plus d’informations, consultez [Types Nullable](../../../csharp/programming-guide/nullable-types/index.md).  
  
## <a name="literals"></a>Littéraux  
 Vous pouvez assigner une valeur booléenne à une variable `bool`. Vous pouvez également assigner à une variable `bool` une expression dont le résultat est une valeur `bool`.  
  
 [!code-csharp[csrefKeywordsTypes#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/bool_1.cs)]  
  
 La valeur par défaut d’une variable `bool` est `false`. La valeur par défaut d’une variable `bool?` est `null`.  
  
## <a name="conversions"></a>Conversions  
 Dans C++, une valeur de type `bool` peut être convertie en une valeur de type `int`. En d’autres termes, `false` équivaut à zéro et `true` équivaut à une valeur différente de zéro. Dans C#, il n’y a pas de conversion possible entre le type `bool` et les autres types. Par exemple, l’instruction `if` suivante n’est pas valide dans C# :  
  
 [!code-csharp[csrefKeywordsTypes#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/bool_2.cs)]  
  
 Pour tester une variable du type `int`, vous devez la comparer explicitement à une valeur, telle que zéro, comme suit :  
  
 [!code-csharp[csrefKeywordsTypes#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/bool_3.cs)]  
  
## <a name="example"></a>Exemple  
 Dans cet exemple, vous tapez un caractère, et le programme vérifie si le caractère entré est une lettre. Si c’est une lettre, le programme vérifie s’il s’agit d’une minuscule ou d’une majuscule. Ces vérifications sont effectuées avec les méthodes <xref:System.Char.IsLetter%2A>, et <xref:System.Char.IsLower%2A>, qui retournent toutes les deux le type `bool` :  
  
 [!code-csharp[csrefKeywordsTypes#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/bool_4.cs)]  
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Référence C#](../../../csharp/language-reference/index.md)  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [Mots clés C#](../../../csharp/language-reference/keywords/index.md)  
 [Tableau des types intégraux](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [Tableau des types intégrés](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [Tableau des conversions numériques implicites](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [Tableau des conversions numériques explicites](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
