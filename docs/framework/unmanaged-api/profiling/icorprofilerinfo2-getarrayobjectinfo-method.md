---
title: "ICorProfilerInfo2::GetArrayObjectInfo, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.GetArrayObjectInfo
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::GetArrayObjectInfo
helpviewer_keywords:
- ICorProfilerInfo2::GetArrayObjectInfo method [.NET Framework profiling]
- GetArrayObjectInfo method [.NET Framework profiling]
ms.assetid: bda75017-739f-4ce5-9000-f3b526e8473c
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 1a1e0c986286483f8236de3a1c73f043691820d5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo2getarrayobjectinfo-method"></a>ICorProfilerInfo2::GetArrayObjectInfo, méthode
Obtient des informations détaillées sur un objet tableau.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetArrayObjectInfo(  
    [in] ObjectID objectId,  
    [in] ULONG32 cDimensions,  
    [out, size_is(cDimensions), length_is(cDimensions)] ULONG32 pDimensionSizes[],  
    [out, size_is(cDimensions), length_is(cDimensions)] int pDimensionLowerBounds[],  
    [out] BYTE **ppData);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `objectId`  
 [in] L’ID d’un objet de tableau valide.  
  
 `cDimensions`  
 [in] Le rang (nombre de dimensions) du tableau.  
  
 `pDimensionSizes`  
 [out] Tableau qui contient des entiers, chacun représentant la taille d’une dimension du tableau.  
  
 `pDimensionLowerBounds`  
 [out] Tableau qui contient des entiers, chacun représentant la limite inférieure lié d’une dimension du tableau.  
  
 `ppData`  
 [out] Pointeur vers l’adresse de la mémoire tampon brute pour le tableau, est disposé selon la convention C++.  
  
## <a name="remarks"></a>Remarques  
 Le `pDimensionSizes` et `pDimensionLowerBounds` sont des tableaux parallèles, les éléments situés au même index dans chaque tableau sont des caractéristiques de la même entité.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [ICorProfilerInfo (Interface)](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [ICorProfilerInfo2 (Interface)](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
