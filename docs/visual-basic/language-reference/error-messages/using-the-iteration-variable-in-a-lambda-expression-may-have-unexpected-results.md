---
title: "À l’aide de la variable d’itération dans une expression lambda peut avoir des résultats inattendus | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc42324
- bc42324
dev_langs:
- VB
helpviewer_keywords:
- BC42324
ms.assetid: b5c2c4bd-3b2a-4a73-aaeb-55728eb03b68
caps.latest.revision: 8
author: stevehoag
ms.author: shoag
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 5b293ec344d816e40d369757fa4d11710b7ecd8d
ms.lasthandoff: 03/13/2017

---
# <a name="using-the-iteration-variable-in-a-lambda-expression-may-have-unexpected-results"></a>L’utilisation de la variable d’itération dans une expression lambda peut provoquer des résultats inattendus
L’utilisation d’une variable d’itération dans une expression lambda peut avoir des résultats inattendus. Au lieu de cela, créez une variable locale dans la boucle et assignez-lui la valeur de la variable d’itération.  
  
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
  
 Le `For` boucle crée un tableau d’expressions lambda où chacune retourne la valeur de la variable d’itération de boucle `i`. Lorsque les expressions lambda sont évaluées dans le `For Each` boucle, que vous attendez à voir 0, 1, 2, 3 et 4 affichés, les valeurs consécutives de `i` dans les `For` boucle. Au lieu de cela, vous voyez la valeur finale du `i` affichée cinq fois :  
  
 `5`  
  
 `5`  
  
 `5`  
  
 `5`  
  
 `5`  
  
 Par défaut, ce message est un avertissement. Pour plus d’informations sur le masquage des avertissements ou le traitement des avertissements comme des erreurs, consultez la page [configuration d’avertissements en Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
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
