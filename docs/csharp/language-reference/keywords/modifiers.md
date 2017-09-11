---
title: "Modificateurs (référence C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- keywords [C#], modifiers
- modifiers [C#]
ms.assetid: c96691dd-b357-49ec-b5ae-03ca214fadfb
caps.latest.revision: 18
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
ms.openlocfilehash: 9e2e7e5e3907ac9bb66676e749ddd55a8ac4836c
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="modifiers-c-reference"></a><span data-ttu-id="40a9d-102">Modificateurs (référence C#)</span><span class="sxs-lookup"><span data-stu-id="40a9d-102">Modifiers (C# Reference)</span></span>
<span data-ttu-id="40a9d-103">Les modificateurs permettent de modifier les déclarations des types et membres de types.</span><span class="sxs-lookup"><span data-stu-id="40a9d-103">Modifiers are used to modify declarations of types and type members.</span></span> <span data-ttu-id="40a9d-104">Cette section présente les modificateurs C#.</span><span class="sxs-lookup"><span data-stu-id="40a9d-104">This section introduces the C# modifiers.</span></span>  
  
|<span data-ttu-id="40a9d-105">Modificateur</span><span class="sxs-lookup"><span data-stu-id="40a9d-105">Modifier</span></span>|<span data-ttu-id="40a9d-106">Objectif</span><span class="sxs-lookup"><span data-stu-id="40a9d-106">Purpose</span></span>|  
|--------------|-------------|  
|[<span data-ttu-id="40a9d-107">Modificateurs d’accès</span><span class="sxs-lookup"><span data-stu-id="40a9d-107">Access Modifiers</span></span>](../../../csharp/language-reference/keywords/access-modifiers.md)<br /><br /> <span data-ttu-id="40a9d-108">-   [public](../../../csharp/language-reference/keywords/public.md)</span><span class="sxs-lookup"><span data-stu-id="40a9d-108">-   [public](../../../csharp/language-reference/keywords/public.md)</span></span><br /><span data-ttu-id="40a9d-109">-   [private](../../../csharp/language-reference/keywords/private.md)</span><span class="sxs-lookup"><span data-stu-id="40a9d-109">-   [private](../../../csharp/language-reference/keywords/private.md)</span></span><br /><span data-ttu-id="40a9d-110">-   [internal](../../../csharp/language-reference/keywords/internal.md)</span><span class="sxs-lookup"><span data-stu-id="40a9d-110">-   [internal](../../../csharp/language-reference/keywords/internal.md)</span></span><br /><span data-ttu-id="40a9d-111">-   [protected](../../../csharp/language-reference/keywords/protected.md)</span><span class="sxs-lookup"><span data-stu-id="40a9d-111">-   [protected](../../../csharp/language-reference/keywords/protected.md)</span></span>|<span data-ttu-id="40a9d-112">Spécifie l'accessibilité déclarée de types et membres de types.</span><span class="sxs-lookup"><span data-stu-id="40a9d-112">Specifies the declared accessibility of types and type members.</span></span>|  
|[<span data-ttu-id="40a9d-113">abstract</span><span class="sxs-lookup"><span data-stu-id="40a9d-113">abstract</span></span>](../../../csharp/language-reference/keywords/abstract.md)|<span data-ttu-id="40a9d-114">Indique qu'une classe est destinée à être uniquement une classe de base d'autres classes.</span><span class="sxs-lookup"><span data-stu-id="40a9d-114">Indicates that a class is intended only to be a base class of other classes.</span></span>|  
|[<span data-ttu-id="40a9d-115">async</span><span class="sxs-lookup"><span data-stu-id="40a9d-115">async</span></span>](../../../csharp/language-reference/keywords/async.md)|<span data-ttu-id="40a9d-116">Indique que la méthode modifiée, une expression lambda ou une méthode anonyme sont asynchrones.</span><span class="sxs-lookup"><span data-stu-id="40a9d-116">Indicates that the modified method, lambda expression, or anonymous method is asynchronous.</span></span>|  
|[<span data-ttu-id="40a9d-117">const</span><span class="sxs-lookup"><span data-stu-id="40a9d-117">const</span></span>](../../../csharp/language-reference/keywords/const.md)|<span data-ttu-id="40a9d-118">Spécifie que la valeur du champ ou de la variable locale ne peut pas être modifiée.</span><span class="sxs-lookup"><span data-stu-id="40a9d-118">Specifies that the value of the field or the local variable cannot be modified.</span></span>|  
|[<span data-ttu-id="40a9d-119">event</span><span class="sxs-lookup"><span data-stu-id="40a9d-119">event</span></span>](../../../csharp/language-reference/keywords/event.md)|<span data-ttu-id="40a9d-120">Déclare un événement.</span><span class="sxs-lookup"><span data-stu-id="40a9d-120">Declares an event.</span></span>|  
|[<span data-ttu-id="40a9d-121">extern</span><span class="sxs-lookup"><span data-stu-id="40a9d-121">extern</span></span>](../../../csharp/language-reference/keywords/extern.md)|<span data-ttu-id="40a9d-122">Indique que la méthode est implémentée en externe.</span><span class="sxs-lookup"><span data-stu-id="40a9d-122">Indicates that the method is implemented externally.</span></span>|  
|[<span data-ttu-id="40a9d-123">new</span><span class="sxs-lookup"><span data-stu-id="40a9d-123">new</span></span>](../../../csharp/language-reference/keywords/new.md)|<span data-ttu-id="40a9d-124">Masque explicitement un membre hérité d'une classe de base.</span><span class="sxs-lookup"><span data-stu-id="40a9d-124">Explicitly hides a member inherited from a base class.</span></span>|  
|[<span data-ttu-id="40a9d-125">override</span><span class="sxs-lookup"><span data-stu-id="40a9d-125">override</span></span>](../../../csharp/language-reference/keywords/override.md)|<span data-ttu-id="40a9d-126">Fournit une nouvelle implémentation d'un membre virtuel hérité d'une classe de base.</span><span class="sxs-lookup"><span data-stu-id="40a9d-126">Provides a new implementation of a virtual member inherited from a base class.</span></span>|  
|[<span data-ttu-id="40a9d-127">partial</span><span class="sxs-lookup"><span data-stu-id="40a9d-127">partial</span></span>](../../../csharp/language-reference/keywords/partial-type.md)|<span data-ttu-id="40a9d-128">Définit des classes, des méthodes et des structs partiels dans le même assembly.</span><span class="sxs-lookup"><span data-stu-id="40a9d-128">Defines partial classes, structs and methods throughout the same assembly.</span></span>|  
|[<span data-ttu-id="40a9d-129">readonly</span><span class="sxs-lookup"><span data-stu-id="40a9d-129">readonly</span></span>](../../../csharp/language-reference/keywords/readonly.md)|<span data-ttu-id="40a9d-130">Déclare un champ auquel seules peuvent être attribuées des valeurs au sein de la déclaration ou dans un constructeur de la même classe.</span><span class="sxs-lookup"><span data-stu-id="40a9d-130">Declares a field that can only be assigned values as part of the declaration or in a constructor in the same class.</span></span>|  
|[<span data-ttu-id="40a9d-131">sealed</span><span class="sxs-lookup"><span data-stu-id="40a9d-131">sealed</span></span>](../../../csharp/language-reference/keywords/sealed.md)|<span data-ttu-id="40a9d-132">Spécifie qu'une classe ne peut pas être héritée.</span><span class="sxs-lookup"><span data-stu-id="40a9d-132">Specifies that a class cannot be inherited.</span></span>|  
|[<span data-ttu-id="40a9d-133">static</span><span class="sxs-lookup"><span data-stu-id="40a9d-133">static</span></span>](../../../csharp/language-reference/keywords/static.md)|<span data-ttu-id="40a9d-134">Déclare un membre qui appartient au type lui-même plutôt qu'à un objet spécifique.</span><span class="sxs-lookup"><span data-stu-id="40a9d-134">Declares a member that belongs to the type itself instead of to a specific object.</span></span>|  
|[<span data-ttu-id="40a9d-135">unsafe</span><span class="sxs-lookup"><span data-stu-id="40a9d-135">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)|<span data-ttu-id="40a9d-136">Déclare un contexte unsafe.</span><span class="sxs-lookup"><span data-stu-id="40a9d-136">Declares an unsafe context.</span></span>|  
|[<span data-ttu-id="40a9d-137">virtual</span><span class="sxs-lookup"><span data-stu-id="40a9d-137">virtual</span></span>](../../../csharp/language-reference/keywords/virtual.md)|<span data-ttu-id="40a9d-138">Déclare une méthode ou un accesseur dont l’implémentation peut être modifiée par un membre de substitution dans une classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="40a9d-138">Declares a method or an accessor whose implementation can be changed by an overriding member in a derived class.</span></span>|  
|[<span data-ttu-id="40a9d-139">volatile</span><span class="sxs-lookup"><span data-stu-id="40a9d-139">volatile</span></span>](../../../csharp/language-reference/keywords/volatile.md)|<span data-ttu-id="40a9d-140">Indique qu'un champ peut être modifié dans le programme par quelque chose, tel que le système d'exploitation, le matériel ou un thread s'exécutant simultanément.</span><span class="sxs-lookup"><span data-stu-id="40a9d-140">Indicates that a field can be modified in the program by something such as the operating system, the hardware, or a concurrently executing thread.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="40a9d-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="40a9d-141">See Also</span></span>  
 <span data-ttu-id="40a9d-142">[Informations de référence sur C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="40a9d-142">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="40a9d-143">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="40a9d-143">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="40a9d-144">Mots clés C#</span><span class="sxs-lookup"><span data-stu-id="40a9d-144">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)

