---
title: Utilisation de types d'exceptions standard
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- throwing exceptions, standard types
- catching exceptions
- exceptions, catching
- exceptions, throwing
ms.assetid: ab22ce03-78f9-4dca-8824-c7ed3bdccc27
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 5098db5131c2e47c0b73efaac51477ef3b107761
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="using-standard-exception-types"></a><span data-ttu-id="d8f8e-102">Utilisation de types d'exceptions standard</span><span class="sxs-lookup"><span data-stu-id="d8f8e-102">Using Standard Exception Types</span></span>
<span data-ttu-id="d8f8e-103">Cette section décrit les exceptions standard fournies par le Framework et les détails d’utilisation.</span><span class="sxs-lookup"><span data-stu-id="d8f8e-103">This section describes the standard exceptions provided by the Framework and the details of their usage.</span></span> <span data-ttu-id="d8f8e-104">La liste n’est pas exhaustive.</span><span class="sxs-lookup"><span data-stu-id="d8f8e-104">The list is by no means exhaustive.</span></span> <span data-ttu-id="d8f8e-105">Reportez-vous à la documentation de référence du .NET Framework pour l’utilisation des autres types d’exception Framework.</span><span class="sxs-lookup"><span data-stu-id="d8f8e-105">Please refer to the .NET Framework reference documentation for usage of other Framework exception types.</span></span>  
  
## <a name="exception-and-systemexception"></a><span data-ttu-id="d8f8e-106">Exception et SystemException</span><span class="sxs-lookup"><span data-stu-id="d8f8e-106">Exception and SystemException</span></span>  
 <span data-ttu-id="d8f8e-107">**X ne sont pas** lever <xref:System.Exception?displayProperty=nameWithType> ou <xref:System.SystemException?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d8f8e-107">**X DO NOT** throw <xref:System.Exception?displayProperty=nameWithType> or <xref:System.SystemException?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="d8f8e-108">**X ne sont pas** catch `System.Exception` ou `System.SystemException` dans le code d’infrastructure, sauf si vous souhaitez lever de nouveau.</span><span class="sxs-lookup"><span data-stu-id="d8f8e-108">**X DO NOT** catch `System.Exception` or `System.SystemException` in framework code, unless you intend to rethrow.</span></span>  
  
 <span data-ttu-id="d8f8e-109">**X Évitez** interception `System.Exception` ou `System.SystemException`, sauf dans les gestionnaires d’exceptions de niveau supérieur.</span><span class="sxs-lookup"><span data-stu-id="d8f8e-109">**X AVOID** catching `System.Exception` or `System.SystemException`, except in top-level exception handlers.</span></span>  
  
## <a name="applicationexception"></a><span data-ttu-id="d8f8e-110">ApplicationException</span><span class="sxs-lookup"><span data-stu-id="d8f8e-110">ApplicationException</span></span>  
 <span data-ttu-id="d8f8e-111">**X ne sont pas** lever ou dériver de <xref:System.ApplicationException>.</span><span class="sxs-lookup"><span data-stu-id="d8f8e-111">**X DO NOT** throw or derive from <xref:System.ApplicationException>.</span></span>  
  
## <a name="invalidoperationexception"></a><span data-ttu-id="d8f8e-112">InvalidOperationException</span><span class="sxs-lookup"><span data-stu-id="d8f8e-112">InvalidOperationException</span></span>  
 <span data-ttu-id="d8f8e-113">**✓ FAIRE** lever un <xref:System.InvalidOperationException> si l’objet est dans un état inapproprié.</span><span class="sxs-lookup"><span data-stu-id="d8f8e-113">**✓ DO** throw an <xref:System.InvalidOperationException> if the object is in an inappropriate state.</span></span>  
  
