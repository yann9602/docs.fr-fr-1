---
title: "long (référence C#)"
ms.date: 03/14/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- long_CSharpKeyword
- long
helpviewer_keywords: long keyword [C#]
ms.assetid: f9b24319-1f39-48be-a42b-d528ee28a7fd
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7f18bed80550b293195961fd9d42491dd571cbaf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="long-c-reference"></a>long (référence C#)

`long` désigne un type intégral qui stocke des valeurs en fonction de la taille et de la plage indiquées dans le tableau suivant.  
  
|Type|Plage|Taille|Type .NET Framework|  
|----------|-----------|----------|-------------------------|  
|`long`|-9 223 372 036 854 775 808 à 9 223 372 036 854 775 807|Entier 64 bits signé|<xref:System.Int64?displayProperty=nameWithType>|  
  
## <a name="literals"></a>Littéraux 

Vous pouvez déclarer et initialiser une variable `long` en lui assignant un littéral décimal, un littéral hexadécimal ou un littéral binaire (à compter de C# 7). 

Dans l’exemple suivant, les entiers égaux à 4 294 967 296 représentés comme des littéraux décimaux, hexadécimaux et binaires sont assignés aux valeurs `long`.  
  
[!code-csharp[long](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Long)]  

> [!NOTE] 
> Vous utilisez le préfixe `0x` ou `0X` pour désigner un littéral hexadécimal, et le préfixe `0b` ou `0B` pour désigner un littéral binaire. Les littéraux décimaux n’ont pas de préfixe. 

À partir de C# 7, quelques fonctionnalités ont été ajoutées améliorer la lisibilité. 
 - C# 7.0 permet l’utilisation d’un caractère de soulignement `_`, comme un séparateur de chiffre.
 - 7.2 c# permet `_` à utiliser comme séparateur de chiffres pour un littéral binaire ou en hexadécimal, après le préfixe. Un littéral décimal n’est pas autorisé à avoir un trait de soulignement.

Certains exemples sont présentés ci-dessous.

[!code-csharp[long](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#LongS)]  
 
 Les littéraux entiers peuvent également inclure un suffixe qui désigne le type. Le suffixe `L` désigne un type `long`. L’exemple suivant utilise le suffixe `L` pour désigner un entier long :
 
```csharp
long value = 4294967296L;  
```  

> [!NOTE]
>  Vous pouvez aussi utiliser la lettre minuscule « l » comme suffixe. Ceci génère cependant un avertissement du compilateur, car la lettre « l » peut être facilement confondue avec le chiffre « 1 ». Utilisez « L » pour plus de clarté.  
  
 Quand vous utilisez le suffixe `L`, le type du littéral entier est déterminé comme étant `long` ou [ulong](../../../csharp/language-reference/keywords/ulong.md), en fonction de sa taille. Dans ce cas, le type est `long`, car le littéral est inférieur à la plage de [ulong](../../../csharp/language-reference/keywords/ulong.md).  
  
 Le suffixe est souvent utilisé pour appeler des méthodes surchargées. Par exemple, les méthodes surchargées suivantes ont des paramètres de type `long` et [int](../../../csharp/language-reference/keywords/int.md) :  
  
```csharp
public static void SampleMethod(int i) {}  
public static void SampleMethod(long l) {}  
```  
  
 Le suffixe `L` garantit que la surcharge appropriée est appelée :  
  
```csharp  
SampleMethod(5);    // Calls the method with the int parameter  
SampleMethod(5L);   // Calls the method with the long parameter  
```  
Quand un littéral entier n’a pas de suffixe, son type est le premier des types suivants dans lesquels sa valeur peut être représentée : 

1. [int](int.md)
2. [uint](../../../csharp/language-reference/keywords/uint.md)
3. `long`
4. [ulong](../../../csharp/language-reference/keywords/ulong.md) 

Dans l’exemple précédent, le littéral 4294967296 est de type `long`, car il dépasse la plage de [uint](../../../csharp/language-reference/keywords/uint.md) (consultez le [Tableau des types intégraux](../../../csharp/language-reference/keywords/integral-types-table.md) pour les tailles de stockage des types intégraux).  
  
 Vous pouvez utiliser le type `long` avec d’autres types intégraux dans la même expression, l’expression est évaluée comme `long` (ou [bool](../../../csharp/language-reference/keywords/bool.md) dans le cas d’expressions relationnelles ou booléennes). Par exemple, l’expression suivante s’évalue en `long` :  
  
```csharp  
898L + 88  
```  
  
 Pour plus d’informations sur les expressions arithmétiques combinant des types virgule flottante et des types intégraux, consultez [float](../../../csharp/language-reference/keywords/float.md) et [double](../../../csharp/language-reference/keywords/double.md).  
  
## <a name="conversions"></a>Conversions  
 Il existe une conversion implicite prédéfinie de `long` en [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md) ou [decimal](../../../csharp/language-reference/keywords/decimal.md). Dans le cas contraire, vous devez utiliser un cast. Par exemple, l’instruction suivante génère une erreur de compilation sans un cast explicite :  
  
```csharp  
int x = 8L;        // Error: no implicit conversion from long to int  
int x = (int)8L;   // OK: explicit conversion to int  
```  
  
 Il existe une conversion implicite prédéfinie de [sbyte](../../../csharp/language-reference/keywords/sbyte.md), [byte](../../../csharp/language-reference/keywords/byte.md), [short](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md) ou [char](../../../csharp/language-reference/keywords/char.md) vers `long`.  
  
 Notez aussi qu’il n’existe pas de conversion implicite des types virgule flottante vers `long`. Par exemple, l’instruction suivante génère une erreur du compilateur, sauf si vous utilisez un cast explicite :  
  
```csharp  
long x = 3.0;         // Error: no implicit conversion from double  
long y = (long)3.0;   // OK: explicit conversion  
```  
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Int64>  
 [Référence C#](../../../csharp/language-reference/index.md)  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [Mots clés C#](../../../csharp/language-reference/keywords/index.md)  
 [Tableau des types intégraux](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [Tableau des types intégrés](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [Tableau des conversions numériques implicites](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [Tableau des conversions numériques explicites](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
