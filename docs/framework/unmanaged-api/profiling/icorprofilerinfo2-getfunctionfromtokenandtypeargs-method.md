---
title: "ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.GetFunctionFromTokenAndTypeArgs
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs
helpviewer_keywords:
- ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs method [.NET Framework profiling]
- GetFunctionFromTokenAndTypeArgs method [.NET Framework profiling]
ms.assetid: ce8f6aa6-4ebf-4a86-b429-4bbc8af41a8f
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: bc89ca6213008192c0af8e519ae255c13e9763c3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo2getfunctionfromtokenandtypeargs-method"></a>ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs, méthode
Obtient le `FunctionID` d’une fonction à l’aide du jeton de métadonnées spécifié contenant la classe, et `ClassID` valeurs des arguments de type.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetFunctionFromTokenAndTypeArgs(  
    [in] ModuleID moduleID,  
    [in] mdMethodDef funcDef,  
    [in] ClassID classId,  
    [in] ULONG32 cTypeArgs,  
    [in, size_is(cTypeArgs)] ClassID typeArgs[],  
    [out] FunctionID* pFunctionID);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `moduleID`  
 [in] L’ID du module dans lequel la fonction réside.  
  
 `funcDef`  
 [in] Un `mdMethodDef` jeton de métadonnées qui fait référence à la fonction.  
  
 `classId`  
 [in] L’ID de classe de conteneur de la fonction.  
  
 `cTypeArgs`  
 [in] Le nombre de paramètres de type pour la fonction donnée. Cette valeur doit être zéro pour les fonctions non génériques.  
  
 `typeArgs`  
 [in] Un tableau de `ClassID` valeurs, chacune d’elles est un argument de la fonction. La valeur de `typeArgs` peut être NULL si `cTypeArgs` est défini à zéro.  
  
 `pFunctionID`  
 [out] Un pointeur vers le `FunctionID` de la fonction spécifiée.  
  
## <a name="remarks"></a>Remarques  
 Appel de la `GetFunctionFromTokenAndTypeArgs` méthode avec un `mdMethodRef` métadonnées au lieu d’un `mdMethodDef` jeton de métadonnées peut avoir des résultats imprévisibles. Les appelants doivent résoudre le `mdMethodRef` à un `mdMethodDef` lors de son passage.  
  
 Si la fonction n’est pas déjà chargée, l’appel `GetFunctionFromTokenAndTypeArgs` provoquera le chargement, qui est une opération dangereuse dans de nombreux contextes. Par exemple, l’appel de cette méthode pendant le chargement de modules ou de types peut entraîner une boucle infinie, que le runtime tente de charger des éléments.  
  
 En règle générale, utilisez des `GetFunctionFromTokenAndTypeArgs` est déconseillée. Si les profileurs sont intéressés par les événements pour une fonction particulière, ils doivent stocker le `ModuleID` et `mdMethodDef` de cette fonction et utilisez [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) pour vérifier si une donnée `FunctionID` est celui de la fonction de votre choix.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorProf.idl, CorProf.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [ICorProfilerInfo (Interface)](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [ICorProfilerInfo2 (Interface)](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
