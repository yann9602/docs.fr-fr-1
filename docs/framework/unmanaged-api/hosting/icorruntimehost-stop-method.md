---
title: "ICorRuntimeHost::Stop, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorRuntimeHost.Stop
api_location: mscoree.dll
api_type: COM
f1_keywords: ICorRuntimeHost::Stop
helpviewer_keywords:
- Stop method, ICorRuntimeHost interface [.NET Framework hosting]
- ICorRuntimeHost::Stop method [.NET Framework hosting]
ms.assetid: 46a0d450-b516-4bef-8b71-8d3bf265cbed
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f9e27bd5d05b10f8db24a1119e4ed3717ce044e0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icorruntimehoststop-method"></a><span data-ttu-id="a3a77-102">ICorRuntimeHost::Stop, méthode</span><span class="sxs-lookup"><span data-stu-id="a3a77-102">ICorRuntimeHost::Stop Method</span></span>
<span data-ttu-id="a3a77-103">Arrête l’exécution de code dans le runtime pour le processus actuel.</span><span class="sxs-lookup"><span data-stu-id="a3a77-103">Stops the execution of code in the runtime for the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3a77-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a3a77-104">Syntax</span></span>  
  
```  
HRESULT Stop ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="a3a77-105">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="a3a77-105">Return Value</span></span>  
  
|<span data-ttu-id="a3a77-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a3a77-106">HRESULT</span></span>|<span data-ttu-id="a3a77-107">Description</span><span class="sxs-lookup"><span data-stu-id="a3a77-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a3a77-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="a3a77-108">S_OK</span></span>|<span data-ttu-id="a3a77-109">L’opération a réussi.</span><span class="sxs-lookup"><span data-stu-id="a3a77-109">The operation was successful.</span></span>|  
|<span data-ttu-id="a3a77-110">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="a3a77-110">S_FALSE</span></span>|<span data-ttu-id="a3a77-111">L’opération a échoué.</span><span class="sxs-lookup"><span data-stu-id="a3a77-111">The operation failed to complete.</span></span>|  
|<span data-ttu-id="a3a77-112">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a3a77-112">E_FAIL</span></span>|<span data-ttu-id="a3a77-113">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="a3a77-113">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="a3a77-114">Si une méthode retourne E_FAIL, le common language runtime (CLR) n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="a3a77-114">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="a3a77-115">Les appels suivants à toute API d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a3a77-115">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="a3a77-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a3a77-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a3a77-117">Le CLR n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="a3a77-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a3a77-118">Notes</span><span class="sxs-lookup"><span data-stu-id="a3a77-118">Remarks</span></span>  
 <span data-ttu-id="a3a77-119">Il est généralement pas nécessaire d’appeler le `Stop` (méthode), car le code s’arrête l’exécution lorsque le processus s’arrête.</span><span class="sxs-lookup"><span data-stu-id="a3a77-119">It is typically unnecessary to call the `Stop` method, because the code stops executing when the process exits.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a3a77-120">Après un appel à `Stop`, le CLR ne peut pas être réinitialisé dans le même processus.</span><span class="sxs-lookup"><span data-stu-id="a3a77-120">After a call to `Stop`, the CLR cannot be reinitialized into the same process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3a77-121">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a3a77-121">Requirements</span></span>  
 <span data-ttu-id="a3a77-122">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a3a77-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3a77-123">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a3a77-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a3a77-124">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a3a77-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a3a77-125">**Versions du .NET framework :** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="a3a77-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3a77-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a3a77-126">See Also</span></span>  
 [<span data-ttu-id="a3a77-127">ICorRuntimeHost, interface</span><span class="sxs-lookup"><span data-stu-id="a3a77-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
