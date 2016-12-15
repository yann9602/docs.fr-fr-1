---
title: "bool (r&#233;f&#233;rence C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bool_CSharpKeyword"
  - "bool"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "bool (mot clé C#)"
ms.assetid: 551cfe35-2632-4343-af49-33ad12da08e2
caps.latest.revision: 30
caps.handback.revision: 30
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# bool (r&#233;f&#233;rence C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Le mot clé `bool` est un alias de <xref:System.Boolean?displayProperty=fullName>.  Il est utilisé pour déclarer des variables afin de stocker les valeurs booléennes, [true](../../../csharp/language-reference/keywords/true.md) et [false](../../../csharp/language-reference/keywords/false.md).  
  
> [!NOTE]
>  Si vous nécessitez une variable booléenne qui peut également avoir une valeur `null, utilisez` , `bool?`.  Pour plus d'informations, consultez [Types Nullable](../../../csharp/programming-guide/nullable-types/index.md).  
  
## Littéraux  
 Vous pouvez assigner une valeur booléenne à une variable `bool`.  Vous pouvez également assigner à une variable `bool` une expression dont le résultat est de type `bool`.  
  
 [!code-cs[csrefKeywordsTypes#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/bool_1.cs)]  
  
 \(La valeur par défaut de la variable `bool` est `false`.  \(La valeur par défaut de la variable `bool?` est `null`.  
  
## Conversions  
 En langage C\+\+, une valeur de type `bool` peut être convertie en une valeur de type `int`. En d'autres termes, `false` équivaut à zéro et `true` équivaut à toute valeur différente de zéro.  En langage C\#, il n'y a pas de conversion possible entre le type `bool` et les autres types.  Par exemple, l'instruction `if` suivante n'est pas valide en C\# :  
  
 [!code-cs[csrefKeywordsTypes#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/bool_2.cs)]  
  
 Pour tester une variable du type `int`, vous devez la comparer explicitement à une valeur telle que zéro, comme suit :  
  
 [!code-cs[csrefKeywordsTypes#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/bool_3.cs)]  
  
## Exemple  
 Dans cet exemple, vous entrez un caractère et le programme contrôle si le caractère que vous avez entré est une lettre.  Si c'est une lettre, le programme vérifie s'il s'agit d'une minuscule ou d'une majuscule.  Ces contrôles sont effectués avec <xref:System.Char.IsLetter%2A>, et <xref:System.Char.IsLower%2A>, qui retournent tous les deux le type `bool` :  
  
 [!code-cs[csrefKeywordsTypes#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/bool_4.cs)]  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Mots clés C\#](../../../csharp/language-reference/keywords/index.md)   
 [Tableau des types intégraux](../../../csharp/language-reference/keywords/integral-types-table.md)   
 [Tableau des types intégrés](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [Tableau des conversions numériques implicites](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)   
 [Tableau des conversions numériques explicites](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)