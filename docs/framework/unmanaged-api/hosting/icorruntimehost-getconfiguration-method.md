---
title: "ICorRuntimeHost::GetConfiguration, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorRuntimeHost.GetConfiguration
api_location: mscoree.dll
api_type: COM
f1_keywords: ICorRuntimeHost::GetConfiguration
helpviewer_keywords:
- ICorRuntimeHost::GetConfiguration method [.NET Framework hosting]
- GetConfiguration method [.NET Framework hosting]
ms.assetid: c431617a-b055-44a0-8730-48b7a86d9610
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 61c0a95df2140d2eaf771fcd8f50cd733b9133e1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icorruntimehostgetconfiguration-method"></a><span data-ttu-id="66eeb-102">ICorRuntimeHost::GetConfiguration, méthode</span><span class="sxs-lookup"><span data-stu-id="66eeb-102">ICorRuntimeHost::GetConfiguration Method</span></span>
<span data-ttu-id="66eeb-103">Obtient un objet qui permet à l’hôte spécifier la configuration du rappel du common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="66eeb-103">Gets an object that allows the host to specify the callback configuration of the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66eeb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="66eeb-104">Syntax</span></span>  
  
```  
HRESULT GetConfiguration(  
    [out] ICorConfiguration** pConfiguration  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="66eeb-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="66eeb-105">Parameters</span></span>  
 `pConfiguration`  
 <span data-ttu-id="66eeb-106">[out] Un pointeur vers l’adresse d’un [ICorConfiguration](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md) objet qui peut être utilisé pour configurer le CLR.</span><span class="sxs-lookup"><span data-stu-id="66eeb-106">[out] A pointer to the address of an [ICorConfiguration](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md) object that can be used to configure the CLR.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="66eeb-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="66eeb-107">Remarks</span></span>  
 <span data-ttu-id="66eeb-108">Le CLR doit être configuré avant son initialisation ; dans le cas contraire, la `GetConfiguration` méthode retourne un HRESULT indiquant une erreur.</span><span class="sxs-lookup"><span data-stu-id="66eeb-108">The CLR must be configured prior to its initialization; otherwise, the `GetConfiguration` method returns an HRESULT indicating an error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66eeb-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="66eeb-109">Requirements</span></span>  
 <span data-ttu-id="66eeb-110">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="66eeb-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66eeb-111">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="66eeb-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="66eeb-112">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="66eeb-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="66eeb-113">**Versions du .NET framework :** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="66eeb-113">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66eeb-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="66eeb-114">See Also</span></span>  
 [<span data-ttu-id="66eeb-115">ICorRuntimeHost (Interface)</span><span class="sxs-lookup"><span data-stu-id="66eeb-115">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
