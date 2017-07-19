---
title: "as (référence C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- as_CSharpKeyword
- as
dev_langs:
- CSharp
helpviewer_keywords:
- type conversion [C#], as keyword
- as keyword [C#]
ms.assetid: a9be126b-cbf4-4990-a70d-d0e1983cad0e
caps.latest.revision: 24
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
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 6c284f288df11e2ac32b7c27f914e3f699bd78f0
ms.contentlocale: fr-fr
ms.lasthandoff: 03/13/2017

---
# <a name="as-c-reference"></a>as (référence C#)
Vous pouvez utiliser l’opérateur `as` pour effectuer certains types de conversions entre des types référence ou des [types Nullable](../../../csharp/programming-guide/nullable-types/index.md) compatibles. Le code suivant fournit un exemple.  
  
 [!code-cs[csrefKeywordsOperator#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/as_1.cs)]  
  
## <a name="remarks"></a>Notes  
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
 [!code-cs[csrefKeywordsOperator#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/as_2.cs)]  
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur C#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Mots clés C#](../../../csharp/language-reference/keywords/index.md)   
 [is](../../../csharp/language-reference/keywords/is.md)   
 [?, opérateur](../../../csharp/language-reference/operators/conditional-operator.md)   
 [Mots clés des opérateurs](../../../csharp/language-reference/keywords/operator-keywords.md)
