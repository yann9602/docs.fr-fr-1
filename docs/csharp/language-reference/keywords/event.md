---
title: "event (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- event
- remove
- event_CSharpKeyword
- add
dev_langs:
- CSharp
helpviewer_keywords:
- event keyword [C#]
ms.assetid: 7858fd85-153b-4259-85d0-6aa13c35f174
caps.latest.revision: 28
author: BillWagner
ms.author: wiwagn
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 674e36625a68243afff75f6c5028309dc7aff02a
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="event-c-reference"></a><span data-ttu-id="f5f11-102">event (référence C#)</span><span class="sxs-lookup"><span data-stu-id="f5f11-102">event (C# Reference)</span></span>
<span data-ttu-id="f5f11-103">Le mot clé `event` sert à déclarer un événement dans une classe d’éditeur.</span><span class="sxs-lookup"><span data-stu-id="f5f11-103">The `event` keyword is used to declare an event in a publisher class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f5f11-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="f5f11-104">Example</span></span>  
 <span data-ttu-id="f5f11-105">L’exemple suivant montre comment déclarer et déclencher un événement qui utilise <xref:System.EventHandler> comme type délégué sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="f5f11-105">The following example shows how to declare and raise an event that uses <xref:System.EventHandler> as the underlying delegate type.</span></span> <span data-ttu-id="f5f11-106">Pour obtenir l’exemple de code complet qui illustre aussi comment utiliser le type délégué générique <xref:System.EventHandler%601> et comment s’abonner à un événement et créer une méthode de gestionnaire d’événements, consultez [Guide pratique pour publier des événements conformes aux indications du .NET Framework](../../../csharp/programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md).</span><span class="sxs-lookup"><span data-stu-id="f5f11-106">For the complete code example that also shows how to use the generic <xref:System.EventHandler%601> delegate type and how to subscribe to an event and create an event handler method, see [How to: Publish Events that Conform to .NET Framework Guidelines](../../../csharp/programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md).</span></span>  
  
 <span data-ttu-id="f5f11-107">[!code-cs[csrefKeywordsModifiers#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/event_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="f5f11-107">[!code-cs[csrefKeywordsModifiers#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/event_1.cs)]</span></span>  
  
 <span data-ttu-id="f5f11-108">Les événements constituent un type spécial de délégué multicast qui peut uniquement être appelé au sein de la classe ou du struct où ils sont déclarés (la classe d’éditeur).</span><span class="sxs-lookup"><span data-stu-id="f5f11-108">Events are a special kind of multicast delegate that can only be invoked from within the class or struct where they are declared (the publisher class).</span></span> <span data-ttu-id="f5f11-109">Si d’autres classes ou structs s’abonnent à l’événement, leurs méthodes de gestionnaire d’événements sont appelées quand la classe d’éditeur déclenche l’événement.</span><span class="sxs-lookup"><span data-stu-id="f5f11-109">If other classes or structs subscribe to the event, their event handler methods will be called when the publisher class raises the event.</span></span> <span data-ttu-id="f5f11-110">Pour plus d’informations et pour obtenir des exemples de code, consultez [Événements](../../../csharp/programming-guide/events/index.md) et [Délégués](../../../csharp/programming-guide/delegates/index.md).</span><span class="sxs-lookup"><span data-stu-id="f5f11-110">For more information and code examples, see [Events](../../../csharp/programming-guide/events/index.md) and [Delegates](../../../csharp/programming-guide/delegates/index.md).</span></span>  
  
 <span data-ttu-id="f5f11-111">Les événements peuvent être marqués comme [public](../../../csharp/language-reference/keywords/public.md), [private](../../../csharp/language-reference/keywords/private.md), [protected](../../../csharp/language-reference/keywords/protected.md), [internal](../../../csharp/language-reference/keywords/internal.md) ou `protected internal`.</span><span class="sxs-lookup"><span data-stu-id="f5f11-111">Events can be marked as [public](../../../csharp/language-reference/keywords/public.md), [private](../../../csharp/language-reference/keywords/private.md), [protected](../../../csharp/language-reference/keywords/protected.md), [internal](../../../csharp/language-reference/keywords/internal.md), or `protected internal`.</span></span> <span data-ttu-id="f5f11-112">Ces modificateurs d’accès définissent comment les utilisateurs de la classe peuvent accéder à l’événement.</span><span class="sxs-lookup"><span data-stu-id="f5f11-112">These access modifiers define how users of the class can access the event.</span></span> <span data-ttu-id="f5f11-113">Pour plus d’informations, consultez [Modificateurs d’accès](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="f5f11-113">For more information, see [Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span></span>  
  
## <a name="keywords-and-events"></a><span data-ttu-id="f5f11-114">Mots clés et événements</span><span class="sxs-lookup"><span data-stu-id="f5f11-114">Keywords and Events</span></span>  
 <span data-ttu-id="f5f11-115">Les mots clés suivants s’appliquent aux événements.</span><span class="sxs-lookup"><span data-stu-id="f5f11-115">The following keywords apply to events.</span></span>  
  
|<span data-ttu-id="f5f11-116">Mot clé</span><span class="sxs-lookup"><span data-stu-id="f5f11-116">Keyword</span></span>|<span data-ttu-id="f5f11-117">Description</span><span class="sxs-lookup"><span data-stu-id="f5f11-117">Description</span></span>|<span data-ttu-id="f5f11-118">Pour plus d'informations</span><span class="sxs-lookup"><span data-stu-id="f5f11-118">For more information</span></span>|  
|-------------|-----------------|--------------------------|  
|[<span data-ttu-id="f5f11-119">static</span><span class="sxs-lookup"><span data-stu-id="f5f11-119">static</span></span>](../../../csharp/language-reference/keywords/static.md)|<span data-ttu-id="f5f11-120">Rend le champ accessible à tout moment aux appelants, même s’il n’existe aucune instance de la classe.</span><span class="sxs-lookup"><span data-stu-id="f5f11-120">Makes the event available to callers at any time, even if no instance of the class exists.</span></span>|[<span data-ttu-id="f5f11-121">Classes statiques et membres de classe statique</span><span class="sxs-lookup"><span data-stu-id="f5f11-121">Static Classes and Static Class Members</span></span>](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)|  
|[<span data-ttu-id="f5f11-122">virtual</span><span class="sxs-lookup"><span data-stu-id="f5f11-122">virtual</span></span>](../../../csharp/language-reference/keywords/virtual.md)|<span data-ttu-id="f5f11-123">Permet aux classes dérivées de substituer le comportement d’événement à l’aide du mot clé [override](../../../csharp/language-reference/keywords/override.md).</span><span class="sxs-lookup"><span data-stu-id="f5f11-123">Allows derived classes to override the event behavior by using the [override](../../../csharp/language-reference/keywords/override.md) keyword.</span></span>|[<span data-ttu-id="f5f11-124">Héritage</span><span class="sxs-lookup"><span data-stu-id="f5f11-124">Inheritance</span></span>](../../../csharp/programming-guide/classes-and-structs/inheritance.md)|  
|[<span data-ttu-id="f5f11-125">sealed</span><span class="sxs-lookup"><span data-stu-id="f5f11-125">sealed</span></span>](../../../csharp/language-reference/keywords/sealed.md)|<span data-ttu-id="f5f11-126">Spécifie que pour les classes dérivées l’événement n’est plus virtuel.</span><span class="sxs-lookup"><span data-stu-id="f5f11-126">Specifies that for derived classes it is no longer virtual.</span></span>||  
|[<span data-ttu-id="f5f11-127">abstract</span><span class="sxs-lookup"><span data-stu-id="f5f11-127">abstract</span></span>](../../../csharp/language-reference/keywords/abstract.md)|<span data-ttu-id="f5f11-128">Le compilateur ne génère pas les blocs d’accesseurs d’événement `add` et `remove`, et par conséquent les classes dérivées doivent fournir leur propre implémentation.</span><span class="sxs-lookup"><span data-stu-id="f5f11-128">The compiler will not generate the `add` and `remove` event accessor blocks and therefore derived classes must provide their own implementation.</span></span>||  
  
 <span data-ttu-id="f5f11-129">Un événement peut être déclaré comme événement statique à l’aide du mot clé [static](../../../csharp/language-reference/keywords/static.md).</span><span class="sxs-lookup"><span data-stu-id="f5f11-129">An event may be declared as a static event by using the [static](../../../csharp/language-reference/keywords/static.md) keyword.</span></span> <span data-ttu-id="f5f11-130">Cela rend le champ accessible à tout moment aux appelants, même s’il n’existe aucune instance de la classe.</span><span class="sxs-lookup"><span data-stu-id="f5f11-130">This makes the event available to callers at any time, even if no instance of the class exists.</span></span> <span data-ttu-id="f5f11-131">Pour plus d’informations, consultez [Classes statiques et membres de classe statique](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="f5f11-131">For more information, see [Static Classes and Static Class Members](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span></span>  
  
 <span data-ttu-id="f5f11-132">Un événement peut être marqué comme événement virtuel à l’aide du mot clé [virtual](../../../csharp/language-reference/keywords/virtual.md).</span><span class="sxs-lookup"><span data-stu-id="f5f11-132">An event can be marked as a virtual event by using the [virtual](../../../csharp/language-reference/keywords/virtual.md) keyword.</span></span> <span data-ttu-id="f5f11-133">Cela permet aux classes dérivées de substituer le comportement d’événement à l’aide du mot clé [override](../../../csharp/language-reference/keywords/override.md).</span><span class="sxs-lookup"><span data-stu-id="f5f11-133">This enables derived classes to override the event behavior by using the [override](../../../csharp/language-reference/keywords/override.md) keyword.</span></span> <span data-ttu-id="f5f11-134">Pour plus d’informations, consultez [Héritage](../../../csharp/programming-guide/classes-and-structs/inheritance.md).</span><span class="sxs-lookup"><span data-stu-id="f5f11-134">For more information, see [Inheritance](../../../csharp/programming-guide/classes-and-structs/inheritance.md).</span></span> <span data-ttu-id="f5f11-135">Un événement qui se substitue à un événement virtuel peut également être [sealed](../../../csharp/language-reference/keywords/sealed.md), ce qui signifie que pour les classes dérivées il n’est plus virtuel.</span><span class="sxs-lookup"><span data-stu-id="f5f11-135">An event overriding a virtual event can also be [sealed](../../../csharp/language-reference/keywords/sealed.md), which specifies that for derived classes it is no longer virtual.</span></span> <span data-ttu-id="f5f11-136">Pour finir, un événement peut être déclaré [abstract](../../../csharp/language-reference/keywords/abstract.md), ce qui signifie que le compilateur ne génère pas les blocs d’accesseurs d’événement `add` et `remove`.</span><span class="sxs-lookup"><span data-stu-id="f5f11-136">Lastly, an event can be declared [abstract](../../../csharp/language-reference/keywords/abstract.md), which means that the compiler will not generate the `add` and `remove` event accessor blocks.</span></span> <span data-ttu-id="f5f11-137">Ainsi, les classes dérivées doivent fournir leur propre implémentation.</span><span class="sxs-lookup"><span data-stu-id="f5f11-137">Therefore derived classes must provide their own implementation.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="f5f11-138">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="f5f11-138">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f5f11-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f5f11-139">See Also</span></span>  
 <span data-ttu-id="f5f11-140">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="f5f11-140">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="f5f11-141">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="f5f11-141">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="f5f11-142">[Mots clés C#](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="f5f11-142">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="f5f11-143">[add](../../../csharp/language-reference/keywords/add.md) </span><span class="sxs-lookup"><span data-stu-id="f5f11-143">[add](../../../csharp/language-reference/keywords/add.md) </span></span>  
 <span data-ttu-id="f5f11-144">[remove](../../../csharp/language-reference/keywords/remove.md) </span><span class="sxs-lookup"><span data-stu-id="f5f11-144">[remove](../../../csharp/language-reference/keywords/remove.md) </span></span>  
 <span data-ttu-id="f5f11-145">[Modificateurs](../../../csharp/language-reference/keywords/modifiers.md) </span><span class="sxs-lookup"><span data-stu-id="f5f11-145">[Modifiers](../../../csharp/language-reference/keywords/modifiers.md) </span></span>  
 [<span data-ttu-id="f5f11-146">Guide pratique pour combiner des délégués (délégués multicast)</span><span class="sxs-lookup"><span data-stu-id="f5f11-146">How to: Combine Delegates (Multicast Delegates)</span></span>](../../../csharp/programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md)

