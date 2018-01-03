---
title: "ICorDebugCode::CreateBreakpoint, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugCode.CreateBreakpoint
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugCode::CreateBreakpoint
helpviewer_keywords:
- ICorDebugCode::CreateBreakpoint method [.NET Framework debugging]
- CreateBreakpoint method, ICorDebugCode interface [.NET Framework debugging]
ms.assetid: 46842618-0fe4-480b-871c-82fba82d23d9
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 211435025fe06eff180244430138be9d42c5eb86
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcodecreatebreakpoint-method"></a>ICorDebugCode::CreateBreakpoint, méthode
Crée un point d’arrêt dans ce segment de code à l’offset spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CreateBreakpoint (  
    [in] ULONG32     offset,  
    [out] ICorDebugFunctionBreakpoint **ppBreakpoint  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `offset`  
 [in] Le décalage à partir duquel créer le point d’arrêt.  
  
 `ppBreakpoint`  
 [out] Pointeur vers l’adresse d’un objet « ICorDebugFunctionBreakpoint » qui représente le point d’arrêt.  
  
## <a name="remarks"></a>Notes  
 Avant le point d’arrêt est actif, il doit être ajouté à l’objet de processus.  
  
 Si ce code est le code Microsoft intermediate language (MSIL), et il existe un juste-à-temps (JIT)-version native compilée du code, le point d’arrêt sera appliquée dans le code compilé par JIT. (Le même a la valeur true si le code est compilé par JIT ultérieurement.)  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 
