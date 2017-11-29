---
title: "ICorDebug::CanLaunchOrAttach, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebug.CanLaunchOrAttach
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebug::CanLaunchOrAttach
helpviewer_keywords:
- ICorDebug::CanLaunchOrAttach method [.NET Framework debugging]
- CanLaunchOrAttach method [.NET Framework debugging]
ms.assetid: ca7723db-7c07-4cdd-bd92-fba34928b623
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5bd657c73dfaf7643405b4b657edeffa6e33cd68
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugcanlaunchorattach-method"></a>ICorDebug::CanLaunchOrAttach, méthode
Retourne un HRESULT qui indique si le lancement d’un nouveau processus ou l’attachement au processus existant spécifié est possible dans le contexte de la configuration actuelle de l’ordinateur et d’exécution.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CanLaunchOrAttach (  
    [in] DWORD      dwProcessId,  
    [in] BOOL       win32DebuggingEnabled  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dwProcessId`  
 [in] L’ID d’un processus existant.  
  
 `win32DebuggingEnabled`  
 [in] Passez dans `true` si vous envisagez de démarrer avec le débogage Win32 activé ou à joindre avec le débogage Win32 activé ; sinon, passez `false`.  
  
## <a name="return-value"></a>Valeur de retour  
 S_OK si les services de débogage déterminent que le lancement d’un nouveau processus ou l’attachement au processus donné est possible, compte tenu des informations concernant la configuration actuelle de l’ordinateur et d’exécution. Les valeurs HRESULT possibles sont :  
  
-   S_OK  
  
-   CORDBG_E_DEBUGGING_NOT_POSSIBLE  
  
-   CORDBG_E_KERNEL_DEBUGGER_PRESENT  
  
-   CORDBG_E_KERNEL_DEBUGGER_ENABLED  
  
## <a name="remarks"></a>Remarques  
 Cette méthode est purement informative. L’interface vous empêche pas de lancement ou l’attachement à un processus, indépendamment de la valeur retournée par `CanLaunchOrAttach`.  
  
 Si vous souhaitez démarrer avec le débogage Win32 activé ou l’attachement avec débogage Win32 activé, passez `true` pour `win32DebuggingEnabled`. Le HRESULT retourné par `CanLaunchOrAttach` peut être différent si vous utilisez cette option.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [ICorDebug (Interface)](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
