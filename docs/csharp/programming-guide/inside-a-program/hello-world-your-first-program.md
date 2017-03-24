---
title: "Hello World -- Votre premier programme (guide de programmation C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "get-started-article"
f1_keywords: 
  - "cs.program"
  - "vs.csharp.startpage.firstapplication"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "exemples (C#), Hello World"
  - "Hello World (exemple C#)"
ms.assetid: 6493182a-b0b6-4539-a719-518a168cb730
caps.latest.revision: 39
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 39
---
# Hello World -- Votre premier programme (guide de programmation C#)
La procédure suivante crée une version C\# du traditionnel programme « Hello World ».  Le programme affiche la chaîne `Hello World!`  
  
 Pour obtenir plus d'exemples de concepts d'introduction, consultez [Mises en route de Visual Basic et Visual C\#](/visual-studio/ide/getting-started-with-visual-csharp-and-visual-basic).  
  
 [!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note-settings-general-md.md)]  
  
### Pour créer et exécuter une application console  
  
1.  Démarrez Visual Studio.  
  
2.  Dans la barre de menus, sélectionnez **Fichier**, **Nouveau**, **Projet**.  
  
     La boîte de dialogue **Nouveau projet** s'affiche.  
  
3.  Développez **Installé**, développez **Modèles**, développez **Visual C\#**, puis choisissez **Application console**.  
  
4.  Dans la zone **Nom**, indiquez un nom de projet, puis choisissez le bouton **OK**.  
  
     Le nouveau projet s'affiche dans l'**Explorateur de solutions**.  
  
5.  Si Program.cs n'est pas ouvert dans l'**Éditeur de code**, ouvrez le menu contextuel de **Program.cs** dans l'**Explorateur de solutions**, puis sélectionnez **Afficher le code**.  
  
