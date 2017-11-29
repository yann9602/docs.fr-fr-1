---
title: "ICorDebugNativeFrame::GetLocalMemoryValue, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugNativeFrame.GetLocalMemoryValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugNativeFrame::GetLocalMemoryValue
helpviewer_keywords:
- GetLocalMemoryValue method [.NET Framework debugging]
- ICorDebugNativeFrame::GetLocalMemoryValue method [.NET Framework debugging]
ms.assetid: b600b3a2-9908-42d8-8093-ab6f39e9a2c9
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a43bc0b4bcfb50804e4bffbe4f4f18280f873436
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugnativeframegetlocalmemoryvalue-method"></a><span data-ttu-id="efddb-102">ICorDebugNativeFrame::GetLocalMemoryValue, méthode</span><span class="sxs-lookup"><span data-stu-id="efddb-102">ICorDebugNativeFrame::GetLocalMemoryValue Method</span></span>
<span data-ttu-id="efddb-103">Obtient la valeur d’un argument ou une variable locale qui est stockée dans l’emplacement de mémoire spécifié pour ce frame natif.</span><span class="sxs-lookup"><span data-stu-id="efddb-103">Gets the value of an argument or local variable that is stored in the specified memory location for this native frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="efddb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="efddb-104">Syntax</span></span>  
  
```  
HRESULT GetLocalMemoryValue (  
    [in]  CORDB_ADDRESS      address,  
    [in]  ULONG              cbSigBlob,  
    [in]  PCCOR_SIGNATURE    pvSigBlob,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="efddb-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="efddb-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="efddb-106">[in] A `CORDB_ADDRESS` valeur qui spécifie l’emplacement de mémoire qui contient la valeur.</span><span class="sxs-lookup"><span data-stu-id="efddb-106">[in] A `CORDB_ADDRESS` value that specifies the memory location containing the value.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="efddb-107">[in] Entier qui spécifie la taille de la signature de métadonnées binaires qui est référencée par le `pvSigBlob` paramètre.</span><span class="sxs-lookup"><span data-stu-id="efddb-107">[in] An integer that specifies the size of the binary metadata signature which is referenced by the `pvSigBlob` parameter.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="efddb-108">[in] A `PCCOR_SIGNATURE` valeur qui pointe vers la signature de métadonnées binaires du type de la valeur.</span><span class="sxs-lookup"><span data-stu-id="efddb-108">[in] A `PCCOR_SIGNATURE` value that points to the binary metadata signature of the value's type.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="efddb-109">[out] Pointeur vers l’adresse d’un objet « ICorDebugValue » représentant la valeur récupérée qui est stockée dans l’emplacement mémoire spécifié.</span><span class="sxs-lookup"><span data-stu-id="efddb-109">[out] A pointer to the address of an "ICorDebugValue" object representing the retrieved value that is stored in the specified memory location.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="efddb-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="efddb-110">Requirements</span></span>  
 <span data-ttu-id="efddb-111">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="efddb-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="efddb-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="efddb-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="efddb-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="efddb-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="efddb-114">**Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="efddb-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efddb-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="efddb-115">See Also</span></span>  
 
