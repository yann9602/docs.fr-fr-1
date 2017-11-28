---
title: "Comment : utiliser des tableaux et des variables locales implicitement typés dans une expression de requête (Guide de programmation C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: implicitly-typed local variables [C#], how to use
ms.assetid: 6b7354d2-af79-427a-b6a8-f74eb8fd0b91
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 754698fc423fb2dfc9bf50ed15be610831cefeda
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression-c-programming-guide"></a>Comment : utiliser des tableaux et des variables locales implicitement typés dans une expression de requête (Guide de programmation C#)
Vous pouvez utiliser des variables locales implicitement typées chaque fois que vous voulez que le compilateur détermine le type d’une variable locale. Vous devez utiliser des variables locales implicitement typées pour stocker des types anonymes, qui sont souvent utilisés dans les expressions de requête. Les exemples suivants illustrent des utilisations facultatives et obligatoires de variables locales implicitement typées dans des requêtes.  
  
 Les variables locales implicitement typées sont déclarées à l’aide du mot clé contextuel [var](../../../csharp/language-reference/keywords/var.md). Pour plus d’informations, consultez [Variables locales implicitement typées](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md) et [Tableaux implicitement typés](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre un scénario courant dans lequel le mot clé `var` est obligatoire : une expression de requête qui produit une séquence de types anonymes. Dans ce scénario, la variable de requête et la variable d’itération figurant dans l’instruction `foreach` doivent être implicitement typées avec `var`, car vous n’avez pas accès à un nom de type pour le type anonyme. Pour plus d’informations sur les types anonymes, consultez [Types anonymes](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).  
  
 [!code-csharp[csProgGuideLINQ#32](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression_1.cs)]  
  
## <a name="example"></a>Exemple  
 Dans l’exemple suivant, le mot clé `var` est utilisé dans un cas similaire, à la différence que l’utilisation de `var` est facultative. Comme `student.LastName` est une chaîne, l’exécution de la requête retourne une séquence de chaînes. De ce fait, le type de `queryID` pourrait être déclaré en tant que `System.Collections.Generic.IEnumerable<string>` au lieu de `var`. Le mot clé `var` est utilisé pour des raisons pratiques. Dans l’exemple, la variable d’itération figurant dans l’instruction `foreach` est explicitement typée en tant que chaîne, mais elle aurait pu être déclarée à l’aide de `var`. Comme le type de la variable d’itération n’est pas un type anonyme, l’utilisation de `var` est facultative et non obligatoire. Pour rappel, `var` n’est pas en soi un type, mais une instruction indiquant au compilateur de déduire et d’assigner le type.  
  
 [!code-csharp[csProgGuideLINQ#33](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression_2.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [Méthodes d’extension](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)  
 [LINQ (Language Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)  
 [var](../../../csharp/language-reference/keywords/var.md)  
 [Expressions de requête LINQ](../../../csharp/programming-guide/linq-query-expressions/index.md)
