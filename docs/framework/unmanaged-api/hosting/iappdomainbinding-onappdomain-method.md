---
title: "IAppDomainBinding::OnAppDomain, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IAppDomainBinding.OnAppDomain
api_location: mscoree.dll
api_type: COM
f1_keywords: OnAppDomain
helpviewer_keywords:
- IAppDomainBinding::OnAppDomain method [.NET Framework hosting]
- OnAppDomain method [.NET Framework hosting]
ms.assetid: b419dcc9-e8aa-484b-af0d-0f40358edb99
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f5350b9c44c04a4faee3b5026bc2b97ff549d4b4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="iappdomainbindingonappdomain-method"></a><span data-ttu-id="166ed-102">IAppDomainBinding::OnAppDomain, méthode</span><span class="sxs-lookup"><span data-stu-id="166ed-102">IAppDomainBinding::OnAppDomain Method</span></span>
<span data-ttu-id="166ed-103">Appelé par le common language runtime (CLR) pour notifier l’hôte qu’un domaine d’application a été créé.</span><span class="sxs-lookup"><span data-stu-id="166ed-103">Called by the common language runtime (CLR) to notify the host that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="166ed-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="166ed-104">Syntax</span></span>  
  
```  
HRESULT OnAppDomain (  
    [in] IUnknown* pAppdomain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="166ed-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="166ed-105">Parameters</span></span>  
 `pAppdomain`  
 <span data-ttu-id="166ed-106">[in] Un pointeur vers un [IUnknown](https://msdn.microsoft.com/library/94as6ehy(v=vs.110).aspx) objet d’interface qui représente le nouveau domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="166ed-106">[in] A pointer to an [IUnknown](https://msdn.microsoft.com/library/94as6ehy(v=vs.110).aspx) interface object that represents the new application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="166ed-107">Spécifications</span><span class="sxs-lookup"><span data-stu-id="166ed-107">Requirements</span></span>  
 <span data-ttu-id="166ed-108">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="166ed-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="166ed-109">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="166ed-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="166ed-110">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="166ed-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="166ed-111">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="166ed-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="166ed-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="166ed-112">See Also</span></span>  
 [<span data-ttu-id="166ed-113">IAppDomainBinding (Interface)</span><span class="sxs-lookup"><span data-stu-id="166ed-113">IAppDomainBinding Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iappdomainbinding-interface.md)
