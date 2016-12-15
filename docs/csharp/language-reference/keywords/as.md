---
title: "as (r&#233;f&#233;rence C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "as_CSharpKeyword"
  - "as"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "as (mot clé C#)"
  - "conversion de type (C#), as (mot clé)"
ms.assetid: a9be126b-cbf4-4990-a70d-d0e1983cad0e
caps.latest.revision: 24
caps.handback.revision: 24
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# as (r&#233;f&#233;rence C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Vous pouvez utiliser l'opérateur d' `as` pour exécuter certains types de conversions entre des types référence compatibles ou l' [types Nullable](../../../csharp/programming-guide/nullable-types/index.md).  Le code suivant est fourni à titre d'exemple.  
  
 [!code-cs[csrefKeywordsOperator#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/as_1.cs)]  
  
## Notes  
 L'opérateur `as` est semblable à une opération de cast.  Toutefois, si la conversion n'est pas possible, `as` retourne `null` au lieu de lever une exception.  Prenons l'exemple suivant :  
  
```  
expression as type  
```  
  
 Le code équivaut à l'expression suivante sauf que la variable d' `expression` est évaluée qu'une seule fois.  
  
```  
expression is type ? (type)expression : (type)null  
```  
  
 Notez que l'opérateur d' `as` exécute uniquement des conversions de référence, des conversions nullables, et les conversions boxings.  L'opérateur d' `as` ne peut pas exécuter d'autres conversions, telles que les conversions définies par l'utilisateur, qui doivent plutôt être exécutées à l'aide de expressions de cast.  
  
## Exemple  
 [!code-cs[csrefKeywordsOperator#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/as_2.cs)]  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Mots clés C\#](../../../csharp/language-reference/keywords/index.md)   
 [is](../../../csharp/language-reference/keywords/is.md)   
 [?:, opérateur](../../../csharp/language-reference/operators/conditional-operator.md)   
 [Mots clés des opérateurs](../../../csharp/language-reference/keywords/operator-keywords.md)