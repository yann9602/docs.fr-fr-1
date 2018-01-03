---
title: "ICorDebugHeapValue3::GetMonitorEventWaitList, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugHeapValue3.GetMonitorEventWaitList
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugHeapValue3::GetMonitorEventWaitList
helpviewer_keywords:
- ICorDebugHeapValue3::GetMonitorEventWaitList method [.NET Framework debugging]
- GetMonitorEventWaitList method [.NET Framework debugging]
ms.assetid: 035a9035-ac66-4953-b48a-99652b42b7fe
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a4112188ff069184cab998f5bbd0fc70d1ce7dc9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugheapvalue3getmonitoreventwaitlist-method"></a>ICorDebugHeapValue3::GetMonitorEventWaitList, méthode
Fournit une liste triée de threads en attente sur l’événement qui est associé à un verrou du moniteur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetMonitorEventWaitList (  
    [out] ICorDebugThreadEnum **ppThreadEnum  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppThreadEnum`  
 [out] L’énumérateur ICorDebugThreadEnum qui fournit la liste triée de threads.  
  
## <a name="return-value"></a>Valeur de retour  
 Cette méthode retourne les HRESULT spécifiques suivants ainsi que les erreurs HRESULT indiquant l'échec de la méthode.  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|The list is not empty.|  
|S_FALSE|La liste est vide.|  
  
## <a name="exceptions"></a>Exceptions  
  
## <a name="remarks"></a>Notes  
 Le premier thread dans la liste est le premier thread qui est libéré par l’appel suivant à <xref:System.Threading.Monitor.Pulse%28System.Object%29?displayProperty=nameWithType>. Le thread suivant dans la liste est publié sur l’appel suivant et ainsi de suite.  
  
 Si la liste n’est pas vide, cette méthode retourne S_OK. Si la liste est vide, la méthode retourne S_FALSE ; Dans ce cas, l’énumération est toujours valide, même s’il est vide.  
  
 Dans les deux cas, l’interface d’énumération est utilisable uniquement pour la durée de l’état synchronisé actuel. Toutefois, les interfaces du thread distribuées à partir de celle-ci sont valides jusqu'à ce que le thread se ferme.  
  
 Si `ppThreadEnum` n’est pas un pointeur valid, le résultat est indéfini.  
  
 Si une erreur se produit et il ne peut pas déterminer qui, le cas échéant, les threads sont en attente pour l’analyse, la méthode retourne un HRESULT qui indique un échec.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Débogage](../../../../docs/framework/unmanaged-api/debugging/index.md)
