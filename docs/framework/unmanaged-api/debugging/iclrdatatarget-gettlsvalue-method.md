---
title: "ICLRDataTarget::GetTLSValue, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDataTarget.GetTLSValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDataTarget::GetTLSValue
helpviewer_keywords:
- GetTLSValue method [.NET Framework debugging]
- ICLRDataTarget::GetTLSValue method [.NET Framework debugging]
ms.assetid: 0d8a7730-edc9-4728-898f-41b219cf5a28
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a820ec7c0a00306266be432a8aceacb3d30d1b4f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="iclrdatatargetgettlsvalue-method"></a><span data-ttu-id="e956b-102">ICLRDataTarget::GetTLSValue, méthode</span><span class="sxs-lookup"><span data-stu-id="e956b-102">ICLRDataTarget::GetTLSValue Method</span></span>
<span data-ttu-id="e956b-103">Obtient une valeur à partir du stockage local des threads (TLS) du thread spécifié dans le processus cible.</span><span class="sxs-lookup"><span data-stu-id="e956b-103">Gets a value from the thread local storage (TLS) of the specified thread in the target process.</span></span> <span data-ttu-id="e956b-104">Cette méthode est appelée par les services d’accès données common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="e956b-104">This method is called by the common language runtime (CLR) data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e956b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e956b-105">Syntax</span></span>  
  
```  
HRESULT GetTLSValue (  
    [in] ULONG32            threadID,  
    [in] ULONG32            index,  
    [out] CLRDATA_ADDRESS   *value  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e956b-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e956b-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="e956b-107">[in] L’identificateur de système d’exploitation d’un thread dans le processus cible.</span><span class="sxs-lookup"><span data-stu-id="e956b-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `index`  
 <span data-ttu-id="e956b-108">[in] Index de l’emplacement.</span><span class="sxs-lookup"><span data-stu-id="e956b-108">[in] The index of the location.</span></span> <span data-ttu-id="e956b-109">Cette valeur doit être un index valide dans le magasin local du thread spécifié.</span><span class="sxs-lookup"><span data-stu-id="e956b-109">This value must be a valid index in the local store of the specified thread.</span></span>  
  
 `value`  
 <span data-ttu-id="e956b-110">[out] Un pointeur vers un `CLRDATA_ADDRESS` valeur qui spécifie la valeur retournée à partir de l’emplacement TLS donné.</span><span class="sxs-lookup"><span data-stu-id="e956b-110">[out] A pointer to a `CLRDATA_ADDRESS` value that specifies the value returned from the given TLS location.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e956b-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="e956b-111">Remarks</span></span>  
 <span data-ttu-id="e956b-112">Cette méthode est implémentée par le writer de l'application de débogage.</span><span class="sxs-lookup"><span data-stu-id="e956b-112">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e956b-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="e956b-113">Requirements</span></span>  
 <span data-ttu-id="e956b-114">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e956b-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e956b-115">**En-tête :** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="e956b-115">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="e956b-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e956b-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e956b-117">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e956b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e956b-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e956b-118">See Also</span></span>  
 [<span data-ttu-id="e956b-119">ICLRDataTarget (Interface)</span><span class="sxs-lookup"><span data-stu-id="e956b-119">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
