---
title: "Comment : appeler une méthode déléguée (Visual Basic) | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
ms.assetid: b56866ae-abf9-4a5a-a855-486359455e9c
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 060a60da16a0032850b0a45822c8fd24b4622b83
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-invoke-a-delegate-method-visual-basic"></a><span data-ttu-id="bf686-102">Comment : appeler une méthode déléguée (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bf686-102">How to: Invoke a Delegate Method (Visual Basic)</span></span>
<span data-ttu-id="bf686-103">Cet exemple montre comment associer une méthode à un délégué, puis appeler cette méthode par le biais du délégué.</span><span class="sxs-lookup"><span data-stu-id="bf686-103">This example shows how to associate a method with a delegate and then invoke that method through the delegate.</span></span>  
  
### <a name="create-the-delegate-and-matching-procedures"></a><span data-ttu-id="bf686-104">Création du délégué et les procédures correspondantes</span><span class="sxs-lookup"><span data-stu-id="bf686-104">Create the delegate and matching procedures</span></span>  
  
1.  <span data-ttu-id="bf686-105">Créez un délégué nommé `MySubDelegate`.</span><span class="sxs-lookup"><span data-stu-id="bf686-105">Create a delegate named `MySubDelegate`.</span></span>  
  
    ```  
    Delegate Sub MySubDelegate(ByVal x As Integer)  
    ```  
  
2.  <span data-ttu-id="bf686-106">Déclarez une classe qui contient une méthode avec la même signature que le délégué.</span><span class="sxs-lookup"><span data-stu-id="bf686-106">Declare a class that contains a method with the same signature as the delegate.</span></span>  
  
    ```  
    Class class1  
        Sub Sub1(ByVal x As Integer)  
            MsgBox("The value of x is: " & CStr(x))  
        End Sub  
    End Class  
    ```  
  
3.  <span data-ttu-id="bf686-107">Définissez une méthode qui crée une instance du délégué et appelle la méthode associée au délégué en appelant intégré `Invoke` méthode.</span><span class="sxs-lookup"><span data-stu-id="bf686-107">Define a method that creates an instance of the delegate and invokes the method associated with the delegate by calling the built-in `Invoke` method.</span></span>  
  
    ```  
    Protected Sub DelegateTest()  
        Dim c1 As New class1  
        ' Create an instance of the delegate.  
        Dim msd As MySubDelegate = AddressOf c1.Sub1  
        ' Call the method.  
        msd.Invoke(10)  
    End Sub  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="bf686-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bf686-108">See Also</span></span>  
 <span data-ttu-id="bf686-109">[Delegate, instruction](../../../../visual-basic/language-reference/statements/delegate-statement.md) </span><span class="sxs-lookup"><span data-stu-id="bf686-109">[Delegate Statement](../../../../visual-basic/language-reference/statements/delegate-statement.md) </span></span>  
<span data-ttu-id="bf686-110"> [Délégués](../../../../visual-basic/programming-guide/language-features/delegates/index.md) </span><span class="sxs-lookup"><span data-stu-id="bf686-110"> [Delegates](../../../../visual-basic/programming-guide/language-features/delegates/index.md) </span></span>  
<span data-ttu-id="bf686-111"> [Événements](../../../../visual-basic/programming-guide/language-features/events/index.md) </span><span class="sxs-lookup"><span data-stu-id="bf686-111"> [Events](../../../../visual-basic/programming-guide/language-features/events/index.md) </span></span>  
<span data-ttu-id="bf686-112"> [Applications multithread](http://msdn.microsoft.com/library/a06a1a56-dd16-44e8-bc01-2c2255511bc6)</span><span class="sxs-lookup"><span data-stu-id="bf686-112"> [Multithreaded Applications](http://msdn.microsoft.com/library/a06a1a56-dd16-44e8-bc01-2c2255511bc6)</span></span>
