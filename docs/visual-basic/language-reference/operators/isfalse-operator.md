---
title: "Opérateur IsFalse (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.isfalse
helpviewer_keywords:
- AndAlso operator [Visual Basic]
- IsFalse operator [Visual Basic]
ms.assetid: 37fc9dbf-e5cc-4570-b93f-7213447974df
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d85fc51a75f82c65cf226b8239a8eee6585bd18a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="isfalse-operator-visual-basic"></a><span data-ttu-id="1fd25-102">Opérateur IsFalse (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1fd25-102">IsFalse Operator (Visual Basic)</span></span>
<span data-ttu-id="1fd25-103">Détermine si une expression est `False`.</span><span class="sxs-lookup"><span data-stu-id="1fd25-103">Determines whether an expression is `False`.</span></span>  
  
 <span data-ttu-id="1fd25-104">Vous ne pouvez pas appeler `IsFalse` explicitement dans votre code, mais Visual Basic compilateur peut l’utiliser pour générer le code à partir de `AndAlso` clauses.</span><span class="sxs-lookup"><span data-stu-id="1fd25-104">You cannot call `IsFalse` explicitly in your code, but the Visual Basic compiler can use it to generate code from `AndAlso` clauses.</span></span> <span data-ttu-id="1fd25-105">Si vous définissez une classe ou une structure et ensuite utiliser une variable de ce type dans un `AndAlso` clause, vous devez définir `IsFalse` sur cette classe ou structure.</span><span class="sxs-lookup"><span data-stu-id="1fd25-105">If you define a class or structure and then use a variable of that type in an `AndAlso` clause, you must define `IsFalse` on that class or structure.</span></span>  
  
 <span data-ttu-id="1fd25-106">Le compilateur considère la `IsFalse` et `IsTrue` opérateurs comme un *paire équilibrée*.</span><span class="sxs-lookup"><span data-stu-id="1fd25-106">The compiler considers the `IsFalse` and `IsTrue` operators as a *matched pair*.</span></span> <span data-ttu-id="1fd25-107">Cela signifie que si vous définissez un d’eux, vous devez également définir la deuxième.</span><span class="sxs-lookup"><span data-stu-id="1fd25-107">This means that if you define one of them, you must also define the other one.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1fd25-108">Le `IsFalse` opérateur peut être *surchargé*, ce qui signifie qu’une classe ou structure peut redéfinir son comportement lorsque son opérande a le type de cette classe ou structure.</span><span class="sxs-lookup"><span data-stu-id="1fd25-108">The `IsFalse` operator can be *overloaded*, which means that a class or structure can redefine its behavior when its operand has the type of that class or structure.</span></span> <span data-ttu-id="1fd25-109">Si votre code utilise cet opérateur sur une telle classe ou structure, assurez-vous que vous comprenez son comportement redéfini.</span><span class="sxs-lookup"><span data-stu-id="1fd25-109">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="1fd25-110">Pour plus d’informations, consultez [procédures d’opérateur](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="1fd25-110">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1fd25-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="1fd25-111">Example</span></span>  
 <span data-ttu-id="1fd25-112">L’exemple de code suivant définit le plan d’une structure qui contient les définitions pour la `IsFalse` et `IsTrue` opérateurs.</span><span class="sxs-lookup"><span data-stu-id="1fd25-112">The following code example defines the outline of a structure that includes definitions for the `IsFalse` and `IsTrue` operators.</span></span>  
  
 [!code-vb[VbVbalrOperators#28](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/isfalse-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="1fd25-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1fd25-113">See Also</span></span>  
 [<span data-ttu-id="1fd25-114">IsTrue (opérateur)</span><span class="sxs-lookup"><span data-stu-id="1fd25-114">IsTrue Operator</span></span>](../../../visual-basic/language-reference/operators/istrue-operator.md)  
 [<span data-ttu-id="1fd25-115">Guide pratique : définir un opérateur</span><span class="sxs-lookup"><span data-stu-id="1fd25-115">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [<span data-ttu-id="1fd25-116">AndAlso (opérateur)</span><span class="sxs-lookup"><span data-stu-id="1fd25-116">AndAlso Operator</span></span>](../../../visual-basic/language-reference/operators/andalso-operator.md)
