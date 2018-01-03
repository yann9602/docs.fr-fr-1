---
title: "ICorDebugHeapValue3::GetMonitorEventWaitList, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugHeapValue3.GetMonitorEventWaitList
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugHeapValue3::GetMonitorEventWaitList
helpviewer_keywords:
- ICorDebugHeapValue3::GetMonitorEventWaitList method [.NET Framework debugging]
- GetMonitorEventWaitList method [.NET Framework debugging]
ms.assetid: 035a9035-ac66-4953-b48a-99652b42b7fe
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a4112188ff069184cab998f5bbd0fc70d1ce7dc9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugheapvalue3getmonitoreventwaitlist-method"></a><span data-ttu-id="2f596-102">ICorDebugHeapValue3::GetMonitorEventWaitList, méthode</span><span class="sxs-lookup"><span data-stu-id="2f596-102">ICorDebugHeapValue3::GetMonitorEventWaitList Method</span></span>
<span data-ttu-id="2f596-103">Fournit une liste triée de threads en attente sur l’événement qui est associé à un verrou du moniteur.</span><span class="sxs-lookup"><span data-stu-id="2f596-103">Provides an ordered list of threads that are queued on the event that is associated with a monitor lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f596-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2f596-104">Syntax</span></span>  
  
```  
HRESULT GetMonitorEventWaitList (  
    [out] ICorDebugThreadEnum **ppThreadEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2f596-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2f596-105">Parameters</span></span>  
 `ppThreadEnum`  
 <span data-ttu-id="2f596-106">[out] L’énumérateur ICorDebugThreadEnum qui fournit la liste triée de threads.</span><span class="sxs-lookup"><span data-stu-id="2f596-106">[out] The ICorDebugThreadEnum enumerator that provides the ordered list of threads.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2f596-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="2f596-107">Return Value</span></span>  
 <span data-ttu-id="2f596-108">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="2f596-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="2f596-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2f596-109">HRESULT</span></span>|<span data-ttu-id="2f596-110">Description</span><span class="sxs-lookup"><span data-stu-id="2f596-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2f596-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="2f596-111">S_OK</span></span>|<span data-ttu-id="2f596-112">The list is not empty.</span><span class="sxs-lookup"><span data-stu-id="2f596-112">The list is not empty.</span></span>|  
|<span data-ttu-id="2f596-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="2f596-113">S_FALSE</span></span>|<span data-ttu-id="2f596-114">La liste est vide.</span><span class="sxs-lookup"><span data-stu-id="2f596-114">The list is empty.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="2f596-115">Exceptions</span><span class="sxs-lookup"><span data-stu-id="2f596-115">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2f596-116">Notes</span><span class="sxs-lookup"><span data-stu-id="2f596-116">Remarks</span></span>  
 <span data-ttu-id="2f596-117">Le premier thread dans la liste est le premier thread qui est libéré par l’appel suivant à <xref:System.Threading.Monitor.Pulse%28System.Object%29?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="2f596-117">The first thread in the list is the first thread that is released by the next call to <xref:System.Threading.Monitor.Pulse%28System.Object%29?displayProperty=nameWithType>.</span></span> <span data-ttu-id="2f596-118">Le thread suivant dans la liste est publié sur l’appel suivant et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="2f596-118">The next thread in the list is released on the following call, and so on.</span></span>  
  
 <span data-ttu-id="2f596-119">Si la liste n’est pas vide, cette méthode retourne S_OK.</span><span class="sxs-lookup"><span data-stu-id="2f596-119">If the list is not empty, this method returns S_OK.</span></span> <span data-ttu-id="2f596-120">Si la liste est vide, la méthode retourne S_FALSE ; Dans ce cas, l’énumération est toujours valide, même s’il est vide.</span><span class="sxs-lookup"><span data-stu-id="2f596-120">If the list is empty, the method returns S_FALSE; in this case, the enumeration is still valid, although it is empty.</span></span>  
  
 <span data-ttu-id="2f596-121">Dans les deux cas, l’interface d’énumération est utilisable uniquement pour la durée de l’état synchronisé actuel.</span><span class="sxs-lookup"><span data-stu-id="2f596-121">In either case, the enumeration interface is usable only for the duration of the current synchronized state.</span></span> <span data-ttu-id="2f596-122">Toutefois, les interfaces du thread distribuées à partir de celle-ci sont valides jusqu'à ce que le thread se ferme.</span><span class="sxs-lookup"><span data-stu-id="2f596-122">However, the thread's interfaces dispensed from it are valid until the thread exits.</span></span>  
  
 <span data-ttu-id="2f596-123">Si `ppThreadEnum` n’est pas un pointeur valid, le résultat est indéfini.</span><span class="sxs-lookup"><span data-stu-id="2f596-123">If `ppThreadEnum` is not a valid pointer, the result is undefined.</span></span>  
  
 <span data-ttu-id="2f596-124">Si une erreur se produit et il ne peut pas déterminer qui, le cas échéant, les threads sont en attente pour l’analyse, la méthode retourne un HRESULT qui indique un échec.</span><span class="sxs-lookup"><span data-stu-id="2f596-124">If an error occurs such that it cannot be determined which, if any, threads are waiting for the monitor, the method returns an HRESULT that indicates failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f596-125">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="2f596-125">Requirements</span></span>  
 <span data-ttu-id="2f596-126">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2f596-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f596-127">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2f596-127">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2f596-128">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2f596-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2f596-129">**Versions du .NET framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f596-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f596-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2f596-130">See Also</span></span>  
 [<span data-ttu-id="2f596-131">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="2f596-131">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="2f596-132">Débogage</span><span class="sxs-lookup"><span data-stu-id="2f596-132">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
