---
title: "as (référence C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- as_CSharpKeyword
- as
helpviewer_keywords:
- type conversion [C#], as keyword
- as keyword [C#]
ms.assetid: a9be126b-cbf4-4990-a70d-d0e1983cad0e
caps.latest.revision: "24"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a4f2964f32a4139ffeb6d51b761f1176a57c5be6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="as-c-reference"></a>as (référence C#)
Vous pouvez utiliser l’opérateur `as` pour effectuer certains types de conversions entre des types référence ou des [types Nullable](../../../csharp/programming-guide/nullable-types/index.md) compatibles. Le code suivant fournit un exemple.  
  
 [!code-csharp[csrefKeywordsOperator#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/as_1.cs)]  
  
## <a name="remarks"></a>Remarques  
 L’opérateur `as` est semblable à une opération de cast. Toutefois, si la conversion n’est pas possible, `as` retourne `null` au lieu de lever une exception. Prenons l'exemple suivant :  
  
```  
expression as type  
```  
  
 Le code est équivalent à l’expression suivante, à la différence que la variable `expression` n’est évaluée qu’une seule fois.  
  
```  
expression is type ? (type)expression : (type)null  
```  
  
 Notez que l’opérateur `as` effectue uniquement des conversions de référence, des conversions Nullable et des conversions boxing. L’opérateur `as` ne peut pas effectuer d’autres conversions, telles que les conversions définies par l’utilisateur, qui doivent être effectuées à l’aide d’expressions cast.  
  
## <a name="example"></a>Exemple  
 [!code-csharp[csrefKeywordsOperator#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/as_2.cs)]  
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Référence C#](../../../csharp/language-reference/index.md)  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [Mots clés C#](../../../csharp/language-reference/keywords/index.md)  
 [is](../../../csharp/language-reference/keywords/is.md)  
 [?, opérateur](../../../csharp/language-reference/operators/conditional-operator.md)  
 [Mots clés des opérateurs](../../../csharp/language-reference/keywords/operator-keywords.md)
