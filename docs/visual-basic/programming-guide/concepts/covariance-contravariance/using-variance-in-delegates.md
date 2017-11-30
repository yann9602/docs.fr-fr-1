---
title: "Utilisation de la Variance dans les délégués (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7b5c20f1-6416-46a3-94b6-f109c31c842c
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 435591d69e67c4fc4be8e781c5f63e025c71a8cf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="using-variance-in-delegates-visual-basic"></a><span data-ttu-id="3ea7e-102">Utilisation de la Variance dans les délégués (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3ea7e-102">Using Variance in Delegates (Visual Basic)</span></span>
<span data-ttu-id="3ea7e-103">Quand vous assignez une méthode à un délégué, la *covariance* et la *contravariance* offrent une grande flexibilité pour la mise en correspondance d’un type délégué avec une signature de méthode.</span><span class="sxs-lookup"><span data-stu-id="3ea7e-103">When you assign a method to a delegate, *covariance* and *contravariance* provide flexibility for matching a delegate type with a method signature.</span></span> <span data-ttu-id="3ea7e-104">La covariance permet à une méthode d’avoir un type de retour qui est plus dérivé que celui défini dans le délégué.</span><span class="sxs-lookup"><span data-stu-id="3ea7e-104">Covariance permits a method to have return type that is more derived than that defined in the delegate.</span></span> <span data-ttu-id="3ea7e-105">La contravariance autorise une méthode qui a des types de paramètres moins dérivés que ceux du type délégué.</span><span class="sxs-lookup"><span data-stu-id="3ea7e-105">Contravariance permits a method that has parameter types that are less derived than those in the delegate type.</span></span>  
  
## <a name="example-1-covariance"></a><span data-ttu-id="3ea7e-106">Exemple 1 : Covariance</span><span class="sxs-lookup"><span data-stu-id="3ea7e-106">Example 1: Covariance</span></span>  
  
### <a name="description"></a><span data-ttu-id="3ea7e-107">Description</span><span class="sxs-lookup"><span data-stu-id="3ea7e-107">Description</span></span>  
 <span data-ttu-id="3ea7e-108">Cet exemple montre comment vous pouvez utiliser des délégués avec des méthodes ayant des types de retour dérivés du type de retour dans la signature du délégué.</span><span class="sxs-lookup"><span data-stu-id="3ea7e-108">This example demonstrates how delegates can be used with methods that have return types that are derived from the return type in the delegate signature.</span></span> <span data-ttu-id="3ea7e-109">Le type de données retourné par `DogsHandler` est `Dogs`, qui dérive du type `Mammals` défini dans le délégué.</span><span class="sxs-lookup"><span data-stu-id="3ea7e-109">The data type returned by `DogsHandler` is of type `Dogs`, which derives from the `Mammals` type that is defined in the delegate.</span></span>  
  
### <a name="code"></a><span data-ttu-id="3ea7e-110">Code</span><span class="sxs-lookup"><span data-stu-id="3ea7e-110">Code</span></span>  
  
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
  
## <a name="example-2-contravariance"></a><span data-ttu-id="3ea7e-111">Exemple 2 : Contravariance</span><span class="sxs-lookup"><span data-stu-id="3ea7e-111">Example 2: Contravariance</span></span>  
  
### <a name="description"></a><span data-ttu-id="3ea7e-112">Description</span><span class="sxs-lookup"><span data-stu-id="3ea7e-112">Description</span></span>  
 <span data-ttu-id="3ea7e-113">Cet exemple montre comment vous pouvez utiliser des délégués avec des méthodes ayant des paramètres d’un type qui sont des types de base du type de paramètre de la signature de délégué.</span><span class="sxs-lookup"><span data-stu-id="3ea7e-113">This example demonstrates how delegates can be used with methods that have parameters of a type that are base types of the delegate signature parameter type.</span></span> <span data-ttu-id="3ea7e-114">Avec la contravariance, vous pouvez maintenant utiliser un gestionnaire d’événements plutôt que des gestionnaires distincts.</span><span class="sxs-lookup"><span data-stu-id="3ea7e-114">With contravariance, you can use one event handler instead of separate handlers.</span></span> <span data-ttu-id="3ea7e-115">Par exemple, vous pouvez créer un gestionnaire d’événements qui accepte un paramètre d’entrée `EventArgs` et l’utiliser avec un événement `Button.MouseClick` qui envoie un type `MouseEventArgs` comme paramètre, ainsi qu’avec un événement `TextBox.KeyDown` qui envoie un paramètre `KeyEventArgs`.</span><span class="sxs-lookup"><span data-stu-id="3ea7e-115">For example, you can create an event handler that accepts an `EventArgs` input parameter and use it with a `Button.MouseClick` event that sends a `MouseEventArgs` type as a parameter, and also with a `TextBox.KeyDown` event that sends a `KeyEventArgs` parameter.</span></span>  
  
### <a name="code"></a><span data-ttu-id="3ea7e-116">Code</span><span class="sxs-lookup"><span data-stu-id="3ea7e-116">Code</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3ea7e-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3ea7e-117">See Also</span></span>  
 [<span data-ttu-id="3ea7e-118">Variance dans les délégués (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3ea7e-118">Variance in Delegates (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)  
 [<span data-ttu-id="3ea7e-119">Utilisation de la variance pour les délégués génériques Func et Action (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3ea7e-119">Using Variance for Func and Action Generic Delegates (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
