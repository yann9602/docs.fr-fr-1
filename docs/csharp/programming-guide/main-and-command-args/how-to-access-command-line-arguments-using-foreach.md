---
title: "Comment&#160;: acc&#233;der &#224; des arguments de ligne de commande &#224; l&#39;aide de foreach (Guide de programmation C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "arguments de ligne de commande (C#)"
ms.assetid: 89c3e335-3f5b-4e24-8c5a-b8036561fe8a
caps.latest.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 15
---
# Comment&#160;: acc&#233;der &#224; des arguments de ligne de commande &#224; l&#39;aide de foreach (Guide de programmation C#)
Une autre approche de l'itération au sein d'un tableau consiste à utiliser l'instruction [foreach](../../../csharp/language-reference/keywords/foreach-in.md) comme illustré dans cet exemple.  L'instruction `foreach` peut être utilisée pour itérer au sein d'un tableau, une classe de collection .NET Framework ou toute classe ou tout struct qui implémente l'interface <xref:System.Collections.IEnumerable>.  
  
> [!NOTE]
>  Lorsque vous exécutez une application dans Visual Studio, vous pouvez spécifier des arguments de ligne de commande dans la [Page Déboguer, Concepteur de projets](/visual-studio/ide/reference/debug-page-project-designer).  
  
## Exemple  
 Cet exemple montre comment imprimer les arguments de ligne de commande à l'aide de `foreach`.  
  
 [!code-cs[csProgGuideMain#10](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-access-command-line-arguments-using-foreach_1.cs)]  
  
 [!code-cs[csProgGuideMain#11](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-access-command-line-arguments-using-foreach_2.cs)]  
  
## Voir aussi  
 <xref:System.Array>   
 <xref:System.Collections>   
 [Command\-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [foreach, in](../../../csharp/language-reference/keywords/foreach-in.md)   
 [Main\(\) et arguments de ligne de commande](../../../csharp/programming-guide/main-and-command-args/main-and-command-line-arguments.md)   
 [Comment : afficher les arguments de ligne de commande](../../../csharp/programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)   
 [Valeurs de retour Main\(\)](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)