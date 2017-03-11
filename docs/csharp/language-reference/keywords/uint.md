---
title: "uint (r&#233;f&#233;rence C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "uint"
  - "uint_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "uint (mot clé C#)"
ms.assetid: e93e42c6-ec72-4b0b-89df-2fd8d36f7a7b
caps.latest.revision: 18
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 18
---
# uint (r&#233;f&#233;rence C#)
Le mot clé `uint` désigne un type intégral qui stocke des valeurs comme indiqué dans le tableau ci\-dessous.  
  
|Type|Plage|Taille|Type .NET Framework|  
|----------|-----------|------------|-------------------------|  
|`uint`|0 à 4 294 967 295|Entier 32 bits non signé|<xref:System.UInt32?displayProperty=fullName>|  
  
 **Remarque** Le type `uint` n'est pas conforme CLS.  Utilisez `int` chaque fois que cela est possible.  
  
## Littéraux  
 Vous pouvez déclarer et initialiser une variable `uint` en suivant l'exemple ci\-après :  
  
```  
  
uint myUint = 4294967290;  
```  
  
 Lorsqu'un littéral entier n'a aucun suffixe, son type est le premier des types dans lesquels sa valeur peut être représentée : [int](../../../csharp/language-reference/keywords/int.md), `uint`, [long](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md).  Dans cet exemple, le littéral entier est de type `uint`.  
  
```  
  
uint uInt1 = 123;  
```  
  
 Vous pouvez aussi utiliser le suffixe u ou U, comme suit :  
  
```  
  
uint uInt2 = 123U;  
```  
  
 Lorsque vous utilisez le suffixe `U` ou `u`, le type du littéral est déterminé pour être `uint` ou `ulong` d'après la valeur numérique du littéral.  Par exemple :  
  
```  
Console.WriteLine(44U.GetType());  
Console.WriteLine(323442434344U.GetType());  
```  
  
 Ce code affiche `System.UInt32`, suivi de `System.UInt64` \(les types sous\-jacents pour `uint` et `ulong` respectivement\) parce que le deuxième littéral est trop grand pour être stocké par le type `uint`.  
  
## Conversions  
 Il y a une conversion implicite prédéfinie de `uint` en [long](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md) ou [decimal](../../../csharp/language-reference/keywords/decimal.md).  Par exemple :  
  
```  
float myFloat = 4294967290;   // OK: implicit conversion to float  
```  
  
 Une conversion implicite prédéfinie est effectuée entre le type [byte](../../../csharp/language-reference/keywords/byte.md), [ushort](../../../csharp/language-reference/keywords/ushort.md) ou [char](../../../csharp/language-reference/keywords/char.md) en `uint`.  Sinon, vous devez utiliser une conversion explicite.  Par exemple, l'instruction d'assignation suivante produit une erreur de compilation sans cast :  
  
```  
long aLong = 22;  
// Error -- no implicit conversion from long:  
uint uInt1 = aLong;   
// OK -- explicit conversion:  
uint uInt2 = (uint)aLong;  
```  
  
 En outre, il n'y a pas de conversion implicite des types virgule flottante en type `uint`.  Par exemple, l'instruction suivante génère une erreur de compilation si aucune conversion explicite n'est spécifiée :  
  
```  
// Error -- no implicit conversion from double:  
uint x = 3.0;  
// OK -- explicit conversion:  
uint y = (uint)3.0;   
```  
  
 Pour plus d'informations sur les expressions arithmétiques dans lesquelles coexistent des types virgule flottante et des types intégraux, consultez [float](../../../csharp/language-reference/keywords/float.md) et [double](../../../csharp/language-reference/keywords/double.md).  
  
 Pour plus d'informations sur les règles de conversion numérique implicite, consultez [Tableau des conversions numériques implicites](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## Voir aussi  
 <xref:System.UInt32>   
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Mots clés C\#](../../../csharp/language-reference/keywords/index.md)   
 [Tableau des types intégraux](../../../csharp/language-reference/keywords/integral-types-table.md)   
 [Tableau des types intégrés](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [Tableau des conversions numériques implicites](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)   
 [Tableau des conversions numériques explicites](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)