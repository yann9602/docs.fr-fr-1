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
ms.workload: dotnet
ms.openlocfilehash: 991470ca0df3e0cf0470a8c40d3e8e4c40d96026
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrruntimeinfoisstarted-method"></a><span data-ttu-id="df1eb-102">ICLRRuntimeInfo::IsStarted, méthode</span><span class="sxs-lookup"><span data-stu-id="df1eb-102">ICLRRuntimeInfo::IsStarted Method</span></span>
<span data-ttu-id="df1eb-103">Indique si le runtime a été démarré (autrement dit, si le [méthode ICLRRuntimeHost::Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) a été appelée et a réussi).</span><span class="sxs-lookup"><span data-stu-id="df1eb-103">Indicates whether the runtime has been started (that is, whether the [ICLRRuntimeHost::Start method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) has been called and has succeeded).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df1eb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="df1eb-104">Syntax</span></span>  
  
```  
HRESULT IsStarted(  
        [out] BOOL     *pbStarted,  
        [out] DWORD    *pdwStartupFlags);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="df1eb-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="df1eb-105">Parameters</span></span>  
 `pbStarted`  
 <span data-ttu-id="df1eb-106">[out] `true` si cette exécution est démarrée ; sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="df1eb-106">[out] `true` if this runtime is started; otherwise, `false`.</span></span>  
  
 `pdwStartupFlags`  
 <span data-ttu-id="df1eb-107">[out] Retourne les indicateurs utilisés pour démarrer le runtime.</span><span class="sxs-lookup"><span data-stu-id="df1eb-107">[out] Returns the flags that were used to start the runtime.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="df1eb-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="df1eb-108">Return Value</span></span>  
 <span data-ttu-id="df1eb-109">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="df1eb-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="df1eb-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="df1eb-110">HRESULT</span></span>|<span data-ttu-id="df1eb-111">Description</span><span class="sxs-lookup"><span data-stu-id="df1eb-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="df1eb-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="df1eb-112">S_OK</span></span>|<span data-ttu-id="df1eb-113">La commande s'est correctement terminée.</span><span class="sxs-lookup"><span data-stu-id="df1eb-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="df1eb-114">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="df1eb-114">E_NOTIMPL</span></span>|<span data-ttu-id="df1eb-115">La version du common language runtime (CLR) est antérieure à la version du CLR dans le [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="df1eb-115">The common language runtime (CLR) version is earlier than the CLR version in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="df1eb-116">Notes</span><span class="sxs-lookup"><span data-stu-id="df1eb-116">Remarks</span></span>  
 <span data-ttu-id="df1eb-117">Cette méthode ne fonctionne avec les versions CLR antérieures à la version du CLR dans le [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="df1eb-117">This method does not work with CLR versions earlier than the CLR version in the [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df1eb-118">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="df1eb-118">Requirements</span></span>  
 <span data-ttu-id="df1eb-119">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="df1eb-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df1eb-120">**En-tête :** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="df1eb-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="df1eb-121">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="df1eb-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="df1eb-122">**Versions du .NET framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df1eb-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df1eb-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="df1eb-123">See Also</span></span>  
 [<span data-ttu-id="df1eb-124">ICLRRuntimeInfo, interface</span><span class="sxs-lookup"><span data-stu-id="df1eb-124">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [<span data-ttu-id="df1eb-125">Interfaces d’hébergement</span><span class="sxs-lookup"><span data-stu-id="df1eb-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="df1eb-126">Hébergement d’applications WPF</span><span class="sxs-lookup"><span data-stu-id="df1eb-126">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
