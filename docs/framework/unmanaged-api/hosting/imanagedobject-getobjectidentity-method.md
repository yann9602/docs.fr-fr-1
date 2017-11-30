---
title: "IManagedObject::GetObjectIdentity, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IManagedObject.GetObjectIdentity
api_location: mscoree.dll
api_type: COM
f1_keywords: GetObjectIdentity
helpviewer_keywords:
- GetObjectIdentity method [.NET Framework hosting]
- IManagedObject::GetObjectIdentity method [.NET Framework hosting]
ms.assetid: b862ff3e-e480-4cdf-84e2-e1013334a467
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7c0dabfca147b203c3bcf93a362e6670ae295338
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="imanagedobjectgetobjectidentity-method"></a><span data-ttu-id="c8ab3-102">IManagedObject::GetObjectIdentity, méthode</span><span class="sxs-lookup"><span data-stu-id="c8ab3-102">IManagedObject::GetObjectIdentity Method</span></span>
<span data-ttu-id="c8ab3-103">Obtient l’identité de cet objet managé.</span><span class="sxs-lookup"><span data-stu-id="c8ab3-103">Gets the identity of this managed object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8ab3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c8ab3-104">Syntax</span></span>  
  
```  
HRESULT GetObjectIdentity (  
    [out] BSTR*   pBSTRGUID,  
    [out] int*    AppDomainID,  
    [out] CCW_PTR pCCW  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c8ab3-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c8ab3-105">Parameters</span></span>  
 `pBSTRGUID`  
 <span data-ttu-id="c8ab3-106">[out] Pointeur vers le GUID du processus dans lequel réside l’objet.</span><span class="sxs-lookup"><span data-stu-id="c8ab3-106">[out] A pointer to the GUID of the process in which the object resides.</span></span>  
  
 `AppDomainID`  
 <span data-ttu-id="c8ab3-107">[out] Pointeur vers l’ID de l’objet domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="c8ab3-107">[out] A pointer to the ID of the object's application domain.</span></span>  
  
 `pCCW`  
 <span data-ttu-id="c8ab3-108">[out] Pointeur vers l’index de l’objet dans la v-table classique COM.</span><span class="sxs-lookup"><span data-stu-id="c8ab3-108">[out] A pointer to object's index in the COM classic v-table.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c8ab3-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="c8ab3-109">Remarks</span></span>  
 <span data-ttu-id="c8ab3-110">L’identité d’un objet managé inclut des ID de domaine d’application, des processus GUID et des index de l’objet dans la v-table classique COM.</span><span class="sxs-lookup"><span data-stu-id="c8ab3-110">The identity of a managed object includes process GUID, application domain ID, and the object's index in the COM classic v-table.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8ab3-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="c8ab3-111">Requirements</span></span>  
 <span data-ttu-id="c8ab3-112">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c8ab3-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8ab3-113">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c8ab3-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c8ab3-114">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c8ab3-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c8ab3-115">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8ab3-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8ab3-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c8ab3-116">See Also</span></span>  
 [<span data-ttu-id="c8ab3-117">IManagedObject (Interface)</span><span class="sxs-lookup"><span data-stu-id="c8ab3-117">IManagedObject Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)
