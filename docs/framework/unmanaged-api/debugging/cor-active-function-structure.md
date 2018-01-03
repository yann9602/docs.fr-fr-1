---
title: COR_ACTIVE_FUNCTION, structure
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_ACTIVE_FUNCTION
api_location: mscordbi.dll
api_type: COM
f1_keywords: COR_ACTIVE_FUNCTION
helpviewer_keywords: COR_ACTIVE_FUNCTION structure [.NET Framework debugging]
ms.assetid: ed86185f-2152-459c-961f-10c06d62e83f
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7bb587f485427d9fd88e2f834d844ece18d336ca
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="coractivefunction-structure"></a><span data-ttu-id="879de-102">COR_ACTIVE_FUNCTION, structure</span><span class="sxs-lookup"><span data-stu-id="879de-102">COR_ACTIVE_FUNCTION Structure</span></span>
<span data-ttu-id="879de-103">Contient des informations sur les fonctions qui sont actuellement actives dans les trames d'un thread.</span><span class="sxs-lookup"><span data-stu-id="879de-103">Contains information about the functions that are currently active in a thread's frames.</span></span> <span data-ttu-id="879de-104">Cette structure est utilisée par le [ICorDebugThread2::GetActiveFunctions](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getactivefunctions-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="879de-104">This structure is used by the [ICorDebugThread2::GetActiveFunctions](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getactivefunctions-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="879de-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="879de-105">Syntax</span></span>  
  
```  
typedef struct  _COR_ACTIVE_FUNCTION {  
    ICorDebugAppDomain   *pAppDomain;  
    ICorDebugModule      *pModule;  
    ICorDebugFunction2   *pFunction;  
    ULONG32              ilOffset;  
    ULONG32              flags;  
} COR_ACTIVE_FUNCTION;  
```  
  
## <a name="members"></a><span data-ttu-id="879de-106">Membres</span><span class="sxs-lookup"><span data-stu-id="879de-106">Members</span></span>  
  
|<span data-ttu-id="879de-107">Membre</span><span class="sxs-lookup"><span data-stu-id="879de-107">Member</span></span>|<span data-ttu-id="879de-108">Description</span><span class="sxs-lookup"><span data-stu-id="879de-108">Description</span></span>|  
|------------|-----------------|  
|`pAppDomain`|<span data-ttu-id="879de-109">Pointeur vers le propriétaire du domaine d’application le `ilOffset` champ.</span><span class="sxs-lookup"><span data-stu-id="879de-109">Pointer to the application domain owner of the `ilOffset` field.</span></span>|  
|`pModule`|<span data-ttu-id="879de-110">Pointeur vers le propriétaire du module du `ilOffset` champ.</span><span class="sxs-lookup"><span data-stu-id="879de-110">Pointer to the module owner of the `ilOffset` field.</span></span>|  
|`pFunction`|<span data-ttu-id="879de-111">Pointeur vers le propriétaire de la fonction de la `ilOffset` champ.</span><span class="sxs-lookup"><span data-stu-id="879de-111">Pointer to the function owner of the `ilOffset` field.</span></span>|  
|`ilOffset`|<span data-ttu-id="879de-112">L’offset Microsoft intermediate language (MSIL), de l’image.</span><span class="sxs-lookup"><span data-stu-id="879de-112">The Microsoft intermediate language (MSIL) offset of the frame.</span></span>|  
|`flags`|<span data-ttu-id="879de-113">Réservé pour une future extensibilité.</span><span class="sxs-lookup"><span data-stu-id="879de-113">Reserved for future extensibility.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="879de-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="879de-114">Requirements</span></span>  
 <span data-ttu-id="879de-115">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="879de-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="879de-116">**En-tête :** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="879de-116">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="879de-117">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="879de-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="879de-118">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="879de-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="879de-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="879de-119">See Also</span></span>  
 [<span data-ttu-id="879de-120">Structures de débogage</span><span class="sxs-lookup"><span data-stu-id="879de-120">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="879de-121">Débogage</span><span class="sxs-lookup"><span data-stu-id="879de-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
