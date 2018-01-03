---
title: ICLRDataTarget2, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDataTarget2
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDataTarget2
helpviewer_keywords: ICLRDataTarget2 interface [.NET Framework debugging]
ms.assetid: 94249397-861b-4294-a538-cf01466a66d3
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a8d8dc7aad35e38b2f9d3b5fb48dacbe1d22bd34
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdatatarget2-interface"></a><span data-ttu-id="7002c-102">ICLRDataTarget2, interface</span><span class="sxs-lookup"><span data-stu-id="7002c-102">ICLRDataTarget2 Interface</span></span>
<span data-ttu-id="7002c-103">Une sous-classe de [ICLRDataTarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md) qui est utilisé par la couche de services d’accès aux données pour manipuler les régions de mémoire virtuelle dans le processus cible.</span><span class="sxs-lookup"><span data-stu-id="7002c-103">A subclass of [ICLRDataTarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md) that is used by the data access services layer to manipulate virtual memory regions in the target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7002c-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="7002c-104">Methods</span></span>  
  
|<span data-ttu-id="7002c-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="7002c-105">Method</span></span>|<span data-ttu-id="7002c-106">Description</span><span class="sxs-lookup"><span data-stu-id="7002c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7002c-107">AllocVirtual, méthode</span><span class="sxs-lookup"><span data-stu-id="7002c-107">AllocVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-allocvirtual-method.md)|<span data-ttu-id="7002c-108">Alloue de la mémoire dans l’espace d’adressage du processus cible.</span><span class="sxs-lookup"><span data-stu-id="7002c-108">Allocates memory in the address space of the target process.</span></span>|  
|[<span data-ttu-id="7002c-109">FreeVirtual, méthode</span><span class="sxs-lookup"><span data-stu-id="7002c-109">FreeVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-freevirtual-method.md)|<span data-ttu-id="7002c-110">Libère la mémoire précédemment alloué dans l’espace d’adressage du processus cible.</span><span class="sxs-lookup"><span data-stu-id="7002c-110">Frees memory that was previously allocated in the address space of the target process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7002c-111">Notes</span><span class="sxs-lookup"><span data-stu-id="7002c-111">Remarks</span></span>  
 <span data-ttu-id="7002c-112">Le client API (c'est-à-dire le débogueur) doit implémenter cette interface comme il convient pour le processus cible particulier.</span><span class="sxs-lookup"><span data-stu-id="7002c-112">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="7002c-113">Par exemple, un processus actif aurait une implémentation différente de celle d'un vidage de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="7002c-113">For example, a live process would have an implementation different from that of a memory dump.</span></span> <span data-ttu-id="7002c-114">La cible ne prend peut-être pas en charge la modification de ses régions de mémoire.</span><span class="sxs-lookup"><span data-stu-id="7002c-114">The target may not support modification of its memory regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7002c-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="7002c-115">Requirements</span></span>  
 <span data-ttu-id="7002c-116">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7002c-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7002c-117">**En-tête :** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="7002c-117">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="7002c-118">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7002c-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7002c-119">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7002c-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7002c-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7002c-120">See Also</span></span>  
 [<span data-ttu-id="7002c-121">ICLRDataTarget, interface</span><span class="sxs-lookup"><span data-stu-id="7002c-121">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)  
 [<span data-ttu-id="7002c-122">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="7002c-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
