---
title: "short (référence C#) | Microsoft Docs"
ms.date: 2017-03-14
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- short
- short_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- short keyword [C#]
ms.assetid: 04c10688-e51a-4a87-bfec-83f7fb42ff11
caps.latest.revision: 17
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 400dfda51d978f35c3995f90840643aaff1b9c13
ms.openlocfilehash: 14f9c66bb620e2ad35513abeeba77372904cc1f3
ms.contentlocale: fr-fr
ms.lasthandoff: 03/24/2017

---
# <a name="short-c-reference"></a>short (référence C#)

`short` désigne un type de données intégral qui stocke des valeurs en fonction de la taille et de la plage indiquées dans le tableau suivant.  
  
|Type|Plage|Taille|Type .NET Framework|  
|----------|-----------|----------|-------------------------|  
|`short`|de -32 768 à 32 767|Entier 16 bits signé|<xref:System.Int16?displayProperty=fullName>|  
  
## <a name="literals"></a>Littéraux  

Vous pouvez déclarer et initialiser une variable `short` en lui assignant un littéral décimal, un littéral hexadécimal ou un littéral binaire (à compter de C# 7).  Si le littéral entier est en dehors de la plage de `short` (autrement dit, s’il est inférieur à <xref:System.Int16.MinValue?displayProperty=fullName> ou supérieur à <xref:System.Int16.MaxValue?displayProperty=fullName>), une erreur de compilation se produit. 

Dans l’exemple suivant, les entiers égaux à 1 034 représentés comme des littéraux décimaux, hexadécimaux et binaires sont implicitement convertis à partir de valeurs [int](../../../csharp/language-reference/keywords/int.md) en `short`.  
  
[!code-cs[Short](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Short)]  

> [!NOTE] 
> Vous utilisez le préfixe `0x` ou `0X` pour désigner un littéral hexadécimal, et le préfixe `0b` ou `0B` pour désigner un littéral binaire. Les littéraux décimaux n’ont pas de préfixe.

À compter de C# 7, vous pouvez également utiliser le caractère de soulignement, `_`, comme séparateur numérique pour améliorer la lisibilité, comme dans l’exemple suivant.

[!code-cs[Short](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#ShortS)]  
 
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
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Int16>   
 [Informations de référence sur C#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Mots clés C#](../../../csharp/language-reference/keywords/index.md)   
 [Tableau des types intégraux](../../../csharp/language-reference/keywords/integral-types-table.md)   
 [Tableau des types intégrés](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [Tableau des conversions numériques implicites](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)   
 [Tableau des conversions numériques explicites](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
