---
title: "float (r&#233;f&#233;rence C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "float"
  - "float_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "float (mot clé C#)"
  - "chiffres à virgule flottante (C#), float (mot clé)"
ms.assetid: 1e77db7b-dedb-48b7-8dd1-b055e96a9258
caps.latest.revision: 24
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 24
---
# float (r&#233;f&#233;rence C#)
Le mot clé `float` désigne un type simple qui stocke des valeurs 32 bits en virgule flottante.  Le tableau suivant indique la plage de valeurs approximative et la précision fournies par le type `float`.  
  
|Type|Plage approximative|Précision|Type .NET Framework|  
|----------|-------------------------|---------------|-------------------------|  
|`float`|\-3,4 × 10<sup>38</sup>à \+3,4 × 10<sup>38</sup>|7 chiffres|<xref:System.Single?displayProperty=fullName>|  
  
## Littéraux  
 Par défaut, un littéral numérique réel situé à droite de l'opérateur d'assignation est considéré de type [double](../../../csharp/language-reference/keywords/double.md).  Par conséquent, si vous souhaitez initialiser une variable de type float, utilisez le suffixe `f` ou `F`, comme indiqué ci\-après :  
  
```  
  
float x = 3.5F;  
```  
  
 Si vous ne spécifiez aucun suffixe dans la déclaration ci\-dessus, une erreur de compilation se produit, car vous essayez de stocker une valeur [double](../../../csharp/language-reference/keywords/double.md) dans une variable `float`.  
  
## Conversions  
 Vous pouvez combiner, au sein d'une expression, des types numériques intégraux et des types virgule flottante.  Dans ce cas, les types intégraux sont convertis en types en virgule flottante.  L'expression est évaluée selon les règles suivantes :  
  
-   Si l'un des types virgule flottante est [double](../../../csharp/language-reference/keywords/double.md), le résultat de l'évaluation est aussi de type [double](../../../csharp/language-reference/keywords/double.md) ou de type [bool](../../../csharp/language-reference/keywords/bool.md) dans des expressions relationnelles ou booléennes.  
  
-   Si l'expression ne comporte pas de type [double](../../../csharp/language-reference/keywords/double.md), le résultat de l'évaluation est de type `float` ou [bool](../../../csharp/language-reference/keywords/bool.md) dans des expressions relationnelles ou booléennes.  
  
 Une expression en virgule flottante peut contenir les ensembles de valeurs suivants :  
  
-   Zéro positif et zéro négatif  
  
-   Nombre positif infini et nombre négatif infini  
  
-   Valeur non numérique \(NaN ou Not\-a\-Number\)  
  
-   Ensemble fini des valeurs différentes de zéro  
  
 Pour plus d'informations sur ces valeurs, consultez IEEE Standard for Binary Floating\-Point Arithmetic, disponible sur le site Web [IEEE](http://go.microsoft.com/fwlink/?LinkId=26269).  
  
## Exemple  
 Dans l'exemple suivant, un [int](../../../csharp/language-reference/keywords/int.md), un [short](../../../csharp/language-reference/keywords/short.md) et un `float` sont inclus dans une expression mathématique produisant un résultat `float`.  \(N'oubliez pas que `float` est un alias pour le type <xref:System.Single?displayProperty=fullName>.\) Notez l'absence de [double](../../../csharp/language-reference/keywords/double.md) dans l'expression.  
  
 [!code-cs[csrefKeywordsTypes#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/float_1.cs)]  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## Voir aussi  
 <xref:System.Single>   
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Cast et conversions de types](../../../csharp/programming-guide/types/casting-and-type-conversions.md)   
 [Mots clés C\#](../../../csharp/language-reference/keywords/index.md)   
 [Tableau des types intégraux](../../../csharp/language-reference/keywords/integral-types-table.md)   
 [Tableau des types intégrés](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [Tableau des conversions numériques implicites](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)   
 [Tableau des conversions numériques explicites](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)