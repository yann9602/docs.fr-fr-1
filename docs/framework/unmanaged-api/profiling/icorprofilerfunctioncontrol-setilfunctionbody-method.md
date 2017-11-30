---
title: "ICorProfilerFunctionControl::SetILFunctionBody, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerFunctionControl.SetILFunctionBody
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerFunctionControl::SetILFunctionBody
helpviewer_keywords:
- ICorProfilerFunctionControl::SetILFunctionBody method [.NET Framework profiling]
- SetILFunctionBody method, ICorProfilerFunctionControl interface [.NET Framework profiling]
ms.assetid: 2c33f0f7-75b2-4c19-b2c7-c94b54997576
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9469435186a5aef130ca4ebef27a4613afeb921c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerfunctioncontrolsetilfunctionbody-method"></a>ICorProfilerFunctionControl::SetILFunctionBody, méthode
Remplace le corps Common Intermediate Language (CIL) de la méthode.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetILFunctionBody(  
    [in]  ULONG   cbNewILMethodHeader,  
    [in, size_is(cbNewILMethodHeader)] LPCBYTE pbNewILMethodHeader);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `cbNewILMethodHeader`  
 [in] La taille totale du nouveau CIL, y compris l'en-tête et toutes structures intervenant après le corps.  
  
 `pbNewILMethodHeader`  
 [in] Un pointeur vers le nouvel en-tête de CIL.  
  
## <a name="return-value"></a>Valeur de retour  
 Cette méthode retourne les HRESULT spécifiques suivants.  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|Le remplacement a été correctement effectué.|  
  
## <a name="remarks"></a>Remarques  
 Contrairement à la [ICorProfilerInfo::SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) (méthode), la `SetILFunctionBody` méthode gère la mémoire requise pour le nouveau corps de CIL. Cela signifie que le corps de CIL fourni par le profileur n’a pas à allouer à l’aide de la [IMethodMalloc](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md) interface ou dans une plage particulière. Il peut être alloué sur n'importe quel segment de mémoire. Le profileur peut libérer la mémoire utilisée pour son corps CIL après `SetILFunctionBody` retourne.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [ICorProfilerFunctionControl (Interface)](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md)
