---
title: Protected (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Protected
helpviewer_keywords:
- Protected Friend keyword combination
- Protected keyword [Visual Basic], and Friend
- Protected keyword [Visual Basic], syntax
- Protected access modifier
- Protected keyword [Visual Basic]
ms.assetid: 74ad3d56-309f-49d2-b60c-1d0157d010e8
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2d0cc7a0cb626a9ec8e2a0e47abc02e5268aed56
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="protected-visual-basic"></a><span data-ttu-id="6fd77-102">Protected (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6fd77-102">Protected (Visual Basic)</span></span>
<span data-ttu-id="6fd77-103">Spécifie qu’un ou plusieurs éléments de programmation déclarés sont accessibles uniquement à partir de leur propre classe ou d’une classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="6fd77-103">Specifies that one or more declared programming elements are accessible only from within their own class or from a derived class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6fd77-104">Remarques</span><span class="sxs-lookup"><span data-stu-id="6fd77-104">Remarks</span></span>  
 <span data-ttu-id="6fd77-105">Parfois, un élément de programmation déclaré dans une classe contient des données sensibles ou du code restreint et vous souhaitez limiter l’accès à l’élément.</span><span class="sxs-lookup"><span data-stu-id="6fd77-105">Sometimes a programming element declared in a class contains sensitive data or restricted code, and you want to limit access to the element.</span></span> <span data-ttu-id="6fd77-106">Toutefois, si la classe peut être héritée et que vous prévoyez une hiérarchie de classes dérivées, il peut être nécessaire pour ces classes dérivées accéder aux données ou au code.</span><span class="sxs-lookup"><span data-stu-id="6fd77-106">However, if the class is inheritable and you expect a hierarchy of derived classes, it might be necessary for these derived classes to access the data or code.</span></span> <span data-ttu-id="6fd77-107">Dans ce cas, vous souhaitez que l’élément doit être accessible à la fois à partir de la classe de base et de toutes les classes dérivées.</span><span class="sxs-lookup"><span data-stu-id="6fd77-107">In such a case, you want the element to be accessible both from the base class and from all derived classes.</span></span> <span data-ttu-id="6fd77-108">Pour limiter l’accès à un élément de cette manière, vous pouvez déclarer avec `Protected`.</span><span class="sxs-lookup"><span data-stu-id="6fd77-108">To limit access to an element in this manner, you can declare it with `Protected`.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="6fd77-109">Règles</span><span class="sxs-lookup"><span data-stu-id="6fd77-109">Rules</span></span>  
  
-   <span data-ttu-id="6fd77-110">**Contexte de déclaration.**</span><span class="sxs-lookup"><span data-stu-id="6fd77-110">**Declaration Context.**</span></span> <span data-ttu-id="6fd77-111">Vous pouvez utiliser `Protected` uniquement au niveau de la classe.</span><span class="sxs-lookup"><span data-stu-id="6fd77-111">You can use `Protected` only at class level.</span></span> <span data-ttu-id="6fd77-112">Cela signifie que le contexte de déclaration pour un `Protected` élément doit être une classe et ne peut pas être un fichier source, espace de noms, interface, un module, structure ou procédure.</span><span class="sxs-lookup"><span data-stu-id="6fd77-112">This means the declaration context for a `Protected` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>  
  
-   <span data-ttu-id="6fd77-113">**Modificateurs combinés.**</span><span class="sxs-lookup"><span data-stu-id="6fd77-113">**Combined Modifiers.**</span></span> <span data-ttu-id="6fd77-114">Vous pouvez utiliser la `Protected` modificateur avec la [Friend](../../../visual-basic/language-reference/modifiers/friend.md) modificateur dans la même déclaration.</span><span class="sxs-lookup"><span data-stu-id="6fd77-114">You can use the `Protected` modifier together with the [Friend](../../../visual-basic/language-reference/modifiers/friend.md) modifier in the same declaration.</span></span> <span data-ttu-id="6fd77-115">Cette combinaison rend les éléments déclarés accessibles à partir de n’importe où dans le même assembly, de leur propre classe et de classes dérivées.</span><span class="sxs-lookup"><span data-stu-id="6fd77-115">This combination makes the declared elements accessible from anywhere in the same assembly, from their own class, and from derived classes.</span></span> <span data-ttu-id="6fd77-116">Vous pouvez spécifier `Protected Friend` uniquement sur les membres de classes.</span><span class="sxs-lookup"><span data-stu-id="6fd77-116">You can specify `Protected Friend` only on members of classes.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="6fd77-117">Comportement</span><span class="sxs-lookup"><span data-stu-id="6fd77-117">Behavior</span></span>  
  
-   <span data-ttu-id="6fd77-118">**Niveau d’accès.**</span><span class="sxs-lookup"><span data-stu-id="6fd77-118">**Access Level.**</span></span> <span data-ttu-id="6fd77-119">Tout le code dans une classe peut accéder à ses éléments.</span><span class="sxs-lookup"><span data-stu-id="6fd77-119">All code in a class can access its elements.</span></span> <span data-ttu-id="6fd77-120">Le code dans n’importe quelle classe qui dérive d’une classe de base peut accéder à tous les `Protected` les éléments de la classe de base.</span><span class="sxs-lookup"><span data-stu-id="6fd77-120">Code in any class that derives from a base class can access all the `Protected` elements of the base class.</span></span> <span data-ttu-id="6fd77-121">Cela est vrai pour toutes les générations de dérivation.</span><span class="sxs-lookup"><span data-stu-id="6fd77-121">This is true for all generations of derivation.</span></span> <span data-ttu-id="6fd77-122">Cela signifie qu’une classe peut accéder `Protected` les éléments de la classe de base de la classe de base et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="6fd77-122">This means that a class can access `Protected` elements of the base class of the base class, and so on.</span></span>  
  
     <span data-ttu-id="6fd77-123">L’accès protégé n’est pas un sur-ensemble ou un sous-ensemble de l’accès ami.</span><span class="sxs-lookup"><span data-stu-id="6fd77-123">Protected access is not a superset or subset of friend access.</span></span>  
  
-   <span data-ttu-id="6fd77-124">**Modificateurs d’accès.**</span><span class="sxs-lookup"><span data-stu-id="6fd77-124">**Access Modifiers.**</span></span> <span data-ttu-id="6fd77-125">Les mots clés qui spécifient le niveau d’accès sont appelés *les modificateurs d’accès*.</span><span class="sxs-lookup"><span data-stu-id="6fd77-125">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="6fd77-126">Pour obtenir une comparaison des modificateurs d’accès, consultez [niveaux en Visual Basic d’accès](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="6fd77-126">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="6fd77-127">Le modificateur `Protected` peut être utilisé dans les contextes suivants :</span><span class="sxs-lookup"><span data-stu-id="6fd77-127">The `Protected` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="6fd77-128">Class (instruction)</span><span class="sxs-lookup"><span data-stu-id="6fd77-128">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="6fd77-129">Const (instruction)</span><span class="sxs-lookup"><span data-stu-id="6fd77-129">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="6fd77-130">Declare (instruction)</span><span class="sxs-lookup"><span data-stu-id="6fd77-130">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="6fd77-131">Delegate (instruction)</span><span class="sxs-lookup"><span data-stu-id="6fd77-131">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="6fd77-132">Dim (instruction)</span><span class="sxs-lookup"><span data-stu-id="6fd77-132">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="6fd77-133">Enum (instruction)</span><span class="sxs-lookup"><span data-stu-id="6fd77-133">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="6fd77-134">Event (instruction)</span><span class="sxs-lookup"><span data-stu-id="6fd77-134">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="6fd77-135">Function (instruction)</span><span class="sxs-lookup"><span data-stu-id="6fd77-135">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="6fd77-136">Interface (instruction)</span><span class="sxs-lookup"><span data-stu-id="6fd77-136">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="6fd77-137">Property (instruction)</span><span class="sxs-lookup"><span data-stu-id="6fd77-137">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="6fd77-138">Structure (instruction)</span><span class="sxs-lookup"><span data-stu-id="6fd77-138">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="6fd77-139">Sub (instruction)</span><span class="sxs-lookup"><span data-stu-id="6fd77-139">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="6fd77-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6fd77-140">See Also</span></span>  
 [<span data-ttu-id="6fd77-141">Public</span><span class="sxs-lookup"><span data-stu-id="6fd77-141">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
 [<span data-ttu-id="6fd77-142">Friend</span><span class="sxs-lookup"><span data-stu-id="6fd77-142">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
 [<span data-ttu-id="6fd77-143">Private</span><span class="sxs-lookup"><span data-stu-id="6fd77-143">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
 [<span data-ttu-id="6fd77-144">Niveaux d’accès dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6fd77-144">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [<span data-ttu-id="6fd77-145">Procédures</span><span class="sxs-lookup"><span data-stu-id="6fd77-145">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [<span data-ttu-id="6fd77-146">Structures</span><span class="sxs-lookup"><span data-stu-id="6fd77-146">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="6fd77-147">Objets et classes</span><span class="sxs-lookup"><span data-stu-id="6fd77-147">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
