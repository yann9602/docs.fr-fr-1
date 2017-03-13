---
title: "Expressions (Guide de programmation C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "langage C#, expressions"
  - "expressions (C#)"
ms.assetid: c7d8feb0-0e58-4f94-8bf6-4d070550a832
caps.latest.revision: 22
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 22
---
# Expressions (Guide de programmation C#)
Une *expression* est une suite d'un ou plusieurs opérandes et de zéro ou plusieurs opérateurs qui peuvent être évalués à une valeur, un objet, une méthode ou un espace de noms unique.  Les expressions peuvent être constituées d'une valeur littérale, d'un appel de méthode, d'un opérateur et de ses opérandes ou d'un *nom simple*.  Les noms simples peuvent être le nom d'une variable, d'un membre de type, d'un paramètre de méthode, d'un espace de noms ou d'un type.  
  
 Les expressions peuvent utiliser des opérateurs qui à leur tour utilisent d'autres expressions comme paramètres, ou des appels de méthode dont les paramètres sont à leur tour d'autres appels de méthode, donc les expressions peuvent aller de simples à très complexes.  Voici deux exemples d'expressions :  
  
```  
((x < 10) && ( x > 5)) || ((x > 20) && (x < 25))   
System.Convert.ToInt32("35")  
```  
  
## Valeurs d'expression  
 Dans la plupart des contextes dans lesquels les expressions sont utilisées, par exemple dans les instructions ou les paramètres de méthode, l'expression est supposée être évaluée à une certaine valeur.  Si x et y sont des entiers, l'expression `x + y` est évaluée à une valeur numérique.  L'expression `new MyClass()` est évaluée à une référence à une nouvelle instance d'un objet `MyClass`.  L'expression `myClass.ToString()` est évaluée à une chaîne car il s'agit du type de retour de la méthode.  Toutefois, bien qu'un nom d'espace de noms soit classifié en tant qu'expression, il n'est pas évalué à une valeur et par conséquent ne peut jamais être le résultat final d'une expression.  Vous ne pouvez pas passer de nom d'espace de noms à un paramètre de méthode, ni l'utiliser dans une nouvelle expression ou l'attribuer à une variable.  Vous pouvez l'utiliser uniquement comme sous\-expression dans une expression plus grande.  Le même principe s'applique aux types \(par opposition aux objets <xref:System.Type?displayProperty=fullName>\), aux noms de groupes de méthodes \(par opposition aux méthodes spécifiques\) et aux accesseurs d'événements [add](../../../csharp/language-reference/keywords/add.md) et [remove](../../../csharp/language-reference/keywords/remove.md).  
  
 Chaque valeur possède un type associé.  Par exemple, si x et y sont tous deux des variables de type `int`, la valeur de l'expression `x + y` est également typée comme `int`.  Si la valeur est assignée à une variable d'un type différent, ou si x et y sont des types différents, les règles de conversion de type sont appliquées.  Pour plus d'informations sur le fonctionnement de ces conversions, consultez [Cast et conversions de types](../../../csharp/programming-guide/types/casting-and-type-conversions.md).  
  
## Dépassements de capacité  
 Les expressions numériques peuvent provoquer un dépassement de capacité si la valeur est supérieure à la valeur maximale du type de la valeur.  Pour plus d'informations, consultez [Checked et unchecked](../../../csharp/language-reference/keywords/checked-and-unchecked.md) et [Tableau des conversions numériques explicites](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md).  
  
## Priorité des opérateurs et associativité  
 La manière dont une expression est évaluée est régie par les règles d'associativité et de priorité des opérateurs.  Pour plus d'informations, consultez [Opérateurs](../../../csharp/programming-guide/statements-expressions-operators/operators.md).  
  
 La plupart des expressions, hormis les expressions d'assignation et les expressions d'appel de méthode, doivent être incorporées dans une instruction.  Pour plus d'informations, consultez [Instructions](../../../csharp/programming-guide/statements-expressions-operators/statements.md).  
  
