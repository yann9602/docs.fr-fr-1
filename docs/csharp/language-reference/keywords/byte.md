---
title: "byte (référence C#)"
ms.date: 2017-03-14
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- byte
- byte_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- byte keyword [C#]
ms.assetid: 111f1db9-ca32-4f0e-b497-4783517eda47
caps.latest.revision: 19
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 8ef7494e2a8a1463d37cff77d1dacebec8182b66
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="byte-c-reference"></a>byte (référence C#)

`byte` désigne un type intégral qui stocke des valeurs comme indiqué dans le tableau suivant.  
  
|Type|Plage|Taille|Type .NET Framework|  
|----------|-----------|----------|-------------------------|  
|`byte`|0 à 255|Entier 8 bits non signé|<xref:System.Byte?displayProperty=fullName>|  
  
## <a name="literals"></a>Littéraux  

 Vous pouvez déclarer et initialiser une variable `byte` en lui assignant un littéral décimal, un littéral hexadécimal ou un littéral binaire (à compter de C# 7). Si le littéral entier est en dehors de la plage de `byte` (autrement dit, s’il est inférieur à <xref:System.Byte.MinValue?displayProperty=fullName> ou supérieur à <xref:System.Byte.MaxValue?displayProperty=fullName>), une erreur de compilation se produit.

Dans l’exemple suivant, les entiers égaux à 201 représentés comme des littéraux décimaux, hexadécimaux et binaires sont implicitement convertis des valeurs [int](../../../csharp/language-reference/keywords/int.md) en `byte`.    
  
[!code-cs[Byte](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Byte)]  

> [!NOTE] 
> Vous utilisez le préfixe `0x` ou `0X` pour désigner un littéral hexadécimal, et le préfixe `0b` ou `0B` pour désigner un littéral binaire. Les littéraux décimaux n’ont pas de préfixe.

À compter de C# 7, vous pouvez également utiliser le caractère de soulignement, `_`, comme un séparateur numérique pour améliorer la lisibilité, comme dans l’exemple suivant.

[!code-cs[Byte](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#ByteS)]  
 
## <a name="conversions"></a>Conversions  
 Il y a une conversion implicite prédéfinie du type `byte` en [short](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md) ou [decimal](../../../csharp/language-reference/keywords/decimal.md).  
  
 Vous ne pouvez pas convertir implicitement en type `byte` des types numériques non littéraux ayant une taille de stockage supérieure. Pour plus d’informations sur les tailles de stockage des types intégraux, consultez [Tableau des types intégraux](../../../csharp/language-reference/keywords/integral-types-table.md). Prenez l’exemple des deux variables `byte`, `x` et `y` suivantes :  
  
```  
byte x = 10, y = 20;  
```  
  
 L’instruction d’assignation suivante entraîne une erreur de compilation, car l’expression arithmétique située à droite de l’opérateur d’assignation donne la valeur `int` par défaut.  
  
```  
// Error: conversion from int to byte:  
byte z = x + y;  
```  
  
 Pour corriger ce problème, utilisez un cast :  
  
```  
// OK: explicit conversion:  
byte z = (byte)(x + y);  
```  
  
 Il est cependant possible d’utiliser les instructions suivantes, dans lesquelles la variable de destination a une taille de stockage égale ou supérieure :  
  
```  
int x = 10, y = 20;  
int m = x + y;  
long n = x + y;  
```  
  
 Il n’y a pas non plus de conversion implicite en `byte` pour les types virgule flottante. Par exemple, l’instruction suivante génère une erreur du compilateur à moins qu’un cast explicite soit utilisé :  
  
```  
// Error: no implicit conversion from double:  
byte x = 3.0;   
// OK: explicit conversion:  
byte y = (byte)3.0;  
```  
  
 Quand vous appelez des méthodes surchargées, vous devez utiliser un cast. Prenons l’exemple des méthodes surchargées suivantes ayant pour paramètres `byte` et [int](../../../csharp/language-reference/keywords/int.md) :  
  
```  
public static void SampleMethod(int i) {}  
public static void SampleMethod(byte b) {}  
```  
  
 L’utilisation du cast `byte` garantit l’appel du type correct, comme dans cet exemple :  
  
```  
// Calling the method with the int parameter:  
SampleMethod(5);  
// Calling the method with the byte parameter:  
SampleMethod((byte)5);  
```  
  
 Pour plus d’informations sur les expressions arithmétiques combinant des types virgule flottante et des types intégraux, consultez [float](../../../csharp/language-reference/keywords/float.md) et [double](../../../csharp/language-reference/keywords/double.md).  
  
 Pour plus d’informations sur les règles des conversions numériques implicites, consultez le [tableau des conversions numériques implicites](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).  
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Byte>   
 [Informations de référence sur C#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Mots clés C#](../../../csharp/language-reference/keywords/index.md)   
 [Tableau des types intégraux](../../../csharp/language-reference/keywords/integral-types-table.md)   
 [Tableau des types intégrés](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [Tableau des conversions numériques implicites](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)   
 [Tableau des conversions numériques explicites](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)

