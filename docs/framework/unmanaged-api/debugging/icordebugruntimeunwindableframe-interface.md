---
title: ICorDebugRuntimeUnwindableFrame, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugUnwindableFrame
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugUnwindableFrame
helpviewer_keywords: ICorDebugUnwindableFrame interface [.NET Framework debugging]
ms.assetid: cd6a3982-6ed3-4909-808d-a66055e813e0
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 80b4212691784d88c92235a5c5c65acaee165201
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugruntimeunwindableframe-interface"></a>ICorDebugRuntimeUnwindableFrame, interface
Fournit un support technique pour les méthodes non managées qui requièrent que le Common Language Runtime (CLR) déroule un frame.  
  
## <a name="remarks"></a>Notes  
 `ICorDebugRuntimeUnwindableFrame`est une version spécialisée de l’interface ICorDebugFrame. Il est utilisé par les méthodes non managées qui requièrent que le runtime déroule un frame sur la pile actuelle. Conventions de déroulement existantes ne fonctionnent pas, car ils n’utilisent pas de code compilé par JIT. Lorsque le débogueur détecte un frame déroulable, elle doit utiliser le [ICorDebugStackWalk::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-next-method.md) méthode afin de dérouler, mais il doit exécuter l’inspection lui-même. Lorsque le débogueur reçoit un `ICorDebugRuntimeUnwindableFrame`, elle peut appeler le [ICorDebugStackWalk::GetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) méthode pour récupérer le contexte de l’image.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Débogage](../../../../docs/framework/unmanaged-api/debugging/index.md)