## Littéraux et noms simples  
 Les deux types d'expressions les plus simples sont littéraux et noms simples.  Un littéral est une valeur constante qui n'a aucun nom.  Par exemple, dans l'exemple de code suivant, `5` et `"Hello World"` sont des valeurs littérales :  
  
 [!code-cs[csProgGuideStatements#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/expressions_1.cs)]  
  
 Pour plus d'informations sur les littéraux, consultez [Types](../../../csharp/language-reference/keywords/types.md).  
  
 Dans l'exemple précédent, `i` et `s` sont des noms simples qui identifient des variables locales.  Lorsque ces variables sont utilisées dans une expression, le nom de variable est évalué à la valeur stockée actuellement à l'emplacement de la variable en mémoire.  Ceci est démontré dans l'exemple suivant :  
  
 [!code-cs[csProgGuideStatements#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/expressions_2.cs)]  
  
## Expressions d'appel  
 Dans l'exemple de code suivant, l'appel à `DoWork` est une autre expression d'appel.  
  
```  
DoWork();  
```  
  
 Un appel de méthode nécessite le nom de la méthode, soit comme un nom comme dans l'exemple précédent, soit comme résultat d'une autre expression, suivi de parenthèses et des paramètres de méthode requis.  Pour plus d'informations, consultez [Méthodes](../../../csharp/programming-guide/classes-and-structs/methods.md).  Un appel de délégué utilise le nom d'un délégué et les paramètres de méthode entre parenthèses.  Pour plus d'informations, consultez [Délégués](../../../csharp/programming-guide/delegates/index.md).  Les appels de méthode et les appels de délégué prennent la valeur de retour de la méthode, si cette dernière retourne une valeur.  Les méthodes qui retournent void ne peuvent pas être utilisées à la place d'une valeur dans une expression.  
  
## Expressions de requête  
 Les règles pour les expressions en général s'appliquent aux expressions de requête.  Pour plus d'informations, consultez [Expressions de requête \(LINQ\)](../../../csharp/programming-guide/linq-query-expressions/index.md).  
  
## Expressions lambda  
 Les expressions lambda représentent des « méthodes inline » qui n'ont aucun nom mais peuvent avoir des paramètres d'entrée et plusieurs instructions.  Elles sont largement utilisées dans LINQ pour passer des arguments aux méthodes.  Les expressions lambda sont compilées en délégués ou en arborescences d'expression selon le contexte dans lequel elles sont utilisées.  Pour plus d'informations, consultez [Expressions lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).  
  
## Arborescences d'expression  
 Les arborescences d'expression permettent aux expressions d'être représentées sous forme de structures de données.  Elles sont largement utilisées par les fournisseurs LINQ pour traduire les expressions de requête en code explicite dans quelque autre contexte, comme une base de données SQL.  Pour plus d'informations, consultez [Arborescences d'expression](../Topic/Expression%20Trees%20\(C%23%20and%20Visual%20Basic\).md).  
  
## Notes  
 Chaque fois qu'une variable, un accès à une propriété ou à un indexeur d'objet est identifié dans une expression, la valeur de cet élément est utilisée comme valeur de l'expression.  En C\#, une expression peut être placée partout où une valeur ou un objet est requis, tant que l'expression a, au bout du compte, la valeur du type requis.  
  
## Chapitre proposé  
 [Variables and Expressions](http://go.microsoft.com/fwlink/?LinkId=221228) dans [Beginning Visual C\# 2010](http://go.microsoft.com/fwlink/?LinkId=221214)  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Méthodes](../../../csharp/programming-guide/classes-and-structs/methods.md)   
 [Délégués](../../../csharp/programming-guide/delegates/index.md)   
 [Opérateurs](../../../csharp/programming-guide/statements-expressions-operators/operators.md)   
 [Types](../../../csharp/programming-guide/types/index.md)   
 [Expressions de requête \(LINQ\)](../../../csharp/programming-guide/linq-query-expressions/index.md)