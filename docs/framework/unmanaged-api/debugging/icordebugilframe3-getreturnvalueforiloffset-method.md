---
title: "ICorDebugILFrame3::GetReturnValueForILOffset, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- csharp
- vb
api_name: ICorDebugILFrame3.GetReturnValueForILOffset
api_location: mscordbi.dll
api_type: COM
ms.assetid: 06522727-5f64-4391-9331-11386883c352
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c58319de99bdd8d7cce0ea55ccb3140a31a39bd0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilframe3getreturnvalueforiloffset-method"></a>ICorDebugILFrame3::GetReturnValueForILOffset, méthode
Obtient un objet « ICorDebugValue » qui encapsule la valeur de retour d’une fonction.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetReturnValueForILOffset(  
    ULONG32 ILoffset,   
    [out] ICorDebugValue **ppReturnValue  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ILOffset`  
 Offset IL. Consultez la section Notes.  
  
 `ppReturnValue`  
 Pointeur vers l’adresse d’un objet d’interface « ICorDebugValue » qui fournit des informations sur la valeur de retour d’un appel de fonction.  
  
## <a name="remarks"></a>Notes  
 Cette méthode est utilisée avec la [ICorDebugCode3::GetReturnValueLiveOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) méthode pour obtenir la valeur de retour d’une méthode. Il est particulièrement utile dans le cas des méthodes dont les valeurs de retournés sont ignorées, comme dans les exemples de deux fichiers de code suivant. Le premier exemple appelle la <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> (méthode), mais ignore la valeur de retour de la méthode.  
  
 [!code-csharp[Unmanaged.Debugging.MRV#1](../../../../samples/snippets/csharp/VS_Snippets_CLR/unmanaged.debugging.mrv/cs/mrv1.cs#1)]
 [!code-vb[Unmanaged.Debugging.MRV#1](../../../../samples/snippets/visualbasic/VS_Snippets_CLR/unmanaged.debugging.mrv/vb/mrv1.vb#1)]  
  
 Le deuxième exemple illustre un problème beaucoup plus courant dans le débogage. Car une méthode est utilisée en tant qu’argument dans un appel de méthode, sa valeur de retour est accessible uniquement lorsque le débogueur parcourt la méthode appelée. Dans de nombreux cas, en particulier lorsque la méthode appelée est définie dans une bibliothèque externe, qui n’est pas possible.  
  
 [!code-csharp[Unmanaged.Debugging.MRV#2](../../../../samples/snippets/csharp/VS_Snippets_CLR/unmanaged.debugging.mrv/cs/mrv2.cs#2)]
 [!code-vb[Unmanaged.Debugging.MRV#2](../../../../samples/snippets/visualbasic/VS_Snippets_CLR/unmanaged.debugging.mrv/vb/mrv2.vb#2)]  
  
 Si vous passez le [ICorDebugCode3::GetReturnValueLiveOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) méthode un offset à un site d’appel de fonction IL, elle retourne un ou plusieurs des offsets natifs. Le débogueur peut ensuite définir des points d’arrêt sur ces offsets natifs dans la fonction. Lorsque le débogueur atteint un des points d’arrêt, vous pouvez ensuite passer le même offset IL que vous avez passé à cette méthode pour obtenir la valeur de retour. Le débogueur doit puis désactivez tous les points d’arrêt qu’il.  
  
> [!WARNING]
>  Le [icordebugcode3::getreturnvalueliveoffset, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) et `ICorDebugILFrame3::GetReturnValueForILOffset` méthodes permettent d’obtenir des informations de valeur de retour pour les types de référence uniquement. Récupération des informations de valeur de retour dans les types valeur (autrement dit, tous les types qui dérivent de <xref:System.ValueType>) n’est pas pris en charge.  
  
 Offset IL spécifié par le `ILOffset` le paramètre doit être sur un site d’appel de fonction, et le programme débogué doit être arrêté à un point d’arrêt défini à l’offset natif retourné par le [ICorDebugCode3::GetReturnValueLiveOffset](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md) (méthode) pour le même offset IL. Si le programme débogué n’est pas arrêté à l’emplacement correct pour l’offset IL spécifié, l’API échoue.  
  
 Si l’appel de fonction ne retourne aucune valeur, l’API échoue.  
  
 Le `ICorDebugILFrame3::GetReturnValueForILOffset` méthode est disponible uniquement sur x86 et les systèmes AMD64.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [GetReturnValueLiveOffset, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md)  
 [ICorDebugILFrame3, interface](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-interface.md)
