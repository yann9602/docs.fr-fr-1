---
title: "Délégué de la classe&lt;classname&gt;&quot; n’a aucun méthode Invoke, donc une expression de ce type ne peut pas être la cible d’un appel de méthode | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30220
- bc30220
dev_langs:
- VB
helpviewer_keywords:
- BC30220
ms.assetid: 6be0d61c-f2f9-4f9b-ab90-8871a0d7206d
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
ms.openlocfilehash: 54cd62bc2b4cafa89873728ba4e5b31c46f1aab1
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="delegate-class-39ltclassnamegt39-has-no-invoke-method-so-an-expression-of-this-type-cannot-be-the-target-of-a-method-call"></a><span data-ttu-id="e14da-102">Délégué de la classe&lt;classname&gt;' n’a aucun méthode Invoke, donc une expression de ce type ne peut pas être la cible d’un appel de méthode</span><span class="sxs-lookup"><span data-stu-id="e14da-102">Delegate class &#39;&lt;classname&gt;&#39; has no Invoke method, so an expression of this type cannot be the target of a method call</span></span>
<span data-ttu-id="e14da-103">Un appel à `Invoke` via un délégué a échoué, car `Invoke` n’est pas implémentée sur la classe déléguée.</span><span class="sxs-lookup"><span data-stu-id="e14da-103">A call to `Invoke` through a delegate has failed because `Invoke` is not implemented on the delegate class.</span></span>  
  
 <span data-ttu-id="e14da-104">**ID d’erreur :** BC30220</span><span class="sxs-lookup"><span data-stu-id="e14da-104">**Error ID:** BC30220</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e14da-105">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="e14da-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="e14da-106">Assurez-vous qu’une instance de la classe déléguée a été créée avec un `Dim` instruction et qu’une procédure a été attribuée à l’instance de délégué avec le `AddressOf` opérateur.</span><span class="sxs-lookup"><span data-stu-id="e14da-106">Ensure that an instance of the delegate class has been created with a `Dim` statement and that a procedure has been assigned to the delegate instance with the `AddressOf` operator.</span></span>  
  
2.  <span data-ttu-id="e14da-107">Recherchez le code qui implémente la classe déléguée et vérifiez qu’il implémente la `Invoke` procédure.</span><span class="sxs-lookup"><span data-stu-id="e14da-107">Locate the code that implements the delegate class and make sure it implements the `Invoke` procedure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e14da-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e14da-108">See Also</span></span>  
 <span data-ttu-id="e14da-109">[Délégués](../../../visual-basic/programming-guide/language-features/delegates/index.md) </span><span class="sxs-lookup"><span data-stu-id="e14da-109">[Delegates](../../../visual-basic/programming-guide/language-features/delegates/index.md) </span></span>  
<span data-ttu-id="e14da-110"> [Delegate, instruction](../../../visual-basic/language-reference/statements/delegate-statement.md) </span><span class="sxs-lookup"><span data-stu-id="e14da-110"> [Delegate Statement](../../../visual-basic/language-reference/statements/delegate-statement.md) </span></span>  
<span data-ttu-id="e14da-111"> [AddressOf (opérateur)](../../../visual-basic/language-reference/operators/addressof-operator.md) </span><span class="sxs-lookup"><span data-stu-id="e14da-111"> [AddressOf Operator](../../../visual-basic/language-reference/operators/addressof-operator.md) </span></span>  
<span data-ttu-id="e14da-112"> [Dim (instruction)](../../../visual-basic/language-reference/statements/dim-statement.md)</span><span class="sxs-lookup"><span data-stu-id="e14da-112"> [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md)</span></span>
