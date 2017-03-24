---
title: "Utilisation de la Variance dans les délégués (Visual Basic) | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 7b5c20f1-6416-46a3-94b6-f109c31c842c
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 5bd3e60031eac713cee3dee1399af8c6b83e6656
ms.lasthandoff: 03/13/2017

---
# <a name="using-variance-in-delegates-visual-basic"></a>Utilisation de la Variance dans les délégués (Visual Basic)
Lorsque vous assignez une méthode à un délégué, *covariance* et *contravariance* offrent une souplesse pour faire correspondre un type délégué avec une signature de méthode. La covariance autorise une méthode de type de retour qui est plus dérivé que celui défini dans le délégué. La contravariance permet à une méthode qui a des types de paramètres qui sont moins dérivés que ceux du type délégué.  
  
## <a name="example-1-covariance"></a>Exemple 1 : Covariance  
  
### <a name="description"></a>Description  
 Cet exemple montre comment les délégués peuvent être utilisés avec les méthodes qui ont des types de retour dérivés du type de retour dans la signature du délégué. Le type de données retourné par `DogsHandler` est de type `Dogs`, qui dérive de la `Mammals` type défini dans le délégué.  
  
### <a name="code"></a>Code  
  
```vb  
Class Mammals  
End Class  
  
Class Dogs  
    Inherits Mammals  
End Class  
Class Test  
    Public Delegate Function HandlerMethod() As Mammals  
    Public Shared Function MammalsHandler() As Mammals  
        Return Nothing  
    End Function  
    Public Shared Function DogsHandler() As Dogs  
        Return Nothing  
    End Function  
    Sub Test()  
        Dim handlerMammals As HandlerMethod = AddressOf MammalsHandler  
        ' Covariance enables this assignment.  
        Dim handlerDogs As HandlerMethod = AddressOf DogsHandler  
    End Sub  
End Class  
```  
  
## <a name="example-2-contravariance"></a>Exemple 2 : Contravariance  
  
### <a name="description"></a>Description  
 Cet exemple montre comment les délégués peuvent être utilisés avec les méthodes qui ont des paramètres d’un type qui sont des types de base du type de paramètre de signature de délégué. Avec la contravariance, vous pouvez utiliser un gestionnaire d’événements au lieu de gestionnaires séparés. Par exemple, vous pouvez créer un gestionnaire d’événements qui accepte un `EventArgs` paramètre d’entrée et l’utiliser avec un `Button.MouseClick` événement envoie un `MouseEventArgs` type comme paramètre et également avec un `TextBox.KeyDown` événement envoie un `KeyEventArgs` paramètre.  
  
### <a name="code"></a>Code  
  
```vb  
' Event hander that accepts a parameter of the EventArgs type.  
Private Sub MultiHandler(ByVal sender As Object,  
                         ByVal e As System.EventArgs)  
    Label1.Text = DateTime.Now  
End Sub  
  
Private Sub Form1_Load(ByVal sender As System.Object,  
    ByVal e As System.EventArgs) Handles MyBase.Load  
  
    ' You can use a method that has an EventArgs parameter,  
    ' although the event expects the KeyEventArgs parameter.  
    AddHandler Button1.KeyDown, AddressOf MultiHandler  
  
    ' You can use the same method   
    ' for the event that expects the MouseEventArgs parameter.  
    AddHandler Button1.MouseClick, AddressOf MultiHandler  
End Sub  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Variance dans les délégués (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)   
 [Utilisation de la Variance pour les délégués Func et Action générique (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
