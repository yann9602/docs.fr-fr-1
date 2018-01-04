---
title: "Surcharges d'opérateurs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- operators [.NET Framework], overloads
- names [.NET Framework], overloaded operators
- member design guidelines, operators
- overloaded operators
ms.assetid: 37585bf2-4c27-4dee-849a-af70e3338cc1
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 1d17aa00ce551d951b0e178304632572abf592b6
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="operator-overloads"></a><span data-ttu-id="1eee6-102">Surcharges d'opérateurs</span><span class="sxs-lookup"><span data-stu-id="1eee6-102">Operator Overloads</span></span>
<span data-ttu-id="1eee6-103">Les surcharges d’opérateur autorise les types de framework apparaissent comme si elles étaient des primitives de langage intégré.</span><span class="sxs-lookup"><span data-stu-id="1eee6-103">Operator overloads allow framework types to appear as if they were built-in language primitives.</span></span>  
  
 <span data-ttu-id="1eee6-104">Bien qu’autorisées et utile dans certaines situations, les surcharges d’opérateur doivent être utilisées avec prudence.</span><span class="sxs-lookup"><span data-stu-id="1eee6-104">Although allowed and useful in some situations, operator overloads should be used cautiously.</span></span> <span data-ttu-id="1eee6-105">Il existe plusieurs cas dans l’opérateur qui surcharge a été détournée, par exemple lorsque les concepteurs de framework commencé à utiliser des opérateurs pour les opérations qui doivent être des méthodes simples.</span><span class="sxs-lookup"><span data-stu-id="1eee6-105">There are many cases in which operator overloading has been abused, such as when framework designers started to use operators for operations that should be simple methods.</span></span> <span data-ttu-id="1eee6-106">Les instructions suivantes doivent vous aider à décider quand et comment utiliser la surcharge d’opérateur.</span><span class="sxs-lookup"><span data-stu-id="1eee6-106">The following guidelines should help you decide when and how to use operator overloading.</span></span>  
  
 <span data-ttu-id="1eee6-107">**X Évitez** définissant les surcharges d’opérateur, sauf dans les types qui vous devraient vous sentir comme des types primitifs (intégrés).</span><span class="sxs-lookup"><span data-stu-id="1eee6-107">**X AVOID** defining operator overloads, except in types that should feel like primitive (built-in) types.</span></span>  
  
 <span data-ttu-id="1eee6-108">**✓ Envisagez** définissant les surcharges d’opérateur dans un type que vous devriez vous sentir comme un type primitif.</span><span class="sxs-lookup"><span data-stu-id="1eee6-108">**✓ CONSIDER** defining operator overloads in a type that should feel like a primitive type.</span></span>  
  
 <span data-ttu-id="1eee6-109">Par exemple, <xref:System.String?displayProperty=nameWithType> a `operator==` et `operator!=` défini.</span><span class="sxs-lookup"><span data-stu-id="1eee6-109">For example, <xref:System.String?displayProperty=nameWithType> has `operator==` and `operator!=` defined.</span></span>  
  
 <span data-ttu-id="1eee6-110">**✓ FAIRE** définir de surcharges d’opérateur dans les structures représentant des nombres (tel que <xref:System.Decimal?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="1eee6-110">**✓ DO** define operator overloads in structs that represent numbers (such as <xref:System.Decimal?displayProperty=nameWithType>).</span></span>  
  
 <span data-ttu-id="1eee6-111">**X ne sont pas** être jolies lors de la définition de surcharges d’opérateur.</span><span class="sxs-lookup"><span data-stu-id="1eee6-111">**X DO NOT** be cute when defining operator overloads.</span></span>  
  
 <span data-ttu-id="1eee6-112">Surcharge d’opérateur est utile dans les cas dans lequel il est difficile d’identifier ce que sera le résultat de l’opération.</span><span class="sxs-lookup"><span data-stu-id="1eee6-112">Operator overloading is useful in cases in which it is immediately obvious what the result of the operation will be.</span></span> <span data-ttu-id="1eee6-113">Par exemple, il est intéressant de pouvoir soustraire une <xref:System.DateTime> d’une autre `DateTime` et obtenir un <xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="1eee6-113">For example, it makes sense to be able to subtract one <xref:System.DateTime> from another `DateTime` and get a <xref:System.TimeSpan>.</span></span> <span data-ttu-id="1eee6-114">Toutefois, il n’est pas approprié d’utiliser l’opérateur union logique pour les requêtes union de deux bases de données ou à utiliser l’opérateur de décalage pour écrire dans un flux.</span><span class="sxs-lookup"><span data-stu-id="1eee6-114">However, it is not appropriate to use the logical union operator to union two database queries, or to use the shift operator to write to a stream.</span></span>  
  
 <span data-ttu-id="1eee6-115">**X ne sont pas** fournissent des surcharges, sauf si au moins un des opérandes est du type définissant la surcharge d’opérateur.</span><span class="sxs-lookup"><span data-stu-id="1eee6-115">**X DO NOT** provide operator overloads unless at least one of the operands is of the type defining the overload.</span></span>  
  
 <span data-ttu-id="1eee6-116">**✓ FAIRE** surchargez les opérateurs de manière symétrique.</span><span class="sxs-lookup"><span data-stu-id="1eee6-116">**✓ DO** overload operators in a symmetric fashion.</span></span>  
  
 <span data-ttu-id="1eee6-117">Par exemple, si vous surchargez les `operator==`, vous devez aussi surcharger le `operator!=`.</span><span class="sxs-lookup"><span data-stu-id="1eee6-117">For example, if you overload the `operator==`, you should also overload the `operator!=`.</span></span> <span data-ttu-id="1eee6-118">De même, si vous surchargez les `operator<`, vous devez aussi surcharger le `operator>`, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="1eee6-118">Similarly, if you overload the `operator<`, you should also overload the `operator>`, and so on.</span></span>  
  
 <span data-ttu-id="1eee6-119">**✓ Envisagez** fournissant des méthodes avec des noms conviviaux qui correspondent à chaque opérateur surchargé.</span><span class="sxs-lookup"><span data-stu-id="1eee6-119">**✓ CONSIDER** providing methods with friendly names that correspond to each overloaded operator.</span></span>  
  
 <span data-ttu-id="1eee6-120">De nombreux langages ne gèrent pas la surcharge d’opérateur.</span><span class="sxs-lookup"><span data-stu-id="1eee6-120">Many languages do not support operator overloading.</span></span> <span data-ttu-id="1eee6-121">Pour cette raison, il est recommandé que les types qui surchargent des opérateurs incluent une méthode secondaire avec un nom spécifique à un domaine approprié qui fournit des fonctionnalités équivalentes.</span><span class="sxs-lookup"><span data-stu-id="1eee6-121">For this reason, it is recommended that types that overload operators include a secondary method with an appropriate domain-specific name that provides equivalent functionality.</span></span>  
  
 <span data-ttu-id="1eee6-122">Le tableau suivant contient une liste d’opérateurs et les noms de méthode convivial correspondants.</span><span class="sxs-lookup"><span data-stu-id="1eee6-122">The following table contains a list of operators and the corresponding friendly method names.</span></span>  
  
|<span data-ttu-id="1eee6-123">Symbole d’opérateur c#</span><span class="sxs-lookup"><span data-stu-id="1eee6-123">C# Operator Symbol</span></span>|<span data-ttu-id="1eee6-124">Nom de métadonnées</span><span class="sxs-lookup"><span data-stu-id="1eee6-124">Metadata Name</span></span>|<span data-ttu-id="1eee6-125">Nom convivial</span><span class="sxs-lookup"><span data-stu-id="1eee6-125">Friendly Name</span></span>|  
|-------------------------|-------------------|-------------------|  
|`N/A`|`op_Implicit`|`To<TypeName>/From<TypeName>`|  
|`N/A`|`op_Explicit`|`To<TypeName>/From<TypeName>`|  
|`+ (binary)`|`op_Addition`|`Add`|  
|`- (binary)`|`op_Subtraction`|`Subtract`|  
|`* (binary)`|`op_Multiply`|`Multiply`|  
|`/`|`op_Division`|`Divide`|  
|`%`|`op_Modulus`|`Mod or Remainder`|  
|`^`|`op_ExclusiveOr`|`Xor`|  
|`& (binary)`|`op_BitwiseAnd`|`BitwiseAnd`|  
|<code>&#124;</code>|`op_BitwiseOr`|`BitwiseOr`|  
|`&&`|`op_LogicalAnd`|`And`|  
|<code>&#124;&#124;</code>|`op_LogicalOr`|`Or`|  
|`=`|`op_Assign`|`Assign`|  
|`<<`|`op_LeftShift`|`LeftShift`|  
|`>>`|`op_RightShift`|`RightShift`|  
|`N/A`|`op_SignedRightShift`|`SignedRightShift`|  
|`N/A`|`op_UnsignedRightShift`|`UnsignedRightShift`|  
|`==`|`op_Equality`|`Equals`|  
|`!=`|`op_Inequality`|`Equals`|  
|`>`|`op_GreaterThan`|`CompareTo`|  
|`<`|`op_LessThan`|`CompareTo`|  
|`>=`|`op_GreaterThanOrEqual`|`CompareTo`|  
|`<=`|`op_LessThanOrEqual`|`CompareTo`|  
|`*=`|`op_MultiplicationAssignment`|`Multiply`|  
|`-=`|`op_SubtractionAssignment`|`Subtract`|  
|`^=`|`op_ExclusiveOrAssignment`|`Xor`|  
|`<<=`|`op_LeftShiftAssignment`|`LeftShift`|  
|`%=`|`op_ModulusAssignment`|`Mod`|  
|`+=`|`op_AdditionAssignment`|`Add`|  
|`&=`|`op_BitwiseAndAssignment`|`BitwiseAnd`|  
|<code>&#124;=</code>|`op_BitwiseOrAssignment`|`BitwiseOr`|  
|`,`|`op_Comma`|`Comma`|  
|`/=`|`op_DivisionAssignment`|`Divide`|  
|`--`|`op_Decrement`|`Decrement`|  
|`++`|`op_Increment`|`Increment`|  
|`- (unary)`|`op_UnaryNegation`|`Negate`|  
|`+ (unary)`|`op_UnaryPlus`|`Plus`|  
|`~`|`op_OnesComplement`|`OnesComplement`|  
  
### <a name="overloading-operator-"></a><span data-ttu-id="1eee6-126">Surcharge d’opérateur ==</span><span class="sxs-lookup"><span data-stu-id="1eee6-126">Overloading Operator ==</span></span>  
 <span data-ttu-id="1eee6-127">La surcharge `operator ==` est beaucoup plus compliqué.</span><span class="sxs-lookup"><span data-stu-id="1eee6-127">Overloading `operator ==` is quite complicated.</span></span> <span data-ttu-id="1eee6-128">La sémantique de l’opérateur doivent être compatibles avec plusieurs autres membres, tels que <xref:System.Object.Equals%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1eee6-128">The semantics of the operator need to be compatible with several other members, such as <xref:System.Object.Equals%2A?displayProperty=nameWithType>.</span></span>  
  
### <a name="conversion-operators"></a><span data-ttu-id="1eee6-129">Conversion, opérateurs</span><span class="sxs-lookup"><span data-stu-id="1eee6-129">Conversion Operators</span></span>  
 <span data-ttu-id="1eee6-130">Opérateurs de conversion sont des opérateurs unaires qui permettent la conversion d’un type à un autre.</span><span class="sxs-lookup"><span data-stu-id="1eee6-130">Conversion operators are unary operators that allow conversion from one type to another.</span></span> <span data-ttu-id="1eee6-131">Les opérateurs doivent être définis en tant que membres statiques de l’opérande ou le type de retour.</span><span class="sxs-lookup"><span data-stu-id="1eee6-131">The operators must be defined as static members on either the operand or the return type.</span></span> <span data-ttu-id="1eee6-132">Il existe deux types d’opérateurs de conversion : implicites et explicites.</span><span class="sxs-lookup"><span data-stu-id="1eee6-132">There are two types of conversion operators: implicit and explicit.</span></span>  
  
 <span data-ttu-id="1eee6-133">**X ne sont pas** fournissent un opérateur de conversion si cette conversion n’est pas clairement attendue par les utilisateurs finaux.</span><span class="sxs-lookup"><span data-stu-id="1eee6-133">**X DO NOT** provide a conversion operator if such conversion is not clearly expected by the end users.</span></span>  
  
 <span data-ttu-id="1eee6-134">**X ne sont pas** définir des opérateurs de conversion en dehors du domaine d’un type.</span><span class="sxs-lookup"><span data-stu-id="1eee6-134">**X DO NOT** define conversion operators outside of a type’s domain.</span></span>  
  
 <span data-ttu-id="1eee6-135">Par exemple, <xref:System.Int32>, <xref:System.Double>, et <xref:System.Decimal> sont tous les types numériques, tandis que <xref:System.DateTime> n’est pas.</span><span class="sxs-lookup"><span data-stu-id="1eee6-135">For example, <xref:System.Int32>, <xref:System.Double>, and <xref:System.Decimal> are all numeric types, whereas <xref:System.DateTime> is not.</span></span> <span data-ttu-id="1eee6-136">Par conséquent, il ne doit y avoir aucun opérateur de conversion pour convertir un `Double(long)` à un `DateTime`.</span><span class="sxs-lookup"><span data-stu-id="1eee6-136">Therefore, there should be no conversion operator to convert a `Double(long)` to a `DateTime`.</span></span> <span data-ttu-id="1eee6-137">Dans ce cas, un constructeur est préféré.</span><span class="sxs-lookup"><span data-stu-id="1eee6-137">A constructor is preferred in such a case.</span></span>  
  
 <span data-ttu-id="1eee6-138">**X ne sont pas** fournissent un opérateur de conversion implicite si la conversion est potentiellement avec perte de données.</span><span class="sxs-lookup"><span data-stu-id="1eee6-138">**X DO NOT** provide an implicit conversion operator if the conversion is potentially lossy.</span></span>  
  
 <span data-ttu-id="1eee6-139">Par exemple, il ne doit pas être une conversion implicite de `Double` à `Int32` car `Double` a une plage plus large que `Int32`.</span><span class="sxs-lookup"><span data-stu-id="1eee6-139">For example, there should not be an implicit conversion from `Double` to `Int32` because `Double` has a wider range than `Int32`.</span></span> <span data-ttu-id="1eee6-140">Un opérateur de conversion explicite peut être fourni, même si la conversion est potentiellement avec perte de données.</span><span class="sxs-lookup"><span data-stu-id="1eee6-140">An explicit conversion operator can be provided even if the conversion is potentially lossy.</span></span>  
  
 <span data-ttu-id="1eee6-141">**X ne sont pas** lever des exceptions de casts implicites.</span><span class="sxs-lookup"><span data-stu-id="1eee6-141">**X DO NOT** throw exceptions from implicit casts.</span></span>  
  
 <span data-ttu-id="1eee6-142">Il est très difficile pour les utilisateurs finaux à comprendre ce qui se passe, car ils ne peuvent pas être conscient qu’une conversion a lieu.</span><span class="sxs-lookup"><span data-stu-id="1eee6-142">It is very difficult for end users to understand what is happening, because they might not be aware that a conversion is taking place.</span></span>  
  
 <span data-ttu-id="1eee6-143">**✓ FAIRE** lever <xref:System.InvalidCastException?displayProperty=nameWithType> si un appel à un opérateur de cast entraîne une conversion avec perte de données et le contrat de l’opérateur n’autorise pas les conversions avec perte de données.</span><span class="sxs-lookup"><span data-stu-id="1eee6-143">**✓ DO** throw <xref:System.InvalidCastException?displayProperty=nameWithType> if a call to a cast operator results in a lossy conversion and the contract of the operator does not allow lossy conversions.</span></span>  
  
 <span data-ttu-id="1eee6-144">*Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*</span><span class="sxs-lookup"><span data-stu-id="1eee6-144">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="1eee6-145">*Réimprimées avec l’autorisation de Pearson éducation, Inc. à partir de [règles de conception d’infrastructure : Conventions, idiomes et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série de développement Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="1eee6-145">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1eee6-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1eee6-146">See Also</span></span>  
 [<span data-ttu-id="1eee6-147">Instructions de conception des membres</span><span class="sxs-lookup"><span data-stu-id="1eee6-147">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)  
 [<span data-ttu-id="1eee6-148">Règles de conception de .NET Framework</span><span class="sxs-lookup"><span data-stu-id="1eee6-148">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
