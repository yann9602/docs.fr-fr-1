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
# <a name="icordebugcode2getcodechunks-method"></a>ICorDebugCode2::GetCodeChunks, méthode
Obtient les segments de code composée de cet objet de code.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetCodeChunks (  
    [in]  ULONG32     cbufSize,  
    [out] ULONG32     *pcnumChunks,  
    [out, size_is(cbufSize), length_is(*pcnumChunks)]   
        CodeChunkInfo chunks[]  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `cbufSize`  
 [in] Taille de la `chunks` tableau.  
  
 `pcnumChunks`  
 [out] Le nombre de segments retournés dans le `chunks` tableau.  
  
 `chunks`  
 [out] Un tableau de structures de « CodeChunkInfo », chacune représentant un segment de code unique. Si la valeur de `cbufSize` est 0, ce paramètre peut être null.  
  
## <a name="remarks"></a>Remarques  
 Les segments de code ne se chevaucheront jamais, et ils suivront l’ordre dans lequel ils auraient été concaténés par [ICorDebugCode::GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getcode-method.md). Un objet de code Microsoft intermediate language (MSIL) dans le .NET Framework version 2.0 comprend un seul segment de code.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 
