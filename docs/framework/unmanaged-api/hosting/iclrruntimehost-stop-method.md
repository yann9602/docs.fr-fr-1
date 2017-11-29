---
title: "ICLRRuntimeHost::Stop, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeHost.Stop
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRRuntimeHost::Stop
helpviewer_keywords:
- ICLRRuntimeHost::Stop method [.NET Framework hosting]
- Stop method, ICLRRuntimeHost interface [.NET Framework hosting]
ms.assetid: b8fd7daf-8f8d-4ad7-92ae-019db244cec1
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3798c4fc451b78257373c0ac47a5e7e7c27dd048
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="iclrruntimehoststop-method"></a><span data-ttu-id="9abda-102">ICLRRuntimeHost::Stop, méthode</span><span class="sxs-lookup"><span data-stu-id="9abda-102">ICLRRuntimeHost::Stop Method</span></span>
<span data-ttu-id="9abda-103">Arrête l’exécution du code par le common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="9abda-103">Stops the execution of code by the common language runtime (CLR).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9abda-104">Cette méthode ne pas libérer les ressources à l’ordinateur hôte, décharger des domaines d’application ou détruire des threads.</span><span class="sxs-lookup"><span data-stu-id="9abda-104">This method does not release resources to the host, unload application domains, or destroy threads.</span></span> <span data-ttu-id="9abda-105">Vous devez terminer le processus pour libérer ces ressources.</span><span class="sxs-lookup"><span data-stu-id="9abda-105">You must terminate the process to release these resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9abda-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9abda-106">Syntax</span></span>  
  
```  
HRESULT Stop();  
```  
  
## <a name="return-value"></a><span data-ttu-id="9abda-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="9abda-107">Return Value</span></span>  
  
|<span data-ttu-id="9abda-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9abda-108">HRESULT</span></span>|<span data-ttu-id="9abda-109">Description</span><span class="sxs-lookup"><span data-stu-id="9abda-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9abda-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="9abda-110">S_OK</span></span>|<span data-ttu-id="9abda-111">`Stop`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="9abda-111">`Stop` returned successfully.</span></span>|  
|<span data-ttu-id="9abda-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9abda-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9abda-113">Le CLR n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="9abda-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9abda-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9abda-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9abda-115">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="9abda-115">The call timed out.</span></span>|  
|<span data-ttu-id="9abda-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9abda-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9abda-117">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="9abda-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9abda-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9abda-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9abda-119">Un événement a été annulé alors qu’un thread bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="9abda-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9abda-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9abda-120">E_FAIL</span></span>|<span data-ttu-id="9abda-121">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="9abda-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9abda-122">Si une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="9abda-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9abda-123">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="9abda-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9abda-124">Spécifications</span><span class="sxs-lookup"><span data-stu-id="9abda-124">Requirements</span></span>  
 <span data-ttu-id="9abda-125">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9abda-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9abda-126">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9abda-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9abda-127">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9abda-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9abda-128">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9abda-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9abda-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9abda-129">See Also</span></span>  
 [<span data-ttu-id="9abda-130">ICLRRuntimeHost (Interface)</span><span class="sxs-lookup"><span data-stu-id="9abda-130">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
