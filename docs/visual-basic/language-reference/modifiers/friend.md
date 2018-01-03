---
title: Friend (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Friend
helpviewer_keywords:
- Friend keyword [Visual Basic]
- Friend access modifier
- Friend keyword [Visual Basic], syntax
- Protected Friend keyword combination
- Friend keyword [Visual Basic], and Protected
ms.assetid: b664605e-1c79-4728-b996-aa59c50846bc
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: df0e8ad1990fe7a1aa495e1794c942813cffb5bc
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="friend-visual-basic"></a><span data-ttu-id="bca0a-102">Friend (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bca0a-102">Friend (Visual Basic)</span></span>
<span data-ttu-id="bca0a-103">Spécifie qu’un ou plusieurs éléments de programmation déclarés sont accessibles uniquement à partir de l’assembly qui contient leur déclaration.</span><span class="sxs-lookup"><span data-stu-id="bca0a-103">Specifies that one or more declared programming elements are accessible only from within the assembly that contains their declaration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bca0a-104">Notes</span><span class="sxs-lookup"><span data-stu-id="bca0a-104">Remarks</span></span>  
 <span data-ttu-id="bca0a-105">Dans de nombreux cas, vous souhaitez que les éléments tels que les classes et les structures à utiliser par la totalité de l’assembly, pas uniquement par le composant qui les déclare de programmation.</span><span class="sxs-lookup"><span data-stu-id="bca0a-105">In many cases, you want programming elements such as classes and structures to be used by the entire assembly, not only by the component that declares them.</span></span> <span data-ttu-id="bca0a-106">Toutefois, vous pouvez les rendre accessibles par le code en dehors de l’assembly (par exemple, si l’application est propriétaire).</span><span class="sxs-lookup"><span data-stu-id="bca0a-106">However, you might not want them to be accessible by code outside the assembly (for example, if the application is proprietary).</span></span> <span data-ttu-id="bca0a-107">Si vous souhaitez limiter l’accès à un élément de cette façon, vous pouvez la déclarer à l’aide de la `Friend` modificateur.</span><span class="sxs-lookup"><span data-stu-id="bca0a-107">If you want to limit access to an element in this way, you can declare it by using the `Friend` modifier.</span></span>  
  
 <span data-ttu-id="bca0a-108">Le code dans d’autres classes, structures et les modules qui sont compilés dans le même assembly peut accéder à tous les `Friend` éléments dans cet assembly.</span><span class="sxs-lookup"><span data-stu-id="bca0a-108">Code in other classes, structures, and modules that are compiled to the same assembly can access all the `Friend` elements in that assembly.</span></span>  
  
 <span data-ttu-id="bca0a-109">`Friend`l’accès est souvent le niveau par défaut pour les éléments de programmation d’une application, et `Friend` est l’accès par défaut au niveau d’une interface, un module, une classe ou une structure.</span><span class="sxs-lookup"><span data-stu-id="bca0a-109">`Friend` access is often the preferred level for an application's programming elements, and `Friend` is the default access level of an interface, a module, a class, or a structure.</span></span>  
  
 <span data-ttu-id="bca0a-110">Vous pouvez utiliser `Friend` uniquement au niveau du module, interface ou espace de noms.</span><span class="sxs-lookup"><span data-stu-id="bca0a-110">You can use `Friend` only at the module, interface, or namespace level.</span></span> <span data-ttu-id="bca0a-111">Par conséquent, le contexte de déclaration pour un `Friend` élément doit être un fichier source, un espace de noms, une interface, un module, une classe ou une structure ; il ne peut pas être une procédure.</span><span class="sxs-lookup"><span data-stu-id="bca0a-111">Therefore, the declaration context for a `Friend` element must be a source file, a namespace, an interface, a module, a class, or a structure; it can't be a procedure.</span></span>  
  
 <span data-ttu-id="bca0a-112">Vous pouvez utiliser la `Friend` modificateur conjointement avec la [protégé](../../../visual-basic/language-reference/modifiers/protected.md) modificateur dans la même déclaration.</span><span class="sxs-lookup"><span data-stu-id="bca0a-112">You can use the `Friend` modifier in conjunction with the [Protected](../../../visual-basic/language-reference/modifiers/protected.md) modifier in the same declaration.</span></span> <span data-ttu-id="bca0a-113">Cette combinaison confère à la fois `Friend` accès et l’accès protégé sur les éléments déclarés, afin qu’ils soient accessibles à partir de n’importe où dans le même assembly, de leur propre classe et de classes dérivées.</span><span class="sxs-lookup"><span data-stu-id="bca0a-113">This combination confers both `Friend` access and protected access on the declared elements, so they are accessible from anywhere in the same assembly, from their own class, and from derived classes.</span></span> <span data-ttu-id="bca0a-114">Vous pouvez spécifier `Protected Friend` uniquement sur les membres de classes.</span><span class="sxs-lookup"><span data-stu-id="bca0a-114">You can specify `Protected Friend` only on members of classes.</span></span>  
  
 <span data-ttu-id="bca0a-115">Pour obtenir une comparaison de `Friend` et l’autre les modificateurs d’accès, consultez [niveaux en Visual Basic d’accès](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="bca0a-115">For a comparison of `Friend` and the other access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bca0a-116">Vous pouvez spécifier qu’un autre assembly est un assembly friend, ce qui permet d’accéder à tous les types et membres qui sont marqués comme `Friend`.</span><span class="sxs-lookup"><span data-stu-id="bca0a-116">You can specify that another assembly is a friend assembly, which allows it to access all types and members that are marked as `Friend`.</span></span> <span data-ttu-id="bca0a-117">Pour plus d’informations, consultez [Assemblys friend](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="bca0a-117">For more information, see [Friend Assemblies](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bca0a-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="bca0a-118">Example</span></span>  
 <span data-ttu-id="bca0a-119">La classe suivante utilise le `Friend` modificateur pour autoriser d’autres éléments de programmation dans le même assembly pour accéder à certains membres.</span><span class="sxs-lookup"><span data-stu-id="bca0a-119">The following class uses the `Friend` modifier to allow other programming elements within the same assembly to access certain members.</span></span>  
  
 [!code-vb[VbVbalrAccessModifiers#1](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/friend_1.vb)]  
  
## <a name="usage"></a><span data-ttu-id="bca0a-120">Utilisation</span><span class="sxs-lookup"><span data-stu-id="bca0a-120">Usage</span></span>  
 <span data-ttu-id="bca0a-121">Vous pouvez utiliser la `Friend` modificateur dans les contextes :</span><span class="sxs-lookup"><span data-stu-id="bca0a-121">You can use the `Friend` modifier in these contexts:</span></span>  
  
 [<span data-ttu-id="bca0a-122">Class (instruction)</span><span class="sxs-lookup"><span data-stu-id="bca0a-122">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="bca0a-123">Const (instruction)</span><span class="sxs-lookup"><span data-stu-id="bca0a-123">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="bca0a-124">Declare (instruction)</span><span class="sxs-lookup"><span data-stu-id="bca0a-124">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="bca0a-125">Delegate (instruction)</span><span class="sxs-lookup"><span data-stu-id="bca0a-125">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="bca0a-126">Dim (instruction)</span><span class="sxs-lookup"><span data-stu-id="bca0a-126">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="bca0a-127">Enum (instruction)</span><span class="sxs-lookup"><span data-stu-id="bca0a-127">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="bca0a-128">Event (instruction)</span><span class="sxs-lookup"><span data-stu-id="bca0a-128">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="bca0a-129">Function (instruction)</span><span class="sxs-lookup"><span data-stu-id="bca0a-129">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="bca0a-130">Interface (instruction)</span><span class="sxs-lookup"><span data-stu-id="bca0a-130">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="bca0a-131">Module (instruction)</span><span class="sxs-lookup"><span data-stu-id="bca0a-131">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)  
  
 [<span data-ttu-id="bca0a-132">Property (instruction)</span><span class="sxs-lookup"><span data-stu-id="bca0a-132">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="bca0a-133">Structure (instruction)</span><span class="sxs-lookup"><span data-stu-id="bca0a-133">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="bca0a-134">Sub (instruction)</span><span class="sxs-lookup"><span data-stu-id="bca0a-134">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="bca0a-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bca0a-135">See Also</span></span>  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>  
 [<span data-ttu-id="bca0a-136">Public</span><span class="sxs-lookup"><span data-stu-id="bca0a-136">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
 [<span data-ttu-id="bca0a-137">Protected</span><span class="sxs-lookup"><span data-stu-id="bca0a-137">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
 [<span data-ttu-id="bca0a-138">Private</span><span class="sxs-lookup"><span data-stu-id="bca0a-138">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
 [<span data-ttu-id="bca0a-139">Niveaux d’accès dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bca0a-139">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [<span data-ttu-id="bca0a-140">Procédures</span><span class="sxs-lookup"><span data-stu-id="bca0a-140">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [<span data-ttu-id="bca0a-141">Structures</span><span class="sxs-lookup"><span data-stu-id="bca0a-141">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="bca0a-142">Objets et classes</span><span class="sxs-lookup"><span data-stu-id="bca0a-142">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
