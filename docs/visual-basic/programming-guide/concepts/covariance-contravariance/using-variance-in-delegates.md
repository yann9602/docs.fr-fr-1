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
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 620fd61000e42d68f566e441d023d73a036000ae
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="using-variance-in-delegates-visual-basic"></a><span data-ttu-id="09415-102">Utilisation de la Variance dans les délégués (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="09415-102">Using Variance in Delegates (Visual Basic)</span></span>
<span data-ttu-id="09415-103">Lorsque vous assignez une méthode à un délégué, *covariance* et *contravariance* offrent une souplesse pour faire correspondre un type délégué avec une signature de méthode.</span><span class="sxs-lookup"><span data-stu-id="09415-103">When you assign a method to a delegate, *covariance* and *contravariance* provide flexibility for matching a delegate type with a method signature.</span></span> <span data-ttu-id="09415-104">La covariance autorise une méthode de type de retour qui est plus dérivé que celui défini dans le délégué.</span><span class="sxs-lookup"><span data-stu-id="09415-104">Covariance permits a method to have return type that is more derived than that defined in the delegate.</span></span> <span data-ttu-id="09415-105">La contravariance permet à une méthode qui a des types de paramètres qui sont moins dérivés que ceux du type délégué.</span><span class="sxs-lookup"><span data-stu-id="09415-105">Contravariance permits a method that has parameter types that are less derived than those in the delegate type.</span></span>  
  
## <a name="example-1-covariance"></a><span data-ttu-id="09415-106">Exemple 1 : Covariance</span><span class="sxs-lookup"><span data-stu-id="09415-106">Example 1: Covariance</span></span>  
  
### <a name="description"></a><span data-ttu-id="09415-107">Description</span><span class="sxs-lookup"><span data-stu-id="09415-107">Description</span></span>  
 <span data-ttu-id="09415-108">Cet exemple montre comment les délégués peuvent être utilisés avec les méthodes qui ont des types de retour dérivés du type de retour dans la signature du délégué.</span><span class="sxs-lookup"><span data-stu-id="09415-108">This example demonstrates how delegates can be used with methods that have return types that are derived from the return type in the delegate signature.</span></span> <span data-ttu-id="09415-109">Le type de données retourné par `DogsHandler` est de type `Dogs`, qui dérive de la `Mammals` type défini dans le délégué.</span><span class="sxs-lookup"><span data-stu-id="09415-109">The data type returned by `DogsHandler` is of type `Dogs`, which derives from the `Mammals` type that is defined in the delegate.</span></span>  
  
### <a name="code"></a><span data-ttu-id="09415-110">Code</span><span class="sxs-lookup"><span data-stu-id="09415-110">Code</span></span>  
  
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
  
## <a name="example-2-contravariance"></a><span data-ttu-id="09415-111">Exemple 2 : Contravariance</span><span class="sxs-lookup"><span data-stu-id="09415-111">Example 2: Contravariance</span></span>  
  
### <a name="description"></a><span data-ttu-id="09415-112">Description</span><span class="sxs-lookup"><span data-stu-id="09415-112">Description</span></span>  
 <span data-ttu-id="09415-113">Cet exemple montre comment les délégués peuvent être utilisés avec les méthodes qui ont des paramètres d’un type qui sont des types de base du type de paramètre de signature de délégué.</span><span class="sxs-lookup"><span data-stu-id="09415-113">This example demonstrates how delegates can be used with methods that have parameters of a type that are base types of the delegate signature parameter type.</span></span> <span data-ttu-id="09415-114">Avec la contravariance, vous pouvez utiliser un gestionnaire d’événements au lieu de gestionnaires séparés.</span><span class="sxs-lookup"><span data-stu-id="09415-114">With contravariance, you can use one event handler instead of separate handlers.</span></span> <span data-ttu-id="09415-115">Par exemple, vous pouvez créer un gestionnaire d’événements qui accepte un `EventArgs` paramètre d’entrée et l’utiliser avec un `Button.MouseClick` événement envoie un `MouseEventArgs` type comme paramètre et également avec un `TextBox.KeyDown` événement envoie un `KeyEventArgs` paramètre.</span><span class="sxs-lookup"><span data-stu-id="09415-115">For example, you can create an event handler that accepts an `EventArgs` input parameter and use it with a `Button.MouseClick` event that sends a `MouseEventArgs` type as a parameter, and also with a `TextBox.KeyDown` event that sends a `KeyEventArgs` parameter.</span></span>  
  
### <a name="code"></a><span data-ttu-id="09415-116">Code</span><span class="sxs-lookup"><span data-stu-id="09415-116">Code</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="09415-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="09415-117">See Also</span></span>  
 <span data-ttu-id="09415-118">[Variance dans les délégués (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) </span><span class="sxs-lookup"><span data-stu-id="09415-118">[Variance in Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) </span></span>  
<span data-ttu-id="09415-119"> [Utilisation de la Variance pour les délégués Func et Action générique (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)</span><span class="sxs-lookup"><span data-stu-id="09415-119"> [Using Variance for Func and Action Generic Delegates (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)</span></span>
