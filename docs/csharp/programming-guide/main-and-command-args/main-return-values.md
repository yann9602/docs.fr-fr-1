---
title: "Valeurs de retour Main() (Guide de programmation C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "Main (méthode C#), valeurs de retour"
ms.assetid: c2f5a1d8-1676-4bea-bc7e-44a97e72d5bc
caps.latest.revision: 20
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 20
---
# Valeurs de retour Main() (Guide de programmation C#)
La méthode `Main` peut retourner `void`.  
  
 [!code-cs[csProgGuideMain#12](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/main-return-values_1.cs)]  
  
 Elle peut également retourner `int` :  
  
 [!code-cs[csProgGuideMain#13](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/main-return-values_2.cs)]  
  
 Si la valeur de retour de `Main` n'est pas utilisée, retourner `void` autorise un code légèrement plus simple.  Toutefois, retourner un entier permet au programme de communiquer des informations d'état à d'autres programmes ou scripts qui appellent le fichier exécutable.  L'exemple suivant affiche la façon d'accéder à la valeur de retour de `Main`.  
  
## Exemple  
 Dans cet exemple, un fichier de commandes est utilisé pour exécuter un programme et tester la valeur de retour de la fonction `Main`.  Lorsqu'un programme est exécuté dans Windows, toute valeur retournée par la fonction `Main` est stockée dans une variable d'environnement appelée `ERRORLEVEL`.  Un fichier de commandes peut donc déterminer le résultat de l'exécution en inspectant la variable `ERRORLEVEL`.  Traditionnellement, une valeur de retour de zéro indique que l'exécution a réussi.  L'exemple suivant est un programme simple qui retourne la valeur zéro de la fonction `Main`.  Le zéro indique que le programme a fonctionné avec succès.  Enregistrez le programme en tant que MainReturnValTest.cs.  
  
 [!code-cs[csProgGuideMain#14](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/main-return-values_3.cs)]  
  
## Exemple  
 Étant donné que cet exemple utilise un fichier de commandes, il vaut mieux compiler le code d'une invite de commandes.  Suivez les instructions dans [How to: Set Environment Variables for the Visual Studio Command Line](../../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md) pour activer des générations en ligne de commande ou utilisez l'invite de commandes de Visual Studio, disponible dans le menu **Démarrer** sous **Visual Studio Tools**.  De l'invite de commandes, naviguez jusqu'au dossier dans lequel vous avez enregistré le programme.  La commande suivante compile MainReturnValTest.cs et produit le fichier exécutable MainReturnValTest.exe.  
  
 `csc MainReturnValTest.cs`  
  
 Ensuite, créez un fichier de commandes pour exécuter MainReturnValTest.exe et afficher le résultat.  Collez le code suivant dans un fichier texte et enregistrez\-le en tant que `test.bat` dans le dossier qui contient MainReturnValTest.cs et MainReturnValTest.exe.  Exécutez le fichier de commandes `test` en tapant ce qui suit à l'invite de commandes.  
  
 Étant donné que le code retourne zéro, le fichier de commandes signalera la réussite.  Toutefois, si vous modifiez MainReturnValTest.cs pour retourner une valeur différente de zéro et recompiler ensuite le programme, l'exécution suivante du fichier de commandes signalera la défaillance.  
  
```  
rem test.bat  
@echo off  
MainReturnValTest  
@if "%ERRORLEVEL%" == "0" goto good  
  
:fail  
    echo Execution Failed  
    echo return value = %ERRORLEVEL%  
    goto end  
  
:good  
    echo Execution succeeded  
    echo Return value = %ERRORLEVEL%  
    goto end  
  
:end  
```  
  
## Résultat de l'exemple  
 `Execution succeeded`  
  
 `Return value = 0`  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Main\(\) et arguments de ligne de commande](../../../csharp/programming-guide/main-and-command-args/main-and-command-line-arguments.md)   
 [Comment : afficher les arguments de ligne de commande](../../../csharp/programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)   
 [Comment : accéder à des arguments de ligne de commande à l'aide de foreach](../../../csharp/programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)