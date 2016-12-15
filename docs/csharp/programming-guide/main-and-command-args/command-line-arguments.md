---
title: "Arguments de ligne de commande (Guide de programmation C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "arguments de ligne de commande (C#)"
ms.assetid: 0e597e0d-ea7a-41ba-a38a-0198122f3c26
caps.latest.revision: 27
caps.handback.revision: 27
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Arguments de ligne de commande (Guide de programmation C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Vous pouvez envoyer des arguments à la méthode `Main` en définissant la méthode de l'une des façons suivantes :  
  
 [!code-cs[csProgGuideMain#2](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/command-line-arguments_1.cs)]  
  
 [!code-cs[csProgGuideMain#3](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/command-line-arguments_2.cs)]  
  
> [!NOTE]
>  Pour activer des arguments de ligne de commande dans la méthode `Main` dans une application Windows Forms, vous devez modifier manuellement la signature de `Main` dans program.cs.  Le code généré par le Concepteur Windows Forms crée un `Main` sans paramètre d'entrée.  Vous pouvez également utiliser <xref:System.Environment.CommandLine%2A?displayProperty=fullName> ou <xref:System.Environment.GetCommandLineArgs%2A?displayProperty=fullName> pour accéder aux arguments de ligne de commande à partir de n'importe quel emplacement d'une application console ou Windows.  
  
 Le paramètre de la méthode `Main` est un tableau <xref:System.String> qui représente les arguments de la ligne de commande.  En général, la vérification de l'existence des arguments s'effectue en testant la propriété `Length`. Exemple :  
  
 [!code-cs[csProgGuideMain#4](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/command-line-arguments_3.cs)]  
  
 Vous pouvez aussi convertir les arguments de type chaîne en arguments numériques à l'aide de la classe <xref:System.Convert> ou de la méthode `Parse`.  Par exemple, l'instruction ci\-dessous convertit `string` en nombre `long` en utilisant la méthode <xref:System.Int64.Parse%2A> :  
  
```  
long num = Int64.Parse(args[0]);  
```  
  
 Il est possible aussi d'utiliser le type `long` C\#, qui sert d'alias à `Int64` :  
  
```  
long num = long.Parse(args[0]);  
```  
  
 Vous pouvez également utiliser la méthode `ToInt64` de la classe `Convert` pour obtenir le même résultat :  
  
```  
long num = Convert.ToInt64(s);  
```  
  
 Pour plus d'informations, consultez <xref:System.Int64.Parse%2A> et <xref:System.Convert>.  
  
## Exemple  
 L'exemple suivant montre comment utiliser les arguments de ligne de commande dans les applications console.  L'application prend un argument au moment de l'exécution, le convertit en entier et calcule la factorielle du nombre.  Si aucun argument n'est fourni, l'application affiche un message pour expliquer comment il doit être utilisé.  
  
 Pour compiler et exécuter l'application à partir d'une invite de commandes, suivez ces étapes :  
  
1.  Collez le code suivant dans un éditeur de texte et enregistrez le fichier sous forme de fichier texte avec le nom `Factorial.cs`.  
  
     [!code-cs[csProgGuideMain#16](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/command-line-arguments_4.cs)]  
  
2.  Dans l'écran **Démarrer** ou le menu **Démarrer**, ouvrez une fenêtre **Invite de commandes Développeur** Visual Studio, puis accédez au dossier qui contient le fichier que vous venez de créer.  
  
3.  Entrez la commande suivante pour compiler l'application.  
  
     `csc Factorial.cs`  
  
     Si votre application n'a pas d'erreurs de compilation, un fichier exécutable nommé `Factorial.exe` est créé.  
  
4.  Entrez la commande suivante pour calculer la factorielle de 3 :  
  
     `Factorial 3`  
  
5.  La commande génère la sortie suivante : `The factorial of 3 is 6.`  
  
> [!NOTE]
>  Lorsque vous exécutez une application dans Visual Studio, vous pouvez spécifier des arguments de ligne de commande dans la [Page Déboguer, Concepteur de projets](/visual-studio/ide/reference/debug-page-project-designer).  
  
 Pour obtenir d'autres exemples d'utilisation des arguments de ligne de commande, consultez [Comment : créer et utiliser des assemblys à l’aide de la ligne de commande](../Topic/How%20to:%20Create%20and%20Use%20Assemblies%20Using%20the%20Command%20Line%20\(C%23%20and%20Visual%20Basic\).md).  
  
## Voir aussi  
 <xref:System.Environment?displayProperty=fullName>   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Main\(\) et arguments de ligne de commande](../../../csharp/programming-guide/main-and-command-args/main-and-command-line-arguments.md)   
 [Comment : afficher les arguments de ligne de commande](../../../csharp/programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)   
 [Comment : accéder à des arguments de ligne de commande à l'aide de foreach](../../../csharp/programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)   
 [Valeurs de retour Main\(\)](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)   
 [Classes](../../../csharp/programming-guide/classes-and-structs/classes.md)