---
title: "ICorDebugCode::GetCode, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugCode.GetCode
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugCode::GetCode
helpviewer_keywords:
- ICorDebugCode::GetCode method [.NET Framework debugging]
- GetCode method, ICorDebugCode interface [.NET Framework debugging]
ms.assetid: 7137e3d1-1dad-48d8-8c37-16ac816534d3
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f906fddf8073a00d2a3741613aae537b8604af67
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcodegetcode-method"></a><span data-ttu-id="be807-102">ICorDebugCode::GetCode, méthode</span><span class="sxs-lookup"><span data-stu-id="be807-102">ICorDebugCode::GetCode Method</span></span>
<span data-ttu-id="be807-103">Obtient tout le code pour la fonction spécifiée, la mise en forme pour le code machine.</span><span class="sxs-lookup"><span data-stu-id="be807-103">Gets all the code for the specified function, formatted for disassembly.</span></span> <span data-ttu-id="be807-104">Cette méthode a été déconseillée dans le .NET Framework version 2.0.</span><span class="sxs-lookup"><span data-stu-id="be807-104">This method has been deprecated in the .NET Framework version 2.0.</span></span> <span data-ttu-id="be807-105">Utilisez [ICorDebugCode2::GetCodeChunks](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md) à la place.</span><span class="sxs-lookup"><span data-stu-id="be807-105">Use [ICorDebugCode2::GetCodeChunks](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be807-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="be807-106">Syntax</span></span>  
  
```  
HRESULT GetCode (  
    [in] ULONG32     startOffset,   
    [in] ULONG32     endOffset,  
    [in] ULONG32     cBufferAlloc,  
    [out, size_is(cBufferAlloc),  
        length_is(*pcBufferSize)] BYTE buffer[],  
    [out] ULONG32    *pcBufferSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="be807-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="be807-107">Parameters</span></span>  
 `startOffset`  
 <span data-ttu-id="be807-108">[in] Le décalage du début de la fonction.</span><span class="sxs-lookup"><span data-stu-id="be807-108">[in] The offset of the beginning of the function.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="be807-109">[in] Le décalage de la fin de la fonction.</span><span class="sxs-lookup"><span data-stu-id="be807-109">[in] The offset of the end of the function.</span></span>  
  
 `cBufferAlloc`  
 <span data-ttu-id="be807-110">[in] La taille de la `buffer` de tableau dans lequel le code sera retourné.</span><span class="sxs-lookup"><span data-stu-id="be807-110">[in] The size of the `buffer` array into which the code will be returned.</span></span>  
  
 `buffer`  
 <span data-ttu-id="be807-111">[out] Tableau dans lequel le code sera retourné.</span><span class="sxs-lookup"><span data-stu-id="be807-111">[out] The array into which the code will be returned.</span></span>  
  
 `pcBufferSize`  
 <span data-ttu-id="be807-112">[out] Le nombre d’octets retourné.</span><span class="sxs-lookup"><span data-stu-id="be807-112">[out] The number of bytes returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="be807-113">Notes</span><span class="sxs-lookup"><span data-stu-id="be807-113">Remarks</span></span>  
 <span data-ttu-id="be807-114">Si le code de fonction a été divisé en plusieurs segments, ils sont concaténés dans l’ordre d’augmenter l’offset natif.</span><span class="sxs-lookup"><span data-stu-id="be807-114">If the function's code has been divided into multiple chunks, they are concatenated in order of increasing native offset.</span></span> <span data-ttu-id="be807-115">Limites d’instruction ne sont pas vérifiées.</span><span class="sxs-lookup"><span data-stu-id="be807-115">Instruction boundaries are not checked.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be807-116">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="be807-116">Requirements</span></span>  
 <span data-ttu-id="be807-117">**Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="be807-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be807-118">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="be807-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="be807-119">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="be807-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="be807-120">**Versions du .NET framework :** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="be807-120">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be807-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="be807-121">See Also</span></span>  
 [<span data-ttu-id="be807-122">GetCodeChunks, méthode</span><span class="sxs-lookup"><span data-stu-id="be807-122">GetCodeChunks Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md)  
 
