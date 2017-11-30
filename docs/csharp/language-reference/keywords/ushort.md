---
title: "ushort (référence C#)"
ms.date: 03/14/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- ushort
- ushort_CSharpKeyword
helpviewer_keywords: ushort keyword [C#]
ms.assetid: 1a7dbaae-b7a0-4111-872a-c88a6d3981ac
caps.latest.revision: "16"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 83fa657303e8392997b04b7d80cdbcdbf39de887
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ushort-c-reference"></a>ushort (référence C#)

Le mot clé `ushort` indique un type de données intégral qui stocke des valeurs selon la taille et la plage indiquées dans le tableau suivant.  
  
|Type|Plage|Taille|Type .NET Framework|  
|----------|-----------|----------|-------------------------|  
|`ushort`|0 à 65 535|Entier 16 bits non signé|<xref:System.UInt16?displayProperty=nameWithType>|  
  
## <a name="literals"></a>Littéraux  

Vous pouvez déclarer et initialiser une variable `ushort` en lui assignant un littéral décimal, un littéral hexadécimal ou un littéral binaire (à compter de C# 7). Si le littéral entier est en dehors de la plage autorisée pour le type `ushort` (autrement dit, s’il est inférieur à <xref:System.UInt16.MinValue?displayProperty=nameWithType> ou supérieur à <xref:System.UInt16.MaxValue?displayProperty=nameWithType>), une erreur de compilation se produit.

Dans l’exemple suivant, les entiers égaux à 65 034 représentés comme des littéraux décimaux, hexadécimaux et binaires sont implicitement convertis à partir de valeurs [int](../../../csharp/language-reference/keywords/int.md) en `ushort`.    
  
[!code-csharp[UShort](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UShort)]  

> [!NOTE] 
> Vous utilisez le préfixe `0x` ou `0X` pour désigner un littéral hexadécimal, et le préfixe `0b` ou `0B` pour désigner un littéral binaire. Les littéraux décimaux n’ont pas de préfixe.

À partir de C# 7, quelques fonctionnalités ont été ajoutées améliorer la lisibilité. 
 - C# 7.0 permet l’utilisation d’un caractère de soulignement `_`, comme un séparateur de chiffre.
 - 7.2 c# permet `_` à utiliser comme séparateur de chiffres pour un littéral binaire ou en hexadécimal, après le préfixe. Un littéral décimal n’est pas autorisé à avoir un trait de soulignement.

Certains exemples sont présentés ci-dessous.

[!code-csharp[UShort](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UShortS)]  
 
## <a name="compiler-overload-resolution"></a>Résolution de surcharge du compilateur
  
 Vous devez utiliser un cast lors de l’appel de méthodes surchargées. Prenons l’exemple des méthodes surchargées suivantes ayant pour paramètres `ushort` et [int](../../../csharp/language-reference/keywords/int.md) :  
  
```csharp  
public static void SampleMethod(int i) {}  
public static void SampleMethod(ushort s) {}  
```  
 
 L’utilisation du cast `ushort` garantit l’appel du type correct, par exemple :  
  
```csharp  
// Calls the method with the int parameter:  
SampleMethod(5);  
// Calls the method with the ushort parameter:  
SampleMethod((ushort)5);    
```  
  
## <a name="conversions"></a>Conversions  
 Il existe une conversion implicite prédéfinie de `ushort` en [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md) ou [decimal](../../../csharp/language-reference/keywords/decimal.md).  
  
 Il existe une conversion implicite prédéfinie de [byte](../../../csharp/language-reference/keywords/byte.md) ou [char](../../../csharp/language-reference/keywords/char.md) en `ushort`. Sinon, vous devez utiliser un cast pour effectuer une conversion explicite. Prenez l’exemple des deux variables `ushort``x` et `y` suivantes :  
  
```csharp 
ushort x = 5, y = 12;  
```  
  
 L’instruction d’assignation suivante entraîne une erreur de compilation, car l’expression arithmétique située à droite de l’opérateur d’assignation donne la valeur `int` par défaut.  
  
```csharp  
ushort z = x + y;   // Error: conversion from int to ushort  
```  
  
 Pour corriger ce problème, utilisez un cast :  
  
```csharp 
ushort z = (ushort)(x + y);   // OK: explicit conversion   
```  
  
 Il est cependant possible d’utiliser les instructions suivantes dans lesquelles la variable de destination a une taille de stockage égale ou supérieure :  
  
```csharp
int m = x + y;  
long n = x + y;  
```  
  
 Notez aussi qu’il n’existe pas de conversion implicite des types virgule flottante en `ushort`. Par exemple, l’instruction suivante génère une erreur du compilateur à moins qu’un cast explicite soit utilisé :  
  
```csharp  
// Error -- no implicit conversion from double:  
ushort x = 3.0;   
// OK -- explicit conversion:  
ushort y = (ushort)3.0;  
```  
  
 Pour plus d’informations sur les expressions arithmétiques dans lesquelles coexistent des types virgule flottante et des types intégraux, consultez [float](../../../csharp/language-reference/keywords/float.md) et [double](../../../csharp/language-reference/keywords/double.md).  
  
 Pour plus d’informations sur les règles des conversions numériques implicites, consultez le [Tableau des conversions numériques implicites](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).  
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.UInt16>  
 [Référence C#](../../../csharp/language-reference/index.md)  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [Mots clés C#](../../../csharp/language-reference/keywords/index.md)  
 [Tableau des types intégraux](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [Tableau des types intégrés](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [Tableau des conversions numériques implicites](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [Tableau des conversions numériques explicites](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
