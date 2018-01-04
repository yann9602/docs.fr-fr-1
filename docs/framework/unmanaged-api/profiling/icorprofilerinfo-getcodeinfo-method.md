---
title: "ICorProfilerInfo::GetCodeInfo, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetCodeInfo
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetCodeInfo
helpviewer_keywords:
- GetCodeInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetCodeInfo method [.NET Framework profiling]
ms.assetid: 90140b0f-a926-4a7e-b6fa-23e05f703cce
topic_type: apiref
caps.latest.revision: "18"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cd05f1ed64e32c4b451f3e60d856be0e99e302b1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfogetcodeinfo-method"></a>ICorProfilerInfo::GetCodeInfo, méthode
Obtient l'étendue de code natif associée à l'ID de la fonction spécifiée.  
  
 Cette méthode est obsolète. Utilisez le [ICorProfilerInfo2::GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md) méthode à la place.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetCodeInfo(  
    [in]  FunctionID functionId,  
    [out] LPCBYTE    *pStart,  
    [out] ULONG      *pcSize);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `functionId`  
 [in] ID de la fonction à laquelle le code natif est associé.  
  
 `pStart`  
 [out] Pointeur vers un tableau d'octets qui composent le code natif de la fonction.  
  
 `pcSize`  
 [out] Pointeur vers un entier qui spécifie la taille, en octets, du code natif.  
  
## <a name="remarks"></a>Notes  
 Pour optimiser la performance, le runtime dans la version 2.0 du .NET Framework fractionne le code natif précompilé d'une fonction en plusieurs régions. Par conséquent, la méthode `GetCodeInfo` est obsolète dans .NET Framework 2.0, car elle ne peut pas gérer l'étendue du code natif d'une fonction. Les profileurs doivent utiliser la méthode `ICorProfilerInfo2::GetCodeInfo2` plus générale à la place.  
  
 Cette fonction utilise des mémoires tampons allouées par l'appelant.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :** 1.0  
  
## <a name="see-also"></a>Voir aussi  
 [ICorProfilerInfo, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [Interfaces de profilage](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Profilage](../../../../docs/framework/unmanaged-api/profiling/index.md)
