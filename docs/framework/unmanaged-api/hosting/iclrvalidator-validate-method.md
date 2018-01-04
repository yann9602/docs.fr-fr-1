---
title: "ICLRValidator::Validate, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRValidator.Validate
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRValidator::Validate
helpviewer_keywords:
- Validate method, ICLRValidator interface [.NET Framework hosting]
- ICLRValidator::Validate method [.NET Framework hosting]
ms.assetid: 0b1b432a-d234-4002-839b-81366c3a8bdc
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7328fe62276de6c33464ab8cfc6d6a5f39ee710e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrvalidatorvalidate-method"></a><span data-ttu-id="b04f8-102">ICLRValidator::Validate, méthode</span><span class="sxs-lookup"><span data-stu-id="b04f8-102">ICLRValidator::Validate Method</span></span>
<span data-ttu-id="b04f8-103">Valide le fichier exécutable portable (PE) ou Microsoft intermediate language (MSIL) dans le fichier spécifié.</span><span class="sxs-lookup"><span data-stu-id="b04f8-103">Validates the portable executable (PE) or Microsoft intermediate language (MSIL) in the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b04f8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b04f8-104">Syntax</span></span>  
  
```  
HRESULT Validate (  
    [in] IVEHandler        *veh,  
    [in] unsigned long      ulAppDomainId,  
    [in] unsigned long      ulFlags,  
    [in] unsigned long      ulMaxError,  
    [in] unsigned long      token,  
    [in] LPWSTR             fileName,  
    [in, size_is(ulSize)] BYTE *pe,  
    [in] unsigned long      ulSize  
);      
```  
  
#### <a name="parameters"></a><span data-ttu-id="b04f8-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b04f8-105">Parameters</span></span>  
 `veh`  
 <span data-ttu-id="b04f8-106">[in] Un pointeur vers un `IVEHandler` instance qui gère les erreurs de validation.</span><span class="sxs-lookup"><span data-stu-id="b04f8-106">[in] A pointer to an `IVEHandler` instance that handles validation errors.</span></span>  
  
 `ulAppDomainId`  
 <span data-ttu-id="b04f8-107">[in] L’identificateur actuel <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="b04f8-107">[in] The identifier for the current <xref:System.AppDomain>.</span></span>  
  
 `ulFlags`  
 <span data-ttu-id="b04f8-108">[in] Une combinaison de [ValidatorFlags](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md) valeurs indiquant le genre de validation doit être effectuée.</span><span class="sxs-lookup"><span data-stu-id="b04f8-108">[in] A combination of [ValidatorFlags](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md) values, indicating the kind of validation that should be performed.</span></span>  
  
 `ulMaxError`  
 <span data-ttu-id="b04f8-109">[in] Le nombre maximal d’erreurs autorisées avant de quitter la validation.</span><span class="sxs-lookup"><span data-stu-id="b04f8-109">[in] The maximum number of errors to allow before exiting the validation.</span></span>  
  
 `token`  
 <span data-ttu-id="b04f8-110">[in] Non utilisé.</span><span class="sxs-lookup"><span data-stu-id="b04f8-110">[in] Unused.</span></span>  
  
 `fileName`  
 <span data-ttu-id="b04f8-111">[in] Le nom du fichier à valider.</span><span class="sxs-lookup"><span data-stu-id="b04f8-111">[in] The name of the file to be validated.</span></span>  
  
 `pe`  
 <span data-ttu-id="b04f8-112">[in] Pointeur vers la mémoire tampon de fichier.</span><span class="sxs-lookup"><span data-stu-id="b04f8-112">[in] A pointer to the file buffer.</span></span>  
  
 `ulSize`  
 <span data-ttu-id="b04f8-113">[in] La taille, en octets, du fichier à valider.</span><span class="sxs-lookup"><span data-stu-id="b04f8-113">[in] The size, in bytes, of the file to be validated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b04f8-114">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="b04f8-114">Return Value</span></span>  
  
|<span data-ttu-id="b04f8-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b04f8-115">HRESULT</span></span>|<span data-ttu-id="b04f8-116">Description</span><span class="sxs-lookup"><span data-stu-id="b04f8-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b04f8-117">S_OK</span><span class="sxs-lookup"><span data-stu-id="b04f8-117">S_OK</span></span>|<span data-ttu-id="b04f8-118">`Validate`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="b04f8-118">`Validate` returned successfully.</span></span>|  
|<span data-ttu-id="b04f8-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b04f8-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b04f8-120">Le common language runtime (CLR) n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="b04f8-120">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b04f8-121">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b04f8-121">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b04f8-122">L’appel a expiré.</span><span class="sxs-lookup"><span data-stu-id="b04f8-122">The call timed out.</span></span>|  
|<span data-ttu-id="b04f8-123">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b04f8-123">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b04f8-124">L’appelant ne possède pas le verrou.</span><span class="sxs-lookup"><span data-stu-id="b04f8-124">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b04f8-125">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b04f8-125">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b04f8-126">Un événement a été annulé alors qu’un thread bloqué ou une fibre l’attendait.</span><span class="sxs-lookup"><span data-stu-id="b04f8-126">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b04f8-127">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b04f8-127">E_FAIL</span></span>|<span data-ttu-id="b04f8-128">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="b04f8-128">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b04f8-129">Lorsqu’une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="b04f8-129">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b04f8-130">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="b04f8-130">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b04f8-131">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b04f8-131">Requirements</span></span>  
 <span data-ttu-id="b04f8-132">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b04f8-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b04f8-133">**En-tête :** IValidator.idl, IValidator.h</span><span class="sxs-lookup"><span data-stu-id="b04f8-133">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="b04f8-134">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b04f8-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b04f8-135">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b04f8-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b04f8-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b04f8-136">See Also</span></span>  
 [<span data-ttu-id="b04f8-137">ICLRValidator, interface</span><span class="sxs-lookup"><span data-stu-id="b04f8-137">ICLRValidator Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)
