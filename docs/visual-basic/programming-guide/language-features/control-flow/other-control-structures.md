---
title: "Autres structures de contrôle (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- statements [Visual Basic], control flow
- control structures [Visual Basic]
ms.assetid: 24b811f7-98ba-40ec-8dd3-4d528cfa4574
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 09e59d25b3b2fc89026295e8500c30dad7b75086
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="other-control-structures-visual-basic"></a><span data-ttu-id="a4793-102">Autres structures de contrôle (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a4793-102">Other Control Structures (Visual Basic)</span></span>
[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="a4793-103">Fournit des structures de contrôle qui vous aident à supprimer une ressource ou de réduisent le nombre de fois où que vous devez répéter une référence d’objet.</span><span class="sxs-lookup"><span data-stu-id="a4793-103"> provides control structures that help you dispose of a resource or reduce the number of times you have to repeat an object reference.</span></span>  
  
## <a name="usingend-using-construction"></a><span data-ttu-id="a4793-104">À l’aide de... À l’aide de la Construction de fin</span><span class="sxs-lookup"><span data-stu-id="a4793-104">Using...End Using Construction</span></span>  
 <span data-ttu-id="a4793-105">Le `Using...End Using` construction établit un bloc d’instruction dans laquelle vous utilisez une ressource telle qu’une connexion SQL.</span><span class="sxs-lookup"><span data-stu-id="a4793-105">The `Using...End Using` construction establishes a statement block within which you make use of a resource such as a SQL connection.</span></span> <span data-ttu-id="a4793-106">Vous pouvez éventuellement acquérir la ressource avec la `Using` instruction.</span><span class="sxs-lookup"><span data-stu-id="a4793-106">You can optionally acquire the resource with the `Using` statement.</span></span> <span data-ttu-id="a4793-107">Lorsque vous quittez la `Using` bloc, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] supprime automatiquement la ressource afin qu’il soit disponible pour un autre code à utiliser.</span><span class="sxs-lookup"><span data-stu-id="a4793-107">When you exit the `Using` block, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] automatically disposes of the resource so that it is available for other code to use.</span></span> <span data-ttu-id="a4793-108">La ressource doit être locale et supprimable.</span><span class="sxs-lookup"><span data-stu-id="a4793-108">The resource must be local and disposable.</span></span> <span data-ttu-id="a4793-109">Pour plus d’informations, consultez [using, instruction](../../../../visual-basic/language-reference/statements/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a4793-109">For more information, see [Using Statement](../../../../visual-basic/language-reference/statements/using-statement.md).</span></span>  
  
## <a name="withend-with-construction"></a><span data-ttu-id="a4793-110">Avec... Se termine par la Construction</span><span class="sxs-lookup"><span data-stu-id="a4793-110">With...End With Construction</span></span>  
 <span data-ttu-id="a4793-111">Le `With...End With` vous permet de spécifier une référence d’objet une fois, puis exécutez une série d’instructions qui accèdent à ses membres.</span><span class="sxs-lookup"><span data-stu-id="a4793-111">The `With...End With` construction lets you specify an object reference once and then run a series of statements that access its members.</span></span> <span data-ttu-id="a4793-112">Cela peut simplifier votre code et améliorer les performances car [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] n’a pas de rétablir la référence pour chaque instruction qui y accède.</span><span class="sxs-lookup"><span data-stu-id="a4793-112">This can simplify your code and improve performance because [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] does not have to re-establish the reference for each statement that accesses it.</span></span> <span data-ttu-id="a4793-113">Pour plus d’informations, consultez [avec... End With, instruction](../../../../visual-basic/language-reference/statements/with-end-with-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a4793-113">For more information, see [With...End With Statement](../../../../visual-basic/language-reference/statements/with-end-with-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4793-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a4793-114">See Also</span></span>  
 [<span data-ttu-id="a4793-115">Flux de contrôle</span><span class="sxs-lookup"><span data-stu-id="a4793-115">Control Flow</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)  
 [<span data-ttu-id="a4793-116">Structures de décision</span><span class="sxs-lookup"><span data-stu-id="a4793-116">Decision Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)  
 [<span data-ttu-id="a4793-117">Structures de boucle</span><span class="sxs-lookup"><span data-stu-id="a4793-117">Loop Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [<span data-ttu-id="a4793-118">Structures de contrôle imbriquées</span><span class="sxs-lookup"><span data-stu-id="a4793-118">Nested Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)  
 [<span data-ttu-id="a4793-119">Using (instruction)</span><span class="sxs-lookup"><span data-stu-id="a4793-119">Using Statement</span></span>](../../../../visual-basic/language-reference/statements/using-statement.md)  
 [<span data-ttu-id="a4793-120">With...End With (instruction)</span><span class="sxs-lookup"><span data-stu-id="a4793-120">With...End With Statement</span></span>](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)
