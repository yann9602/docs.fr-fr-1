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
ms.openlocfilehash: 054615e08da785f34be59c52488b8a4dcc2d7d98
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icorruntimehostunloaddomain-method"></a><span data-ttu-id="9a41d-102">ICorRuntimeHost::UnloadDomain, méthode</span><span class="sxs-lookup"><span data-stu-id="9a41d-102">ICorRuntimeHost::UnloadDomain Method</span></span>
<span data-ttu-id="9a41d-103">Décharge le domaine d’application du processus en cours.</span><span class="sxs-lookup"><span data-stu-id="9a41d-103">Unloads the specified application domain from the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a41d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9a41d-104">Syntax</span></span>  
  
```  
HRESULT UnloadDomain (  
    [in] IUnknown* pAppDomain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9a41d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9a41d-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="9a41d-106">[in] Un pointeur de type <xref:System._AppDomain?displayProperty=nameWithType> qui représente le domaine d’être déchargé.</span><span class="sxs-lookup"><span data-stu-id="9a41d-106">[in] A pointer of type <xref:System._AppDomain?displayProperty=nameWithType> that represents the domain to be unloaded.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9a41d-107">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="9a41d-107">Return Value</span></span>  
  
|<span data-ttu-id="9a41d-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9a41d-108">HRESULT</span></span>|<span data-ttu-id="9a41d-109">Description</span><span class="sxs-lookup"><span data-stu-id="9a41d-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9a41d-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="9a41d-110">S_OK</span></span>|<span data-ttu-id="9a41d-111">L’opération a réussi.</span><span class="sxs-lookup"><span data-stu-id="9a41d-111">The operation was successful.</span></span>|  
|<span data-ttu-id="9a41d-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="9a41d-112">S_FALSE</span></span>|<span data-ttu-id="9a41d-113">L’opération a échoué.</span><span class="sxs-lookup"><span data-stu-id="9a41d-113">The operation failed to complete.</span></span>|  
|<span data-ttu-id="9a41d-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9a41d-114">E_FAIL</span></span>|<span data-ttu-id="9a41d-115">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="9a41d-115">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="9a41d-116">Si une méthode retourne E_FAIL, le common language runtime (CLR) n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="9a41d-116">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="9a41d-117">Les appels suivants à toute API d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="9a41d-117">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="9a41d-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9a41d-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9a41d-119">Le CLR n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="9a41d-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9a41d-120">Spécifications</span><span class="sxs-lookup"><span data-stu-id="9a41d-120">Requirements</span></span>  
 <span data-ttu-id="9a41d-121">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9a41d-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a41d-122">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9a41d-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9a41d-123">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9a41d-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9a41d-124">**Version du .NET framework :** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="9a41d-124">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a41d-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9a41d-125">See Also</span></span>  
 <xref:System._AppDomain>  
 <xref:System.AppDomain>  
 [<span data-ttu-id="9a41d-126">ICorRuntimeHost (Interface)</span><span class="sxs-lookup"><span data-stu-id="9a41d-126">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
