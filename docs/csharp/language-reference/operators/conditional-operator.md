---
title: "?:, opérateur (référence C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ?:_CSharpKeyword
- ?_CSharpKeyword
- :_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- '?: operator [C#]'
- conditional operator (?:) [C#]
ms.assetid: e83a17f1-7500-48ba-8bee-2fbc4c847af4
caps.latest.revision: 23
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 3e60516d1f443528c357eb12612b6149f34c1f7e
ms.contentlocale: fr-fr
ms.lasthandoff: 05/22/2017

---
# <a name="-operator-c-reference"></a>?:, opérateur (référence C#)
L'opérateur conditionnel (`?:`) retourne l'une de deux valeurs selon la valeur d'une expression booléenne. Voici la syntaxe de l'opérateur conditionnel.  
  
```  
condition ? first_expression : second_expression;  
```  
  
## <a name="remarks"></a>Remarques  
 La `condition` est évaluée entre `true` ou `false`. Si `condition` est `true`, `first_expression` est évaluée et devient le résultat. Si `condition` est `false`, `second_expression` est évaluée et devient le résultat. Seule une des deux expressions peut être évaluée.  
  
 Soit le type de `first_expression` et `second_expression` doivent être identiques, soit une conversion implicite doit exister d'un type à un autre.  
  
 Vous pouvez exprimer des calculs qui pourraient sinon requérir une construction `if-else` plus concise en utilisant l'opérateur conditionnel. Par exemple, le code suivant utilise en premier lieu une instruction `if`, puis un opérateur conditionnel pour classifier un entier positif ou négatif.  
  
```  
int input = Convert.ToInt32(Console.ReadLine());  
string classify;  
  
// if-else construction.  
if (input > 0)  
    classify = "positive";  
else  
    classify = "negative";  
  
// ?: conditional operator.  
classify = (input > 0) ? "positive" : "negative";  
```  
  
 L'opérateur conditionnel est associatif sur sa droite. L'expression `a ? b : c ? d : e` est évaluée comme `a ? b : (c ? d : e)`, et non pas sous la forme `(a ? b : c) ? d : e`.  
  
 L'opérateur conditionnel ne peut pas être surchargé.  
  
## <a name="example"></a>Exemple  
 [!code-cs[csRefOperators#41](../../../csharp/language-reference/operators/codesnippet/CSharp/conditional-operator_1.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur C#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Opérateurs C#](../../../csharp/language-reference/operators/index.md)   
 [if-else](../../../csharp/language-reference/keywords/if-else.md)   
 [Opérateurs ?. et ?](../../../csharp/language-reference/operators/null-conditional-operators.md)   
 [?? Opérateur](../../../csharp/language-reference/operators/null-conditional-operator.md)

