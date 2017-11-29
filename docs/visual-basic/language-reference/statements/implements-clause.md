---
title: Implements, clause (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.ImplementsClause
helpviewer_keywords:
- interface implementation [Visual Basic], reimplementation
- interface members [Visual Basic], reimplementation
- interface members [Visual Basic], Implements keyword
- interface members
- members [Visual Basic], reimplementation
- interface implementation [Visual Basic], Implements keyword
- interface members [Visual Basic], implementing
- Implements keyword [Visual Basic]
- Implements statement [Visual Basic], about Implements
- members [Visual Basic], implementing
- members [Visual Basic], Implements keyword
- reimplementation
ms.assetid: 5252cdf9-964d-4fc6-af0f-0449b7126b5a
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 73f66eda29e37fda15b4c838da5a0458684131da
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="implements-clause-visual-basic"></a><span data-ttu-id="4eef6-102">Implements, clause (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4eef6-102">Implements Clause (Visual Basic)</span></span>
<span data-ttu-id="4eef6-103">Indique qu’un membre de classe ou de structure fournit l’implémentation d’un membre défini dans une interface.</span><span class="sxs-lookup"><span data-stu-id="4eef6-103">Indicates that a class or structure member is providing the implementation for a member defined in an interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4eef6-104">Remarques</span><span class="sxs-lookup"><span data-stu-id="4eef6-104">Remarks</span></span>  
<span data-ttu-id="4eef6-105">Le `Implements` mot clé n’est pas le même que le [Implements, instruction](../../../visual-basic/language-reference/statements/implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="4eef6-105">The `Implements` keyword is not the same as the [Implements Statement](../../../visual-basic/language-reference/statements/implements-statement.md).</span></span> <span data-ttu-id="4eef6-106">Vous utilisez la `Implements` instruction pour spécifier qu’une classe ou structure implémente une ou plusieurs interfaces, et ensuite pour chaque membre que vous utilisez le `Implements` mot clé pour spécifier l’interface et le membre qu’elle implémente.</span><span class="sxs-lookup"><span data-stu-id="4eef6-106">You use the `Implements` statement to specify that a class or structure implements one or more interfaces, and then for each member you use the `Implements` keyword to specify which interface and which member it implements.</span></span>

<span data-ttu-id="4eef6-107">Si une classe ou structure implémente une interface, elle doit inclure le `Implements` instruction immédiatement après le [Class, instruction](../../../visual-basic/language-reference/statements/class-statement.md) ou [instruction Structure](../../../visual-basic/language-reference/statements/structure-statement.md), et il doit implémenter tous les membres définies par l’interface.</span><span class="sxs-lookup"><span data-stu-id="4eef6-107">If a class or structure implements an interface, it must include the `Implements` statement immediately after the [Class Statement](../../../visual-basic/language-reference/statements/class-statement.md) or [Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md), and it must implement all the members defined by the interface.</span></span>

## <a name="reimplementation"></a><span data-ttu-id="4eef6-108">Nouvelle implémentation</span><span class="sxs-lookup"><span data-stu-id="4eef6-108">Reimplementation</span></span>  
<span data-ttu-id="4eef6-109">Dans une classe dérivée, vous pouvez implémenter de nouveau un membre d’interface que la classe de base a déjà implémenté.</span><span class="sxs-lookup"><span data-stu-id="4eef6-109">In a derived class, you can reimplement an interface member that the base class has already implemented.</span></span> <span data-ttu-id="4eef6-110">Cela est différent de substituer le membre de classe de base aux points suivants :</span><span class="sxs-lookup"><span data-stu-id="4eef6-110">This is different from overriding the base class member in the following respects:</span></span>

- <span data-ttu-id="4eef6-111">Le membre de classe de base n’est pas nécessaire de [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md) à être implémentées de nouveau.</span><span class="sxs-lookup"><span data-stu-id="4eef6-111">The base class member does not need to be [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md) to be reimplemented.</span></span>
- <span data-ttu-id="4eef6-112">Vous pouvez implémenter de nouveau le membre avec un nom différent.</span><span class="sxs-lookup"><span data-stu-id="4eef6-112">You can reimplement the member with a different name.</span></span>

<span data-ttu-id="4eef6-113">Le `Implements` mot clé peut être utilisé dans les contextes suivants :</span><span class="sxs-lookup"><span data-stu-id="4eef6-113">The `Implements` keyword can be used in the following contexts:</span></span>
- [<span data-ttu-id="4eef6-114">Event (instruction)</span><span class="sxs-lookup"><span data-stu-id="4eef6-114">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)
- [<span data-ttu-id="4eef6-115">Function (instruction)</span><span class="sxs-lookup"><span data-stu-id="4eef6-115">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="4eef6-116">Property (instruction)</span><span class="sxs-lookup"><span data-stu-id="4eef6-116">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="4eef6-117">Sub (instruction)</span><span class="sxs-lookup"><span data-stu-id="4eef6-117">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="4eef6-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4eef6-118">See Also</span></span>  
 [<span data-ttu-id="4eef6-119">Implements (instruction)</span><span class="sxs-lookup"><span data-stu-id="4eef6-119">Implements Statement</span></span>](../../../visual-basic/language-reference/statements/implements-statement.md)  
 [<span data-ttu-id="4eef6-120">Interface (instruction)</span><span class="sxs-lookup"><span data-stu-id="4eef6-120">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [<span data-ttu-id="4eef6-121">Class (instruction)</span><span class="sxs-lookup"><span data-stu-id="4eef6-121">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
 [<span data-ttu-id="4eef6-122">Structure (instruction)</span><span class="sxs-lookup"><span data-stu-id="4eef6-122">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)
