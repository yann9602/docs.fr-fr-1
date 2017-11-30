---
title: Public (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Public
helpviewer_keywords:
- Public keyword [Visual Basic]
- Public keyword [Visual Basic], syntax
- Public access modifier
ms.assetid: 284c9e1b-ed23-499b-9bc9-ad87c11485a5
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e6cd70adf6ec31c56f39d0443d320dd1b00b00d3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="public-visual-basic"></a><span data-ttu-id="be03b-102">Public (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="be03b-102">Public (Visual Basic)</span></span>
<span data-ttu-id="be03b-103">Spécifie ne qu’aucune restriction d’accès à un ou plusieurs éléments de programmation déclarés.</span><span class="sxs-lookup"><span data-stu-id="be03b-103">Specifies that one or more declared programming elements have no access restrictions.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="be03b-104">Remarques</span><span class="sxs-lookup"><span data-stu-id="be03b-104">Remarks</span></span>  
 <span data-ttu-id="be03b-105">Si vous publiez un composant ou un ensemble de composants, tels que d’une bibliothèque de classes, vous souhaitez généralement les éléments de programmation accessibles par tout code qui interagit avec votre assembly.</span><span class="sxs-lookup"><span data-stu-id="be03b-105">If you are publishing a component or set of components, such as a class library, you usually want the programming elements to be accessible by any code that interoperates with your assembly.</span></span> <span data-ttu-id="be03b-106">Pour octroyer cet accès illimité sur un élément, vous pouvez déclarer avec `Public`.</span><span class="sxs-lookup"><span data-stu-id="be03b-106">To confer such unlimited access on an element, you can declare it with `Public`.</span></span>  
  
 <span data-ttu-id="be03b-107">Accès public est le niveau normal pour un élément de programmation lorsque vous n’avez pas besoin de restreindre l’accès.</span><span class="sxs-lookup"><span data-stu-id="be03b-107">Public access is the normal level for a programming element when you do not need to limit access to it.</span></span> <span data-ttu-id="be03b-108">Notez que le niveau d’accès d’un élément déclaré dans une interface, un module, une classe ou une structure de valeur par défaut est `Public` si vous ne déclarez pas une dans le cas contraire.</span><span class="sxs-lookup"><span data-stu-id="be03b-108">Note that the access level of an element declared within an interface, module, class, or structure defaults to `Public` if you do not declare it otherwise.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="be03b-109">Règles</span><span class="sxs-lookup"><span data-stu-id="be03b-109">Rules</span></span>  
  
-   <span data-ttu-id="be03b-110">**Contexte de déclaration.**</span><span class="sxs-lookup"><span data-stu-id="be03b-110">**Declaration Context.**</span></span> <span data-ttu-id="be03b-111">Vous pouvez utiliser `Public` uniquement au niveau du module, interface ou espace de noms.</span><span class="sxs-lookup"><span data-stu-id="be03b-111">You can use `Public` only at module, interface, or namespace level.</span></span> <span data-ttu-id="be03b-112">Cela signifie que le contexte de déclaration pour un `Public` élément doit être un fichier source, un espace de noms, une interface, un module, une classe ou une structure et ne peut pas être une procédure.</span><span class="sxs-lookup"><span data-stu-id="be03b-112">This means the declaration context for a `Public` element must be a source file, namespace, interface, module, class, or structure, and cannot be a procedure.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="be03b-113">Comportement</span><span class="sxs-lookup"><span data-stu-id="be03b-113">Behavior</span></span>  
  
-   <span data-ttu-id="be03b-114">**Niveau d’accès.**</span><span class="sxs-lookup"><span data-stu-id="be03b-114">**Access Level.**</span></span> <span data-ttu-id="be03b-115">Tout le code qui peut accéder à un module, classe ou structure peut accéder à ses `Public` éléments.</span><span class="sxs-lookup"><span data-stu-id="be03b-115">All code that can access a module, class, or structure can access its `Public` elements.</span></span>  
  
-   <span data-ttu-id="be03b-116">**Accès par défaut.**</span><span class="sxs-lookup"><span data-stu-id="be03b-116">**Default Access.**</span></span> <span data-ttu-id="be03b-117">Variables locales à l’intérieur d’une procédure reviennent par défaut à l’accès public et que vous ne pouvez pas utiliser les modificateurs d’accès sur ces derniers.</span><span class="sxs-lookup"><span data-stu-id="be03b-117">Local variables inside a procedure default to public access, and you cannot use any access modifiers on them.</span></span>  
  
-   <span data-ttu-id="be03b-118">**Modificateurs d’accès.**</span><span class="sxs-lookup"><span data-stu-id="be03b-118">**Access Modifiers.**</span></span> <span data-ttu-id="be03b-119">Les mots clés qui spécifient le niveau d’accès sont appelés *les modificateurs d’accès*.</span><span class="sxs-lookup"><span data-stu-id="be03b-119">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="be03b-120">Pour obtenir une comparaison des modificateurs d’accès, consultez [niveaux en Visual Basic d’accès](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="be03b-120">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="be03b-121">Le modificateur `Public` peut être utilisé dans les contextes suivants :</span><span class="sxs-lookup"><span data-stu-id="be03b-121">The `Public` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="be03b-122">Class (instruction)</span><span class="sxs-lookup"><span data-stu-id="be03b-122">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="be03b-123">Const (instruction)</span><span class="sxs-lookup"><span data-stu-id="be03b-123">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="be03b-124">Declare (instruction)</span><span class="sxs-lookup"><span data-stu-id="be03b-124">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="be03b-125">Delegate (instruction)</span><span class="sxs-lookup"><span data-stu-id="be03b-125">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="be03b-126">Dim (instruction)</span><span class="sxs-lookup"><span data-stu-id="be03b-126">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="be03b-127">Enum (instruction)</span><span class="sxs-lookup"><span data-stu-id="be03b-127">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="be03b-128">Event (instruction)</span><span class="sxs-lookup"><span data-stu-id="be03b-128">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="be03b-129">Function (instruction)</span><span class="sxs-lookup"><span data-stu-id="be03b-129">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="be03b-130">Interface (instruction)</span><span class="sxs-lookup"><span data-stu-id="be03b-130">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="be03b-131">Module (instruction)</span><span class="sxs-lookup"><span data-stu-id="be03b-131">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)  
  
 [<span data-ttu-id="be03b-132">Operator (instruction)</span><span class="sxs-lookup"><span data-stu-id="be03b-132">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [<span data-ttu-id="be03b-133">Property (instruction)</span><span class="sxs-lookup"><span data-stu-id="be03b-133">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="be03b-134">Structure (instruction)</span><span class="sxs-lookup"><span data-stu-id="be03b-134">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="be03b-135">Sub (instruction)</span><span class="sxs-lookup"><span data-stu-id="be03b-135">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="be03b-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="be03b-136">See Also</span></span>  
 [<span data-ttu-id="be03b-137">Protected</span><span class="sxs-lookup"><span data-stu-id="be03b-137">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
 [<span data-ttu-id="be03b-138">Friend</span><span class="sxs-lookup"><span data-stu-id="be03b-138">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
 [<span data-ttu-id="be03b-139">Private</span><span class="sxs-lookup"><span data-stu-id="be03b-139">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
 [<span data-ttu-id="be03b-140">Niveaux d’accès dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="be03b-140">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [<span data-ttu-id="be03b-141">Procédures</span><span class="sxs-lookup"><span data-stu-id="be03b-141">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [<span data-ttu-id="be03b-142">Structures</span><span class="sxs-lookup"><span data-stu-id="be03b-142">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="be03b-143">Objets et classes</span><span class="sxs-lookup"><span data-stu-id="be03b-143">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
