---
title: ICLRMetadataLocator, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRMetadataLocator
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRMetadataLocator
helpviewer_keywords: ICLRMetadataLocator interface [.NET Framework debugging]
ms.assetid: 43c944f4-406a-4df6-981e-0eabb33dd5d0
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a06997c47a85ced56dc579759192f7256def4f5a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrmetadatalocator-interface"></a><span data-ttu-id="6f47d-102">ICLRMetadataLocator, interface</span><span class="sxs-lookup"><span data-stu-id="6f47d-102">ICLRMetadataLocator Interface</span></span>
<span data-ttu-id="6f47d-103">Utilisé par la couche de services d’accès aux données pour localiser les métadonnées des assemblys dans un processus cible.</span><span class="sxs-lookup"><span data-stu-id="6f47d-103">Used by the data access services layer to locate metadata of assemblies in a target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6f47d-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="6f47d-104">Methods</span></span>  
  
|<span data-ttu-id="6f47d-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="6f47d-105">Method</span></span>|<span data-ttu-id="6f47d-106">Description</span><span class="sxs-lookup"><span data-stu-id="6f47d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6f47d-107">GetMetadata, méthode</span><span class="sxs-lookup"><span data-stu-id="6f47d-107">GetMetadata Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrmetadatalocator-getmetadata-method.md)|<span data-ttu-id="6f47d-108">Récupère les métadonnées d’une image du processus cible.</span><span class="sxs-lookup"><span data-stu-id="6f47d-108">Retrieves the metadata of an image from the target process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6f47d-109">Notes</span><span class="sxs-lookup"><span data-stu-id="6f47d-109">Remarks</span></span>  
 <span data-ttu-id="6f47d-110">Le client API (c'est-à-dire le débogueur) doit implémenter cette interface comme il convient pour le processus cible particulier.</span><span class="sxs-lookup"><span data-stu-id="6f47d-110">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="6f47d-111">Par exemple, l’implémentation pour un processus actif serait différente de celui d’un vidage de mémoire.</span><span class="sxs-lookup"><span data-stu-id="6f47d-111">For example, the implementation for a live process would be different from that of a memory dump.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f47d-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="6f47d-112">Requirements</span></span>  
 <span data-ttu-id="6f47d-113">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6f47d-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f47d-114">**En-tête :** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="6f47d-114">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="6f47d-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6f47d-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6f47d-116">**.**</span><span class="sxs-lookup"><span data-stu-id="6f47d-116">**.**</span></span> <span data-ttu-id="6f47d-117">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f47d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f47d-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6f47d-118">See Also</span></span>  
 [<span data-ttu-id="6f47d-119">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="6f47d-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
