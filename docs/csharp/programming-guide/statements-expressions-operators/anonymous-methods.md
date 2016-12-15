---
title: "M&#233;thodes anonymes (Guide de programmation C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "méthodes anonymes (C#)"
  - "délégués (C#), méthodes anonymes"
  - "méthodes (C#), anonymes"
ms.assetid: a62441fa-f0a3-4acb-9aa6-93762a635275
caps.latest.revision: 31
caps.handback.revision: 31
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# M&#233;thodes anonymes (Guide de programmation C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Dans les versions de C\# antérieures à 2.0, la seule façon de déclarer un [délégué](../../../csharp/language-reference/keywords/delegate.md) consistait à utiliser des [méthodes nommées](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md).  C\# 2.0 a introduit les méthodes anonymes et dans C\# 3.0 et les versions ultérieures, les expressions lambda remplacent des méthodes anonymes comme manière privilégiée d'écrire du code incorporé.  Toutefois, les informations à propos des méthodes anonymes dans cette rubrique s'appliquent également aux expressions lambda.  Il existe un cas dans lequel une méthode anonyme fournit des fonctionnalités introuvables dans les expressions lambda.  Les méthodes anonymes vous permettent d'omettre la liste de paramètres.  Cela signifie qu'une méthode anonyme peut être convertie en délégués avec diverses signatures.  Ceci est impossible avec les expressions lambda.  Pour plus d'informations spécifiques aux expressions lambda, consultez [Expressions lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).  
  
 La création de méthodes anonymes est essentiellement un moyen de passer un bloc de code en paramètre de délégué.  En voici deux exemples :  
  
 [!code-cs[csProgGuideDelegates#6](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_1.cs)]  
  
 [!code-cs[csProgGuideDelegates#5](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_2.cs)]  
  
 En utilisant des méthodes anonymes, vous réduisez la charge de travail liée au codage de l'instanciation de délégués, car vous n'avez pas à créer de méthode distincte.  
  
 Par exemple, la spécification d'un bloc de code au lieu d'un délégué peut être utile dans une situation où le travail nécessité par la création d'une méthode ne semble pas justifié.  Un bon exemple pourrait être le moment où vous démarrez un nouveau thread.  Cette classe crée un thread et contient également le code exécuté par le thread sans créer une méthode supplémentaire pour le délégué.  
  
 [!code-cs[csProgGuideDelegates#7](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_3.cs)]  
  
## Notes  
 La portée des paramètres d'une méthode anonyme est *anonymous\-method\-block*.  
  
 C'est une erreur d'avoir une instruction de saut, telle que [goto](../../../csharp/language-reference/keywords/goto.md), [break](../../../csharp/language-reference/keywords/break.md) ou [continue](../../../csharp/language-reference/keywords/continue.md), à l'intérieur du bloc de méthode anonyme si la cible est à l'extérieur du bloc.  C'est également une erreur d'avoir une instruction de saut, telle que `goto`, `break` ou `continue`, à l'extérieur du bloc de méthode anonyme si la cible est à l'intérieur du bloc.  
  
 Les variables locales et les paramètres dont la portée contient une déclaration de méthode anonyme sont appelés des variables *externes* de la méthode anonyme.  Par exemple, dans le segment de code suivant, `n` est une variable externe :  
  
 [!code-cs[csProgGuideDelegates#8](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_4.cs)]  
  
 Une référence à la variable externe `n` parle  *capturées* lorsque le délégué est créé.  Contrairement aux variables locales, la durée de vie d'une variable capturée s'étend jusqu'à ce que les délégués qui font référence aux méthodes anonymes soient éligibles pour le garbage collection.  
  
 Une méthode anonyme ne peut pas accéder aux paramètres [ref](../../../csharp/language-reference/keywords/ref.md) ou [out](../../../csharp/language-reference/keywords/out.md) d'une portée externe.  
  
 Aucun code unsafe n'est accessible dans *anonymous\-method\-block*.  
  
 Les méthodes anonymes ne sont pas autorisées à gauche de l'opérateur [is](../../../csharp/language-reference/keywords/is.md).  
  
## Exemple  
 L'exemple suivant illustre deux manières d'instancier un délégué :  
  
-   Associer le délégué à une méthode anonyme.  
  
-   Associer le délégué à une méthode nommée \(`DoWork`\).  
  
 Dans chaque cas, un message est affiché lorsque le délégué est appelé.  
  
 [!code-cs[csProgGuideDelegates#4](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_5.cs)]  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Délégués](../../../csharp/programming-guide/delegates/index.md)   
 [Expressions lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)   
 [Pointeurs et code unsafe](../../../csharp/programming-guide/unsafe-code-pointers/index.md)   
 [Méthodes](../../../csharp/programming-guide/classes-and-structs/methods.md)   
 [Délégués avec méthodes nommées et méthodes anonymes](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md)