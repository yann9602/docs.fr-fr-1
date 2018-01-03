---
title: "ICorDebugProcessEnum::Next, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcessEnum.Next
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcessEnum::Next
helpviewer_keywords:
- Next method, ICorDebugProcessEnum interface [.NET Framework debugging]
- ICorDebugProcessEnum::Next method [.NET Framework debugging]
ms.assetid: 4ac7077c-8d88-49c4-b360-b3af0c541c63
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 566d4a7eefee846f26abbc64f97e0063e847218b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocessenumnext-method"></a>ICorDebugProcessEnum::Next, méthode
Obtient le nombre spécifié d’instances de ICorDebugProcess à partir de l’énumération, en commençant à la position actuelle.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Next (  
    [in]  ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugProcess *processes[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `celt`  
 [in] Le nombre de `ICorDebugProcess` instances doit être récupéré.  
  
 `processess`  
 [out] Un tableau de pointeurs, chacun pointant vers un `ICorDebugProcess` objet qui représente un processus.  
  
 `pceltFetched`  
 [out] Pointeur vers le nombre de `ICorDebugProcess` instances réellement retournées. Cette valeur peut être null si `celt` fait partie.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
