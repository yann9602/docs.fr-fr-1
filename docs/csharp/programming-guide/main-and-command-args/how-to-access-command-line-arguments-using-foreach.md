---
title: "Guide pratique pour accéder à des arguments de ligne de commande à l’aide de foreach (Guide de programmation C#) | Microsoft Docs"
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
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 2f0e3bce88beafd45a21773a7b26ffb2bb41215d
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-access-command-line-arguments-using-foreach-c-programming-guide"></a>Guide pratique pour accéder à des arguments de ligne de commande à l’aide de foreach (Guide de programmation C#)
Il existe une autre méthode d’itération au sein d’un tableau qui consiste à utiliser l’instruction [foreach](../../../csharp/language-reference/keywords/foreach-in.md), comme indiqué dans cet exemple. L’instruction `foreach` peut être utilisée pour effectuer une itération au sein d’un tableau, une classe de collection .NET Framework, ou toute classe ou struct qui implémente l’interface <xref:System.Collections.IEnumerable>.  
  
> [!NOTE]
>  Quand vous exécutez une application dans Visual Studio, vous pouvez spécifier des arguments de ligne de commande dans la [page Déboguer du Concepteur de projet](https://docs.microsoft.com/visualstudio/ide/reference/debug-page-project-designer).  
  
## <a name="example"></a>Exemple  
 Cet exemple montre comment imprimer les arguments de ligne de commande à l’aide de `foreach`.  
  
 [!code-cs[csProgGuideMain#10](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-access-command-line-arguments-using-foreach_1.cs)]  
  
 [!code-cs[csProgGuideMain#11](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-access-command-line-arguments-using-foreach_2.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Array>   
 <xref:System.Collections>   
 [Génération à partir de la ligne de commande avec csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [foreach, in](../../../csharp/language-reference/keywords/foreach-in.md)   
 [Main() et arguments de ligne de commande](../../../csharp/programming-guide/main-and-command-args/index.md)   
 [Guide pratique pour afficher les arguments de ligne de commande](../../../csharp/programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)   
 [Valeurs de retour Main()](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)
