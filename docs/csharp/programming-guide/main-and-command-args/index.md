---
title: "Main() et arguments de ligne de commande (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- CS5001
- main_CSharpKeyword
- Main
dev_langs:
- CSharp
helpviewer_keywords:
- Main method [C#]
- C# language, command-line arguments
- arguments [C#], command-line
- command line [C#], arguments
- command-line arguments [C#], Main method
ms.assetid: 73a17231-cf96-44ea-aa8a-54807c6fb1f4
caps.latest.revision: 30
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
ms.openlocfilehash: 1b2950f7718cda66b545935229a64850449850d0
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="main-and-command-line-arguments-c-programming-guide"></a>Main() et arguments de ligne de commande (Guide de programmation C#)
La méthode `Main` est le point d’entrée d’une application Windows ou d’une application console C#. (Les bibliothèques et les services ne requièrent pas de méthode `Main` comme point d’entrée.) Lorsque l’application est démarrée, la méthode `Main` est la première méthode appelée.  
  
 Il ne peut y avoir qu’un seul point d’entrée dans un programme C#. Si plusieurs classes ont une méthode `Main`, vous devez compiler votre programme avec l’option de compilateur **/main** pour spécifier quelle méthode `Main` utiliser comme point d’entrée. Pour plus d’informations, consultez l’article [/main (C# Compiler Options) (/main [Options du compilateur C#])](../../../csharp/language-reference/compiler-options/main-compiler-option.md).  
  
 [!code-cs[csProgGuideMain#17](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/main-and-command-line-arguments_1.cs)]  
  
## <a name="overview"></a>Vue d'ensemble  
  
-   La méthode `Main` est le point d’entrée d’un programme .exe ; c’est l’endroit où le contrôle du programme commence et se termine.  
  
-   `Main` est déclaré à l’intérieur d’une classe ou d’un struct. `Main` doit être [statique](../../../csharp/language-reference/keywords/static.md) et ne doit pas être [public](../../../csharp/language-reference/keywords/public.md). (Dans l’exemple précédent, il reçoit l’accès [privé](../../../csharp/language-reference/keywords/private.md) par défaut.) Il n’est pas nécessaire que la classe ou le struct englobant soit statique.  
  
-   `Main` peut avoir le type de retour `void` ou `int`.  
  
-   La méthode `Main` peut être déclarée avec ou sans paramètre `string[]`, qui contient des arguments de ligne de commande. Lorsque vous utilisez [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] pour créer des applications Windows Forms, vous pouvez ajouter le paramètre manuellement ou bien utiliser la classe <xref:System.Environment> pour obtenir les arguments de ligne de commande. Les paramètres sont lus comme des arguments de ligne de commande avec index de base zéro. Contrairement à C et C++, le nom du programme n’est pas traité comme le premier argument de ligne de commande.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Arguments de ligne de commande](../../../csharp/programming-guide/main-and-command-args/command-line-arguments.md)  
  
-   [Comment : afficher les arguments de ligne de commande](../../../csharp/programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)  
  
-   [Comment : accéder à des arguments de ligne de commande à l’aide de foreach](../../../csharp/programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)  
  
-   [Valeurs de retour Main()](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)  
  
## <a name="c-language-specification"></a>Spécification du langage C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Génération en ligne de commande avec csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Méthodes](../../../csharp/programming-guide/classes-and-structs/methods.md)   
 [À l’intérieur d’un programme C#](../../../csharp/programming-guide/inside-a-program/index.md)   
 [\<paveover>Exemples d’applications C#](http://msdn.microsoft.com/en-us/9a9d7aaa-51d3-4224-b564-95409b0f3e15)

