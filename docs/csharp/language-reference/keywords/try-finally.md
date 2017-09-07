---
title: "try-finally (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- finally
- finally_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- finally keyword [C#]
- try-finally statement [C#]
ms.assetid: c27623fb-7261-4464-862c-7a369d3c8f0a
caps.latest.revision: 25
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
ms.openlocfilehash: 88b9960b8c026d1fcd8eed1815ade57422cd2a15
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="try-finally-c-reference"></a>try-finally (référence C#)
En utilisant un bloc `finally`, vous pouvez nettoyer toutes les ressources allouées dans un bloc [try](../../../csharp/language-reference/keywords/try-catch.md) et vous pouvez exécuter du code même si une exception se produit dans le bloc `try`. En règle générale, les instructions d’un bloc `finally` s’exécutent lorsque le contrôle quitte une instruction `try`. Le transfert de contrôle peut se produire suite à une exécution normale, à l’exécution d’une instruction `break`, `continue`, `goto` ou `return`, ou à la propagation d’une exception hors de l’instruction `try`.  
  
 Dans une exception gérée, le bloc `finally` associé est assuré d’être exécuté. Toutefois, si l’exception n’est pas gérée, l’exécution du bloc `finally` dépend de la manière dont l’opération de déroulement d’exception est déclenchée. Ceci, à son tour, dépend du paramétrage de votre ordinateur. Pour plus d’informations, consultez [Traitement d’une exception non prise en charge dans le CLR](http://go.microsoft.com/fwlink/?LinkId=128371).  
  
 En général, lorsqu’une exception non gérée met fin à une application, que le bloc `finally` soit exécuté ou non n’est pas important. Toutefois, si vous avez des instructions dans un bloc `finally` qui doivent être exécutées même dans cette situation, une solution consiste à ajouter un bloc `catch` à l’instruction `try`-`finally`. Ou bien, vous pouvez intercepter l’exception qui peut être levée dans le bloc `try` d’une instruction `try`-`finally` plus haut dans la pile des appels. Autrement dit, vous pouvez intercepter l’exception dans la méthode qui appelle la méthode contenant l’instruction `try`-`finally`, ou dans la méthode qui appelle cette méthode, ou dans n’importe quelle méthode figurant dans la pile des appels. Si l’exception n’est pas interceptée, l’exécution du bloc `finally` varie selon que le système d’exploitation choisit de déclencher une opération de déroulement d’exception.  
  
## <a name="example"></a>Exemple  
 Dans l’exemple suivant, une instruction de conversion non valide provoque une exception `System.InvalidCastException`. L’exception n’est pas gérée.  
  
 [!code-cs[csrefKeywordsExceptions#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-finally_1.cs)]  
  
 Dans l’exemple suivant, une exception issue de la méthode `TryCast` est interceptée dans une méthode plus loin dans la pile des appels.  
  
 [!code-cs[csrefKeywordsExceptions#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-finally_2.cs)]  
  
 Pour plus d’informations sur `finally`, consultez [try-catch-finally](../../../csharp/language-reference/keywords/try-catch-finally.md).  
  
 C# contient également l’[instruction using](../../../csharp/language-reference/keywords/using-statement.md), qui fournit des fonctionnalités similaires pour les objets <xref:System.IDisposable> dans une syntaxe pratique.  
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur C#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Mots clés C#](../../../csharp/language-reference/keywords/index.md)   
 [Instructions try, throw et catch (C++)](/cpp/cpp/try-throw-and-catch-statements-cpp)   
 [Instructions de gestion des exceptions](../../../csharp/language-reference/keywords/exception-handling-statements.md)   
 [throw](../../../csharp/language-reference/keywords/throw.md)   
 [try-catch](../../../csharp/language-reference/keywords/try-catch.md)   
 [Guide pratique pour lever explicitement des exceptions](https://msdn.microsoft.com/library/xhcbs8fz)

