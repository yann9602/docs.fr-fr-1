---
title: "Guide pratique pour gérer une exception à l’aide de try/catch (Guide de programmation C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- exception handling [C#], try/catch blocks
- exceptions [C#], try/catch blocks
- try/catch blocks [C#]
ms.assetid: ca8e3773-980e-4767-8633-7408540e9818
caps.latest.revision: 14
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
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 10eac61f4b9bb186d28044862ebc7273c6eb07b2
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-handle-an-exception-using-trycatch-c-programming-guide"></a>Guide pratique pour gérer une exception à l'aide de try/catch (Guide de programmation C#)
L’objectif d’un bloc [try-catch](../../../csharp/language-reference/keywords/try-catch.md) est d’intercepter et de gérer une exception générée par du code opérationnel. Certaines exceptions peuvent être gérées dans un bloc `catch` et le problème résolu sans que l’exception soit levée à nouveau, mais le plus souvent la seule chose que vous puissiez faire est de vous assurer que l’exception appropriée est levée.  
  
## <a name="example"></a>Exemple  
 Dans cet exemple, <xref:System.IndexOutOfRangeException> n’est pas l’exception la plus appropriée : <xref:System.ArgumentOutOfRangeException> est plus logique pour la méthode, car l’erreur est provoquée par l’argument `index` passé par l’appelant.  
  
 [!code-cs[csProgGuideExceptions#5](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/how-to-handle-an-exception-using-try-catch_1.cs)]  
  
## <a name="comments"></a>Commentaires  
 Le code qui provoque une exception est cloisonné dans le bloc `try`. Une instruction `catch` est ajoutée juste après pour gérer `IndexOutOfRangeException`, si elle se produit. Le bloc `catch` gère `IndexOutOfRangeException` et lève l’exception plus appropriée `ArgumentOutOfRangeException` à la place. Pour fournir à l’appelant le plus d’informations possible, vous pouvez spécifier l’exception d’origine comme <xref:System.Exception.InnerException%2A> de la nouvelle exception. La propriété <xref:System.Exception.InnerException%2A> ayant la valeur [readonly](../../../csharp/language-reference/keywords/readonly.md), vous devez l’attribuer dans le constructeur de la nouvelle exception.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Exceptions et gestion des exceptions](../../../csharp/programming-guide/exceptions/index.md)   
 [Gestion des exceptions](../../../csharp/programming-guide/exceptions/exception-handling.md)
