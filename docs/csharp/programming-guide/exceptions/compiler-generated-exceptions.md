---
title: "Exceptions générées par le compilateur (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- exceptions [C#], compiler-generated
ms.assetid: 53b52f97-b366-4ed7-b05b-9eb78096b7f9
caps.latest.revision: 13
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: d8fbae9272b34dd4d010199470c930c846cd1b74
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="compiler-generated-exceptions-c-programming-guide"></a>Exceptions générées par le compilateur (Guide de programmation C#)
Certaines exceptions sont levées automatiquement par le Common Language Runtime (CLR) du .NET Framework en cas d’échec d’opérations de base. Ces exceptions et leurs conditions d’erreur sont répertoriées dans le tableau suivant.  
  
|Exception|Description|  
|---------------|-----------------|  
|<xref:System.ArithmeticException>|Classe de base pour les exceptions qui se produisent pendant des opérations arithmétiques, telles que <xref:System.DivideByZeroException> et <xref:System.OverflowException>.|  
|<xref:System.ArrayTypeMismatchException>|Levée quand un tableau ne peut pas stocker un élément donné, car le type réel de l’élément est incompatible avec le type réel du tableau.|  
|<xref:System.DivideByZeroException>|Levée lors d’une tentative de division d’une valeur intégrale par zéro.|  
|<xref:System.IndexOutOfRangeException>|Levée lors d’une tentative d’indexation d’un tableau à l’aide d’un index qui est inférieur à zéro ou en dehors des limites du tableau.|  
|<xref:System.InvalidCastException>|Levée quand une conversion explicite d’un type de base en interface ou en un type dérivé échoue au moment de l’exécution.|  
|<xref:System.NullReferenceException>|Levée quand vous essayez de référencer un objet dont la valeur est [null](../../../csharp/language-reference/keywords/null.md).|  
|<xref:System.OutOfMemoryException>|Levée quand une tentative d’allocation de mémoire à l’aide de l’opérateur [new](../../../csharp/language-reference/keywords/new-operator.md) échoue. Cela indique que la mémoire disponible pour le Commun Language Runtime est épuisée.|  
|<xref:System.OverflowException>|Levée quand une opération dans un contexte `checked` engendre un dépassement.|  
|<xref:System.StackOverflowException>|Levée quand la pile d’exécution est épuisée par un trop grand nombre d’appels de méthode en attente ; cela indique généralement une récurrence très profonde ou infinie.|  
|<xref:System.TypeInitializationException>|Levée quand un constructeur statique lève une exception et qu’il n’existe aucune clause `catch` pour l’intercepter.|  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Exceptions et gestion des exceptions](../../../csharp/programming-guide/exceptions/index.md)   
 [Gestion des exceptions](../../../csharp/programming-guide/exceptions/exception-handling.md)   
 [try-catch](../../../csharp/language-reference/keywords/try-catch.md)   
 [try-finally](../../../csharp/language-reference/keywords/try-finally.md)   
 [try-catch-finally](../../../csharp/language-reference/keywords/try-catch-finally.md)

