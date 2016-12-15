---
title: "sbyte (r&#233;f&#233;rence C#) | Microsoft Docs"
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
  - "sbyte_CSharpKeyword"
  - "sbyte"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "sbyte (mot clé C#)"
ms.assetid: 1a9c7b48-73d1-4d33-b485-c4faf0a816bc
caps.latest.revision: 17
caps.handback.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# sbyte (r&#233;f&#233;rence C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Le mot clé `sbyte` indique un type intégral qui stocke des valeurs comme indiqué dans le tableau ci\-dessous.  
  
|Type|Plage|Taille|Type .NET Framework|  
|----------|-----------|------------|-------------------------|  
|`sbyte`|\-128 à 127|Entier 8 bits signé|<xref:System.SByte?displayProperty=fullName>|  
  
## Littéraux  
 Vous pouvez déclarer et initialiser une variable `sbyte` de la façon suivante :  
  
```  
  
sbyte sByte1 = 127;  
```  
  
 Dans la déclaration précédente, le littéral entier 127 est implicitement converti de type [int](../../../csharp/language-reference/keywords/int.md) en type `sbyte`.  Si le littéral entier est en dehors de la plage de valeurs autorisées pour `sbyte`, une erreur de compilation se produit.  
  
 Une conversion doit être utilisée lors de l'appel de méthodes surchargées.  Prenez l'exemple suivant de deux méthodes surchargées ayant pour paramètres `sbyte` et [int](../../../csharp/language-reference/keywords/int.md) :  
  
```  
public static void SampleMethod(int i) {}  
public static void SampleMethod(sbyte b) {}  
```  
  
 Le recours à un cast `sbyte` permet de garantir que le type correct sera appelé, comme indiqué ci\-après :  
  
```  
// Calling the method with the int parameter:  
SampleMethod(5);  
// Calling the method with the sbyte parameter:  
SampleMethod((sbyte)5);  
```  
  
## Conversions  
 Il y a une conversion implicite prédéfinie de `sbyte` en [short](../../../csharp/language-reference/keywords/short.md), [int](../../../csharp/language-reference/keywords/int.md), [long](../../../csharp/language-reference/keywords/long.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md) ou [decimal](../../../csharp/language-reference/keywords/decimal.md).  
  
 Il n'est pas possible de convertir implicitement en `sbyte` des types numériques non littéraux d'une taille de stockage supérieure \(consultez [Tableau des types intégraux](../../../csharp/language-reference/keywords/integral-types-table.md) pour plus d'informations sur les tailles de stockage des types intégraux\).  Prenez l'exemple suivant de deux variables `sbyte`, `x` et `y` :  
  
```  
  
sbyte x = 10, y = 20;  
```  
  
 L'instruction d'assignation suivante entraîne une erreur de compilation, car l'expression arithmétique située à droite de l'opérateur d'assignation correspond à [int](../../../csharp/language-reference/keywords/int.md) par défaut.  
  
```  
  
sbyte z = x + y;   // Error: conversion from int to sbyte  
```  
  
 Pour résoudre ce problème, effectuez un cast de l'expression comme dans l'exemple suivant :  
  
```  
  
sbyte z = (sbyte)(x + y);   // OK: explicit conversion  
```  
  
 Il est cependant possible d'utiliser les instructions suivantes dans lesquelles la variable de destination possède une taille de stockage égale ou supérieure :  
  
```  
  
        sbyte x = 10, y = 20;  
int m = x + y;  
long n = x + y;  
```  
  
 En outre, il n'y a pas de conversion implicite des types virgule flottante en type `sbyte`.  Par exemple, l'instruction suivante génère une erreur de compilation si aucune conversion explicite n'est spécifiée :  
  
```  
  
        sbyte x = 3.0;         // Error: no implicit conversion from double  
sbyte y = (sbyte)3.0;  // OK: explicit conversion  
```  
  
 Pour plus d'informations sur les expressions arithmétiques dans lesquelles coexistent des types virgule flottante et des types intégraux, consultez [float](../../../csharp/language-reference/keywords/float.md) et [double](../../../csharp/language-reference/keywords/double.md).  
  
 Pour plus d'informations sur les règles de conversion numérique implicite, consultez [Tableau des conversions numériques implicites](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Voir aussi  
 <xref:System.SByte>   
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Mots clés C\#](../../../csharp/language-reference/keywords/index.md)   
 [Tableau des types intégraux](../../../csharp/language-reference/keywords/integral-types-table.md)   
 [Tableau des types intégrés](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [Tableau des conversions numériques implicites](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)   
 [Tableau des conversions numériques explicites](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)