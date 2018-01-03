---
title: ICorDebugAppDomainEnum Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAppDomainEnum
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugAppDomainEnum
helpviewer_keywords: ICorDebugAppDomainEnum interface [.NET Framework debugging]
ms.assetid: e9226e6e-ca2c-428e-bb38-0c099210f507
topic_type: apiref
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e5d3d11e3897ff56ffcd475eb363405651578c1c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugappdomainenum-interface1"></a><span data-ttu-id="09ace-102">ICorDebugAppDomainEnum Interface1</span><span class="sxs-lookup"><span data-stu-id="09ace-102">ICorDebugAppDomainEnum Interface1</span></span>
<span data-ttu-id="09ace-103">Fournit la `Next` (méthode), qui retourne un nombre spécifié de `ICorDebugAppDomainEnum` en commençant à l’emplacement suivant dans l’énumération des valeurs.</span><span class="sxs-lookup"><span data-stu-id="09ace-103">Provides the `Next` method, which returns a specified number of `ICorDebugAppDomainEnum` values starting at the next location in the enumeration.</span></span> <span data-ttu-id="09ace-104">Cette interface est une sous-classe de « ICorDebugEnum ».</span><span class="sxs-lookup"><span data-stu-id="09ace-104">This interface is a subclass of "ICorDebugEnum".</span></span>  
  
## <a name="methods"></a><span data-ttu-id="09ace-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="09ace-105">Methods</span></span>  
  
|<span data-ttu-id="09ace-106">Méthode</span><span class="sxs-lookup"><span data-stu-id="09ace-106">Method</span></span>|<span data-ttu-id="09ace-107">Description</span><span class="sxs-lookup"><span data-stu-id="09ace-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="09ace-108">Next, méthode</span><span class="sxs-lookup"><span data-stu-id="09ace-108">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomainenum-next-method.md)|<span data-ttu-id="09ace-109">Obtient le nombre spécifié de domaines d’application à partir de la collection, en commençant à la position actuelle du curseur.</span><span class="sxs-lookup"><span data-stu-id="09ace-109">Gets the specified number of application domains from the collection, starting at the current cursor position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="09ace-110">Notes</span><span class="sxs-lookup"><span data-stu-id="09ace-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="09ace-111">Cette interface ne prend pas en charge l'appel à distance, que ce soit entre ordinateurs ou entre processus.</span><span class="sxs-lookup"><span data-stu-id="09ace-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="09ace-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="09ace-112">Requirements</span></span>  
 <span data-ttu-id="09ace-113">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="09ace-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09ace-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="09ace-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="09ace-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="09ace-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="09ace-116">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="09ace-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09ace-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="09ace-117">See Also</span></span>  
 [<span data-ttu-id="09ace-118">ICorDebug, interface</span><span class="sxs-lookup"><span data-stu-id="09ace-118">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
 [<span data-ttu-id="09ace-119">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="09ace-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
