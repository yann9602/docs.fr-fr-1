---
title: "ICorProfilerInfo4::GetReJITIDs, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo4.GetReJITIDs
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo4::GetReJITIDs
helpviewer_keywords:
- GetReJITIDs method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::GetReJITIDs method [.NET Framework profiling]
ms.assetid: 634ac28c-a5b7-4fc3-af84-256c24ca8177
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: cc16cd932fc2ce0cf5cb53c227081501e79ed2d5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo4getrejitids-method"></a>ICorProfilerInfo4::GetReJITIDs, méthode
Retourne un tableau d’ID qui identifie toutes les recompilée juste-versions de la fonction spécifiée qui sont toujours allouées. Cela inclut les versions de recompilée juste-des fonctions qui ont été annulées par la suite, mais pas encore libérées (par exemple, lorsque le domaine d’application qui contient la fonction restaurée est en cours d’utilisation).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetReJITIDs (  
     [in]  FunctionID          functionId,  
     [in]  ULONG               cReJitIds,  
     [out] ULONG *             pcReJitIds,  
     [out, size_is(cReJitIds), length_is(*pcReJitIds)]   ReJITID        reJitIds[]);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `functionId`  
 [in] Le `FunctionID` de l’instance de la fonction pour laquelle énumérer des versions.  
  
 `cReJitIds`  
 [in] Le nombre d’ID recompilé juste-allouée dans le `reJitIds` tableau.  
  
 `pcReJitIds`  
 [out] Le nombre réel d’ID de recompilée juste.  
  
 `reJitIds`  
 [out] Tableau alloué par l’appelant qui contiendra les ID recompilé juste-pour la fonction spécifiée.  
  
## <a name="remarks"></a>Remarques  
 `GetReJITIDs`énumère les ID recompilé juste-actives pour une instance de la fonction donnée. Il suit le même modèle d’utilisation en tant qu’autre `ICorProfilerInfo` les fonctions qui acceptent des mémoires tampons allouées par l’appelant.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Icorprofilerinfo4, Interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 [Interfaces de profilage](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Profilage](../../../../docs/framework/unmanaged-api/profiling/index.md)
