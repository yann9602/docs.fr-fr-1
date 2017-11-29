---
title: "ICLRRuntimeInfo::IsStarted, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeInfo.IsStarted
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRRuntimeInfo::IsStarted
helpviewer_keywords:
- IsStarted method [.NET Framework hosting]
- ICLRRuntimeInfo::IsStarted method [.NET Framework hosting]
ms.assetid: ef6f2662-323b-4534-aa82-6d1afb7b9309
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d6bcaf6e0d10bd935e7ba4a2bb79941be1af6950
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrruntimeinfoisstarted-method"></a><span data-ttu-id="c9db5-102">ICLRRuntimeInfo::IsStarted, méthode</span><span class="sxs-lookup"><span data-stu-id="c9db5-102">ICLRRuntimeInfo::IsStarted Method</span></span>
<span data-ttu-id="c9db5-103">Indique si le runtime a été démarré (autrement dit, si le [méthode ICLRRuntimeHost::Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) a été appelée et a réussi).</span><span class="sxs-lookup"><span data-stu-id="c9db5-103">Indicates whether the runtime has been started (that is, whether the [ICLRRuntimeHost::Start method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) has been called and has succeeded).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9db5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c9db5-104">Syntax</span></span>  
  
```  
HRESULT IsStarted(  
        [out] BOOL     *pbStarted,  
        [out] DWORD    *pdwStartupFlags);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c9db5-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c9db5-105">Parameters</span></span>  
 `pbStarted`  
 <span data-ttu-id="c9db5-106">[out] `true` si cette exécution est démarrée ; sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="c9db5-106">[out] `true` if this runtime is started; otherwise, `false`.</span></span>  
  
 `pdwStartupFlags`  
 <span data-ttu-id="c9db5-107">[out] Retourne les indicateurs utilisés pour démarrer le runtime.</span><span class="sxs-lookup"><span data-stu-id="c9db5-107">[out] Returns the flags that were used to start the runtime.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c9db5-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="c9db5-108">Return Value</span></span>  
 <span data-ttu-id="c9db5-109">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="c9db5-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="c9db5-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c9db5-110">HRESULT</span></span>|<span data-ttu-id="c9db5-111">Description</span><span class="sxs-lookup"><span data-stu-id="c9db5-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c9db5-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="c9db5-112">S_OK</span></span>|<span data-ttu-id="c9db5-113">La commande s'est correctement terminée.</span><span class="sxs-lookup"><span data-stu-id="c9db5-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="c9db5-114">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="c9db5-114">E_NOTIMPL</span></span>|<span data-ttu-id="c9db5-115">La version du common language runtime (CLR) est antérieure à la version du CLR dans le [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c9db5-115">The common language runtime (CLR) version is earlier than the CLR version in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c9db5-116">Remarques</span><span class="sxs-lookup"><span data-stu-id="c9db5-116">Remarks</span></span>  
 <span data-ttu-id="c9db5-117">Cette méthode ne fonctionne avec les versions CLR antérieures à la version du CLR dans le [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c9db5-117">This method does not work with CLR versions earlier than the CLR version in the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9db5-118">Spécifications</span><span class="sxs-lookup"><span data-stu-id="c9db5-118">Requirements</span></span>  
 <span data-ttu-id="c9db5-119">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c9db5-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9db5-120">**En-tête :** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="c9db5-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="c9db5-121">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c9db5-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c9db5-122">**Versions du .NET framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9db5-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9db5-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c9db5-123">See Also</span></span>  
 [<span data-ttu-id="c9db5-124">ICLRRuntimeInfo (Interface)</span><span class="sxs-lookup"><span data-stu-id="c9db5-124">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [<span data-ttu-id="c9db5-125">Interfaces d’hébergement</span><span class="sxs-lookup"><span data-stu-id="c9db5-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="c9db5-126">Hébergement d’applications WPF</span><span class="sxs-lookup"><span data-stu-id="c9db5-126">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
