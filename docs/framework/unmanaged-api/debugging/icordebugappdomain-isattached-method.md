---
title: "ICorDebugAppDomain::IsAttached, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAppDomain.IsAttached
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugAppDomain::IsAttached
helpviewer_keywords:
- IsAttached method [.NET Framework debugging]
- ICorDebugAppDomain::IsAttached method [.NET Framework debugging]
ms.assetid: af0c67c7-f53e-47c9-b84b-be50bd04903e
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a1af550de7198041a885a788d6b36349c8e1c091
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugappdomainisattached-method"></a>ICorDebugAppDomain::IsAttached, méthode
Obtient une valeur qui indique si le débogueur est attaché au domaine d’application.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT IsAttached (  
    [out] BOOL  *pbAttached  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pbAttached`  
 [out] `true` si le débogueur est attaché au domaine d’application ; sinon, `false`.  
  
## <a name="remarks"></a>Notes  
 Les méthodes ICorDebugController ne peut pas être utilisés tant que le débogueur s’attache au domaine d’application.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
