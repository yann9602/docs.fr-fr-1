---
title: "ICorDebugVariableHome::GetSlotIndex (méthode)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name: ICorDebugVariableHome.GetSlotIndex
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugVariableHome::GetSlotIndex
helpviewer_keywords:
- ICorDebugVariableHome::GetSlotIndex method [.NET Framework debugging]
- GetSlotIndex method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: 966da50d-5665-4fff-bf7b-1c72bbadd9a4
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3eb8ed980fd523d0b0d29fbef770652a1d96146f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugvariablehomegetslotindex-method"></a>ICorDebugVariableHome::GetSlotIndex (méthode)
Obtient l’index d’emplacement géré d’une variable locale.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetSlotIndex(  
    [out] ULONG32 *pSlotIndex  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pSlotIndex`  
 [out] Pointeur vers l’index d’emplacement d’une variable locale.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode retourne les valeurs suivantes.  
  
|Valeur|Description|  
|-----------|-----------------|  
|`S_OK`|L’appel de méthode a retourné une valeur de l’index de l’emplacement dans `pSlotIndex`.|  
|`E_FAIL`|En cours [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instance représente un argument de fonction.|  
  
## <a name="remarks"></a>Remarques  
 L’index d’emplacement peut être utilisé pour récupérer les métadonnées pour cette variable locale.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Interface de ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
