---
title: "Événements de sécurité ETW"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security events [.NET Framework]
- ETW, security events (CLR)
ms.assetid: 0ed69f73-5c01-4514-bd63-979c6e38d41d
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: abf6e6896267b6d1c8449b020230381923f38f1f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="security-etw-events"></a><span data-ttu-id="bc0a2-102">Événements de sécurité ETW</span><span class="sxs-lookup"><span data-stu-id="bc0a2-102">Security ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="bc0a2-103">Les événements de sécurité sont déclenchés pendant la vérification de nom fort et la vérification Authenticode.</span><span class="sxs-lookup"><span data-stu-id="bc0a2-103">Security events are raised during strong name verification and Authenticode verification.</span></span>  
  
 <span data-ttu-id="bc0a2-104">Cette catégorie comprend les événements suivants :</span><span class="sxs-lookup"><span data-stu-id="bc0a2-104">This category consists of the following events:</span></span>  
  
-   [<span data-ttu-id="bc0a2-105">Événements StrongNameVerificationStart_V1 et StrongNameVerificationStop_V1</span><span class="sxs-lookup"><span data-stu-id="bc0a2-105">StrongNameVerificationStart_V1 and StrongNameVerificationStop_V1 Events</span></span>](#strongnameverificationstart_v1_and_strongnameverificationstop_v1_events)  
  
-   [<span data-ttu-id="bc0a2-106">Événements AuthenticodeVerificationStart_V1 et AuthenticodeVerificationStop_V1</span><span class="sxs-lookup"><span data-stu-id="bc0a2-106">AuthenticodeVerificationStart_V1 and AuthenticodeVerificationStop_V1 Events</span></span>](#authenticodeverificationstart_v1_and_authenticodeverificationstop_v1_events)  
  
<a name="strongnameverificationstart_v1_and_strongnameverificationstop_v1_events"></a>   
## <a name="strongnameverificationstartv1-and-strongnameverificationstopv1-events"></a><span data-ttu-id="bc0a2-107">Événements StrongNameVerificationStart_V1 et StrongNameVerificationStop_V1</span><span class="sxs-lookup"><span data-stu-id="bc0a2-107">StrongNameVerificationStart_V1 and StrongNameVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="bc0a2-108">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="bc0a2-108">The following table shows the keyword and level.</span></span> <span data-ttu-id="bc0a2-109">(Pour plus d'informations, consultez [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="bc0a2-109">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="bc0a2-110">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="bc0a2-110">Keyword for raising the event</span></span>|<span data-ttu-id="bc0a2-111">Niveau</span><span class="sxs-lookup"><span data-stu-id="bc0a2-111">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="bc0a2-112">`SecurityKeyword` (0x400)</span><span class="sxs-lookup"><span data-stu-id="bc0a2-112">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="bc0a2-113">Informatif(4)</span><span class="sxs-lookup"><span data-stu-id="bc0a2-113">Informational(4)</span></span>|  
  
 <span data-ttu-id="bc0a2-114">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="bc0a2-114">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="bc0a2-115">Événement</span><span class="sxs-lookup"><span data-stu-id="bc0a2-115">Event</span></span>|<span data-ttu-id="bc0a2-116">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="bc0a2-116">Event ID</span></span>|<span data-ttu-id="bc0a2-117">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="bc0a2-117">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`StrongNameVerificationStart_V1`|<span data-ttu-id="bc0a2-118">181</span><span class="sxs-lookup"><span data-stu-id="bc0a2-118">181</span></span>|<span data-ttu-id="bc0a2-119">Début de la vérification de nom fort.</span><span class="sxs-lookup"><span data-stu-id="bc0a2-119">Start of strong name verification.</span></span>|  
|`StrongNameVerificationStop_V1`|<span data-ttu-id="bc0a2-120">182</span><span class="sxs-lookup"><span data-stu-id="bc0a2-120">182</span></span>|<span data-ttu-id="bc0a2-121">Fin de la vérification de nom fort.</span><span class="sxs-lookup"><span data-stu-id="bc0a2-121">End of strong name verification.</span></span>|  
  
 <span data-ttu-id="bc0a2-122">Le tableau ci-dessous montre les données liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="bc0a2-122">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="bc0a2-123">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="bc0a2-123">Field name</span></span>|<span data-ttu-id="bc0a2-124">Type de données</span><span class="sxs-lookup"><span data-stu-id="bc0a2-124">Data type</span></span>|<span data-ttu-id="bc0a2-125">Description</span><span class="sxs-lookup"><span data-stu-id="bc0a2-125">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="bc0a2-126">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="bc0a2-126">VerificationFlags</span></span>|<span data-ttu-id="bc0a2-127">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="bc0a2-127">win:UInt32</span></span>|<span data-ttu-id="bc0a2-128">Indicateurs de vérification.</span><span class="sxs-lookup"><span data-stu-id="bc0a2-128">The verification flags.</span></span>|  
|<span data-ttu-id="bc0a2-129">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="bc0a2-129">ErrorCode</span></span>|<span data-ttu-id="bc0a2-130">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="bc0a2-130">win:UInt32</span></span>|<span data-ttu-id="bc0a2-131">Code d'erreur HResult.</span><span class="sxs-lookup"><span data-stu-id="bc0a2-131">The HResult error code.</span></span>|  
|<span data-ttu-id="bc0a2-132">FullyQualifiedAssemblyName</span><span class="sxs-lookup"><span data-stu-id="bc0a2-132">FullyQualifiedAssemblyName</span></span>|<span data-ttu-id="bc0a2-133">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="bc0a2-133">win:UnicodeString</span></span>|<span data-ttu-id="bc0a2-134">Nom d'assembly qualifié complet.</span><span class="sxs-lookup"><span data-stu-id="bc0a2-134">The fully qualified assembly name.</span></span>|  
|<span data-ttu-id="bc0a2-135">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="bc0a2-135">ClrInstanceID</span></span>|<span data-ttu-id="bc0a2-136">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="bc0a2-136">win:UInt16</span></span>|<span data-ttu-id="bc0a2-137">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="bc0a2-137">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="bc0a2-138">Retour au début</span><span class="sxs-lookup"><span data-stu-id="bc0a2-138">Back to top</span></span>](#top)  
  
<a name="authenticodeverificationstart_v1_and_authenticodeverificationstop_v1_events"></a>   
## <a name="authenticodeverificationstartv1-and-authenticodeverificationstopv1-events"></a><span data-ttu-id="bc0a2-139">Événements AuthenticodeVerificationStart_V1 et AuthenticodeVerificationStop_V1</span><span class="sxs-lookup"><span data-stu-id="bc0a2-139">AuthenticodeVerificationStart_V1 and AuthenticodeVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="bc0a2-140">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="bc0a2-140">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="bc0a2-141">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="bc0a2-141">Keyword for raising the event</span></span>|<span data-ttu-id="bc0a2-142">Niveau</span><span class="sxs-lookup"><span data-stu-id="bc0a2-142">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="bc0a2-143">`SecurityKeyword` (0x400)</span><span class="sxs-lookup"><span data-stu-id="bc0a2-143">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="bc0a2-144">Informatif(4)</span><span class="sxs-lookup"><span data-stu-id="bc0a2-144">Informational(4)</span></span>|  
  
 <span data-ttu-id="bc0a2-145">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="bc0a2-145">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="bc0a2-146">Événement</span><span class="sxs-lookup"><span data-stu-id="bc0a2-146">Event</span></span>|<span data-ttu-id="bc0a2-147">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="bc0a2-147">Event ID</span></span>|<span data-ttu-id="bc0a2-148">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="bc0a2-148">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AuthenticodeVerificationStart_V1`|<span data-ttu-id="bc0a2-149">183</span><span class="sxs-lookup"><span data-stu-id="bc0a2-149">183</span></span>|<span data-ttu-id="bc0a2-150">Début de la vérification Authenticode.</span><span class="sxs-lookup"><span data-stu-id="bc0a2-150">Start of Authenticode verification.</span></span>|  
|`AuthenticodeVerificationStop_V1`|<span data-ttu-id="bc0a2-151">184</span><span class="sxs-lookup"><span data-stu-id="bc0a2-151">184</span></span>|<span data-ttu-id="bc0a2-152">Fin de la vérification Authenticode.</span><span class="sxs-lookup"><span data-stu-id="bc0a2-152">End of Authenticode verification.</span></span>|  
  
 <span data-ttu-id="bc0a2-153">Le tableau ci-dessous montre les données liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="bc0a2-153">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="bc0a2-154">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="bc0a2-154">Field name</span></span>|<span data-ttu-id="bc0a2-155">Type de données</span><span class="sxs-lookup"><span data-stu-id="bc0a2-155">Data type</span></span>|<span data-ttu-id="bc0a2-156">Description</span><span class="sxs-lookup"><span data-stu-id="bc0a2-156">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="bc0a2-157">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="bc0a2-157">VerificationFlags</span></span>|<span data-ttu-id="bc0a2-158">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="bc0a2-158">win:UInt32</span></span>|<span data-ttu-id="bc0a2-159">Indicateurs de vérification.</span><span class="sxs-lookup"><span data-stu-id="bc0a2-159">The verification flags.</span></span>|  
|<span data-ttu-id="bc0a2-160">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="bc0a2-160">ErrorCode</span></span>|<span data-ttu-id="bc0a2-161">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="bc0a2-161">win:UInt32</span></span>|<span data-ttu-id="bc0a2-162">Code d'erreur HResult.</span><span class="sxs-lookup"><span data-stu-id="bc0a2-162">The HResult error code.</span></span>|  
|<span data-ttu-id="bc0a2-163">ModulePath</span><span class="sxs-lookup"><span data-stu-id="bc0a2-163">ModulePath</span></span>|<span data-ttu-id="bc0a2-164">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="bc0a2-164">win:UnicodeString</span></span>|<span data-ttu-id="bc0a2-165">Chemin d’accès du module.</span><span class="sxs-lookup"><span data-stu-id="bc0a2-165">The module path.</span></span>|  
|<span data-ttu-id="bc0a2-166">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="bc0a2-166">ClrInstanceID</span></span>|<span data-ttu-id="bc0a2-167">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="bc0a2-167">win:UInt16</span></span>|<span data-ttu-id="bc0a2-168">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="bc0a2-168">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bc0a2-169">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bc0a2-169">See Also</span></span>  
 [<span data-ttu-id="bc0a2-170">Événements ETW du CLR</span><span class="sxs-lookup"><span data-stu-id="bc0a2-170">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
