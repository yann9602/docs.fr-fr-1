---
title: "CorDebugCreateProcessFlags, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugCreateProcessFlags
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugCreateProcessFlags
helpviewer_keywords: CorDebugCreateProcessFlags enumeration [.NET Framework debugging]
ms.assetid: e709acce-6a17-4346-b38a-467dba567358
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 35503a89077b05d622ccc3f8e5cf1bb7d95ea9e0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="cordebugcreateprocessflags-enumeration"></a><span data-ttu-id="d54a1-102">CorDebugCreateProcessFlags, énumération</span><span class="sxs-lookup"><span data-stu-id="d54a1-102">CorDebugCreateProcessFlags Enumeration</span></span>
<span data-ttu-id="d54a1-103">Fournit des options de débogage supplémentaires qui peuvent être utilisées dans un appel à la [ICorDebug::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="d54a1-103">Provides additional debugging options that can be used in a call to the [ICorDebug::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d54a1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d54a1-104">Syntax</span></span>  
  
```  
typedef enum CorDebugCreateProcessFlags {  
    DEBUG_NO_SPECIAL_OPTIONS    = 0x0000  
} CorDebugCreateProcessFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="d54a1-105">Membres</span><span class="sxs-lookup"><span data-stu-id="d54a1-105">Members</span></span>  
  
|<span data-ttu-id="d54a1-106">Membre</span><span class="sxs-lookup"><span data-stu-id="d54a1-106">Member</span></span>|<span data-ttu-id="d54a1-107">Description</span><span class="sxs-lookup"><span data-stu-id="d54a1-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_NO_SPECIAL_OPTIONS`|<span data-ttu-id="d54a1-108">Sans options spéciales sont définies.</span><span class="sxs-lookup"><span data-stu-id="d54a1-108">No special options are set.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d54a1-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="d54a1-109">Requirements</span></span>  
 <span data-ttu-id="d54a1-110">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d54a1-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d54a1-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d54a1-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d54a1-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d54a1-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d54a1-113">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d54a1-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d54a1-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d54a1-114">See Also</span></span>  
 [<span data-ttu-id="d54a1-115">Énumérations de débogage</span><span class="sxs-lookup"><span data-stu-id="d54a1-115">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
