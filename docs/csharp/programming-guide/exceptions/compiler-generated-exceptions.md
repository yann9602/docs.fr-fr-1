---
title: "Exceptions g&#233;n&#233;r&#233;es par le compilateur (Guide de programmation C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "exceptions (C#), générées par le compilateur"
ms.assetid: 53b52f97-b366-4ed7-b05b-9eb78096b7f9
caps.latest.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 13
---
# Exceptions g&#233;n&#233;r&#233;es par le compilateur (Guide de programmation C#)
Certaines exceptions sont levées automatiquement par le Common Language Runtime \(CLR\) du .NET Framework lorsque des opérations de base échouent.  Ces exceptions et leurs conditions d'erreur sont répertoriées dans le tableau suivant.  
  
|Exception|Description|  
|---------------|-----------------|  
|<xref:System.ArithmeticException>|Classe de base pour les exceptions qui se produisent pendant des opérations arithmétiques, telles que <xref:System.DivideByZeroException> et <xref:System.OverflowException>.|  
|<xref:System.ArrayTypeMismatchException>|Levée lorsqu'un tableau ne peut pas stocker un élément donné, car le type réel de l'élément est incompatible avec le type réel du tableau.|  
|<xref:System.DivideByZeroException>|Levée à l'occasion d'une tentative de division d'une valeur intégrale par zéro.|  
|<xref:System.IndexOutOfRangeException>|Levée lors d'une tentative d'indexation d'un tableau via un index qui est inférieur à zéro ou en dehors des limites du tableau.|  
|<xref:System.InvalidCastException>|Levée lorsqu'une conversion explicite d'un type de base en interface ou en un type dérivé échoue au moment de l'exécution.|  
|<xref:System.NullReferenceException>|Levée lorsque vous essayez de référencer un objet dont la valeur est [nulle](../../../csharp/language-reference/keywords/null.md).|  
|<xref:System.OutOfMemoryException>|Levée lorsqu'une tentative d'allouer la mémoire à l'aide de l'opérateur [new](../../../csharp/language-reference/keywords/new-operator.md) échoue.  Cela indique que la mémoire disponible pour le Commun Language Runtime a été épuisée.|  
|<xref:System.OverflowException>|Levée lorsqu'une opération dans un contexte `checked` déborde.|  
|<xref:System.StackOverflowException>|Levée lorsque la pile d'exécution est épuisée par un trop grand nombre d'appels de méthode en attente ; ce qui est généralement le signe d'une récurrence très profonde ou infinie.|  
|<xref:System.TypeInitializationException>|Levée lorsqu'un constructeur statique lève une exception, et qu'aucune clause `catch` n'existe pour l'intercepter.|  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Exceptions et gestion des exceptions](../../../csharp/programming-guide/exceptions/exceptions-and-exception-handling.md)   
 [Gestion des exceptions](../../../csharp/programming-guide/exceptions/exception-handling.md)   
 [try\-catch](../../../csharp/language-reference/keywords/try-catch.md)   
 [try\-finally](../../../csharp/language-reference/keywords/try-finally.md)   
 [try\-catch\-finally](../../../csharp/language-reference/keywords/try-catch-finally.md)