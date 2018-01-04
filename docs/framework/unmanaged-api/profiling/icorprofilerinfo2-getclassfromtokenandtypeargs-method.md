---
title: "ICorProfilerInfo2::GetClassFromTokenAndTypeArgs, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.GetClassFromTokenAndTypeArgs
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::GetClassFromTokenAndTypeArgs
helpviewer_keywords:
- GetClassFromTokenAndTypeArgs method [.NET Framework profiling]
- ICorProfilerInfo2::GetClassFromTokenAndTypeArgs method [.NET Framework profiling]
ms.assetid: b25c88f0-71b9-443b-8eea-1c94db0a44b9
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5a459f8e9ec6d63dc42d6a0a8f752c129d278524
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo2getclassfromtokenandtypeargs-method"></a>ICorProfilerInfo2::GetClassFromTokenAndTypeArgs, méthode
Obtient le `ClassID` d’un type à l’aide du jeton de métadonnées spécifié et le `ClassID` valeurs des arguments de type.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetClassFromTokenAndTypeArgs(  
    [in] ModuleID moduleID,  
    [in] mdTypeDef typeDef,  
    [in] ULONG32 cTypeArgs,  
    [in, size_is(cTypeArgs)] ClassID typeArgs[],  
    [out] ClassID* pClassID);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `moduleID`  
 [in] L’ID du module dans lequel réside le type.  
  
 `typeDef`  
 [in] Un `mdTypeDef` jeton de métadonnées qui fait référence au type.  
  
 `cTypeArgs`  
 [in] Le nombre de paramètres de type pour le type donné. Cette valeur doit être zéro pour les types non génériques.  
  
 `typeArgs`  
 [in] Un tableau de `ClassID` valeurs, chacune d’elles est un argument de type. La valeur de `typeArgs` peut être NULL si `cTypeArgs` est défini à zéro.  
  
 `pClassID`  
 [out] Un pointeur vers le `ClassID` du type spécifié.  
  
## <a name="remarks"></a>Notes  
 Appel de la `GetClassFromTokenAndTypeArgs` méthode avec une `mdTypeRef` au lieu d’un `mdTypeDef` jeton de métadonnées peut avoir des résultats imprévisibles ; les appelants doivent résoudre le `mdTypeRef` à un `mdTypeDef` lors de son passage.  
  
 Si le type n’est pas déjà chargé, l’appel `GetClassFromTokenAndTypeArgs` déclenchera le chargement, qui est une opération dangereuse dans de nombreux contextes. Par exemple, l’appel de cette méthode pendant le chargement de modules ou d’autres types peut entraîner une boucle infinie, que le runtime tente de charger des éléments.  
  
 En règle générale, utilisez des `GetClassFromTokenAndTypeArgs` est déconseillée. Si les profileurs sont intéressés par les événements pour un type particulier, ils doivent stocker le `ModuleID` et `mdTypeDef` de ce type et utilisez [ICorProfilerInfo2::GetClassIDInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md) pour vérifier si une donnée `ClassID` est celle de la type souhaité.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [ICorProfilerInfo, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [ICorProfilerInfo2, interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
