---
title: "Guide pratique pour gérer une exception à l’aide de try/catch (Guide de programmation C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- exception handling [C#], try/catch blocks
- exceptions [C#], try/catch blocks
- try/catch blocks [C#]
ms.assetid: ca8e3773-980e-4767-8633-7408540e9818
caps.latest.revision: "14"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 9098bbcf5cefb85211f9d3bb9cac15943ba02172
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-handle-an-exception-using-trycatch-c-programming-guide"></a>Guide pratique pour gérer une exception à l'aide de try/catch (Guide de programmation C#)
L’objectif d’un bloc [try-catch](../../../csharp/language-reference/keywords/try-catch.md) est d’intercepter et de gérer une exception générée par du code opérationnel. Certaines exceptions peuvent être gérées dans un bloc `catch` et le problème résolu sans que l’exception soit levée à nouveau, mais le plus souvent la seule chose que vous puissiez faire est de vous assurer que l’exception appropriée est levée.  
  
## <a name="example"></a>Exemple  
 Dans cet exemple, <xref:System.IndexOutOfRangeException> n’est pas l’exception la plus appropriée : <xref:System.ArgumentOutOfRangeException> a de plus de sens pour la méthode car l’erreur est provoquée par l’argument `index` passé par l’appelant.  
  
 [!code-csharp[csProgGuideExceptions#5](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/how-to-handle-an-exception-using-try-catch_1.cs)]  
  
## <a name="comments"></a>Commentaires  
 Le code qui provoque une exception est cloisonné dans le bloc `try`. Une instruction `catch` est ajoutée juste après pour gérer `IndexOutOfRangeException`, si elle se produit. Le bloc `catch` gère `IndexOutOfRangeException` et lève l’exception plus appropriée `ArgumentOutOfRangeException` à la place. Pour fournir à l’appelant autant d’informations que possible, pensez à spécifier l’exception d’origine comme <xref:System.Exception.InnerException%2A> de la nouvelle exception. Comme la propriété <xref:System.Exception.InnerException%2A> a la valeur [readonly](../../../csharp/language-reference/keywords/readonly.md), vous devez l’affecter dans le constructeur de la nouvelle exception.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [Exceptions et gestion des exceptions](../../../csharp/programming-guide/exceptions/index.md)  
 [Gestion des exceptions](../../../csharp/programming-guide/exceptions/exception-handling.md)
