---
title: Private (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Private
helpviewer_keywords:
- Private keyword [Visual Basic]
- Private keyword [Visual Basic], syntax
ms.assetid: aba74a2e-5824-4613-bf63-b9ec7787f4e6
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 07450c2a5443bf6bc147cad2cfc779072bfc363b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="private-visual-basic"></a><span data-ttu-id="2e420-102">Private (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2e420-102">Private (Visual Basic)</span></span>
<span data-ttu-id="2e420-103">Spécifie qu’un ou plusieurs éléments de programmation déclarés sont accessibles uniquement à partir de leur contexte de déclaration, y compris à partir des types contenus.</span><span class="sxs-lookup"><span data-stu-id="2e420-103">Specifies that one or more declared programming elements are accessible only from within their declaration context, including from within any contained types.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2e420-104">Remarques</span><span class="sxs-lookup"><span data-stu-id="2e420-104">Remarks</span></span>  
 <span data-ttu-id="2e420-105">Si un élément de programmation représente des fonctionnalités exclusives ou contient des données confidentielles, vous souhaitez généralement limiter son accès aussi strictement que possible.</span><span class="sxs-lookup"><span data-stu-id="2e420-105">If a programming element represents proprietary functionality, or contains confidential data, you usually want to limit access to it as strictly as possible.</span></span> <span data-ttu-id="2e420-106">Vous obtenez une limitation maximale en autorisant uniquement le module, classe ou structure qui le définit pour y accéder.</span><span class="sxs-lookup"><span data-stu-id="2e420-106">You achieve the maximum limitation by allowing only the module, class, or structure that defines it to access it.</span></span> <span data-ttu-id="2e420-107">Pour limiter l’accès à un élément de cette façon, vous pouvez déclarer avec `Private`.</span><span class="sxs-lookup"><span data-stu-id="2e420-107">To limit access to an element in this way, you can declare it with `Private`.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="2e420-108">Règles</span><span class="sxs-lookup"><span data-stu-id="2e420-108">Rules</span></span>  
  
-   <span data-ttu-id="2e420-109">**Contexte de déclaration.**</span><span class="sxs-lookup"><span data-stu-id="2e420-109">**Declaration Context.**</span></span> <span data-ttu-id="2e420-110">Vous pouvez utiliser `Private` seulement au niveau du module.</span><span class="sxs-lookup"><span data-stu-id="2e420-110">You can use `Private` only at module level.</span></span> <span data-ttu-id="2e420-111">Cela signifie que le contexte de déclaration pour un `Private` élément doit être un module, classe ou structure et ne peut pas être un fichier source, un espace de noms, une interface ou une procédure.</span><span class="sxs-lookup"><span data-stu-id="2e420-111">This means the declaration context for a `Private` element must be a module, class, or structure, and cannot be a source file, namespace, interface, or procedure.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="2e420-112">Comportement</span><span class="sxs-lookup"><span data-stu-id="2e420-112">Behavior</span></span>  
  
-   <span data-ttu-id="2e420-113">**Niveau d’accès.**</span><span class="sxs-lookup"><span data-stu-id="2e420-113">**Access Level.**</span></span> <span data-ttu-id="2e420-114">Tout le code dans un contexte de déclaration peut accéder à ses `Private` éléments.</span><span class="sxs-lookup"><span data-stu-id="2e420-114">All code within a declaration context can access its `Private` elements.</span></span> <span data-ttu-id="2e420-115">Cela inclut le code au sein d’un type de relation contenant-contenu, comme une classe imbriquée ou une expression d’assignation dans une énumération.</span><span class="sxs-lookup"><span data-stu-id="2e420-115">This includes code within a contained type, such as a nested class or an assignment expression in an enumeration.</span></span> <span data-ttu-id="2e420-116">Aucun code en dehors du contexte de déclaration ne peut accéder à ses `Private` éléments.</span><span class="sxs-lookup"><span data-stu-id="2e420-116">No code outside of the declaration context can access its `Private` elements.</span></span>  
  
-   <span data-ttu-id="2e420-117">**Modificateurs d’accès.**</span><span class="sxs-lookup"><span data-stu-id="2e420-117">**Access Modifiers.**</span></span> <span data-ttu-id="2e420-118">Les mots clés qui spécifient le niveau d’accès sont appelés *les modificateurs d’accès*.</span><span class="sxs-lookup"><span data-stu-id="2e420-118">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="2e420-119">Pour obtenir une comparaison des modificateurs d’accès, consultez [niveaux en Visual Basic d’accès](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="2e420-119">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="2e420-120">Le modificateur `Private` peut être utilisé dans les contextes suivants :</span><span class="sxs-lookup"><span data-stu-id="2e420-120">The `Private` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="2e420-121">Class (instruction)</span><span class="sxs-lookup"><span data-stu-id="2e420-121">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="2e420-122">Const (instruction)</span><span class="sxs-lookup"><span data-stu-id="2e420-122">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="2e420-123">Declare (instruction)</span><span class="sxs-lookup"><span data-stu-id="2e420-123">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="2e420-124">Delegate (instruction)</span><span class="sxs-lookup"><span data-stu-id="2e420-124">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="2e420-125">Dim (instruction)</span><span class="sxs-lookup"><span data-stu-id="2e420-125">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="2e420-126">Enum (instruction)</span><span class="sxs-lookup"><span data-stu-id="2e420-126">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="2e420-127">Event (instruction)</span><span class="sxs-lookup"><span data-stu-id="2e420-127">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="2e420-128">Function (instruction)</span><span class="sxs-lookup"><span data-stu-id="2e420-128">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="2e420-129">Interface (instruction)</span><span class="sxs-lookup"><span data-stu-id="2e420-129">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="2e420-130">Property (instruction)</span><span class="sxs-lookup"><span data-stu-id="2e420-130">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="2e420-131">Structure (instruction)</span><span class="sxs-lookup"><span data-stu-id="2e420-131">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="2e420-132">Sub (instruction)</span><span class="sxs-lookup"><span data-stu-id="2e420-132">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="2e420-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2e420-133">See Also</span></span>  
 [<span data-ttu-id="2e420-134">Public</span><span class="sxs-lookup"><span data-stu-id="2e420-134">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
 [<span data-ttu-id="2e420-135">Protected</span><span class="sxs-lookup"><span data-stu-id="2e420-135">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
 [<span data-ttu-id="2e420-136">Friend</span><span class="sxs-lookup"><span data-stu-id="2e420-136">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
 [<span data-ttu-id="2e420-137">Niveaux d’accès dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2e420-137">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [<span data-ttu-id="2e420-138">Procédures</span><span class="sxs-lookup"><span data-stu-id="2e420-138">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [<span data-ttu-id="2e420-139">Structures</span><span class="sxs-lookup"><span data-stu-id="2e420-139">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="2e420-140">Objets et classes</span><span class="sxs-lookup"><span data-stu-id="2e420-140">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
