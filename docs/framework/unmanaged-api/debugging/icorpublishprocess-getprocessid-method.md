---
title: "ICorPublishProcess::GetProcessID, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorPublishProcess.GetProcessID
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorPublishProcess::GetProcessID
helpviewer_keywords:
- ICorPublishProcess::GetProcessID method [.NET Framework debugging]
- GetProcessID method [.NET Framework debugging]
ms.assetid: f31185e0-f01d-463a-b392-42163e39bfe9
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bb785c84436e2b0c6848c8af2540e8efada38e6f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icorpublishprocessgetprocessid-method"></a><span data-ttu-id="42dcf-102">ICorPublishProcess::GetProcessID, méthode</span><span class="sxs-lookup"><span data-stu-id="42dcf-102">ICorPublishProcess::GetProcessID Method</span></span>
<span data-ttu-id="42dcf-103">Obtient l’identificateur de système d’exploitation de ce processus.</span><span class="sxs-lookup"><span data-stu-id="42dcf-103">Gets the operating system identifier for this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42dcf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="42dcf-104">Syntax</span></span>  
  
```  
HRESULT GetProcessID (  
    [out] unsigned   *pid  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="42dcf-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="42dcf-105">Parameters</span></span>  
 `pid`  
 <span data-ttu-id="42dcf-106">[out] Un pointeur vers l’identificateur du processus représenté par ce [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) objet.</span><span class="sxs-lookup"><span data-stu-id="42dcf-106">[out] A pointer to the identifier of the process represented by this [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42dcf-107">Spécifications</span><span class="sxs-lookup"><span data-stu-id="42dcf-107">Requirements</span></span>  
 <span data-ttu-id="42dcf-108">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="42dcf-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42dcf-109">**En-tête :** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="42dcf-109">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="42dcf-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="42dcf-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="42dcf-111">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42dcf-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42dcf-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="42dcf-112">See Also</span></span>  
 [<span data-ttu-id="42dcf-113">ICorPublishProcess (Interface)</span><span class="sxs-lookup"><span data-stu-id="42dcf-113">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)
