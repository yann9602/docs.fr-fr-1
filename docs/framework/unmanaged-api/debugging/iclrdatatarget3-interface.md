---
title: ICLRDataTarget3, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDataTarget3
api_location: mscordbi.dll
api_type: COM
ms.assetid: d2711bdf-64b3-404c-a0c3-01ba4907f703
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 16e2d2aa1a2626f4124e1b43ff85abcdd17f6990
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrdatatarget3-interface"></a><span data-ttu-id="0411b-102">ICLRDataTarget3, interface</span><span class="sxs-lookup"><span data-stu-id="0411b-102">ICLRDataTarget3 Interface</span></span>
<span data-ttu-id="0411b-103">Une sous-classe de [ICLRDataTarget2](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md) qui fournit l’accès aux informations sur l’exception.</span><span class="sxs-lookup"><span data-stu-id="0411b-103">A subclass of [ICLRDataTarget2](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md) that provides access to exception information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0411b-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="0411b-104">Methods</span></span>  
  
|<span data-ttu-id="0411b-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="0411b-105">Method</span></span>|<span data-ttu-id="0411b-106">Description</span><span class="sxs-lookup"><span data-stu-id="0411b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0411b-107">Getexceptionrecord, méthode</span><span class="sxs-lookup"><span data-stu-id="0411b-107">GetExceptionRecord Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionrecord-method.md)|<span data-ttu-id="0411b-108">Appelé par les services d'accès aux données du Common Langage Runtime (CLR) pour récupérer l'enregistrement d'exception associé au processus cible.</span><span class="sxs-lookup"><span data-stu-id="0411b-108">Called by the common language runtime (CLR) data access services to retrieve the exception record associated with the target process.</span></span>|  
|[<span data-ttu-id="0411b-109">Getexceptioncontextrecord, méthode</span><span class="sxs-lookup"><span data-stu-id="0411b-109">GetExceptionContextRecord Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptioncontextrecord-method.md)|<span data-ttu-id="0411b-110">Appelé par les services d'accès aux données CLR pour récupérer l'enregistrement de contexte associé au processus cible.</span><span class="sxs-lookup"><span data-stu-id="0411b-110">Called by the CLR data access services to retrieve the context record associated with the target process.</span></span>|  
|[<span data-ttu-id="0411b-111">Getexceptionthreadid, méthode</span><span class="sxs-lookup"><span data-stu-id="0411b-111">GetExceptionThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionthreadid-method.md)|<span data-ttu-id="0411b-112">Appelée par les services d'accès aux données de CLR (Common Language Runtime) pour obtenir l'ID du thread qui a levé l'exception.</span><span class="sxs-lookup"><span data-stu-id="0411b-112">Called by the CLR data access services to get the ID of the thread that threw the exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0411b-113">Remarques</span><span class="sxs-lookup"><span data-stu-id="0411b-113">Remarks</span></span>  
 <span data-ttu-id="0411b-114">Le client API (c'est-à-dire le débogueur) doit implémenter cette interface comme il convient pour le processus cible particulier.</span><span class="sxs-lookup"><span data-stu-id="0411b-114">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="0411b-115">Par exemple, un processus actif aurait une implémentation différente de celle d'un vidage de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="0411b-115">For example, a live process would have an implementation different from that of a memory dump.</span></span> <span data-ttu-id="0411b-116">La cible ne prend peut-être pas en charge la modification de ses régions de mémoire.</span><span class="sxs-lookup"><span data-stu-id="0411b-116">The target may not support modification of its memory regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0411b-117">Spécifications</span><span class="sxs-lookup"><span data-stu-id="0411b-117">Requirements</span></span>  
 <span data-ttu-id="0411b-118">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0411b-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0411b-119">**En-tête :** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="0411b-119">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="0411b-120">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0411b-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0411b-121">**Versions du .NET framework :**[!INCLUDE[v451_update](../../../../includes/v451-update-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0411b-121">**.NET Framework Versions:** [!INCLUDE[v451_update](../../../../includes/v451-update-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0411b-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0411b-122">See Also</span></span>  
 [<span data-ttu-id="0411b-123">ICLRDataTarget (Interface)</span><span class="sxs-lookup"><span data-stu-id="0411b-123">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)  
 [<span data-ttu-id="0411b-124">ICLRDataTarget2 (Interface)</span><span class="sxs-lookup"><span data-stu-id="0411b-124">ICLRDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)  
 [<span data-ttu-id="0411b-125">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="0411b-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
