---
title: "IInstallReferenceEnum::GetNextInstallReferenceItem, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IInstallReferenceEnum.GetNextInstallReferenceItem
api_location: fusion.dll
api_type: COM
f1_keywords: IInstallReferenceEnum::GetNextInstallReferenceItem
helpviewer_keywords:
- IInstallReferenceEnum::GetNextInstallReferenceItem method [.NET Framework fusion]
- GetNextInstallReferenceItem method [.NET Framework fusion]
ms.assetid: ce969c9d-6538-4c34-8784-148ffd99fe7a
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0f3a1b745c3ee28c126e328b1a3fa9e283f98d99
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="iinstallreferenceenumgetnextinstallreferenceitem-method"></a><span data-ttu-id="1c23a-102">IInstallReferenceEnum::GetNextInstallReferenceItem, méthode</span><span class="sxs-lookup"><span data-stu-id="1c23a-102">IInstallReferenceEnum::GetNextInstallReferenceItem Method</span></span>
<span data-ttu-id="1c23a-103">Obtient un pointeur vers la prochaine [IInstallReferenceItem](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md) objet contenu dans ce [IInstallReferenceEnum](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md) objet.</span><span class="sxs-lookup"><span data-stu-id="1c23a-103">Gets a pointer to the next [IInstallReferenceItem](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md) object contained in this [IInstallReferenceEnum](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c23a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1c23a-104">Syntax</span></span>  
  
```  
HRESULT GetNextInstallReferenceItem (  
    [out] IInstallReferenceItem **ppRefItem,  
    [in]  DWORD dwFlags,  
    [in]  LPVOID pvReserved  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1c23a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1c23a-105">Parameters</span></span>  
 `ppRefItem`  
 <span data-ttu-id="1c23a-106">[out] Retourné `IInstallReferenceItem` pointeur.</span><span class="sxs-lookup"><span data-stu-id="1c23a-106">[out] The returned `IInstallReferenceItem` pointer.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="1c23a-107">[in] Réservé pour une future extensibilité.</span><span class="sxs-lookup"><span data-stu-id="1c23a-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="1c23a-108">`dwFlags`doit être 0 (zéro).</span><span class="sxs-lookup"><span data-stu-id="1c23a-108">`dwFlags` must be 0 (zero).</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="1c23a-109">[in] Réservé pour une future extensibilité.</span><span class="sxs-lookup"><span data-stu-id="1c23a-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="1c23a-110">`pvReserved`doit être une référence null.</span><span class="sxs-lookup"><span data-stu-id="1c23a-110">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c23a-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="1c23a-111">Requirements</span></span>  
 <span data-ttu-id="1c23a-112">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1c23a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c23a-113">**En-tête :** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="1c23a-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="1c23a-114">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c23a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c23a-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1c23a-115">See Also</span></span>  
 [<span data-ttu-id="1c23a-116">IInstallReferenceItem, interface</span><span class="sxs-lookup"><span data-stu-id="1c23a-116">IInstallReferenceItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md)  
 [<span data-ttu-id="1c23a-117">IInstallReferenceEnum, interface</span><span class="sxs-lookup"><span data-stu-id="1c23a-117">IInstallReferenceEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md)
