---
title: "ICorProfilerInfo::GetILToNativeMapping, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetILToNativeMapping
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetILToNativeMapping
helpviewer_keywords:
- GetILToNativeMapping method, ICorProfilerInfo interface [.NET Framework profiling]
- ICorProfilerInfo::GetILToNativeMapping method [.NET Framework profiling]
ms.assetid: 6a5431ef-22fb-4e53-bac5-703986297eb1
topic_type: apiref
caps.latest.revision: "20"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c8d7b248d27f9336fbc846a50e513d18f02c6aa7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfogetiltonativemapping-method"></a>ICorProfilerInfo::GetILToNativeMapping, méthode
Obtient un mappage des offsets MSIL (Microsoft Intermediate Language) aux offsets natifs pour le code contenu dans la fonction spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetILToNativeMapping(  
    [in] FunctionID functionId,  
    [in] ULONG32 cMap,  
    [out] ULONG32 *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        COR_DEBUG_IL_TO_NATIVE_MAP map[]);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `functionId`  
 [in] ID de la fonction contenant le code.  
  
 `cMap`  
 [in] Taille maximale du tableau `map`.  
  
 `pcMap`  
 [out] Nombre total de structures COR_DEBUG_IL_TO_NATIVE_MAP disponibles.  
  
 `map`  
 [out] Tableau de structures `COR_DEBUG_IL_TO_NATIVE_MAP` qui spécifient chacune les offsets. Suite au retour de la méthode `GetILToNativeMapping`, `map` contient une partie ou la totalité des structures `COR_DEBUG_IL_TO_NATIVE_MAP`.  
  
## <a name="remarks"></a>Remarques  
 La méthode `GetILToNativeMapping` retourne un tableau de structures `COR_DEBUG_IL_TO_NATIVE_MAP`. Pour indiquer la finalité que certaines plages d’instructions natives correspondent à des régions spéciales de code (par exemple, le prologue), une entrée dans le tableau peut avoir son `ilOffset` champ défini sur une valeur de la [CorDebugIlToNativeMappingTypes](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md) énumération.  
  
 Suite au retour de `GetILToNativeMapping`, vous devez vérifier que la mémoire tampon `map` est suffisamment grande pour contenir toutes les structures `COR_DEBUG_IL_TO_NATIVE_MAP`. Pour ce faire, comparez la valeur de `cMap` à celle du paramètre `pcMap`. Si la valeur `pcMap`, une fois multipliée par la taille d'une structure `COR_DEBUG_IL_TO_NATIVE_MAP`, est supérieure à `cMap`, allouez une mémoire tampon `map` plus grande, mettez à jour `cMap` pour refléter la nouvelle taille et rappelez `GetILToNativeMapping`.  
  
 Vous pouvez également commencer par appeler `GetILToNativeMapping` avec une mémoire tampon `map` de longueur nulle pour obtenir la taille correcte de la mémoire tampon. Vous pouvez ensuite affecter à la taille de la mémoire tampon la valeur retournée dans `pcMap` et rappeler `GetILToNativeMapping`.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [ICorProfilerInfo (Interface)](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [GetILToNativeMapping2 (méthode)](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getiltonativemapping2-method.md)  
 [Interfaces de profilage](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Profilage](../../../../docs/framework/unmanaged-api/profiling/index.md)
