---
title: "Fonctions anonymes (Guide de programmation&#160;C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "fonctions anonymes (C#)"
  - "méthodes anonymes (C#)"
  - "expressions lambda (C#), en tant que fonctions anonymes"
ms.assetid: 6ce3f04d-0c71-4728-9127-634c7e9a8365
caps.latest.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 14
---
# Fonctions anonymes (Guide de programmation&#160;C#)
Une fonction anonyme est une instruction ou expression "inline" qui peut être utilisée partout où un type délégué est attendu.  Vous pouvez l'utiliser pour initialiser un délégué nommé ou la passer à la place d'un type délégué nommé en tant que paramètre de méthode.  
  
 Il existe deux types de fonctions anonymes, qui sont décrits dans les rubriques suivantes :  
  
-   [Expressions lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).  
  
-   [Méthodes anonymes](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)  
  
    > [!NOTE]
    >  Les expressions lambda peuvent être liées aux arborescences d'expression et également aux délégués.  
  
## L'évolution de délégués en C\#  
 Dans C\# 1.0, vous avez créé une instance d'un délégué en l'initialisant explicitement avec une méthode définie à un autre endroit dans le code.  C\# 2.0 a introduit le concept de méthodes anonymes comme moyen d'écrire des blocs d'instructions inline sans nom qui peuvent être exécutés dans un appel de délégué.  C\# 3.0 a introduit des expressions lambda, qui sont semblables du point de vue du concept aux méthodes anonymes, mais plus expressives et concises.  Ces deux fonctionnalités sont désignées collectivement comme des *fonctions anonymes*.  En général, les applications qui ciblent la version 3.5 et les versions ultérieures de [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] doivent utiliser des expressions lambda.  
  
 L'exemple suivant montre l'évolution de la création de délégué de C\# 1.0 à C\# 3.0 :  
  
 [!code-cs[csProgGuideLINQ#65](../../../csharp/programming-guide/arrays/codesnippet/csharp/csLINQProgRef/csRef30LangFeatures_2.cs#65)]  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## Voir aussi  
 [Instructions, expressions et opérateurs](../../../csharp/programming-guide/statements-expressions-operators/index.md)   
 [Expressions lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)   
 [Délégués](../../../csharp/programming-guide/delegates/index.md)   
 [Arborescences d'expression](../Topic/Expression%20Trees%20\(C%23%20and%20Visual%20Basic\).md)