---
title: WithEvents (Visual Basic) | Documents Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.WithEvents
- WithEvents
dev_langs:
- VB
helpviewer_keywords:
- WithEvents keyword
ms.assetid: 19d461f5-d72f-4de9-8c1d-0a6650316990
caps.latest.revision: 17
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
ms.openlocfilehash: b956f8f0d6f0a2fd9f41c5df6d6c82b43fa09018
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="withevents-visual-basic"></a><span data-ttu-id="9f363-102">WithEvents (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9f363-102">WithEvents (Visual Basic)</span></span>
<span data-ttu-id="9f363-103">Spécifie qu’une ou plusieurs variables membres déclarées font référence à une instance d’une classe qui peut déclencher des événements.</span><span class="sxs-lookup"><span data-stu-id="9f363-103">Specifies that one or more declared member variables refer to an instance of a class that can raise events.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9f363-104">Notes</span><span class="sxs-lookup"><span data-stu-id="9f363-104">Remarks</span></span>  
 <span data-ttu-id="9f363-105">Lorsqu’une variable est définie à l’aide de `WithEvents`, vous pouvez spécifier de façon déclarative qu’une méthode gère les événements de la variable à l’aide du `Handles` (mot clé).</span><span class="sxs-lookup"><span data-stu-id="9f363-105">When a variable is defined using `WithEvents`, you can declaratively specify that a method handles the variable's events using the `Handles` keyword.</span></span>  
  
 <span data-ttu-id="9f363-106">Vous pouvez utiliser `WithEvents` uniquement au niveau de la classe ou du module.</span><span class="sxs-lookup"><span data-stu-id="9f363-106">You can use `WithEvents` only at class or module level.</span></span> <span data-ttu-id="9f363-107">Cela signifie que le contexte de déclaration pour une `WithEvents` variable doit être une classe ou un module et ne peut pas être un fichier source, un espace de noms, une structure ou une procédure.</span><span class="sxs-lookup"><span data-stu-id="9f363-107">This means the declaration context for a `WithEvents` variable must be a class or module and cannot be a source file, namespace, structure, or procedure.</span></span>  
  
 <span data-ttu-id="9f363-108">Vous ne pouvez pas utiliser `WithEvents` sur un membre de structure.</span><span class="sxs-lookup"><span data-stu-id="9f363-108">You cannot use `WithEvents` on a structure member.</span></span>  
  
 <span data-ttu-id="9f363-109">Vous pouvez déclarer que des variables, des tableaux non — avec `WithEvents`.</span><span class="sxs-lookup"><span data-stu-id="9f363-109">You can declare only individual variables—not arrays—with `WithEvents`.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="9f363-110">Règles</span><span class="sxs-lookup"><span data-stu-id="9f363-110">Rules</span></span>  
  
-   <span data-ttu-id="9f363-111">**Types d’élément.**</span><span class="sxs-lookup"><span data-stu-id="9f363-111">**Element Types.**</span></span> <span data-ttu-id="9f363-112">Vous devez déclarer `WithEvents` variables comme des variables d’objet afin qu’ils puissent accepter des instances de classes.</span><span class="sxs-lookup"><span data-stu-id="9f363-112">You must declare `WithEvents` variables to be object variables so that they can accept class instances.</span></span> <span data-ttu-id="9f363-113">Toutefois, vous ne pouvez pas déclarer comme `Object`.</span><span class="sxs-lookup"><span data-stu-id="9f363-113">However, you cannot declare them as `Object`.</span></span> <span data-ttu-id="9f363-114">Vous devez les déclarer comme la classe spécifique capable de déclencher les événements.</span><span class="sxs-lookup"><span data-stu-id="9f363-114">You must declare them as the specific class that can raise the events.</span></span>  
  
 <span data-ttu-id="9f363-115">Le `WithEvents` modificateur peut être utilisé dans ce contexte : [Dim (instruction)](../../../visual-basic/language-reference/statements/dim-statement.md)</span><span class="sxs-lookup"><span data-stu-id="9f363-115">The `WithEvents` modifier can be used in this context: [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f363-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9f363-116">See Also</span></span>  
 <span data-ttu-id="9f363-117">[Gère](../../../visual-basic/language-reference/statements/handles-clause.md) </span><span class="sxs-lookup"><span data-stu-id="9f363-117">[Handles](../../../visual-basic/language-reference/statements/handles-clause.md) </span></span>  
<span data-ttu-id="9f363-118"> [Mots clés](../../../visual-basic/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="9f363-118"> [Keywords](../../../visual-basic/language-reference/keywords/index.md) </span></span>  
<span data-ttu-id="9f363-119"> [Événements](../../../visual-basic/programming-guide/language-features/events/index.md)</span><span class="sxs-lookup"><span data-stu-id="9f363-119"> [Events](../../../visual-basic/programming-guide/language-features/events/index.md)</span></span>
