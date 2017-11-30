---
title: "ICorDebugILCode2::GetLocalVarSigToken, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: ICorDebugILCode2.GetLocalVarSigToken
api_location: mscordbi.dll
api_type: COM
ms.assetid: 17665b77-1342-4115-94fd-9f45b0ecfb0f
topic_type: apiref
caps.latest.revision: "3"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2d41b60e5fb528dfba0f7fa82d7792a1f08ba915
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugilcode2getlocalvarsigtoken-method"></a><span data-ttu-id="1026b-102">ICorDebugILCode2::GetLocalVarSigToken, méthode</span><span class="sxs-lookup"><span data-stu-id="1026b-102">ICorDebugILCode2::GetLocalVarSigToken Method</span></span>
<span data-ttu-id="1026b-103">[Pris en charge dans .NET Framework 4.5.2 et ultérieur]</span><span class="sxs-lookup"><span data-stu-id="1026b-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="1026b-104">Obtient le jeton de métadonnées de la signature de variable locale pour la fonction représentée par cette instance.</span><span class="sxs-lookup"><span data-stu-id="1026b-104">Gets the metadata token for the local variable signature for the function that is represented by this instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1026b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1026b-105">Syntax</span></span>  
  
```cpp
HRESULT GetLocalVarSigToken(  
   [out] mdSignature *pmdSig  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1026b-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1026b-106">Parameters</span></span>  
 `pmdSig`  
 <span data-ttu-id="1026b-107">[en sortie] Un pointeur vers le jeton `mdSignature` pour la signature de variable globale pour cette fonction, ou `mdSignatureNil` s'il n'y a pas de signature (c'est-à-dire si la fonction n'a aucune variable locale).</span><span class="sxs-lookup"><span data-stu-id="1026b-107">[out] A pointer to the `mdSignature` token for the local variable signature for this function, or `mdSignatureNil` if there is no signature (that is, if the function doesn't have any local variables).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1026b-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="1026b-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1026b-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="1026b-109">Requirements</span></span>  
 <span data-ttu-id="1026b-110">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1026b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1026b-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1026b-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1026b-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1026b-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1026b-113">**Versions du .NET framework :**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1026b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1026b-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1026b-114">See Also</span></span>  
 [<span data-ttu-id="1026b-115">Icordebugilcode2, Interface</span><span class="sxs-lookup"><span data-stu-id="1026b-115">ICorDebugILCode2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-interface.md)  
 [<span data-ttu-id="1026b-116">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="1026b-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
