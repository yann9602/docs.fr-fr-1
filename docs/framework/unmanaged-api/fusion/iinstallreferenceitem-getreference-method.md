---
title: "IInstallReferenceItem::GetReference, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IInstallReferenceItem.GetReference
api_location: fusion.dll
api_type: COM
f1_keywords: IInstallReferenceItem::GetReference
helpviewer_keywords:
- IInstallReferenceItem::GetReference method [.NET Framework fusion]
- GetReference method [.NET Framework fusion]
ms.assetid: 8960332f-c98a-405a-ba92-7003de0c1187
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: de21e9b0d224ec417eeb50f8de5c33411d0dadb2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="iinstallreferenceitemgetreference-method"></a><span data-ttu-id="f738b-102">IInstallReferenceItem::GetReference, méthode</span><span class="sxs-lookup"><span data-stu-id="f738b-102">IInstallReferenceItem::GetReference Method</span></span>
<span data-ttu-id="f738b-103">Obtient un pointeur vers le [FUSION_INSTALL_REFERENCE](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md) structure représentée par ce [IInstallReferenceItem](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md) objet.</span><span class="sxs-lookup"><span data-stu-id="f738b-103">Gets a pointer to the [FUSION_INSTALL_REFERENCE](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md) structure represented by this [IInstallReferenceItem](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f738b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f738b-104">Syntax</span></span>  
  
```  
HRESULT GetReference (  
    [out] LPFUSION_INSTALL_REFERENCE *ppRefData,  
    [in]  DWORD dwFlags,  
    [in]  LPVOID pvReserved  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f738b-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f738b-105">Parameters</span></span>  
 `ppRefData`  
 <span data-ttu-id="f738b-106">[out] Retourné `FUSION_INSTALL_REFERENCE` pointeur.</span><span class="sxs-lookup"><span data-stu-id="f738b-106">[out] The returned `FUSION_INSTALL_REFERENCE` pointer.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="f738b-107">[in] Réservé pour une future extensibilité.</span><span class="sxs-lookup"><span data-stu-id="f738b-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="f738b-108">`dwFlags`doit être 0 (zéro).</span><span class="sxs-lookup"><span data-stu-id="f738b-108">`dwFlags` must be 0 (zero).</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="f738b-109">[in] Réservé pour une future extensibilité.</span><span class="sxs-lookup"><span data-stu-id="f738b-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="f738b-110">`pvReserved`doit être une référence null.</span><span class="sxs-lookup"><span data-stu-id="f738b-110">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f738b-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f738b-111">Requirements</span></span>  
 <span data-ttu-id="f738b-112">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f738b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f738b-113">**En-tête :** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="f738b-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="f738b-114">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f738b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f738b-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f738b-115">See Also</span></span>  
 [<span data-ttu-id="f738b-116">IInstallReferenceItem, interface</span><span class="sxs-lookup"><span data-stu-id="f738b-116">IInstallReferenceItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md)  
 [<span data-ttu-id="f738b-117">FUSION_INSTALL_REFERENCE, structure</span><span class="sxs-lookup"><span data-stu-id="f738b-117">FUSION_INSTALL_REFERENCE Structure</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md)
