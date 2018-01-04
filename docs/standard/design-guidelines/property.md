---
title: "Conception des propriétés"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- member design guidelines, properties
- properties [.NET Framework], design guidelines
ms.assetid: 127cbc0c-cbed-48fd-9c89-7c5d4f98f163
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 8f9c65dc6265daa793656177f066b97373f48ab8
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="property-design"></a><span data-ttu-id="db75c-102">Conception des propriétés</span><span class="sxs-lookup"><span data-stu-id="db75c-102">Property Design</span></span>
<span data-ttu-id="db75c-103">Bien que les propriétés sont techniquement très semblables aux méthodes, ils sont très différents en termes de leurs scénarios d’utilisation.</span><span class="sxs-lookup"><span data-stu-id="db75c-103">Although properties are technically very similar to methods, they are quite different in terms of their usage scenarios.</span></span> <span data-ttu-id="db75c-104">Ils doivent être considérés comme des champs intelligents.</span><span class="sxs-lookup"><span data-stu-id="db75c-104">They should be seen as smart fields.</span></span> <span data-ttu-id="db75c-105">Ils ont la syntaxe d’appel de champs et la flexibilité des méthodes.</span><span class="sxs-lookup"><span data-stu-id="db75c-105">They have the calling syntax of fields, and the flexibility of methods.</span></span>  
  
 <span data-ttu-id="db75c-106">**✓ FAIRE** créer des propriétés get-only si l’appelant ne doit pas être en mesure de modifier la valeur de la propriété.</span><span class="sxs-lookup"><span data-stu-id="db75c-106">**✓ DO** create get-only properties if the caller should not be able to change the value of the property.</span></span>  
  
 <span data-ttu-id="db75c-107">Gardez à l’esprit ce cas le type de la propriété est un type référence mutable, la valeur de propriété peut être modifiée même si la propriété est get-only.</span><span class="sxs-lookup"><span data-stu-id="db75c-107">Keep in mind that if the type of the property is a mutable reference type, the property value can be changed even if the property is get-only.</span></span>  
  
 <span data-ttu-id="db75c-108">**X ne sont pas** fournissent des propriétés ou propriétés à définir uniquement avec la méthode setter ayant le plus large d’accessibilité de l’accesseur Get.</span><span class="sxs-lookup"><span data-stu-id="db75c-108">**X DO NOT** provide set-only properties or properties with the setter having broader accessibility than the getter.</span></span>  
  
 <span data-ttu-id="db75c-109">Par exemple, n’utilisez pas de propriétés avec un accesseur Set public et un accesseur Get protégé.</span><span class="sxs-lookup"><span data-stu-id="db75c-109">For example, do not use properties with a public setter and a protected getter.</span></span>  
  
 <span data-ttu-id="db75c-110">Si l’accesseur Get de propriété ne peut pas être fourni, implémenter la fonctionnalité en tant que méthode à la place.</span><span class="sxs-lookup"><span data-stu-id="db75c-110">If the property getter cannot be provided, implement the functionality as a method instead.</span></span> <span data-ttu-id="db75c-111">Pensez à démarrer avec le nom de la méthode `Set` et suivez avec ce que vous avez appellerait la propriété.</span><span class="sxs-lookup"><span data-stu-id="db75c-111">Consider starting the method name with `Set` and follow with what you would have named the property.</span></span> <span data-ttu-id="db75c-112">Par exemple, <xref:System.AppDomain> possède une méthode appelée `SetCachePath` au lieu d’avoir une propriété de jeu uniquement appelée `CachePath`.</span><span class="sxs-lookup"><span data-stu-id="db75c-112">For example, <xref:System.AppDomain> has a method called `SetCachePath` instead of having a set-only property called `CachePath`.</span></span>  
  
 <span data-ttu-id="db75c-113">**✓ FAIRE** fournissent des valeurs par défaut raisonnables pour toutes les propriétés, garantissant que les valeurs par défaut n’entraînent pas une faille de sécurité ou du code très inefficace.</span><span class="sxs-lookup"><span data-stu-id="db75c-113">**✓ DO** provide sensible default values for all properties, ensuring that the defaults do not result in a security hole or terribly inefficient code.</span></span>  
  
 <span data-ttu-id="db75c-114">**✓ FAIRE** permettent d’être définie dans n’importe quel ordre, même si cela aboutit à un état temporaire non valide de l’objet.</span><span class="sxs-lookup"><span data-stu-id="db75c-114">**✓ DO** allow properties to be set in any order even if this results in a temporary invalid state of the object.</span></span>  
  
 <span data-ttu-id="db75c-115">Il est courant pour les deux ou plusieurs propriétés être reliés entre eux à un point où des valeurs d’une propriété peuvent être non valides, étant donné les valeurs des autres propriétés sur le même objet.</span><span class="sxs-lookup"><span data-stu-id="db75c-115">It is common for two or more properties to be interrelated to a point where some values of one property might be invalid given the values of other properties on the same object.</span></span> <span data-ttu-id="db75c-116">Dans ce cas, les exceptions résultant de l’état non valide doivent être différées jusqu'à ce que les propriétés liées entre elles sont réellement utilisées ensemble par l’objet.</span><span class="sxs-lookup"><span data-stu-id="db75c-116">In such cases, exceptions resulting from the invalid state should be postponed until the interrelated properties are actually used together by the object.</span></span>  
  
 <span data-ttu-id="db75c-117">**✓ FAIRE** conserver la valeur précédente si un accesseur Set de propriété lève une exception.</span><span class="sxs-lookup"><span data-stu-id="db75c-117">**✓ DO** preserve the previous value if a property setter throws an exception.</span></span>  
  
 <span data-ttu-id="db75c-118">**X Évitez** lever des exceptions à partir des accesseurs Get de propriété.</span><span class="sxs-lookup"><span data-stu-id="db75c-118">**X AVOID** throwing exceptions from property getters.</span></span>  
  
 <span data-ttu-id="db75c-119">Accesseurs Get de propriété doit être des opérations simples et ne doit pas avoir toutes les conditions préalables.</span><span class="sxs-lookup"><span data-stu-id="db75c-119">Property getters should be simple operations and should not have any preconditions.</span></span> <span data-ttu-id="db75c-120">Si un accesseur Get peut lever une exception, il doit probablement être modifiée pour être une méthode.</span><span class="sxs-lookup"><span data-stu-id="db75c-120">If a getter can throw an exception, it should probably be redesigned to be a method.</span></span> <span data-ttu-id="db75c-121">Notez que cette règle ne s’applique pas à des indexeurs, où devrait exceptions à la suite de valider les arguments.</span><span class="sxs-lookup"><span data-stu-id="db75c-121">Notice that this rule does not apply to indexers, where we do expect exceptions as a result of validating the arguments.</span></span>  
  
