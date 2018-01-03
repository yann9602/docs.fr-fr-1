---
title: "CorDebugMappingResult, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugMappingResult
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugMappingResult
helpviewer_keywords: CorDebugMappingResult enumeration [.NET Framework debugging]
ms.assetid: 701281dd-2936-45c8-a1f0-3bf7332b093b
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 924cfec87b99cba9621af02d4e78e72094060ae8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugmappingresult-enumeration"></a><span data-ttu-id="93f72-102">CorDebugMappingResult, énumération</span><span class="sxs-lookup"><span data-stu-id="93f72-102">CorDebugMappingResult Enumeration</span></span>
<span data-ttu-id="93f72-103">Fournit les détails sur la façon dont la valeur du pointeur d'instruction a été obtenue.</span><span class="sxs-lookup"><span data-stu-id="93f72-103">Provides the details of how the value of the instruction pointer (IP) was obtained.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93f72-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="93f72-104">Syntax</span></span>  
  
```  
typedef enum CorDebugMappingResult {  
    MAPPING_PROLOG              = 0x1,  
    MAPPING_EPILOG              = 0x2,  
    MAPPING_NO_INFO             = 0x4,  
    MAPPING_UNMAPPED_ADDRESS    = 0x8,  
    MAPPING_EXACT               = 0x10,  
    MAPPING_APPROXIMATE         = 0x20,  
} CorDebugMappingResult;  
```  
  
## <a name="members"></a><span data-ttu-id="93f72-105">Membres</span><span class="sxs-lookup"><span data-stu-id="93f72-105">Members</span></span>  
  
|<span data-ttu-id="93f72-106">Membre</span><span class="sxs-lookup"><span data-stu-id="93f72-106">Member</span></span>|<span data-ttu-id="93f72-107">Description</span><span class="sxs-lookup"><span data-stu-id="93f72-107">Description</span></span>|  
|------------|-----------------|  
|`MAPPING_PROLOG`|<span data-ttu-id="93f72-108">Le code natif est dans le prologue, la valeur de l’adresse IP est 0.</span><span class="sxs-lookup"><span data-stu-id="93f72-108">The native code is in the prolog, so the value of the IP is 0.</span></span>|  
|`MAPPING_EPILOG`|<span data-ttu-id="93f72-109">Le code natif est dans un épilogue, la valeur de l’adresse IP est l’adresse de la dernière instruction de la méthode.</span><span class="sxs-lookup"><span data-stu-id="93f72-109">The native code is in an epilog, so the value of the IP is the address of the last instruction of the method.</span></span>|  
|`MAPPING_NO_INFO`|<span data-ttu-id="93f72-110">Aucune information de mappage n’est disponible pour la méthode, la valeur de l’adresse IP est 0.</span><span class="sxs-lookup"><span data-stu-id="93f72-110">No mapping information is available for the method, so the value of the IP is 0.</span></span>|  
|`MAPPING_UNMAPPED_ADDRESS`|<span data-ttu-id="93f72-111">Bien qu’il existe des informations de mappage pour la méthode, l’adresse actuelle ne peut pas être mappé au code Microsoft intermediate language (MSIL).</span><span class="sxs-lookup"><span data-stu-id="93f72-111">Although there is mapping information for the method, the current address cannot be mapped to Microsoft intermediate language (MSIL) code.</span></span> <span data-ttu-id="93f72-112">La valeur de l’adresse IP est 0.</span><span class="sxs-lookup"><span data-stu-id="93f72-112">The value of the IP is 0.</span></span>|  
|`MAPPING_EXACT`|<span data-ttu-id="93f72-113">La méthode correspond exactement au code MSIL soit le frame a été interprété, donc la valeur de l’adresse IP est précise.</span><span class="sxs-lookup"><span data-stu-id="93f72-113">Either the method maps exactly to MSIL code or the frame has been interpreted, so the value of the IP is accurate.</span></span>|  
|`MAPPING_APPROXIMATE`|<span data-ttu-id="93f72-114">La méthode a été correctement mappée, mais la valeur de l’adresse IP peut être approximative.</span><span class="sxs-lookup"><span data-stu-id="93f72-114">The method was successfully mapped, but the value of the IP may be approximate.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="93f72-115">Notes</span><span class="sxs-lookup"><span data-stu-id="93f72-115">Remarks</span></span>  
 <span data-ttu-id="93f72-116">Vous pouvez utiliser la [ICorDebugILFrame::GetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getip-method.md) méthode pour obtenir la valeur du pointeur d’instruction.</span><span class="sxs-lookup"><span data-stu-id="93f72-116">You can use the [ICorDebugILFrame::GetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getip-method.md) method to obtain the value of the instruction pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93f72-117">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="93f72-117">Requirements</span></span>  
 <span data-ttu-id="93f72-118">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="93f72-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93f72-119">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="93f72-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="93f72-120">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="93f72-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="93f72-121">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93f72-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93f72-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="93f72-122">See Also</span></span>  
 [<span data-ttu-id="93f72-123">Énumérations de débogage</span><span class="sxs-lookup"><span data-stu-id="93f72-123">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
