---
title: "long (référence C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- long_CSharpKeyword
- long
dev_langs:
- CSharp
helpviewer_keywords:
- long keyword [C#]
ms.assetid: f9b24319-1f39-48be-a42b-d528ee28a7fd
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
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: c28c8308d7ed32f7240f56113a77a0794cb1ba62
ms.lasthandoff: 03/13/2017

---
# <a name="long-c-reference"></a>long (référence C#)
Le mot clé `long` désigne un type intégral qui stocke des valeurs en fonction de la taille et de la plage indiquées dans le tableau suivant.  
  
|Type|Plage|Taille|Type .NET Framework|  
|----------|-----------|----------|-------------------------|  
|`long`|-9 223 372 036 854 775 808 à 9 223 372 036 854 775 807|Entier 64 bits signé|<xref:System.Int64?displayProperty=fullName>|  
  
## <a name="literals"></a>Littéraux  
 Vous pouvez déclarer et initialiser une variable `long` comme dans cet exemple :  
  
```  
  
long long1 = 4294967296;  
```  
  
 Quand un littéral entier n’a pas de suffixe, son type est le premier de ces types dans lesquels sa valeur peut être représentée : [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), `long`, [ulong](../../../csharp/language-reference/keywords/ulong.md). Dans l’exemple précédent, il est de type `long`, car il dépasse la plage de [uint](../../../csharp/language-reference/keywords/uint.md) (consultez [Tableau des types intégraux](../../../csharp/language-reference/keywords/integral-types-table.md) pour les tailles de stockage des types intégraux).  
  
 Vous pouvez aussi utiliser le suffixe L avec le type `long` comme ceci :  
  
```  
  
long long2 = 4294967296L;  
```  
  
 Quand vous utilisez le suffixe L, le type du littéral entier est déterminé comme étant `long` ou [ulong](../../../csharp/language-reference/keywords/ulong.md), en fonction de sa taille. Dans ce cas, il est `long`, car il est inférieur à la plage de [ulong](../../../csharp/language-reference/keywords/ulong.md).  
  
 Une utilisation courante du suffixe est d’appeler des méthodes surchargées. Considérons par exemple ces deux méthodes surchargées qui utilisent les paramètres `long` et [int](../../../csharp/language-reference/keywords/int.md) :  
  
```  
public static void SampleMethod(int i) {}  
public static void SampleMethod(long l) {}  
```  
  
 L’utilisation du suffixe L garantit que le type correct est appelé, par exemple :  
  
```  
SampleMethod(5);    // Calling the method with the int parameter  
SampleMethod(5L);   // Calling the method with the long parameter  
```  
  
 Vous pouvez utiliser le type `long` avec d’autres types numériques entiers dans la même expression, auquel cas l’expression est évaluée en `long` (ou [bool](../../../csharp/language-reference/keywords/bool.md) dans le cas d’expressions relationnelles ou booléennes). Par exemple, l’expression suivante s’évalue en `long` :  
  
```  
898L + 88  
```  
  
> [!NOTE]
>  Vous pouvez aussi utiliser la lettre minuscule « l » comme suffixe. Ceci génère cependant un avertissement du compilateur, car la lettre « l » peut être facilement confondue avec le chiffre « 1 ». Utilisez « L » pour plus de clarté.  
  
 Pour plus d’informations sur les expressions arithmétiques avec des types virgule flottante et des types intégraux, consultez [float](../../../csharp/language-reference/keywords/float.md) et [double](../../../csharp/language-reference/keywords/double.md).  
  
## <a name="conversions"></a>Conversions  
 Il existe une conversion implicite prédéfinie de `long` en [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md) ou [decimal](../../../csharp/language-reference/keywords/decimal.md). Dans le cas contraire, vous devez utiliser un cast. Par exemple, l’instruction suivante génère une erreur de compilation sans un cast explicite :  
  
```  
int x = 8L;        // Error: no implicit conversion from long to int  
int x = (int)8L;   // OK: explicit conversion to int  
```  
  
 Il existe une conversion implicite prédéfinie de [sbyte](../../../csharp/language-reference/keywords/sbyte.md), [byte](../../../csharp/language-reference/keywords/byte.md), [short](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md) ou [char](../../../csharp/language-reference/keywords/char.md) vers `long`.  
  
 Notez aussi qu’il n’existe pas de conversion implicite des types virgule flottante vers `long`. Par exemple, l’instruction suivante génère une erreur du compilateur, sauf si vous utilisez un cast explicite :  
  
```  
  
      long x = 3.0;         // Error: no implicit conversion from double  
long y = (long)3.0;   // OK: explicit conversion  
```  
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Int64>   
 [Informations de référence sur C#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Mots clés C#](../../../csharp/language-reference/keywords/index.md)   
 [Tableau des types intégraux](../../../csharp/language-reference/keywords/integral-types-table.md)   
 [Tableau des types prédéfinis](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [Tableau des conversions numériques implicites](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)   
 [Tableau des conversions numériques explicites](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
