---
title: "ICorProfilerInfo2::GetCodeInfo2, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.GetCodeInfo2
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::GetCodeInfo2
helpviewer_keywords:
- ICorProfilerInfo2::GetCodeInfo2 method [.NET Framework profiling]
- GetCodeInfo2 method [.NET Framework profiling]
ms.assetid: 532da6ee-7f0a-401b-a61e-fc47ec235d2e
topic_type: apiref
caps.latest.revision: "17"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b211ba79de7454361b44c6e9852ad6698c2e71c3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo2getcodeinfo2-method"></a>ICorProfilerInfo2::GetCodeInfo2, méthode
Obtient l'étendue de code natif associée au `FunctionID` spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetCodeInfo2(  
    [in]  FunctionID functionID,  
    [in]  ULONG32 cCodeInfos,  
    [out] ULONG32 *pcCodeInfos,  
    [out, size_is(cCodeInfos), length_is(*pcCodeInfos)]  
    COR_PRF_CODE_INFO codeInfos[]);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `functionID`  
 [in] ID de la fonction à laquelle le code natif est associé.  
  
 `cCodeInfos`  
 [in] Taille du tableau `codeInfos`.  
  
 `pcCodeInfos`  
 [out] Un pointeur vers le nombre total de [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structures disponibles.  
  
 `codeInfos`  
 [out] Mémoire tampon fournie par l'appelant. Suite au retour de la méthode, celle-ci contient un tableau de structures `COR_PRF_CODE_INFO` qui décrivent chacune un bloc de code natif.  
  
## <a name="remarks"></a>Notes  
 Les étendues sont triées par ordre croissant des offsets du langage MSIL (Microsoft Intermediate Language).  
  
 Suite au retour de `GetCodeInfo2`, vous devez vérifier que la mémoire tampon `codeInfos` est suffisamment grande pour contenir toutes les structures `COR_PRF_CODE_INFO`. Pour ce faire, comparez la valeur de `cCodeInfos` à celle du paramètre `cchName`. Si le résultat de la division de `cCodeInfos` par la taille d'une structure `COR_PRF_CODE_INFO` est inférieur à `pcCodeInfos`, allouez une mémoire tampon `codeInfos` plus grande, mettez à jour `cCodeInfos` pour refléter la nouvelle taille et rappelez `GetCodeInfo2`.  
  
 Vous pouvez également commencer par appeler `GetCodeInfo2` avec une mémoire tampon `codeInfos` de longueur nulle pour obtenir la taille correcte de la mémoire tampon. Vous pouvez ensuite affecter à la taille de la mémoire tampon `codeInfos` la valeur retournée dans `pcCodeInfos`, multipliée par la taille d'une structure `COR_PRF_CODE_INFO`, puis rappeler `GetCodeInfo2`.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [GetCodeInfo3, méthode](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getcodeinfo3-method.md)  
 [ICorProfilerInfo2, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)  
 [Interfaces de profilage](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Profilage](../../../../docs/framework/unmanaged-api/profiling/index.md)
