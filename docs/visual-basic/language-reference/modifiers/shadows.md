---
title: Shadows (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Shadows
- shadows
helpviewer_keywords:
- shadowing
- duplicate names [Visual Basic]
- scope [Visual Basic], shadowing
- Shadows keyword [Visual Basic]
- names [Visual Basic], shadowing
ms.assetid: 6bf687cd-0544-4797-b51b-911125ec57c6
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bb767c372cc05d61d569227af8eef0dc3c67489b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="shadows-visual-basic"></a><span data-ttu-id="26fde-102">Shadows (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="26fde-102">Shadows (Visual Basic)</span></span>
<span data-ttu-id="26fde-103">Spécifie qu’un élément de programmation déclaré redéclare et masque un élément portant le même nom ou un ensemble d’éléments surchargés, dans une classe de base.</span><span class="sxs-lookup"><span data-stu-id="26fde-103">Specifies that a declared programming element redeclares and hides an identically named element, or set of overloaded elements, in a base class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="26fde-104">Remarques</span><span class="sxs-lookup"><span data-stu-id="26fde-104">Remarks</span></span>  
 <span data-ttu-id="26fde-105">L’objectif principal d’une occultation (qui est également appelé *masquage par nom*) est de conserver la définition de vos membres de classe.</span><span class="sxs-lookup"><span data-stu-id="26fde-105">The main purpose of shadowing (which is also known as *hiding by name*) is to preserve the definition of your class members.</span></span> <span data-ttu-id="26fde-106">La classe de base peut subir une modification qui crée un élément avec le même nom que vous avez déjà défini.</span><span class="sxs-lookup"><span data-stu-id="26fde-106">The base class might undergo a change that creates an element with the same name as one you have already defined.</span></span> <span data-ttu-id="26fde-107">Si cela se produit, le `Shadows` modificateur force références de votre classe à être résolues vers le membre que vous avez défini, et non vers le nouvel élément de la classe de base.</span><span class="sxs-lookup"><span data-stu-id="26fde-107">If this happens, the `Shadows` modifier forces references through your class to be resolved to the member you defined, instead of to the new base class element.</span></span>  
  
 <span data-ttu-id="26fde-108">L'occultation et la substitution redéfinissent toutes les deux un élément hérité, mais il existe des différences importantes entre ces deux approches.</span><span class="sxs-lookup"><span data-stu-id="26fde-108">Both shadowing and overriding redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="26fde-109">Pour plus d’informations, consultez [occultation dans Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span><span class="sxs-lookup"><span data-stu-id="26fde-109">For more information, see [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="26fde-110">Règles</span><span class="sxs-lookup"><span data-stu-id="26fde-110">Rules</span></span>  
  
-   <span data-ttu-id="26fde-111">**Contexte de déclaration.**</span><span class="sxs-lookup"><span data-stu-id="26fde-111">**Declaration Context.**</span></span> <span data-ttu-id="26fde-112">Vous pouvez utiliser `Shadows` uniquement au niveau de la classe.</span><span class="sxs-lookup"><span data-stu-id="26fde-112">You can use `Shadows` only at class level.</span></span> <span data-ttu-id="26fde-113">Cela signifie que le contexte de déclaration pour un `Shadows` élément doit être une classe et ne peut pas être un fichier source, espace de noms, interface, un module, structure ou procédure.</span><span class="sxs-lookup"><span data-stu-id="26fde-113">This means the declaration context for a `Shadows` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>  
  
     <span data-ttu-id="26fde-114">Vous pouvez déclarer qu’un seul élément d’occultation dans une instruction de déclaration unique.</span><span class="sxs-lookup"><span data-stu-id="26fde-114">You can declare only one shadowing element in a single declaration statement.</span></span>  
  
-   <span data-ttu-id="26fde-115">**Modificateurs combinés.**</span><span class="sxs-lookup"><span data-stu-id="26fde-115">**Combined Modifiers.**</span></span> <span data-ttu-id="26fde-116">Vous ne pouvez pas spécifier `Shadows` avec `Overloads`, `Overrides`, ou `Static` dans la même déclaration.</span><span class="sxs-lookup"><span data-stu-id="26fde-116">You cannot specify `Shadows` together with `Overloads`, `Overrides`, or `Static` in the same declaration.</span></span>  
  
-   <span data-ttu-id="26fde-117">**Types d’élément.**</span><span class="sxs-lookup"><span data-stu-id="26fde-117">**Element Types.**</span></span> <span data-ttu-id="26fde-118">Vous pouvez occulter tout type d'élément déclaré par un autre type.</span><span class="sxs-lookup"><span data-stu-id="26fde-118">You can shadow any kind of declared element with any other kind.</span></span> <span data-ttu-id="26fde-119">Si vous masquez une propriété ou une procédure avec une autre propriété ou procédure, les paramètres et le type de retour n’ont pas correspondre à ceux de la propriété de classe de base ou la procédure.</span><span class="sxs-lookup"><span data-stu-id="26fde-119">If you shadow a property or procedure with another property or procedure, the parameters and the return type do not have to match those in the base class property or procedure.</span></span>  
  
-   <span data-ttu-id="26fde-120">**L’accès à.**</span><span class="sxs-lookup"><span data-stu-id="26fde-120">**Accessing.**</span></span> <span data-ttu-id="26fde-121">L’élément occulté dans la classe de base est normalement pas disponible à partir de la classe dérivée qui l’occulte.</span><span class="sxs-lookup"><span data-stu-id="26fde-121">The shadowed element in the base class is normally unavailable from within the derived class that shadows it.</span></span> <span data-ttu-id="26fde-122">Toutefois, les considérations suivantes s’appliquent.</span><span class="sxs-lookup"><span data-stu-id="26fde-122">However, the following considerations apply.</span></span>  
  
    -   <span data-ttu-id="26fde-123">Si l’élément d’occultation n’est pas accessible à partir du code qui fait référence à ce dernier, la référence est résolue à l’élément occulté.</span><span class="sxs-lookup"><span data-stu-id="26fde-123">If the shadowing element is not accessible from the code referring to it, the reference is resolved to the shadowed element.</span></span> <span data-ttu-id="26fde-124">Par exemple, si un `Private` élément occulte un élément de la classe de base, le code qui n’est pas autorisé à accéder à la `Private` élément accède à l’élément de la classe de base à la place.</span><span class="sxs-lookup"><span data-stu-id="26fde-124">For example, if a `Private` element shadows a base class element, code that does not have permission to access the `Private` element accesses the base class element instead.</span></span>  
  
    -   <span data-ttu-id="26fde-125">Si vous masquez un élément, vous pouvez toujours accéder à l’élément occulté via un objet déclaré avec le type de la classe de base.</span><span class="sxs-lookup"><span data-stu-id="26fde-125">If you shadow an element, you can still access the shadowed element through an object declared with the type of the base class.</span></span> <span data-ttu-id="26fde-126">Vous pouvez également y accéder via `MyBase`.</span><span class="sxs-lookup"><span data-stu-id="26fde-126">You can also access it through `MyBase`.</span></span>  
  
 <span data-ttu-id="26fde-127">Le modificateur `Shadows` peut être utilisé dans les contextes suivants :</span><span class="sxs-lookup"><span data-stu-id="26fde-127">The `Shadows` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="26fde-128">Class (instruction)</span><span class="sxs-lookup"><span data-stu-id="26fde-128">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="26fde-129">Const (instruction)</span><span class="sxs-lookup"><span data-stu-id="26fde-129">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="26fde-130">Declare (instruction)</span><span class="sxs-lookup"><span data-stu-id="26fde-130">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="26fde-131">Delegate (instruction)</span><span class="sxs-lookup"><span data-stu-id="26fde-131">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="26fde-132">Dim (instruction)</span><span class="sxs-lookup"><span data-stu-id="26fde-132">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="26fde-133">Enum (instruction)</span><span class="sxs-lookup"><span data-stu-id="26fde-133">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="26fde-134">Event (instruction)</span><span class="sxs-lookup"><span data-stu-id="26fde-134">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="26fde-135">Function (instruction)</span><span class="sxs-lookup"><span data-stu-id="26fde-135">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="26fde-136">Interface (instruction)</span><span class="sxs-lookup"><span data-stu-id="26fde-136">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="26fde-137">Property (instruction)</span><span class="sxs-lookup"><span data-stu-id="26fde-137">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="26fde-138">Structure (instruction)</span><span class="sxs-lookup"><span data-stu-id="26fde-138">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="26fde-139">Sub (instruction)</span><span class="sxs-lookup"><span data-stu-id="26fde-139">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="26fde-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="26fde-140">See Also</span></span>  
 [<span data-ttu-id="26fde-141">Shared</span><span class="sxs-lookup"><span data-stu-id="26fde-141">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)  
 [<span data-ttu-id="26fde-142">Static</span><span class="sxs-lookup"><span data-stu-id="26fde-142">Static</span></span>](../../../visual-basic/language-reference/modifiers/static.md)  
 [<span data-ttu-id="26fde-143">Private</span><span class="sxs-lookup"><span data-stu-id="26fde-143">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
 [<span data-ttu-id="26fde-144">Me, My, MyBase et MyClass</span><span class="sxs-lookup"><span data-stu-id="26fde-144">Me, My, MyBase, and MyClass</span></span>](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 [<span data-ttu-id="26fde-145">Éléments fondamentaux de l’héritage</span><span class="sxs-lookup"><span data-stu-id="26fde-145">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 [<span data-ttu-id="26fde-146">MustOverride</span><span class="sxs-lookup"><span data-stu-id="26fde-146">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)  
 [<span data-ttu-id="26fde-147">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="26fde-147">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)  
 [<span data-ttu-id="26fde-148">Overloads</span><span class="sxs-lookup"><span data-stu-id="26fde-148">Overloads</span></span>](../../../visual-basic/language-reference/modifiers/overloads.md)  
 [<span data-ttu-id="26fde-149">Overridable</span><span class="sxs-lookup"><span data-stu-id="26fde-149">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)  
 [<span data-ttu-id="26fde-150">Overrides</span><span class="sxs-lookup"><span data-stu-id="26fde-150">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)  
 [<span data-ttu-id="26fde-151">Occultation dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="26fde-151">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
