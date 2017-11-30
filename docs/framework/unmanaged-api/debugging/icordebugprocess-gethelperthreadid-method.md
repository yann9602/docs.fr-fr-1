---
title: "ICorDebugProcess::GetHelperThreadID, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess.GetHelperThreadID
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess::GetHelperThreadID
helpviewer_keywords:
- GetHelperThreadID method [.NET Framework debugging]
- ICorDebugProcess::GetHelperThreadID method [.NET Framework debugging]
ms.assetid: 84e1e605-37c1-49a5-8e12-35db85654622
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 092e99cb1d5534cee56db08b5a2eedaaa2fc4724
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugprocessgethelperthreadid-method"></a>ICorDebugProcess::GetHelperThreadID, méthode
Obtient l’ID de thread de système d’exploitation (OS) du thread d’assistance interne du débogueur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetHelperThreadID (  
    [out] DWORD *pThreadID  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pThreadID`  
 [out] Un pointeur vers le système d’exploitation ID de thread du thread d’assistance interne du débogueur.  
  
## <a name="remarks"></a>Remarques  
 Pendant le débogage managé et, il incombe du débogueur pour vous assurer que le thread avec l’ID spécifié est en cours d’exécution s’il rencontre un point d’arrêt placé par le débogueur. Un débogueur souhaitera peut-être également masquer ce thread de l’utilisateur. Si aucun thread d’assistance n’existe encore, dans le processus de le `GetHelperThreadID` retourne la valeur zéro dans *`pThreadID`.  
  
 Vous ne peut pas mettre en cache l’ID de thread du thread d’assistance, car il peut changer au fil du temps. Vous devez redemander l’ID de thread à chaque événement d’arrêt.  
  
 L’ID du thread d’application d’assistance du débogueur est correct sur chaque non managé [ICorDebugManagedCallback::CreateThread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md) événement, ce qui permet un débogueur déterminer l’ID de son thread d’assistance et de le masquer de l’utilisateur. Un thread qui est identifié comme un thread d’assistance pendant une fonction non managée `ICorDebugManagedCallback::CreateThread` événement ne sera jamais exécuté de code utilisateur managé.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl. CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
