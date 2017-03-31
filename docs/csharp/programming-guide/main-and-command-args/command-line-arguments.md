---
title: "Arguments de ligne de commande (Guide de programmation C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- command-line arguments [C#]
ms.assetid: 0e597e0d-ea7a-41ba-a38a-0198122f3c26
caps.latest.revision: 27
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
ms.openlocfilehash: 4034f1575321c94f003a12a83df617d4a0d50702
ms.lasthandoff: 03/13/2017

---
# <a name="command-line-arguments-c-programming-guide"></a>Arguments de ligne de commande (Guide de programmation C#)
Vous pouvez envoyer des arguments à la méthode `Main` en définissant la méthode de l’une des manières suivantes :  
  
 [!code-cs[csProgGuideMain#2](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/command-line-arguments_1.cs)]  
  
 [!code-cs[csProgGuideMain#3](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/command-line-arguments_2.cs)]  
  
> [!NOTE]
>  Pour activer des arguments de ligne de commande dans la méthode `Main` dans une application Windows Forms, vous devez modifier manuellement la signature de `Main` dans program.cs. Le code généré par le Concepteur Windows Forms crée un `Main` sans paramètre d’entrée. Vous pouvez également utiliser <xref:System.Environment.CommandLine%2A?displayProperty=fullName> ou <xref:System.Environment.GetCommandLineArgs%2A?displayProperty=fullName> pour accéder aux arguments de ligne de commande à partir de n’importe quel emplacement d’une application console ou Windows.  
  
 Le paramètre de la méthode `Main` est un tableau <xref:System.String> qui représente les arguments de ligne de commande. En général, vous déterminez s’il existe des arguments en testant la propriété `Length`, par exemple :  
  
 [!code-cs[csProgGuideMain#4](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/command-line-arguments_3.cs)]  
  
 Vous pouvez également convertir les arguments de chaîne en types numériques à l’aide de la classe <xref:System.Convert> ou de la méthode `Parse`. Par exemple, l’instruction suivante convertit `string` en nombre `long` en utilisant la méthode <xref:System.Int64.Parse%2A> :  
  
```  
long num = Int64.Parse(args[0]);  
```  
  
 Il est également possible d’utiliser le type C# `long`, qui sert d’alias à `Int64` :  
  
```  
long num = long.Parse(args[0]);  
```  
  
 Vous pouvez également utiliser la méthode `ToInt64` de la classe `Convert` pour obtenir le même résultat :  
  
```  
long num = Convert.ToInt64(s);  
```  
  
 Pour plus d’informations, consultez <xref:System.Int64.Parse%2A> et <xref:System.Convert>.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment utiliser des arguments de ligne de commande dans une application console. L’application prend un argument au moment de l’exécution, le convertit en entier, puis calcule la factorielle du nombre. Si aucun argument n’est fourni, l’application affiche un message pour expliquer comment le programme doit être utilisé.  
  
 Pour compiler et exécuter l’application à partir d’une invite de commandes, procédez comme suit :  
  
1.  Collez le code suivant dans un éditeur de texte, puis enregistrez le fichier en tant que fichier texte sous le nom `Factorial.cs`.  
  
     [!code-cs[csProgGuideMain#16](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/command-line-arguments_4.cs)]  
  
2.  Dans l’écran **Démarrer** ou le menu **Démarrer**, ouvrez une fenêtre **Invite de commandes développeur** Visual Studio, puis accédez au dossier qui contient le fichier que vous venez de créer.  
  
3.  Entrez la commande suivante pour compiler l’application.  
  
     `csc Factorial.cs`  
  
     Si votre application ne contient pas d’erreurs de compilation, un fichier exécutable nommé `Factorial.exe` est créé.  
  
4.  Entrez la commande suivante pour calculer la factorielle de 3 :  
  
     `Factorial 3`  
  
5.  Cette commande génère la sortie suivante : `The factorial of 3 is 6.`  
  
> [!NOTE]
>  Quand vous exécutez une application dans Visual Studio, vous pouvez spécifier des arguments de ligne de commande dans la [page Déboguer du Concepteur de projet](https://docs.microsoft.com/visualstudio/ide/reference/debug-page-project-designer).  
  
 Pour obtenir d’autres exemples d’utilisation des arguments de ligne de commande, consultez [Guide pratique pour créer et utiliser des assemblys à l’aide de la ligne de commande](http://msdn.microsoft.com/library/70f65026-3687-4e9c-ab79-c18b97dd8be4).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Environment?displayProperty=fullName>   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Main() et arguments de ligne de commande](../../../csharp/programming-guide/main-and-command-args/index.md)   
 [Guide pratique pour afficher les arguments de ligne de commande](../../../csharp/programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)   
 [Guide pratique pour accéder à des arguments de ligne de commande à l’aide de foreach](../../../csharp/programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)   
 [Valeurs de retour Main()](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)   
 [Classes](../../../csharp/programming-guide/classes-and-structs/classes.md)
