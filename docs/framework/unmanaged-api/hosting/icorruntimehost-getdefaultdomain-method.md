---
title: "ICorRuntimeHost::GetDefaultDomain, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorRuntimeHost.GetDefaultDomain
api_location: mscoree.dll
api_type: COM
f1_keywords: ICorRuntimeHost::GetDefaultDomain
helpviewer_keywords:
- ICorRuntimeHost::GetDefaultDomain method [.NET Framework hosting]
- GetDefaultDomain method [.NET Framework hosting]
ms.assetid: 5e17a6fc-f335-4aae-9bb0-c3e1271a9426
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4c482247a0a227c202bb81db09d13ad9af71e60f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icorruntimehostgetdefaultdomain-method"></a><span data-ttu-id="b7541-102">ICorRuntimeHost::GetDefaultDomain, méthode</span><span class="sxs-lookup"><span data-stu-id="b7541-102">ICorRuntimeHost::GetDefaultDomain Method</span></span>
<span data-ttu-id="b7541-103">Obtient un pointeur d’interface de type <xref:System._AppDomain?displayProperty=nameWithType> qui représente le domaine par défaut pour le processus actuel.</span><span class="sxs-lookup"><span data-stu-id="b7541-103">Gets an interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType> that represents the default domain for the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7541-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b7541-104">Syntax</span></span>  
  
```  
HRESULT GetDefaultDomain (  
    [out] IUnknown** pAppDomain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b7541-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b7541-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="b7541-106">[out] Un pointeur d’interface de type <xref:System._AppDomain?displayProperty=nameWithType> à la <xref:System.AppDomain> instance qui représente le domaine d’application par défaut pour le processus.</span><span class="sxs-lookup"><span data-stu-id="b7541-106">[out] An interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType> to the <xref:System.AppDomain> instance that represents the default application domain for the process.</span></span>  
  
 <span data-ttu-id="b7541-107">Ce pointeur est tapé `IUnknown`, de sorte que les appelants doivent généralement appeler `QueryInterface` pour obtenir un pointeur d’interface de type <xref:System._AppDomain?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b7541-107">This pointer is typed `IUnknown`, so callers should generally call `QueryInterface` to obtain an interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b7541-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="b7541-108">Return Value</span></span>  
  
|<span data-ttu-id="b7541-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b7541-109">HRESULT</span></span>|<span data-ttu-id="b7541-110">Description</span><span class="sxs-lookup"><span data-stu-id="b7541-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b7541-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="b7541-111">S_OK</span></span>|<span data-ttu-id="b7541-112">L’opération a réussi.</span><span class="sxs-lookup"><span data-stu-id="b7541-112">The operation was successful.</span></span>|  
|<span data-ttu-id="b7541-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="b7541-113">S_FALSE</span></span>|<span data-ttu-id="b7541-114">L’opération a échoué.</span><span class="sxs-lookup"><span data-stu-id="b7541-114">The operation failed to complete.</span></span>|  
|<span data-ttu-id="b7541-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b7541-115">E_FAIL</span></span>|<span data-ttu-id="b7541-116">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="b7541-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="b7541-117">Si une méthode retourne E_FAIL, le common language runtime (CLR) n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="b7541-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="b7541-118">Les appels suivants à toute API d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="b7541-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="b7541-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b7541-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b7541-120">Le CLR n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="b7541-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b7541-121">Spécifications</span><span class="sxs-lookup"><span data-stu-id="b7541-121">Requirements</span></span>  
 <span data-ttu-id="b7541-122">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b7541-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7541-123">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b7541-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b7541-124">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b7541-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b7541-125">**Versions du .NET framework :** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="b7541-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7541-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b7541-126">See Also</span></span>  
 <xref:System._AppDomain>  
 <xref:System.AppDomain>  
 [<span data-ttu-id="b7541-127">ICorRuntimeHost (Interface)</span><span class="sxs-lookup"><span data-stu-id="b7541-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
