---
title: "let, clause (Référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- let_CSharpKeyword
- let
helpviewer_keywords:
- let keyword [C#]
- let clause [C#]
ms.assetid: 13c9c1a4-ce57-48ef-8e1b-4c2a59b99fb4
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 077c5178946b85d0fb85aa8da94966e4c5821736
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="let-clause-c-reference"></a>let, clause (Référence C#)
Dans une expression de requête, il est parfois utile de stocker le résultat d’une sous-expression pour pouvoir l’utiliser dans des clauses ultérieures. Pour cela, vous pouvez utiliser le mot clé `let`, qui crée une variable de portée et l’initialise avec le résultat de l’expression que vous fournissez. Une fois initialisée avec une valeur, la variable de portée ne peut pas être utilisée pour stocker une autre valeur. Cependant, si la variable de portée contient un type requêtable, elle peut être interrogée.  
  
## <a name="example"></a>Exemple  
 Dans l’exemple suivant, la clause `let` est utilisée de deux façons différentes :  
  
1.  Pour créer un type énumérable qui peut être interrogé.  
  
2.  Pour activer la requête doit appeler `ToLower` qu’une seule fois sur la variable de portée `word`. Sans utiliser de `let`, vous devez appeler `ToLower` dans chaque prédicat de la `where` clause.  
  
 [!code-csharp[cscsrefQueryKeywords#28](../../../csharp/language-reference/keywords/codesnippet/CSharp/let-clause_1.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 [Référence C#](../../../csharp/language-reference/index.md)  
 [Mots clés de requête (LINQ)](../../../csharp/language-reference/keywords/query-keywords.md)  
 [Expressions de requête LINQ](../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [Bien démarrer avec LINQ en C#](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)  
 [Comment : gérer des exceptions dans des expressions de requête](../../../csharp/programming-guide/linq-query-expressions/how-to-handle-exceptions-in-query-expressions.md)
