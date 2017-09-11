---
title: "Opérateur AddressOf (Visual Basic) | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- AddressOf
- vb.AddressOf
dev_langs:
- VB
helpviewer_keywords:
- AddressOf operator
- addresses, passing to API procedures
ms.assetid: 8105a59d-60d8-4ab5-b221-5899cdfacbf4
caps.latest.revision: 11
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
ms.sourcegitcommit: 14abadaf548e228244a1ff7ca72fa3896ef4eb5d
ms.openlocfilehash: e29b7ae2a6f6040cfc8c6e0cd0c9eb055a6694e9
ms.contentlocale: fr-fr
ms.lasthandoff: 05/23/2017

---
# <a name="addressof-operator-visual-basic"></a><span data-ttu-id="88dd8-102">Opérateur AddressOf (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="88dd8-102">AddressOf Operator (Visual Basic)</span></span>
<span data-ttu-id="88dd8-103">Crée une instance de délégué de procédure qui fait référence à la procédure spécifique.</span><span class="sxs-lookup"><span data-stu-id="88dd8-103">Creates a procedure delegate instance that references the specific procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88dd8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="88dd8-104">Syntax</span></span>  
  
```  
AddressOf procedurename  
```  
  
## <a name="parts"></a><span data-ttu-id="88dd8-105">Composants</span><span class="sxs-lookup"><span data-stu-id="88dd8-105">Parts</span></span>  
 `procedurename`  
 <span data-ttu-id="88dd8-106">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="88dd8-106">Required.</span></span> <span data-ttu-id="88dd8-107">Indique la procédure à référencer par le délégué de procédure nouvellement créé.</span><span class="sxs-lookup"><span data-stu-id="88dd8-107">Specifies the procedure to be referenced by the newly created procedure delegate.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="88dd8-108">Notes</span><span class="sxs-lookup"><span data-stu-id="88dd8-108">Remarks</span></span>  
 <span data-ttu-id="88dd8-109">Le `AddressOf` opérateur crée un délégué de fonction qui pointe vers la fonction spécifiée par `procedurename`.</span><span class="sxs-lookup"><span data-stu-id="88dd8-109">The `AddressOf` operator creates a function delegate that points to the function specified by `procedurename`.</span></span> <span data-ttu-id="88dd8-110">Lorsque la procédure spécifiée est qu'une méthode d’instance puis le délégué de fonction fait référence à l’instance et de la méthode.</span><span class="sxs-lookup"><span data-stu-id="88dd8-110">When the specified procedure is an instance method then the function delegate refers to both the instance and the method.</span></span> <span data-ttu-id="88dd8-111">Ensuite, lorsque le délégué de fonction est appelé la méthode spécifiée de l’instance spécifiée est appelée.</span><span class="sxs-lookup"><span data-stu-id="88dd8-111">Then, when the function delegate is invoked the specified method of the specified instance is called.</span></span>  
  
 <span data-ttu-id="88dd8-112">Le `AddressOf` opérateur peut être utilisé comme opérande d’un constructeur délégué ou il peut être utilisé dans un contexte où le type du délégué peut être déterminé par le compilateur.</span><span class="sxs-lookup"><span data-stu-id="88dd8-112">The `AddressOf` operator can be used as the operand of a delegate constructor or it can be used in a context in which the type of the delegate can be determined by the compiler.</span></span>  
  
## <a name="example"></a><span data-ttu-id="88dd8-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="88dd8-113">Example</span></span>  
 <span data-ttu-id="88dd8-114">Cet exemple utilise le `AddressOf` opérateur pour désigner un délégué pour gérer les `Click` événements d’un bouton.</span><span class="sxs-lookup"><span data-stu-id="88dd8-114">This example uses the `AddressOf` operator to designate a delegate to handle the `Click` event of a button.</span></span>  
  
 <span data-ttu-id="88dd8-115">[!code-vb[VbVbalrDelegates n °&8;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addressof-operator_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="88dd8-115">[!code-vb[VbVbalrDelegates#8](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addressof-operator_1.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="88dd8-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="88dd8-116">Example</span></span>  
 <span data-ttu-id="88dd8-117">L’exemple suivant utilise le `AddressOf` opérateur pour désigner la fonction de démarrage d’un thread.</span><span class="sxs-lookup"><span data-stu-id="88dd8-117">The following example uses the `AddressOf` operator to designate the startup function for a thread.</span></span>  
  
 <span data-ttu-id="88dd8-118">[!code-vb[VbVbalrDelegates&#9;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addressof-operator_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="88dd8-118">[!code-vb[VbVbalrDelegates#9](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addressof-operator_2.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88dd8-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="88dd8-119">See Also</span></span>  
 <span data-ttu-id="88dd8-120">[Declare (instruction)](../../../visual-basic/language-reference/statements/declare-statement.md) </span><span class="sxs-lookup"><span data-stu-id="88dd8-120">[Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) </span></span>  
<span data-ttu-id="88dd8-121"> [Function (instruction)](../../../visual-basic/language-reference/statements/function-statement.md) </span><span class="sxs-lookup"><span data-stu-id="88dd8-121"> [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md) </span></span>  
<span data-ttu-id="88dd8-122"> [Sub (instruction)](../../../visual-basic/language-reference/statements/sub-statement.md) </span><span class="sxs-lookup"><span data-stu-id="88dd8-122"> [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md) </span></span>  
<span data-ttu-id="88dd8-123"> [Délégués](../../../visual-basic/programming-guide/language-features/delegates/index.md)</span><span class="sxs-lookup"><span data-stu-id="88dd8-123"> [Delegates](../../../visual-basic/programming-guide/language-features/delegates/index.md)</span></span>

