---
title: "IHostMemoryManager::NeedsVirtualAddressSpace, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostMemoryManager.NeedsVirtualAddressSpace
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostMemoryManager::NeedsVirtualAddressSpace
helpviewer_keywords:
- IHostMemoryManager::NeedsVirtualAddressSpace method [.NET Framework hosting]
- NeedsVirtualAddressSpace method [.NET Framework hosting]
ms.assetid: 71f0eab5-0170-46f8-9f88-1df5abdeb34a
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 62ceb9e5b4d5843b8e2adad344b3ffb662ab3aff
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="ihostmemorymanagerneedsvirtualaddressspace-method"></a><span data-ttu-id="dc398-102">IHostMemoryManager::NeedsVirtualAddressSpace, méthode</span><span class="sxs-lookup"><span data-stu-id="dc398-102">IHostMemoryManager::NeedsVirtualAddressSpace Method</span></span>
<span data-ttu-id="dc398-103">Avertit l’hôte que le common language runtime (CLR) va tenter d’utiliser la mémoire spécifiée.</span><span class="sxs-lookup"><span data-stu-id="dc398-103">Notifies the host that the common language runtime (CLR) is going to attempt to use the specified memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc398-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dc398-104">Syntax</span></span>  
  
```  
HRESULT NeedsVirtualAddressSpace (  
    [in] LPVOID  startAddress,  
    [in] SIZE_T  size  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dc398-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="dc398-105">Parameters</span></span>  
 `startAddress`  
 <span data-ttu-id="dc398-106">[in] Adresse de départ de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="dc398-106">[in] The starting address of the memory.</span></span>  
  
 `size`  
 <span data-ttu-id="dc398-107">[in] La taille, en octets, de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="dc398-107">[in] The size, in bytes, of the memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dc398-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="dc398-108">Remarks</span></span>  
 <span data-ttu-id="dc398-109">Le `NeedsVirtualAddressSpace` méthode est une méthode de rappel et doit être implémentée par le writer de l’application d’hébergement.</span><span class="sxs-lookup"><span data-stu-id="dc398-109">The `NeedsVirtualAddressSpace` method is a callback method and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="dc398-110">Elle est appelée par le CLR.</span><span class="sxs-lookup"><span data-stu-id="dc398-110">It is called by the CLR.</span></span>  
  
 <span data-ttu-id="dc398-111">Si l’hôte ne souhaite pas que le CLR à utiliser la mémoire spécifiée, elle peut retourner un HRESULT E_OUTOFMEMORY.</span><span class="sxs-lookup"><span data-stu-id="dc398-111">If the host does not want the CLR to use the specified memory, it may return an E_OUTOFMEMORY HRESULT.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc398-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="dc398-112">Requirements</span></span>  
 <span data-ttu-id="dc398-113">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dc398-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc398-114">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="dc398-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dc398-115">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="dc398-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dc398-116">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc398-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc398-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dc398-117">See Also</span></span>  
 [<span data-ttu-id="dc398-118">IHostMemoryManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="dc398-118">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
