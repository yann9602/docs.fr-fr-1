---
title: "Expressions (Guide de programmation C#) | Microsoft Docs"
ms.date: 2017-05-11
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- expressions [C#]
- C# language, expressions
ms.assetid: c7d8feb0-0e58-4f94-8bf6-4d070550a832
caps.latest.revision: 22
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
ms.sourcegitcommit: a5ed524a1b17f7be8903f998cbd732594faab831
ms.openlocfilehash: 79efbca3d8d0b32c83dc3909e0a33839ecc0ef3e
ms.contentlocale: fr-fr
ms.lasthandoff: 05/22/2017

---
# <a name="expressions-c-programming-guide"></a>Expressions (Guide de programmation C#)
Une *expression* est une séquence d’un ou plusieurs opérandes et de zéro, un ou plusieurs opérateurs qui peuvent être évalués à une valeur, un objet, une méthode ou un espace de noms unique. Elle peut être constituée d’une valeur littérale, d’un appel de méthode, d’un opérateur et de ses opérandes, ou d’un *nom simple*. Un nom simple peut être le nom d'une variable, d'un membre de type, d'un paramètre de méthode, d'un espace de noms ou d'un type.  
  
 Les expressions peuvent utiliser des opérateurs qui à leur tour utilisent d’autres expressions en tant que paramètres, ou des appels de méthode dont les paramètres sont à leur tour d’autres appels de méthode. Leur complexité est donc très variable. Voici deux exemples d’expressions :  
  
```csharp  
((x < 10) && ( x > 5)) || ((x > 20) && (x < 25));
   
System.Convert.ToInt32("35");  
```  
  
## <a name="expression-values"></a>Valeurs d’expressions  
 Dans la plupart des contextes dans lesquels les expressions sont utilisées, par exemple dans les instructions ou les paramètres de méthode, l’expression est supposée correspondre à une valeur. Si x et y sont des entiers, l’expression `x + y` correspond à une valeur numérique. L’expression `new MyClass()` correspond à une référence à une nouvelle instance d’un objet `MyClass`. L’expression `myClass.ToString()` correspond à une chaîne, car c’est le type de retour de la méthode. Toutefois, même si un espace de noms est considéré comme une expression, il ne correspond pas à une valeur et ne peut donc jamais être le résultat final d’une expression. Vous ne pouvez pas passer un nom d’espace de noms à un paramètre de méthode, ni l’utiliser dans une nouvelle expression ou l’affecter à une variable. Vous pouvez l’utiliser uniquement en tant que sous-expression dans une expression plus longue. Il en va de même pour les types (par opposition aux objets <xref:System.Type?displayProperty=fullName>), aux noms de groupes de méthodes (par opposition aux méthodes spécifiques) et aux accesseurs d’événements [add](../../../csharp/language-reference/keywords/add.md) et [remove](../../../csharp/language-reference/keywords/remove.md).  
  
 Chaque valeur possède un type associé. Par exemple, si x et y sont toutes deux des variables de type `int`, la valeur de l’expression `x + y` est également de type `int`. Si la valeur est assignée à une variable d’un type différent, ou si x et y sont des types différents, les règles de conversion de type sont appliquées. Pour plus d’informations sur le fonctionnement de ces conversions, consultez [Cast et conversions de types](../../../csharp/programming-guide/types/casting-and-type-conversions.md).  
  
## <a name="overflows"></a>Dépassements de capacité  
 Les expressions numériques peuvent provoquer des dépassements de capacité si la valeur est supérieure à la valeur maximale du type de la valeur. Pour plus d’informations, consultez [Checked et Unchecked](../../../csharp/language-reference/keywords/checked-and-unchecked.md) et [Tableau des conversions numériques explicites](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md).  
  
## <a name="operator-precedence-and-associativity"></a>Priorité des opérateurs et associativité  
 Le mode d’évaluation de l’expression est régi par les règles de priorité des opérateurs et d’associativité. Pour plus d’informations, consultez [Opérateurs](../../../csharp/programming-guide/statements-expressions-operators/operators.md).  
  
 La plupart des expressions, sauf les expressions d’assignation et les expressions d’appel de méthode, doivent être incorporées dans une instruction. Pour plus d’informations, consultez [Instructions](../../../csharp/programming-guide/statements-expressions-operators/statements.md).  
  
## <a name="literals-and-simple-names"></a>Littéraux et noms simples  
 Les deux types d’expressions les plus simples sont les littéraux et les noms simples. Un littéral est une valeur constante qui n’a aucun nom. Par exemple, dans l’exemple de code suivant, `5` et `"Hello World"` sont des valeurs littérales :  
  
 [!code-cs[csProgGuideStatements#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/expressions_1.cs)]  
  
 Pour plus d’informations sur les littéraux, consultez [Types](../../../csharp/language-reference/keywords/types.md).  
  
 Dans l’exemple précédent, `i` et `s` sont des noms simples qui identifient des variables locales. Quand ces variables sont utilisées dans une expression, le nom de la variable prend la valeur qui est stockée actuellement à l’emplacement de la variable en mémoire. Ceci est illustré dans l'exemple suivant :  
  
 [!code-cs[csProgGuideStatements#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/expressions_2.cs)]  
## <a name="invocation-expressions"></a>Appel d’expressions  
 Dans l’exemple de code suivant, l’appel à `DoWork` est une expression d’appel.  
  
```csharp
DoWork();  
```  
  
 Un appel de méthode nécessite le nom de la méthode, soit comme nom (comme dans l’exemple précédent), soit comme le résultat d’une autre expression, suivi de parenthèses et des éventuels paramètres de méthode. Pour plus d’informations, consultez [Méthodes](../../../csharp/programming-guide/classes-and-structs/methods.md). Un appel de délégué utilise le nom d’un délégué et des paramètres de méthode entre parenthèses. Pour plus d’informations, consultez [Délégués](../../../csharp/programming-guide/delegates/index.md). Les appels de méthode et les appels de délégué sont évalués à la valeur de retour de la méthode, si celle-ci retourne une valeur. Les méthodes qui retournent void ne peuvent pas être utilisées à la place d’une valeur dans une expression.  

## <a name="query-expressions"></a>Expressions de requête  
 Les mêmes règles relatives aux expressions s’appliquent en général aux expressions de requête. Pour plus d’informations, consultez [Expressions de requête LINQ](../../../csharp/programming-guide/linq-query-expressions/index.md).  
  
## <a name="lambda-expressions"></a>Expressions lambda  
 Les expressions lambda représentent des « méthodes inline » qui n’ont aucun nom mais qui peuvent avoir des paramètres d’entrée et plusieurs instructions. Elles sont largement utilisées dans LINQ pour passer des arguments aux méthodes. Les expressions lambda sont compilées en délégués ou en arborescences de l’expression en fonction du contexte dans lequel elles sont utilisées. Pour plus d’informations, consultez [Expressions lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).  
  
## <a name="expression-trees"></a>Arborescences de l’expression  
 Les arborescences de l’expression permettent de représenter des expressions en tant que structures de données. Elles sont largement utilisées par les fournisseurs LINQ pour traduire des expressions de requête en code explicite dans un autre contexte, comme une base de données SQL. Pour plus d’informations, consultez [Arborescences de l’expression](http://msdn.microsoft.com/library/fb1d3ed8-d5b0-4211-a71f-dd271529294b).  
  
## <a name="expression-body-definitions"></a>Définitions de corps d’expression

C# prend en charge les *membres expression-bodied*, qui vous permettent de fournir une définition de corps d’expression concise pour des méthodes, des constructeurs, des finaliseurs, des propriétés et des indexeurs. Pour plus d’informations, consultez [Membres expression-bodied](expression-bodied-members.md).

## <a name="remarks"></a>Remarques  
 Chaque fois qu’un accès à un indexeur d’objet, une variable ou une propriété d’objet est identifié à partir d’une expression, la valeur de cet élément est utilisée comme valeur de l’expression. Une expression peut être placée n’importe où en C# où une valeur ou un objet est obligatoire, tant que l’expression correspond finalement au type obligatoire.  

## <a name="see-also"></a>Voir aussi  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Méthodes](../../../csharp/programming-guide/classes-and-structs/methods.md)   
 [Délégués](../../../csharp/programming-guide/delegates/index.md)   
 [Opérateurs](../../../csharp/programming-guide/statements-expressions-operators/operators.md)   
 [Types](../../../csharp/programming-guide/types/index.md)   
 [Expressions de requête LINQ](../../../csharp/programming-guide/linq-query-expressions/index.md)
