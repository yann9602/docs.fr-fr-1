---
title: "float (référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- float
- float_CSharpKeyword
helpviewer_keywords:
- float keyword [C#]
- floating-point numbers [C#], float keyword
ms.assetid: 1e77db7b-dedb-48b7-8dd1-b055e96a9258
caps.latest.revision: "24"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 846f132812fe90a285c81a020d440fc846f88b5b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="float-c-reference"></a>float (référence C#)
Le mot clé `float` désigne un type simple qui stocke des valeurs à virgule flottante de 32 bits. Le tableau suivant montre la précision et la plage approximative pour le type `float`.  
  
|Type|Plage approximative|Précision|Type .NET Framework|  
|----------|-----------------------|---------------|-------------------------|  
|`float`|-3,4 × 10<sup>38</sup> à +3,4 × 10<sup>38</sup>|7 chiffres|<xref:System.Single?displayProperty=nameWithType>|  
  
## <a name="literals"></a>Littéraux  
 Par défaut, un littéral numérique réel sur le côté droit de l’opérateur d’assignation est traité comme un [double](double.md). Par conséquent, pour initialiser une variable de type float, utilisez le suffixe `f` ou `F`, comme dans l’exemple suivant :  
  
```csharp
float x = 3.5F;  
```
  
 Si vous n’utilisez pas de suffixe dans la déclaration précédente, vous obtiendrez une erreur de compilation, puisque vous essayez de stocker une valeur [double](double.md) dans une variable `float`.  
  
## <a name="conversions"></a>Conversions  
 Vous pouvez combiner des types numériques intégraux et des types virgule flottante dans une expression. Dans ce cas, les types intégraux sont convertis en types virgule flottante. L’évaluation de l’expression est exécutée d’après les règles suivantes :  
  
-   Si l’un des types virgule flottante est [double](double.md), l’expression prend la valeur [double](double.md) ou [bool](bool.md) dans les expressions relationnelles ou booléennes.  
  
-   S’il n’existe aucun type [double](double.md) dans l’expression, elle prend la valeur `float` ou [bool](bool.md) dans les expressions relationnelles ou booléennes.  
  
 Une expression à virgule flottante peut contenir les ensembles de valeurs suivants :  
  
-   Zéro positif et négatif  
  
-   Infini positif et négatif  
  
-   Valeur NaN (N’est pas un nombre)  
  
-   L’ensemble fini de valeurs différentes de zéro  
  
 Pour plus d’informations sur ces valeurs, consultez IEEE Standard for Binary Floating-Point Arithmetic, disponible sur le site web de l’[IEEE](http://www.ieee.org).  
  
## <a name="example"></a>Exemple  
 Dans l’exemple suivant, un [int](int.md), un [short](short.md) et un `float` sont inclus dans une expression mathématique produisant un résultat `float`. (N’oubliez pas que `float` est un alias du type <xref:System.Single?displayProperty=nameWithType>.) Notez qu’il n’y a aucune valeur [double](double.md) dans l’expression.  
  
 [!code-csharp[csrefKeywordsTypes#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/float_1.cs)]  
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Single>  
 [Référence C#](../../../csharp/language-reference/index.md)  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [Cast et conversions de types](../../../csharp/programming-guide/types/casting-and-type-conversions.md)  
 [Mots clés C#](index.md)  
 [Tableau des types intégraux](integral-types-table.md)  
 [Tableau des types intégrés](built-in-types-table.md)  
 [Tableau des conversions numériques implicites](implicit-numeric-conversions-table.md)  
 [Tableau des conversions numériques explicites](explicit-numeric-conversions-table.md)
