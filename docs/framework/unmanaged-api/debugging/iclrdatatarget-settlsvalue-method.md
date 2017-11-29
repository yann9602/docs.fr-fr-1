---
title: "ICLRDataTarget::SetTLSValue, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDataTarget.SetTLSValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDataTarget::SetTLSValue
helpviewer_keywords:
- ICLRDataTarget::SetTLSValue method [.NET Framework debugging]
- SetTLSValue method [.NET Framework debugging]
ms.assetid: 4a2d6a24-749a-47ad-9f01-4517203d3f35
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 75c9d25b496e300d66844e3fd88655ab38da4b0e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="iclrdatatargetsettlsvalue-method"></a><span data-ttu-id="42c80-102">ICLRDataTarget::SetTLSValue, méthode</span><span class="sxs-lookup"><span data-stu-id="42c80-102">ICLRDataTarget::SetTLSValue Method</span></span>
<span data-ttu-id="42c80-103">Définit une valeur dans le stockage local des threads (TLS) du thread spécifié dans le processus cible.</span><span class="sxs-lookup"><span data-stu-id="42c80-103">Sets a value in the thread local storage (TLS) of the specified thread in the target process.</span></span> <span data-ttu-id="42c80-104">Cette méthode est appelée par les services d’accès données common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="42c80-104">This method is called by the common language runtime (CLR) data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42c80-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="42c80-105">Syntax</span></span>  
  
```  
HRESULT SetTLSValue (  
    [in] ULONG32            threadID,  
    [in] ULONG32            index,  
    [in] CLRDATA_ADDRESS    value  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="42c80-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="42c80-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="42c80-107">[in] L’identificateur de système d’exploitation d’un thread dans le processus cible.</span><span class="sxs-lookup"><span data-stu-id="42c80-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `index`  
 <span data-ttu-id="42c80-108">[in] Index de l’emplacement.</span><span class="sxs-lookup"><span data-stu-id="42c80-108">[in] The index of the location.</span></span> <span data-ttu-id="42c80-109">Cette valeur doit être un index valide dans le magasin local du thread spécifié.</span><span class="sxs-lookup"><span data-stu-id="42c80-109">This value must be a valid index in the local store of the specified thread.</span></span>  
  
 `value`  
 <span data-ttu-id="42c80-110">[in] A `CLRDATA_ADDRESS` valeur qui spécifie la valeur à placer dans l’emplacement de TLS donné.</span><span class="sxs-lookup"><span data-stu-id="42c80-110">[in] A `CLRDATA_ADDRESS` value that specifies the value to place in the given TLS location.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="42c80-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="42c80-111">Remarks</span></span>  
 <span data-ttu-id="42c80-112">Cette méthode est implémentée par le writer de l'application de débogage.</span><span class="sxs-lookup"><span data-stu-id="42c80-112">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42c80-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="42c80-113">Requirements</span></span>  
 <span data-ttu-id="42c80-114">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="42c80-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42c80-115">**En-tête :** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="42c80-115">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="42c80-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="42c80-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="42c80-117">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42c80-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42c80-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="42c80-118">See Also</span></span>  
 [<span data-ttu-id="42c80-119">ICLRDataTarget (Interface)</span><span class="sxs-lookup"><span data-stu-id="42c80-119">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
