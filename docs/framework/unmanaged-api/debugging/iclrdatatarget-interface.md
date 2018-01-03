---
title: ICLRDataTarget, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDataTarget
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDataTarget
helpviewer_keywords: ICLRDataTarget interface [.NET Framework debugging]
ms.assetid: e2f05155-9bef-4e11-b703-7f05890665ca
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 73966ffe89f0e84d5a516f20962472d900332faa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdatatarget-interface"></a><span data-ttu-id="1da6b-102">ICLRDataTarget, interface</span><span class="sxs-lookup"><span data-stu-id="1da6b-102">ICLRDataTarget Interface</span></span>
<span data-ttu-id="1da6b-103">Fournit des méthodes pour l’interaction avec un élément cible du common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="1da6b-103">Provides methods for interaction with a target item of the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1da6b-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="1da6b-104">Methods</span></span>  
  
|<span data-ttu-id="1da6b-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="1da6b-105">Method</span></span>|<span data-ttu-id="1da6b-106">Description</span><span class="sxs-lookup"><span data-stu-id="1da6b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1da6b-107">GetCurrentThreadID, méthode</span><span class="sxs-lookup"><span data-stu-id="1da6b-107">GetCurrentThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getcurrentthreadid-method.md)|<span data-ttu-id="1da6b-108">Obtient l’identificateur de système d’exploitation pour le thread actuel.</span><span class="sxs-lookup"><span data-stu-id="1da6b-108">Gets the operating system identifier for the current thread.</span></span>|  
|[<span data-ttu-id="1da6b-109">GetImageBase, méthode</span><span class="sxs-lookup"><span data-stu-id="1da6b-109">GetImageBase Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getimagebase-method.md)|<span data-ttu-id="1da6b-110">Obtient l’adresse mémoire de base pour l’image spécifiée.</span><span class="sxs-lookup"><span data-stu-id="1da6b-110">Gets the base memory address for the specified image.</span></span>|  
|[<span data-ttu-id="1da6b-111">GetMachineType, méthode</span><span class="sxs-lookup"><span data-stu-id="1da6b-111">GetMachineType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getmachinetype-method.md)|<span data-ttu-id="1da6b-112">Obtient un identificateur pour le type de jeu d’instructions qui utilise le processus cible.</span><span class="sxs-lookup"><span data-stu-id="1da6b-112">Gets an identifier for the kind of instruction set that the target process is using.</span></span>|  
|[<span data-ttu-id="1da6b-113">GetPointerSize, méthode</span><span class="sxs-lookup"><span data-stu-id="1da6b-113">GetPointerSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getpointersize-method.md)|<span data-ttu-id="1da6b-114">Obtient la taille, en octets, d’un pointeur vers la cible actuelle.</span><span class="sxs-lookup"><span data-stu-id="1da6b-114">Gets the size, in bytes, of a pointer to the current target.</span></span>|  
|[<span data-ttu-id="1da6b-115">GetThreadContext, méthode</span><span class="sxs-lookup"><span data-stu-id="1da6b-115">GetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getthreadcontext-method.md)|<span data-ttu-id="1da6b-116">Obtient un pointeur vers le contexte du thread avec l’identificateur spécifié.</span><span class="sxs-lookup"><span data-stu-id="1da6b-116">Gets a pointer to the context of the thread with the specified identifier.</span></span>|  
|[<span data-ttu-id="1da6b-117">GetTLSValue, méthode</span><span class="sxs-lookup"><span data-stu-id="1da6b-117">GetTLSValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-gettlsvalue-method.md)|<span data-ttu-id="1da6b-118">Obtient une valeur dans le stockage local des threads (TLS) à l’index spécifié pour le thread spécifié.</span><span class="sxs-lookup"><span data-stu-id="1da6b-118">Gets a value in thread local storage (TLS) at the specified index for the specified thread.</span></span>|  
|[<span data-ttu-id="1da6b-119">ReadVirtual, méthode</span><span class="sxs-lookup"><span data-stu-id="1da6b-119">ReadVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-readvirtual-method.md)|<span data-ttu-id="1da6b-120">Lit les données à partir de l’adresse de mémoire virtuelle spécifiée dans la mémoire tampon spécifiée.</span><span class="sxs-lookup"><span data-stu-id="1da6b-120">Reads data from the specified virtual memory address into the specified buffer.</span></span>|  
|[<span data-ttu-id="1da6b-121">Request, méthode</span><span class="sxs-lookup"><span data-stu-id="1da6b-121">Request Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-request-method.md)|<span data-ttu-id="1da6b-122">Appelé par les services d’accès aux données du common language runtime (CLR) pour demander une opération, tel que défini par l’implémentation.</span><span class="sxs-lookup"><span data-stu-id="1da6b-122">Called by the common language runtime (CLR) data access services to request an operation, as defined by the implementation.</span></span>|  
|[<span data-ttu-id="1da6b-123">SetThreadContext, méthode</span><span class="sxs-lookup"><span data-stu-id="1da6b-123">SetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-setthreadcontext-method.md)|<span data-ttu-id="1da6b-124">Définit le contexte actuel du thread spécifié dans le processus cible.</span><span class="sxs-lookup"><span data-stu-id="1da6b-124">Sets the current context of the specified thread in the target process.</span></span>|  
|[<span data-ttu-id="1da6b-125">SetTLSValue, méthode</span><span class="sxs-lookup"><span data-stu-id="1da6b-125">SetTLSValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-settlsvalue-method.md)|<span data-ttu-id="1da6b-126">Définit une valeur dans le stockage local des threads (TLS) du thread spécifié dans le processus cible.</span><span class="sxs-lookup"><span data-stu-id="1da6b-126">Sets a value in the thread local storage (TLS) of the specified thread in the target process.</span></span>|  
|[<span data-ttu-id="1da6b-127">WriteVirtual, méthode</span><span class="sxs-lookup"><span data-stu-id="1da6b-127">WriteVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-writevirtual-method.md)|<span data-ttu-id="1da6b-128">Écrit des données à partir de la mémoire tampon spécifiée à l’adresse de mémoire virtuelle spécifiée.</span><span class="sxs-lookup"><span data-stu-id="1da6b-128">Writes data from the specified buffer to the specified virtual memory address.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1da6b-129">Notes</span><span class="sxs-lookup"><span data-stu-id="1da6b-129">Remarks</span></span>  
 <span data-ttu-id="1da6b-130">Le client API (c'est-à-dire le débogueur) doit implémenter cette interface comme il convient pour l’élément cible particulier.</span><span class="sxs-lookup"><span data-stu-id="1da6b-130">The API client (that is, the debugger) must implement this interface as appropriate for the particular target item.</span></span> <span data-ttu-id="1da6b-131">Par exemple, un processus actif aurait une implémentation différente de celle d'un vidage de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="1da6b-131">For example, a live process would have an implementation different from that of a memory dump.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1da6b-132">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="1da6b-132">Requirements</span></span>  
 <span data-ttu-id="1da6b-133">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1da6b-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1da6b-134">**En-tête :** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="1da6b-134">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="1da6b-135">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1da6b-135">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1da6b-136">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1da6b-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1da6b-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1da6b-137">See Also</span></span>  
 [<span data-ttu-id="1da6b-138">ICLRDataTarget2, interface</span><span class="sxs-lookup"><span data-stu-id="1da6b-138">ICLRDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)  
 [<span data-ttu-id="1da6b-139">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="1da6b-139">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
