---
title: "double (référence C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- double
- double_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- double data type [C#]
ms.assetid: 0980e11b-6004-4102-abcf-cfc280fc6991
caps.latest.revision: 26
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
ms.openlocfilehash: ccdd29c78a3cdc9d32fa08b1be94eecd717418fc
ms.lasthandoff: 03/13/2017

---
# <a name="double-c-reference"></a>double (référence C#)
Le mot clé `double` désigne un type simple qui stocke des valeurs à virgule flottante de 64 bits. Le tableau suivant montre la précision et la plage approximative pour le type `double`.  
  
|Type|Plage approximative|Précision|Type .NET Framework|  
|----------|-----------------------|---------------|-------------------------|  
|`double`|De ±5,0 × 10<sup>−324</sup> à ±1,7 × 10<sup>308</sup>|15 à 16 chiffres|<xref:System.Double?displayProperty=fullName>|  
  
## <a name="literals"></a>Littéraux  
 Par défaut, un littéral numérique réel sur le côté droit de l’opérateur d’assignation est traité comme `double`. Toutefois, si vous souhaitez qu’un nombre entier soit traité comme `double`, utilisez le suffixe d ou D, par exemple :  
  
```  
  
double x = 3D;  
```  
  
## <a name="conversions"></a>Conversions  
 Vous pouvez combiner des types numériques intégraux et des types virgule flottante dans une expression. Dans ce cas, les types intégraux sont convertis en types virgule flottante. L’évaluation de l’expression est exécutée d’après les règles suivantes :  
  
-   Si l’un des types virgule flottante est `double`, l’expression prend la valeur `double`, ou [bool](../../../csharp/language-reference/keywords/bool.md) dans les expressions relationnelles ou booléennes.  
  
-   S’il n’existe aucun type `double` dans l’expression, elle prend la valeur [float](../../../csharp/language-reference/keywords/float.md), ou [bool](../../../csharp/language-reference/keywords/bool.md) dans les expressions relationnelles ou booléennes.  
  
 Une expression à virgule flottante peut contenir les ensembles de valeurs suivants :  
  
-   Zéro positif et négatif.  
  
-   Infini positif et négatif.  
  
-   Valeur NaN (N’est pas un nombre).  
  
-   L’ensemble fini de valeurs différentes de zéro.  
  
 Pour plus d’informations sur ces valeurs, consultez IEEE Standard for Binary Floating-Point Arithmetic, disponible sur le site web de l’[IEEE](http://go.microsoft.com/fwlink/?LinkId=26269).  
  
## <a name="example"></a>Exemple  
 Dans l’exemple suivant, un [int](../../../csharp/language-reference/keywords/int.md), un [short](../../../csharp/language-reference/keywords/short.md), un [float](../../../csharp/language-reference/keywords/float.md)et un `double` sont ajoutés pour donner un résultat `double`.  
  
 [!code-cs[csrefKeywordsTypes#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/double_1.cs)]  
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Référence C#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Mots clés C#](../../../csharp/language-reference/keywords/index.md)   
 [Tableau des valeurs par défaut](../../../csharp/language-reference/keywords/default-values-table.md)   
 [Tableau des types intégrés](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [Tableau des types virgule flottante](../../../csharp/language-reference/keywords/floating-point-types-table.md)   
 [Tableau des conversions numériques implicites](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)   
 [Tableau des conversions numériques explicites](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
