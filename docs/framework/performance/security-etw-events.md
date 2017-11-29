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
ms.openlocfilehash: a7e28eeabecfe0f1043328618f6e1be143f198a6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="security-etw-events"></a><span data-ttu-id="0375d-102">Événements de sécurité ETW</span><span class="sxs-lookup"><span data-stu-id="0375d-102">Security ETW Events</span></span>
<span data-ttu-id="0375d-103"><a name="top"></a> Les événements de sécurité sont déclenchés pendant la vérification de nom fort et la vérification Authenticode.</span><span class="sxs-lookup"><span data-stu-id="0375d-103"><a name="top"></a> Security events are raised during strong name verification and Authenticode verification.</span></span>  
  
 <span data-ttu-id="0375d-104">Cette catégorie comprend les événements suivants :</span><span class="sxs-lookup"><span data-stu-id="0375d-104">This category consists of the following events:</span></span>  
  
-   [<span data-ttu-id="0375d-105">Événements StrongNameVerificationStart_V1 et StrongNameVerificationStop_V1</span><span class="sxs-lookup"><span data-stu-id="0375d-105">StrongNameVerificationStart_V1 and StrongNameVerificationStop_V1 Events</span></span>](#strongnameverificationstart_v1_and_strongnameverificationstop_v1_events)  
  
-   [<span data-ttu-id="0375d-106">Événements AuthenticodeVerificationStart_V1 et AuthenticodeVerificationStop_V1</span><span class="sxs-lookup"><span data-stu-id="0375d-106">AuthenticodeVerificationStart_V1 and AuthenticodeVerificationStop_V1 Events</span></span>](#authenticodeverificationstart_v1_and_authenticodeverificationstop_v1_events)  
  
<a name="strongnameverificationstart_v1_and_strongnameverificationstop_v1_events"></a>   
## <a name="strongnameverificationstartv1-and-strongnameverificationstopv1-events"></a><span data-ttu-id="0375d-107">Événements StrongNameVerificationStart_V1 et StrongNameVerificationStop_V1</span><span class="sxs-lookup"><span data-stu-id="0375d-107">StrongNameVerificationStart_V1 and StrongNameVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="0375d-108">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="0375d-108">The following table shows the keyword and level.</span></span> <span data-ttu-id="0375d-109">(Pour plus d'informations, consultez [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="0375d-109">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="0375d-110">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="0375d-110">Keyword for raising the event</span></span>|<span data-ttu-id="0375d-111">Niveau</span><span class="sxs-lookup"><span data-stu-id="0375d-111">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="0375d-112">`SecurityKeyword` (0x400)</span><span class="sxs-lookup"><span data-stu-id="0375d-112">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="0375d-113">Informatif(4)</span><span class="sxs-lookup"><span data-stu-id="0375d-113">Informational(4)</span></span>|  
  
 <span data-ttu-id="0375d-114">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="0375d-114">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="0375d-115">Événement</span><span class="sxs-lookup"><span data-stu-id="0375d-115">Event</span></span>|<span data-ttu-id="0375d-116">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="0375d-116">Event ID</span></span>|<span data-ttu-id="0375d-117">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="0375d-117">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`StrongNameVerificationStart_V1`|<span data-ttu-id="0375d-118">181</span><span class="sxs-lookup"><span data-stu-id="0375d-118">181</span></span>|<span data-ttu-id="0375d-119">Début de la vérification de nom fort.</span><span class="sxs-lookup"><span data-stu-id="0375d-119">Start of strong name verification.</span></span>|  
|`StrongNameVerificationStop_V1`|<span data-ttu-id="0375d-120">182</span><span class="sxs-lookup"><span data-stu-id="0375d-120">182</span></span>|<span data-ttu-id="0375d-121">Fin de la vérification de nom fort.</span><span class="sxs-lookup"><span data-stu-id="0375d-121">End of strong name verification.</span></span>|  
  
 <span data-ttu-id="0375d-122">Le tableau ci-dessous montre les données liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="0375d-122">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="0375d-123">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="0375d-123">Field name</span></span>|<span data-ttu-id="0375d-124">Type de données</span><span class="sxs-lookup"><span data-stu-id="0375d-124">Data type</span></span>|<span data-ttu-id="0375d-125">Description</span><span class="sxs-lookup"><span data-stu-id="0375d-125">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="0375d-126">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="0375d-126">VerificationFlags</span></span>|<span data-ttu-id="0375d-127">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="0375d-127">win:UInt32</span></span>|<span data-ttu-id="0375d-128">Indicateurs de vérification.</span><span class="sxs-lookup"><span data-stu-id="0375d-128">The verification flags.</span></span>|  
|<span data-ttu-id="0375d-129">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="0375d-129">ErrorCode</span></span>|<span data-ttu-id="0375d-130">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="0375d-130">win:UInt32</span></span>|<span data-ttu-id="0375d-131">Code d'erreur HResult.</span><span class="sxs-lookup"><span data-stu-id="0375d-131">The HResult error code.</span></span>|  
|<span data-ttu-id="0375d-132">FullyQualifiedAssemblyName</span><span class="sxs-lookup"><span data-stu-id="0375d-132">FullyQualifiedAssemblyName</span></span>|<span data-ttu-id="0375d-133">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="0375d-133">win:UnicodeString</span></span>|<span data-ttu-id="0375d-134">Nom d'assembly qualifié complet.</span><span class="sxs-lookup"><span data-stu-id="0375d-134">The fully qualified assembly name.</span></span>|  
|<span data-ttu-id="0375d-135">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="0375d-135">ClrInstanceID</span></span>|<span data-ttu-id="0375d-136">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="0375d-136">win:UInt16</span></span>|<span data-ttu-id="0375d-137">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="0375d-137">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="0375d-138">Retour au début</span><span class="sxs-lookup"><span data-stu-id="0375d-138">Back to top</span></span>](#top)  
  
<a name="authenticodeverificationstart_v1_and_authenticodeverificationstop_v1_events"></a>   
## <a name="authenticodeverificationstartv1-and-authenticodeverificationstopv1-events"></a><span data-ttu-id="0375d-139">Événements AuthenticodeVerificationStart_V1 et AuthenticodeVerificationStop_V1</span><span class="sxs-lookup"><span data-stu-id="0375d-139">AuthenticodeVerificationStart_V1 and AuthenticodeVerificationStop_V1 Events</span></span>  
 <span data-ttu-id="0375d-140">Le tableau suivant montre les mots clés et les niveaux.</span><span class="sxs-lookup"><span data-stu-id="0375d-140">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="0375d-141">Mot clé pour déclencher l'événement</span><span class="sxs-lookup"><span data-stu-id="0375d-141">Keyword for raising the event</span></span>|<span data-ttu-id="0375d-142">Niveau</span><span class="sxs-lookup"><span data-stu-id="0375d-142">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="0375d-143">`SecurityKeyword` (0x400)</span><span class="sxs-lookup"><span data-stu-id="0375d-143">`SecurityKeyword` (0x400)</span></span>|<span data-ttu-id="0375d-144">Informatif(4)</span><span class="sxs-lookup"><span data-stu-id="0375d-144">Informational(4)</span></span>|  
  
 <span data-ttu-id="0375d-145">Le tableau ci-dessous montre les informations liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="0375d-145">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="0375d-146">Événement</span><span class="sxs-lookup"><span data-stu-id="0375d-146">Event</span></span>|<span data-ttu-id="0375d-147">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="0375d-147">Event ID</span></span>|<span data-ttu-id="0375d-148">Moment du déclenchement</span><span class="sxs-lookup"><span data-stu-id="0375d-148">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`AuthenticodeVerificationStart_V1`|<span data-ttu-id="0375d-149">183</span><span class="sxs-lookup"><span data-stu-id="0375d-149">183</span></span>|<span data-ttu-id="0375d-150">Début de la vérification Authenticode.</span><span class="sxs-lookup"><span data-stu-id="0375d-150">Start of Authenticode verification.</span></span>|  
|`AuthenticodeVerificationStop_V1`|<span data-ttu-id="0375d-151">184</span><span class="sxs-lookup"><span data-stu-id="0375d-151">184</span></span>|<span data-ttu-id="0375d-152">Fin de la vérification Authenticode.</span><span class="sxs-lookup"><span data-stu-id="0375d-152">End of Authenticode verification.</span></span>|  
  
 <span data-ttu-id="0375d-153">Le tableau ci-dessous montre les données liées aux événements.</span><span class="sxs-lookup"><span data-stu-id="0375d-153">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="0375d-154">Nom du champ</span><span class="sxs-lookup"><span data-stu-id="0375d-154">Field name</span></span>|<span data-ttu-id="0375d-155">Type de données</span><span class="sxs-lookup"><span data-stu-id="0375d-155">Data type</span></span>|<span data-ttu-id="0375d-156">Description</span><span class="sxs-lookup"><span data-stu-id="0375d-156">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="0375d-157">VerificationFlags</span><span class="sxs-lookup"><span data-stu-id="0375d-157">VerificationFlags</span></span>|<span data-ttu-id="0375d-158">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="0375d-158">win:UInt32</span></span>|<span data-ttu-id="0375d-159">Indicateurs de vérification.</span><span class="sxs-lookup"><span data-stu-id="0375d-159">The verification flags.</span></span>|  
|<span data-ttu-id="0375d-160">ErrorCode</span><span class="sxs-lookup"><span data-stu-id="0375d-160">ErrorCode</span></span>|<span data-ttu-id="0375d-161">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="0375d-161">win:UInt32</span></span>|<span data-ttu-id="0375d-162">Code d'erreur HResult.</span><span class="sxs-lookup"><span data-stu-id="0375d-162">The HResult error code.</span></span>|  
|<span data-ttu-id="0375d-163">ModulePath</span><span class="sxs-lookup"><span data-stu-id="0375d-163">ModulePath</span></span>|<span data-ttu-id="0375d-164">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="0375d-164">win:UnicodeString</span></span>|<span data-ttu-id="0375d-165">Chemin d’accès du module.</span><span class="sxs-lookup"><span data-stu-id="0375d-165">The module path.</span></span>|  
|<span data-ttu-id="0375d-166">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="0375d-166">ClrInstanceID</span></span>|<span data-ttu-id="0375d-167">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="0375d-167">win:UInt16</span></span>|<span data-ttu-id="0375d-168">ID unique de l'instance de CLR ou CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="0375d-168">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0375d-169">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0375d-169">See Also</span></span>  
 [<span data-ttu-id="0375d-170">Événements ETW du CLR</span><span class="sxs-lookup"><span data-stu-id="0375d-170">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
