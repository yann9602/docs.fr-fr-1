---
title: "ICorDebugEval::CallFunction, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugEval.CallFunction
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugEval::CallFunction
helpviewer_keywords:
- ICorDebugEval::CallFunction method [.NET Framework debugging]
- CallFunction method [.NET Framework debugging]
ms.assetid: 7f470c5c-e1c0-4d8d-aad8-830f113ae751
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3c2d5582c9ac69692546e9a2310c4d0c9cdde83e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugevalcallfunction-method"></a>ICorDebugEval::CallFunction, méthode
Définit un appel à la fonction spécifiée.  
  
 Cette méthode est obsolète dans le .NET Framework version 2.0. Utilisez [ICorDebugEval2::CallParameterizedFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-callparameterizedfunction-method.md) à la place.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CallFunction (  
    [in] ICorDebugFunction  *pFunction,  
    [in] ULONG32            nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pFunction`  
 [in] Pointeur vers un objet ICorDebugFunction qui spécifie la fonction à appeler.  
  
 `nArgs`  
 [in] Le nombre d’arguments pour la fonction.  
  
 `ppArgs`  
 [in] Tableau de pointeurs, chacun pointant vers un objet ICorDebugValue qui spécifie un argument à passer à la fonction.  
  
## <a name="remarks"></a>Notes  
 Si la fonction est virtuelle, `CallFunction` exécute une répartition virtuelle. Si la fonction est dans un domaine d’application différent, une transition se produit tant que tous les arguments sont également inclus dans ce domaine d’application.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** WindowSee [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :** 1.1, 1.0  
  
## <a name="see-also"></a>Voir aussi  
 [CallParameterizedFunction, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-callparameterizedfunction-method.md)
