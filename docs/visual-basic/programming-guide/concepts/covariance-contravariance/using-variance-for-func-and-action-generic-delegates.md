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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: b4dc4a162d3562b218a448653cb51473fff4165a
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="using-variance-for-func-and-action-generic-delegates-visual-basic"></a><span data-ttu-id="3926b-102">Utilisation de la Variance pour les délégués Func et Action générique (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3926b-102">Using Variance for Func and Action Generic Delegates (Visual Basic)</span></span>
<span data-ttu-id="3926b-103">Ces exemples montrent comment utiliser la covariance et contravariance dans les `Func` et `Action` des délégués génériques pour permettre la réutilisation des méthodes et fournir davantage de flexibilité dans votre code.</span><span class="sxs-lookup"><span data-stu-id="3926b-103">These examples demonstrate how to use covariance and contravariance in the `Func` and `Action` generic delegates to enable reuse of methods and provide more flexibility in your code.</span></span>  
  
 <span data-ttu-id="3926b-104">Pour plus d’informations sur la covariance et la contravariance, consultez [Variance dans les délégués (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="3926b-104">For more information about covariance and contravariance, see [Variance in Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).</span></span>  
  
## <a name="using-delegates-with-covariant-type-parameters"></a><span data-ttu-id="3926b-105">Utilisation des délégués avec les paramètres de Type Covariant</span><span class="sxs-lookup"><span data-stu-id="3926b-105">Using Delegates with Covariant Type Parameters</span></span>  
 <span data-ttu-id="3926b-106">L’exemple suivant illustre les avantages de la prise en charge de la covariance dans le générique `Func` délégués.</span><span class="sxs-lookup"><span data-stu-id="3926b-106">The following example illustrates the benefits of covariance support in the generic `Func` delegates.</span></span> <span data-ttu-id="3926b-107">Le `FindByTitle` méthode prend un paramètre de la `String` type et retourne un objet de la `Employee` type.</span><span class="sxs-lookup"><span data-stu-id="3926b-107">The `FindByTitle` method takes a parameter of the `String` type and returns an object of the `Employee` type.</span></span> <span data-ttu-id="3926b-108">Toutefois, vous pouvez assigner cette méthode pour le `Func(Of String, Person)` délégué, car `Employee` hérite `Person`.</span><span class="sxs-lookup"><span data-stu-id="3926b-108">However, you can assign this method to the `Func(Of String, Person)` delegate because `Employee` inherits `Person`.</span></span>  
  
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
  
## <a name="using-delegates-with-contravariant-type-parameters"></a><span data-ttu-id="3926b-109">Utilisation des délégués avec les paramètres de Type Contravariant</span><span class="sxs-lookup"><span data-stu-id="3926b-109">Using Delegates with Contravariant Type Parameters</span></span>  
 <span data-ttu-id="3926b-110">L’exemple suivant illustre les avantages de la prise en charge de la contravariance dans les génériques `Action` délégués.</span><span class="sxs-lookup"><span data-stu-id="3926b-110">The following example illustrates the benefits of contravariance support in the generic `Action` delegates.</span></span> <span data-ttu-id="3926b-111">Le `AddToContacts` méthode prend un paramètre de la `Person` type.</span><span class="sxs-lookup"><span data-stu-id="3926b-111">The `AddToContacts` method takes a parameter of the `Person` type.</span></span> <span data-ttu-id="3926b-112">Toutefois, vous pouvez assigner cette méthode pour le `Action(Of Employee)` délégué, car `Employee` hérite `Person`.</span><span class="sxs-lookup"><span data-stu-id="3926b-112">However, you can assign this method to the `Action(Of Employee)` delegate because `Employee` inherits `Person`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3926b-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3926b-113">See Also</span></span>  
 <span data-ttu-id="3926b-114">[Covariance et Contravariance (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/covariance-and-contravariance.md) </span><span class="sxs-lookup"><span data-stu-id="3926b-114">[Covariance and Contravariance (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/covariance-and-contravariance.md) </span></span>  
<span data-ttu-id="3926b-115"> [Génériques](https://msdn.microsoft.com/library/ms172192)</span><span class="sxs-lookup"><span data-stu-id="3926b-115"> [Generics](https://msdn.microsoft.com/library/ms172192)</span></span>
