---
title: "decimal (r&#233;f&#233;rence C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "decimal_CSharpKeyword"
  - "decimal"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "decimal (mot clé C#)"
ms.assetid: b6522132-b5ee-4be3-ad13-3adfdb7de7a1
caps.latest.revision: 32
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 32
---
# decimal (r&#233;f&#233;rence C#)
Le mot clé `decimal` indique un type de données 128 bits.  Par rapport aux types virgule flottante, le type `decimal` fournit une plus grande précision et une plage de valeurs plus réduite ; il est donc particulièrement approprié aux calculs financiers et monétaires.  Le tableau suivant indique la plage de valeurs approximative et la précision fournies par le type `decimal`.  
  
|Type|Plage approximative|Précision|Type .NET Framework|  
|----------|-------------------------|---------------|-------------------------|  
|`decimal`|\(\-7.9 x 10<sup>28</sup> à 7.9 x 10<sup>28</sup>\) \/ \(10<sup>0 à 28</sup>\)|28\-29 chiffres significatifs|<xref:System.Decimal?displayProperty=fullName>|  
  
## Littéraux  
 Si vous souhaitez qu'un littéral numérique réel soit considéré comme une valeur de type `decimal`, utilisez le suffixe m ou M, comme indiqué ci\-après :  
  
```  
  
decimal myMoney = 300.5m;  
```  
  
 Si le suffixe m n'est pas spécifié, le nombre est considéré comme une valeur de type [double](../../../csharp/language-reference/keywords/double.md) et génère une erreur du compilateur.  
  
## Conversions  
 Les types intégraux sont convertis implicitement en type `decimal` et ont pour résultat une valeur de type `decimal`.  Par conséquent, vous pouvez initialiser une variable de type decimal avec un littéral d'entier, sans utiliser de suffixe, par exemple :  
  
```  
  
decimal myMoney = 300;  
```  
  
 Étant donné qu'il n'y a pas de conversion implicite entre les types virgule flottante et le type `decimal`, un cast doit être utilisé pour convertir ces types.  Par exemple :  
  
```  
  
        decimal myMoney = 99.9m;  
double x = (double)myMoney;  
myMoney = (decimal)x;  
```  
  
 Vous pouvez aussi combiner, au sein d'une même expression, des types `decimal` et des types numériques intégraux.  En revanche, si vous combinez le type `decimal` avec des types virgule flottante sans spécifier de cast, une erreur de compilation se produit.  
  
 Pour plus d'informations sur les conversions numériques implicites, consultez [Tableau des conversions numériques implicites](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).  
  
 Pour plus d'informations sur les conversions numériques explicites, consultez [Tableau des conversions numériques explicites](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md).  
  
## Application d'un format à un résultat de type decimal  
 Vous pouvez appliquer un format à un résultat à l'aide de la méthode `String.Format`, ou de la méthode <xref:System.Console.Write%2A?displayProperty=fullName>, qui appelle `String.Format()`.  Le format monétaire est spécifié à l'aide du format de chaîne monétaire standard « C » ou « c », comme le montre le second exemple traité ultérieurement dans cet article.  Pour plus d'informations sur la méthode `String.Format`, consultez <xref:System.String.Format%2A?displayProperty=fullName>.  
  
## Exemple  
 L'exemple suivant provoque une erreur du compilateur en essayant d'ajouter [double](../../../csharp/language-reference/keywords/double.md) et des variables `decimal`.  
  
```c#  
double dub = 9;  
// The following line causes an error that reads "Operator '+' cannot be applied to   
// operands of type 'double' and 'decimal'"  
Console.WriteLine(dec + dub);   
  
// You can fix the error by using explicit casting of either operand.  
Console.WriteLine(dec + (decimal)dub);  
Console.WriteLine((double)dec + dub);  
  
```  
  
 Le résultat est l'erreur suivante :  
  
 `Operator '+' cannot be applied to operands of type 'double' and 'decimal'`  
  
 Dans cet exemple, un `decimal` et un [int](../../../csharp/language-reference/keywords/int.md) sont combinés dans la même expression.  Le résultat est de type `decimal`.  
  
 [!code-cs[csrefKeywordsTypes#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/decimal_1.cs)]  
  
## Exemple  
 Dans cet exemple, le résultat est mis en forme à l'aide de la chaîne de format monétaire.  Notez que la valeur `x` est arrondie, car le nombre de décimales excède 0,99 $.  La variable `y`, représentant le nombre maximal exact de chiffres, est affichée dans le format correct.  
  
 [!code-cs[csrefKeywordsTypes#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/decimal_2.cs)]  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## Voir aussi  
 <xref:System.Decimal>   
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Mots clés C\#](../../../csharp/language-reference/keywords/index.md)   
 [Tableau des types intégraux](../../../csharp/language-reference/keywords/integral-types-table.md)   
 [Tableau des types intégrés](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [Tableau des conversions numériques implicites](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)   
 [Tableau des conversions numériques explicites](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)   
 [Chaînes de format numériques standard](../Topic/Standard%20Numeric%20Format%20Strings.md)