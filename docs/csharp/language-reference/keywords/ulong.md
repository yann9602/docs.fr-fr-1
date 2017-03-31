---
title: "ulong (référence C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ulong_CSharpKeyword
- ulong
dev_langs:
- CSharp
helpviewer_keywords:
- ulong keyword [C#]
ms.assetid: f2ece624-837a-40cf-92c5-343e7f33397c
caps.latest.revision: 16
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
ms.openlocfilehash: 36de0add1d7fdf58745c65d231f3789c532ab69f
ms.lasthandoff: 03/13/2017

---
# <a name="ulong-c-reference"></a>ulong (référence C#)
Le mot clé `ulong` désigne un type intégral qui stocke des valeurs en fonction de la taille et de la plage indiquées dans le tableau suivant.  
  
|Type|Plage|Taille|Type .NET Framework|  
|----------|-----------|----------|-------------------------|  
|`ulong`|de 0 à 18 446 744 073 709 551 615|Entier 64 bits non signé|<xref:System.UInt64?displayProperty=fullName>|  
  
## <a name="literals"></a>Littéraux  
 Vous pouvez déclarer et initialiser une variable `ulong` comme dans cet exemple :  
  
```  
  
ulong uLong = 9223372036854775808;  
```  
  
 Quand un littéral entier n’a pas de suffixe, son type est le premier de ces types dans lesquels sa valeur peut être représentée : [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), `ulong`. Dans l’exemple ci-dessus, il est du type `ulong`.  
  
 Vous pouvez également utiliser des suffixes pour spécifier le type du littéral selon les règles suivantes :  
  
-   Si vous utilisez L ou l, le type du littéral entier est [long](../../../csharp/language-reference/keywords/long.md) ou `ulong` selon sa taille.  
  
    > [!NOTE]
    >  Vous pouvez utiliser la lettre minuscule « l » comme suffixe. Toutefois, ceci génère un avertissement du compilateur, car la lettre « l » peut être facilement confondue avec le chiffre « 1 ». Utilisez « L » pour plus de clarté.  
  
-   Si vous utilisez `U` ou `u`, le type du littéral entier est [uint](../../../csharp/language-reference/keywords/uint.md) ou `ulong` selon sa taille.  
  
-   Si vous utilisez UL, ul, Ul, uL, LU, lu, Lu ou lU, le type du littéral entier est `ulong`.  
  
     Par exemple, le résultat des trois instructions suivantes correspond au type système `UInt64`, qui correspond à l’alias `ulong` :  
  
    ```  
    Console.WriteLine(9223372036854775808L.GetType());  
    Console.WriteLine(123UL.GetType());  
    Console.WriteLine((123UL + 456).GetType());  
    ```  
  
 Une utilisation courante du suffixe est d’appeler des méthodes surchargées. Prenons l’exemple des méthodes surchargées suivantes ayant pour paramètres `ulong` et [int](../../../csharp/language-reference/keywords/int.md) :  
  
```  
public static void SampleMethod(int i) {}  
public static void SampleMethod(ulong l) {}  
```  
  
 L’utilisation d’un suffixe avec le paramètre `ulong` garantit que le type correct est appelé, par exemple :  
  
```  
SampleMethod(5);    // Calling the method with the int parameter  
SampleMethod(5UL);  // Calling the method with the ulong parameter  
```  
  
## <a name="conversions"></a>Conversions  
 Il existe une conversion implicite prédéfinie de `ulong` en [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md) ou [decimal](../../../csharp/language-reference/keywords/decimal.md).  
  
 Il n’existe aucune conversion implicite de `ulong` en un type intégral. Par exemple, l’instruction suivante génère une erreur de compilation sans cast explicite :  
  
```  
long long1 = 8UL;   // Error: no implicit conversion from ulong  
```  
  
 Il existe une conversion implicite prédéfinie de [byte](../../../csharp/language-reference/keywords/byte.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [uint](../../../csharp/language-reference/keywords/uint.md) ou [char](../../../csharp/language-reference/keywords/char.md) en `ulong`.  
  
 De plus, il n’existe pas de conversion implicite des types virgule flottante en `ulong`. Par exemple, l’instruction suivante génère une erreur du compilateur à moins qu’un cast explicite soit utilisé :  
  
```  
// Error -- no implicit conversion from double:  
ulong x = 3.0;  
// OK -- explicit conversion:  
ulong y = (ulong)3.0;    
```  
  
 Pour plus d’informations sur les expressions arithmétiques combinant des types virgule flottante et des types intégraux, consultez [float](../../../csharp/language-reference/keywords/float.md) et [double](../../../csharp/language-reference/keywords/double.md).  
  
 Pour plus d’informations sur les règles des conversions numériques implicites, consultez le [tableau des conversions numériques implicites](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).  
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.UInt64>   
 [Informations de référence sur C#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Mots clés C#](../../../csharp/language-reference/keywords/index.md)   
 [Tableau des types intégraux](../../../csharp/language-reference/keywords/integral-types-table.md)   
 [Tableau des types intégrés](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [Tableau des conversions numériques implicites](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)   
 [Tableau des conversions numériques explicites](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
