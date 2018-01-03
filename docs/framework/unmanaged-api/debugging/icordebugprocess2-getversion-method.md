---
title: "ICorDebugProcess2::GetVersion, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess2.GetVersion
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess2::GetVersion
helpviewer_keywords:
- GetVersion method, ICorDebugProcess2 nterface [.NET Framework debugging]
- ICorDebugProcess2::GetVersion method [.NET Framework debugging]
ms.assetid: e11d5a75-61d9-4548-aedf-79c26079bd17
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ae9c80a65908d6ec1514ce64845217bd7b5c7805
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess2getversion-method"></a>ICorDebugProcess2::GetVersion, méthode
Obtient le numéro de version du common language runtime (CLR) qui est en cours d’exécution de ce processus.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetVersion (  
    [out] COR_VERSION     *version  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `version`  
 [out] Pointeur vers une structure COR_VERSION qui stocke le numéro de version du runtime.  
  
## <a name="remarks"></a>Notes  
 Le `GetVersion` méthode retourne un code d’erreur si aucune exécution n’a été chargée dans le processus.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
