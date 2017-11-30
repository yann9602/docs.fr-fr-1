---
title: "Opérateur AddressOf (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- AddressOf
- vb.AddressOf
helpviewer_keywords:
- AddressOf operator [Visual Basic]
- addresses, passing to API procedures
ms.assetid: 8105a59d-60d8-4ab5-b221-5899cdfacbf4
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 52560a2d9071373fd28f7aad2e485da08324656d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="addressof-operator-visual-basic"></a><span data-ttu-id="9db44-102">Opérateur AddressOf (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9db44-102">AddressOf Operator (Visual Basic)</span></span>
<span data-ttu-id="9db44-103">Crée une instance de délégué de procédure qui fait référence à la procédure spécifique.</span><span class="sxs-lookup"><span data-stu-id="9db44-103">Creates a procedure delegate instance that references the specific procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9db44-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9db44-104">Syntax</span></span>  
  
```  
AddressOf procedurename  
```  
  
## <a name="parts"></a><span data-ttu-id="9db44-105">Composants</span><span class="sxs-lookup"><span data-stu-id="9db44-105">Parts</span></span>  
 `procedurename`  
 <span data-ttu-id="9db44-106">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="9db44-106">Required.</span></span> <span data-ttu-id="9db44-107">Indique la procédure d’être référencées par le délégué de procédure nouvellement créé.</span><span class="sxs-lookup"><span data-stu-id="9db44-107">Specifies the procedure to be referenced by the newly created procedure delegate.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9db44-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="9db44-108">Remarks</span></span>  
 <span data-ttu-id="9db44-109">Le `AddressOf` opérateur crée un délégué de fonction qui pointe vers la fonction spécifiée par `procedurename`.</span><span class="sxs-lookup"><span data-stu-id="9db44-109">The `AddressOf` operator creates a function delegate that points to the function specified by `procedurename`.</span></span> <span data-ttu-id="9db44-110">Lorsque la procédure spécifiée est qu'une méthode d’instance puis le délégué de fonction fait référence à l’instance et de la méthode.</span><span class="sxs-lookup"><span data-stu-id="9db44-110">When the specified procedure is an instance method then the function delegate refers to both the instance and the method.</span></span> <span data-ttu-id="9db44-111">Ensuite, lorsque le délégué de fonction est appelé la méthode spécifiée de l’instance spécifiée est appelée.</span><span class="sxs-lookup"><span data-stu-id="9db44-111">Then, when the function delegate is invoked the specified method of the specified instance is called.</span></span>  
  
 <span data-ttu-id="9db44-112">Le `AddressOf` opérateur peut être utilisé comme opérande d’un constructeur délégué, ou il peut être utilisé dans un contexte dans lequel le type du délégué peut être déterminé par le compilateur.</span><span class="sxs-lookup"><span data-stu-id="9db44-112">The `AddressOf` operator can be used as the operand of a delegate constructor or it can be used in a context in which the type of the delegate can be determined by the compiler.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9db44-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="9db44-113">Example</span></span>  
 <span data-ttu-id="9db44-114">Cet exemple utilise le `AddressOf` opérateur pour désigner un délégué pour gérer les `Click` événements d’un bouton.</span><span class="sxs-lookup"><span data-stu-id="9db44-114">This example uses the `AddressOf` operator to designate a delegate to handle the `Click` event of a button.</span></span>  
  
 [!code-vb[VbVbalrDelegates#8](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addressof-operator_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="9db44-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="9db44-115">Example</span></span>  
 <span data-ttu-id="9db44-116">L’exemple suivant utilise le `AddressOf` opérateur pour désigner la fonction de démarrage d’un thread.</span><span class="sxs-lookup"><span data-stu-id="9db44-116">The following example uses the `AddressOf` operator to designate the startup function for a thread.</span></span>  
  
 [!code-vb[VbVbalrDelegates#9](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addressof-operator_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="9db44-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9db44-117">See Also</span></span>  
 [<span data-ttu-id="9db44-118">Declare (instruction)</span><span class="sxs-lookup"><span data-stu-id="9db44-118">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
 [<span data-ttu-id="9db44-119">Function (instruction)</span><span class="sxs-lookup"><span data-stu-id="9db44-119">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="9db44-120">Sub (instruction)</span><span class="sxs-lookup"><span data-stu-id="9db44-120">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="9db44-121">Délégués</span><span class="sxs-lookup"><span data-stu-id="9db44-121">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)
