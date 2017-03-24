---
title: "using, instruction (r&#233;f&#233;rence C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "using (instruction C#)"
ms.assetid: afc355e6-f0b9-4240-94dd-0d93f17d9fc3
caps.latest.revision: 31
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 31
---
# using, instruction (r&#233;f&#233;rence C#)
Fournit une syntaxe qui garantit l'utilisation correcte d'objets <xref:System.IDisposable>.  
  
## Exemple  
 L'exemple suivant montre comment utiliser l'instruction using.  
  
 [!code-cs[csrefKeywordsNamespace#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_1.cs)]  
  
## Notes  
 <xref:System.IO.File> et <xref:System.Drawing.Font> sont des exemples des types managés qui accèdent aux ressources non managées \(dans ce cas, des handles de fichiers et des contextes de périphérique\).  Beaucoup d'autres types de ressources non managées et de bibliothèques de classes peuvent les encapsuler.  Tous doivent implémenter l'interface <xref:System.IDisposable>.  
  
 En règle générale, lorsque vous utilisez un objet `IDisposable`, vous devez le déclarer et l'instancier dans une instruction `using`.  L'instruction `using` appelle la méthode <xref:System.IDisposable.Dispose%2A> sur l'objet et, si vous l'utilisez comme indiqué précédemment, met l'objet hors de portée dès que <xref:System.IDisposable.Dispose%2A> est appelé.  Dans le bloc `using`, l'objet est en lecture seule et ne peut être ni modifié ni réassigné.  
  
 L'instruction `using` garantit que <xref:System.IDisposable.Dispose%2A> est appelé même si une exception se produit lors de l'appel de méthodes sur l'objet.  Vous pouvez obtenir le même résultat en plaçant l'objet dans un bloc try puis en appelant <xref:System.IDisposable.Dispose%2A> dans un bloc finally ; c'est d'ailleurs ainsi que l'instruction `using` est traduite par le compilateur.  L'exemple de code précédent se développe vers le code suivant à la compilation \(notez les accolades supplémentaires qui limitent la portée de l'objet\) :  
  
 [!code-cs[csrefKeywordsNamespace#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_2.cs)]  
  
 Plusieurs instances d'un type peuvent être déclarées dans une instruction `using`, comme indiqué dans l'exemple suivant.  
  
 [!code-cs[csrefKeywordsNamespace#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_3.cs)]  
  
 Il n'est pas conseillé d'instancier l'objet de ressource puis de passer la variable à l'instruction `using`.  En effet, l'objet reste dans la portée une fois que le contrôle a quitté le bloc `using`, même s'il ne peut probablement plus accéder à ses ressources non managées.  En d'autres termes, il ne sera plus complètement initialisé.  Si vous essayez d'utiliser l'objet à l'extérieur du bloc `using`, vous risquez de provoquer la levée d'une exception.  C'est pourquoi il vaut mieux instancier l'objet dans l'instruction `using` et limiter sa portée au bloc `using`.  
  
 [!code-cs[csrefKeywordsNamespace#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_4.cs)]  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Mots clés C\#](../../../csharp/language-reference/keywords/index.md)   
 [using, directive](../../../csharp/language-reference/keywords/using-directive.md)   
 [Garbage Collection](../Topic/Garbage%20Collection.md)   
 [Implementing a Dispose Method](../Topic/Implementing%20a%20Dispose%20Method.md)