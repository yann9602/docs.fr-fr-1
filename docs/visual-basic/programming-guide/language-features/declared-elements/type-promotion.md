---
title: Promotion de type (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- declared elements [Visual Basic], scope
- visibility [Visual Basic], declared elements
- Partial keyword [Visual Basic], unexpected results with type promotion
- scope [Visual Basic], declared elements
- scope [Visual Basic], Visual Basic
- type promotion
- declared elements [Visual Basic], visibility
ms.assetid: 035eeb15-e4c5-4288-ab3c-6bd5d22f7051
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f3a55c023afe7afe96f862f0b3cbbdb03a15b902
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="type-promotion-visual-basic"></a><span data-ttu-id="c4831-102">Promotion de type (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c4831-102">Type Promotion (Visual Basic)</span></span>
<span data-ttu-id="c4831-103">Lorsque vous déclarez un élément de programmation dans un module, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] élève sa portée vers l’espace de noms contenant le module.</span><span class="sxs-lookup"><span data-stu-id="c4831-103">When you declare a programming element in a module, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] promotes its scope to the namespace containing the module.</span></span> <span data-ttu-id="c4831-104">Il s’agit en tant que *promotion de type*.</span><span class="sxs-lookup"><span data-stu-id="c4831-104">This is known as *type promotion*.</span></span>  
  
 <span data-ttu-id="c4831-105">L’exemple suivant montre une définition squelette d’un module et de deux membres de ce module.</span><span class="sxs-lookup"><span data-stu-id="c4831-105">The following example shows a skeleton definition of a module and two members of that module.</span></span>  
  
 [!code-vb[VbVbalrDeclaredElements#1](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_1.vb)]  
  
 <span data-ttu-id="c4831-106">Dans `projModule`, programmation éléments déclarés au niveau du module sont promus à `projNamespace`.</span><span class="sxs-lookup"><span data-stu-id="c4831-106">Within `projModule`, programming elements declared at module level are promoted to `projNamespace`.</span></span> <span data-ttu-id="c4831-107">Dans l’exemple précédent, `basicEnum` et `innerClass` sont promues, mais `numberSub` n’est pas, car il n’est pas déclaré au niveau du module.</span><span class="sxs-lookup"><span data-stu-id="c4831-107">In the preceding example, `basicEnum` and `innerClass` are promoted, but `numberSub` is not, because it is not declared at module level.</span></span>  
  
## <a name="effect-of-type-promotion"></a><span data-ttu-id="c4831-108">Promotion de Type</span><span class="sxs-lookup"><span data-stu-id="c4831-108">Effect of Type Promotion</span></span>  
 <span data-ttu-id="c4831-109">L’effet de la promotion de type est que la chaîne de qualification n’a pas besoin d’inclure le nom de module.</span><span class="sxs-lookup"><span data-stu-id="c4831-109">The effect of type promotion is that a qualification string does not need to include the module name.</span></span> <span data-ttu-id="c4831-110">L’exemple suivant effectue deux appels à la procédure dans l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="c4831-110">The following example makes two calls to the procedure in the preceding example.</span></span>  
  
 [!code-vb[VbVbalrDeclaredElements#2](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_2.vb)]  
  
 <span data-ttu-id="c4831-111">Dans l’exemple précédent, le premier appel utilise des chaînes de qualification complète.</span><span class="sxs-lookup"><span data-stu-id="c4831-111">In the preceding example, the first call uses complete qualification strings.</span></span> <span data-ttu-id="c4831-112">Toutefois, cela n’est pas nécessaire en raison de la promotion de type.</span><span class="sxs-lookup"><span data-stu-id="c4831-112">However, this is not necessary because of type promotion.</span></span> <span data-ttu-id="c4831-113">Le deuxième appel accède également aux membres du module sans inclure `projModule` dans les chaînes de qualification.</span><span class="sxs-lookup"><span data-stu-id="c4831-113">The second call also accesses the module's members without including `projModule` in the qualification strings.</span></span>  
  
## <a name="defeat-of-type-promotion"></a><span data-ttu-id="c4831-114">Invalidation de la Promotion de Type</span><span class="sxs-lookup"><span data-stu-id="c4831-114">Defeat of Type Promotion</span></span>  
 <span data-ttu-id="c4831-115">Si l’espace de noms comporte déjà un membre portant le même nom qu’un membre de module, la promotion de type est invalidée pour ce membre de module.</span><span class="sxs-lookup"><span data-stu-id="c4831-115">If the namespace already has a member with the same name as a module member, type promotion is defeated for that module member.</span></span> <span data-ttu-id="c4831-116">L’exemple suivant montre une définition squelette d’une énumération et d’un module au sein du même espace de noms.</span><span class="sxs-lookup"><span data-stu-id="c4831-116">The following example shows a skeleton definition of an enumeration and a module within the same namespace.</span></span>  
  
 [!code-vb[VbVbalrDeclaredElements#3](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_3.vb)]  
  
 <span data-ttu-id="c4831-117">Dans l’exemple précédent, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] ne peut pas promouvoir la classe `abc` à `thisNameSpace` , car il existe déjà une énumération du même nom au niveau de l’espace de noms.</span><span class="sxs-lookup"><span data-stu-id="c4831-117">In the preceding example, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] cannot promote class `abc` to `thisNameSpace` because there is already an enumeration with the same name at namespace level.</span></span> <span data-ttu-id="c4831-118">Pour accéder à `abcSub`, vous devez utiliser la chaîne de qualification complète `thisNamespace.thisModule.abc.abcSub`.</span><span class="sxs-lookup"><span data-stu-id="c4831-118">To access `abcSub`, you must use the full qualification string `thisNamespace.thisModule.abc.abcSub`.</span></span> <span data-ttu-id="c4831-119">Toutefois, la classe `xyz` est promue, vous pouvez accéder à `xyzSub` avec la chaîne de qualification plus courte `thisNamespace.xyz.xyzSub`.</span><span class="sxs-lookup"><span data-stu-id="c4831-119">However, class `xyz` is still promoted, and you can access `xyzSub` with the shorter qualification string `thisNamespace.xyz.xyzSub`.</span></span>  
  
### <a name="defeat-of-type-promotion-for-partial-types"></a><span data-ttu-id="c4831-120">Invalidation de la Promotion de Type pour les Types partiels</span><span class="sxs-lookup"><span data-stu-id="c4831-120">Defeat of Type Promotion for Partial Types</span></span>  
 <span data-ttu-id="c4831-121">Si une classe ou structure à l’intérieur d’un module utilise la [partielle](../../../../visual-basic/language-reference/modifiers/partial.md) (mot clé), la promotion de type est automatiquement invalidée pour cette classe ou structure, ou non de l’espace de noms a un membre portant le même nom.</span><span class="sxs-lookup"><span data-stu-id="c4831-121">If a class or structure inside a module uses the [Partial](../../../../visual-basic/language-reference/modifiers/partial.md) keyword, type promotion is automatically defeated for that class or structure, whether or not the namespace has a member with the same name.</span></span> <span data-ttu-id="c4831-122">Autres éléments dans le module sont toujours éligibles pour la promotion de type.</span><span class="sxs-lookup"><span data-stu-id="c4831-122">Other elements in the module are still eligible for type promotion.</span></span>  
  
 <span data-ttu-id="c4831-123">**Conséquences.**</span><span class="sxs-lookup"><span data-stu-id="c4831-123">**Consequences.**</span></span> <span data-ttu-id="c4831-124">Invalidation de la promotion de type d’une définition partielle peut provoquer des résultats inattendus et même des erreurs du compilateur.</span><span class="sxs-lookup"><span data-stu-id="c4831-124">Defeat of type promotion of a partial definition can cause unexpected results and even compiler errors.</span></span> <span data-ttu-id="c4831-125">L’exemple suivant montre des définitions partielles squelettes d’une classe, y compris à l’intérieur d’un module.</span><span class="sxs-lookup"><span data-stu-id="c4831-125">The following example shows skeleton partial definitions of a class, one of which is inside a module.</span></span>  
  
 [!code-vb[VbVbalrDeclaredElements#4](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_4.vb)]  
  
 <span data-ttu-id="c4831-126">Dans l’exemple précédent, le développeur peut s’attendre le compilateur fusionne les deux définitions partielles de `sampleClass`.</span><span class="sxs-lookup"><span data-stu-id="c4831-126">In the preceding example, the developer might expect the compiler to merge the two partial definitions of `sampleClass`.</span></span> <span data-ttu-id="c4831-127">Toutefois, le compilateur ne tient pas compte pour la définition partielle à l’intérieur de la promotion `sampleModule`.</span><span class="sxs-lookup"><span data-stu-id="c4831-127">However, the compiler does not consider promotion for the partial definition inside `sampleModule`.</span></span> <span data-ttu-id="c4831-128">Par conséquent, il tente de compiler deux classes distinctes, toutes deux nommées `sampleClass` , mais avec des chemins d’accès de qualification différents.</span><span class="sxs-lookup"><span data-stu-id="c4831-128">As a result, it attempts to compile two separate and distinct classes, both named `sampleClass` but with different qualification paths.</span></span>  
  
 <span data-ttu-id="c4831-129">Le compilateur fusionne des définitions partielles uniquement lorsque leurs chemins qualifiés complets sont identiques.</span><span class="sxs-lookup"><span data-stu-id="c4831-129">The compiler merges partial definitions only when their fully qualified paths are identical.</span></span>  
  
## <a name="recommendations"></a><span data-ttu-id="c4831-130">Recommandations</span><span class="sxs-lookup"><span data-stu-id="c4831-130">Recommendations</span></span>  
 <span data-ttu-id="c4831-131">Les recommandations suivantes représentent les bonnes pratiques de programmation.</span><span class="sxs-lookup"><span data-stu-id="c4831-131">The following recommendations represent good programming practice.</span></span>  
  
-   <span data-ttu-id="c4831-132">**Noms uniques.**</span><span class="sxs-lookup"><span data-stu-id="c4831-132">**Unique Names.**</span></span> <span data-ttu-id="c4831-133">Lorsque vous avez un contrôle total sur la dénomination des éléments de programmation, il est toujours de judicieux d’utiliser des noms uniques partout.</span><span class="sxs-lookup"><span data-stu-id="c4831-133">When you have full control over the naming of programming elements, it is always a good idea to use unique names everywhere.</span></span> <span data-ttu-id="c4831-134">Des noms identiques requièrent une qualification supplémentaire et peuvent rendre votre code plus difficile à lire.</span><span class="sxs-lookup"><span data-stu-id="c4831-134">Identical names require extra qualification and can make your code harder to read.</span></span> <span data-ttu-id="c4831-135">Elles peuvent entraîner des erreurs subtiles et des résultats inattendus.</span><span class="sxs-lookup"><span data-stu-id="c4831-135">They can also lead to subtle errors and unexpected results.</span></span>  
  
-   <span data-ttu-id="c4831-136">**Qualification complète.**</span><span class="sxs-lookup"><span data-stu-id="c4831-136">**Full Qualification.**</span></span> <span data-ttu-id="c4831-137">Lorsque vous travaillez avec des modules et autres éléments dans le même espace de noms, l’approche la plus sûre consiste à toujours utiliser la qualification complète pour tous les éléments de programmation.</span><span class="sxs-lookup"><span data-stu-id="c4831-137">When you are working with modules and other elements in the same namespace, the safest approach is to always use full qualification for all programming elements.</span></span> <span data-ttu-id="c4831-138">Si la promotion de type est invalidée pour un membre de module et que vous ne qualifiez pas complètement ce membre, vous pouvez accéder par inadvertance un élément de programmation différent.</span><span class="sxs-lookup"><span data-stu-id="c4831-138">If type promotion is defeated for a module member and you do not fully qualify that member, you could inadvertently access a different programming element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4831-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c4831-139">See Also</span></span>  
 [<span data-ttu-id="c4831-140">Module (instruction)</span><span class="sxs-lookup"><span data-stu-id="c4831-140">Module Statement</span></span>](../../../../visual-basic/language-reference/statements/module-statement.md)  
 [<span data-ttu-id="c4831-141">Namespace (instruction)</span><span class="sxs-lookup"><span data-stu-id="c4831-141">Namespace Statement</span></span>](../../../../visual-basic/language-reference/statements/namespace-statement.md)  
 [<span data-ttu-id="c4831-142">Partial</span><span class="sxs-lookup"><span data-stu-id="c4831-142">Partial</span></span>](../../../../visual-basic/language-reference/modifiers/partial.md)  
 [<span data-ttu-id="c4831-143">Portée dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c4831-143">Scope in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)  
 [<span data-ttu-id="c4831-144">Guide pratique : contrôler la portée d'une variable</span><span class="sxs-lookup"><span data-stu-id="c4831-144">How to: Control the Scope of a Variable</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-scope-of-a-variable.md)  
 [<span data-ttu-id="c4831-145">Références aux éléments déclarés</span><span class="sxs-lookup"><span data-stu-id="c4831-145">References to Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
