---
title: "Comment : appeler une méthode d’extension (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- calling extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: df07750f-40f4-4c07-a79e-1113a27cfbea
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 25b5a86af15694e6f64f96a5d5d645a01f8f1f12
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-call-an-extension-method-visual-basic"></a>Comment : appeler une méthode d’extension (Visual Basic)
Méthodes d’extension permettent d’ajouter des méthodes à une classe existante. Après qu’une méthode d’extension est déclarée et placée dans la portée, vous pouvez l’appeler comme une méthode d’instance du type qu’il étend. Pour plus d’informations sur la façon d’écrire une méthode d’extension, consultez [Comment : écrire une méthode d’Extension](./how-to-write-an-extension-method.md).  
  
 Les instructions suivantes font référence à la méthode d’extension `PrintAndPunctuate`, qui affiche l’instance de chaîne qui l’appelle, suivie de la valeur envoyée pour le deuxième paramètre, `punc`.  
  
```vb  
Imports System.Runtime.CompilerServices  
  
Module StringExtensions  
    <Extension()>   
    Public Sub PrintAndPunctuate(ByVal aString As String,   
                                 ByVal punc As String)  
        Console.WriteLine(aString & punc)  
    End Sub  
  
End Module  
```  
  
 La méthode doit être dans la portée lorsqu’elle est appelée.  
  
### <a name="to-call-an-extension-method"></a>Pour appeler une méthode d’extension  
  
1.  Déclarez une variable qui a le type de données du premier paramètre de la méthode d’extension. Pour `PrintAndPunctuate`, vous devez un <xref:System.String> variable :  
  
    ```  
    Dim example = "Ready"  
    ```  
  
2.  Que la variable appellera la méthode d’extension, et sa valeur est liée au premier paramètre, `aString`. L’instruction d’appel suivante affichera `Ready?`.  
  
    ```  
    example.PrintAndPunctuate("?")  
    ```  
  
     Notez que l’appel à cette méthode d’extension ressemble à un appel à l’un de le <xref:System.String> les méthodes qui nécessitent un paramètre d’instance :  
  
    ```  
    example.EndsWith("dy")  
    example.IndexOf("R")  
    ```  
  
3.  Déclarez une autre variable de chaîne et appelez la méthode afin de vérifier qu’il fonctionne avec n’importe quelle chaîne.  
  
    ```  
    Dim example2 = " or not"  
    example2.PrintAndPunctuate("!!!")  
    ```  
  
     Le résultat de cette heure est : `or not!!!`.  
  
## <a name="example"></a>Exemple  
 Le code suivant est un exemple complet de la création et l’utilisation d’une méthode d’extension simple.  
  
```vb  
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
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique : écrire une méthode d’extension](./how-to-write-an-extension-method.md)  
 [Méthodes d’extension](./extension-methods.md)  
 [Portée dans Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
