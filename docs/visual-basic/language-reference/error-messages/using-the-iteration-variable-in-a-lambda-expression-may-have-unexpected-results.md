---
title: "Using the iteration variable in a lambda expression may have unexpected results | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc42324"
  - "bc42324"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC42324"
ms.assetid: b5c2c4bd-3b2a-4a73-aaeb-55728eb03b68
caps.latest.revision: 8
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 8
---
# Using the iteration variable in a lambda expression may have unexpected results
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

L'utilisation de la variable d'itération dans une expression lambda peut provoquer des résultats inattendus.À la place, créez une variable locale dans la boucle et assignez\-lui la valeur de la variable d'itération.  
  
 Cet avertissement apparaît lorsque vous utilisez une variable d'itération de la boucle dans une expression lambda déclarée à l'intérieur de la boucle.  Par exemple, l'exemple suivant entraîne l'affichage de l'avertissement.  
  
```vb#  
For i As Integer = 1 To 10  
    ' The warning is given for the use of i.  
    Dim exampleFunc As Func(Of Integer) = Function() i  
Next  
```  
  
 L'exemple suivant affiche les résultats inattendus qui peuvent se produire.  
  
```vb#  
Module Module1  
    Sub Main()  
        Dim array1 As Func(Of Integer)() = New Func(Of Integer)(4) {}  
  
        For i As Integer = 0 To 4  
            array1(i) = Function() i  
        Next  
  
        For Each funcElement In array1  
            System.Console.WriteLine(funcElement())  
        Next  
  
    End Sub  
End Module  
```  
  
 La boucle `For` crée un tableau d'expressions lambda où chacune retourne la variable de la valeur d'itération de la boucle `i`.  Lorsque les expressions lambda sont évaluées dans la boucle `For Each`, vous pouvez vous attendre à consulter 0, 1, 2, 3 et 4 affichés, les valeurs consécutives d' `i` dans la boucle `For`.  À la place, vous voyez la dernière valeur d' `i` affichée cinq fois :  
  
 `5`  
  
 `5`  
  
 `5`  
  
 `5`  
  
 `5`  
  
 Par défaut, ce message est un avertissement.  Pour plus d'informations sur le masquage des avertissements ou le traitement des avertissements en tant qu'erreurs, consultez [Configuration d'avertissements en Visual Basic](/visual-studio/ide/configuring-warnings-in-visual-basic).  
  
 **ID d'erreur :** BC42324  
  
### Pour corriger cette erreur  
  
-   Assignez la valeur de la variable d'itération à une variable locale et utilisez cette dernière dans l'expression lambda.  
  
    ```vb#  
    Module Module1  
        Sub Main()  
            Dim array1 As Func(Of Integer)() = New Func(Of Integer)(4) {}  
  
            For i As Integer = 0 To 4  
                Dim j = i  
                array1(i) = Function() j  
            Next  
  
            For Each funcElement In array1  
                System.Console.WriteLine(funcElement())  
            Next  
  
        End Sub  
    End Module  
    ```  
  
## Voir aussi  
 [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)