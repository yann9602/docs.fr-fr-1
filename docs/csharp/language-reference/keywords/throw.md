---
title: "throw (référence C#) | Microsoft Docs"
ms.date: 2015-03-02
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- throw
- throw_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- throw statement [C#]
- throw expression [C#]
- throw keyword [C#]
ms.assetid: 5ac4feef-4b1a-4c61-aeb4-61d549e5dd42
caps.latest.revision: 22
author: rpetrusha
ms.author: ronpet
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
ms.openlocfilehash: 095a86f5ab2ce50f5931643161a44b5759583e4e
ms.lasthandoff: 03/13/2017

---
# <a name="throw-c-reference"></a>throw (référence C#)
Signale l’occurrence d’une exception pendant l’exécution du programme.  
  
## <a name="remarks"></a>Notes

La syntaxe de `throw` est :

```csharp
throw [e]
```
où `e` est une instance d’une classe dérivée de <xref:System.Exception?displayProperty=fullName>. L’exemple suivant utilise l’instruction `throw` pour lever une exception @System.IndexOutOfRangeException si l’argument passé à une méthode nommée `GetNumber` ne correspond pas à un index valide d’un tableau interne.

[!code-cs[csrefKeyword#1](../../../../samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#1)]  

Les appelants de méthode utilisent alors un bloc `try-catch` ou `try-catch-finally` pour gérer l’exception levée. L’exemple suivant gère l’exception levée par la méthode `GetNumber`.

[!code-cs[csrefKeyword#2](../../../../samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#2)]  

## <a name="re-throwing-an-exception"></a>Génération répétée d’une exception

`throw` peut également être utilisé dans un bloc `catch` pour lever de nouveau une exception gérée dans un bloc `catch`.  Dans ce cas, `throw` n’accepte pas d’opérande d’exception. Cela est très utile lorsqu’une méthode passe un argument d’un appelant à une autre méthode de bibliothèque, et que la méthode de bibliothèque lève une exception qui doit être passée à l’appelant. Par exemple, l’exemple suivant lève de nouveau une exception @System.NullReferenceException qui est levée lorsque vous tentez de récupérer le premier caractère d’une chaîne non initialisée. 

[!code-cs[csrefKeyword#3](../../../../samples/snippets/csharp/language-reference/keywords/throw/throw-3.cs#3)]  

> [!IMPORTANT]
> Vous pouvez également utiliser la syntaxe `throw e` dans un bloc `catch` pour instancier une nouvelle exception que vous passez à l’appelant. Dans ce cas, la trace de la pile de l’exception d’origine, qui est disponible à partir de la propriété @System.Exception.Stacktrace, n’est pas conservée.
 
## <a name="the-throw-expression"></a>Expression `throw`

À compter de C# 7, `throw` peut être utilisé en tant qu’expression et en tant qu’instruction. Ainsi, une exception peut être levée dans des contextes qui n’étaient précédemment pas pris en charge. à savoir :

- [l’opérateur conditionnel](../operators/conditional-operator.md) : l’exemple suivant utilise une expression `throw` pour lever une exception @System.ArgumentException si une méthode reçoit un tableau de chaînes vide. Avant C# 7, cette logique devait figurer dans une instruction `if`/`else`.

   [!code-cs[csrefKeyword#4](../../../../samples/snippets/csharp/language-reference/keywords/throw/conditional.cs#1)]  
  
- [l’opérateur de fusion de Null](../operators/null-conditional-operator.md) : dans l’exemple suivant, une expression `throw` est utilisée avec un opérateur de fusion de Null pour lever une exception si la chaîne assignée à une propriété `Name` est `null`.
 
   [!code-cs[csrefKeyword#5](../../../../samples/snippets/csharp/language-reference/keywords/throw/coalescing.cs#1)]  
 
- un [lambda](../../lambda-expressions.md) ou une méthode expression-bodied : l’exemple suivant illustre une méthode expression-bodied qui lève une exception @System.InvalidCastException, car une conversion vers une valeur @System.DateTime n’est pas prise en charge.
 
   [!code-cs[csrefKeyword#6](../../../../samples/snippets/csharp/language-reference/keywords/throw/exp-bodied.cs#1)]  
 
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur C#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [try-catch](../../../csharp/language-reference/keywords/try-catch.md)   
 [Les instructions try, catch et throw en C++](../../../csharp/language-reference/keywords/try-catch.md)   
 [Mots clés C#](../../../csharp/language-reference/keywords/index.md)   
 [Instructions de gestion des exceptions](../../../csharp/language-reference/keywords/exception-handling-statements.md)   
 [Guide pratique pour lever explicitement des exceptions](https://msdn.microsoft.com/library/xhcbs8fz)
