---
title: "ICorDebugCode3::GetReturnValueLiveOffset, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: ICorDebugCode3.GetReturnValueLiveOffset
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugCode3::GetReturnValueLiveOffset
helpviewer_keywords:
- ICorDebugCode3::GetReturnValueLiveOffset method [.NET Framework debugging]
- GetReturnValueLiveOffset method [.NET Framework debugging]
ms.assetid: 8c2ff5d8-8c04-4423-b1e1-e1c8764b36d3
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4516f2244b72bd4f254c5090b09d6d90579f1ae6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugcode3getreturnvalueliveoffset-method"></a>ICorDebugCode3::GetReturnValueLiveOffset, méthode
Pour un offset IL spécifié, obtient les offsets natifs où un point d’arrêt doit être placé afin que le débogueur peut obtenir la valeur de retour d’une fonction.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetReturnValueLiveOffset(  
    [in] ULONG32 ILoffset,  
    [in] ULONG32 bufferSize,   
    [out] ULONG32 *pFetched,   
    [out, size_is(buffersize), length_is(*pFetched)] ULong32 pOffsets[]  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ILoffset`  
 Offset IL. Il doit être un site d’appel de fonction ou l’appel de fonction échoue.  
  
 `bufferSize`  
 Le nombre d’octets disponibles pour stocker les `pOffsets`.  
  
 `pFetched`  
 Pointeur vers le nombre de décalages réellement retournés. En règle générale, sa valeur est 1, mais une seule instruction de langage intermédiaire peut mapper à plusieurs `CALL` instructions assembleur.  
  
 `pOffsets`  
 Tableau d’offsets natifs. En règle générale, `pOffsets` contient un offset unique, bien qu’une seule instruction de langage intermédiaire peut mapper à une carte plusieurs à plusieurs `CALL` instructions assembleur.  
  
## <a name="remarks"></a>Remarques  
 Cette méthode est utilisée avec la [ICorDebugILFrame3::GetReturnValueForILOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md) méthode pour obtenir la valeur de retour d’une méthode qui retourne un type référence. En passant un IL décalage à un site d’appel de fonction à cette méthode retourne un ou plusieurs des offsets natifs. Le débogueur peut ensuite définir des points d’arrêt sur ces offsets natifs dans la fonction. Lorsque le débogueur atteint un des points d’arrêt, vous pouvez ensuite passer le même offset IL que vous avez passé à cette méthode pour le [ICorDebugILFrame3::GetReturnValueForILOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md) méthode pour obtenir la valeur de retour. Le débogueur doit puis désactivez tous les points d’arrêt qu’il.  
  
> [!WARNING]
>  Le `ICorDebugCode3::GetReturnValueLiveOffset` et [ICorDebugILFrame3::GetReturnValueForILOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md) méthodes permettent d’obtenir des informations de valeur de retour pour les types de référence uniquement. Récupération des informations de valeur de retour dans les types valeur (autrement dit, tous les types qui dérivent de <xref:System.ValueType>) n’est pas pris en charge.  
  
 La fonction retourne le `HRESULT` valeurs indiquées dans le tableau suivant.  
  
|Valeur `HRESULT`|Description|  
|---------------------|-----------------|  
|`S_OK`|Opération réussie.|  
|`CORDBG_E_INVALID_OPCODE`|Le site offset IL donné n’est pas une instruction d’appel ou de la fonction retourne `void`.|  
|`CORDBG_E_UNSUPPORTED`|L’offset IL donné est un appel approprié, mais le type de retour non pris en charge pour l’obtention d’une valeur de retour.|  
  
 Le `ICorDebugCode3::GetReturnValueLiveOffset` méthode est disponible uniquement sur x86 et les systèmes AMD64.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Getreturnvalueforiloffset, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md)  
 [Icordebugcode3, Interface](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)
