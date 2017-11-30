---
title: Overridable (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- Overridable
- vb.Overridable
helpviewer_keywords:
- elements [Visual Basic], concrete
- properties [Visual Basic], redefining
- overriding, Overridable keyword
- elements [Visual Basic], virtual
- virtual [elements VB]
- procedures [Visual Basic], overriding
- concrete [elements VB]
- procedures [Visual Basic], redefining
- Overridable keyword [Visual Basic]
- properties [Visual Basic], overriding
ms.assetid: 612581e7-8a4c-4a5d-beff-3402fffa6f35
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f7d5dd33f8591be1b4305e954e55e035882626c6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="overridable-visual-basic"></a><span data-ttu-id="da6b5-102">Overridable (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="da6b5-102">Overridable (Visual Basic)</span></span>
<span data-ttu-id="da6b5-103">Spécifie qu’une propriété ou procédure peut être remplacée par une propriété portant le même nommée ou de la procédure dans une classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="da6b5-103">Specifies that a property or procedure can be overridden by an identically named property or procedure in a derived class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="da6b5-104">Remarques</span><span class="sxs-lookup"><span data-stu-id="da6b5-104">Remarks</span></span>  
 <span data-ttu-id="da6b5-105">Le `Overridable` modificateur permet à une propriété ou une méthode dans une classe de substitution dans une classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="da6b5-105">The `Overridable` modifier allows a property or method in a class to be overridden in a derived class.</span></span> <span data-ttu-id="da6b5-106">Le [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md) modificateur empêche une propriété ou méthode d’être substituée dans une classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="da6b5-106">The [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md) modifier prevents a property or method from being overridden in a derived class.</span></span>  <span data-ttu-id="da6b5-107">Pour plus d’informations, consultez [Concepts de base de l’héritage](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span><span class="sxs-lookup"><span data-stu-id="da6b5-107">For more information, see [Inheritance Basics](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span></span>  
  
 <span data-ttu-id="da6b5-108">Si le `Overridable` ou `NotOverridable` modificateur n’est pas spécifié, le paramètre par défaut varie selon que la propriété ou méthode se substitue à une méthode ou propriété de classe de base.</span><span class="sxs-lookup"><span data-stu-id="da6b5-108">If the `Overridable` or `NotOverridable` modifier is not specified, the default setting depends on whether the property or method overrides a base class property or method.</span></span> <span data-ttu-id="da6b5-109">Si la propriété ou méthode substitue une méthode ou propriété de classe de base, le paramètre par défaut est `Overridable`; sinon, elle est `NotOverridable`.</span><span class="sxs-lookup"><span data-stu-id="da6b5-109">If the property or method overrides a base class property or method, the default setting is `Overridable`; otherwise, it is `NotOverridable`.</span></span>  
  
 <span data-ttu-id="da6b5-110">Vous pouvez masquer ou remplacer pour redéfinir un élément hérité, mais il existe des différences importantes entre les deux approches.</span><span class="sxs-lookup"><span data-stu-id="da6b5-110">You can shadow or override to redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="da6b5-111">Pour plus d’informations, consultez [occultation dans Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span><span class="sxs-lookup"><span data-stu-id="da6b5-111">For more information, see [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).</span></span>  
  
 <span data-ttu-id="da6b5-112">Un élément qui peut être substitué est parfois appelée une *virtuels* élément.</span><span class="sxs-lookup"><span data-stu-id="da6b5-112">An element that can be overridden is sometimes referred to as a *virtual* element.</span></span> <span data-ttu-id="da6b5-113">Si elle peut être remplacée, mais pas nécessairement être, il est parfois également appelé un *concrète* élément.</span><span class="sxs-lookup"><span data-stu-id="da6b5-113">If it can be overridden, but does not have to be, it is sometimes also called a *concrete* element.</span></span>  
  
 <span data-ttu-id="da6b5-114">Vous pouvez utiliser `Overridable` uniquement dans une instruction de déclaration de propriété ou de procédure.</span><span class="sxs-lookup"><span data-stu-id="da6b5-114">You can use `Overridable` only in a property or procedure declaration statement.</span></span>  
  
## <a name="combined-modifiers"></a><span data-ttu-id="da6b5-115">Modificateurs combinés</span><span class="sxs-lookup"><span data-stu-id="da6b5-115">Combined Modifiers</span></span>  
 <span data-ttu-id="da6b5-116">Vous ne pouvez pas spécifier `Overridable` ou `NotOverridable` pour un `Private` (méthode).</span><span class="sxs-lookup"><span data-stu-id="da6b5-116">You cannot specify `Overridable` or `NotOverridable` for a `Private` method.</span></span>  
  
 <span data-ttu-id="da6b5-117">Vous ne pouvez pas spécifier `Overridable` avec `MustOverride`, `NotOverridable`, ou `Shared` dans la même déclaration.</span><span class="sxs-lookup"><span data-stu-id="da6b5-117">You cannot specify `Overridable` together with `MustOverride`, `NotOverridable`, or `Shared` in the same declaration.</span></span>  
  
 <span data-ttu-id="da6b5-118">Comme un élément de substitution est implicitement substituable, vous ne pouvez pas combiner `Overridable` avec `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="da6b5-118">Because an overriding element is implicitly overridable, you cannot combine `Overridable` with `Overrides`.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="da6b5-119">Utilisation</span><span class="sxs-lookup"><span data-stu-id="da6b5-119">Usage</span></span>  
 <span data-ttu-id="da6b5-120">Le modificateur `Overridable` peut être utilisé dans les contextes suivants :</span><span class="sxs-lookup"><span data-stu-id="da6b5-120">The `Overridable` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="da6b5-121">Function (instruction)</span><span class="sxs-lookup"><span data-stu-id="da6b5-121">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="da6b5-122">Property (instruction)</span><span class="sxs-lookup"><span data-stu-id="da6b5-122">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="da6b5-123">Sub (instruction)</span><span class="sxs-lookup"><span data-stu-id="da6b5-123">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="da6b5-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="da6b5-124">See Also</span></span>  
 [<span data-ttu-id="da6b5-125">Modificateurs</span><span class="sxs-lookup"><span data-stu-id="da6b5-125">Modifiers</span></span>](../../../visual-basic/language-reference/modifiers/index.md)  
 [<span data-ttu-id="da6b5-126">Éléments fondamentaux de l’héritage</span><span class="sxs-lookup"><span data-stu-id="da6b5-126">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 [<span data-ttu-id="da6b5-127">MustOverride</span><span class="sxs-lookup"><span data-stu-id="da6b5-127">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)  
 [<span data-ttu-id="da6b5-128">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="da6b5-128">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)  
 [<span data-ttu-id="da6b5-129">Overrides</span><span class="sxs-lookup"><span data-stu-id="da6b5-129">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)  
 [<span data-ttu-id="da6b5-130">Mots clés</span><span class="sxs-lookup"><span data-stu-id="da6b5-130">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)  
 [<span data-ttu-id="da6b5-131">Occultation dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="da6b5-131">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
