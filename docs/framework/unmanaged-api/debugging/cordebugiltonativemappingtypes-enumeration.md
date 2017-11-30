---
title: "CorDebugIlToNativeMappingTypes, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugIlToNativeMappingTypes
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugIlToNativeMappingTypes
helpviewer_keywords: CorDebugIIToNativeMappingTypes enumeration [.NET Framework debugging]
ms.assetid: c35e2919-42c3-4ba0-ae28-443c35f66f93
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 03046ebb678df64ad3d151aaadba313645417979
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="cordebugiltonativemappingtypes-enumeration"></a><span data-ttu-id="7873a-102">CorDebugIlToNativeMappingTypes, énumération</span><span class="sxs-lookup"><span data-stu-id="7873a-102">CorDebugIlToNativeMappingTypes Enumeration</span></span>
<span data-ttu-id="7873a-103">Indique si une plage particulière d’instructions natives, représentée par une instance de la structure COR_DEBUG_IL_TO_NATIVE_MAP, correspond à une région de code spéciale.</span><span class="sxs-lookup"><span data-stu-id="7873a-103">Indicates whether a particular range of native instructions, represented by an instance of the COR_DEBUG_IL_TO_NATIVE_MAP structure, corresponds to a special code region.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7873a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7873a-104">Syntax</span></span>  
  
```  
typedef enum CorDebugIlToNativeMappingTypes {  
    NO_MAPPING = -1,  
    PROLOG     = -2,  
    EPILOG     = -3  
} CorDebugIlToNativeMappingTypes;  
```  
  
## <a name="members"></a><span data-ttu-id="7873a-105">Membres</span><span class="sxs-lookup"><span data-stu-id="7873a-105">Members</span></span>  
  
|<span data-ttu-id="7873a-106">Membre</span><span class="sxs-lookup"><span data-stu-id="7873a-106">Member</span></span>|<span data-ttu-id="7873a-107">Description</span><span class="sxs-lookup"><span data-stu-id="7873a-107">Description</span></span>|  
|------------|-----------------|  
|`NO_MAPPING`|<span data-ttu-id="7873a-108">La plage d’instructions natives ne correspond pas à n’importe quelle région de code spéciale.</span><span class="sxs-lookup"><span data-stu-id="7873a-108">The range of native instructions does not correspond to any special code region.</span></span>|  
|`PROLOG`|<span data-ttu-id="7873a-109">La plage d’instructions natives correspond au prologue.</span><span class="sxs-lookup"><span data-stu-id="7873a-109">The range of native instructions corresponds to the prolog.</span></span>|  
|`EPILOG`|<span data-ttu-id="7873a-110">La plage d’instructions natives correspond à l’épilogue.</span><span class="sxs-lookup"><span data-stu-id="7873a-110">The range of native instructions corresponds to the epilog.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7873a-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="7873a-111">Requirements</span></span>  
 <span data-ttu-id="7873a-112">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7873a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7873a-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7873a-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7873a-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7873a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7873a-115">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7873a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7873a-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7873a-116">See Also</span></span>  
 [<span data-ttu-id="7873a-117">GetILToNativeMapping, méthode</span><span class="sxs-lookup"><span data-stu-id="7873a-117">GetILToNativeMapping Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getiltonativemapping-method.md)  
 [<span data-ttu-id="7873a-118">Énumérations de débogage</span><span class="sxs-lookup"><span data-stu-id="7873a-118">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
