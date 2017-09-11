---
title: Type de Promotion (Visual Basic) | Documents Microsoft
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- declared elements, scope
- visibility, declared elements
- Partial keyword, unexpected results with type promotion
- scope, declared elements
- scope, Visual Basic
- type promotion
- declared elements, visibility
ms.assetid: 035eeb15-e4c5-4288-ab3c-6bd5d22f7051
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
ms.openlocfilehash: 383f4b1d29e9bbf81eee44bf78762a80aea9eb36
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="type-promotion-visual-basic"></a><span data-ttu-id="4fcdd-102">Promotion de type (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4fcdd-102">Type Promotion (Visual Basic)</span></span>
<span data-ttu-id="4fcdd-103">Lorsque vous déclarez un élément de programmation dans un module, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] élève sa portée vers l’espace de noms contenant le module.</span><span class="sxs-lookup"><span data-stu-id="4fcdd-103">When you declare a programming element in a module, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] promotes its scope to the namespace containing the module.</span></span> <span data-ttu-id="4fcdd-104">Il s’agit en tant que *promotion de type*.</span><span class="sxs-lookup"><span data-stu-id="4fcdd-104">This is known as *type promotion*.</span></span>  
  
 <span data-ttu-id="4fcdd-105">L’exemple suivant montre une définition squelette d’un module et deux membres de ce module.</span><span class="sxs-lookup"><span data-stu-id="4fcdd-105">The following example shows a skeleton definition of a module and two members of that module.</span></span>  
  
 <span data-ttu-id="4fcdd-106">[!code-vb[VbVbalrDeclaredElements n °&1;](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="4fcdd-106">[!code-vb[VbVbalrDeclaredElements#1](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_1.vb)]</span></span>  
  
 <span data-ttu-id="4fcdd-107">Dans `projModule`, programmation éléments déclarés au niveau du module sont promus à `projNamespace`.</span><span class="sxs-lookup"><span data-stu-id="4fcdd-107">Within `projModule`, programming elements declared at module level are promoted to `projNamespace`.</span></span> <span data-ttu-id="4fcdd-108">Dans l’exemple précédent, `basicEnum` et `innerClass` sont promues, mais `numberSub` n’est pas, car il n’est pas déclaré au niveau du module.</span><span class="sxs-lookup"><span data-stu-id="4fcdd-108">In the preceding example, `basicEnum` and `innerClass` are promoted, but `numberSub` is not, because it is not declared at module level.</span></span>  
  
## <a name="effect-of-type-promotion"></a><span data-ttu-id="4fcdd-109">Promotion de Type</span><span class="sxs-lookup"><span data-stu-id="4fcdd-109">Effect of Type Promotion</span></span>  
 <span data-ttu-id="4fcdd-110">L’effet de la promotion de type est que la chaîne de qualification n’a pas besoin d’inclure le nom du module.</span><span class="sxs-lookup"><span data-stu-id="4fcdd-110">The effect of type promotion is that a qualification string does not need to include the module name.</span></span> <span data-ttu-id="4fcdd-111">L’exemple suivant effectue deux appels à la procédure dans l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="4fcdd-111">The following example makes two calls to the procedure in the preceding example.</span></span>  
  
 <span data-ttu-id="4fcdd-112">[!code-vb[VbVbalrDeclaredElements n °&2;](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="4fcdd-112">[!code-vb[VbVbalrDeclaredElements#2](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_2.vb)]</span></span>  
  
 <span data-ttu-id="4fcdd-113">Dans l’exemple précédent, le premier appel utilise des chaînes de qualification complètes.</span><span class="sxs-lookup"><span data-stu-id="4fcdd-113">In the preceding example, the first call uses complete qualification strings.</span></span> <span data-ttu-id="4fcdd-114">Toutefois, cela n’est pas nécessaire en raison de la promotion de type.</span><span class="sxs-lookup"><span data-stu-id="4fcdd-114">However, this is not necessary because of type promotion.</span></span> <span data-ttu-id="4fcdd-115">Le deuxième appel accède également aux membres du module sans inclure `projModule` dans les chaînes de qualification.</span><span class="sxs-lookup"><span data-stu-id="4fcdd-115">The second call also accesses the module's members without including `projModule` in the qualification strings.</span></span>  
  
## <a name="defeat-of-type-promotion"></a><span data-ttu-id="4fcdd-116">Invalidation de la Promotion de Type</span><span class="sxs-lookup"><span data-stu-id="4fcdd-116">Defeat of Type Promotion</span></span>  
 <span data-ttu-id="4fcdd-117">Si l’espace de noms possède déjà un membre portant le même nom qu’un membre de module, la promotion de type est invalidée pour ce membre de module.</span><span class="sxs-lookup"><span data-stu-id="4fcdd-117">If the namespace already has a member with the same name as a module member, type promotion is defeated for that module member.</span></span> <span data-ttu-id="4fcdd-118">L’exemple suivant montre une définition squelette d’une énumération et d’un module dans le même espace de noms.</span><span class="sxs-lookup"><span data-stu-id="4fcdd-118">The following example shows a skeleton definition of an enumeration and a module within the same namespace.</span></span>  
  
 <span data-ttu-id="4fcdd-119">[!code-vb[VbVbalrDeclaredElements n °&3;](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="4fcdd-119">[!code-vb[VbVbalrDeclaredElements#3](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_3.vb)]</span></span>  
  
 <span data-ttu-id="4fcdd-120">Dans l’exemple précédent, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] ne peut pas promouvoir la classe `abc` à `thisNameSpace` car il existe déjà une énumération du même nom au niveau de l’espace de noms.</span><span class="sxs-lookup"><span data-stu-id="4fcdd-120">In the preceding example, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] cannot promote class `abc` to `thisNameSpace` because there is already an enumeration with the same name at namespace level.</span></span> <span data-ttu-id="4fcdd-121">Pour accéder à `abcSub`, vous devez utiliser la chaîne de qualification complète `thisNamespace.thisModule.abc.abcSub`.</span><span class="sxs-lookup"><span data-stu-id="4fcdd-121">To access `abcSub`, you must use the full qualification string `thisNamespace.thisModule.abc.abcSub`.</span></span> <span data-ttu-id="4fcdd-122">Toutefois, la classe `xyz` est promue et vous pouvez accéder aux `xyzSub` avec la chaîne de qualification plus courte `thisNamespace.xyz.xyzSub`.</span><span class="sxs-lookup"><span data-stu-id="4fcdd-122">However, class `xyz` is still promoted, and you can access `xyzSub` with the shorter qualification string `thisNamespace.xyz.xyzSub`.</span></span>  
  
### <a name="defeat-of-type-promotion-for-partial-types"></a><span data-ttu-id="4fcdd-123">Invalidation de la Promotion de Type pour les Types partiels</span><span class="sxs-lookup"><span data-stu-id="4fcdd-123">Defeat of Type Promotion for Partial Types</span></span>  
 <span data-ttu-id="4fcdd-124">Si une classe ou structure à l’intérieur d’un module utilise le [partielle](../../../../visual-basic/language-reference/modifiers/partial.md) (mot clé), la promotion de type est automatiquement invalidée pour cette classe ou structure, ou non de l’espace de noms possède un membre portant le même nom.</span><span class="sxs-lookup"><span data-stu-id="4fcdd-124">If a class or structure inside a module uses the [Partial](../../../../visual-basic/language-reference/modifiers/partial.md) keyword, type promotion is automatically defeated for that class or structure, whether or not the namespace has a member with the same name.</span></span> <span data-ttu-id="4fcdd-125">D’autres éléments dans le module sont toujours éligibles pour la promotion de type.</span><span class="sxs-lookup"><span data-stu-id="4fcdd-125">Other elements in the module are still eligible for type promotion.</span></span>  
  
 <span data-ttu-id="4fcdd-126">**Conséquences.**</span><span class="sxs-lookup"><span data-stu-id="4fcdd-126">**Consequences.**</span></span> <span data-ttu-id="4fcdd-127">Invalidation de la promotion de type d’une définition partielle peut provoquer des résultats inattendus et même des erreurs du compilateur.</span><span class="sxs-lookup"><span data-stu-id="4fcdd-127">Defeat of type promotion of a partial definition can cause unexpected results and even compiler errors.</span></span> <span data-ttu-id="4fcdd-128">L’exemple suivant montre des définitions squelettes partielles d’une classe, y compris à l’intérieur d’un module.</span><span class="sxs-lookup"><span data-stu-id="4fcdd-128">The following example shows skeleton partial definitions of a class, one of which is inside a module.</span></span>  
  
 <span data-ttu-id="4fcdd-129">[!code-vb[VbVbalrDeclaredElements n °&4;](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="4fcdd-129">[!code-vb[VbVbalrDeclaredElements#4](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_4.vb)]</span></span>  
  
 <span data-ttu-id="4fcdd-130">Dans l’exemple précédent, le développeur peut s’attendre le compilateur fusionne les deux définitions partielles de `sampleClass`.</span><span class="sxs-lookup"><span data-stu-id="4fcdd-130">In the preceding example, the developer might expect the compiler to merge the two partial definitions of `sampleClass`.</span></span> <span data-ttu-id="4fcdd-131">Toutefois, le compilateur ne considère pas de promotion pour la définition partielle à l’intérieur de `sampleModule`.</span><span class="sxs-lookup"><span data-stu-id="4fcdd-131">However, the compiler does not consider promotion for the partial definition inside `sampleModule`.</span></span> <span data-ttu-id="4fcdd-132">Par conséquent, il tente de compiler deux classes distinctes, toutes deux nommées `sampleClass` , mais avec des chemins d’accès de qualification différents.</span><span class="sxs-lookup"><span data-stu-id="4fcdd-132">As a result, it attempts to compile two separate and distinct classes, both named `sampleClass` but with different qualification paths.</span></span>  
  
 <span data-ttu-id="4fcdd-133">Le compilateur fusionne des définitions partielles uniquement lorsque leurs chemins qualifiés complets sont identiques.</span><span class="sxs-lookup"><span data-stu-id="4fcdd-133">The compiler merges partial definitions only when their fully qualified paths are identical.</span></span>  
  
## <a name="recommendations"></a><span data-ttu-id="4fcdd-134">Recommandations</span><span class="sxs-lookup"><span data-stu-id="4fcdd-134">Recommendations</span></span>  
 <span data-ttu-id="4fcdd-135">Les recommandations suivantes représentent les bonnes pratiques de programmation.</span><span class="sxs-lookup"><span data-stu-id="4fcdd-135">The following recommendations represent good programming practice.</span></span>  
  
-   <span data-ttu-id="4fcdd-136">**Noms uniques.**</span><span class="sxs-lookup"><span data-stu-id="4fcdd-136">**Unique Names.**</span></span> <span data-ttu-id="4fcdd-137">Lorsque vous avez un contrôle total sur l’appellation des éléments de programmation, il est toujours judicieux d’utiliser des noms uniques partout.</span><span class="sxs-lookup"><span data-stu-id="4fcdd-137">When you have full control over the naming of programming elements, it is always a good idea to use unique names everywhere.</span></span> <span data-ttu-id="4fcdd-138">Des noms identiques requièrent une qualification supplémentaire et peuvent rendre votre code plus difficile à lire.</span><span class="sxs-lookup"><span data-stu-id="4fcdd-138">Identical names require extra qualification and can make your code harder to read.</span></span> <span data-ttu-id="4fcdd-139">Elles peuvent entraîner des erreurs subtiles et des résultats inattendus.</span><span class="sxs-lookup"><span data-stu-id="4fcdd-139">They can also lead to subtle errors and unexpected results.</span></span>  
  
-   <span data-ttu-id="4fcdd-140">**Qualification complète.**</span><span class="sxs-lookup"><span data-stu-id="4fcdd-140">**Full Qualification.**</span></span> <span data-ttu-id="4fcdd-141">Lorsque vous travaillez avec des modules et d’autres éléments dans le même espace de noms, l’approche la plus sûre consiste à toujours utiliser la qualification complète pour tous les éléments de programmation.</span><span class="sxs-lookup"><span data-stu-id="4fcdd-141">When you are working with modules and other elements in the same namespace, the safest approach is to always use full qualification for all programming elements.</span></span> <span data-ttu-id="4fcdd-142">Si la promotion de type est invalidée pour un membre de module et vous ne qualifiez pas complètement ce membre, vous pouvez accéder par inadvertance un élément de programmation différents.</span><span class="sxs-lookup"><span data-stu-id="4fcdd-142">If type promotion is defeated for a module member and you do not fully qualify that member, you could inadvertently access a different programming element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fcdd-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4fcdd-143">See Also</span></span>  
 <span data-ttu-id="4fcdd-144">[Module, instruction](../../../../visual-basic/language-reference/statements/module-statement.md) </span><span class="sxs-lookup"><span data-stu-id="4fcdd-144">[Module Statement](../../../../visual-basic/language-reference/statements/module-statement.md) </span></span>  
<span data-ttu-id="4fcdd-145"> [Déclaration de Namespace](../../../../visual-basic/language-reference/statements/namespace-statement.md) </span><span class="sxs-lookup"><span data-stu-id="4fcdd-145"> [Namespace Statement](../../../../visual-basic/language-reference/statements/namespace-statement.md) </span></span>  
<span data-ttu-id="4fcdd-146"> [Partielle](../../../../visual-basic/language-reference/modifiers/partial.md) </span><span class="sxs-lookup"><span data-stu-id="4fcdd-146"> [Partial](../../../../visual-basic/language-reference/modifiers/partial.md) </span></span>  
<span data-ttu-id="4fcdd-147"> [Portée dans Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md) </span><span class="sxs-lookup"><span data-stu-id="4fcdd-147"> [Scope in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md) </span></span>  
<span data-ttu-id="4fcdd-148"> [Comment : contrôler la portée d’une Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-scope-of-a-variable.md) </span><span class="sxs-lookup"><span data-stu-id="4fcdd-148"> [How to: Control the Scope of a Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-scope-of-a-variable.md) </span></span>  
<span data-ttu-id="4fcdd-149"> [Références aux éléments déclarés](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)</span><span class="sxs-lookup"><span data-stu-id="4fcdd-149"> [References to Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)</span></span>
