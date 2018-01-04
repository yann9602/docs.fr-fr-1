---
title: "ICorRuntimeHost::UnloadDomain, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorRuntimeHost.UnloadDomain
api_location: mscoree.dll
api_type: COM
f1_keywords: ICorRuntimeHost::UnloadDomain
helpviewer_keywords:
- ICorRuntimeHost::UnloadDomain method [.NET Framework hosting]
- UnloadDomain method [.NET Framework hosting]
ms.assetid: dd9e9204-a80d-44f3-8192-779224b35056
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 067b60b9da02300e9e7316712d0058a61ab8a697
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icorruntimehostunloaddomain-method"></a><span data-ttu-id="67908-102">ICorRuntimeHost::UnloadDomain, méthode</span><span class="sxs-lookup"><span data-stu-id="67908-102">ICorRuntimeHost::UnloadDomain Method</span></span>
<span data-ttu-id="67908-103">Décharge le domaine d’application du processus en cours.</span><span class="sxs-lookup"><span data-stu-id="67908-103">Unloads the specified application domain from the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67908-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="67908-104">Syntax</span></span>  
  
```  
HRESULT UnloadDomain (  
    [in] IUnknown* pAppDomain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="67908-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="67908-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="67908-106">[in] Un pointeur de type <xref:System._AppDomain?displayProperty=nameWithType> qui représente le domaine d’être déchargé.</span><span class="sxs-lookup"><span data-stu-id="67908-106">[in] A pointer of type <xref:System._AppDomain?displayProperty=nameWithType> that represents the domain to be unloaded.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="67908-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="67908-107">Return Value</span></span>  
  
|<span data-ttu-id="67908-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="67908-108">HRESULT</span></span>|<span data-ttu-id="67908-109">Description</span><span class="sxs-lookup"><span data-stu-id="67908-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="67908-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="67908-110">S_OK</span></span>|<span data-ttu-id="67908-111">L’opération a réussi.</span><span class="sxs-lookup"><span data-stu-id="67908-111">The operation was successful.</span></span>|  
|<span data-ttu-id="67908-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="67908-112">S_FALSE</span></span>|<span data-ttu-id="67908-113">L’opération a échoué.</span><span class="sxs-lookup"><span data-stu-id="67908-113">The operation failed to complete.</span></span>|  
|<span data-ttu-id="67908-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="67908-114">E_FAIL</span></span>|<span data-ttu-id="67908-115">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="67908-115">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="67908-116">Si une méthode retourne E_FAIL, le common language runtime (CLR) n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="67908-116">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="67908-117">Les appels suivants à toute API d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="67908-117">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="67908-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="67908-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="67908-119">Le CLR n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="67908-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="67908-120">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="67908-120">Requirements</span></span>  
 <span data-ttu-id="67908-121">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="67908-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67908-122">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="67908-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="67908-123">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="67908-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="67908-124">**Version du .NET framework :** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="67908-124">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67908-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="67908-125">See Also</span></span>  
 <xref:System._AppDomain>  
 <xref:System.AppDomain>  
 [<span data-ttu-id="67908-126">ICorRuntimeHost, interface</span><span class="sxs-lookup"><span data-stu-id="67908-126">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
