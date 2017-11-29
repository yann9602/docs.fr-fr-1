---
title: "ICorDebug::DebugActiveProcess, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebug.DebugActiveProcess
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebug::DebugActiveProcess
helpviewer_keywords:
- DebugActiveProcess method [.NET Framework debugging]
- ICorDebug::DebugActiveProcess method [.NET Framework debugging]
ms.assetid: fdab0ade-7f56-4fa2-b3ef-f7a1d2852bba
topic_type: apiref
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c17345caaec71e4d4b057bdcfc2cc395014cbf82
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugdebugactiveprocess-method"></a>ICorDebug::DebugActiveProcess, méthode
Attache le débogueur à un processus existant.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT DebugActiveProcess (  
    [in]  DWORD               id,  
    [in]  BOOL                win32Attach,  
    [out] ICorDebugProcess    **ppProcess  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `id`  
 [in] L’ID du processus auquel le débogueur doit être attaché.  
  
 `win32Attach`  
 [in] Valeur booléenne qui est définie sur `true` si le débogueur doit se comporter comme le débogueur Win32 pour le processus et distribuer les rappels non managés ; sinon, `false`.  
  
 `ppProcess`  
 [out] Pointeur vers l’adresse d’un objet « ICorDebugProcess » qui représente le processus auquel le débogueur est attaché.  
  
## <a name="remarks"></a>Remarques  
 Débogage d’interopérabilité n’est pas pris en charge sur les plateformes Win9x et non-x86, telles que les plateformes basée sur IA-64 et AMD64.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [ICorDebug (Interface)](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
