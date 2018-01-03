---
title: "ICorDebugModule::EnableJITDebugging, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule.EnableJITDebugging
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModule::EnableJITDebugging
helpviewer_keywords:
- ICorDebugModule::EnableJITDebugging method [.NET Framework debugging]
- EnableJITDebugging method [.NET Framework debugging]
ms.assetid: 0a65e2a4-5bb6-496c-ae6f-40474426b5a6
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7a699f32d8ec4b2418c6af815c22f35470bede3d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmoduleenablejitdebugging-method"></a>ICorDebugModule::EnableJITDebugging, méthode
Contrôle si le compilateur (JIT) juste-à-temps conserve les informations de débogage pour les méthodes de ce module.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT EnableJITDebugging(  
    [in] BOOL bTrackJITInfo,  
    [in] BOOL bAllowJitOpts  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `bTrackJITInfo`  
 [in] Définissez cette valeur sur `true` pour permettre au compilateur JIT de conserver les informations de mappage entre la version de langage intermédiaire (MSIL) de Microsoft et de la version de compilation JIT de chaque méthode dans ce module.  
  
 `bAllowJitOpts`  
 [in] Définissez cette valeur sur `true` pour permettre au compilateur JIT de générer du code avec certaines optimisations spécifiques au JIT pour le débogage.  
  
## <a name="remarks"></a>Notes  
 Débogage JIT est activé par défaut pour tous les modules qui sont chargés lorsque le débogueur est actif. Par programmation l’activation ou désactivation des paramètres substitue les paramètres globaux.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
