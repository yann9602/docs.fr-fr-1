---
title: "Événements ETW d'interopérabilité"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interop events [.NET Framework]
- ETW, interop events (CLR)
ms.assetid: eb6eac2e-45f4-4923-a32c-38f203da66df
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 55097e38161ea5c76f4e46584241344ec5a52cb9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="interop-etw-events"></a><span data-ttu-id="1c7a6-102">Événements ETW d'interopérabilité</span><span class="sxs-lookup"><span data-stu-id="1c7a6-102">Interop ETW Events</span></span>
<span data-ttu-id="1c7a6-103"><a name="top"></a> Les événements d'interopérabilité capturent des informations sur la création et la mise en cache du stub MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="1c7a6-103"><a name="top"></a> Interop events capture information about Microsoft intermediate language (MSIL) stub generation and caching.</span></span>  
  
 <span data-ttu-id="1c7a6-104">Cette catégorie comprend les événements suivants :</span><span class="sxs-lookup"><span data-stu-id="1c7a6-104">This category consists of the following events:</span></span>  
  
-   [<span data-ttu-id="1c7a6-105">Événement ILStubGenerated</span><span class="sxs-lookup"><span data-stu-id="1c7a6-105">ILStubGenerated Event</span></span>](#ilstubgenerated_event)  
  
-   [<span data-ttu-id="1c7a6-106">Événement ILStubCacheHit</span><span class="sxs-lookup"><span data-stu-id="1c7a6-106">ILStubCacheHit Event</span></span>](#ilstubcachehit_event)  
  
<a name="ilstubgenerated_event"></a>   
## <a name="ilstubgenerated-event"></a><span data-ttu-id="1c7a6-107">Événement ILStubGenerated</span><span class="sxs-lookup"><span data-stu-id="1c7a6-107">ILStubGenerated Event</span></span>  
 <span data-ttu-id="1c7a6-108">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="1c7a6-108">The following table shows the keyword and level.</span></span> <span data-ttu-id="1c7a6-109">(Pour plus d'informations, consultez [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="1c7a6-109">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="1c7a6-110">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="1c7a6-110">Keyword for raising the event</span></span>|<span data-ttu-id="1c7a6-111">Niveau</span><span class="sxs-lookup"><span data-stu-id="1c7a6-111">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="1c7a6-112">`InteropKeyword` (0x2000)</span><span class="sxs-lookup"><span data-stu-id="1c7a6-112">`InteropKeyword` (0x2000)</span></span>|<span data-ttu-id="1c7a6-113">Informatif(4)</span><span class="sxs-lookup"><span data-stu-id="1c7a6-113">Informational(4)</span></span>|  
  
 <span data-ttu-id="1c7a6-114">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="1c7a6-114">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="1c7a6-115">Événement</span><span class="sxs-lookup"><span data-stu-id="1c7a6-115">Event</span></span>|<span data-ttu-id="1c7a6-116">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="1c7a6-116">Event ID</span></span>|<span data-ttu-id="1c7a6-117">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="1c7a6-117">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ILStubGenerated`|<span data-ttu-id="1c7a6-118">88</span><span class="sxs-lookup"><span data-stu-id="1c7a6-118">88</span></span>|<span data-ttu-id="1c7a6-119">Le stub MSIL a été généré.</span><span class="sxs-lookup"><span data-stu-id="1c7a6-119">The MSIL stub has been generated.</span></span>|  
  
 <span data-ttu-id="1c7a6-120">Le tableau ci-dessous montre les données liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="1c7a6-120">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="1c7a6-121">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="1c7a6-121">Field name</span></span>|<span data-ttu-id="1c7a6-122">Type de données</span><span class="sxs-lookup"><span data-stu-id="1c7a6-122">Data type</span></span>|<span data-ttu-id="1c7a6-123">Description</span><span class="sxs-lookup"><span data-stu-id="1c7a6-123">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="1c7a6-124">ModuleID</span><span class="sxs-lookup"><span data-stu-id="1c7a6-124">ModuleID</span></span>|<span data-ttu-id="1c7a6-125">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="1c7a6-125">win:UInt16</span></span>|<span data-ttu-id="1c7a6-126">Identificateur du module</span><span class="sxs-lookup"><span data-stu-id="1c7a6-126">The module identifier.</span></span>|  
|<span data-ttu-id="1c7a6-127">StubMethodID</span><span class="sxs-lookup"><span data-stu-id="1c7a6-127">StubMethodID</span></span>|<span data-ttu-id="1c7a6-128">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="1c7a6-128">win:UInt64</span></span>|<span data-ttu-id="1c7a6-129">Identificateur de la méthode stub</span><span class="sxs-lookup"><span data-stu-id="1c7a6-129">The stub method identifier.</span></span>|  
|<span data-ttu-id="1c7a6-130">StubFlags</span><span class="sxs-lookup"><span data-stu-id="1c7a6-130">StubFlags</span></span>|<span data-ttu-id="1c7a6-131">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="1c7a6-131">win:UInt64</span></span>|<span data-ttu-id="1c7a6-132">Indicateurs du stub :</span><span class="sxs-lookup"><span data-stu-id="1c7a6-132">The flags for the stub:</span></span><br /><br /> <span data-ttu-id="1c7a6-133">0x1 – Interopérabilité inversée.</span><span class="sxs-lookup"><span data-stu-id="1c7a6-133">0x1 - Reverse interop.</span></span><br /><br /> <span data-ttu-id="1c7a6-134">0x2 – COM Interop</span><span class="sxs-lookup"><span data-stu-id="1c7a6-134">0x2 - COM interop.</span></span><br /><br /> <span data-ttu-id="1c7a6-135">0x4 – Stub généré par NGen.exe.</span><span class="sxs-lookup"><span data-stu-id="1c7a6-135">0x4 - Stub generated by NGen.exe.</span></span><br /><br /> <span data-ttu-id="1c7a6-136">0x8 – Délégué</span><span class="sxs-lookup"><span data-stu-id="1c7a6-136">0x8 - Delegate.</span></span><br /><br /> <span data-ttu-id="1c7a6-137">0x10 – Argument variable</span><span class="sxs-lookup"><span data-stu-id="1c7a6-137">0x10 - Variable arrgument.</span></span><br /><br /> <span data-ttu-id="1c7a6-138">0x20 – Appelé non managé</span><span class="sxs-lookup"><span data-stu-id="1c7a6-138">0x20 - Unmanaged callee.</span></span>|  
|<span data-ttu-id="1c7a6-139">ManagedInteropMethodToken</span><span class="sxs-lookup"><span data-stu-id="1c7a6-139">ManagedInteropMethodToken</span></span>|<span data-ttu-id="1c7a6-140">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="1c7a6-140">win:UInt32</span></span>|<span data-ttu-id="1c7a6-141">Jeton de la méthode d’interopérabilité managée</span><span class="sxs-lookup"><span data-stu-id="1c7a6-141">The token for the managed interop method.</span></span>|  
|<span data-ttu-id="1c7a6-142">ManagedInteropMethodNameSpace</span><span class="sxs-lookup"><span data-stu-id="1c7a6-142">ManagedInteropMethodNameSpace</span></span>|<span data-ttu-id="1c7a6-143">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="1c7a6-143">win:UnicodeString</span></span>|<span data-ttu-id="1c7a6-144">Espace de noms de la méthode d’interopérabilité managée</span><span class="sxs-lookup"><span data-stu-id="1c7a6-144">The namespace of the managed interop method.</span></span>|  
|<span data-ttu-id="1c7a6-145">ManagedInteropMethodName</span><span class="sxs-lookup"><span data-stu-id="1c7a6-145">ManagedInteropMethodName</span></span>|<span data-ttu-id="1c7a6-146">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="1c7a6-146">win:UnicodeString</span></span>|<span data-ttu-id="1c7a6-147">Nom de la méthode d’interopérabilité managée</span><span class="sxs-lookup"><span data-stu-id="1c7a6-147">The name of the managed interop method.</span></span>|  
|<span data-ttu-id="1c7a6-148">ManagedInteropMethodSignature</span><span class="sxs-lookup"><span data-stu-id="1c7a6-148">ManagedInteropMethodSignature</span></span>|<span data-ttu-id="1c7a6-149">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="1c7a6-149">win:UnicodeString</span></span>|<span data-ttu-id="1c7a6-150">Signature de la méthode d'interopérabilité managée</span><span class="sxs-lookup"><span data-stu-id="1c7a6-150">The signature of the managed interop method.</span></span>|  
|<span data-ttu-id="1c7a6-151">NativeMethodSignature</span><span class="sxs-lookup"><span data-stu-id="1c7a6-151">NativeMethodSignature</span></span>|<span data-ttu-id="1c7a6-152">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="1c7a6-152">win:UnicodeString</span></span>|<span data-ttu-id="1c7a6-153">Signature de la méthode native</span><span class="sxs-lookup"><span data-stu-id="1c7a6-153">The native method signature.</span></span>|  
|<span data-ttu-id="1c7a6-154">StubMethodSignature</span><span class="sxs-lookup"><span data-stu-id="1c7a6-154">StubMethodSignature</span></span>|<span data-ttu-id="1c7a6-155">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="1c7a6-155">win:UnicodeString</span></span>|<span data-ttu-id="1c7a6-156">Signature de la méthode stub</span><span class="sxs-lookup"><span data-stu-id="1c7a6-156">The stub method signature.</span></span>|  
|<span data-ttu-id="1c7a6-157">StubMethodILCode</span><span class="sxs-lookup"><span data-stu-id="1c7a6-157">StubMethodILCode</span></span>|<span data-ttu-id="1c7a6-158">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="1c7a6-158">win:UnicodeString</span></span>|<span data-ttu-id="1c7a6-159">Code MSIL de la méthode stub</span><span class="sxs-lookup"><span data-stu-id="1c7a6-159">The MSIL code for the stub method.</span></span>|  
|<span data-ttu-id="1c7a6-160">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="1c7a6-160">ClrInstanceID</span></span>|<span data-ttu-id="1c7a6-161">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="1c7a6-161">win:UInt16</span></span>|<span data-ttu-id="1c7a6-162">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="1c7a6-162">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="1c7a6-163">Retour au début</span><span class="sxs-lookup"><span data-stu-id="1c7a6-163">Back to top</span></span>](#top)  
  
<a name="ilstubcachehit_event"></a>   
## <a name="ilstubcachehit-event"></a><span data-ttu-id="1c7a6-164">Événement ILStubCacheHit</span><span class="sxs-lookup"><span data-stu-id="1c7a6-164">ILStubCacheHit Event</span></span>  
 <span data-ttu-id="1c7a6-165">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="1c7a6-165">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="1c7a6-166">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="1c7a6-166">Keyword for raising the event</span></span>|<span data-ttu-id="1c7a6-167">Niveau</span><span class="sxs-lookup"><span data-stu-id="1c7a6-167">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="1c7a6-168">`InteropKeyword` (0x2000)</span><span class="sxs-lookup"><span data-stu-id="1c7a6-168">`InteropKeyword` (0x2000)</span></span>|<span data-ttu-id="1c7a6-169">Informatif(4)</span><span class="sxs-lookup"><span data-stu-id="1c7a6-169">Informational(4)</span></span>|  
  
 <span data-ttu-id="1c7a6-170">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="1c7a6-170">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="1c7a6-171">Événement</span><span class="sxs-lookup"><span data-stu-id="1c7a6-171">Event</span></span>|<span data-ttu-id="1c7a6-172">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="1c7a6-172">Event ID</span></span>|<span data-ttu-id="1c7a6-173">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="1c7a6-173">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ILStubCacheHit`|<span data-ttu-id="1c7a6-174">89</span><span class="sxs-lookup"><span data-stu-id="1c7a6-174">89</span></span>|<span data-ttu-id="1c7a6-175">Le cache MSIL a fait l’objet d’un accès.</span><span class="sxs-lookup"><span data-stu-id="1c7a6-175">The MSIL cache has been accessed.</span></span>|  
  
 <span data-ttu-id="1c7a6-176">Le tableau ci-dessous montre les données liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="1c7a6-176">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="1c7a6-177">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="1c7a6-177">Field name</span></span>|<span data-ttu-id="1c7a6-178">Type de données</span><span class="sxs-lookup"><span data-stu-id="1c7a6-178">Data type</span></span>|<span data-ttu-id="1c7a6-179">Description</span><span class="sxs-lookup"><span data-stu-id="1c7a6-179">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="1c7a6-180">ModuleID</span><span class="sxs-lookup"><span data-stu-id="1c7a6-180">ModuleID</span></span>|<span data-ttu-id="1c7a6-181">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="1c7a6-181">win:UInt16</span></span>|<span data-ttu-id="1c7a6-182">Identificateur du module</span><span class="sxs-lookup"><span data-stu-id="1c7a6-182">The module identifier.</span></span>|  
|<span data-ttu-id="1c7a6-183">StubMethodID</span><span class="sxs-lookup"><span data-stu-id="1c7a6-183">StubMethodID</span></span>|<span data-ttu-id="1c7a6-184">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="1c7a6-184">win:UInt64</span></span>|<span data-ttu-id="1c7a6-185">Identificateur de la méthode stub</span><span class="sxs-lookup"><span data-stu-id="1c7a6-185">The stub method identifier.</span></span>|  
|<span data-ttu-id="1c7a6-186">ManagedInteropMethodToken</span><span class="sxs-lookup"><span data-stu-id="1c7a6-186">ManagedInteropMethodToken</span></span>|<span data-ttu-id="1c7a6-187">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="1c7a6-187">win:UInt32</span></span>|<span data-ttu-id="1c7a6-188">Jeton de la méthode d’interopérabilité managée</span><span class="sxs-lookup"><span data-stu-id="1c7a6-188">The token for the managed interop method.</span></span>|  
|<span data-ttu-id="1c7a6-189">ManagedInteropMethodNameSpace</span><span class="sxs-lookup"><span data-stu-id="1c7a6-189">ManagedInteropMethodNameSpace</span></span>|<span data-ttu-id="1c7a6-190">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="1c7a6-190">win:UnicodeString</span></span>|<span data-ttu-id="1c7a6-191">Espace de noms de la méthode d’interopérabilité managée</span><span class="sxs-lookup"><span data-stu-id="1c7a6-191">The namespace of the managed interop method.</span></span>|  
|<span data-ttu-id="1c7a6-192">ManagedInteropMethodName</span><span class="sxs-lookup"><span data-stu-id="1c7a6-192">ManagedInteropMethodName</span></span>|<span data-ttu-id="1c7a6-193">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="1c7a6-193">win:UnicodeString</span></span>|<span data-ttu-id="1c7a6-194">Nom de la méthode d’interopérabilité managée</span><span class="sxs-lookup"><span data-stu-id="1c7a6-194">The name of the managed interop method.</span></span>|  
|<span data-ttu-id="1c7a6-195">ManagedInteropMethodSignature</span><span class="sxs-lookup"><span data-stu-id="1c7a6-195">ManagedInteropMethodSignature</span></span>|<span data-ttu-id="1c7a6-196">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="1c7a6-196">win:UnicodeString</span></span>|<span data-ttu-id="1c7a6-197">Signature de la méthode d'interopérabilité managée</span><span class="sxs-lookup"><span data-stu-id="1c7a6-197">The signature of the managed interop method.</span></span>|  
|<span data-ttu-id="1c7a6-198">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="1c7a6-198">ClrInstanceID</span></span>|<span data-ttu-id="1c7a6-199">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="1c7a6-199">win:UInt16</span></span>|<span data-ttu-id="1c7a6-200">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="1c7a6-200">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="1c7a6-201">Retour au début</span><span class="sxs-lookup"><span data-stu-id="1c7a6-201">Back to top</span></span>](#top)  
  
## <a name="see-also"></a><span data-ttu-id="1c7a6-202">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1c7a6-202">See Also</span></span>  
 [<span data-ttu-id="1c7a6-203">Événements ETW du CLR</span><span class="sxs-lookup"><span data-stu-id="1c7a6-203">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
