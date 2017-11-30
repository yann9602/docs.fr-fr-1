---
title: "int (référence C#)"
ms.date: 03/14/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- int_CSharpKeyword
- int
helpviewer_keywords: int keyword [C#]
ms.assetid: 212447b4-5d2a-41aa-88ab-84fe710bdb52
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e7acb8bb482ebf8f5c2b508e7cfd45b5b64aae3b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="int-c-reference"></a>int (référence C#)

`int` désigne un type intégral qui stocke des valeurs en fonction de la taille et de la plage indiquées dans le tableau suivant.  
  
|Type|Plage|Taille|Type .NET Framework|Valeur par défaut|  
|----------|-----------|----------|-------------------------|-------------------|  
|`int`|-2,147,483,648 en 2,147,483,647|Entier 32 bits signé|<xref:System.Int32?displayProperty=nameWithType>|0|  
  
## <a name="literals"></a>Littéraux  
 
Vous pouvez déclarer et initialiser une variable `int` en lui assignant un littéral décimal, un littéral hexadécimal ou un littéral binaire (à compter de C# 7).  Si le littéral entier est en dehors de la plage autorisée pour le type `int` (autrement dit, s’il est inférieur à <xref:System.Int32.MinValue?displayProperty=nameWithType> ou supérieur à <xref:System.Int32.MaxValue?displayProperty=nameWithType>), une erreur de compilation se produit. 

Dans l’exemple suivant, les entiers égaux à 90 946 représentés comme des littéraux décimaux, hexadécimaux et binaires sont assignés aux valeurs `int`.  
  
[!code-csharp[int](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Int)]  

> [!NOTE] 
> Vous utilisez le préfixe `0x` ou `0X` pour désigner un littéral hexadécimal, et le préfixe `0b` ou `0B` pour désigner un littéral binaire. Les littéraux décimaux n’ont pas de préfixe. 

À partir de C# 7, quelques fonctionnalités ont été ajoutées améliorer la lisibilité. 
 - C# 7.0 permet l’utilisation d’un caractère de soulignement `_`, comme un séparateur de chiffre.
 - 7.2 c# permet `_` à utiliser comme séparateur de chiffres pour un littéral binaire ou en hexadécimal, après le préfixe. Un littéral décimal n’est pas autorisé à avoir un trait de soulignement.

Certains exemples sont présentés ci-dessous.

[!code-csharp[int](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#IntS)]  
 
 Les littéraux entiers peuvent également inclure un suffixe désignant le type, bien qu’il n’existe aucun suffixe qui désigne le type `int`. Quand un littéral entier n’a pas de suffixe, son type est le premier des types suivants dans lesquels sa valeur peut être représentée : 

1. `int`
2. [uint](../../../csharp/language-reference/keywords/uint.md)
3. [long](../../../csharp/language-reference/keywords/long.md)
4. [ulong](../../../csharp/language-reference/keywords/ulong.md) 
 
Dans ces exemples, le littéral 90946 est de type `int`.
  
## <a name="conversions"></a>Conversions  
 Il existe une conversion implicite prédéfinie de `int` en [long](../../../csharp/language-reference/keywords/long.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md) ou [decimal](../../../csharp/language-reference/keywords/decimal.md). Exemple :  
  
```csharp  
// '123' is an int, so an implicit conversion takes place here:  
float f = 123;  
```  
  
 Il existe une conversion implicite prédéfinie de [sbyte](../../../csharp/language-reference/keywords/sbyte.md), [byte](../../../csharp/language-reference/keywords/byte.md), [short](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md) ou [char](../../../csharp/language-reference/keywords/char.md) en `int`. Par exemple, l’instruction d’assignation suivante génère une erreur de compilation sans cast :  
  
```csharp  
long aLong = 22;  
int i1 = aLong;       // Error: no implicit conversion from long.  
int i2 = (int)aLong;  // OK: explicit conversion.  
```  
  
 Remarquez également qu’il n’existe pas de conversion implicite des types virgule flottante en `int`. Par exemple, l’instruction suivante génère une erreur du compilateur à moins qu’un cast explicite soit utilisé :  
  
```csharp  
int x = 3.0;         // Error: no implicit conversion from double.  
int y = (int)3.0;    // OK: explicit conversion.  
```  
  
 Pour plus d’informations sur les expressions arithmétiques combinant des types virgule flottante et des types intégraux, consultez [float](../../../csharp/language-reference/keywords/float.md) et [double](../../../csharp/language-reference/keywords/double.md).  
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Int32>  
 [Référence C#](../../../csharp/language-reference/index.md)  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [Mots clés C#](../../../csharp/language-reference/keywords/index.md)  
 [Tableau des types intégraux](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [Tableau des types intégrés](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [Tableau des conversions numériques implicites](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [Tableau des conversions numériques explicites](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