6.  Remplacez le contenu de Program.cs par le code suivant.  
  
     [!code-cs[csProgGuide#21](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_1.cs)]  
  
7.  Sélectionnez la touche F5 pour exécuter le projet.  Une fenêtre d'invite de commandes s'affiche avec la ligne `Hello World!`  
  
 Ensuite, les parties importantes de ce programme sont examinées.  
  
## Commentaires  
 La première ligne contient un commentaire.  Les caractères `//` convertissent le reste de la ligne en commentaire.  
  
 [!code-cs[csProgGuide#32](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_2.cs)]  
  
 Vous pouvez également mettre en commentaire un bloc de texte en le plaçant entre les caractères `/*` et `*/`.  L'exemple suivant le démontre.  
  
 [!code-cs[csProgGuide#33](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_3.cs)]  
  
## Méthode Main  
 Une application console C\# doit contenir une méthode `Main`, dans laquelle le contrôle démarre et s'arrête.  La méthode `Main` est là où vous créez des objets et exécutez d'autres méthodes.  
  
 La méthode `Main` est une méthode [statiques](../../../csharp/language-reference/keywords/static.md) qui réside dans une classe ou un struct.  Dans l'exemple « Hello World\! » précédent, elle réside dans une classe nommée `Hello`.  Vous pouvez déclarer la méthode `Main` d'une des manières suivantes :  
  
-   Elle peut retourner `void` :  
  
     [!code-cs[csProgGuideMain#12](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_4.cs)]  
  
-   Il peut également retourner un entier.  
  
     [!code-cs[csProgGuideMain#13](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_5.cs)]  
  
-   Avec l'un des deux types de retour, elle peut accepter des arguments.  
  
     [!code-cs[csProgGuideMain#19](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_6.cs)]  
  
     ou  
  
     [!code-cs[csProgGuideMain#18](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_7.cs)]  
  
 Le paramètre de la méthode `Main` `args` est un tableau `string` qui contient les arguments de la ligne de commande utilisés pour appeler le programme.  Contrairement à C\+\+, le tableau n'inclut pas le nom du fichier exécutable \(exe\).  
  
 Pour plus d'informations sur l'utilisation d'arguments de ligne de commande, consultez les exemples figurant dans [Main\(\) et arguments de ligne de commande](../../../csharp/programming-guide/main-and-command-args/main-and-command-line-arguments.md) et [Comment : créer et utiliser des assemblys à l’aide de la ligne de commande](../Topic/How%20to:%20Create%20and%20Use%20Assemblies%20Using%20the%20Command%20Line%20\(C%23%20and%20Visual%20Basic\).md).  
  
 L'appel à <xref:System.Console.ReadKey%2A> à la fin de la méthode `Main` empêche la fenêtre de console de se fermer avant que vous n'ayez pu lire la sortie, lorsque vous exécutez votre programme en mode débogage en appuyant sur F5.  
  
## Entrées et sorties  
 Les programmes C\# utilisent généralement les services d'entrée\/sortie fournis par la bibliothèque runtime du .NET Framework.  L'instruction `System.Console.WriteLine("Hello World!");` utilise la méthode <xref:System.Console.WriteLine%2A>.  C'est l'une des méthodes de sortie de la classe <xref:System.Console> dans la bibliothèque Runtime.  Elle affiche son paramètre chaîne sur le flux de sortie standard suivi d'une nouvelle ligne.  D'autres méthodes <xref:System.Console> sont disponibles pour différentes opérations d'entrée et de sortie.  Si vous insérez la directive `using System;` au début du programme, vous pouvez utiliser directement les classes et les méthodes <xref:System> sans les qualifier complètement.  Par exemple, vous pouvez appeler `Console.WriteLine` au lieu de `System.Console.WriteLine` :  
  
 [!code-cs[csProgGuide#1](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_8.cs)]  
  
 [!code-cs[csProgGuide#23](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/hello-world-your-first-program_9.cs)]  
  
 Pour plus d'informations sur les méthodes d'entrée\/de sortie, consultez <xref:System.IO>.  
  
## Compilation et exécution de ligne de commande  
 Vous pouvez compiler le programme « Hello, World\! » en utilisant la ligne de commande à la place d'environnement de développement intégré \(IDE, Integrated Development Environment\) Visual Studio.  
  
#### Pour compiler et exécuter à partir d'une invite de commandes  
  
1.  Collez le code affiché dans la procédure précédente dans n'importe quel éditeur de texte et enregistrez le fichier sous forme de fichier texte.  Nommez le fichier `Hello.cs`.  Les fichiers du code source C\# portent l'extension `.cs`.  
  
2.  Effectuez l'une des étapes suivantes pour ouvrir une fenêtre d'invite de commandes :  
  
    -   Dans Windows 8, dans l'écran d'**accueil**, recherchez `Invite de commandes développeur`, puis cliquez ou choisissez **Invite de commandes développeur pour VS2012**.  
  
         Une fenêtre Invite de commandes de développeur apparaît.  
  
    -   Dans Windows 7, ouvrez le menu **Démarrer**, développez le dossier de la version actuelle de Visual Studio, ouvrez le menu contextuel de **Visual Studio Tools**, puis choisissez **Invite de commandes développeur pour VS2012**.  
  
         Une fenêtre Invite de commandes de développeur apparaît.  
  
    -   Vérifier les générations à partir de la ligne de commande dans la fenêtre d'invite de commandes standard.  
  
         Consultez [How to: Set Environment Variables for the Visual Studio Command Line](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md).  
  
3.  Dans la fenêtre d'invite de commandes, accédez au dossier qui contient votre fichier `Hello.cs`.  
  
4.  Entrez la commande suivante pour compiler `Hello.cs`.  
  
     `csc Hello.cs`  
  
     Si votre programme n'a pas d'erreurs de compilation, un fichier exécutable nommé `Hello.exe` est créé.  
  
5.  Dans la fenêtre d'invite de commandes, entrez la commande suivante pour exécuter la programme :  
  
     `Hello`  
  
 Pour plus d'informations sur le compilateur C\# et ses options, consultez [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md).  
  
## Chapitre proposé  
 [Écriture d'un programme C\#](http://go.microsoft.com/fwlink/?LinkId=221227) dans [Démarrage de Visual C\# 2010](http://go.microsoft.com/fwlink/?LinkId=221214)  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [À l'intérieur d'un programme C\#](../../../csharp/programming-guide/inside-a-program/index.md)   
 [Chaînes](../../../csharp/programming-guide/strings/index.md)   
 [\<paveover\>C\# Sample Applications](http://msdn.microsoft.com/fr-fr/9a9d7aaa-51d3-4224-b564-95409b0f3e15)   
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Main\(\) et arguments de ligne de commande](../../../csharp/programming-guide/main-and-command-args/main-and-command-line-arguments.md)   
 [Mises en route de Visual Basic et Visual C\#](/visual-studio/ide/getting-started-with-visual-csharp-and-visual-basic)