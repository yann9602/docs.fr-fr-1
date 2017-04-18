---
title: "Utilisation de la Variance pour les délégués génériques Func et Action (Visual Basic) | Documents Microsoft"
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
ms.assetid: 36c3012f-b39c-493b-b90f-079b5912ac1b
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 28c3f84d21f9fbc7e57ba079461194acf7612add
ms.lasthandoff: 03/13/2017

---
# <a name="using-variance-for-func-and-action-generic-delegates-visual-basic"></a>Utilisation de la Variance pour les délégués Func et Action générique (Visual Basic)
Ces exemples montrent comment utiliser la covariance et contravariance dans les `Func` et `Action` des délégués génériques pour permettre la réutilisation des méthodes et fournir davantage de flexibilité dans votre code.  
  
 Pour plus d’informations sur la covariance et la contravariance, consultez [Variance dans les délégués (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).  
  
## <a name="using-delegates-with-covariant-type-parameters"></a>Utilisation des délégués avec les paramètres de Type Covariant  
 L’exemple suivant illustre les avantages de la prise en charge de la covariance dans le générique `Func` délégués. Le `FindByTitle` méthode prend un paramètre de la `String` type et retourne un objet de la `Employee` type. Toutefois, vous pouvez assigner cette méthode pour le `Func(Of String, Person)` délégué, car `Employee` hérite `Person`.  
  
```vb  
' Simple hierarchy of classes.  
Public Class Person  
End Class  
  
Public Class Employee  
    Inherits Person  
End Class  
  
Class Finder  
    Public Shared Function FindByTitle(  
        ByVal title As String) As Employee  
        ' This is a stub for a method that returns  
        ' an employee that has the specified title.  
        Return New Employee  
    End Function  
  
    Sub Test()  
        ' Create an instance of the delegate without using variance.  
        Dim findEmployee As Func(Of String, Employee) =  
            AddressOf FindByTitle  
  
        ' The delegate expects a method to return Person,  
        ' but you can assign it a method that returns Employee.  
        Dim findPerson As Func(Of String, Person) =  
            AddressOf FindByTitle  
  
        ' You can also assign a delegate   
        ' that returns a more derived type to a delegate   
        ' that returns a less derived type.  
        findPerson = findEmployee  
    End Sub  
End Class  
```  
  
## <a name="using-delegates-with-contravariant-type-parameters"></a>Utilisation des délégués avec les paramètres de Type Contravariant  
 L’exemple suivant illustre les avantages de la prise en charge de la contravariance dans les génériques `Action` délégués. Le `AddToContacts` méthode prend un paramètre de la `Person` type. Toutefois, vous pouvez assigner cette méthode pour le `Action(Of Employee)` délégué, car `Employee` hérite `Person`.  
  
```vb  
Public Class Person  
End Class  
  
Public Class Employee  
    Inherits Person  
End Class  
  
Class AddressBook  
    Shared Sub AddToContacts(ByVal person As Person)  
        ' This method adds a Person object  
        ' to a contact list.  
    End Sub  
  
    Sub Test()  
        ' Create an instance of the delegate without using variance.  
        Dim addPersonToContacts As Action(Of Person) =  
            AddressOf AddToContacts  
  
        ' The Action delegate expects   
        ' a method that has an Employee parameter,  
        ' but you can assign it a method that has a Person parameter  
        ' because Employee derives from Person.  
        Dim addEmployeeToContacts As Action(Of Employee) =  
            AddressOf AddToContacts  
  
        ' You can also assign a delegate   
        ' that accepts a less derived parameter   
        ' to a delegate that accepts a more derived parameter.  
        addEmployeeToContacts = addPersonToContacts  
    End Sub  
End Class  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Covariance et Contravariance (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/covariance-and-contravariance.md)   
 [Génériques](https://msdn.microsoft.com/library/ms172192)
