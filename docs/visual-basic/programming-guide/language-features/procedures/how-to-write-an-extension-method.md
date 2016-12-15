---
title: "How to: Write an Extension Method (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "extending data types"
  - "writing extension methods"
  - "extension methods [Visual Basic]"
ms.assetid: fb2739cc-958d-4ef4-a38b-214a74c93413
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Write an Extension Method (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Les méthodes d'extension vous permettent d'ajouter des méthodes à une classe existante.  La méthode d'extension peut être appelée comme s'il s'agissait d'une instance de cette classe.  
  
### Pour définir une méthode d'extension  
  
1.  Ouvrez une application Visual Basic nouvelle ou existante dans Visual Studio.  
  
2.  En haut du fichier dans lequel vous souhaitez définir une méthode d'extension, incluez l'instruction Import suivante :  
  
    ```  
    Imports System.Runtime.CompilerServices  
    ```  
  
3.  Dans un module de votre application nouvelle ou existante, commencez la définition de méthode par l'attribut d'extension :  
  
    ```  
    <Extension()>  
    ```  
  
4.  Déclarez votre méthode de la façon habituelle, le type du premier paramètre doit toutefois être le type de données que vous souhaitez étendre.  
  
    ```  
    <Extension()>   
    Public Sub subName (ByVal para1 As ExtendedType, <other parameters>)  
         ' < Body of the method >  
    End Sub  
    ```  
  
## Exemple  
 L'exemple suivant déclare une méthode d'extension dans le module `StringExtensions`.  Un deuxième module, `Module1`, importe `StringExtensions` et appelle la méthode.  La méthode d'extension doit se trouver dans la portée lorsqu'elle est appelée.  La méthode d'extension `PrintAndPunctuate` étend la classe <xref:System.String> avec une méthode qui affiche l'instance de chaîne suivie d'une chaîne de symboles de ponctuation envoyée en tant que paramètre.  
  
```vb#  
' Declarations will typically be in a separate module.  
Imports System.Runtime.CompilerServices  
  
Module StringExtensions  
    <Extension()>   
    Public Sub PrintAndPunctuate(ByVal aString As String,   
                                 ByVal punc As String)  
        Console.WriteLine(aString & punc)  
    End Sub  
  
End Module  
```  
  
```vb#  
' Import the module that holds the extension method you want to use,   
' and call it.  
  
Imports ConsoleApplication2.StringExtensions  
  
Module Module1  
  
    Sub Main()  
        Dim example = "Hello"  
        example.PrintAndPunctuate("?")  
        example.PrintAndPunctuate("!!!!")  
    End Sub  
  
End Module  
  
```  
  
 Notez que la méthode est définie avec deux paramètres et est appelée avec un seul paramètre.  Le premier paramètre, `aString`, dans la définition de méthode est lié à `example`, l'instance de `String` qui appelle la méthode.  Le résultat de l'exemple est le suivant :  
  
 `Hello?`  
  
 `Hello!!!!`  
  
## Voir aussi  
 <xref:System.Runtime.CompilerServices.ExtensionAttribute>   
 [méthodes d'extension.](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)   
 [Module Statement](../../../../visual-basic/language-reference/statements/module-statement.md)   
 [Procedure Parameters and Arguments](../../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)   
 [Scope in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)