## <a name="argumentexception-argumentnullexception-and-argumentoutofrangeexception"></a><span data-ttu-id="d8f8e-114">ArgumentException, ArgumentNullException et ArgumentOutOfRangeException</span><span class="sxs-lookup"><span data-stu-id="d8f8e-114">ArgumentException, ArgumentNullException, and ArgumentOutOfRangeException</span></span>  
 <span data-ttu-id="d8f8e-115">**✓ FAIRE** lever <xref:System.ArgumentException> ou l’un de ses sous-types si des arguments incorrects sont passés à un membre.</span><span class="sxs-lookup"><span data-stu-id="d8f8e-115">**✓ DO** throw <xref:System.ArgumentException> or one of its subtypes if bad arguments are passed to a member.</span></span> <span data-ttu-id="d8f8e-116">Préférez le type plus dérivé de l’exception, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="d8f8e-116">Prefer the most derived exception type, if applicable.</span></span>  
  
 <span data-ttu-id="d8f8e-117">**✓ FAIRE** définir le `ParamName` propriété lors de la levée d’une des sous-classes de `ArgumentException`.</span><span class="sxs-lookup"><span data-stu-id="d8f8e-117">**✓ DO** set the `ParamName` property when throwing one of the subclasses of `ArgumentException`.</span></span>  
  
 <span data-ttu-id="d8f8e-118">Cette propriété représente le nom du paramètre ayant provoqué l’exception levée.</span><span class="sxs-lookup"><span data-stu-id="d8f8e-118">This property represents the name of the parameter that caused the exception to be thrown.</span></span> <span data-ttu-id="d8f8e-119">Notez que la propriété peut être définie à l’aide d’une des surcharges de constructeur.</span><span class="sxs-lookup"><span data-stu-id="d8f8e-119">Note that the property can be set using one of the constructor overloads.</span></span>  
  
 <span data-ttu-id="d8f8e-120">**✓ FAIRE** utiliser `value` pour le nom du paramètre de valeur implicite d’accesseurs Set de propriété.</span><span class="sxs-lookup"><span data-stu-id="d8f8e-120">**✓ DO** use `value` for the name of the implicit value parameter of property setters.</span></span>  
  
## <a name="nullreferenceexception-indexoutofrangeexception-and-accessviolationexception"></a><span data-ttu-id="d8f8e-121">NullReferenceException et IndexOutOfRangeException AccessViolationException</span><span class="sxs-lookup"><span data-stu-id="d8f8e-121">NullReferenceException, IndexOutOfRangeException, and AccessViolationException</span></span>  
 <span data-ttu-id="d8f8e-122">**X ne sont pas** autoriser API pouvant être appelées publiquement à lever explicitement ou implicitement <xref:System.NullReferenceException>, <xref:System.AccessViolationException>, ou <xref:System.IndexOutOfRangeException>.</span><span class="sxs-lookup"><span data-stu-id="d8f8e-122">**X DO NOT** allow publicly callable APIs to explicitly or implicitly throw <xref:System.NullReferenceException>, <xref:System.AccessViolationException>, or <xref:System.IndexOutOfRangeException>.</span></span> <span data-ttu-id="d8f8e-123">Ces exceptions sont réservées et levée par le moteur d’exécution et dans que la plupart des cas indiquer un bogue.</span><span class="sxs-lookup"><span data-stu-id="d8f8e-123">These exceptions are reserved and thrown by the execution engine and in most cases indicate a bug.</span></span>  
  
 <span data-ttu-id="d8f8e-124">Effectuer la vérification pour éviter de lever les exceptions d’argument.</span><span class="sxs-lookup"><span data-stu-id="d8f8e-124">Do argument checking to avoid throwing these exceptions.</span></span> <span data-ttu-id="d8f8e-125">Levée de ces exceptions expose des détails d’implémentation de votre méthode peuvent changer au fil du temps.</span><span class="sxs-lookup"><span data-stu-id="d8f8e-125">Throwing these exceptions exposes implementation details of your method that might change over time.</span></span>  
  
