---
title: "Expression lambda ne sera pas être supprimée de ce gestionnaire d’événements | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc42326
- vbc42326
dev_langs:
- VB
helpviewer_keywords:
- BC42326
ms.assetid: 63214dc6-0112-4245-8ebf-7c9e8f5a5782
caps.latest.revision: 8
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
ms.openlocfilehash: 7afe8160a25130cd92722df527d9567192912292
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="lambda-expression-will-not-be-removed-from-this-event-handler"></a><span data-ttu-id="5ded1-102">L’expression lambda ne sera pas supprimée de ce gestionnaire d’événements</span><span class="sxs-lookup"><span data-stu-id="5ded1-102">Lambda expression will not be removed from this event handler</span></span>
<span data-ttu-id="5ded1-103">L’expression lambda ne sera pas supprimée de ce gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="5ded1-103">Lambda expression will not be removed from this event handler.</span></span> <span data-ttu-id="5ded1-104">Assignez l’expression lambda à une variable et utilisez la variable pour ajouter et supprimer l’événement.</span><span class="sxs-lookup"><span data-stu-id="5ded1-104">Assign the lambda expression to a variable and use the variable to add and remove the event.</span></span>  
  
 <span data-ttu-id="5ded1-105">Lorsque les expressions lambda sont utilisées avec les gestionnaires d’événements, vous ne voyez pas le comportement attendu.</span><span class="sxs-lookup"><span data-stu-id="5ded1-105">When lambda expressions are used with event handlers, you may not see the behavior you expect.</span></span> <span data-ttu-id="5ded1-106">Le compilateur génère une nouvelle méthode pour chaque définition d’expression lambda, même si elles sont identiques.</span><span class="sxs-lookup"><span data-stu-id="5ded1-106">The compiler generates a new method for each lambda expression definition, even if they are identical.</span></span> <span data-ttu-id="5ded1-107">Par conséquent, le code suivant affiche `False`.</span><span class="sxs-lookup"><span data-stu-id="5ded1-107">Therefore, the following code displays `False`.</span></span>  
  
```vb  
Module Module1  
  
    Sub Main()  
        Dim fun1 As ChangeInteger = Function(p As Integer) p + 1  
        Dim fun2 As ChangeInteger = Function(p As Integer) p + 1  
        Console.WriteLine(fun1 = fun2)  
    End Sub  
  
    Delegate Function ChangeInteger(ByVal x As Integer) As Integer  
  
End Module  
```  
  
 <span data-ttu-id="5ded1-108">Lorsque les expressions lambda sont utilisées avec les gestionnaires d’événements, cela peut entraîner des résultats inattendus.</span><span class="sxs-lookup"><span data-stu-id="5ded1-108">When lambda expressions are used with event handlers, this may cause unexpected results.</span></span> <span data-ttu-id="5ded1-109">Dans l’exemple suivant, l’expression lambda ajoutée par `AddHandler` n’est pas supprimé par la `RemoveHandler` instruction.</span><span class="sxs-lookup"><span data-stu-id="5ded1-109">In the following example, the lambda expression added by `AddHandler` is not removed by the `RemoveHandler` statement.</span></span>  
  
```vb  
Module Module1  
  
    Event ProcessInteger(ByVal x As Integer)  
  
    Sub Main()  
  
        ' The following line adds one listener to the event.  
        AddHandler ProcessInteger, Function(m As Integer) m  
  
        ' The following statement searches the current listeners   
        ' for a match to remove. However, this lambda is not the same  
        ' as the previous one, so nothing is removed.  
        RemoveHandler ProcessInteger, Function(m As Integer) m  
  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="5ded1-110">Par défaut, ce message est un avertissement.</span><span class="sxs-lookup"><span data-stu-id="5ded1-110">By default, this message is a warning.</span></span> <span data-ttu-id="5ded1-111">Pour plus d’informations sur le masquage des avertissements ou considérer les avertissements comme des erreurs, consultez la page [configuration d’avertissements en Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="5ded1-111">For more information about how to hide warnings or treat warnings as errors, see [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="5ded1-112">**ID d’erreur :** BC42326</span><span class="sxs-lookup"><span data-stu-id="5ded1-112">**Error ID:** BC42326</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5ded1-113">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="5ded1-113">To correct this error</span></span>  
  
-   <span data-ttu-id="5ded1-114">Pour éviter l’avertissement et supprimer l’expression lambda, assignez l’expression lambda à une variable et utilisez la variable à la fois dans le `AddHandler` et `RemoveHandler` instructions, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="5ded1-114">To avoid the warning and remove the lambda expression, assign the lambda expression to a variable and use the variable in both the `AddHandler` and `RemoveHandler` statements, as shown in the following example.</span></span>  
  
```vb  
Module Module1  
  
    Event ProcessInteger(ByVal x As Integer)  
  
    Dim PrintHandler As ProcessIntegerEventHandler  
  
    Sub Main()  
  
        ' Assign the lambda expression to a variable.  
        PrintHandler = Function(m As Integer) m  
  
        ' Use the variable to add the listener.  
        AddHandler ProcessInteger, PrintHandler  
  
        ' Use the variable again when you want to remove the listener.  
        RemoveHandler ProcessInteger, PrintHandler  
  
    End Sub  
End Module  
```  
  
## <a name="see-also"></a><span data-ttu-id="5ded1-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5ded1-115">See Also</span></span>  
 <span data-ttu-id="5ded1-116">[Expressions lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="5ded1-116">[Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md) </span></span>  
<span data-ttu-id="5ded1-117"> [Conversion simplifiée des délégués](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md) </span><span class="sxs-lookup"><span data-stu-id="5ded1-117"> [Relaxed Delegate Conversion](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md) </span></span>  
<span data-ttu-id="5ded1-118"> [Événements](../../../visual-basic/programming-guide/language-features/events/index.md)</span><span class="sxs-lookup"><span data-stu-id="5ded1-118"> [Events](../../../visual-basic/programming-guide/language-features/events/index.md)</span></span>
