---
title: "short (référence C#)"
ms.date: 03/14/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- short
- short_CSharpKeyword
helpviewer_keywords: short keyword [C#]
ms.assetid: 04c10688-e51a-4a87-bfec-83f7fb42ff11
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8ca3c5444c4fa7a49b7169be3e2a5b15d1a72207
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="short-c-reference"></a>short (référence C#)

`short` désigne un type de données intégral qui stocke des valeurs en fonction de la taille et de la plage indiquées dans le tableau suivant.  
  
|Type|Plage|Taille|Type .NET Framework|  
|----------|-----------|----------|-------------------------|  
|`short`|de -32 768 à 32 767|Entier 16 bits signé|<xref:System.Int16?displayProperty=nameWithType>|  
  
## <a name="literals"></a>Littéraux  

Vous pouvez déclarer et initialiser une variable `short` en lui assignant un littéral décimal, un littéral hexadécimal ou un littéral binaire (à compter de C# 7).  Si le littéral entier est en dehors de la plage autorisée pour le type `short` (autrement dit, s’il est inférieur à <xref:System.Int16.MinValue?displayProperty=nameWithType> ou supérieur à <xref:System.Int16.MaxValue?displayProperty=nameWithType>), une erreur de compilation se produit. 

Dans l’exemple suivant, les entiers égaux à 1 034 représentés comme des littéraux décimaux, hexadécimaux et binaires sont implicitement convertis à partir de valeurs [int](../../../csharp/language-reference/keywords/int.md) en `short`.  
  
[!code-csharp[Short](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Short)]  

> [!NOTE] 
> Vous utilisez le préfixe `0x` ou `0X` pour désigner un littéral hexadécimal, et le préfixe `0b` ou `0B` pour désigner un littéral binaire. Les littéraux décimaux n’ont pas de préfixe.

À partir de C# 7, quelques fonctionnalités ont été ajoutées améliorer la lisibilité. 
 - C# 7.0 permet l’utilisation d’un caractère de soulignement `_`, comme un séparateur de chiffre.
 - 7.2 c# permet `_` à utiliser comme séparateur de chiffres pour un littéral binaire ou en hexadécimal, après le préfixe. Un littéral décimal n’est pas autorisé à avoir un trait de soulignement.

Certains exemples sont présentés ci-dessous.

[!code-csharp[Short](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#ShortS)]  
 
## <a name="compiler-overload-resolution"></a>Résolution de surcharge du compilateur

 Un cast doit être utilisé lors de l’appel de méthodes surchargées. Prenons l’exemple des méthodes surchargées suivantes ayant pour paramètres `short` et [int](../../../csharp/language-reference/keywords/int.md) :  
  
```csharp  
public static void SampleMethod(int i) {}  
public static void SampleMethod(short s) {}  
```  
  
 L’utilisation du cast `short` garantit l’appel du type correct, par exemple :  
  
```csharp  
SampleMethod(5);         // Calling the method with the int parameter  
SampleMethod((short)5);  // Calling the method with the short parameter  
```  
  
## <a name="conversions"></a>Conversions  

 Il existe une conversion implicite prédéfinie de `short` en [int](../../../csharp/language-reference/keywords/int.md), [long](../../../csharp/language-reference/keywords/long.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md) ou [decimal](../../../csharp/language-reference/keywords/decimal.md).  
  
 Vous ne pouvez pas convertir implicitement des types numériques non littéraux de taille de stockage supérieure à `short` (consultez le [tableau des types intégraux](../../../csharp/language-reference/keywords/integral-types-table.md) pour voir les tailles de stockage des types intégraux). Prenez l’exemple des deux variables `short``x` et `y` suivantes :  
  
```csharp  
short x = 5, y = 12;  
```  
  
 L’instruction d’assignation suivante entraîne une erreur de compilation, car l’expression arithmétique située à droite de l’opérateur d’assignation donne la valeur [int](../../../csharp/language-reference/keywords/int.md) par défaut.  
  
```csharp
short z  = x + y;        // Compiler error CS0266: no conversion from int to short
```

 Pour corriger ce problème, utilisez un cast :  
  
```csharp
short z  = (short)(x + y);   // Explicit conversion
```
  
 Il est toutefois possible d’utiliser les instructions suivantes, dans lesquelles la variable de destination a une taille de stockage égale ou supérieure :  
  
```csharp  
int m = x + y;  
long n = x + y;  
```  
  
 Il n’existe pas de conversion implicite des types virgule flottante en `short`. Par exemple, l’instruction suivante génère une erreur du compilateur à moins qu’un cast explicite soit utilisé :  
  
```csharp  
short x = 3.0;          // Error: no implicit conversion from double  
short y = (short)3.0;   // OK: explicit conversion  
```  
  
 Pour plus d’informations sur les expressions arithmétiques combinant des types virgule flottante et des types intégraux, consultez [float](../../../csharp/language-reference/keywords/float.md) et [double](../../../csharp/language-reference/keywords/double.md).  
  
 Pour plus d’informations sur les règles des conversions numériques implicites, consultez le [tableau des conversions numériques implicites](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).  
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Int16>  
 [Référence C#](../../../csharp/language-reference/index.md)  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [Mots clés C#](../../../csharp/language-reference/keywords/index.md)  
 [Tableau des types intégraux](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [Tableau des types intégrés](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [Tableau des conversions numériques implicites](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [Tableau des conversions numériques explicites](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
