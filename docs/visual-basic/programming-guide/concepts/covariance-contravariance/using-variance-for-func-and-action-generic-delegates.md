---
title: "Utilisation de la Variance pour Func et Action de délégués génériques (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 36c3012f-b39c-493b-b90f-079b5912ac1b
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b8f9b2ebf758bc0d67b2b623038a4beeb7149261
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="using-variance-for-func-and-action-generic-delegates-visual-basic"></a><span data-ttu-id="f3e0a-102">Utilisation de la Variance pour Func et Action de délégués génériques (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f3e0a-102">Using Variance for Func and Action Generic Delegates (Visual Basic)</span></span>
<span data-ttu-id="f3e0a-103">Ces exemples montrent comment utiliser la covariance et la contravariance dans les délégués génériques `Func` et `Action` pour permettre de réutiliser des méthodes et fournir davantage de flexibilité dans votre code.</span><span class="sxs-lookup"><span data-stu-id="f3e0a-103">These examples demonstrate how to use covariance and contravariance in the `Func` and `Action` generic delegates to enable reuse of methods and provide more flexibility in your code.</span></span>  
  
 <span data-ttu-id="f3e0a-104">Pour plus d’informations sur la covariance et contravariance, consultez [Variance dans les délégués (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="f3e0a-104">For more information about covariance and contravariance, see [Variance in Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md).</span></span>  
  
## <a name="using-delegates-with-covariant-type-parameters"></a><span data-ttu-id="f3e0a-105">Utilisation des délégués avec les paramètres de type covariant</span><span class="sxs-lookup"><span data-stu-id="f3e0a-105">Using Delegates with Covariant Type Parameters</span></span>  
 <span data-ttu-id="f3e0a-106">L’exemple suivant illustre les avantages de la prise en charge de la covariance dans les délégués génériques `Func`.</span><span class="sxs-lookup"><span data-stu-id="f3e0a-106">The following example illustrates the benefits of covariance support in the generic `Func` delegates.</span></span> <span data-ttu-id="f3e0a-107">La méthode `FindByTitle` prend un paramètre de type `String` et retourne un objet de type `Employee`.</span><span class="sxs-lookup"><span data-stu-id="f3e0a-107">The `FindByTitle` method takes a parameter of the `String` type and returns an object of the `Employee` type.</span></span> <span data-ttu-id="f3e0a-108">Toutefois, vous pouvez assigner cette méthode au délégué `Func(Of String, Person)`, car `Employee` hérite de `Person`.</span><span class="sxs-lookup"><span data-stu-id="f3e0a-108">However, you can assign this method to the `Func(Of String, Person)` delegate because `Employee` inherits `Person`.</span></span>  
  
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
  
## <a name="using-delegates-with-contravariant-type-parameters"></a><span data-ttu-id="f3e0a-109">Utilisation des délégués avec les paramètres de type contravariant</span><span class="sxs-lookup"><span data-stu-id="f3e0a-109">Using Delegates with Contravariant Type Parameters</span></span>  
 <span data-ttu-id="f3e0a-110">L’exemple suivant illustre les avantages de la prise en charge de la contravariance dans les délégués génériques `Action`.</span><span class="sxs-lookup"><span data-stu-id="f3e0a-110">The following example illustrates the benefits of contravariance support in the generic `Action` delegates.</span></span> <span data-ttu-id="f3e0a-111">La méthode `AddToContacts` prend un paramètre de type `Person`.</span><span class="sxs-lookup"><span data-stu-id="f3e0a-111">The `AddToContacts` method takes a parameter of the `Person` type.</span></span> <span data-ttu-id="f3e0a-112">Toutefois, vous pouvez assigner cette méthode au délégué `Action(Of Employee)`, car `Employee` hérite de `Person`.</span><span class="sxs-lookup"><span data-stu-id="f3e0a-112">However, you can assign this method to the `Action(Of Employee)` delegate because `Employee` inherits `Person`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f3e0a-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f3e0a-113">See Also</span></span>  
 [<span data-ttu-id="f3e0a-114">Covariance et contravariance (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f3e0a-114">Covariance and Contravariance (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/index.md)  
 [<span data-ttu-id="f3e0a-115">Génériques</span><span class="sxs-lookup"><span data-stu-id="f3e0a-115">Generics</span></span>](~/docs/standard/generics/index.md)
