---
title: "delegate (r&#233;f&#233;rence C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "delegate_CSharpKeyword"
  - "delegate"
  - "CS0123"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "delegate (mot clé C#)"
  - "pointeurs fonction (C#)"
ms.assetid: 0bb8cb6d-2f87-47c7-9d1f-d65c1cd01e9f
caps.latest.revision: 24
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 24
---
# delegate (r&#233;f&#233;rence C#)
La déclaration d'un type délégué est semblable à une signature de méthode.  Elle présente une valeur de retour et n'importe quel nombre de paramètres de tout type :  
  
```  
public delegate void TestDelegate(string message);  
public delegate int TestDelegate(MyType m, long num);  
```  
  
 Un `delegate` est un type référence qui peut être utilisé pour encapsuler une méthode nommée ou anonyme.  Les délégués sont comparables aux pointeurs fonction en C\+\+, mais ils offrent l'avantage d'être sécurisés et de garantir le type \(sécurisés au niveau du type\).  Pour les applications de délégués, consultez [Délégués](../../../csharp/programming-guide/delegates/index.md) et [Délégués génériques](../../../csharp/programming-guide/generics/generic-delegates.md).  
  
## Notes  
 Les délégués sont la base des [Événements](../../../csharp/programming-guide/events/index.md).  
  
 Un délégué peut être instancié en l'associant à une méthode nommée ou à une méthode anonyme.  Pour plus d'informations, consultez [Méthodes nommées](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md) et [Méthodes anonymes](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md).  
  
 Le délégué doit être instancié avec une méthode ou une expression lambda qui présente un type de retour compatible et des paramètres d'entrée.  Pour plus d'informations sur le degré de variance qui est autorisé dans la signature de méthode, consultez [Variance dans les délégués](../Topic/Variance%20in%20Delegates%20\(C%23%20and%20Visual%20Basic\).md).  Pour son utilisation avec des méthodes anonymes, le délégué et le code à lui associer sont déclarés ensemble.  Les deux manières d'instancier un délégué sont présentées dans cette section.  
  
## Exemple  
 [!code-cs[csrefKeywordsTypes#8](../../../csharp/language-reference/keywords/codesnippet/csharp/delegate_1.cs)]  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Mots clés C\#](../../../csharp/language-reference/keywords/index.md)   
 [Types référence](../../../csharp/language-reference/keywords/reference-types.md)   
 [Délégués](../../../csharp/programming-guide/delegates/index.md)   
 [Événements](../../../csharp/programming-guide/events/index.md)   
 [Délégués avec méthodes nommées et méthodes anonymes](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md)   
 [Méthodes anonymes](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)