## <a name="stackoverflowexception"></a><span data-ttu-id="d8f8e-126">StackOverflowException</span><span class="sxs-lookup"><span data-stu-id="d8f8e-126">StackOverflowException</span></span>  
 <span data-ttu-id="d8f8e-127">**X ne sont pas** lever explicitement <xref:System.StackOverflowException>.</span><span class="sxs-lookup"><span data-stu-id="d8f8e-127">**X DO NOT** explicitly throw <xref:System.StackOverflowException>.</span></span> <span data-ttu-id="d8f8e-128">L’exception doit être levée explicitement uniquement par le CLR.</span><span class="sxs-lookup"><span data-stu-id="d8f8e-128">The exception should be explicitly thrown only by the CLR.</span></span>  
  
 <span data-ttu-id="d8f8e-129">**X ne sont pas** catch `StackOverflowException`.</span><span class="sxs-lookup"><span data-stu-id="d8f8e-129">**X DO NOT** catch `StackOverflowException`.</span></span>  
  
 <span data-ttu-id="d8f8e-130">Il est quasiment impossible d’écrire du code managé qui reste cohérent en cas de dépassement arbitraire.</span><span class="sxs-lookup"><span data-stu-id="d8f8e-130">It is almost impossible to write managed code that remains consistent in the presence of arbitrary stack overflows.</span></span> <span data-ttu-id="d8f8e-131">Les parties non managés du CLR restent cohérentes à l’aide de sondes pour déplacer les dépassements de capacité de pile à des endroits bien définis, plutôt que par la régularisation de dépassement arbitraire.</span><span class="sxs-lookup"><span data-stu-id="d8f8e-131">The unmanaged parts of the CLR remain consistent by using probes to move stack overflows to well-defined places rather than by backing out from arbitrary stack overflows.</span></span>  
  
## <a name="outofmemoryexception"></a><span data-ttu-id="d8f8e-132">OutOfMemoryException</span><span class="sxs-lookup"><span data-stu-id="d8f8e-132">OutOfMemoryException</span></span>  
 <span data-ttu-id="d8f8e-133">**X ne sont pas** lever explicitement <xref:System.OutOfMemoryException>.</span><span class="sxs-lookup"><span data-stu-id="d8f8e-133">**X DO NOT** explicitly throw <xref:System.OutOfMemoryException>.</span></span> <span data-ttu-id="d8f8e-134">Cette exception est levée uniquement par l’infrastructure CLR.</span><span class="sxs-lookup"><span data-stu-id="d8f8e-134">This exception is to be thrown only by the CLR infrastructure.</span></span>  
  
## <a name="comexception-sehexception-and-executionengineexception"></a><span data-ttu-id="d8f8e-135">ComException et SEHException ExecutionEngineException</span><span class="sxs-lookup"><span data-stu-id="d8f8e-135">ComException, SEHException, and ExecutionEngineException</span></span>  
 <span data-ttu-id="d8f8e-136">**X ne sont pas** lever explicitement <xref:System.Runtime.InteropServices.COMException>, <xref:System.ExecutionEngineException>, et <xref:System.Runtime.InteropServices.SEHException>.</span><span class="sxs-lookup"><span data-stu-id="d8f8e-136">**X DO NOT** explicitly throw <xref:System.Runtime.InteropServices.COMException>,  <xref:System.ExecutionEngineException>, and <xref:System.Runtime.InteropServices.SEHException>.</span></span> <span data-ttu-id="d8f8e-137">Ces exceptions doivent être levée uniquement par l’infrastructure du CLR.</span><span class="sxs-lookup"><span data-stu-id="d8f8e-137">These exceptions are to be thrown only by the CLR infrastructure.</span></span>  
  
 <span data-ttu-id="d8f8e-138">*Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*</span><span class="sxs-lookup"><span data-stu-id="d8f8e-138">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="d8f8e-139">*Réimprimées avec l’autorisation de Pearson éducation, Inc. à partir de [règles de conception d’infrastructure : Conventions, idiomes et des modèles pour les bibliothèques .NET réutilisable, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série de développement Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="d8f8e-139">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8f8e-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d8f8e-140">See Also</span></span>  
 [<span data-ttu-id="d8f8e-141">Règles de conception de .NET Framework</span><span class="sxs-lookup"><span data-stu-id="d8f8e-141">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="d8f8e-142">Instructions de conception pour les exceptions</span><span class="sxs-lookup"><span data-stu-id="d8f8e-142">Design Guidelines for Exceptions</span></span>](../../../docs/standard/design-guidelines/exceptions.md)
