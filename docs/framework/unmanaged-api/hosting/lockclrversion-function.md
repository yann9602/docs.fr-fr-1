---
title: LockClrVersion, fonction
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: LockClrVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type: DLLExport
f1_keywords: LockClrVersion
helpviewer_keywords: LockClrVersion function [.NET Framework hosting]
ms.assetid: 1318ee37-c43b-40eb-bbe8-88fc46453d74
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: be41ae47f78a41e2f2be10a1e38d938dde9a4701
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="lockclrversion-function"></a><span data-ttu-id="e3173-102">LockClrVersion, fonction</span><span class="sxs-lookup"><span data-stu-id="e3173-102">LockClrVersion Function</span></span>
<span data-ttu-id="e3173-103">Permet à l’hôte déterminer quelle version du common language runtime (CLR) sera utilisée au sein du processus avant d’initialiser le CLR explicitement.</span><span class="sxs-lookup"><span data-stu-id="e3173-103">Allows the host to determine which version of the common language runtime (CLR) will be used within the process before explicitly initializing the CLR.</span></span>  
  
 <span data-ttu-id="e3173-104">Cette fonction est déconseillée dans le [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e3173-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3173-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e3173-105">Syntax</span></span>  
  
```  
HRESULT LockClrVersion (  
    [in] FLockClrVersionCallback   hostCallback,  
    [in] FLockClrVersionCallback  *pBeginHostSetup,  
    [in] FLockClrVersionCallback  *pEndHostSetup  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e3173-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e3173-106">Parameters</span></span>  
 `hostCallback`  
 <span data-ttu-id="e3173-107">[in] La fonction d’être appelée par le CLR lors de l’initialisation.</span><span class="sxs-lookup"><span data-stu-id="e3173-107">[in] The function to be called by the CLR upon initialization.</span></span>  
  
 `pBeginHostSetup`  
 <span data-ttu-id="e3173-108">[in] La fonction peut être appelée par l’hôte pour informer le CLR que l’initialisation démarre.</span><span class="sxs-lookup"><span data-stu-id="e3173-108">[in] The function to be called by the host to inform the CLR that initialization is starting.</span></span>  
  
 `pEndHostSetup`  
 <span data-ttu-id="e3173-109">[in] La fonction peut être appelée par l’hôte pour informer le CLR que l’initialisation est terminée.</span><span class="sxs-lookup"><span data-stu-id="e3173-109">[in] The function to be called by the host to inform the CLR that initialization is complete.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e3173-110">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="e3173-110">Return Value</span></span>  
 <span data-ttu-id="e3173-111">Cette méthode retourne des codes d’erreur COM standard, tel que défini dans WinError.h, en plus des valeurs suivantes.</span><span class="sxs-lookup"><span data-stu-id="e3173-111">This method returns standard COM error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="e3173-112">Code de retour</span><span class="sxs-lookup"><span data-stu-id="e3173-112">Return code</span></span>|<span data-ttu-id="e3173-113">Description</span><span class="sxs-lookup"><span data-stu-id="e3173-113">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="e3173-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="e3173-114">S_OK</span></span>|<span data-ttu-id="e3173-115">La commande s'est correctement terminée.</span><span class="sxs-lookup"><span data-stu-id="e3173-115">The method completed successfully.</span></span>|  
|<span data-ttu-id="e3173-116">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="e3173-116">E_INVALIDARG</span></span>|<span data-ttu-id="e3173-117">Un ou plusieurs des arguments sont null.</span><span class="sxs-lookup"><span data-stu-id="e3173-117">One or more of the arguments is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e3173-118">Remarques</span><span class="sxs-lookup"><span data-stu-id="e3173-118">Remarks</span></span>  
 <span data-ttu-id="e3173-119">L’hôte appelle `LockClrVersion` avant d’initialiser le CLR.</span><span class="sxs-lookup"><span data-stu-id="e3173-119">The host calls `LockClrVersion` before initializing the CLR.</span></span> <span data-ttu-id="e3173-120">`LockClrVersion`accepte trois paramètres, qui sont tous des rappels de type [FLockClrVersionCallback](../../../../docs/framework/unmanaged-api/hosting/flockclrversioncallback-function-pointer.md).</span><span class="sxs-lookup"><span data-stu-id="e3173-120">`LockClrVersion` takes three parameters, all of which are callbacks of type [FLockClrVersionCallback](../../../../docs/framework/unmanaged-api/hosting/flockclrversioncallback-function-pointer.md).</span></span> <span data-ttu-id="e3173-121">Ce type est défini comme suit.</span><span class="sxs-lookup"><span data-stu-id="e3173-121">This type is defined as follows.</span></span>  
  
```  
typedef HRESULT ( __stdcall *FLockClrVersionCallback ) ();  
```  
  
 <span data-ttu-id="e3173-122">Les étapes suivantes se produisent lors de l’initialisation du runtime :</span><span class="sxs-lookup"><span data-stu-id="e3173-122">The following steps occur upon initialization of the runtime:</span></span>  
  
1.  <span data-ttu-id="e3173-123">L’hôte appelle [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) ou l’une des autres fonctions de l’initialisation du runtime.</span><span class="sxs-lookup"><span data-stu-id="e3173-123">The host calls [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) or one of the other runtime initialization functions.</span></span> <span data-ttu-id="e3173-124">L’hôte peut également initialiser le runtime à l’aide d’activation d’un objet COM.</span><span class="sxs-lookup"><span data-stu-id="e3173-124">Alternatively, the host could initialize the runtime using COM object activation.</span></span>  
  
2.  <span data-ttu-id="e3173-125">Le runtime appelle la fonction spécifiée par le `hostCallback` paramètre.</span><span class="sxs-lookup"><span data-stu-id="e3173-125">The runtime calls the function specified by the `hostCallback` parameter.</span></span>  
  
3.  <span data-ttu-id="e3173-126">La fonction spécifiée par `hostCallback` fait ensuite la séquence d’appels suivante :</span><span class="sxs-lookup"><span data-stu-id="e3173-126">The function specified by `hostCallback` then makes the following sequence of calls:</span></span>  
  
    -   <span data-ttu-id="e3173-127">La fonction spécifiée par le `pBeginHostSetup` paramètre.</span><span class="sxs-lookup"><span data-stu-id="e3173-127">The function specified by the `pBeginHostSetup` parameter.</span></span>  
  
    -   <span data-ttu-id="e3173-128">`CorBindToRuntimeEx`(ou une autre fonction de l’initialisation du runtime).</span><span class="sxs-lookup"><span data-stu-id="e3173-128">`CorBindToRuntimeEx` (or another runtime initialization function).</span></span>  
  
    -   <span data-ttu-id="e3173-129">[ICLRRuntimeHost::SetHostControl](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md).</span><span class="sxs-lookup"><span data-stu-id="e3173-129">[ICLRRuntimeHost::SetHostControl](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md).</span></span>  
  
    -   <span data-ttu-id="e3173-130">[ICLRRuntimeHost::Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md).</span><span class="sxs-lookup"><span data-stu-id="e3173-130">[ICLRRuntimeHost::Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md).</span></span>  
  
    -   <span data-ttu-id="e3173-131">La fonction spécifiée par le `pEndHostSetup` paramètre.</span><span class="sxs-lookup"><span data-stu-id="e3173-131">The function specified by the `pEndHostSetup` parameter.</span></span>  
  
 <span data-ttu-id="e3173-132">Tous les appels de `pBeginHostSetup` à `pEndHostSetup` doit se produire sur un seul thread ou d’une fibre, avec la même pile logique.</span><span class="sxs-lookup"><span data-stu-id="e3173-132">All the calls from `pBeginHostSetup` to `pEndHostSetup` must occur on a single thread or fiber, with the same logical stack.</span></span> <span data-ttu-id="e3173-133">Ce thread peut être différent du thread sur lequel `hostCallback` est appelée.</span><span class="sxs-lookup"><span data-stu-id="e3173-133">This thread can be different from the thread upon which `hostCallback` is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3173-134">Spécifications</span><span class="sxs-lookup"><span data-stu-id="e3173-134">Requirements</span></span>  
 <span data-ttu-id="e3173-135">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3173-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3173-136">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e3173-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e3173-137">**Bibliothèque :** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e3173-137">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e3173-138">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3173-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3173-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e3173-139">See Also</span></span>  
 [<span data-ttu-id="e3173-140">Fonctions d’hébergement du CLR déconseillées</span><span class="sxs-lookup"><span data-stu-id="e3173-140">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
