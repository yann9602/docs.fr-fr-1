---
title: "ICorDebugBreakpoint::IsActive, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugBreakpoint.IsActive
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugBreakpoint::IsActive
helpviewer_keywords:
- ICorDebugBreakpoint::IsActive method [.NET Framework debugging]
- IsActive method, ICorDebugBreakpoint interface [.NET Framework debugging]
ms.assetid: 06e583d6-d88a-4ff5-bb95-5c48618a461c
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 394caaaff0b0269acd63a590225ffde420ebfd2e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugbreakpointisactive-method"></a>ICorDebugBreakpoint::IsActive, méthode
Obtient une valeur qui indique si cette `ICorDebugBreakpoint` est actif.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT IsActive (  
    [out] BOOL *pbActive  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pbActive`  
 [out] `true` si ce point d’arrêt est actif ; sinon, `false`.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
