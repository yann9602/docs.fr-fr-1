---
title: Interface ICorDebugComObjectValue
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugComObjectValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugComObjectValue
helpviewer_keywords: ICorDebugComObjectValue interface [.NET Framework debugging]
ms.assetid: 505a7f6c-d92b-42b4-b539-433f5102ea9b
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8d339d3146a8a9214c3518eac6c31ed5222f9b31
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugcomobjectvalue-interface"></a><span data-ttu-id="5a926-102">Interface ICorDebugComObjectValue</span><span class="sxs-lookup"><span data-stu-id="5a926-102">ICorDebugComObjectValue Interface</span></span>
<span data-ttu-id="5a926-103">Fournit des méthodes pour récupérer les informations associées à un wrapper RCW (RCW).</span><span class="sxs-lookup"><span data-stu-id="5a926-103">Provides methods to retrieve information associated with a runtime callable wrapper (RCW).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5a926-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="5a926-104">Methods</span></span>  
  
|<span data-ttu-id="5a926-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="5a926-105">Method</span></span>|<span data-ttu-id="5a926-106">Description</span><span class="sxs-lookup"><span data-stu-id="5a926-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5a926-107">GetCachedInterfacePointers (méthode)</span><span class="sxs-lookup"><span data-stu-id="5a926-107">GetCachedInterfacePointers Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-getcachedinterfacepointers-method.md)|<span data-ttu-id="5a926-108">Obtient les pointeurs d’interface brut mis en cache sur le wrapper RCW en cours.</span><span class="sxs-lookup"><span data-stu-id="5a926-108">Gets the raw interface pointers cached on the current RCW.</span></span>|  
|[<span data-ttu-id="5a926-109">Getcachedinterfacetypes, méthode</span><span class="sxs-lookup"><span data-stu-id="5a926-109">GetCachedInterfaceTypes Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-getcachedinterfacetypes-method.md)|<span data-ttu-id="5a926-110">Fournit un énumérateur pour les types d’interfaces que l’objet actuel a été à la casse ou utilisé en tant que.</span><span class="sxs-lookup"><span data-stu-id="5a926-110">Provides an enumerator for the interface types that the current object has been cased to or used as.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5a926-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="5a926-111">Remarks</span></span>  
 <span data-ttu-id="5a926-112">Pour vérifier si une instance d’une interface « ICorDebugValue » représente un wrapper RCW, appelle un débogueur `QueryInterface` sur « ICorDebugValue » avec `IID_ICorDebugComObjectValue`.</span><span class="sxs-lookup"><span data-stu-id="5a926-112">To check whether an instance of an "ICorDebugValue" interface represents an RCW, a debugger calls `QueryInterface` on "ICorDebugValue" with `IID_ICorDebugComObjectValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a926-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="5a926-113">Requirements</span></span>  
 <span data-ttu-id="5a926-114">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5a926-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a926-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5a926-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5a926-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5a926-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5a926-117">**Versions du .NET framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a926-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a926-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5a926-118">See Also</span></span>  
 [<span data-ttu-id="5a926-119">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="5a926-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="5a926-120">Débogage</span><span class="sxs-lookup"><span data-stu-id="5a926-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
