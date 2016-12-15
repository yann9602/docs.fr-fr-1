---
title: "D&#233;l&#233;gu&#233;s avec m&#233;thodes nomm&#233;es et m&#233;thodes anonymes (Guide de programmation&#160;C#) | Microsoft Docs"
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
  - "délégués (C#), avec méthodes nommées et méthodes anonymes"
  - "méthodes (C#), dans les délégués"
ms.assetid: 98fa8c61-66b6-4146-986c-3236c4045733
caps.latest.revision: 18
caps.handback.revision: 18
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# D&#233;l&#233;gu&#233;s avec m&#233;thodes nomm&#233;es et m&#233;thodes anonymes (Guide de programmation&#160;C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Un [délégué](../../../csharp/language-reference/keywords/delegate.md) peut être associé à une méthode nommée.  Lorsque vous instanciez un délégué à l'aide d'une méthode nommée, la méthode est passée en paramètre, par exemple :  
  
 [!code-cs[csProgGuideDelegates#1](../../../csharp/programming-guide/delegates/codesnippet/CSharp/delegates-with-named-vs-anonymous-methods_1.cs)]  
  
 C'est ce que l'on appelle utiliser une méthode nommée.  Les délégués construits avec une méthode nommée peuvent encapsuler une méthode [statique](../../../csharp/language-reference/keywords/static.md) ou une méthode d'instance.  Les méthodes nommées sont la seule méthode pour instancier un délégué dans les versions précédentes de C\#.  Toutefois, dans une situation où la création d'une nouvelle méthode constitue une charge de travail non souhaitée, C\# vous permet d'instancier un délégué et de spécifier immédiatement un bloc de code que le délégué traitera lorsqu'il sera appelé.  Le bloc peut contenir une expression lambda ou une méthode anonyme.  Pour plus d'informations, consultez [Fonctions anonymes](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md).  
  
## Notes  
 La méthode que vous passez en tant que paramètre de délégué doit avoir la même signature que la déclaration du délégué.  
  
 Une instance de délégué encapsule soit une méthode statique soit une méthode d'instance.  
  
 Même si le délégué peut utiliser un paramètre de [sortie](../../../csharp/language-reference/keywords/out.md), nous ne recommandons pas son utilisation avec les délégués d'événement multicast, car vous ne pouvez pas savoir quel délégué sera appelé.  
  
## Exemple 1  
 L'exemple suivant est un exemple simple de déclaration et d'utilisation d'un délégué.  Notez que le délégué, `Del`, et la méthode associée, `MultiplyNumbers`, ont la même signature  
  
 [!code-cs[csProgGuideDelegates#2](../../../csharp/programming-guide/delegates/codesnippet/CSharp/delegates-with-named-vs-anonymous-methods_2.cs)]  
  
## Exemple 2  
 Dans l'exemple suivant, un délégué est associé à une méthode statique et à une méthode d'instance, et ces méthodes retournent chacune des informations spécifiques.  
  
 [!code-cs[csProgGuideDelegates#3](../../../csharp/programming-guide/delegates/codesnippet/CSharp/delegates-with-named-vs-anonymous-methods_3.cs)]  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Délégués](../../../csharp/programming-guide/delegates/index.md)   
 [Méthodes anonymes](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)   
 [Comment : combiner des délégués \(délégués multicast\)](../../../csharp/programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md)   
 [Événements](../../../csharp/programming-guide/events/index.md)