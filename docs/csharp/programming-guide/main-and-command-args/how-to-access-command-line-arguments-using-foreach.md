---
title: "Guide pratique pour accéder à des arguments de ligne de commande à l’aide de foreach (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- command-line arguments [C#]
ms.assetid: 89c3e335-3f5b-4e24-8c5a-b8036561fe8a
caps.latest.revision: 15
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
ms.openlocfilehash: 766b5cd0879edec1dc409e07c4f62ee693fd615d
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-access-command-line-arguments-using-foreach-c-programming-guide"></a>Guide pratique pour accéder à des arguments de ligne de commande à l’aide de foreach (Guide de programmation C#)
Il existe une autre méthode d’itération au sein d’un tableau qui consiste à utiliser l’instruction [foreach](../../../csharp/language-reference/keywords/foreach-in.md), comme indiqué dans cet exemple. L’instruction `foreach` peut être utilisée pour effectuer une itération au sein d’un tableau, d’une classe de collection .NET Framework, ou d’une classe ou d’un struct qui implémente l’interface <xref:System.Collections.IEnumerable>.  
  
> [!NOTE]
>  Quand vous exécutez une application dans Visual Studio, vous pouvez spécifier des arguments de ligne de commande dans la [page Déboguer du Concepteur de projet](/visualstudio/ide/reference/debug-page-project-designer).  
  
## <a name="example"></a>Exemple  
 Cet exemple montre comment imprimer les arguments de ligne de commande à l’aide de `foreach`.  
  
 [!code-cs[csProgGuideMain#10](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-access-command-line-arguments-using-foreach_1.cs)]  
  
 [!code-cs[csProgGuideMain#11](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-access-command-line-arguments-using-foreach_2.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Array>   
 <xref:System.Collections>   
 [Génération en ligne de commande avec csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [foreach, in](../../../csharp/language-reference/keywords/foreach-in.md)   
 [Main() et arguments de ligne de commande](../../../csharp/programming-guide/main-and-command-args/index.md)   
 [Guide pratique pour afficher les arguments de ligne de commande](../../../csharp/programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)   
 [Valeurs de retour Main()](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)

