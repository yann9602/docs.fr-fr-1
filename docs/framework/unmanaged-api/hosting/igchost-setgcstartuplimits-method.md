---
title: "IGCHost::SetGCStartupLimits, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IGCHost.SetGCStartupLimits
api_location: mscoree.dll
api_type: COM
f1_keywords: SetGCStartupLimits
helpviewer_keywords:
- SetGCStartupLimits method, IGCHost interface [.NET Framework hosting]
- IGCHost::SetGCStartupLimits method [.NET Framework hosting]
ms.assetid: cae53926-82ac-4d1d-b297-0bde0bd1bebb
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f95e5afa1297602e4ef12ed0dfb3f98aa5c762ca
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="igchostsetgcstartuplimits-method"></a><span data-ttu-id="1cca2-102">IGCHost::SetGCStartupLimits, méthode</span><span class="sxs-lookup"><span data-stu-id="1cca2-102">IGCHost::SetGCStartupLimits Method</span></span>
<span data-ttu-id="1cca2-103">Définit la taille du segment et la taille maximale pour la génération 0.</span><span class="sxs-lookup"><span data-stu-id="1cca2-103">Sets the segment size and the maximum size for generation 0.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1cca2-104">En commençant par le [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], vous pouvez définir la taille du segment et taille maximale de génération 0 pour les valeurs supérieure `DWORD` à l’aide de la [IGCHost2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="1cca2-104">Starting with the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], you can set segment size and maximum generation 0 size to values greater than `DWORD` by using the [IGCHost2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1cca2-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1cca2-105">Syntax</span></span>  
  
```  
HRESULT SetGCStartupLimits (  
    [in] DWORD SegmentSize,  
    [in] DWORD MaxGen0Size  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1cca2-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1cca2-106">Parameters</span></span>  
 `SegmentSize`  
 <span data-ttu-id="1cca2-107">[in] La taille du segment utilisé par le système de garbage collection.</span><span class="sxs-lookup"><span data-stu-id="1cca2-107">[in] The size of the segment used by the garbage collection system.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="1cca2-108">[in] La taille maximale pour la génération 0.</span><span class="sxs-lookup"><span data-stu-id="1cca2-108">[in] The maximum size for generation 0.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1cca2-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="1cca2-109">Remarks</span></span>  
 <span data-ttu-id="1cca2-110">Le `SetGCStartupLimits` méthode peut être appelée qu’une seule fois.</span><span class="sxs-lookup"><span data-stu-id="1cca2-110">The `SetGCStartupLimits` method may be called only once.</span></span> <span data-ttu-id="1cca2-111">Ces valeurs ne peuvent pas être modifiées ultérieurement.</span><span class="sxs-lookup"><span data-stu-id="1cca2-111">These values cannot be changed later.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1cca2-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="1cca2-112">Requirements</span></span>  
 <span data-ttu-id="1cca2-113">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1cca2-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1cca2-114">**En-tête :** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="1cca2-114">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="1cca2-115">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1cca2-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1cca2-116">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1cca2-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1cca2-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1cca2-117">See Also</span></span>  
 [<span data-ttu-id="1cca2-118">IGCHost (Interface)</span><span class="sxs-lookup"><span data-stu-id="1cca2-118">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
