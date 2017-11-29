---
title: WithEvents (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.WithEvents
- WithEvents
helpviewer_keywords: WithEvents keyword [Visual Basic]
ms.assetid: 19d461f5-d72f-4de9-8c1d-0a6650316990
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 68a58fd130c04f2ed0cb1f2e5b9250f6c85f120d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="withevents-visual-basic"></a><span data-ttu-id="128b9-102">WithEvents (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="128b9-102">WithEvents (Visual Basic)</span></span>
<span data-ttu-id="128b9-103">Spécifie qu’une ou plusieurs variables membres déclarées font référence à une instance d’une classe qui peut déclencher des événements.</span><span class="sxs-lookup"><span data-stu-id="128b9-103">Specifies that one or more declared member variables refer to an instance of a class that can raise events.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="128b9-104">Remarques</span><span class="sxs-lookup"><span data-stu-id="128b9-104">Remarks</span></span>  
 <span data-ttu-id="128b9-105">Lorsqu’une variable est définie à l’aide de `WithEvents`, vous pouvez spécifier de façon déclarative qu’une méthode gère les événements de la variable à l’aide du `Handles` (mot clé).</span><span class="sxs-lookup"><span data-stu-id="128b9-105">When a variable is defined using `WithEvents`, you can declaratively specify that a method handles the variable's events using the `Handles` keyword.</span></span>  
  
 <span data-ttu-id="128b9-106">Vous pouvez utiliser `WithEvents` uniquement au niveau de la classe ou le module.</span><span class="sxs-lookup"><span data-stu-id="128b9-106">You can use `WithEvents` only at class or module level.</span></span> <span data-ttu-id="128b9-107">Cela signifie que le contexte de déclaration pour une `WithEvents` variable doit être une classe ou un module et ne peut pas être un fichier source, un espace de noms, une structure ou une procédure.</span><span class="sxs-lookup"><span data-stu-id="128b9-107">This means the declaration context for a `WithEvents` variable must be a class or module and cannot be a source file, namespace, structure, or procedure.</span></span>  
  
 <span data-ttu-id="128b9-108">Vous ne pouvez pas utiliser `WithEvents` sur un membre de structure.</span><span class="sxs-lookup"><span data-stu-id="128b9-108">You cannot use `WithEvents` on a structure member.</span></span>  
  
 <span data-ttu-id="128b9-109">Vous pouvez déclarer que des variables, pas les tableaux, avec `WithEvents`.</span><span class="sxs-lookup"><span data-stu-id="128b9-109">You can declare only individual variables—not arrays—with `WithEvents`.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="128b9-110">Règles</span><span class="sxs-lookup"><span data-stu-id="128b9-110">Rules</span></span>  
  
-   <span data-ttu-id="128b9-111">**Types d’élément.**</span><span class="sxs-lookup"><span data-stu-id="128b9-111">**Element Types.**</span></span> <span data-ttu-id="128b9-112">Vous devez déclarer `WithEvents` variables comme des variables d’objet afin qu’ils puissent accepter des instances de classes.</span><span class="sxs-lookup"><span data-stu-id="128b9-112">You must declare `WithEvents` variables to be object variables so that they can accept class instances.</span></span> <span data-ttu-id="128b9-113">Toutefois, vous ne pouvez pas déclarer en tant que `Object`.</span><span class="sxs-lookup"><span data-stu-id="128b9-113">However, you cannot declare them as `Object`.</span></span> <span data-ttu-id="128b9-114">Vous devez les déclarer en tant que la classe spécifique capable de déclencher les événements.</span><span class="sxs-lookup"><span data-stu-id="128b9-114">You must declare them as the specific class that can raise the events.</span></span>  
  
 <span data-ttu-id="128b9-115">Le `WithEvents` modificateur peut être utilisé dans ce contexte : [Dim (instruction)](../../../visual-basic/language-reference/statements/dim-statement.md)</span><span class="sxs-lookup"><span data-stu-id="128b9-115">The `WithEvents` modifier can be used in this context: [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="128b9-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="128b9-116">See Also</span></span>  
 [<span data-ttu-id="128b9-117">Handles</span><span class="sxs-lookup"><span data-stu-id="128b9-117">Handles</span></span>](../../../visual-basic/language-reference/statements/handles-clause.md)  
 [<span data-ttu-id="128b9-118">Mots clés</span><span class="sxs-lookup"><span data-stu-id="128b9-118">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)  
 [<span data-ttu-id="128b9-119">Événements</span><span class="sxs-lookup"><span data-stu-id="128b9-119">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
