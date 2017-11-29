---
title: "ICorRuntimeHost::NextDomain, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorRuntimeHost.NextDomain
api_location: mscoree.dll
api_type: COM
f1_keywords: ICorRuntimeHost::NextDomain
helpviewer_keywords:
- ICorRuntimeHost::NextDomain method [.NET Framework hosting]
- NextDomain method [.NET Framework hosting]
ms.assetid: fe07a05b-f6d6-44b5-ab01-b9a6eb15c350
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: de7d90ed55cf27aa0b1679b5e55d9f28902b6aeb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icorruntimehostnextdomain-method"></a><span data-ttu-id="10804-102">ICorRuntimeHost::NextDomain, méthode</span><span class="sxs-lookup"><span data-stu-id="10804-102">ICorRuntimeHost::NextDomain Method</span></span>
<span data-ttu-id="10804-103">Obtient un pointeur d’interface au domaine suivant dans l’énumération.</span><span class="sxs-lookup"><span data-stu-id="10804-103">Gets an interface pointer to the next domain in the enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10804-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="10804-104">Syntax</span></span>  
  
```  
HRESULT NextDomain (  
    [in] HCORENUM hEnum,  
    [out] void** pAppDomain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="10804-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="10804-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="10804-106">[in] L’énumérateur a été obtenu via un appel à [EnumDomains](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-enumdomains-method.md).</span><span class="sxs-lookup"><span data-stu-id="10804-106">[in] The enumerator that was obtained through a call to [EnumDomains](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-enumdomains-method.md).</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="10804-107">[out] Pointeur d’interface vers le <xref:System._AppDomain?displayProperty=nameWithType> type qui représente le domaine suivant dans l’énumération ou la valeur null, si aucun domaine n’existe.</span><span class="sxs-lookup"><span data-stu-id="10804-107">[out] An interface pointer to the <xref:System._AppDomain?displayProperty=nameWithType> type that represents the next domain in the enumeration, or null, if no more domains exist.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="10804-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="10804-108">Return Value</span></span>  
  
|<span data-ttu-id="10804-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="10804-109">HRESULT</span></span>|<span data-ttu-id="10804-110">Description</span><span class="sxs-lookup"><span data-stu-id="10804-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="10804-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="10804-111">S_OK</span></span>|<span data-ttu-id="10804-112">L’opération a réussi.</span><span class="sxs-lookup"><span data-stu-id="10804-112">The operation was successful.</span></span>|  
|<span data-ttu-id="10804-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="10804-113">S_FALSE</span></span>|<span data-ttu-id="10804-114">L’opération a échoué, ou il n’existe aucun domaine plus dans l’énumération.</span><span class="sxs-lookup"><span data-stu-id="10804-114">The operation failed to complete, or there are no more domains in the enumeration.</span></span>|  
|<span data-ttu-id="10804-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="10804-115">E_FAIL</span></span>|<span data-ttu-id="10804-116">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="10804-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="10804-117">Si une méthode retourne E_FAIL, le common language runtime (CLR) n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="10804-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="10804-118">Les appels suivants à toute API d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="10804-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="10804-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="10804-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="10804-120">Le CLR n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="10804-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="10804-121">Spécifications</span><span class="sxs-lookup"><span data-stu-id="10804-121">Requirements</span></span>  
 <span data-ttu-id="10804-122">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="10804-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10804-123">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="10804-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="10804-124">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="10804-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="10804-125">**Versions du .NET framework :** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="10804-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10804-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="10804-126">See Also</span></span>  
 <xref:System._AppDomain>  
 <xref:System.AppDomain>  
 [<span data-ttu-id="10804-127">ICorRuntimeHost (Interface)</span><span class="sxs-lookup"><span data-stu-id="10804-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