### <a name="indexed-property-design"></a><span data-ttu-id="db75c-122">Conception de la propriété indexée</span><span class="sxs-lookup"><span data-stu-id="db75c-122">Indexed Property Design</span></span>  
 <span data-ttu-id="db75c-123">Une propriété indexée est une propriété spéciale qui peut avoir des paramètres et peut être appelée avec une syntaxe spéciale semblable à l’indexation de tableau.</span><span class="sxs-lookup"><span data-stu-id="db75c-123">An indexed property is a special property that can have parameters and can be called with special syntax similar to array indexing.</span></span>  
  
 <span data-ttu-id="db75c-124">Les propriétés indexées sont communément appelé indexeurs.</span><span class="sxs-lookup"><span data-stu-id="db75c-124">Indexed properties are commonly referred to as indexers.</span></span> <span data-ttu-id="db75c-125">Les indexeurs doivent être utilisés uniquement dans les API qui donnent accès aux éléments d’une collection logique.</span><span class="sxs-lookup"><span data-stu-id="db75c-125">Indexers should be used only in APIs that provide access to items in a logical collection.</span></span> <span data-ttu-id="db75c-126">Par exemple, une chaîne est un ensemble de caractères et que l’indexeur sur <xref:System.String?displayProperty=nameWithType> a été ajouté à accéder à ses caractères.</span><span class="sxs-lookup"><span data-stu-id="db75c-126">For example, a string is a collection of characters, and the indexer on <xref:System.String?displayProperty=nameWithType> was added to access its characters.</span></span>  
  
 <span data-ttu-id="db75c-127">**✓ Envisagez** des indexeurs pour fournir l’accès aux données stockées dans un tableau interne.</span><span class="sxs-lookup"><span data-stu-id="db75c-127">**✓ CONSIDER** using indexers to provide access to data stored in an internal array.</span></span>  
  
 <span data-ttu-id="db75c-128">**✓ Envisagez** fournir des indexeurs sur les types de collections d’éléments.</span><span class="sxs-lookup"><span data-stu-id="db75c-128">**✓ CONSIDER** providing indexers on types representing collections of items.</span></span>  
  
 <span data-ttu-id="db75c-129">**X Évitez** à l’aide des propriétés avec plusieurs paramètres indexées.</span><span class="sxs-lookup"><span data-stu-id="db75c-129">**X AVOID** using indexed properties with more than one parameter.</span></span>  
  
 <span data-ttu-id="db75c-130">Si la conception requiert plusieurs paramètres, reconsidérez si la propriété représente réellement un accesseur à une collection logique.</span><span class="sxs-lookup"><span data-stu-id="db75c-130">If the design requires multiple parameters, reconsider whether the property really represents an accessor to a logical collection.</span></span> <span data-ttu-id="db75c-131">Si elle n’est pas le cas, utilisez à la place des méthodes.</span><span class="sxs-lookup"><span data-stu-id="db75c-131">If it does not, use methods instead.</span></span> <span data-ttu-id="db75c-132">Pensez à démarrer avec le nom de la méthode `Get` ou `Set`.</span><span class="sxs-lookup"><span data-stu-id="db75c-132">Consider starting the method name with `Get` or `Set`.</span></span>  
  
 <span data-ttu-id="db75c-133">**X Évitez** indexeurs avec les types de paramètres autres que <xref:System.Int32?displayProperty=nameWithType>, <xref:System.Int64?displayProperty=nameWithType>, <xref:System.String?displayProperty=nameWithType>, <xref:System.Object?displayProperty=nameWithType>, ou d’un enum.</span><span class="sxs-lookup"><span data-stu-id="db75c-133">**X AVOID** indexers with parameter types other than <xref:System.Int32?displayProperty=nameWithType>, <xref:System.Int64?displayProperty=nameWithType>, <xref:System.String?displayProperty=nameWithType>, <xref:System.Object?displayProperty=nameWithType>, or an enum.</span></span>  
  
 <span data-ttu-id="db75c-134">Si la conception nécessite d’autres types de paramètres, est important si l’API représente réellement un accesseur à une collection logique.</span><span class="sxs-lookup"><span data-stu-id="db75c-134">If the design requires other types of parameters, strongly reevaluate whether the API really represents an accessor to a logical collection.</span></span> <span data-ttu-id="db75c-135">Si elle n’est pas le cas, utilisez une méthode.</span><span class="sxs-lookup"><span data-stu-id="db75c-135">If it does not, use a method.</span></span> <span data-ttu-id="db75c-136">Pensez à démarrer avec le nom de la méthode `Get` ou `Set`.</span><span class="sxs-lookup"><span data-stu-id="db75c-136">Consider starting the method name with `Get` or `Set`.</span></span>  
  
 <span data-ttu-id="db75c-137">**✓ FAIRE** utiliser le nom `Item` pour des propriétés indexées, sauf s’il existe un meilleur nom (par exemple, consultez la <xref:System.String.Chars%2A> propriété sur `System.String`).</span><span class="sxs-lookup"><span data-stu-id="db75c-137">**✓ DO** use the name `Item` for indexed properties unless there is an obviously better name (e.g., see the <xref:System.String.Chars%2A> property on `System.String`).</span></span>  
  
 <span data-ttu-id="db75c-138">En c#, les indexeurs sont par défaut nommé « Item ».</span><span class="sxs-lookup"><span data-stu-id="db75c-138">In C#, indexers are by default named Item.</span></span> <span data-ttu-id="db75c-139">Le <xref:System.Runtime.CompilerServices.IndexerNameAttribute> peut être utilisé pour personnaliser ce nom.</span><span class="sxs-lookup"><span data-stu-id="db75c-139">The <xref:System.Runtime.CompilerServices.IndexerNameAttribute> can be used to customize this name.</span></span>  
  
 <span data-ttu-id="db75c-140">**X ne sont pas** fournissent à la fois un indexeur et des méthodes qui sont sémantiquement équivalents.</span><span class="sxs-lookup"><span data-stu-id="db75c-140">**X DO NOT** provide both an indexer and methods that are semantically equivalent.</span></span>  
  
 <span data-ttu-id="db75c-141">**X ne sont pas** fournissent plusieurs familles d’indexeurs surchargés dans un type.</span><span class="sxs-lookup"><span data-stu-id="db75c-141">**X DO NOT** provide more than one family of overloaded indexers in one type.</span></span>  
  
 <span data-ttu-id="db75c-142">Elle est appliquée par le compilateur c#.</span><span class="sxs-lookup"><span data-stu-id="db75c-142">This is enforced by the C# compiler.</span></span>  
  
 <span data-ttu-id="db75c-143">**X ne sont pas** différent de l’utilisation des propriétés indexées.</span><span class="sxs-lookup"><span data-stu-id="db75c-143">**X DO NOT** use nondefault indexed properties.</span></span>  
  
 <span data-ttu-id="db75c-144">Elle est appliquée par le compilateur c#.</span><span class="sxs-lookup"><span data-stu-id="db75c-144">This is enforced by the C# compiler.</span></span>  
  
