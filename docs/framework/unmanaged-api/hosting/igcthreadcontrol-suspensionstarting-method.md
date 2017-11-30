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
ms.openlocfilehash: d9d5f403c2880d0079a89c6de5c2ad9aa4f8d9fa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="igcthreadcontrolsuspensionstarting-method"></a><span data-ttu-id="c7cb1-102">IGCThreadControl::SuspensionStarting, méthode</span><span class="sxs-lookup"><span data-stu-id="c7cb1-102">IGCThreadControl::SuspensionStarting Method</span></span>
<span data-ttu-id="c7cb1-103">Avertit l’hôte que le runtime débute une suspension du thread pour un garbage collection ou une suspension.</span><span class="sxs-lookup"><span data-stu-id="c7cb1-103">Notifies the host that the runtime is beginning a thread suspension for a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7cb1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c7cb1-104">Syntax</span></span>  
  
```  
HRESULT SuspensionStarting ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="c7cb1-105">Remarques</span><span class="sxs-lookup"><span data-stu-id="c7cb1-105">Remarks</span></span>  
 <span data-ttu-id="c7cb1-106">Ne replanifiez pas de threads pendant le `SuspensionStarting` rappel.</span><span class="sxs-lookup"><span data-stu-id="c7cb1-106">Do not reschedule any threads during the `SuspensionStarting` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7cb1-107">Spécifications</span><span class="sxs-lookup"><span data-stu-id="c7cb1-107">Requirements</span></span>  
 <span data-ttu-id="c7cb1-108">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7cb1-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7cb1-109">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c7cb1-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c7cb1-110">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c7cb1-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c7cb1-111">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7cb1-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7cb1-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c7cb1-112">See Also</span></span>  
 [<span data-ttu-id="c7cb1-113">IGCThreadControl (Interface)</span><span class="sxs-lookup"><span data-stu-id="c7cb1-113">IGCThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)
