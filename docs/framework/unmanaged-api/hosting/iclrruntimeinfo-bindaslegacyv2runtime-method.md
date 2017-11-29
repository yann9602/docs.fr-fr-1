---
title: "ICLRRuntimeInfo::BindAsLegacyV2Runtime, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeInfo.BindAsLegacyV2Runtime
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRRuntimeInfo::BindAsLegacyV2Runtime
helpviewer_keywords:
- ICLRRuntimeInfo::BindAsLegacyV2Runtime method [.NET Framework hosting]
- BindAsLegacyV2Runtime method [.NET Framework hosting]
ms.assetid: 65fd55ac-4a24-4479-9384-a2e8013bfb2b
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 229c5483c02357054f3d2821d8e024c78887e839
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrruntimeinfobindaslegacyv2runtime-method"></a><span data-ttu-id="9e010-102">ICLRRuntimeInfo::BindAsLegacyV2Runtime, méthode</span><span class="sxs-lookup"><span data-stu-id="9e010-102">ICLRRuntimeInfo::BindAsLegacyV2Runtime Method</span></span>
<span data-ttu-id="9e010-103">Lie l’exécution actuelle pour tous les hérité common language runtime (CLR) version 2 d’activation aux décisions de stratégie.</span><span class="sxs-lookup"><span data-stu-id="9e010-103">Binds the current runtime for all legacy common language runtime (CLR) version 2 activation policy decisions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e010-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9e010-104">Syntax</span></span>  
  
```  
HRESULT BindAsLegacyV2Runtime ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="9e010-105">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="9e010-105">Return Value</span></span>  
 <span data-ttu-id="9e010-106">Cette méthode retourne les HRESULT spécifiques suivants :</span><span class="sxs-lookup"><span data-stu-id="9e010-106">This method returns the following specific HRESULTs:</span></span>  
  
|<span data-ttu-id="9e010-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9e010-107">HRESULT</span></span>|<span data-ttu-id="9e010-108">Description</span><span class="sxs-lookup"><span data-stu-id="9e010-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9e010-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="9e010-109">S_OK</span></span>|<span data-ttu-id="9e010-110">Liaison a réussi, ou cette exécution a déjà été liée en tant que le runtime de stratégie CLR version 2 d’activation hérité.</span><span class="sxs-lookup"><span data-stu-id="9e010-110">Either binding succeeded, or this runtime was already bound as the legacy CLR version 2 activation policy runtime.</span></span>|  
|<span data-ttu-id="9e010-111">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span><span class="sxs-lookup"><span data-stu-id="9e010-111">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span></span>|<span data-ttu-id="9e010-112">Une exécution différente a déjà été liée à la stratégie d’activation 2 de version CLR héritée.</span><span class="sxs-lookup"><span data-stu-id="9e010-112">A different runtime was already bound to the legacy CLR version 2 activation policy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9e010-113">Remarques</span><span class="sxs-lookup"><span data-stu-id="9e010-113">Remarks</span></span>  
 <span data-ttu-id="9e010-114">Si le runtime actuel est déjà lié à toutes les décisions de stratégie CLR version 2 d’activation héritées (par exemple, à l’aide de la `useLegacyV2RuntimeActivationPolicy` de l’attribut le [ \<démarrage > élément](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) dans le fichier de configuration), cette méthode ne retourne pas de résultat d’erreur ; au lieu de cela, le résultat est S_OK, tout comme il le serait si la méthode avait été liée à une stratégie d’activation héritée.</span><span class="sxs-lookup"><span data-stu-id="9e010-114">If the current runtime is already bound for all legacy CLR version 2 activation policy decisions (for example, by using the `useLegacyV2RuntimeActivationPolicy` attribute on the [\<startup> element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) in the configuration file), this method does not return an error result; instead, the result is S_OK, just as it would be if the method had successfully bound legacy activation policy.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e010-115">Spécifications</span><span class="sxs-lookup"><span data-stu-id="9e010-115">Requirements</span></span>  
 <span data-ttu-id="9e010-116">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9e010-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e010-117">**En-tête :** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="9e010-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="9e010-118">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9e010-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9e010-119">**Versions du .NET framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e010-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e010-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9e010-120">See Also</span></span>  
 [<span data-ttu-id="9e010-121">ICLRRuntimeInfo (Interface)</span><span class="sxs-lookup"><span data-stu-id="9e010-121">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [<span data-ttu-id="9e010-122">Interfaces d’hébergement</span><span class="sxs-lookup"><span data-stu-id="9e010-122">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="9e010-123">Hébergement d’applications WPF</span><span class="sxs-lookup"><span data-stu-id="9e010-123">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)  
 [<span data-ttu-id="9e010-124">\<démarrage > élément</span><span class="sxs-lookup"><span data-stu-id="9e010-124">\<startup> Element</span></span>](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)
