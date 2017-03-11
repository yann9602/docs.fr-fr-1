---
title: "Comment&#160;: afficher les arguments de ligne de commande (Guide de programmation C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "arguments de ligne de commande (C#), afficher"
ms.assetid: b8479f2d-9e05-4d38-82da-2e61246e5437
caps.latest.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 19
---
# Comment&#160;: afficher les arguments de ligne de commande (Guide de programmation C#)
Les arguments fournis à un fichier exécutable sur la ligne de commande sont accessibles au moyen d'un paramètre optionnel à `Main`.  Les arguments sont fournis sous la forme d'un tableau de chaînes.  Chaque élément du tableau contient un argument.  L'espace blanc entre arguments est supprimé.  Par exemple, observez ci\-après les appels de ligne de commande d'un fichier exécutable fictif :  
  
|Entrée sur la ligne de commande|Tableau de chaînes passé à Main|  
|-------------------------------------|-------------------------------------|  
|**executable.exe a b c**|"a"<br /><br /> "b"<br /><br /> "c"|  
|**executable.exe un deux**|"un"<br /><br /> "deux"|  
|**executable.exe "un deux" trois**|"un deux"<br /><br /> "trois"|  
  
> [!NOTE]
>  Lorsque vous exécutez une application dans Visual Studio, vous pouvez spécifier des arguments de ligne de commande dans la [Page Déboguer, Concepteur de projets](/visual-studio/ide/reference/debug-page-project-designer).  
  
## Exemple  
 Cet exemple affiche les arguments de ligne de commande passés à une application en ligne de commande.  La sortie indiquée se trouve au\-dessus de la première entrée du tableau ci\-dessus.  
  
 [!code-cs[csProgGuideMain#9](../../../csharp/programming-guide/inside-a-program/codesnippet/csharp/how-to-display-command-l_1.cs)]  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Command\-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)   
 [Main\(\) et arguments de ligne de commande](../../../csharp/programming-guide/main-and-command-args/main-and-command-line-arguments.md)   
 [Comment : accéder à des arguments de ligne de commande à l'aide de foreach](../../../csharp/programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)   
 [Valeurs de retour Main\(\)](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)