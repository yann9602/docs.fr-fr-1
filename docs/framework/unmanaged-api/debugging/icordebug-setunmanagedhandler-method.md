---
title: "ICorDebug::SetUnmanagedHandler, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebug.SetUnmanagedHandler
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebug::SetUnmanagerHandler
helpviewer_keywords:
- SetUnmanagedHandler method [.NET Framework debugging]
- ICorDebug::SetUnmanagedHandler method [.NET Framework debugging]
ms.assetid: 6b546be4-f86d-4536-8cfc-1d08e5066eb6
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 658cbaeb10496ccd88e0abb3d2174289a820c2e6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugsetunmanagedhandler-method"></a>ICorDebug::SetUnmanagedHandler, méthode
Spécifie l’objet de gestionnaire d’événements pour les événements non gérés.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetUnmanagedHandler (  
    [in] ICorDebugUnmanagedCallback  *pCallback  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pCallback`  
 [in] Un pointeur vers un [ICorDebugUnmanagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md) objet qui représente le Gestionnaire d’événements pour les événements non gérés.  
  
## <a name="remarks"></a>Remarques  
 Le Gestionnaire d’événements d’objet non managée pour les événements doivent être définis après un appel à [ICorDebug::Initialize](../../../../docs/framework/unmanaged-api/debugging/icordebug-initialize-method.md) et avant tous les appels à [ICorDebug::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) ou [ICorDebug::DebugActiveProcess ](../../../../docs/framework/unmanaged-api/debugging/icordebug-debugactiveprocess-method.md). Toutefois, pour des raisons d’héritage, vous ne sont pas requis pour définir l’objet de gestionnaire d’événements pour les événements non managés jusqu'à ce que le premier événement de débogage natif est déclenché. Plus précisément, si `ICorDebug::CreateProcess` a défini l’indicateur CREATE_SUSPENDED, les événements ne peuvent pas être distribués jusqu'à ce que le thread principal est repris de débogage natif.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [ICorDebug (Interface)](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
