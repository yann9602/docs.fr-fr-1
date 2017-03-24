---
title: "ulong (r&#233;f&#233;rence C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "ulong_CSharpKeyword"
  - "ulong"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "ulong (mot clé C#)"
ms.assetid: f2ece624-837a-40cf-92c5-343e7f33397c
caps.latest.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 16
---
# ulong (r&#233;f&#233;rence C#)
Le mot clé `ulong` désigne un type intégral ; il est utilisé pour stocker des valeurs comme indiqué dans le tableau ci\-dessous.  
  
|Type|Plage|Taille|Type .NET Framework|  
|----------|-----------|------------|-------------------------|  
|`ulong`|0 à 18,446,744,073,709,551,615|Entier 64 bits non signé|<xref:System.UInt64?displayProperty=fullName>|  
  
## Littéraux  
 Vous pouvez déclarer et initialiser une variable `ulong` en suivant l'exemple ci\-après :  
  
```  
  
ulong uLong = 9223372036854775808;  
```  
  
 Lorsqu'un littéral entier n'a aucun suffixe, son type est le premier des types dans lesquels sa valeur peut être représentée : [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), `ulong`.  Dans l'exemple ci\-dessous, le littéral entier est de type `ulong`.  
  
 Vous pouvez également employer des suffixes pour spécifier le type du littéral, en tenant compte des règles suivantes :  
  
-   Si vous utilisez le suffixe L ou l, le littéral entier est de type [long](../../../csharp/language-reference/keywords/long.md) ou `ulong` selon sa taille.  
  
    > [!NOTE]
    >  Vous pouvez utiliser la lettre minuscule "l" comme suffixe.  Le cas échéant, le compilateur génère un avertissement pour signaler que la lettre "l" peut être confondue avec le chiffre "1". Pour cette raison, préférez le suffixe "L".  
  
-   Si vous utilisez `U` ou `u`, le type d'entier littéral est [uint](../../../csharp/language-reference/keywords/uint.md) ou `ulong` selon sa taille.  
  
-   Si vous utilisez le suffixe UL, ul, Ul, uL, LU, lu, Lu ou lU, le littéral entier est de type `ulong`.  
  
     Par exemple, le résultat des trois instructions suivantes sera de type système `UInt64`, ce qui correspond à l'alias `ulong` :  
  
    ```  
    Console.WriteLine(9223372036854775808L.GetType());  
    Console.WriteLine(123UL.GetType());  
    Console.WriteLine((123UL + 456).GetType());  
    ```  
  
 Ce suffixe est souvent utilisé lors de l'appel de méthodes surchargées.  Prenez l'exemple suivant de deux méthodes surchargées ayant pour paramètres `ulong` et [int](../../../csharp/language-reference/keywords/int.md) :  
  
```  
public static void SampleMethod(int i) {}  
public static void SampleMethod(ulong l) {}  
```  
  
 Le recours au suffixe UL avec le paramètre `ulong` permet de garantir que le type correct sera appelé, comme indiqué ci\-après :  
  
```  
SampleMethod(5);    // Calling the method with the int parameter  
SampleMethod(5UL);  // Calling the method with the ulong parameter  
```  
  
## Conversions  
 Une conversion implicite prédéfinie intervient de `ulong` en [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md) ou [decimal](../../../csharp/language-reference/keywords/decimal.md).  
  
 Il n'y a pas de conversion implicite du type `ulong` en un type intégral.  Par exemple, l'instruction suivante génère une erreur de compilation si vous ne spécifiez pas de conversion explicite :  
  
```  
long long1 = 8UL;   // Error: no implicit conversion from ulong  
```  
  
 Une conversion implicite prédéfinie est effectuée entre le type [byte](../../../csharp/language-reference/keywords/byte.md), [ushort](../../../csharp/language-reference/keywords/ushort.md),  [uint](../../../csharp/language-reference/keywords/uint.md) ou [char](../../../csharp/language-reference/keywords/char.md) en `ulong`.  
  
 En outre, il n'y a pas de conversion implicite des types virgule flottante en type `ulong`.  Par exemple, l'instruction suivante génère une erreur de compilation si aucune conversion explicite n'est spécifiée :  
  
```  
// Error -- no implicit conversion from double:  
ulong x = 3.0;  
// OK -- explicit conversion:  
ulong y = (ulong)3.0;    
```  
  
 Pour plus d'informations sur les expressions arithmétiques dans lesquelles coexistent des types virgule flottante et des types intégraux, consultez [float](../../../csharp/language-reference/keywords/float.md) et [double](../../../csharp/language-reference/keywords/double.md).  
  
 Pour plus d'informations sur les règles de conversion numérique implicite, consultez [Tableau des conversions numériques implicites](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## Voir aussi  
 <xref:System.UInt64>   
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Mots clés C\#](../../../csharp/language-reference/keywords/index.md)   
 [Tableau des types intégraux](../../../csharp/language-reference/keywords/integral-types-table.md)   
 [Tableau des types intégrés](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [Tableau des conversions numériques implicites](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)   
 [Tableau des conversions numériques explicites](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)