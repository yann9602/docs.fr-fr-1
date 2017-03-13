---
title: "double (r&#233;f&#233;rence C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "double"
  - "double_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "double (type de données C#)"
ms.assetid: 0980e11b-6004-4102-abcf-cfc280fc6991
caps.latest.revision: 26
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 26
---
# double (r&#233;f&#233;rence C#)
Le mot clé `double` désigne un type simple qui stocke des valeurs 64 bits en virgule flottante.  Le tableau suivant indique la plage de valeurs approximative et la précision fournies par le type `double`.  
  
|Type|Plage approximative|Précision|Type .NET Framework|  
|----------|-------------------------|---------------|-------------------------|  
|`double`|±5.0 × 10<sup>−324</sup> à ±1.7 × 10<sup>308</sup>|15\-16 chiffres|<xref:System.Double?displayProperty=fullName>|  
  
## Littéraux  
 Par défaut, un littéral numérique réel situé à droite de l'opérateur d'assignation est considéré de type `double`.  Si vous souhaitez qu'un nombre entier soit considéré comme une valeur de type `double`, utilisez le suffixe d ou D, comme indiqué ci\-après :  
  
```  
  
double x = 3D;  
```  
  
## Conversions  
 Vous pouvez combiner, au sein d'une expression, des types numériques intégraux et des types virgule flottante.  Dans ce cas, les types intégraux sont convertis en types en virgule flottante.  L'expression est évaluée selon les règles suivantes :  
  
-   Si l'un des types virgule flottante est `double`, le résultat de l'évaluation est aussi de type `double` ou [bool](../../../csharp/language-reference/keywords/bool.md) dans des expressions relationnelles ou booléennes.  
  
-   Si l'expression ne comporte pas de type `double`, le résultat de l'évaluation est de type [float](../../../csharp/language-reference/keywords/float.md) ou [bool](../../../csharp/language-reference/keywords/bool.md) dans des expressions relationnelles ou booléennes.  
  
 Une expression en virgule flottante peut contenir les ensembles de valeurs suivants :  
  
-   Zéro positif et zéro négatif.  
  
-   Nombre positif infini et nombre négatif infini.  
  
-   Valeur non numérique \(NaN ou Not\-a\-Number\).  
  
-   Ensemble fini des valeurs différentes de zéro.  
  
 Pour plus d'informations sur ces valeurs, consultez IEEE Standard for Binary Floating\-Point Arithmetic, disponible sur le site Web [IEEE](http://go.microsoft.com/fwlink/?LinkId=26269).  
  
## Exemple  
 Dans l'exemple suivant, [int](../../../csharp/language-reference/keywords/int.md), [short](../../../csharp/language-reference/keywords/short.md), [float](../../../csharp/language-reference/keywords/float.md) et `double` sont ajoutés pour donner un résultat `double`.  
  
 [!code-cs[csrefKeywordsTypes#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/double_1.cs)]  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Mots clés C\#](../../../csharp/language-reference/keywords/index.md)   
 [Tableau des valeurs par défaut](../../../csharp/language-reference/keywords/default-values-table.md)   
 [Tableau des types intégrés](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [Tableau des types virgule flottante](../../../csharp/language-reference/keywords/floating-point-types-table.md)   
 [Tableau des conversions numériques implicites](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)   
 [Tableau des conversions numériques explicites](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)