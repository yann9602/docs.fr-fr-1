---
title: "ICLRRuntimeInfo::LoadErrorString, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeInfo.LoadErrorString
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRRuntimeInfo::LoadErrorString
helpviewer_keywords:
- ICLRRuntimeInfo::LoadErrorString method [.NET Framework hosting]
- LoadErrorString method [.NET Framework hosting]
ms.assetid: 52c543ab-9ef5-4ee7-b836-c0ffc35cd45b
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 26fa051e5c4735307edbb443e6615a57190c0ae5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrruntimeinfoloaderrorstring-method"></a><span data-ttu-id="bdfeb-102">ICLRRuntimeInfo::LoadErrorString, méthode</span><span class="sxs-lookup"><span data-stu-id="bdfeb-102">ICLRRuntimeInfo::LoadErrorString Method</span></span>
<span data-ttu-id="bdfeb-103">Traduit une valeur HRESULT dans un message d’erreur approprié pour la culture spécifiée.</span><span class="sxs-lookup"><span data-stu-id="bdfeb-103">Translates an HRESULT value into an appropriate error message for the specified culture.</span></span>  
  
 <span data-ttu-id="bdfeb-104">Cette méthode remplace les fonctions suivantes :</span><span class="sxs-lookup"><span data-stu-id="bdfeb-104">This method supersedes the following functions:</span></span>  
  
-   [<span data-ttu-id="bdfeb-105">LoadStringRC</span><span class="sxs-lookup"><span data-stu-id="bdfeb-105">LoadStringRC</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md)  
  
-   [<span data-ttu-id="bdfeb-106">LoadStringRCEx</span><span class="sxs-lookup"><span data-stu-id="bdfeb-106">LoadStringRCEx</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md)  
  
## <a name="syntax"></a><span data-ttu-id="bdfeb-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bdfeb-107">Syntax</span></span>  
  
```  
HRESULT LoadErrorString(  
     [in] UINT iResourceID,  
     [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
     [in, out]  DWORD *pcchBuffer,  
     [in, lcid] LONG iLocaleID);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bdfeb-108">Paramètres</span><span class="sxs-lookup"><span data-stu-id="bdfeb-108">Parameters</span></span>  
 `iResourceID`  
 <span data-ttu-id="bdfeb-109">[in] HRESULT à convertir.</span><span class="sxs-lookup"><span data-stu-id="bdfeb-109">[in] The HRESULT to translate.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="bdfeb-110">[out] La chaîne de message associée au HRESULT donné.</span><span class="sxs-lookup"><span data-stu-id="bdfeb-110">[out] The message string associated with the given HRESULT.</span></span>  
  
 `pcchBuffer`  
 <span data-ttu-id="bdfeb-111">[dans, out] La taille de `pwzbuffer` pour éviter les dépassements de mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="bdfeb-111">[in, out] The size of `pwzbuffer` to avoid buffer overruns.</span></span> <span data-ttu-id="bdfeb-112">Si `pwzbuffer` a la valeur null, `pcchBuffer` fournit la taille attendue de `pwzbuffer` pour autoriser la pré-allocation.</span><span class="sxs-lookup"><span data-stu-id="bdfeb-112">If `pwzbuffer` is null, `pcchBuffer` provides the expected size of `pwzbuffer` to allow preallocation.</span></span>  
  
 `iLocaleID`  
 <span data-ttu-id="bdfeb-113">[in] L’identificateur de culture.</span><span class="sxs-lookup"><span data-stu-id="bdfeb-113">[in] The culture identifier.</span></span> <span data-ttu-id="bdfeb-114">Pour utiliser la culture par défaut, vous devez spécifier -1.</span><span class="sxs-lookup"><span data-stu-id="bdfeb-114">To use the default culture, you must specify -1.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bdfeb-115">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="bdfeb-115">Return Value</span></span>  
 <span data-ttu-id="bdfeb-116">Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.</span><span class="sxs-lookup"><span data-stu-id="bdfeb-116">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="bdfeb-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bdfeb-117">HRESULT</span></span>|<span data-ttu-id="bdfeb-118">Description</span><span class="sxs-lookup"><span data-stu-id="bdfeb-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bdfeb-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="bdfeb-119">S_OK</span></span>|<span data-ttu-id="bdfeb-120">La commande s'est correctement terminée.</span><span class="sxs-lookup"><span data-stu-id="bdfeb-120">The method completed successfully.</span></span>|  
|<span data-ttu-id="bdfeb-121">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="bdfeb-121">E_POINTER</span></span>|<span data-ttu-id="bdfeb-122">`pcchBuffer` a la valeur null.</span><span class="sxs-lookup"><span data-stu-id="bdfeb-122">`pcchBuffer` is null.</span></span>|  
|<span data-ttu-id="bdfeb-123">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="bdfeb-123">E_INVALIDARG</span></span>|<span data-ttu-id="bdfeb-124">`pwzBuffer` a la valeur null.</span><span class="sxs-lookup"><span data-stu-id="bdfeb-124">`pwzBuffer` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bdfeb-125">Spécifications</span><span class="sxs-lookup"><span data-stu-id="bdfeb-125">Requirements</span></span>  
 <span data-ttu-id="bdfeb-126">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bdfeb-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bdfeb-127">**En-tête :** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="bdfeb-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="bdfeb-128">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bdfeb-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bdfeb-129">**Versions du .NET framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bdfeb-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdfeb-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bdfeb-130">See Also</span></span>  
 [<span data-ttu-id="bdfeb-131">ICLRRuntimeInfo (Interface)</span><span class="sxs-lookup"><span data-stu-id="bdfeb-131">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [<span data-ttu-id="bdfeb-132">Interfaces d’hébergement</span><span class="sxs-lookup"><span data-stu-id="bdfeb-132">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="bdfeb-133">Hébergement d’applications WPF</span><span class="sxs-lookup"><span data-stu-id="bdfeb-133">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
