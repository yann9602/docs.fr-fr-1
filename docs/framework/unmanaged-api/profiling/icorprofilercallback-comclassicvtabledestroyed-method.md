---
title: "ICorProfilerCallback::COMClassicVTableDestroyed, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.COMClassicVTableDestroyed
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::COMClassicVTableDestroyed
helpviewer_keywords:
- ICorProfilerCallback::COMClassicVTableDestroyed method [.NET Framework profiling]
- COMClassicVTableDestroyed method [.NET Framework profiling]
ms.assetid: 29da20ca-bf39-4356-8099-d9c3ac3423a9
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ebff8297a708b130a0d3983fd75b76c3aeaeceaf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackcomclassicvtabledestroyed-method"></a><span data-ttu-id="35a02-102">ICorProfilerCallback::COMClassicVTableDestroyed, méthode</span><span class="sxs-lookup"><span data-stu-id="35a02-102">ICorProfilerCallback::COMClassicVTableDestroyed Method</span></span>
<span data-ttu-id="35a02-103">Notifie le profileur qu’une vtable d’interopérabilité COM est détruite.</span><span class="sxs-lookup"><span data-stu-id="35a02-103">Notifies the profiler that a COM interop vtable is being destroyed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="35a02-104">Ce rappel n’est pas susceptible de se produire, car la destruction de vtables survient très proche de l’arrêt.</span><span class="sxs-lookup"><span data-stu-id="35a02-104">This callback is likely never to occur, because the destruction of vtables occurs very close to shutdown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35a02-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="35a02-105">Syntax</span></span>  
  
```  
HRESULT COMClassicVTableDestroyed(  
    [in] ClassID wrappedClassId,  
    [in] REFGUID implementedIID,  
    [in] void    *pVTable);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="35a02-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="35a02-106">Parameters</span></span>  
 `wrappedClasId`  
 <span data-ttu-id="35a02-107">[in] L’ID de la classe pour laquelle cette vtable a été créée.</span><span class="sxs-lookup"><span data-stu-id="35a02-107">[in] The ID of the class for which this vtable was created.</span></span>  
  
 `implementedIID`  
 <span data-ttu-id="35a02-108">[in] L’ID de l’interface implémentée par la classe.</span><span class="sxs-lookup"><span data-stu-id="35a02-108">[in] The ID of the interface implemented by the class.</span></span> <span data-ttu-id="35a02-109">Cette valeur peut être NULL si l’interface est uniquement interne.</span><span class="sxs-lookup"><span data-stu-id="35a02-109">This value may be NULL if the interface is internal only.</span></span>  
  
 `pVTable`  
 <span data-ttu-id="35a02-110">[in] Pointeur vers le début de la vtable.</span><span class="sxs-lookup"><span data-stu-id="35a02-110">[in] A pointer to the start of the vtable.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="35a02-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="35a02-111">Remarks</span></span>  
 <span data-ttu-id="35a02-112">Le profileur ne doit pas bloquer dans son implémentation de cette méthode, car la pile ne peut pas être dans un état qui autorise le garbage collection, et par conséquent, le garbage collection préemptif ne peut pas être activé.</span><span class="sxs-lookup"><span data-stu-id="35a02-112">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="35a02-113">Si le profileur bloque ici et le garbage collection est tenté, le runtime bloque jusqu'à ce que ce rappel retourne.</span><span class="sxs-lookup"><span data-stu-id="35a02-113">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="35a02-114">L’implémentation du profileur de cette méthode ne doit pas appeler dans du code managé ou de quelque manière qu’une allocation de mémoire managée.</span><span class="sxs-lookup"><span data-stu-id="35a02-114">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="35a02-115">Spécifications</span><span class="sxs-lookup"><span data-stu-id="35a02-115">Requirements</span></span>  
 <span data-ttu-id="35a02-116">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="35a02-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="35a02-117">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="35a02-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="35a02-118">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="35a02-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="35a02-119">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="35a02-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35a02-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="35a02-120">See Also</span></span>  
 [<span data-ttu-id="35a02-121">Interface ICorProfilerCallback</span><span class="sxs-lookup"><span data-stu-id="35a02-121">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="35a02-122">COMClassicVTableCreated (méthode)</span><span class="sxs-lookup"><span data-stu-id="35a02-122">COMClassicVTableCreated Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-comclassicvtablecreated-method.md)
