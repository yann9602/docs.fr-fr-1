---
title: "ICorDebugProcess::SetThreadContext, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess.SetThreadContext
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess::SetThreadContext
helpviewer_keywords:
- ICorDebugProcess::SetThreadContext method [.NET Framework debugging]
- SetThreadContext method, ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: a7b50175-2bf1-40be-8f65-64aec7aa1247
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a7d40d455ea17b8df2acd77a1222ac6b080116c6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocesssetthreadcontext-method"></a>ICorDebugProcess::SetThreadContext, méthode
Définit le contexte pour le thread donné dans ce processus.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetThreadContext(  
    [in] DWORD threadID,  
    [in] ULONG32 contextSize,  
    [in, length_is(contextSize), size_is(contextSize)]  
    BYTE context[]);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `threadID`  
 [in] L’ID du thread pour lequel définir le contexte.  
  
 `contextSize`  
 [in] Taille du tableau `context`.  
  
 `context`  
 [in] Un tableau d’octets qui décrivent le contexte du thread.  
  
 Le contexte spécifie l’architecture du processeur sur lequel le thread s’exécute.  
  
## <a name="remarks"></a>Notes  
 Le débogueur doit appeler cette méthode plutôt que Win32 `SetThreadContext` fonctionne, car le thread peut être dans un état « piraté », dans lequel son contexte a été modifié temporairement. Cette méthode doit être utilisée uniquement lorsqu’un thread est en code natif. Utilisez [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) pour les threads en code managé. Vous ne devez jamais modifier le contexte d’un thread pendant un événement de débogage hors-bande (OOB).  
  
 Les données passées doivent être une structure de contexte pour la plateforme actuelle.  
  
 Cette méthode peut endommager le runtime pour une utilisation incorrecte.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
