---
title: "int (r&#233;f&#233;rence C#) | Microsoft Docs"
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
  - "int_CSharpKeyword"
  - "int"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "int (mot clé C#)"
ms.assetid: 212447b4-5d2a-41aa-88ab-84fe710bdb52
caps.latest.revision: 19
caps.handback.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# int (r&#233;f&#233;rence C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Le mot clé `int` désigne un type intégral ; il est utilisé pour stocker des valeurs comme indiqué dans le tableau ci\-dessous.  
  
|Type|Plage|Taille|Type .NET Framework|Valeur par défaut|  
|----------|-----------|------------|-------------------------|-----------------------|  
|`int`|\-2 147 483 648 à 2 147 483 647|Entier 32 bits signé|<xref:System.Int32?displayProperty=fullName>|0|  
  
## Littéraux  
 Vous pouvez déclarer et initialiser une variable `int` en suivant l'exemple ci\-après :  
  
```  
  
int i = 123;  
```  
  
 Lorsqu'un littéral entier n'a aucun suffixe, son type est le premier des types dans lesquels sa valeur peut être représentée : `int`, [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md).  Dans cet exemple, le littéral entier est de type `int`.  
  
## Conversions  
 Le type `int` est implicitement converti dans l'un de ces types : [long](../../../csharp/language-reference/keywords/long.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md) ou [decimal](../../../csharp/language-reference/keywords/decimal.md).  Par exemple :  
  
```  
// '123' is an int, so an implicit conversion takes place here:  
float f = 123;  
```  
  
 Il y a une conversion implicite prédéfinie de [sbyte](../../../csharp/language-reference/keywords/sbyte.md), [byte](../../../csharp/language-reference/keywords/byte.md), [short](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md) ou [char](../../../csharp/language-reference/keywords/char.md) en `int`.  Par exemple, l'instruction d'assignation suivante produit une erreur de compilation sans cast :  
  
```  
long aLong = 22;  
int i1 = aLong;       // Error: no implicit conversion from long.  
int i2 = (int)aLong;  // OK: explicit conversion.  
```  
  
 En outre, il n'y a pas de conversion implicite des types virgule flottante en type `int`.  Par exemple, l'instruction suivante génère une erreur de compilation si aucune conversion explicite n'est spécifiée :  
  
```  
  
        int x = 3.0;         // Error: no implicit conversion from double.  
int y = (int)3.0;    // OK: explicit conversion.  
```  
  
 Pour plus d'informations sur les expressions arithmétiques dans lesquelles coexistent des types virgule flottante et des types intégraux, consultez [float](../../../csharp/language-reference/keywords/float.md) et [double](../../../csharp/language-reference/keywords/double.md).  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Voir aussi  
 <xref:System.Int32>   
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Mots clés C\#](../../../csharp/language-reference/keywords/index.md)   
 [Tableau des types intégraux](../../../csharp/language-reference/keywords/integral-types-table.md)   
 [Tableau des types intégrés](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [Tableau des conversions numériques implicites](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)   
 [Tableau des conversions numériques explicites](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)