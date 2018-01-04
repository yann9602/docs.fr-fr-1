---
title: "IManagedObject::GetSerializedBuffer, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IManagedObject.GetSerializedBuffer
api_location: mscoree.dll
api_type: COM
f1_keywords: GetSerializedBuffer
helpviewer_keywords:
- IManagedObject::GetSerializedBuffer method [.NET Framework hosting]
- GetSerializedBuffer method [.NET Framework hosting]
ms.assetid: c17105bb-b49f-434e-8f9b-77f8c85b9220
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d8ae9edab2ca943fc6fb265ab698c2c82d6c531b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="imanagedobjectgetserializedbuffer-method"></a><span data-ttu-id="cbf33-102">IManagedObject::GetSerializedBuffer, méthode</span><span class="sxs-lookup"><span data-stu-id="cbf33-102">IManagedObject::GetSerializedBuffer Method</span></span>
<span data-ttu-id="cbf33-103">Obtient la représentation sous forme de chaîne de cet objet managé.</span><span class="sxs-lookup"><span data-stu-id="cbf33-103">Gets the string representation of this managed object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cbf33-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cbf33-104">Syntax</span></span>  
  
```  
HRESULT GetSerializedBuffer (  
    [out] BSTR *pBSTR  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cbf33-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="cbf33-105">Parameters</span></span>  
 `pBSTR`  
 <span data-ttu-id="cbf33-106">[out] Pointeur vers une chaîne qui est l’objet sérialisé.</span><span class="sxs-lookup"><span data-stu-id="cbf33-106">[out] A pointer to a string that is the serialized object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cbf33-107">Notes</span><span class="sxs-lookup"><span data-stu-id="cbf33-107">Remarks</span></span>  
 <span data-ttu-id="cbf33-108">Le `GetSerializedBuffer` méthode sérialise l’objet afin qu’elle peut être marshalée au client.</span><span class="sxs-lookup"><span data-stu-id="cbf33-108">The `GetSerializedBuffer` method serializes the object so it can be marshaled to the client.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cbf33-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="cbf33-109">Requirements</span></span>  
 <span data-ttu-id="cbf33-110">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cbf33-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cbf33-111">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="cbf33-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cbf33-112">**Bibliothèque :** inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cbf33-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cbf33-113">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cbf33-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbf33-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cbf33-114">See Also</span></span>  
 [<span data-ttu-id="cbf33-115">IManagedObject, interface</span><span class="sxs-lookup"><span data-stu-id="cbf33-115">IManagedObject Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)
