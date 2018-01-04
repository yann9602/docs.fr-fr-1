---
title: "ICorRuntimeHost::Start, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorRuntimeHost.Start
api_location: mscoree.dll
api_type: COM
f1_keywords: ICorRuntimeHost::Start
helpviewer_keywords:
- Start method, ICorRuntimeHost interface [.NET Framework hosting]
- ICorRuntimeHost::Start method [.NET Framework hosting]
ms.assetid: c66f3ac5-6489-484a-9bed-c31b711cee01
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2d79046db904de68e5b24b2f96206bb1de2de470
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icorruntimehoststart-method"></a><span data-ttu-id="290a7-102">ICorRuntimeHost::Start, méthode</span><span class="sxs-lookup"><span data-stu-id="290a7-102">ICorRuntimeHost::Start Method</span></span>
<span data-ttu-id="290a7-103">Démarre le common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="290a7-103">Starts the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="290a7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="290a7-104">Syntax</span></span>  
  
```  
HRESULT Start ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="290a7-105">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="290a7-105">Return Value</span></span>  
  
|<span data-ttu-id="290a7-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="290a7-106">HRESULT</span></span>|<span data-ttu-id="290a7-107">Description</span><span class="sxs-lookup"><span data-stu-id="290a7-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="290a7-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="290a7-108">S_OK</span></span>|<span data-ttu-id="290a7-109">L’opération a réussi.</span><span class="sxs-lookup"><span data-stu-id="290a7-109">The operation was successful.</span></span>|  
|<span data-ttu-id="290a7-110">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="290a7-110">S_FALSE</span></span>|<span data-ttu-id="290a7-111">L’opération a échoué.</span><span class="sxs-lookup"><span data-stu-id="290a7-111">The operation failed to complete.</span></span>|  
|<span data-ttu-id="290a7-112">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="290a7-112">E_FAIL</span></span>|<span data-ttu-id="290a7-113">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="290a7-113">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="290a7-114">Si une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="290a7-114">If a method returns E_FAIL, the CLR is no longer usable in the process.</span></span> <span data-ttu-id="290a7-115">Les appels suivants à toute API d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="290a7-115">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="290a7-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="290a7-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="290a7-117">Le CLR n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="290a7-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="290a7-118">Notes</span><span class="sxs-lookup"><span data-stu-id="290a7-118">Remarks</span></span>  
 <span data-ttu-id="290a7-119">Il n’est généralement pas nécessaire d’appeler le `Start` (méthode), car le CLR démarre automatiquement dès la première demande d’exécuter du code managé.</span><span class="sxs-lookup"><span data-stu-id="290a7-119">It is typically not necessary to call the `Start` method, because the CLR starts automatically upon the first request to run managed code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="290a7-120">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="290a7-120">Requirements</span></span>  
 <span data-ttu-id="290a7-121">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="290a7-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="290a7-122">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="290a7-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="290a7-123">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="290a7-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="290a7-124">**Versions du .NET framework :** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="290a7-124">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="290a7-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="290a7-125">See Also</span></span>  
 [<span data-ttu-id="290a7-126">ICorRuntimeHost, interface</span><span class="sxs-lookup"><span data-stu-id="290a7-126">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
