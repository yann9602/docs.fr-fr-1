---
title: "CLRDataEnumMemoryFlags, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CLRDataEnumMemoryFlags
api_location: mscordbi.dll
api_type: COM
f1_keywords: CLRDataEnumMemoryFlags
helpviewer_keywords: CLRDataEnumMemoryFlags enumeration [.NET Framework debugging]
ms.assetid: e249f9fc-e24a-4506-903c-92781f6eab7c
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 88e8ca340c8512156606f10236c779daf96c3156
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="clrdataenummemoryflags-enumeration"></a><span data-ttu-id="92f05-102">CLRDataEnumMemoryFlags, énumération</span><span class="sxs-lookup"><span data-stu-id="92f05-102">CLRDataEnumMemoryFlags Enumeration</span></span>
<span data-ttu-id="92f05-103">Indique les régions de mémoire qu’un appel à la [ICLRDataEnumMemoryRegions::EnumMemoryRegions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) méthode doit inclure.</span><span class="sxs-lookup"><span data-stu-id="92f05-103">Indicates which memory regions a call to the [ICLRDataEnumMemoryRegions::EnumMemoryRegions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) method should include.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92f05-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="92f05-104">Syntax</span></span>  
  
```  
typedef enum CLRDataEnumMemoryFlags {  
    CLRDATA_ENUM_MEM_DEFAULT  = 0x0,  
    CLRDATA_ENUM_MEM_MINI     = CLRDATA_ENUM_MEM_DEFAULT,  
    CLRDATA_ENUM_MEM_HEAP     = 0x1  
} CLRDataEnumMemoryFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="92f05-105">Membres</span><span class="sxs-lookup"><span data-stu-id="92f05-105">Members</span></span>  
  
|<span data-ttu-id="92f05-106">Membre</span><span class="sxs-lookup"><span data-stu-id="92f05-106">Member</span></span>|<span data-ttu-id="92f05-107">Description</span><span class="sxs-lookup"><span data-stu-id="92f05-107">Description</span></span>|  
|------------|-----------------|  
|`CLRDATA_ENUM_MEM_DEFAULT`|<span data-ttu-id="92f05-108">Un minidump, autrement dit, une image mémoire incomplète.</span><span class="sxs-lookup"><span data-stu-id="92f05-108">A minidump, that is, a sparse memory dump.</span></span>|  
|`CLRDATA_ENUM_MEM_HEAP`|<span data-ttu-id="92f05-109">Un dump de tas complet.</span><span class="sxs-lookup"><span data-stu-id="92f05-109">A full heap dump.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="92f05-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="92f05-110">Requirements</span></span>  
 <span data-ttu-id="92f05-111">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92f05-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92f05-112">**En-tête :** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="92f05-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="92f05-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="92f05-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="92f05-114">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92f05-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92f05-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="92f05-115">See Also</span></span>  
 [<span data-ttu-id="92f05-116">Énumérations de débogage</span><span class="sxs-lookup"><span data-stu-id="92f05-116">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
