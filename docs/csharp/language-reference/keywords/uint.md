---
title: "uint (référence C#)"
ms.date: 2017-03-14
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- uint
- uint_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- uint keyword [C#]
ms.assetid: e93e42c6-ec72-4b0b-89df-2fd8d36f7a7b
caps.latest.revision: 18
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
ms.openlocfilehash: 4342c08ab536f45a2e3b5fa6fe94839436600a4a
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="uint-c-reference"></a>uint (référence C#)

Le mot clé `uint` désigne un type intégral qui stocke des valeurs en fonction de la taille et de la plage indiquées dans le tableau suivant.  
  
|Type|Plage|Taille|Type .NET Framework|  
|----------|-----------|----------|-------------------------|  
|`uint`|de 0 à 4 294 967 295|Entier 32 bits non signé|<xref:System.UInt32?displayProperty=fullName>|  
  
 **Note** Le type `uint` n’est pas conforme CLS. Utilisez `int` autant que possible.  
  
## <a name="literals"></a>Littéraux  

Vous pouvez déclarer et initialiser une variable `uint` en lui assignant un littéral décimal, un littéral hexadécimal ou un littéral binaire (à compter de C# 7). Si le littéral entier est en dehors de la plage de `uint` (autrement dit, s’il est inférieur à <xref:System.UInt32.MinValue?displayProperty=fullName> ou supérieur à <xref:System.UInt32.MaxValue?displayProperty=fullName>), une erreur de compilation se produit.

Dans l’exemple suivant, les entiers égaux à 3 000 000 000 représentés comme des littéraux décimaux, hexadécimaux et binaires sont assignés aux valeurs `uint`.  
  
[!code-cs[uint](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UInt)]  

> [!NOTE] 
> Vous utilisez le préfixe `0x` ou `0X` pour désigner un littéral hexadécimal, et le préfixe `0b` ou `0B` pour désigner un littéral binaire. Les littéraux décimaux n’ont pas de préfixe. 

À compter de C# 7, vous pouvez également utiliser le caractère de soulignement, `_`, comme séparateur numérique pour améliorer la lisibilité, comme dans l’exemple suivant.

[!code-cs[uint](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UIntS)]  
 
 Les littéraux entiers peuvent également inclure un suffixe qui désigne le type. Le suffixe `U` ou « u » désigne un type `uint` ou `ulong`, selon la valeur numérique du littéral. L’exemple suivant utilise le suffixe `u` pour désigner un entier non signé des deux types. Notez que le premier littéral est un type `uint`, car sa valeur est inférieure à <xref:System.UInt32.MaxValue?displayProperty=fullName>, tandis que le deuxième est un type `ulong`, car sa valeur est supérieure à <xref:System.UInt32.MaxValue?displayProperty=fullName>.

[!code-cs[usuffix](../../../../samples/snippets/csharp/language-reference/keywords/numeric-suffixes.cs#1)]  
 
Quand un littéral entier n’a pas de suffixe, son type est le premier des types suivants dans lesquels sa valeur peut être représentée : 

1. [int](int.md)
2. `uint`
3. [long](../../../csharp/language-reference/keywords/long.md)
4. [ulong](../../../csharp/language-reference/keywords/ulong.md) 
  
## <a name="conversions"></a>Conversions  
 Il existe une conversion implicite prédéfinie de `uint` en [long](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md) et [decimal](../../../csharp/language-reference/keywords/decimal.md). Exemple :  
  
```csharp  
float myFloat = 4294967290;   // OK: implicit conversion to float  
```  
  
 Il existe une conversion implicite prédéfinie de [byte](../../../csharp/language-reference/keywords/byte.md), [ushort](../../../csharp/language-reference/keywords/ushort.md) ou [char](../../../csharp/language-reference/keywords/char.md) en `uint`. Dans le cas contraire, vous devez utiliser un cast. Par exemple, l’instruction d’assignation suivante génère une erreur de compilation sans cast :  
  
```csharp  
long aLong = 22;  
// Error -- no implicit conversion from long:  
uint uInt1 = aLong;   
// OK -- explicit conversion:  
uint uInt2 = (uint)aLong;  
```  
  
 Remarquez également qu’il n’existe pas de conversion implicite des types virgule flottante en `uint`. Par exemple, l’instruction suivante génère une erreur du compilateur à moins qu’un cast explicite soit utilisé :  
  
```csharp  
// Error -- no implicit conversion from double:  
uint x = 3.0;  
// OK -- explicit conversion:  
uint y = (uint)3.0;   
```  
  
 Pour plus d’informations sur les expressions arithmétiques dans lesquelles coexistent des types virgule flottante et des types intégraux, consultez [float](../../../csharp/language-reference/keywords/float.md) et [double](../../../csharp/language-reference/keywords/double.md).  
  
 Pour plus d’informations sur les règles des conversions numériques implicites, consultez le [Tableau des conversions numériques implicites](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).  
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.UInt32>   
 [Informations de référence sur C#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Mots clés C#](../../../csharp/language-reference/keywords/index.md)   
 [Tableau des types intégraux](../../../csharp/language-reference/keywords/integral-types-table.md)   
 [Tableau des types intégrés](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [Tableau des conversions numériques implicites](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)   
 [Tableau des conversions numériques explicites](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)

