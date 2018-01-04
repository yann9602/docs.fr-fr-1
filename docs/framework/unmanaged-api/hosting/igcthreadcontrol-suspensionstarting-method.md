---
title: "IGCThreadControl::SuspensionStarting, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IGCThreadControl.SuspensionStarting
api_location: mscoree.dll
api_type: COM
f1_keywords: SuspensionStarting
helpviewer_keywords:
- IGCThreadControl::SuspensionStarting method [.NET Framework hosting]
- SuspensionStarting method, IGCThreadControl interface [.NET Framework hosting]
ms.assetid: 0af312af-98e9-415e-b182-42e80a1aee51
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6da39ec675cafcd51a5d748d4cbe8f9fd376eff8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="igcthreadcontrolsuspensionstarting-method"></a><span data-ttu-id="c1456-102">IGCThreadControl::SuspensionStarting, méthode</span><span class="sxs-lookup"><span data-stu-id="c1456-102">IGCThreadControl::SuspensionStarting Method</span></span>
<span data-ttu-id="c1456-103">Avertit l’hôte que le runtime débute une suspension du thread pour un garbage collection ou une suspension.</span><span class="sxs-lookup"><span data-stu-id="c1456-103">Notifies the host that the runtime is beginning a thread suspension for a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1456-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c1456-104">Syntax</span></span>  
  
```  
HRESULT SuspensionStarting ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="c1456-105">Notes</span><span class="sxs-lookup"><span data-stu-id="c1456-105">Remarks</span></span>  
 <span data-ttu-id="c1456-106">Ne replanifiez pas de threads pendant le `SuspensionStarting` rappel.</span><span class="sxs-lookup"><span data-stu-id="c1456-106">Do not reschedule any threads during the `SuspensionStarting` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1456-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c1456-107">Requirements</span></span>  
 <span data-ttu-id="c1456-108">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c1456-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1456-109">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c1456-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c1456-110">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c1456-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c1456-111">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c1456-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1456-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c1456-112">See Also</span></span>  
 [<span data-ttu-id="c1456-113">IGCThreadControl, interface</span><span class="sxs-lookup"><span data-stu-id="c1456-113">IGCThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)
