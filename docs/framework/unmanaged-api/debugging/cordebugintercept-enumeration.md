---
title: "CorDebugIntercept, énumération"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugIntercept
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugIntercept
helpviewer_keywords: CorDebugIntercept enumeration [.NET Framework debugging]
ms.assetid: 3d5b642e-7ef2-428b-a5ae-509c35ed461a
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b7d34b5f1bdff7a7089d780645b91503a8464849
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="cordebugintercept-enumeration"></a><span data-ttu-id="b1c35-102">CorDebugIntercept, énumération</span><span class="sxs-lookup"><span data-stu-id="b1c35-102">CorDebugIntercept Enumeration</span></span>
<span data-ttu-id="b1c35-103">Indique les types de code qui peuvent être interceptés (c'est-à-dire pouvant faire l'objet d'un pas à pas détaillé).</span><span class="sxs-lookup"><span data-stu-id="b1c35-103">Indicates the types of code that can be intercepted (that is, stepped into).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1c35-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b1c35-104">Syntax</span></span>  
  
```  
typedef enum CorDebugIntercept {  
    INTERCEPT_NONE                = 0x0,  
    INTERCEPT_CLASS_INIT          = 0x01,  
    INTERCEPT_EXCEPTION_FILTER    = 0x02,  
    INTERCEPT_SECURITY            = 0x04,  
    INTERCEPT_CONTEXT_POLICY      = 0x08,  
    INTERCEPT_INTERCEPTION        = 0x10,  
    INTERCEPT_ALL                 = 0xffff  
} CorDebugIntercept;  
```  
  
## <a name="members"></a><span data-ttu-id="b1c35-105">Membres</span><span class="sxs-lookup"><span data-stu-id="b1c35-105">Members</span></span>  
  
|<span data-ttu-id="b1c35-106">Membre</span><span class="sxs-lookup"><span data-stu-id="b1c35-106">Member</span></span>|<span data-ttu-id="b1c35-107">Description</span><span class="sxs-lookup"><span data-stu-id="b1c35-107">Description</span></span>|  
|------------|-----------------|  
|`INTERCEPT_NONE`|<span data-ttu-id="b1c35-108">Aucun code ne peut être intercepté.</span><span class="sxs-lookup"><span data-stu-id="b1c35-108">No code can be intercepted.</span></span>|  
|`INTERCEPT_CLASS_INIT`|<span data-ttu-id="b1c35-109">Un constructeur peut être intercepté.</span><span class="sxs-lookup"><span data-stu-id="b1c35-109">A constructor can be intercepted.</span></span>|  
|`INTERCEPT_EXCEPTION_FILTER`|<span data-ttu-id="b1c35-110">Un filtre d'exception peut être intercepté.</span><span class="sxs-lookup"><span data-stu-id="b1c35-110">An exception filter can be intercepted.</span></span>|  
|`INTERCEPT_SECURITY`|<span data-ttu-id="b1c35-111">Le code qui applique la sécurité peut être intercepté.</span><span class="sxs-lookup"><span data-stu-id="b1c35-111">Code that enforces security can be intercepted.</span></span>|  
|`INTERCEPT_CONTEXT_POLICY`|<span data-ttu-id="b1c35-112">Une stratégie de contexte peut être interceptée.</span><span class="sxs-lookup"><span data-stu-id="b1c35-112">A context policy can be intercepted.</span></span>|  
|`INTERCEPT_INTERCEPTION`|<span data-ttu-id="b1c35-113">Non utilisé.</span><span class="sxs-lookup"><span data-stu-id="b1c35-113">Not used.</span></span>|  
|`INTERCEPT_ALL`|<span data-ttu-id="b1c35-114">Aucun code ne peut être intercepté.</span><span class="sxs-lookup"><span data-stu-id="b1c35-114">All code can be intercepted.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b1c35-115">Remarques</span><span class="sxs-lookup"><span data-stu-id="b1c35-115">Remarks</span></span>  
 <span data-ttu-id="b1c35-116">Utilisez le [ICorDebugStepper::SetInterceptMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setinterceptmask-method.md) méthode pour définir les types de code qui peuvent être interceptés.</span><span class="sxs-lookup"><span data-stu-id="b1c35-116">Use the [ICorDebugStepper::SetInterceptMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setinterceptmask-method.md) method to establish the types of code that can be intercepted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1c35-117">Spécifications</span><span class="sxs-lookup"><span data-stu-id="b1c35-117">Requirements</span></span>  
 <span data-ttu-id="b1c35-118">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1c35-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1c35-119">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b1c35-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b1c35-120">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b1c35-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b1c35-121">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1c35-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1c35-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b1c35-122">See Also</span></span>  
 [<span data-ttu-id="b1c35-123">Énumérations de débogage</span><span class="sxs-lookup"><span data-stu-id="b1c35-123">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
