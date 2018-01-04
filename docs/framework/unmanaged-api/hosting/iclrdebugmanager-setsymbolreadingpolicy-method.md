---
title: "ICLRDebugManager::SetSymbolReadingPolicy, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDebugManager.SetSymbolReadingPolicy
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRDebugManager::SetSymbolReadingPolicy
helpviewer_keywords:
- ICLRDebugManager, SetSymbolREadingPolicy method
- SetSymbolReadingPolicy method [.NET Framework hosting]
- ICLRDebugManager::SetSymbolReadingPolicy method [.NET Framework hosting]
ms.assetid: bd921fa2-d377-4d79-acfc-64c38d4dcae9
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 440bab97dc765438758abad3275bb2e4f8051da9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdebugmanagersetsymbolreadingpolicy-method"></a><span data-ttu-id="7ec57-102">ICLRDebugManager::SetSymbolReadingPolicy, méthode</span><span class="sxs-lookup"><span data-stu-id="7ec57-102">ICLRDebugManager::SetSymbolReadingPolicy Method</span></span>
<span data-ttu-id="7ec57-103">Définit la stratégie pour la lecture des fichiers de programme (PDB) de la base de données.</span><span class="sxs-lookup"><span data-stu-id="7ec57-103">Sets the policy for reading program database (PDB) files.</span></span> <span data-ttu-id="7ec57-104">La stratégie détermine si les informations sur les fichiers et les numéros de ligne sont incluses dans les piles d’appels.</span><span class="sxs-lookup"><span data-stu-id="7ec57-104">The policy determines whether information about line numbers and files is included in call stacks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ec57-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7ec57-105">Syntax</span></span>  
  
```  
HRESULT SetSymbolReadingPolicy (  
    [in] ESymbolReadingPolicy policy  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7ec57-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7ec57-106">Parameters</span></span>  
 `policy`  
 <span data-ttu-id="7ec57-107">[in] Un membre de la [ESymbolReadingPolicy](../../../../docs/framework/unmanaged-api/hosting/esymbolreadingpolicy-enumeration.md) énumération.</span><span class="sxs-lookup"><span data-stu-id="7ec57-107">[in] A member of the [ESymbolReadingPolicy](../../../../docs/framework/unmanaged-api/hosting/esymbolreadingpolicy-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7ec57-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="7ec57-108">Return Value</span></span>  
  
|<span data-ttu-id="7ec57-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7ec57-109">HRESULT</span></span>|<span data-ttu-id="7ec57-110">Description</span><span class="sxs-lookup"><span data-stu-id="7ec57-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7ec57-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="7ec57-111">S_OK</span></span>|<span data-ttu-id="7ec57-112">`SetSymbolReadingPolicy`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="7ec57-112">`SetSymbolReadingPolicy` returned successfully.</span></span>|  
|<span data-ttu-id="7ec57-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7ec57-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7ec57-114">Le common language runtime (CLR) n’a pas été chargé dans un processus ou le CLR est dans un état dans lequel il ne peut pas exécuter du code managé ou traiter l’appel avec succès.</span><span class="sxs-lookup"><span data-stu-id="7ec57-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7ec57-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7ec57-115">E_FAIL</span></span>|<span data-ttu-id="7ec57-116">Une défaillance grave et inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="7ec57-116">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7ec57-117">Une fois une méthode retourne E_FAIL, le CLR n’est plus utilisable dans le processus.</span><span class="sxs-lookup"><span data-stu-id="7ec57-117">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7ec57-118">Les appels suivants aux méthodes d’hébergement retournent HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="7ec57-118">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7ec57-119">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="7ec57-119">Requirements</span></span>  
 <span data-ttu-id="7ec57-120">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7ec57-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ec57-121">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7ec57-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7ec57-122">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7ec57-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7ec57-123">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ec57-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ec57-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7ec57-124">See Also</span></span>  
 [<span data-ttu-id="7ec57-125">ICLRDebugManager, interface</span><span class="sxs-lookup"><span data-stu-id="7ec57-125">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)
