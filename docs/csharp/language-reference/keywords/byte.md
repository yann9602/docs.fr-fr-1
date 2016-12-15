---
title: "byte (r&#233;f&#233;rence C#) | Microsoft Docs"
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
  - "byte"
  - "byte_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "byte (mot clé C#)"
ms.assetid: 111f1db9-ca32-4f0e-b497-4783517eda47
caps.latest.revision: 19
caps.handback.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# byte (r&#233;f&#233;rence C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Le mot clé `byte` désigne un type intégral qui stocke des valeurs comme indiqué dans le tableau suivant.  
  
|Type|Plage|Taille|Type .NET Framework|  
|----------|-----------|------------|-------------------------|  
|`byte`|0 à 255|Entier 8 bits non signé|<xref:System.Byte?displayProperty=fullName>|  
  
## Littéraux  
 Vous pouvez déclarer et initialiser une variable `byte` en suivant l'exemple ci\-après :  
  
```  
byte myByte = 255;  
```  
  
 Dans la déclaration précédente, le littéral entier `255` est implicitement converti de type [int](../../../csharp/language-reference/keywords/int.md) en type `byte`.  Si le littéral entier est en dehors de la plage de valeurs autorisées pour `byte`, une erreur de compilation se produit.  
  
## Conversions  
 Il y a une conversion implicite prédéfinie de `byte` en [short](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md) ou [decimal](../../../csharp/language-reference/keywords/decimal.md).  
  
 Vous ne pouvez pas convertir implicitement les types numériques non littéraux de taille de stockage plus importante en `byte`.  Pour plus d'informations sur les tailles de stockage des types intégraux, consultez [Tableau des types intégraux](../../../csharp/language-reference/keywords/integral-types-table.md).  Prenez l'exemple suivant de deux variables `byte`, `x` et `y` :  
  
```  
  
byte x = 10, y = 20;  
```  
  
 L'instruction d'assignation suivante entraîne une erreur de compilation, car l'expression arithmétique située à droite de l'opérateur d'assignation correspond à `int` par défaut.  
  
```  
// Error: conversion from int to byte:  
byte z = x + y;  
```  
  
 Pour résoudre ce problème, utilisez une conversion explicite :  
  
```  
// OK: explicit conversion:  
byte z = (byte)(x + y);  
```  
  
 Il est cependant possible d'utiliser les instructions suivantes dans lesquelles la variable de destination possède une taille de stockage égale ou supérieure :  
  
```  
int x = 10, y = 20;  
int m = x + y;  
long n = x + y;  
```  
  
 En outre, il n'y a pas de conversion implicite des types virgule flottante en type `byte`.  Par exemple, l'instruction suivante génère une erreur de compilation si aucune conversion explicite n'est spécifiée :  
  
```  
// Error: no implicit conversion from double:  
byte x = 3.0;   
// OK: explicit conversion:  
byte y = (byte)3.0;  
```  
  
 Une conversion explicite doit être utilisée lors de l'appel de méthodes surchargées.  Prenez l'exemple suivant de deux méthodes surchargées ayant pour paramètres `byte` et [int](../../../csharp/language-reference/keywords/int.md) :  
  
```  
public static void SampleMethod(int i) {}  
public static void SampleMethod(byte b) {}  
```  
  
 Le recours à un cast `byte` permet de garantir que le type correct sera appelé, comme indiqué ci\-après :  
  
```  
// Calling the method with the int parameter:  
SampleMethod(5);  
// Calling the method with the byte parameter:  
SampleMethod((byte)5);  
```  
  
 Pour plus d'informations sur les expressions arithmétiques dans lesquelles coexistent des types virgule flottante et des types intégraux, consultez [float](../../../csharp/language-reference/keywords/float.md) et [double](../../../csharp/language-reference/keywords/double.md).  
  
 Pour plus d'informations sur les règles de conversion numérique implicite, consultez [Tableau des conversions numériques implicites](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Voir aussi  
 <xref:System.Byte>   
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Mots clés C\#](../../../csharp/language-reference/keywords/index.md)   
 [Tableau des types intégraux](../../../csharp/language-reference/keywords/integral-types-table.md)   
 [Tableau des types intégrés](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [Tableau des conversions numériques implicites](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)   
 [Tableau des conversions numériques explicites](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)