### <a name="property-change-notification-events"></a><span data-ttu-id="db75c-145">Événements de Notification de modification de propriété</span><span class="sxs-lookup"><span data-stu-id="db75c-145">Property Change Notification Events</span></span>  
 <span data-ttu-id="db75c-146">Il est parfois utile de fournir un événement de notification à l’utilisateur des modifications dans une valeur de propriété.</span><span class="sxs-lookup"><span data-stu-id="db75c-146">Sometimes it is useful to provide an event notifying the user of changes in a property value.</span></span> <span data-ttu-id="db75c-147">Par exemple, `System.Windows.Forms.Control` déclenche un `TextChanged` événement après la valeur de son `Text` propriété a changé.</span><span class="sxs-lookup"><span data-stu-id="db75c-147">For example, `System.Windows.Forms.Control` raises a `TextChanged` event after the value of its `Text` property has changed.</span></span>  
  
 <span data-ttu-id="db75c-148">**✓ Envisagez** modifier les déclenchement d’événements de notification lorsque les valeurs de propriété dans les API de niveau supérieur (composants de concepteur généralement) sont modifiés.</span><span class="sxs-lookup"><span data-stu-id="db75c-148">**✓ CONSIDER** raising change notification events when property values in high-level APIs (usually designer components) are modified.</span></span>  
  
 <span data-ttu-id="db75c-149">S’il existe un bon scénario d’un utilisateur de savoir quand une propriété d’un objet change, l’objet doit déclencher un événement de notification de modification de la propriété.</span><span class="sxs-lookup"><span data-stu-id="db75c-149">If there is a good scenario for a user to know when a property of an object is changing, the object should raise a change notification event for the property.</span></span>  
  
 <span data-ttu-id="db75c-150">Toutefois, il est peu de chances d’être intéressant le traitement de déclencher des événements pour les API de bas niveau tels que les types de base ou des collections.</span><span class="sxs-lookup"><span data-stu-id="db75c-150">However, it is unlikely to be worth the overhead to raise such events for low-level APIs such as base types or collections.</span></span> <span data-ttu-id="db75c-151">Par exemple, <xref:System.Collections.Generic.List%601> ne déclenchera pas ces événements quand un nouvel élément est ajouté à la liste et le `Count` de propriété est modifiée.</span><span class="sxs-lookup"><span data-stu-id="db75c-151">For example, <xref:System.Collections.Generic.List%601> would not raise such events when a new item is added to the list and the `Count` property changes.</span></span>  
  
 <span data-ttu-id="db75c-152">**✓ Envisagez** déclenchement modifier les événements de notification lorsque la valeur d’une propriété modifiée via la force externe.</span><span class="sxs-lookup"><span data-stu-id="db75c-152">**✓ CONSIDER** raising change notification events when the value of a property changes via external forces.</span></span>  
  
 <span data-ttu-id="db75c-153">Si une valeur de propriété change via une force externe (d’une manière différente en appelant des méthodes sur l’objet), déclencher des événements indiquent au développeur que la valeur change et qu’il a été modifié.</span><span class="sxs-lookup"><span data-stu-id="db75c-153">If a property value changes via some external force (in a way other than by calling methods on the object), raise events indicate to the developer that the value is changing and has changed.</span></span> <span data-ttu-id="db75c-154">Un bon exemple est le `Text` propriété d’un contrôle de zone de texte.</span><span class="sxs-lookup"><span data-stu-id="db75c-154">A good example is the `Text` property of a text box control.</span></span> <span data-ttu-id="db75c-155">Lorsque l’utilisateur tape du texte dans un `TextBox`, la valeur de propriété change automatiquement.</span><span class="sxs-lookup"><span data-stu-id="db75c-155">When the user types text in a `TextBox`, the property value automatically changes.</span></span>  
  
 <span data-ttu-id="db75c-156">*Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*</span><span class="sxs-lookup"><span data-stu-id="db75c-156">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="db75c-157">*Réimprimées avec l’autorisation de Pearson éducation, Inc. à partir de [règles de conception d’infrastructure : Conventions, idiomes et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série de développement Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="db75c-157">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db75c-158">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="db75c-158">See Also</span></span>  
 [<span data-ttu-id="db75c-159">Instructions de conception des membres</span><span class="sxs-lookup"><span data-stu-id="db75c-159">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)  
 [<span data-ttu-id="db75c-160">Règles de conception de .NET Framework</span><span class="sxs-lookup"><span data-stu-id="db75c-160">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
