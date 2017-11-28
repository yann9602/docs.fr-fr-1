---
title: "Fonctions anonymes (Guide de programmation C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- lambda expressions [C#], as anonymus functions
- anonymous functions [C#]
- anonymous methods [C#]
ms.assetid: 6ce3f04d-0c71-4728-9127-634c7e9a8365
caps.latest.revision: "14"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 888743bb1c49df123b57b4d09e0251dbe1e049d3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="anonymous-functions-c-programming-guide"></a>Fonctions anonymes (Guide de programmation C#)
Une fonction anonyme est une instruction ou expression « inline » qui peut être utilisée partout où un type délégué est attendu. Vous pouvez l’utiliser pour initialiser un délégué nommé ou la passer à la place d’un type délégué nommé comme paramètre de méthode.  
  
 Il existe deux sortes de fonctions anonymes, qui sont décrites dans les rubriques suivantes :  
  
-   [Expressions lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
  
-   [Méthodes anonymes](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)  
  
    > [!NOTE]
    >  Les expressions lambda peuvent être liées à des arborescences d’expression et également à des délégués.  
  
## <a name="the-evolution-of-delegates-in-c"></a>Évolution des délégués en C#  
 Dans C# 1.0, vous pouviez créer une instance d’un délégué en l’initialisant explicitement avec une méthode déjà définie à un autre endroit dans le code. C# 2.0 a introduit le concept des méthodes anonymes, qui vous permettent d’écrire des blocs d’instructions inline sans nom pouvant être exécutés dans un appel de délégué. C# 3.0 a introduit les expressions lambda, qui sont semblables aux méthodes anonymes d’un point de vue conceptuel, mais qui sont plus expressives et concises. Ces deux fonctionnalités sont désignées collectivement comme des *fonctions anonymes*. En général, les applications qui ciblent la version 3.5 ou une version ultérieure de [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] utilisent des expressions lambda.  
  
 L’exemple suivant montre l’évolution de la création de délégués entre C# 1.0 et C# 3.0 :  
  
 [!code-csharp[csProgGuideLINQ#65](../../../csharp/programming-guide/arrays/codesnippet/CSharp/anonymous-functions_1.cs)]  
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Instructions, expressions et opérateurs](../../../csharp/programming-guide/statements-expressions-operators/index.md)  
 [Expressions lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
 [Délégués](../../../csharp/programming-guide/delegates/index.md)  
 [Arborescences de l’expression](http://msdn.microsoft.com/library/fb1d3ed8-d5b0-4211-a71f-dd271529294b)
