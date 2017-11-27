---
title: "L’utilisation de la variable d’itération dans une expression lambda peut provoquer des résultats inattendus"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc42324
- bc42324
helpviewer_keywords: BC42324
ms.assetid: b5c2c4bd-3b2a-4a73-aaeb-55728eb03b68
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fb707cd4e09a149d21b70bb0f998a40c7ed58b49
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="using-the-iteration-variable-in-a-lambda-expression-may-have-unexpected-results"></a>L’utilisation de la variable d’itération dans une expression lambda peut provoquer des résultats inattendus
L’utilisation de la variable d’itération dans une expression lambda peut avoir des résultats inattendus. Au lieu de cela, créez une variable locale dans la boucle et assignez-lui la valeur de la variable d’itération.  
  
 Cet avertissement s’affiche lorsque vous utilisez une variable d’itération de boucle dans une expression lambda qui est déclarée à l’intérieur de la boucle. Par exemple, l’exemple suivant génère l’avertissement apparaît.  
  
```vb  
For i As Integer = 1 To 10  
    ' The warning is given for the use of i.  
    Dim exampleFunc As Func(Of Integer) = Function() i  
Next  
```  
  
 L’exemple suivant montre les résultats inattendus peuvent se produire.  
  
```vb  
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
  
 Le `For` boucle crée un tableau d’expressions lambda, chacun d’eux retourne la valeur de la variable d’itération de boucle `i`. Lorsque les expressions lambda sont évaluées dans le `For Each` boucle, vous pouvez vous attendre à voir 0, 1, 2, 3 et 4 affichés, les valeurs consécutives de `i` dans le `For` boucle. Au lieu de cela, vous voyez la valeur finale de `i` affiche cinq fois :  
  
 `5`  
  
 `5`  
  
 `5`  
  
 `5`  
  
 `5`  
  
 Par défaut, ce message est un avertissement. Pour plus d’informations sur le masquage des avertissements ou le traitement des avertissements en tant qu’erreurs, consultez [configuration des avertissements en Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID d’erreur :** BC42324  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Affecter la valeur de la variable d’itération à une variable locale et utilisez la variable locale dans l’expression lambda.  
  
```vb  
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
  
## <a name="see-also"></a>Voir aussi  
 [Expressions lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
