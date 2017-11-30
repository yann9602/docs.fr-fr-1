---
title: "ICorDebugCode2::GetCodeChunks, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugCode2.GetCodeChunks
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugCode2::GetCodeChunks
helpviewer_keywords:
- GetCodeChunks method [.NET Framework debugging]
- ICorDebugCode2::GetCodeChunks method [.NET Framework debugging]
ms.assetid: 210a2f02-2678-4555-bc4a-78a0408764c8
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 950fd5c19e8827a63dcf075c42d3e0c18ff91261
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugcode2getcodechunks-method"></a><span data-ttu-id="2c5a2-102">ICorDebugCode2::GetCodeChunks, méthode</span><span class="sxs-lookup"><span data-stu-id="2c5a2-102">ICorDebugCode2::GetCodeChunks Method</span></span>
<span data-ttu-id="2c5a2-103">Obtient les segments de code composée de cet objet de code.</span><span class="sxs-lookup"><span data-stu-id="2c5a2-103">Gets the chunks of code that this code object is composed of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c5a2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2c5a2-104">Syntax</span></span>  
  
```  
HRESULT GetCodeChunks (  
    [in]  ULONG32     cbufSize,  
    [out] ULONG32     *pcnumChunks,  
    [out, size_is(cbufSize), length_is(*pcnumChunks)]   
        CodeChunkInfo chunks[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2c5a2-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2c5a2-105">Parameters</span></span>  
 `cbufSize`  
 <span data-ttu-id="2c5a2-106">[in] Taille de la `chunks` tableau.</span><span class="sxs-lookup"><span data-stu-id="2c5a2-106">[in] Size of the `chunks` array.</span></span>  
  
 `pcnumChunks`  
 <span data-ttu-id="2c5a2-107">[out] Le nombre de segments retournés dans le `chunks` tableau.</span><span class="sxs-lookup"><span data-stu-id="2c5a2-107">[out] The number of chunks returned in the `chunks` array.</span></span>  
  
 `chunks`  
 <span data-ttu-id="2c5a2-108">[out] Un tableau de structures de « CodeChunkInfo », chacune représentant un segment de code unique.</span><span class="sxs-lookup"><span data-stu-id="2c5a2-108">[out] An array of "CodeChunkInfo" structures, each of which represents a single chunk of code.</span></span> <span data-ttu-id="2c5a2-109">Si la valeur de `cbufSize` est 0, ce paramètre peut être null.</span><span class="sxs-lookup"><span data-stu-id="2c5a2-109">If the value of `cbufSize` is 0, this parameter can be null.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2c5a2-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="2c5a2-110">Remarks</span></span>  
 <span data-ttu-id="2c5a2-111">Les segments de code ne se chevaucheront jamais, et ils suivront l’ordre dans lequel ils auraient été concaténés par [ICorDebugCode::GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getcode-method.md).</span><span class="sxs-lookup"><span data-stu-id="2c5a2-111">The code chunks will never overlap, and they will follow the order in which they would have been concatenated by [ICorDebugCode::GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getcode-method.md).</span></span> <span data-ttu-id="2c5a2-112">Un objet de code Microsoft intermediate language (MSIL) dans le .NET Framework version 2.0 comprend un seul segment de code.</span><span class="sxs-lookup"><span data-stu-id="2c5a2-112">A Microsoft intermediate language (MSIL) code object in the .NET Framework version 2.0 will comprise a single code chunk.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c5a2-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="2c5a2-113">Requirements</span></span>  
 <span data-ttu-id="2c5a2-114">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c5a2-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c5a2-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2c5a2-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2c5a2-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2c5a2-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2c5a2-117">**Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c5a2-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c5a2-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2c5a2-118">See Also</span></span>  
 
