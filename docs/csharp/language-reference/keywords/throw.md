---
title: "throw (référence C#)"
ms.date: 03/02/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- throw
- throw_CSharpKeyword
helpviewer_keywords:
- throw statement [C#]
- throw expression [C#]
- throw keyword [C#]
ms.assetid: 5ac4feef-4b1a-4c61-aeb4-61d549e5dd42
caps.latest.revision: "22"
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e56bd8f8b6bfcc7c8f1eb2df6ac157e28adac331
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="throw-c-reference"></a>throw (référence C#)
Signale l’occurrence d’une exception pendant l’exécution du programme.  
  
## <a name="remarks"></a>Notes

La syntaxe de `throw` est :

```csharp
throw [e]
```
où `e` est une instance d’une classe dérivée de <xref:System.Exception?displayProperty=nameWithType>. L’exemple suivant utilise l’instruction `throw` pour lever une exception <xref:System.IndexOutOfRangeException> si l’argument passé à une méthode nommée `GetNumber` ne correspond pas à un index valide d’un tableau interne.

[!code-csharp[csrefKeyword#1](../../../../samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#1)]  

Les appelants de méthode utilisent alors un bloc `try-catch` ou `try-catch-finally` pour gérer l’exception levée. L’exemple suivant gère l’exception levée par la méthode `GetNumber`.

[!code-csharp[csrefKeyword#2](../../../../samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#2)]  

## <a name="re-throwing-an-exception"></a>Génération répétée d’une exception

`throw` peut également être utilisé dans un bloc `catch` pour lever de nouveau une exception gérée dans un bloc `catch`.  Dans ce cas, `throw` n’accepte pas d’opérande d’exception. Cela est très utile lorsqu’une méthode passe un argument d’un appelant à une autre méthode de bibliothèque, et que la méthode de bibliothèque lève une exception qui doit être passée à l’appelant. Par exemple, l’exemple suivant lève de nouveau une exception <xref:System.NullReferenceException> qui est levée lorsque vous tentez de récupérer le premier caractère d’une chaîne non initialisée. 

[!code-csharp[csrefKeyword#3](../../../../samples/snippets/csharp/language-reference/keywords/throw/throw-3.cs#3)]  

> [!IMPORTANT]
> Vous pouvez également utiliser la syntaxe `throw e` dans un bloc `catch` pour instancier une nouvelle exception que vous passez à l’appelant. Dans ce cas, la trace de la pile de l’exception d’origine, qui est disponible à partir de la propriété <xref:System.Exception.StackTrace>, n’est pas conservée.
 
## <a name="the-throw-expression"></a>Expression `throw`

À compter de C# 7, `throw` peut être utilisé en tant qu’expression et en tant qu’instruction. Ainsi, une exception peut être levée dans des contextes qui n’étaient précédemment pas pris en charge. à savoir :

- [l’opérateur conditionnel](../operators/conditional-operator.md) : l’exemple suivant utilise une expression `throw` pour lever une exception <xref:System.ArgumentException> si une méthode reçoit un tableau de chaînes vide. Avant C# 7, cette logique devait figurer dans une instruction `if`/`else`.

   [!code-csharp[csrefKeyword#4](../../../../samples/snippets/csharp/language-reference/keywords/throw/conditional.cs#1)]  
  
- [l’opérateur de fusion de Null](../operators/null-conditional-operator.md) : dans l’exemple suivant, une expression `throw` est utilisée avec un opérateur de fusion de Null pour lever une exception si la chaîne assignée à une propriété `Name` est `null`.
 
   [!code-csharp[csrefKeyword#5](../../../../samples/snippets/csharp/language-reference/keywords/throw/coalescing.cs#1)]  
 
- un [lambda](../../lambda-expressions.md) ou une méthode expression-bodied : l’exemple suivant illustre une méthode expression-bodied qui lève une exception <xref:System.InvalidCastException>, car une conversion vers une valeur <xref:System.DateTime> n’est pas prise en charge.
 
   [!code-csharp[csrefKeyword#6](../../../../samples/snippets/csharp/language-reference/keywords/throw/exp-bodied.cs#1)]  
 
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Référence C#](../../../csharp/language-reference/index.md)  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [try-catch](../../../csharp/language-reference/keywords/try-catch.md)  
 [Try, catch et throw instructions en C++](../../../csharp/language-reference/keywords/try-catch.md)  
 [Mots clés C#](../../../csharp/language-reference/keywords/index.md)  
 [Instructions de gestion des exceptions](../../../csharp/language-reference/keywords/exception-handling-statements.md)  
 [Guide pratique pour lever explicitement des exceptions](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
