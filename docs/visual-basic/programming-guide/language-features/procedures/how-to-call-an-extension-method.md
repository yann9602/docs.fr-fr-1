---
title: "How to: Call an Extension Method (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "calling extension methods"
  - "extension methods [Visual Basic]"
ms.assetid: df07750f-40f4-4c07-a79e-1113a27cfbea
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 11
---
# How to: Call an Extension Method (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Les méthodes d'extension vous permettent d'ajouter des méthodes à une classe existante.  Après avoir déclaré et placer dans la portée une méthode d'extension, vous pouvez l'appeler comme une méthode d'instance du type qu'elle étend.  Pour plus d'informations sur l'écriture d'une méthode d'extension, consultez [How to: Write an Extension Method](../../../../visual-basic/programming-guide/language-features/procedures/how-to-write-an-extension-method.md).  
  
 Les instructions suivantes font référence à la méthode d'extension `PrintAndPunctuate`, qui affichera l'instance de chaîne qui l'appelle, suivie d'une valeur envoyée pour le deuxième paramètre, `punc`.  
  
```vb#  
Imports System.Runtime.CompilerServices  
  
Module StringExtensions  
    <Extension()>   
    Public Sub PrintAndPunctuate(ByVal aString As String,   
                                 ByVal punc As String)  
        Console.WriteLine(aString & punc)  
    End Sub  
  
End Module  
  
```  
  
 La méthode doit se trouver dans la portée lorsqu'elle est appelée.  
  
### Pour appeler une méthode d'extension  
  
1.  Déclarez une variable dont le type de données est celui du premier paramètre de la méthode d'extension.  Pour `PrintAndPunctuate`, vous avez besoin d'une variable <xref:System.String> :  
  
    ```  
    Dim example = "Ready"  
    ```  
  
2.  Cette variable appellera la méthode d'extension et sa valeur est liée au premier paramètre, `aString`.  L'instruction d'appel suivante affichera `Ready?`.  
  
    ```  
    example.PrintAndPunctuate("?")  
    ```  
  
     Notez que l'appel à cette méthode d'extension ressemble à un appel à une des méthodes d'instance <xref:System.String> qui nécessitent un paramètre :  
  
    ```  
    example.EndsWith("dy")  
    example.IndexOf("R")  
    ```  
  
3.  Déclarez une autre variable chaîne et appelez encore la méthode pour vérifier si elle fonctionne avec n'importe quelle chaîne.  
  
    ```  
    Dim example2 = " or not"  
    example2.PrintAndPunctuate("!!!")  
    ```  
  
     Cette fois\-ci, le résultat est : `or not!!!`.  
  
## Exemple  
 Le code suivant est un exemple complet de création et d'utilisation d'une méthode d'extension simple.  
  
```vb#  
Imports System.Runtime.CompilerServices  
Imports ConsoleApplication1.StringExtensions  
  
Module Module1  
  
    Sub Main()  
  
        Dim example = "Hello"  
        example.PrintAndPunctuate(".")  
        example.PrintAndPunctuate("!!!!")  
  
        Dim example2 = "Goodbye"  
        example2.PrintAndPunctuate("?")  
    End Sub  
  
    <Extension()>   
    Public Sub PrintAndPunctuate(ByVal aString As String,   
                                 ByVal punc As String)  
        Console.WriteLine(aString & punc)  
    End Sub  
End Module  
  
' Output:  
' Hello.  
' Hello!!!!  
' Goodbye?  
```  
  
## Voir aussi  
 [How to: Write an Extension Method](../../../../visual-basic/programming-guide/language-features/procedures/how-to-write-an-extension-method.md)   
 [méthodes d'extension.](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)   
 [Scope in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)