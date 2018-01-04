---
title: "ICorProfilerInfo::IsArrayClass, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.IsArrayClass
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::IsArrayClass
helpviewer_keywords:
- IsArrayClass method [.NET Framework profiling]
- ICorProfilerInfo::IsArrayClass method [.NET Framework profiling]
ms.assetid: 7f230961-23a6-4d56-ad2d-7a876d65705f
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a1063aea795d73ebaad0803abb7e555e1bb8b7e4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfoisarrayclass-method"></a>ICorProfilerInfo::IsArrayClass, méthode
Détermine si la classe spécifiée est une classe de tableau.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT IsArrayClass(  
    [in]  ClassID        classId,  
    [out] CorElementType *pBaseElemType,  
    [out] ClassID        *pBaseClassId,  
    [out] ULONG          *pcRank);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `classId`  
 [in] L’ID de la classe doit être examinée.  
  
 `pBaseElemType`  
 [out] Pointeur vers une valeur de l’énumération CorElementType qui indique le type des éléments du tableau.  
  
 `pBaseClassId`  
 [out] Pointeur vers l’ID de classe des éléments du tableau, lorsqu’il est disponible.  
  
 `pcRank`  
 [out] Pointeur vers un entier qui indique le rang (autrement dit, le nombre de dimensions) du tableau.  
  
## <a name="remarks"></a>Notes  
 Si la classe spécifiée est une classe de tableau, le `IsArrayClass` méthode retourne un HRESULT S_OK et les valeurs des paramètres de sortie non null. Sinon, elle retourne S_FALSE.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [ICorProfilerInfo, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
