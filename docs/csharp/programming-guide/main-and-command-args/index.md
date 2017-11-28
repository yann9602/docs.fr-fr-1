---
title: "Main() et arguments de ligne de commande (Guide de programmation C#)"
ms.date: 08/02/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- CS5001
- main_CSharpKeyword
- Main
helpviewer_keywords:
- Main method [C#]
- C# language, command-line arguments
- arguments [C#], command-line
- command line [C#], arguments
- command-line arguments [C#], Main method
ms.assetid: 73a17231-cf96-44ea-aa8a-54807c6fb1f4
caps.latest.revision: "30"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ab0b93a867ecf252bffd529d284ef9ddcc9163ba
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="main-and-command-line-arguments-c-programming-guide"></a>Main() et arguments de ligne de commande (Guide de programmation C#)

La méthode `Main` est le point d’entrée d’une application C#. (Les bibliothèques et les services ne requièrent pas de méthode `Main` comme point d’entrée.) Lorsque l’application est démarrée, la méthode `Main` est la première méthode appelée.

 Il ne peut y avoir qu’un seul point d’entrée dans un programme C#. Si plusieurs classes ont une méthode `Main`, vous devez compiler votre programme avec l’option de compilateur **/main** pour spécifier quelle méthode `Main` utiliser comme point d’entrée. Pour plus d’informations, consultez l’article [/main (C# Compiler Options) (/main [Options du compilateur C#])](../../../csharp/language-reference/compiler-options/main-compiler-option.md).

 [!code-csharp[csProgGuideMain#17](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/main-and-command-line-arguments_1.cs)]

## <a name="overview"></a>Vue d'ensemble

- La méthode `Main` est le point d’entrée d’un programme exécutable ; c’est l’endroit où le contrôle du programme commence et se termine.
- `Main` est déclaré à l’intérieur d’une classe ou d’un struct. `Main` doit être [statique](../../../csharp/language-reference/keywords/static.md) et ne doit pas être [public](../../../csharp/language-reference/keywords/public.md). (Dans l’exemple précédent, il reçoit l’accès [privé](../../../csharp/language-reference/keywords/private.md) par défaut.) Il n’est pas nécessaire que la classe ou le struct englobant soit statique.
- `Main` peut avoir un type de retour `void`, `int` ou, à partir de C# 7.1, `Task` ou `Task<int>`.
- Si et seulement si `Main` retourne un `Task` ou `Task<int>`, la déclaration de `Main` peut inclure le modificateur [`async`](../../language-reference/keywords/async.md). Notez que cela exclut spécifiquement une méthode `async void Main`.
- La méthode `Main` peut être déclarée avec ou sans paramètre `string[]`, qui contient des arguments de ligne de commande. Lorsque vous utilisez [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] pour créer des applications Windows, vous pouvez ajouter le paramètre manuellement ou bien utiliser la classe <xref:System.Environment> pour obtenir les arguments de ligne de commande. Les paramètres sont lus comme des arguments de ligne de commande avec index de base zéro. Contrairement à C et C++, le nom du programme n’est pas traité comme le premier argument de ligne de commande.

L’ajout des types de retour `async` et `Task`, `Task<int>` simplifie le code de programme lorsque les applications de console doivent démarrer et `await` des opérations asynchrones dans `Main`.

## <a name="c-language-specification"></a>spécification du langage C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Voir aussi
[Génération à partir de la ligne de commande avec csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)
[Guide de programmation C#](../../../csharp/programming-guide/index.md)
[Méthodes](../../../csharp/programming-guide/classes-and-structs/methods.md)
[À l’intérieur d’un programme C#](../../../csharp/programming-guide/inside-a-program/index.md)
