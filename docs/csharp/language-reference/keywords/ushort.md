---
title: "ushort (r&#233;f&#233;rence C#) | Microsoft Docs"
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
  - "ushort"
  - "ushort_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "ushort (mot clé C#)"
ms.assetid: 1a7dbaae-b7a0-4111-872a-c88a6d3981ac
caps.latest.revision: 16
caps.handback.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# ushort (r&#233;f&#233;rence C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Le mot clé `ushort` indique un type intégral ; il est utilisé pour stocker des valeurs comme indiqué dans le tableau ci\-dessous.  
  
|Type|Plage|Taille|Type .NET Framework|  
|----------|-----------|------------|-------------------------|  
|`ushort`|0 à 65 535|Entier 16 bits non signé|<xref:System.UInt16?displayProperty=fullName>|  
  
## Littéraux  
 Vous pouvez déclarer et initialiser une variable `ushort` en suivant l'exemple ci\-après :  
  
```  
  
ushort myShort = 65535;  
```  
  
 Dans la déclaration précédente, le littéral entier `65535` est implicitement converti de type [int](../../../csharp/language-reference/keywords/int.md) en type `ushort`.  Si le littéral entier est en dehors de la plage de valeurs autorisées pour `ushort`, une erreur de compilation se produit.  
  
 Une conversion explicite doit être utilisée lors de l'appel de méthodes surchargées.  Prenez l'exemple suivant de deux méthodes surchargées ayant pour paramètres `ushort` et [int](../../../csharp/language-reference/keywords/int.md) :  
  
```  
public static void SampleMethod(int i) {}  
public static void SampleMethod(ushort s) {}  
```  
  
 Le recours à un cast `ushort` permet de garantir que le type correct sera appelé, comme indiqué ci\-après :  
  
```  
// Calls the method with the int parameter:  
SampleMethod(5);  
// Calls the method with the ushort parameter:  
SampleMethod((ushort)5);    
```  
  
## Conversions  
 Il y a une conversion implicite prédéfinie de `ushort` en [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md) ou [décimal](../../../csharp/language-reference/keywords/decimal.md).  
  
 Une conversion implicite prédéfinie est effectuée du type [byte](../../../csharp/language-reference/keywords/byte.md) ou [char](../../../csharp/language-reference/keywords/char.md) en `ushort`.  Sinon, une conversion explicite doit être utilisée.  Prenez l'exemple suivant de deux variables `ushort`, `x` et `y` :  
  
```  
  
ushort x = 5, y = 12;  
```  
  
 L'instruction d'assignation suivante entraîne une erreur de compilation, car l'expression arithmétique située à droite de l'opérateur d'assignation correspond à `int` par défaut.  
  
```  
  
ushort z = x + y;   // Error: conversion from int to ushort  
```  
  
 Pour résoudre ce problème, utilisez une conversion explicite :  
  
```  
  
ushort z = (ushort)(x + y);   // OK: explicit conversion   
```  
  
 Il est cependant possible d'utiliser les instructions suivantes dans lesquelles la variable de destination possède une taille de stockage égale ou supérieure :  
  
```  
int m = x + y;  
long n = x + y;  
```  
  
 En outre, il n'y a pas de conversion implicite des types virgule flottante en type `ushort`.  Par exemple, l'instruction suivante génère une erreur de compilation si aucune conversion explicite n'est spécifiée :  
  
```  
// Error -- no implicit conversion from double:  
ushort x = 3.0;   
// OK -- explicit conversion:  
ushort y = (ushort)3.0;  
```  
  
 Pour plus d'informations sur les expressions arithmétiques dans lesquelles coexistent des types virgule flottante et des types intégraux, consultez [float](../../../csharp/language-reference/keywords/float.md) et [double](../../../csharp/language-reference/keywords/double.md).  
  
 Pour plus d'informations sur les règles de conversion numérique implicite, consultez [Tableau des conversions numériques implicites](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Voir aussi  
 <xref:System.UInt16>   
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Mots clés C\#](../../../csharp/language-reference/keywords/index.md)   
 [Tableau des types intégraux](../../../csharp/language-reference/keywords/integral-types-table.md)   
 [Tableau des types intégrés](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [Tableau des conversions numériques implicites](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)   
 [Tableau des conversions numériques explicites](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)