---
title: "ICorProfilerInfo5::SetEventMask2, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: IcorProfilerInfo5.SetEventMask2
api_location: mscorwks.dll
api_type: COM
ms.assetid: 05dbbe2b-049c-4a60-be69-2ad7a949405e
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2cf383ef8100e096b8373b59231d4aef12725c3e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo5seteventmask2-method"></a>ICorProfilerInfo5::SetEventMask2, méthode
[Pris en charge dans .NET Framework 4.5.2 et ultérieur]  
  
 Définit une valeur qui spécifie les types d'événements pour lesquels le profileur veut recevoir des notifications d'événements du CLR (Common Language Runtime). Il fournit davantage de fonctionnalités que le [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) (méthode).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT SetEventMask2(        [in] DWORD dwEventsLow,        [in] DWORD dwEventsHigh  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dwEventsLow`  
 [en entrée] Une valeur de 4 octets qui spécifie les catégories des événements. Chaque bit contrôle une fonctionnalité, un comportement ou un type d'événement différents. Les bits sont décrits dans le [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) énumération.  
  
 `dwEventsHigh`  
 [en entrée] Une valeur de 4 octets qui spécifie les catégories des événements.  Chaque bit contrôle une fonctionnalité, un comportement ou un type d'événement différents. Les bits sont décrits dans le [COR_PRF_HIGH_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) énumération.  
  
## <a name="remarks"></a>Remarques  
 La méthode `SetEventMask2` est utilisée pour définir les rappels auxquels le profileur s'abonne. En général, vous appelez le [GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) méthode pour déterminer les bits définis, effectuer une opération OR logique de ses `pdwEventsLow` et `pdwEventsHigh` valeurs et des nouveaux bits que vous souhaitez définir, puis appelez le `SetEventMask2` (méthode).  
  
 Cette méthode est l’alternative recommandée à la [SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) (méthode).  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Icorprofilerinfo5, Interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)  
 [Geteventmask2, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md)
