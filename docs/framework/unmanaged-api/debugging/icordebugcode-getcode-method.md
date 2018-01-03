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
# <a name="icordebugcodegetcode-method"></a>ICorDebugCode::GetCode, méthode
Obtient tout le code pour la fonction spécifiée, la mise en forme pour le code machine. Cette méthode a été déconseillée dans le .NET Framework version 2.0. Utilisez [ICorDebugCode2::GetCodeChunks](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md) à la place.  
  
## <a name="syntax"></a>Syntaxe  
  
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
  
#### <a name="parameters"></a>Paramètres  
 `startOffset`  
 [in] Le décalage du début de la fonction.  
  
 `endOffset`  
 [in] Le décalage de la fin de la fonction.  
  
 `cBufferAlloc`  
 [in] La taille de la `buffer` de tableau dans lequel le code sera retourné.  
  
 `buffer`  
 [out] Tableau dans lequel le code sera retourné.  
  
 `pcBufferSize`  
 [out] Le nombre d’octets retourné.  
  
## <a name="remarks"></a>Notes  
 Si le code de fonction a été divisé en plusieurs segments, ils sont concaténés dans l’ordre d’augmenter l’offset natif. Limites d’instruction ne sont pas vérifiées.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :** 1.1, 1.0  
  
## <a name="see-also"></a>Voir aussi  
 [GetCodeChunks, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md)  
 
