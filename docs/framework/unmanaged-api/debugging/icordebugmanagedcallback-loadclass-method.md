---
title: "ICorDebugManagedCallback::LoadClass, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback.LoadClass
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback::LoadClass
helpviewer_keywords:
- ICorDebugManagedCallback::LoadClass method [.NET Framework debugging]
- LoadClass method [.NET Framework debugging]
ms.assetid: e58dac7b-85c3-41ca-b9aa-3a7fc9ae6680
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f3e732b418398e9c917085d22507c9304981b06a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallbackloadclass-method"></a><span data-ttu-id="8f6e3-102">ICorDebugManagedCallback::LoadClass, méthode</span><span class="sxs-lookup"><span data-stu-id="8f6e3-102">ICorDebugManagedCallback::LoadClass Method</span></span>
<span data-ttu-id="8f6e3-103">Notifie le débogueur qu’une classe a été chargée.</span><span class="sxs-lookup"><span data-stu-id="8f6e3-103">Notifies the debugger that a class has been loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f6e3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8f6e3-104">Syntax</span></span>  
  
```  
HRESULT LoadClass (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugClass     *c  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8f6e3-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8f6e3-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="8f6e3-106">[in] Pointeur vers un objet ICorDebugAppDomain qui représente le domaine d’application dans lequel la classe a été chargée.</span><span class="sxs-lookup"><span data-stu-id="8f6e3-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain into which the class has been loaded.</span></span>  
  
 `c`  
 <span data-ttu-id="8f6e3-107">[in] Pointeur vers un objet ICorDebugClass qui représente la classe.</span><span class="sxs-lookup"><span data-stu-id="8f6e3-107">[in] A pointer to an ICorDebugClass object that represents the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8f6e3-108">Notes</span><span class="sxs-lookup"><span data-stu-id="8f6e3-108">Remarks</span></span>  
 <span data-ttu-id="8f6e3-109">Ce rappel se produit uniquement lors du chargement de la classe a été activé pour le module qui contient la classe.</span><span class="sxs-lookup"><span data-stu-id="8f6e3-109">This callback occurs only if class loading has been enabled for the module that contains the class.</span></span> <span data-ttu-id="8f6e3-110">Chargement de classe est toujours activé pour les modules dynamiques.</span><span class="sxs-lookup"><span data-stu-id="8f6e3-110">Class loading is always enabled for dynamic modules.</span></span>  
  
 <span data-ttu-id="8f6e3-111">Le `LoadClass` rappel fournit un moment opportun pour lier les points d’arrêt aux classes récemment générées dans les modules dynamiques.</span><span class="sxs-lookup"><span data-stu-id="8f6e3-111">The `LoadClass` callback provides an appropriate time to bind breakpoints to newly generated classes in dynamic modules.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f6e3-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="8f6e3-112">Requirements</span></span>  
 <span data-ttu-id="8f6e3-113">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8f6e3-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f6e3-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8f6e3-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8f6e3-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8f6e3-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8f6e3-116">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f6e3-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f6e3-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8f6e3-117">See Also</span></span>  
 [<span data-ttu-id="8f6e3-118">UnloadClass, méthode</span><span class="sxs-lookup"><span data-stu-id="8f6e3-118">UnloadClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md)  
 [<span data-ttu-id="8f6e3-119">ICorDebugManagedCallback, interface</span><span class="sxs-lookup"><span data-stu-id="8f6e3-119">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
