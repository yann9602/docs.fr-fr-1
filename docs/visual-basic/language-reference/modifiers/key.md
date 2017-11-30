---
title: Key (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.AnonymousKey
helpviewer_keywords:
- anonymous types [Visual Basic], key
- Key [Visual Basic]
- Key keyword [Visual Basic]
ms.assetid: 7697a928-7d14-4430-a72a-c9e96e8d6c11
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 20dbe4e67fb3e415ba0202555ace7fd5afed68d2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="key-visual-basic"></a><span data-ttu-id="489b5-102">Key (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="489b5-102">Key (Visual Basic)</span></span>
<span data-ttu-id="489b5-103">Le `Key` mot clé permet de spécifier le comportement des propriétés de types anonymes.</span><span class="sxs-lookup"><span data-stu-id="489b5-103">The `Key` keyword enables you to specify behavior for properties of anonymous types.</span></span> <span data-ttu-id="489b5-104">Seules les propriétés que vous désignez comme propriétés de clé participent aux tests d’égalité entre les instances de type anonyme, ou un calcul de valeurs de code de hachage.</span><span class="sxs-lookup"><span data-stu-id="489b5-104">Only properties you designate as key properties participate in tests of equality between anonymous type instances, or calculation of hash code values.</span></span> <span data-ttu-id="489b5-105">Les valeurs des propriétés de clé ne peut pas être modifiés.</span><span class="sxs-lookup"><span data-stu-id="489b5-105">The values of key properties cannot be changed.</span></span>  
  
 <span data-ttu-id="489b5-106">Vous désignez une propriété d’un type anonyme comme propriété de clé en plaçant le mot clé `Key` devant sa déclaration dans la liste d’initialisation.</span><span class="sxs-lookup"><span data-stu-id="489b5-106">You designate a property of an anonymous type as a key property by placing the keyword `Key` in front of its declaration in the initialization list.</span></span> <span data-ttu-id="489b5-107">Dans l’exemple suivant, `Airline` et `FlightNo` sont des propriétés de clé, mais `Gate` n’est pas.</span><span class="sxs-lookup"><span data-stu-id="489b5-107">In the following example, `Airline` and `FlightNo` are key properties, but `Gate` is not.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#26](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_1.vb)]  
  
 <span data-ttu-id="489b5-108">Lorsqu’un nouveau type anonyme est créé, il hérite directement de <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="489b5-108">When a new anonymous type is created, it inherits directly from <xref:System.Object>.</span></span> <span data-ttu-id="489b5-109">Le compilateur substitue trois membres hérités : <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>, et <xref:System.Object.ToString%2A>.</span><span class="sxs-lookup"><span data-stu-id="489b5-109">The compiler overrides three inherited members: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>, and <xref:System.Object.ToString%2A>.</span></span> <span data-ttu-id="489b5-110">Le code de substitution qui est généré pour <xref:System.Object.Equals%2A> et <xref:System.Object.GetHashCode%2A> est basée sur les propriétés de clé.</span><span class="sxs-lookup"><span data-stu-id="489b5-110">The override code that is produced for <xref:System.Object.Equals%2A> and <xref:System.Object.GetHashCode%2A> is based on key properties.</span></span> <span data-ttu-id="489b5-111">S’il en existe aucune propriété de clé dans le type, <xref:System.Object.GetHashCode%2A> et <xref:System.Object.Equals%2A> ne sont pas substitués.</span><span class="sxs-lookup"><span data-stu-id="489b5-111">If there are no key properties in the type, <xref:System.Object.GetHashCode%2A> and <xref:System.Object.Equals%2A> are not overridden.</span></span>  
  
## <a name="equality"></a><span data-ttu-id="489b5-112">Égalité</span><span class="sxs-lookup"><span data-stu-id="489b5-112">Equality</span></span>  
 <span data-ttu-id="489b5-113">Deux instances de type anonyme sont égales si elles sont des instances du même type et si les valeurs de leurs propriétés de clé sont égales.</span><span class="sxs-lookup"><span data-stu-id="489b5-113">Two anonymous type instances are equal if they are instances of the same type and if the values of their key properties are equal.</span></span> <span data-ttu-id="489b5-114">Dans les exemples suivants, `flight2` est égal à `flight1` à partir de l’exemple précédent, car ce sont des instances du même anonyme type et ils ont des valeurs correspondantes pour leurs propriétés de clé.</span><span class="sxs-lookup"><span data-stu-id="489b5-114">In the following examples, `flight2` is equal to `flight1` from the previous example because they are instances of the same anonymous type and they have matching values for their key properties.</span></span> <span data-ttu-id="489b5-115">Toutefois, `flight3` n’est pas égal à `flight1` , car il a une valeur différente pour une propriété de clé, `FlightNo`.</span><span class="sxs-lookup"><span data-stu-id="489b5-115">However, `flight3` is not equal to `flight1` because it has a different value for a key property, `FlightNo`.</span></span> <span data-ttu-id="489b5-116">Instance `flight4` n’est pas du même type que `flight1` car ils désignent des propriétés différentes comme propriétés de clé.</span><span class="sxs-lookup"><span data-stu-id="489b5-116">Instance `flight4` is not the same type as `flight1` because they designate different properties as key properties.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#27](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_2.vb)]  
  
 <span data-ttu-id="489b5-117">Si deux instances sont déclarées avec uniquement des propriétés non-clés, identiques dans nom, type, ordre et valeur, les deux instances ne sont pas égaux.</span><span class="sxs-lookup"><span data-stu-id="489b5-117">If two instances are declared with only non-key properties, identical in name, type, order, and value, the two instances are not equal.</span></span> <span data-ttu-id="489b5-118">Une instance sans propriété de clé est uniquement égale à elle-même.</span><span class="sxs-lookup"><span data-stu-id="489b5-118">An instance without key properties is equal only to itself.</span></span>  
  
 <span data-ttu-id="489b5-119">Pour plus d’informations sur les conditions dans lesquelles deux instances de type anonyme sont des instances du même type anonyme, consultez [Types anonymes](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="489b5-119">For more information about the conditions under which two anonymous type instances are instances of the same anonymous type, see [Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>  
  
## <a name="hash-code-calculation"></a><span data-ttu-id="489b5-120">Calcul de Code de hachage</span><span class="sxs-lookup"><span data-stu-id="489b5-120">Hash Code Calculation</span></span>  
 <span data-ttu-id="489b5-121">Comme <xref:System.Object.Equals%2A>, la fonction de hachage qui est définie dans <xref:System.Object.GetHashCode%2A> pour un type anonyme est basé sur les propriétés de clé du type.</span><span class="sxs-lookup"><span data-stu-id="489b5-121">Like <xref:System.Object.Equals%2A>, the hash function that is defined in <xref:System.Object.GetHashCode%2A> for an anonymous type is based on the key properties of the type.</span></span> <span data-ttu-id="489b5-122">Les exemples suivants illustrent l’interaction entre les propriétés de clé et le hachage des valeurs de code.</span><span class="sxs-lookup"><span data-stu-id="489b5-122">The following examples show the interaction between key properties and hash code values.</span></span>  
  
 <span data-ttu-id="489b5-123">Les instances d’un type anonyme qui ont les mêmes valeurs pour toutes les propriétés de clé ont la même valeur de code de hachage, même si des propriétés non-clés n’ont pas de valeurs correspondantes.</span><span class="sxs-lookup"><span data-stu-id="489b5-123">Instances of an anonymous type that have the same values for all key properties have the same hash code value, even if non-key properties do not have matching values.</span></span> <span data-ttu-id="489b5-124">L’instruction suivante retourne `True`.</span><span class="sxs-lookup"><span data-stu-id="489b5-124">The following statement returns `True`.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#37](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_3.vb)]  
  
 <span data-ttu-id="489b5-125">Les instances d’un type anonyme qui ont des valeurs différentes pour une ou plusieurs propriétés de clé ont des valeurs de code de hachage différent.</span><span class="sxs-lookup"><span data-stu-id="489b5-125">Instances of an anonymous type that have different values for one or more key properties have different hash code values.</span></span> <span data-ttu-id="489b5-126">L’instruction suivante retourne `False`.</span><span class="sxs-lookup"><span data-stu-id="489b5-126">The following statement returns `False`.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#38](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_4.vb)]  
  
 <span data-ttu-id="489b5-127">Instances de types anonymes qui désignent des propriétés différentes comme propriétés de clé ne sont pas des instances du même type.</span><span class="sxs-lookup"><span data-stu-id="489b5-127">Instances of anonymous types that designate different properties as key properties are not instances of the same type.</span></span> <span data-ttu-id="489b5-128">Ils ont des valeurs de code de hachage différentes même lorsque les noms et valeurs de toutes les propriétés sont identiques.</span><span class="sxs-lookup"><span data-stu-id="489b5-128">They have different hash code values even when the names and values of all properties are the same.</span></span> <span data-ttu-id="489b5-129">L’instruction suivante retourne `False`.</span><span class="sxs-lookup"><span data-stu-id="489b5-129">The following statement returns `False`.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#39](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_5.vb)]  
  
## <a name="read-only-values"></a><span data-ttu-id="489b5-130">Valeurs en lecture seule</span><span class="sxs-lookup"><span data-stu-id="489b5-130">Read-Only Values</span></span>  
 <span data-ttu-id="489b5-131">Les valeurs des propriétés de clé ne peut pas être modifiés.</span><span class="sxs-lookup"><span data-stu-id="489b5-131">The values of key properties cannot be changed.</span></span> <span data-ttu-id="489b5-132">Par exemple, dans `flight1` dans les exemples précédents, le `Airline` et `FlightNo` champs sont en lecture seule, mais `Gate` peut être modifié.</span><span class="sxs-lookup"><span data-stu-id="489b5-132">For example, in `flight1` in the earlier examples, the `Airline` and `FlightNo` fields are read-only, but `Gate` can be changed.</span></span>  
  
 [!code-vb[VbVbalrAnonymousTypes#28](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/key_6.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="489b5-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="489b5-133">See Also</span></span>  
 [<span data-ttu-id="489b5-134">Définition du type anonyme</span><span class="sxs-lookup"><span data-stu-id="489b5-134">Anonymous Type Definition</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-type-definition.md)  
 [<span data-ttu-id="489b5-135">Guide pratique : déduire les types et les noms de propriétés dans des déclarations de types anonymes</span><span class="sxs-lookup"><span data-stu-id="489b5-135">How to: Infer Property Names and Types in Anonymous Type Declarations</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)  
 [<span data-ttu-id="489b5-136">Types anonymes</span><span class="sxs-lookup"><span data-stu-id="489b5-136">Anonymous Types</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
