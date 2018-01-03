---
title: "ICorDebugILFrame::GetIP, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugILFrame.GetIP
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugILFrame::GetIP
helpviewer_keywords:
- GetIP method, ICorDebugILFrame interface [.NET Framework debugging]
- ICorDebugILFrame::GetIP method [.NET Framework debugging]
ms.assetid: 18217ba1-1776-4297-a3b9-f77e64b0fead
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 79b18c6fe15e28b2cec07ef9dfaa06ee295ab42d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilframegetip-method"></a>ICorDebugILFrame::GetIP, méthode
Obtient la valeur du pointeur d’instruction et une valeur de la combinaison de bits qui décrit la façon dont la valeur du pointeur d’instruction a été obtenue.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetIP (  
    [out] ULONG32               *pnOffset,   
    [out] CorDebugMappingResult *pMappingResult  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pnOffset`  
 [out] La valeur du pointeur d’instruction.  
  
 `pMappingResult`  
 [out] Pointeur vers une combinaison d’opérations de bits des valeurs d’énumération CorDebugMappingResult qui décrivent comment la valeur du pointeur d’instruction a été obtenue.  
  
## <a name="remarks"></a>Notes  
 La valeur du pointeur d’instruction est l’offset du frame de pile dans le code de la fonction Microsoft intermediate language (MSIL). Si le frame de pile est actif, cette adresse est l’instruction suivante à exécuter. Si le frame de pile n’est pas actif, cette adresse est l’instruction suivante à exécuter lorsque le frame de pile est réactivé.  
  
 Si cette image est un frame de compilé juste-à-temps (JIT), la valeur du pointeur d’instruction sera déterminée en mappant vers l’arrière à partir du pointeur d’instruction natif réel, donc la valeur peut être uniquement approximative.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
