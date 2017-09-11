---
title: "Utilisation de la Variance dans les Interfaces pour les Collections génériques (Visual Basic) | Documents Microsoft"
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
ms.assetid: c867fcea-7462-4995-b9c5-542feec74036
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 86184c7de3fe16148bf954b16d703ca682216337
ms.contentlocale: fr-fr
ms.lasthandoff: 03/13/2017

---
# <a name="using-variance-in-interfaces-for-generic-collections-visual-basic"></a><span data-ttu-id="a639e-102">Utilisation de la Variance dans les Interfaces pour les Collections génériques (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a639e-102">Using Variance in Interfaces for Generic Collections (Visual Basic)</span></span>
<span data-ttu-id="a639e-103">Une interface covariante autorise ses méthodes à retourner des types plus dérivés que ceux spécifiés dans l’interface.</span><span class="sxs-lookup"><span data-stu-id="a639e-103">A covariant interface allows its methods to return more derived types than those specified in the interface.</span></span> <span data-ttu-id="a639e-104">Une interface contravariante autorise ses méthodes à accepter des paramètres de types moins dérivés que ceux spécifiés dans l’interface.</span><span class="sxs-lookup"><span data-stu-id="a639e-104">A contravariant interface allows its methods to accept parameters of less derived types than those specified in the interface.</span></span>  
  
 <span data-ttu-id="a639e-105">Dans .NET Framework 4, plusieurs interfaces existantes est devenu covariants et contravariant.</span><span class="sxs-lookup"><span data-stu-id="a639e-105">In .NET Framework 4, several existing interfaces became covariant and contravariant.</span></span> <span data-ttu-id="a639e-106">Ceux-ci incluent <xref:System.Collections.Generic.IEnumerable%601>et <xref:System.IComparable%601>.</xref:System.IComparable%601> </xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="a639e-106">These include <xref:System.Collections.Generic.IEnumerable%601> and <xref:System.IComparable%601>.</span></span> <span data-ttu-id="a639e-107">Cela vous permet de réutiliser des méthodes qui fonctionnent avec les collections génériques de types de base pour les collections de types dérivés.</span><span class="sxs-lookup"><span data-stu-id="a639e-107">This enables you to reuse methods that operate with generic collections of base types for collections of derived types.</span></span>  
  
 <span data-ttu-id="a639e-108">Pour obtenir la liste des variantes dans le .NET Framework, consultez [Variance dans les Interfaces génériques (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="a639e-108">For a list of variant interfaces in the .NET Framework, see [Variance in Generic Interfaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md).</span></span>  
  
## <a name="converting-generic-collections"></a><span data-ttu-id="a639e-109">Conversion de Collections génériques</span><span class="sxs-lookup"><span data-stu-id="a639e-109">Converting Generic Collections</span></span>  
 <span data-ttu-id="a639e-110">L’exemple suivant illustre les avantages de la prise en charge de la covariance dans le <xref:System.Collections.Generic.IEnumerable%601>interface.</xref:System.Collections.Generic.IEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="a639e-110">The following example illustrates the benefits of covariance support in the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="a639e-111">Le `PrintFullName` méthode accepte une collection de la `IEnumerable(Of Person)` type en tant que paramètre.</span><span class="sxs-lookup"><span data-stu-id="a639e-111">The `PrintFullName` method accepts a collection of the `IEnumerable(Of Person)` type as a parameter.</span></span> <span data-ttu-id="a639e-112">Toutefois, vous pouvez le réutiliser pour une collection de la `IEnumerable(Of Person)` type, car `Employee` hérite `Person`.</span><span class="sxs-lookup"><span data-stu-id="a639e-112">However, you can reuse it for a collection of the `IEnumerable(Of Person)` type because `Employee` inherits `Person`.</span></span>  
  
<span data-ttu-id="a639e-113"><CodeContentPlaceHolder>0</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="a639e-113"><CodeContentPlaceHolder>0</CodeContentPlaceHolder></span></span>  
## <a name="comparing-generic-collections"></a><span data-ttu-id="a639e-114">Comparaison de Collections génériques</span><span class="sxs-lookup"><span data-stu-id="a639e-114">Comparing Generic Collections</span></span>  
 <span data-ttu-id="a639e-115">L’exemple suivant illustre les avantages de la prise en charge de la contravariance dans les <xref:System.Collections.Generic.IComparer%601>interface.</xref:System.Collections.Generic.IComparer%601></span><span class="sxs-lookup"><span data-stu-id="a639e-115">The following example illustrates the benefits of contravariance support in the <xref:System.Collections.Generic.IComparer%601> interface.</span></span> <span data-ttu-id="a639e-116">La classe `PersonComparer` implémente l'interface `IComparer(Of Person)`.</span><span class="sxs-lookup"><span data-stu-id="a639e-116">The `PersonComparer` class implements the `IComparer(Of Person)` interface.</span></span> <span data-ttu-id="a639e-117">Toutefois, vous pouvez réutiliser cette classe pour comparer une séquence d’objets de la `Employee` type, car `Employee` hérite `Person`.</span><span class="sxs-lookup"><span data-stu-id="a639e-117">However, you can reuse this class to compare a sequence of objects of the `Employee` type because `Employee` inherits `Person`.</span></span>  
  
```vb  
' Simple hierarhcy of classes.  
Public Class Person  
    Public Property FirstName As String  
    Public Property LastName As String  
End Class  
  
Public Class Employee  
    Inherits Person  
End Class  
' The custom comparer for the Person type  
' with standard implementations of Equals()  
' and GetHashCode() methods.  
Class PersonComparer  
    Implements IEqualityComparer(Of Person)  
  
    Public Function Equals1(  
        ByVal x As Person,  
        ByVal y As Person) As Boolean _  
        Implements IEqualityComparer(Of Person).Equals  
  
        If x Is y Then Return True  
        If x Is Nothing OrElse y Is Nothing Then Return False  
        Return (x.FirstName = y.FirstName) AndAlso  
            (x.LastName = y.LastName)  
    End Function  
    Public Function GetHashCode1(  
        ByVal person As Person) As Integer _  
        Implements IEqualityComparer(Of Person).GetHashCode  
  
        If person Is Nothing Then Return 0  
        Dim hashFirstName =  
            If(person.FirstName Is Nothing,  
            0, person.FirstName.GetHashCode())  
        Dim hashLastName = person.LastName.GetHashCode()  
        Return hashFirstName Xor hashLastName  
    End Function  
End Class  
  
Sub Main()  
    Dim employees = New List(Of Employee) From {  
        New Employee With {.FirstName = "Michael", .LastName = "Alexander"},  
        New Employee With {.FirstName = "Jeff", .LastName = "Price"}  
    }  
  
    ' You can pass PersonComparer,   
    ' which implements IEqualityComparer(Of Person),  
    ' although the method expects IEqualityComparer(Of Employee)  
  
    Dim noduplicates As IEnumerable(Of Employee) = employees.Distinct(New PersonComparer())  
  
    For Each employee In noduplicates  
        Console.WriteLine(employee.FirstName & " " & employee.LastName)  
    Next  
End Sub  
```  
  
## <a name="see-also"></a><span data-ttu-id="a639e-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a639e-118">See Also</span></span>  
 [<span data-ttu-id="a639e-119">Variance dans les Interfaces génériques (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a639e-119">Variance in Generic Interfaces (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
