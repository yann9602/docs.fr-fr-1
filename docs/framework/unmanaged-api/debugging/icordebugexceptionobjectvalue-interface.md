---
title: ICorDebugExceptionObjectValue, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugExceptionObjectValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugExceptionObjectValue
helpviewer_keywords: ICorDebugExceptionObjectValue interface [.NET Framework debugging]
ms.assetid: 43416dd5-8892-4106-9f59-f9143b19ddb4
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e6ee743a5e3e28b5d8b864f325239725ca6c0042
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugexceptionobjectvalue-interface"></a><span data-ttu-id="79671-102">ICorDebugExceptionObjectValue, interface</span><span class="sxs-lookup"><span data-stu-id="79671-102">ICorDebugExceptionObjectValue Interface</span></span>
<span data-ttu-id="79671-103">Étend l’interface « ICorDebugObjectValue » pour fournir des informations à partir d’un objet d’exception managée.</span><span class="sxs-lookup"><span data-stu-id="79671-103">Extends the "ICorDebugObjectValue" interface to provide stack trace information from a managed exception object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="79671-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="79671-104">Methods</span></span>  
  
|<span data-ttu-id="79671-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="79671-105">Method</span></span>|<span data-ttu-id="79671-106">Description</span><span class="sxs-lookup"><span data-stu-id="79671-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="79671-107">EnumerateExceptionCallStack, méthode</span><span class="sxs-lookup"><span data-stu-id="79671-107">EnumerateExceptionCallStack Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md)|<span data-ttu-id="79671-108">Obtient un énumérateur pour la pile des appels incorporée dans un objet d’exception.</span><span class="sxs-lookup"><span data-stu-id="79671-108">Gets an enumerator to the call stack embedded in an exception object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="79671-109">Notes</span><span class="sxs-lookup"><span data-stu-id="79671-109">Remarks</span></span>  
 <span data-ttu-id="79671-110">L’appel à `QueryInterface` réussira pour des objets managés qui dérivent de <xref:System.Exception?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="79671-110">The call to `QueryInterface` will succeed for managed objects that derive from <xref:System.Exception?displayProperty=nameWithType>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79671-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="79671-111">Requirements</span></span>  
 <span data-ttu-id="79671-112">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="79671-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79671-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="79671-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="79671-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="79671-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="79671-115">**Versions du .NET framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="79671-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79671-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="79671-116">See Also</span></span>  
 [<span data-ttu-id="79671-117">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="79671-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="79671-118">Débogage</span><span class="sxs-lookup"><span data-stu-id="79671-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)  
 
