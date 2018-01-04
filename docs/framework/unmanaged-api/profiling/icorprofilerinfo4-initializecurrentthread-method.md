---
title: "ICorProfilerInfo4::InitializeCurrentThread, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo4::InitializeCurrentThread
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo4::InitializeCurrentThread
helpviewer_keywords:
- ICorProfilerInfo4::InitializeCurrentThread method [.NET Framework profiling]
- InitializeCurrentThread method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 18a3335c-8c75-476c-b6de-72c0bfedae5d
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4f3c261068b38861dca2633a490e46d9f44371d7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo4initializecurrentthread-method"></a>ICorProfilerInfo4::InitializeCurrentThread, méthode
Initialise le thread actuel avant profiler ultérieur qu'appels d’API sur le même thread, afin que le blocage peut être évité.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT InitializeCurrentThread ();  
```  
  
## <a name="remarks"></a>Notes  
 Nous vous recommandons d’appeler `InitializeCurrentThread` sur n’importe quel thread qui appelle un profileur API lorsqu’il y a suspendu des threads. Cette méthode est généralement utilisée par les profileurs d’échantillonnage qui créent leurs propres threads pour appeler le [ICorProfilerInfo2::DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) méthode pour effectuer la pile présente alors que le thread cible est suspendu. En appelant `InitializeCurrentThread` une fois lorsque le profileur crée d’abord le thread d’échantillonnage, les profileurs peuvent s’assurer que l’initialisation tardive par thread que le CLR, sinon, exécuterait pendant le premier appel à `DoStackSnapshot` peut désormais se produire en toute sécurité lorsque aucun autre thread n’est suspendu.  
  
> [!NOTE]
>  `InitializeCurrentThread`exécute l’initialisation à l’avance pour terminer les tâches qui prennent des verrous et peuvent se bloquer. Appelez `InitializeCurrentThread` uniquement lorsque aucun thread interrompu.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [ICorProfilerInfo4, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 [Interfaces de profilage](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Profilage](../../../../docs/framework/unmanaged-api/profiling/index.md)
