---
title: "ICLRValidator::FormatEventInfo, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRValidator.FormatEventInfo
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRValidator::FormatEventInfo
helpviewer_keywords:
- FormatEventInfo method, ICLRValidator interface [.NET Framework hosting]
- ICLRValidator::FormatEventInfo method [.NET Framework hosting]
ms.assetid: 808e1f1d-52f4-47c4-83cc-dcf47d075219
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d03864ac8e4e0423e45ac084e01af98e3eab13a2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrvalidatorformateventinfo-method"></a><span data-ttu-id="d78e4-102">ICLRValidator::FormatEventInfo, méthode</span><span class="sxs-lookup"><span data-stu-id="d78e4-102">ICLRValidator::FormatEventInfo Method</span></span>
<span data-ttu-id="d78e4-103">Obtient un message détaillé sur l’erreur de validation spécifiée.</span><span class="sxs-lookup"><span data-stu-id="d78e4-103">Gets a detailed message about the specified validation error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d78e4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d78e4-104">Syntax</span></span>  
  
```  
HRESULT FormatEventInfo (  
    [in] HRESULT            hVECode,  
    [in] VEContext          Context,  
    [in, out] LPWSTR        msg,  
    [in] unsigned long      ulMaxLength,  
    [in] SAFEARRAY(VARIANT) psa  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d78e4-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d78e4-105">Parameters</span></span>  
 `hVECode`  
 <span data-ttu-id="d78e4-106">[in] La valeur HRESULT qui a été passée au gestionnaire d’erreurs de validation.</span><span class="sxs-lookup"><span data-stu-id="d78e4-106">[in] The HRESULT value that was passed to the validation error handler.</span></span>  
  
 `Context`  
 <span data-ttu-id="d78e4-107">[in] A `VEContext` instance qui contient des informations de contexte sur les erreurs de validation.</span><span class="sxs-lookup"><span data-stu-id="d78e4-107">[in] A `VEContext` instance that contains context information about the validation errors.</span></span>  
  
 `msg`  
 <span data-ttu-id="d78e4-108">[dans, out] Le message d’erreur convivial.</span><span class="sxs-lookup"><span data-stu-id="d78e4-108">[in, out] The friendly error message.</span></span>  
  
 `ulMaxLength`  
 <span data-ttu-id="d78e4-109">[in] La longueur maximale du message d’erreur.</span><span class="sxs-lookup"><span data-stu-id="d78e4-109">[in] The maximum length of the error message.</span></span>  
  
 `psa`  
 <span data-ttu-id="d78e4-110">[in] Un tableau sécurisé de paramètres supplémentaires à utiliser dans le message.</span><span class="sxs-lookup"><span data-stu-id="d78e4-110">[in] A safe array of additional parameters to be used in the message.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d78e4-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="d78e4-111">Return Value</span></span>  
  
|<span data-ttu-id="d78e4-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d78e4-112">HRESULT</span></span>|<span data-ttu-id="d78e4-113">Description</span><span class="sxs-lookup"><span data-stu-id="d78e4-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d78e4-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="d78e4-114">S_OK</span></span>|<span data-ttu-id="d78e4-115">`FormatEventInfo`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="d78e4-115">`FormatEventInfo` returned successfully.</span></span>|  
|<span data-ttu-id="d78e4-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d78e4-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d78e4-117">Le common language runtime (CLR) n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="d78e4-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d78e4-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d78e4-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d78e4-119">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="d78e4-119">The call timed out.</span></span>|  
|<span data-ttu-id="d78e4-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d78e4-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d78e4-121">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="d78e4-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d78e4-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d78e4-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d78e4-123">Un événement a été annulé alors qu’un thread bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="d78e4-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d78e4-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d78e4-124">E_FAIL</span></span>|<span data-ttu-id="d78e4-125">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="d78e4-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d78e4-126">Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="d78e4-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d78e4-127">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d78e4-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d78e4-128">Spécifications</span><span class="sxs-lookup"><span data-stu-id="d78e4-128">Requirements</span></span>  
 <span data-ttu-id="d78e4-129">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d78e4-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d78e4-130">**En-tête :** IValidator.idl, IValidator.h</span><span class="sxs-lookup"><span data-stu-id="d78e4-130">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="d78e4-131">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d78e4-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d78e4-132">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d78e4-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d78e4-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d78e4-133">See Also</span></span>  
 [<span data-ttu-id="d78e4-134">ICLRErrorReportingManager (Interface)</span><span class="sxs-lookup"><span data-stu-id="d78e4-134">ICLRErrorReportingManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)  
 [<span data-ttu-id="d78e4-135">ICLRValidator (Interface)</span><span class="sxs-lookup"><span data-stu-id="d78e4-135">ICLRValidator Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)
