---
title: "IHostMemoryManager::VirtualFree, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostMemoryManager.VirtualFree
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostMemoryManager::VirtualFree
helpviewer_keywords:
- IHostMemoryManager::VirtualFree method [.NET Framework hosting]
- VirtualFree method [.NET Framework hosting]
ms.assetid: 1a436e89-eb28-4d15-bcf1-a072f86dbd99
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 468228101403c7ce3c123401e906e3ccbe301e28
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="ihostmemorymanagervirtualfree-method"></a><span data-ttu-id="353a1-102">IHostMemoryManager::VirtualFree, méthode</span><span class="sxs-lookup"><span data-stu-id="353a1-102">IHostMemoryManager::VirtualFree Method</span></span>
<span data-ttu-id="353a1-103">Sert de wrapper logique pour la fonction Win32 correspondante.</span><span class="sxs-lookup"><span data-stu-id="353a1-103">Serves as a logical wrapper for the corresponding Win32 function.</span></span> <span data-ttu-id="353a1-104">L’implémentation Win32 de `VirtualFree` libère, annule sa validation ou libère et invalider une région de pages au sein de l’espace d’adressage virtuel du processus appelant.</span><span class="sxs-lookup"><span data-stu-id="353a1-104">The Win32 implementation of `VirtualFree` releases, decommits, or releases and decommits a region of pages within the virtual address space of the calling process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="353a1-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="353a1-105">Syntax</span></span>  
  
```  
HRESULT VirtualFree (  
    [in] LPVOID  lpAddress,  
    [in] SIZE_T  dwSize,  
    [in] DWORD   dwFreeType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="353a1-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="353a1-106">Parameters</span></span>  
 `lpAddress`  
 <span data-ttu-id="353a1-107">[in] Pointeur vers l’adresse de base des pages de mémoire virtuelle à libérer.</span><span class="sxs-lookup"><span data-stu-id="353a1-107">[in] A pointer to the base address of the virtual memory pages to be freed.</span></span>  
  
 `dwSize`  
 <span data-ttu-id="353a1-108">[in] La taille, en octets, de la région à libérer.</span><span class="sxs-lookup"><span data-stu-id="353a1-108">[in] The size, in bytes, of the region to be freed.</span></span>  
  
 `dwFreeType`  
 <span data-ttu-id="353a1-109">[in] Le type d’opération de libération.</span><span class="sxs-lookup"><span data-stu-id="353a1-109">[in] The type of freeing operation.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="353a1-110">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="353a1-110">Return Value</span></span>  
  
|<span data-ttu-id="353a1-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="353a1-111">HRESULT</span></span>|<span data-ttu-id="353a1-112">Description</span><span class="sxs-lookup"><span data-stu-id="353a1-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="353a1-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="353a1-113">S_OK</span></span>|<span data-ttu-id="353a1-114">`VirtualFree`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="353a1-114">`VirtualFree` returned successfully.</span></span>|  
|<span data-ttu-id="353a1-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="353a1-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="353a1-116">Le common language runtime (CLR) n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="353a1-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="353a1-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="353a1-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="353a1-118">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="353a1-118">The call timed out.</span></span>|  
|<span data-ttu-id="353a1-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="353a1-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="353a1-120">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="353a1-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="353a1-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="353a1-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="353a1-122">Un événement a été annulé alors qu’un thread bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="353a1-122">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="353a1-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="353a1-123">E_FAIL</span></span>|<span data-ttu-id="353a1-124">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="353a1-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="353a1-125">Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="353a1-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="353a1-126">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="353a1-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="353a1-127">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="353a1-127">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="353a1-128">Une tentative a été effectuée pour libérer de la mémoire n’est allouée par l’hôte.</span><span class="sxs-lookup"><span data-stu-id="353a1-128">An attempt was made to free memory that was not allocated through the host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="353a1-129">Remarques</span><span class="sxs-lookup"><span data-stu-id="353a1-129">Remarks</span></span>  
 <span data-ttu-id="353a1-130">`VirtualFree`Libère des pages de mémoire virtuelle associés à la `lpAddress` paramètre via un appel précédent à la [IHostMemoryManager::VirtualAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualalloc-method.md) (fonction).</span><span class="sxs-lookup"><span data-stu-id="353a1-130">`VirtualFree` frees virtual memory pages associated with the `lpAddress` parameter through an earlier call to the [IHostMemoryManager::VirtualAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualalloc-method.md) function.</span></span> <span data-ttu-id="353a1-131">Tente de libérer de la mémoire n’est allouée par l’hôte doit retourner HOST_E_INVALIDOPERATION.</span><span class="sxs-lookup"><span data-stu-id="353a1-131">Attempts to free memory that was not allocated through the host should return HOST_E_INVALIDOPERATION.</span></span>  
  
 <span data-ttu-id="353a1-132">La sémantique est identique à celles de l’implémentation Win32 de `VirtualFree`.</span><span class="sxs-lookup"><span data-stu-id="353a1-132">The semantics are identical to those of the Win32 implementation of `VirtualFree`.</span></span> <span data-ttu-id="353a1-133">Pour plus d’informations, consultez la documentation de la plateforme Windows.</span><span class="sxs-lookup"><span data-stu-id="353a1-133">For more information, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="353a1-134">Spécifications</span><span class="sxs-lookup"><span data-stu-id="353a1-134">Requirements</span></span>  
 <span data-ttu-id="353a1-135">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="353a1-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="353a1-136">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="353a1-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="353a1-137">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="353a1-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="353a1-138">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="353a1-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="353a1-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="353a1-139">See Also</span></span>  
 [<span data-ttu-id="353a1-140">IHostMemoryManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="353a1-140">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 [<span data-ttu-id="353a1-141">IHostMalloc (Interface)</span><span class="sxs-lookup"><span data-stu-id="353a1-141">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
