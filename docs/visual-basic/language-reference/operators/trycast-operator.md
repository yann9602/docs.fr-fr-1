---
title: "Opérateur TryCast (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.trycast
- trycast
helpviewer_keywords: TryCast keyword [Visual Basic]
ms.assetid: d1ef5d47-fef4-491e-b014-1d910628f65c
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b6be11b49eb3b9d98e3bf147e9b1026d4ffc860c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="trycast-operator-visual-basic"></a><span data-ttu-id="96f6e-102">Opérateur TryCast (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="96f6e-102">TryCast Operator (Visual Basic)</span></span>
<span data-ttu-id="96f6e-103">Introduit une opération de conversion de type qui ne lève pas d’exception.</span><span class="sxs-lookup"><span data-stu-id="96f6e-103">Introduces a type conversion operation that does not throw an exception.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="96f6e-104">Remarques</span><span class="sxs-lookup"><span data-stu-id="96f6e-104">Remarks</span></span>  
 <span data-ttu-id="96f6e-105">Si une tentative de conversion échoue, `CType` et `DirectCast` les lèvent une <xref:System.InvalidCastException> erreur.</span><span class="sxs-lookup"><span data-stu-id="96f6e-105">If an attempted conversion fails, `CType` and `DirectCast` both throw an <xref:System.InvalidCastException> error.</span></span> <span data-ttu-id="96f6e-106">Cela peut nuire aux performances de votre application.</span><span class="sxs-lookup"><span data-stu-id="96f6e-106">This can adversely affect the performance of your application.</span></span> <span data-ttu-id="96f6e-107">`TryCast`Retourne [rien](../../../visual-basic/language-reference/nothing.md), de sorte qu’au lieu de devoir gérer une exception possible, vous devez seulement tester le résultat retourné par rapport à `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="96f6e-107">`TryCast` returns [Nothing](../../../visual-basic/language-reference/nothing.md), so that instead of having to handle a possible exception, you need only test the returned result against `Nothing`.</span></span>  
  
 <span data-ttu-id="96f6e-108">Vous utilisez la `TryCast` mot clé de la même façon que vous utilisez le [CType, fonction](../../../visual-basic/language-reference/functions/ctype-function.md) et le [DirectCast, opérateur](../../../visual-basic/language-reference/operators/directcast-operator.md) (mot clé).</span><span class="sxs-lookup"><span data-stu-id="96f6e-108">You use the `TryCast` keyword the same way you use the [CType Function](../../../visual-basic/language-reference/functions/ctype-function.md) and the [DirectCast Operator](../../../visual-basic/language-reference/operators/directcast-operator.md) keyword.</span></span> <span data-ttu-id="96f6e-109">Vous fournissez une expression comme premier argument et un type pour convertir comme deuxième argument.</span><span class="sxs-lookup"><span data-stu-id="96f6e-109">You supply an expression as the first argument and a type to convert it to as the second argument.</span></span> <span data-ttu-id="96f6e-110">`TryCast`fonctionne uniquement sur les types référence, tels que les classes et interfaces.</span><span class="sxs-lookup"><span data-stu-id="96f6e-110">`TryCast` operates only on reference types, such as classes and interfaces.</span></span> <span data-ttu-id="96f6e-111">Il requiert une relation d’héritage ou d’implémentation entre les deux types.</span><span class="sxs-lookup"><span data-stu-id="96f6e-111">It requires an inheritance or implementation relationship between the two types.</span></span> <span data-ttu-id="96f6e-112">Cela signifie qu’un type doit hériter ou l’implémenter l’autre.</span><span class="sxs-lookup"><span data-stu-id="96f6e-112">This means that one type must inherit from or implement the other.</span></span>  
  
## <a name="errors-and-failures"></a><span data-ttu-id="96f6e-113">Erreurs et échecs</span><span class="sxs-lookup"><span data-stu-id="96f6e-113">Errors and Failures</span></span>  
 <span data-ttu-id="96f6e-114">`TryCast`génère une erreur du compilateur s’il détecte qu’il n’existe aucune relation d’héritage ou d’implémentation.</span><span class="sxs-lookup"><span data-stu-id="96f6e-114">`TryCast` generates a compiler error if it detects that no inheritance or implementation relationship exists.</span></span> <span data-ttu-id="96f6e-115">Mais l’absence d’une erreur du compilateur ne garantit pas une conversion réussie.</span><span class="sxs-lookup"><span data-stu-id="96f6e-115">But the lack of a compiler error does not guarantee a successful conversion.</span></span> <span data-ttu-id="96f6e-116">Si la conversion souhaitée est restrictive, elle peut échouer au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="96f6e-116">If the desired conversion is narrowing, it could fail at run time.</span></span> <span data-ttu-id="96f6e-117">Si cela se produit, `TryCast` retourne [rien](../../../visual-basic/language-reference/nothing.md).</span><span class="sxs-lookup"><span data-stu-id="96f6e-117">If this happens, `TryCast` returns [Nothing](../../../visual-basic/language-reference/nothing.md).</span></span>  
  
## <a name="conversion-keywords"></a><span data-ttu-id="96f6e-118">Mots clés de conversion</span><span class="sxs-lookup"><span data-stu-id="96f6e-118">Conversion Keywords</span></span>  
 <span data-ttu-id="96f6e-119">Une comparaison de mots clés de conversion de type est la suivante.</span><span class="sxs-lookup"><span data-stu-id="96f6e-119">A comparison of the type conversion keywords is as follows.</span></span>  
  
|<span data-ttu-id="96f6e-120">Mot clé</span><span class="sxs-lookup"><span data-stu-id="96f6e-120">Keyword</span></span>|<span data-ttu-id="96f6e-121">Types de données</span><span class="sxs-lookup"><span data-stu-id="96f6e-121">Data types</span></span>|<span data-ttu-id="96f6e-122">Relation d’argument</span><span class="sxs-lookup"><span data-stu-id="96f6e-122">Argument relationship</span></span>|<span data-ttu-id="96f6e-123">Échec d’exécution</span><span class="sxs-lookup"><span data-stu-id="96f6e-123">Run-time failure</span></span>|  
|---|---|---|---|  
|[<span data-ttu-id="96f6e-124">CType (fonction)</span><span class="sxs-lookup"><span data-stu-id="96f6e-124">CType Function</span></span>](../../../visual-basic/language-reference/functions/ctype-function.md)|<span data-ttu-id="96f6e-125">Les types de données</span><span class="sxs-lookup"><span data-stu-id="96f6e-125">Any data types</span></span>|<span data-ttu-id="96f6e-126">Conversion restrictive ou étendue doit être défini entre les deux types de données</span><span class="sxs-lookup"><span data-stu-id="96f6e-126">Widening or narrowing conversion must be defined between the two data types</span></span>|<span data-ttu-id="96f6e-127">Lève une exception<xref:System.InvalidCastException></span><span class="sxs-lookup"><span data-stu-id="96f6e-127">Throws <xref:System.InvalidCastException></span></span>|  
|[<span data-ttu-id="96f6e-128">DirectCast (opérateur)</span><span class="sxs-lookup"><span data-stu-id="96f6e-128">DirectCast Operator</span></span>](../../../visual-basic/language-reference/operators/directcast-operator.md)|<span data-ttu-id="96f6e-129">Les types de données</span><span class="sxs-lookup"><span data-stu-id="96f6e-129">Any data types</span></span>|<span data-ttu-id="96f6e-130">Un type doit hériter ou implémenter l’autre type</span><span class="sxs-lookup"><span data-stu-id="96f6e-130">One type must inherit from or implement the other type</span></span>|<span data-ttu-id="96f6e-131">Lève une exception<xref:System.InvalidCastException></span><span class="sxs-lookup"><span data-stu-id="96f6e-131">Throws <xref:System.InvalidCastException></span></span>|  
|`TryCast`|<span data-ttu-id="96f6e-132">Seuls les types référence</span><span class="sxs-lookup"><span data-stu-id="96f6e-132">Reference types only</span></span>|<span data-ttu-id="96f6e-133">Un type doit hériter ou implémenter l’autre type</span><span class="sxs-lookup"><span data-stu-id="96f6e-133">One type must inherit from or implement the other type</span></span>|<span data-ttu-id="96f6e-134">Retourne [Nothing](../../../visual-basic/language-reference/nothing.md)</span><span class="sxs-lookup"><span data-stu-id="96f6e-134">Returns [Nothing](../../../visual-basic/language-reference/nothing.md)</span></span>|  
  
## <a name="example"></a><span data-ttu-id="96f6e-135">Exemple</span><span class="sxs-lookup"><span data-stu-id="96f6e-135">Example</span></span>  
 <span data-ttu-id="96f6e-136">L'exemple suivant montre comment utiliser `TryCast`.</span><span class="sxs-lookup"><span data-stu-id="96f6e-136">The following example shows how to use `TryCast`.</span></span>  
  
 [!code-vb[VbVbalrKeywords#6](../../../visual-basic/language-reference/codesnippet/VisualBasic/trycast-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="96f6e-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="96f6e-137">See Also</span></span>  
 [<span data-ttu-id="96f6e-138">Conversions étendues et restrictives</span><span class="sxs-lookup"><span data-stu-id="96f6e-138">Widening and Narrowing Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [<span data-ttu-id="96f6e-139">Conversions implicites et explicites</span><span class="sxs-lookup"><span data-stu-id="96f6e-139">Implicit and Explicit Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
