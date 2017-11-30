---
title: "CorDebugDebugEventKind, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugDebugEventKind
api_location: mscordbi.dll
api_type: COM
ms.assetid: 6075a6cd-97e6-4472-a090-0dd14860d1f3
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5aeb6085671e645e12713944d6456b9581a3886f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="cordebugdebugeventkind-enumeration"></a><span data-ttu-id="90b61-102">CorDebugDebugEventKind, énumération</span><span class="sxs-lookup"><span data-stu-id="90b61-102">CorDebugDebugEventKind Enumeration</span></span>
<span data-ttu-id="90b61-103">Indique le type d’événement dont les informations sont décodées par le [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="90b61-103">Indicates the type of event whose information is decoded by the [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90b61-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="90b61-104">Syntax</span></span>  
  
```  
typedef enum CorDebugDebugEventKind {  
    DEBUG_EVENT_KIND_MODULE_LOADED                          = 1,  
    DEBUG_EVENT_KIND_MODULE_UNLOADED                        = 2,  
    DEBUG_EVENT_KIND_MANAGED_EXCEPTION_FIRST_CHANCE         = 3,  
    DEBUG_EVENT_KIND_MANAGED_EXCEPTION_USER_FIRST_CHANCE    = 4,  
    DEBUG_EVENT_KIND_MANAGED_EXCEPTION_CATCH_HANDLER_FOUND  = 5,  
    DEBUG_EVENT_KIND_MANAGED_EXCEPTION_UNHANDLED            = 6  
} CorDebugRecordFormat;  
```  
  
## <a name="members"></a><span data-ttu-id="90b61-105">Membres</span><span class="sxs-lookup"><span data-stu-id="90b61-105">Members</span></span>  
  
|<span data-ttu-id="90b61-106">Membre</span><span class="sxs-lookup"><span data-stu-id="90b61-106">Member</span></span>|<span data-ttu-id="90b61-107">Description</span><span class="sxs-lookup"><span data-stu-id="90b61-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EVENT_KIND_MODULE_LOADED`|<span data-ttu-id="90b61-108">Événement de chargement de module.</span><span class="sxs-lookup"><span data-stu-id="90b61-108">A module load event.</span></span>|  
|`DEBUG_EVENT_KIND_MODULE_UNLOADED`|<span data-ttu-id="90b61-109">Événement de déchargement de module.</span><span class="sxs-lookup"><span data-stu-id="90b61-109">A module unload event.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_FIRST_CHANCE`|<span data-ttu-id="90b61-110">Exception de première chance.</span><span class="sxs-lookup"><span data-stu-id="90b61-110">A first-chance exception.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_USER_FIRST_CHANCE`|<span data-ttu-id="90b61-111">Exception utilisateur de première chance.</span><span class="sxs-lookup"><span data-stu-id="90b61-111">A first-chance user exception.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_CATCH_HANDLER_FOUND`|<span data-ttu-id="90b61-112">Exception pour laquelle il existe un gestionnaire `catch`.</span><span class="sxs-lookup"><span data-stu-id="90b61-112">An exception for which a `catch` handler exists.</span></span>|  
|`DEBUG_EVENT_KIND_MANAGED_EXCEPTION_UNHANDLED`|<span data-ttu-id="90b61-113">Exception non gérée.</span><span class="sxs-lookup"><span data-stu-id="90b61-113">An unhandled exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="90b61-114">Remarques</span><span class="sxs-lookup"><span data-stu-id="90b61-114">Remarks</span></span>  
 <span data-ttu-id="90b61-115">Un membre de la `CorDebugDebugEventKind` énumération est retournée en appelant le [ICorDebugDebugEvent::GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="90b61-115">A member of the `CorDebugDebugEventKind` enumeration is returned by calling the [ICorDebugDebugEvent::GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="90b61-116">Cette énumération est destinée à une utilisation dans des scénarios de débogage .NET Native uniquement.</span><span class="sxs-lookup"><span data-stu-id="90b61-116">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90b61-117">Spécifications</span><span class="sxs-lookup"><span data-stu-id="90b61-117">Requirements</span></span>  
 <span data-ttu-id="90b61-118">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="90b61-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90b61-119">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="90b61-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="90b61-120">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="90b61-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="90b61-121">**Versions du .NET framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90b61-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90b61-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="90b61-122">See Also</span></span>  
 [<span data-ttu-id="90b61-123">Énumérations de débogage</span><span class="sxs-lookup"><span data-stu-id="90b61-123">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
