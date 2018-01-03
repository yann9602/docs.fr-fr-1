---
title: "CorDebugPlatform, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugPlatformEnum
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugPlatformEnum
helpviewer_keywords: CorDebugPlatformEnum enumeration [.NET Framework debugging]
ms.assetid: c5444816-7378-4521-afd3-bf5e4b5303d5
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1f67ed6ad886c137eddaa42840f3f0edda88bd4a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugplatform-enumeration"></a><span data-ttu-id="55b4c-102">CorDebugPlatform, énumération</span><span class="sxs-lookup"><span data-stu-id="55b4c-102">CorDebugPlatform Enumeration</span></span>
<span data-ttu-id="55b4c-103">Fournit des valeurs de plateforme cible utilisées par le [ICorDebugDataTarget::GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="55b4c-103">Provides target platform values that are used by the [ICorDebugDataTarget::GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55b4c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="55b4c-104">Syntax</span></span>  
  
```  
typedef enum CorDebugPlatform  
{  
    CORDB_PLATFORM_WINDOWS_X86,    // Windows on Intel x86  
    CORDB_PLATFORM_WINDOWS_AMD64,  // Windows x64 (AMD64, Intel EM64T)  
    CORDB_PLATFORM_WINDOWS_IA64,   // Windows on Intel IA-64  
    CORDB_PLATFORM_MAC_PPC,        // Macintosh OS on PowerPC  
    CORDB_PLATFORM_MAC_X86,        // Macintosh OS on Intel x86  
    CORDB_PLATFORM_WINDOWS_ARM,    // Windows on ARM  
    CORDB_PLATFORM_MAC_AMD64       // MacOS on Intel x64  
} CorDebugPlatform;  
```  
  
## <a name="members"></a><span data-ttu-id="55b4c-105">Membres</span><span class="sxs-lookup"><span data-stu-id="55b4c-105">Members</span></span>  
  
|<span data-ttu-id="55b4c-106">Membre</span><span class="sxs-lookup"><span data-stu-id="55b4c-106">Member</span></span>|<span data-ttu-id="55b4c-107">Description</span><span class="sxs-lookup"><span data-stu-id="55b4c-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="55b4c-108">CORDB_PLATFORM_WINDOWS_X86</span><span class="sxs-lookup"><span data-stu-id="55b4c-108">CORDB_PLATFORM_WINDOWS_X86</span></span>|<span data-ttu-id="55b4c-109">La plateforme cible est Windows s'exécutant sur du matériel Intel x86.</span><span class="sxs-lookup"><span data-stu-id="55b4c-109">The target platform is Windows running on Intel x86 hardware.</span></span>|  
|<span data-ttu-id="55b4c-110">CORDB_PLATFORM_WINDOWS_AMD64</span><span class="sxs-lookup"><span data-stu-id="55b4c-110">CORDB_PLATFORM_WINDOWS_AMD64</span></span>|<span data-ttu-id="55b4c-111">La plateforme cible est Windows 64 bits s'exécutant sur du matériel AMD64 ou Intel EM64T.</span><span class="sxs-lookup"><span data-stu-id="55b4c-111">The target platform is 64 bit Windows running on AMD64 or Intel EM64T hardware.</span></span>|  
|<span data-ttu-id="55b4c-112">CORDB_PLATFORM_WINDOWS_IA64</span><span class="sxs-lookup"><span data-stu-id="55b4c-112">CORDB_PLATFORM_WINDOWS_IA64</span></span>|<span data-ttu-id="55b4c-113">La plateforme cible est Windows 32 bits s'exécutant sur du matériel IA-64.</span><span class="sxs-lookup"><span data-stu-id="55b4c-113">The target platform is 32 bit Windows running on Intel IA-64 hardware.</span></span>|  
|<span data-ttu-id="55b4c-114">CORDB_PLATFORM_MAC_PPC</span><span class="sxs-lookup"><span data-stu-id="55b4c-114">CORDB_PLATFORM_MAC_PPC</span></span>|<span data-ttu-id="55b4c-115">La plateforme cible est le système d’exploitation Macintosh s’exécutant sur du matériel PowerPC.</span><span class="sxs-lookup"><span data-stu-id="55b4c-115">The target platform is the Macintosh operating system running on PowerPC hardware.</span></span>|  
|<span data-ttu-id="55b4c-116">CORDB_PLATFORM_MAC_X86</span><span class="sxs-lookup"><span data-stu-id="55b4c-116">CORDB_PLATFORM_MAC_X86</span></span>|<span data-ttu-id="55b4c-117">La plateforme cible est en cours d’exécution sur du matériel Intel x86 avec le système d’exploitation Macintosh.</span><span class="sxs-lookup"><span data-stu-id="55b4c-117">The target platform is the Macintosh operating system running on Intel x86 hardware.</span></span>|  
|<span data-ttu-id="55b4c-118">CORDB_PLATFORM_WINDOWS_ARM</span><span class="sxs-lookup"><span data-stu-id="55b4c-118">CORDB_PLATFORM_WINDOWS_ARM</span></span>|<span data-ttu-id="55b4c-119">La plateforme cible est le système d’exploitation Macintosh s’exécutant sur le matériel Windows ARM.</span><span class="sxs-lookup"><span data-stu-id="55b4c-119">The target platform is the Macintosh operating system running on Windows ARM hardware.</span></span>|  
|<span data-ttu-id="55b4c-120">CORDB_PLATFORM_MAC_AMD64</span><span class="sxs-lookup"><span data-stu-id="55b4c-120">CORDB_PLATFORM_MAC_AMD64</span></span>|<span data-ttu-id="55b4c-121">La plateforme cible est en cours d’exécution sur du matériel AMD64 avec le système d’exploitation Macintosh.</span><span class="sxs-lookup"><span data-stu-id="55b4c-121">The target platform is the Macintosh operating system running on AMD64 hardware.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="55b4c-122">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="55b4c-122">Requirements</span></span>  
 <span data-ttu-id="55b4c-123">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="55b4c-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="55b4c-124">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="55b4c-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="55b4c-125">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="55b4c-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="55b4c-126">**Versions du .NET framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="55b4c-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
 <span data-ttu-id="55b4c-127">Les membres `CORDB_PLATFORM_WINDOWS_ARM` et `CORDB_PLATFORM_MAC_AMD64` sont disponibles dans .NET Framework 4.5.2 et ultérieur.</span><span class="sxs-lookup"><span data-stu-id="55b4c-127">The `CORDB_PLATFORM_WINDOWS_ARM` and `CORDB_PLATFORM_MAC_AMD64` members are available in the .NET Framework 4.5.2 and later versions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55b4c-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="55b4c-128">See Also</span></span>  
 [<span data-ttu-id="55b4c-129">Énumérations de débogage</span><span class="sxs-lookup"><span data-stu-id="55b4c-129">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
