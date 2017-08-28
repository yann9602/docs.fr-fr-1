---
title: "let, clause (Référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- let_CSharpKeyword
- let
dev_langs:
- CSharp
helpviewer_keywords:
- let keyword [C#]
- let clause [C#]
ms.assetid: 13c9c1a4-ce57-48ef-8e1b-4c2a59b99fb4
caps.latest.revision: 15
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 37ec0cb0c8c374a0b5250d82e880c96696b5584a
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="let-clause-c-reference"></a>let, clause (Référence C#)
Dans une expression de requête, il est parfois utile de stocker le résultat d’une sous-expression pour pouvoir l’utiliser dans des clauses ultérieures. Pour cela, vous pouvez utiliser le mot clé `let`, qui crée une variable de portée et l’initialise avec le résultat de l’expression que vous fournissez. Une fois initialisée avec une valeur, la variable de portée ne peut pas être utilisée pour stocker une autre valeur. Cependant, si la variable de portée contient un type requêtable, elle peut être interrogée.  
  
## <a name="example"></a>Exemple  
 Dans l’exemple suivant, la clause `let` est utilisée de deux façons différentes :  
  
1.  Pour créer un type énumérable qui peut lui-même être interrogé.  
  
2.  Pour permettre à la requête d’appeler `ToLower` une seule fois sur la variable de portée `word`. Si vous n’utilisez pas `let`, vous devez appeler `ToLower` dans chaque prédicat de la clause `where`.  
  
 [!code-cs[cscsrefQueryKeywords#28](../../../csharp/language-reference/keywords/codesnippet/CSharp/let-clause_1.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur C#](../../../csharp/language-reference/index.md)   
 [Mots clés de requête (LINQ)](../../../csharp/language-reference/keywords/query-keywords.md)   
 [Expressions de requête LINQ](../../../csharp/programming-guide/linq-query-expressions/index.md)   
 [Bien démarrer avec LINQ en C#](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)   
 [Guide pratique pour gérer des exceptions dans des expressions de requête](../../../csharp/programming-guide/linq-query-expressions/how-to-handle-exceptions-in-query-expressions.md)

