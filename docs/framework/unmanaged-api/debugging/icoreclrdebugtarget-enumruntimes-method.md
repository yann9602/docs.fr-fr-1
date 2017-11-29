---
title: "Méthode ICoreClrDebugTarget::EnumRuntimes"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICoreClrDebugTarget.EnumRuntimes
api_location: mscordbi_macx86.dll
api_type: COM
f1_keywords: ICoreClrDebugTarget::EnumRuntimes
helpviewer_keywords:
- remote debugging API [Silverlight]
- ICorClrDebugTarget::EnumRuntimes method [Silverlight debugging]
- EnumRuntimes method, ICoreClrDebugTarget interface [Silverlight debugging]
- Silverlight, remote debugging
ms.assetid: 316df866-442d-40cc-b049-45e8adcb65d1
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d28e5f3f529f72607e2ddd84789e89f82dcdaba0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icoreclrdebugtargetenumruntimes-method"></a><span data-ttu-id="79f3b-102">Méthode ICoreClrDebugTarget::EnumRuntimes</span><span class="sxs-lookup"><span data-stu-id="79f3b-102">ICoreClrDebugTarget::EnumRuntimes Method</span></span>
<span data-ttu-id="79f3b-103">Énumère les CLR (Common Language Runtime) dans le processus spécifié en cours d'exécution sur un ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="79f3b-103">Enumerates the common language runtimes (CLRs) in the specified process that is running on a remote computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79f3b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="79f3b-104">Syntax</span></span>  
  
```  
HRESULT EnumRuntimes (  
      [in] DWORD       dwInternalProcessID,  
      [out] DWORD*     pcRuntimes,  
      [out] CoreClrDebugRuntimeInfo**    ppRuntimes  
    );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="79f3b-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="79f3b-105">Parameters</span></span>  
 `dwInternalProcessID`  
 <span data-ttu-id="79f3b-106">[in] ID de processus interne du processus pour lequel vous souhaitez énumérer les runtimes.</span><span class="sxs-lookup"><span data-stu-id="79f3b-106">[in] The internal process ID of the process for which you want to enumerate runtimes.</span></span> <span data-ttu-id="79f3b-107">Il s’agit de `m_dwInternalID` correspondant [CoreClrDebugProcInfo](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md).</span><span class="sxs-lookup"><span data-stu-id="79f3b-107">This will be `m_dwInternalID` from the corresponding [CoreClrDebugProcInfo](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md).</span></span>  
  
 `pcRuntimes`  
 <span data-ttu-id="79f3b-108">[out] Nombre de runtimes retournés dans `ppRuntimes`.</span><span class="sxs-lookup"><span data-stu-id="79f3b-108">[out] The number of runtimes returned in `ppRuntimes`.</span></span> <span data-ttu-id="79f3b-109">Cette valeur peut être égale à 0 (zéro).</span><span class="sxs-lookup"><span data-stu-id="79f3b-109">This value can be 0 (zero).</span></span>  
  
 `ppRuntimes`  
 <span data-ttu-id="79f3b-110">[out] Un tableau de [CoreClrDebugRuntimeInfo](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugruntimeinfo-structure.md) des structures qui représentent les runtimes chargement dans le processus distant cible.</span><span class="sxs-lookup"><span data-stu-id="79f3b-110">[out] An array of [CoreClrDebugRuntimeInfo](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugruntimeinfo-structure.md) structures that represent the runtimes loaded in the remote target process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="79f3b-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="79f3b-111">Return Value</span></span>  
 <span data-ttu-id="79f3b-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="79f3b-112">S_OK</span></span>  
 <span data-ttu-id="79f3b-113">Opération réussie.</span><span class="sxs-lookup"><span data-stu-id="79f3b-113">Success.</span></span>  
  
 <span data-ttu-id="79f3b-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="79f3b-114">S_FALSE</span></span>  
 <span data-ttu-id="79f3b-115">`dwInternalProcessID` ne correspond à aucun processus qui s'exécute sur l'ordinateur, probablement parce que le processus a été arrêté.</span><span class="sxs-lookup"><span data-stu-id="79f3b-115">`dwInternalProcessID` does not match any process that is running on the computer, probably because the process was terminated.</span></span> <span data-ttu-id="79f3b-116">`pcRuntimes` et `ppRuntimes` sont null.</span><span class="sxs-lookup"><span data-stu-id="79f3b-116">`pcRuntimes` and `ppRuntimes` will be null.</span></span>  
  
 <span data-ttu-id="79f3b-117">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="79f3b-117">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="79f3b-118">Impossible d'allouer suffisamment de mémoire pour `ppRuntimes`.</span><span class="sxs-lookup"><span data-stu-id="79f3b-118">Unable to allocate enough memory for `ppRuntimes`.</span></span>  
  
 <span data-ttu-id="79f3b-119">E_FAIL (ou autres codes de retour E_)</span><span class="sxs-lookup"><span data-stu-id="79f3b-119">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="79f3b-120">Autres échecs.</span><span class="sxs-lookup"><span data-stu-id="79f3b-120">Other failures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="79f3b-121">Remarques</span><span class="sxs-lookup"><span data-stu-id="79f3b-121">Remarks</span></span>  
 <span data-ttu-id="79f3b-122">Pour libérer la mémoire allouée par cette méthode, appelez le [ICoreClrDebugTarget::FreeMemory](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-freememory-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="79f3b-122">To free the memory that was allocated by this method, call the [ICoreClrDebugTarget::FreeMemory](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-freememory-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79f3b-123">Spécifications</span><span class="sxs-lookup"><span data-stu-id="79f3b-123">Requirements</span></span>  
 <span data-ttu-id="79f3b-124">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="79f3b-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79f3b-125">**En-tête :** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="79f3b-125">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="79f3b-126">**Bibliothèque :** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="79f3b-126">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="79f3b-127">**Versions du .NET framework :** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="79f3b-127">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79f3b-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="79f3b-128">See Also</span></span>  
 [<span data-ttu-id="79f3b-129">ICoreClrDebugTarget (Interface)</span><span class="sxs-lookup"><span data-stu-id="79f3b-129">ICoreClrDebugTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md)
