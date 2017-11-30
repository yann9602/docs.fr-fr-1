---
title: "IHostTaskManager::GetStackGuarantee, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTaskManager.GetStackGuarantee
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTaskManager::GetStackGuarantee
helpviewer_keywords:
- GetStackGuarantee method [.NET Framework hosting]
- IHostTaskManager::GetStackGuarantee method [.NET Framework hosting]
ms.assetid: 8176d732-c25c-4520-811d-e3310f339947
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 691eaa2bd462af5fff0b222e991c13032ddb1af1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="ihosttaskmanagergetstackguarantee-method"></a><span data-ttu-id="09feb-102">IHostTaskManager::GetStackGuarantee, méthode</span><span class="sxs-lookup"><span data-stu-id="09feb-102">IHostTaskManager::GetStackGuarantee Method</span></span>
<span data-ttu-id="09feb-103">Obtient la quantité d’espace de pile est assuré d’être disponible après qu’une opération de pile se termine, mais avant la fermeture d’un processus.</span><span class="sxs-lookup"><span data-stu-id="09feb-103">Gets the amount of stack space that is guaranteed to be available after a stack operation completes, but before the closing of a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09feb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="09feb-104">Syntax</span></span>  
  
```  
HRESULT GetStackGuarantee(  
    [out] ULONG *pGuarantee  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="09feb-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="09feb-105">Parameters</span></span>  
 `pGuarantee`  
 <span data-ttu-id="09feb-106">[out] Pointeur vers le nombre d’octets qui sont disponibles.</span><span class="sxs-lookup"><span data-stu-id="09feb-106">[out] A pointer to the number of bytes that are available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="09feb-107">Spécifications</span><span class="sxs-lookup"><span data-stu-id="09feb-107">Requirements</span></span>  
 <span data-ttu-id="09feb-108">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="09feb-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09feb-109">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="09feb-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="09feb-110">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="09feb-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="09feb-111">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="09feb-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09feb-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="09feb-112">See Also</span></span>  
 [<span data-ttu-id="09feb-113">IHostTaskManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="09feb-113">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
