---
title: ICorProfilerCallback6, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback6
api_location:
- mscorwks.dll
- corprof.idl
api_type: COM
ms.assetid: edc420b7-96d1-4dec-ace0-36d907f644bc
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: dca83aca3aee4a072e90793e1bb33526b6e5ebd8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallback6-interface"></a>ICorProfilerCallback6, interface
[Pris en charge dans .NET Framework 4.5.2 et ultérieur]  
  
 Une sous-classe de [ICorProfilerCallback5](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md) qui fournit une méthode de rappel que le common language runtime utilise pour notifier au profileur que le chargement d’un assembly.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[Getassemblyreferences, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)|Notifie le profileur qu'un assembly en est au tout début du chargement, quand le CLR effectue un parcours de fermeture de références d'assembly.|  
  
## <a name="remarks"></a>Remarques  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de profilage](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
