---
title: "Main Procedure in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Main"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Main procedure"
  - "Main method [Visual Basic]"
  - "main function"
ms.assetid: f0db283e-f283-4464-b521-b90858cc1b44
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# Main Procedure in Visual Basic
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Toutes les applications Visual Basic doivent contenir une procédure appelée `Main`.  Cette procédure sert de point de départ et de contrôle général de l'application.  .NET Framework appelle votre procédure `Main` lorsqu'il a chargé votre application et qu'il est prêt à lui passer le contrôle.  À moins que vous ne créiez une application Windows Forms, vous devez écrire la procédure `Main` pour les applications qui s'exécutent seules.  
  
 `Main` contient le code qui s'exécute en premier.  Dans `Main`, vous pouvez identifier le premier formulaire à être chargé lors du démarrage du programme, savoir si une copie de votre application s'exécute déjà sur le système, définir un ensemble de variables pour votre application ou ouvrir une base de données requise par l'application.  
  
## Conditions de la procédure Main  
 Un fichier qui s'exécute seul \(généralement avec l'extension .exe\) doit contenir une procédure `Main`.  Une bibliothèque \(par exemple avec l'extension .dll\) ne s'exécute pas toute seule et ne requiert pas de procédure `Main`.  Les conditions relatives à ces différents types de projet que vous pouvez créer sont les suivantes :  
  
-   Les applications console s'exécutent toutes seules et vous devez fournir au moins une procédure `Main`.  .  
  
-   Les applications Windows Forms s'exécutent toutes seules.  Toutefois, le compilateur Visual Basic génère automatiquement une procédure `Main` dans une telle application et vous n'avez pas besoin d'en écrire une.  
  
-   Les bibliothèques ne requièrent pas de procédure `Main`.  Celles\-ci comprennent les bibliothèques de contrôles Windows et les bibliothèques de contrôles Web.  Les applications Web sont déployées comme des bibliothèques de classes.  
  
## Déclaration de la procédure Main  
 Il existe quatre méthodes possibles pour déclarer la procédure `Main` :  Elle peut prendre ou non des arguments, retourner ou non une valeur.  
  
> [!NOTE]
>  Si vous déclarez la procédure `Main` dans une classe, vous devez utiliser le mot clé `Shared`.  Dans un module, la procédure `Main` n'a pas besoin d'être partagée \(`Shared`\).  
  
-   La méthode la plus simple consiste à déclarer une procédure `Sub` que ne prend pas d'arguments et ne retourne pas de valeur.  
  
    ```  
    Module mainModule  
        Sub Main()  
            MsgBox("The Main procedure is starting the application.")  
            ' Insert call to appropriate starting place in your code.  
            MsgBox("The application is terminating.")  
        End Sub  
    End Module  
    ```  
  
-   La procédure `Main` peut également retourner une valeur `Integer`, que le système d'exploitation utilise comme code de sortie du programme.  D'autres programmes peuvent tester ce code en examinant la valeur ERRORLEVEL Windows.  Pour retourner un code de sortie, vous devez déclarer `Main` comme une procédure `Function` et non comme une procédure `Sub`.  
  
    ```  
    Module mainModule  
        Function Main() As Integer  
            MsgBox("The Main procedure is starting the application.")  
            Dim returnValue As Integer = 0  
            ' Insert call to appropriate starting place in your code.  
            ' On return, assign appropriate value to returnValue.  
            ' 0 usually means successful completion.  
            MsgBox("The application is terminating with error level " &  
                 CStr(returnValue) & ".")  
            Return returnValue  
        End Function  
    End Module  
    ```  
  
-   `Main` peut également prendre comme argument un tableau `String`.  Chaque chaîne du tableau contient un des arguments de ligne de commande utilisés pour appeler le programme.  Vous pouvez réaliser diverses actions en fonction de leurs valeurs.  
  
    ```  
    Module mainModule  
        Function Main(ByVal cmdArgs() As String) As Integer  
            MsgBox("The Main procedure is starting the application.")  
            Dim returnValue As Integer = 0  
            ' See if there are any arguments.  
            If cmdArgs.Length > 0 Then  
                For argNum As Integer = 0 To UBound(cmdArgs, 1)  
                    ' Insert code to examine cmdArgs(argNum) and take  
                    ' appropriate action based on its value.  
                Next argNum  
            End If  
            ' Insert call to appropriate starting place in your code.  
            ' On return, assign appropriate value to returnValue.  
            ' 0 usually means successful completion.  
            MsgBox("The application is terminating with error level " &  
                 CStr(returnValue) & ".")  
            Return returnValue  
        End Function  
    End Module  
    ```  
  
-   Vous pouvez déclarer `Main` de sorte à examiner les arguments de ligne de commande, sans qu'elle ne retourne toutefois un code de sortie.  
  
    ```  
    Module mainModule  
        Sub Main(ByVal cmdArgs() As String)  
            MsgBox("The Main procedure is starting the application.")  
            Dim returnValue As Integer = 0  
            ' See if there are any arguments.  
            If cmdArgs.Length > 0 Then  
                For argNum As Integer = 0 To UBound(cmdArgs, 1)  
                    ' Insert code to examine cmdArgs(argNum) and take  
                    ' appropriate action based on its value.  
                Next argNum  
            End If  
            ' Insert call to appropriate starting place in your code.  
            MsgBox("The application is terminating.")  
        End Sub  
    End Module  
    ```  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>   
 <xref:System.Array.Length%2A>   
 <xref:Microsoft.VisualBasic.Information.UBound%2A>   
 [Structure of a Visual Basic Program](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)   
 [NIB: Visual Basic Version of Hello, World](http://msdn.microsoft.com/fr-fr/9d030b60-e148-4366-a462-69532f02294c)   
 [\/main](../../../visual-basic/reference/command-line-compiler/main.md)   
 [Shared](../../../visual-basic/language-reference/modifiers/shared.md)   
 [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md)   
 [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md)   
 [Integer Data Type](../../../visual-basic/language-reference/data-types/integer-data-type.md)   
 [String Data Type](../../../visual-basic/language-reference/data-types/string-data-type.md)