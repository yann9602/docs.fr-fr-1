---
title: Fonction PreBindAssemblyEx
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: PreBindAssemblyEx
api_location: fusion.dll
api_type: DLLExport
f1_keywords: PreBindAssemblyEx
helpviewer_keywords: PreBindAssemblyEx function [.NET Framework fusion]
ms.assetid: bd285233-a4a2-4b52-bbca-0025a60e4864
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 05977db8e01d00af6e160cb2993867cf83eb24c1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="prebindassemblyex-function"></a><span data-ttu-id="05f3d-102">Fonction PreBindAssemblyEx</span><span class="sxs-lookup"><span data-stu-id="05f3d-102">PreBindAssemblyEx Function</span></span>
<span data-ttu-id="05f3d-103">Obtient le nom complet de post-stratégie pour un assembly.</span><span class="sxs-lookup"><span data-stu-id="05f3d-103">Gets the post-policy display name for an assembly.</span></span>  
  
 <span data-ttu-id="05f3d-104">Cette fonction prend en charge l’infrastructure .NET Framework et n’est pas destinée à être utilisée directement depuis votre code.</span><span class="sxs-lookup"><span data-stu-id="05f3d-104">This function supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05f3d-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="05f3d-105">Syntax</span></span>  
  
```  
HRESULT PreBindAssemblyEx (  
    [in]  IApplicationContext *pAppCtx,  
    [in]  IAssemblyName       *pName,  
    [in]  IAssembly           *pAsmParent,  
    [in]  LPCWSTR             pwzRuntimeVersion,  
    [out] IAssemblyName       **ppNamePostPolicy,  
    [in]  LPVOID              pvReserved  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="05f3d-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="05f3d-106">Parameters</span></span>  
 `pAppCtx`  
 <span data-ttu-id="05f3d-107">[in] Identifie le contexte d’application.</span><span class="sxs-lookup"><span data-stu-id="05f3d-107">[in] Identifies the application context.</span></span>  
  
 `pName`  
 <span data-ttu-id="05f3d-108">[in] Identifie le nom de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="05f3d-108">[in] Identifies the assembly name.</span></span>  
  
 `pAsmParent`  
 <span data-ttu-id="05f3d-109">[in] Identifie l’assembly parent.</span><span class="sxs-lookup"><span data-stu-id="05f3d-109">[in] Identifies the parent assembly.</span></span> <span data-ttu-id="05f3d-110">Ce paramètre est ignoré.</span><span class="sxs-lookup"><span data-stu-id="05f3d-110">This parameter is ignored.</span></span>  
  
 `pwzRuntimeVersion`  
 <span data-ttu-id="05f3d-111">[in] Identifie la version du runtime.</span><span class="sxs-lookup"><span data-stu-id="05f3d-111">[in] Identifies the runtime version.</span></span>  
  
 `ppNamePostPolicy`  
 <span data-ttu-id="05f3d-112">[out] Contient le nom complet de post-stratégie.</span><span class="sxs-lookup"><span data-stu-id="05f3d-112">[out] Contains the post-policy display name.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="05f3d-113">[in] Réservé pour une future extensibilité.</span><span class="sxs-lookup"><span data-stu-id="05f3d-113">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="05f3d-114">`pvReserved`doit être une référence null.</span><span class="sxs-lookup"><span data-stu-id="05f3d-114">`pvReserved` must be a null reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="05f3d-115">Notes</span><span class="sxs-lookup"><span data-stu-id="05f3d-115">Remarks</span></span>  
 <span data-ttu-id="05f3d-116">Le `ppNamePostPolicy` paramètre de sortie est défini uniquement si la fonction retourne HRESULT FUSION_E_REF_DEF_MISMATCH.</span><span class="sxs-lookup"><span data-stu-id="05f3d-116">The `ppNamePostPolicy` output parameter is set only if the function returns HRESULT FUSION_E_REF_DEF_MISMATCH.</span></span> <span data-ttu-id="05f3d-117">Sinon, elle a la valeur null.</span><span class="sxs-lookup"><span data-stu-id="05f3d-117">Otherwise, it is null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05f3d-118">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="05f3d-118">Requirements</span></span>  
 <span data-ttu-id="05f3d-119">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05f3d-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05f3d-120">**En-tête :** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="05f3d-120">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="05f3d-121">**Bibliothèque :** inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="05f3d-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="05f3d-122">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05f3d-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05f3d-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="05f3d-123">See Also</span></span>  
 [<span data-ttu-id="05f3d-124">Fonctions statiques globales de fusion</span><span class="sxs-lookup"><span data-stu-id="05f3d-124">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
