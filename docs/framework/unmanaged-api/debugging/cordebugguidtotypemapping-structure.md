---
title: CorDebugGuidToTypeMapping, structure
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: CorDebugGuidToTypeMapping
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugGuidToTypeMapping
helpviewer_keywords: CorDebugGuidToTypeMapping structure [.NET Framework debugging]
ms.assetid: 57dbccd9-b16d-4da3-ae25-7a2cf9adf679
topic_type: apiref
caps.latest.revision: "3"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ecdadc96c0fb850fef13ba978fc97eef91dadd65
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugguidtotypemapping-structure"></a><span data-ttu-id="bb786-102">CorDebugGuidToTypeMapping, structure</span><span class="sxs-lookup"><span data-stu-id="bb786-102">CorDebugGuidToTypeMapping Structure</span></span>
<span data-ttu-id="bb786-103">Mappe un [!INCLUDE[wrt](../../../../includes/wrt-md.md)] GUID à son objet ICorDebugType correspondant.</span><span class="sxs-lookup"><span data-stu-id="bb786-103">Maps a [!INCLUDE[wrt](../../../../includes/wrt-md.md)] GUID to its corresponding ICorDebugType object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb786-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bb786-104">Syntax</span></span>  
  
```cpp
typedef struct CorDebugGuidToTypeMapping {  
    GUID iid;  
    ICorDebugType *pType;  
} CorDebugGuidToTypeMapping;  
```  
  
## <a name="members"></a><span data-ttu-id="bb786-105">Membres</span><span class="sxs-lookup"><span data-stu-id="bb786-105">Members</span></span>  
  
|<span data-ttu-id="bb786-106">Membre</span><span class="sxs-lookup"><span data-stu-id="bb786-106">Member</span></span>|<span data-ttu-id="bb786-107">Description</span><span class="sxs-lookup"><span data-stu-id="bb786-107">Description</span></span>|  
|------------|-----------------|  
|`iid`|<span data-ttu-id="bb786-108">Le GUID de la mise en cache [!INCLUDE[wrt](../../../../includes/wrt-md.md)] type.</span><span class="sxs-lookup"><span data-stu-id="bb786-108">The GUID of the cached [!INCLUDE[wrt](../../../../includes/wrt-md.md)] type.</span></span>|  
|`pType`|<span data-ttu-id="bb786-109">Pointeur vers un objet ICorDebugType qui fournit des informations sur le type de mise en cache.</span><span class="sxs-lookup"><span data-stu-id="bb786-109">A pointer to an ICorDebugType object that provides information about the cached type.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bb786-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="bb786-110">Requirements</span></span>  
 <span data-ttu-id="bb786-111">**Plateformes :** [!INCLUDE[wrt](../../../../includes/wrt-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bb786-111">**Platforms:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)].</span></span>  
  
 <span data-ttu-id="bb786-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bb786-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bb786-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bb786-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bb786-114">**Versions du .NET framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb786-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb786-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bb786-115">See Also</span></span>  
 [<span data-ttu-id="bb786-116">Structures de débogage</span><span class="sxs-lookup"><span data-stu-id="bb786-116">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="bb786-117">Débogage</span><span class="sxs-lookup"><span data-stu-id="bb786-117">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
