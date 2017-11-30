---
title: "ICorRuntimeHost::CreateDomainSetup, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorRuntimeHost.CreateDomainSetup
api_location: mscoree.dll
api_type: COM
f1_keywords: ICorRuntimeHost::CreateDomainSetup
helpviewer_keywords:
- CreateDomainSetup method [.NET Framework hosting]
- ICorRuntimeHost::CreateDomainSetup method [.NET Framework hosting]
ms.assetid: c21dab60-fb65-47d9-8a94-7fd47ca53b48
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ca09788ea403e2a60d6de0cb6834fdc90261b770
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icorruntimehostcreatedomainsetup-method"></a><span data-ttu-id="39496-102">ICorRuntimeHost::CreateDomainSetup, méthode</span><span class="sxs-lookup"><span data-stu-id="39496-102">ICorRuntimeHost::CreateDomainSetup Method</span></span>
<span data-ttu-id="39496-103">Obtient un pointeur d’interface de type IAppDomainSetup à un <xref:System.AppDomainSetup?displayProperty=nameWithType> instance.</span><span class="sxs-lookup"><span data-stu-id="39496-103">Gets an interface pointer of type IAppDomainSetup to an <xref:System.AppDomainSetup?displayProperty=nameWithType> instance.</span></span> <span data-ttu-id="39496-104">`IAppDomainSetup`Fournit des méthodes pour configurer les aspects d’un domaine d’application avant qu’il est créé.</span><span class="sxs-lookup"><span data-stu-id="39496-104">`IAppDomainSetup` provides methods to configure aspects of an application domain before it is created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39496-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="39496-105">Syntax</span></span>  
  
```  
HRESULT CreateDomainSetup (  
    [out] IUnknown** pAppDomainSetup  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="39496-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="39496-106">Parameters</span></span>  
 `pAppDomainSetup`  
 <span data-ttu-id="39496-107">[out] Pointeur d’interface vers un <xref:System.AppDomainSetup?displayProperty=nameWithType> instance.</span><span class="sxs-lookup"><span data-stu-id="39496-107">[out] An interface pointer to an <xref:System.AppDomainSetup?displayProperty=nameWithType> instance.</span></span> <span data-ttu-id="39496-108">Ce paramètre est de type `IUnknown`, de sorte que les appelants doivent généralement appeler `QueryInterface` sur ce pointeur pour obtenir un pointeur d’interface de type `IAppDomainSetup`.</span><span class="sxs-lookup"><span data-stu-id="39496-108">This parameter is typed as `IUnknown`, so callers should generally call `QueryInterface` on this pointer to obtain an interface pointer of type `IAppDomainSetup`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="39496-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="39496-109">Return Value</span></span>  
  
|<span data-ttu-id="39496-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="39496-110">HRESULT</span></span>|<span data-ttu-id="39496-111">Description</span><span class="sxs-lookup"><span data-stu-id="39496-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="39496-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="39496-112">S_OK</span></span>|<span data-ttu-id="39496-113">L’opération a réussi.</span><span class="sxs-lookup"><span data-stu-id="39496-113">The operation was successful.</span></span>|  
|<span data-ttu-id="39496-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="39496-114">S_FALSE</span></span>|<span data-ttu-id="39496-115">L’opération a échoué.</span><span class="sxs-lookup"><span data-stu-id="39496-115">The operation failed to complete.</span></span>|  
|<span data-ttu-id="39496-116">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="39496-116">E_FAIL</span></span>|<span data-ttu-id="39496-117">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="39496-117">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="39496-118">Si une méthode retourne E_FAIL, le common language runtime (CLR) n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="39496-118">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="39496-119">Les appels suivants à toute API d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="39496-119">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="39496-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="39496-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="39496-121">Le CLR n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="39496-121">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="39496-122">Remarques</span><span class="sxs-lookup"><span data-stu-id="39496-122">Remarks</span></span>  
 <span data-ttu-id="39496-123">Le pointeur retourné par cette méthode est généralement passé en tant que paramètre à la [CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="39496-123">The pointer returned from this method is typically passed as a parameter to the [CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="39496-124">Spécifications</span><span class="sxs-lookup"><span data-stu-id="39496-124">Requirements</span></span>  
 <span data-ttu-id="39496-125">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="39496-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="39496-126">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="39496-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="39496-127">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="39496-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="39496-128">**Version du .NET framework :** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="39496-128">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39496-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="39496-129">See Also</span></span>  
 <xref:System._AppDomain>  
 <xref:System.AppDomain>  
 <xref:System.AppDomainSetup>  
 <xref:System.IAppDomainSetup?displayProperty=nameWithType>  
 [<span data-ttu-id="39496-130">ICorRuntimeHost (Interface)</span><span class="sxs-lookup"><span data-stu-id="39496-130">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
