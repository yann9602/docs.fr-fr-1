---
title: "Classe déléguée &#39; &lt;classname&gt;&#39; n’a aucun méthode Invoke, afin de l’expression de ce type ne peut pas être la cible d’un appel de méthode"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30220
- bc30220
helpviewer_keywords: BC30220
ms.assetid: 6be0d61c-f2f9-4f9b-ab90-8871a0d7206d
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 55d0e2442807e25737d90ac4b45a59b9d3e73037
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="delegate-class-39ltclassnamegt39-has-no-invoke-method-so-an-expression-of-this-type-cannot-be-the-target-of-a-method-call"></a><span data-ttu-id="7c444-102">Classe déléguée &#39; &lt;classname&gt;&#39; n’a aucun méthode Invoke, afin de l’expression de ce type ne peut pas être la cible d’un appel de méthode</span><span class="sxs-lookup"><span data-stu-id="7c444-102">Delegate class &#39;&lt;classname&gt;&#39; has no Invoke method, so an expression of this type cannot be the target of a method call</span></span>
<span data-ttu-id="7c444-103">Un appel à `Invoke` via un délégué a échoué, car `Invoke` n’est pas implémentée sur la classe déléguée.</span><span class="sxs-lookup"><span data-stu-id="7c444-103">A call to `Invoke` through a delegate has failed because `Invoke` is not implemented on the delegate class.</span></span>  
  
 <span data-ttu-id="7c444-104">**ID d’erreur :** BC30220</span><span class="sxs-lookup"><span data-stu-id="7c444-104">**Error ID:** BC30220</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7c444-105">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="7c444-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="7c444-106">Assurez-vous qu’une instance de la classe déléguée a été créée avec un `Dim` instruction et qu’une procédure a été assignée à l’instance de délégué avec le `AddressOf` opérateur.</span><span class="sxs-lookup"><span data-stu-id="7c444-106">Ensure that an instance of the delegate class has been created with a `Dim` statement and that a procedure has been assigned to the delegate instance with the `AddressOf` operator.</span></span>  
  
2.  <span data-ttu-id="7c444-107">Recherchez le code qui implémente la classe déléguée et vérifiez qu’il implémente la `Invoke` procédure.</span><span class="sxs-lookup"><span data-stu-id="7c444-107">Locate the code that implements the delegate class and make sure it implements the `Invoke` procedure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c444-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7c444-108">See Also</span></span>  
 [<span data-ttu-id="7c444-109">Délégués</span><span class="sxs-lookup"><span data-stu-id="7c444-109">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [<span data-ttu-id="7c444-110">Delegate (instruction)</span><span class="sxs-lookup"><span data-stu-id="7c444-110">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
 [<span data-ttu-id="7c444-111">AddressOf (opérateur)</span><span class="sxs-lookup"><span data-stu-id="7c444-111">AddressOf Operator</span></span>](../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [<span data-ttu-id="7c444-112">Dim (instruction)</span><span class="sxs-lookup"><span data-stu-id="7c444-112">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)
