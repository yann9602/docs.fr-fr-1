---
title: "Opérateur IsTrue (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.istrue
helpviewer_keywords:
- IsTrue operator [Visual Basic]
- OrElse operator [Visual Basic]
ms.assetid: b6cec0f2-61b1-4331-a7f0-4d07ee3179d6
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c0d261186ce68f06cec95251e815248a189f6da5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="istrue-operator-visual-basic"></a><span data-ttu-id="8d961-102">Opérateur IsTrue (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8d961-102">IsTrue Operator (Visual Basic)</span></span>
<span data-ttu-id="8d961-103">Détermine si une expression est `True`.</span><span class="sxs-lookup"><span data-stu-id="8d961-103">Determines whether an expression is `True`.</span></span>  
  
 <span data-ttu-id="8d961-104">Vous ne pouvez pas appeler `IsTrue` explicitement dans votre code, mais Visual Basic compilateur peut l’utiliser pour générer le code à partir de `OrElse` clauses.</span><span class="sxs-lookup"><span data-stu-id="8d961-104">You cannot call `IsTrue` explicitly in your code, but the Visual Basic compiler can use it to generate code from `OrElse` clauses.</span></span> <span data-ttu-id="8d961-105">Si vous définissez une classe ou une structure et ensuite utiliser une variable de ce type dans un `OrElse` clause, vous devez définir `IsTrue` sur cette classe ou structure.</span><span class="sxs-lookup"><span data-stu-id="8d961-105">If you define a class or structure and then use a variable of that type in an `OrElse` clause, you must define `IsTrue` on that class or structure.</span></span>  
  
 <span data-ttu-id="8d961-106">Le compilateur considère la `IsTrue` et `IsFalse` opérateurs comme un *paire équilibrée*.</span><span class="sxs-lookup"><span data-stu-id="8d961-106">The compiler considers the `IsTrue` and `IsFalse` operators as a *matched pair*.</span></span> <span data-ttu-id="8d961-107">Cela signifie que si vous définissez un d’eux, vous devez également définir la deuxième.</span><span class="sxs-lookup"><span data-stu-id="8d961-107">This means that if you define one of them, you must also define the other one.</span></span>  
  
## <a name="compiler-use-of-istrue"></a><span data-ttu-id="8d961-108">Utilisation du compilateur de IsTrue</span><span class="sxs-lookup"><span data-stu-id="8d961-108">Compiler Use of IsTrue</span></span>  
 <span data-ttu-id="8d961-109">Lorsque vous avez défini une classe ou structure, vous pouvez utiliser une variable de ce type dans un `For`, `If`, `Else``If`, ou `While` instruction, ou dans un `When` clause.</span><span class="sxs-lookup"><span data-stu-id="8d961-109">When you have defined a class or structure, you can use a variable of that type in a `For`, `If`, `Else``If`, or `While` statement, or in a `When` clause.</span></span> <span data-ttu-id="8d961-110">Si vous faites cela, le compilateur requiert un opérateur qui convertit votre type en un `Boolean` valeur de façon à pouvoir tester une condition.</span><span class="sxs-lookup"><span data-stu-id="8d961-110">If you do this, the compiler requires an operator that converts your type into a `Boolean` value so it can test a condition.</span></span> <span data-ttu-id="8d961-111">Il recherche un opérateur adéquat dans l’ordre suivant :</span><span class="sxs-lookup"><span data-stu-id="8d961-111">It searches for a suitable operator in the following order:</span></span>  
  
1.  <span data-ttu-id="8d961-112">Un opérateur de conversion étendue de votre classe ou structure à `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="8d961-112">A widening conversion operator from your class or structure to `Boolean`.</span></span>  
  
2.  <span data-ttu-id="8d961-113">Un opérateur de conversion étendue de votre classe ou structure à `Boolean?`.</span><span class="sxs-lookup"><span data-stu-id="8d961-113">A widening conversion operator from your class or structure to `Boolean?`.</span></span>  
  
3.  <span data-ttu-id="8d961-114">Le `IsTrue` opérateur sur votre classe ou structure.</span><span class="sxs-lookup"><span data-stu-id="8d961-114">The `IsTrue` operator on your class or structure.</span></span>  
  
4.  <span data-ttu-id="8d961-115">Une conversion restrictive `Boolean?` qui n’implique pas de conversion de `Boolean` à `Boolean?`.</span><span class="sxs-lookup"><span data-stu-id="8d961-115">A narrowing conversion to `Boolean?` that does not involve a conversion from `Boolean` to `Boolean?`.</span></span>  
  
5.  <span data-ttu-id="8d961-116">Un opérateur de conversion restrictive de votre classe ou structure à `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="8d961-116">A narrowing conversion operator from your class or structure to `Boolean`.</span></span>  
  
 <span data-ttu-id="8d961-117">Si vous n’avez pas défini de conversion en `Boolean` ou `IsTrue` (opérateur), le compilateur signale une erreur.</span><span class="sxs-lookup"><span data-stu-id="8d961-117">If you have not defined any conversion to `Boolean` or an `IsTrue` operator, the compiler signals an error.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8d961-118">Le `IsTrue` opérateur peut être *surchargé*, ce qui signifie qu’une classe ou structure peut redéfinir son comportement lorsque son opérande a le type de cette classe ou structure.</span><span class="sxs-lookup"><span data-stu-id="8d961-118">The `IsTrue` operator can be *overloaded*, which means that a class or structure can redefine its behavior when its operand has the type of that class or structure.</span></span> <span data-ttu-id="8d961-119">Si votre code utilise cet opérateur sur une telle classe ou structure, assurez-vous que vous comprenez son comportement redéfini.</span><span class="sxs-lookup"><span data-stu-id="8d961-119">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="8d961-120">Pour plus d’informations, consultez [procédures d’opérateur](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="8d961-120">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8d961-121">Exemple</span><span class="sxs-lookup"><span data-stu-id="8d961-121">Example</span></span>  
 <span data-ttu-id="8d961-122">L’exemple de code suivant définit le plan d’une structure qui contient les définitions pour la `IsFalse` et `IsTrue` opérateurs.</span><span class="sxs-lookup"><span data-stu-id="8d961-122">The following code example defines the outline of a structure that includes definitions for the `IsFalse` and `IsTrue` operators.</span></span>  
  
 [!code-vb[VbVbalrOperators#28](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/istrue-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="8d961-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8d961-123">See Also</span></span>  
 [<span data-ttu-id="8d961-124">IsFalse (opérateur)</span><span class="sxs-lookup"><span data-stu-id="8d961-124">IsFalse Operator</span></span>](../../../visual-basic/language-reference/operators/isfalse-operator.md)  
 [<span data-ttu-id="8d961-125">Guide pratique : définir un opérateur</span><span class="sxs-lookup"><span data-stu-id="8d961-125">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [<span data-ttu-id="8d961-126">OrElse (opérateur)</span><span class="sxs-lookup"><span data-stu-id="8d961-126">OrElse Operator</span></span>](../../../visual-basic/language-reference/operators/orelse-operator.md)
