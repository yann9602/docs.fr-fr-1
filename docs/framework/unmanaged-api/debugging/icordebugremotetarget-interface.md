---
title: ICorDebugRemoteTarget, interface
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugRemoteTarget
api_location: CorDebug.dll
api_type: COM
f1_keywords: ICorDebugRemoteTarget
helpviewer_keywords: ICorDebugRemoteTarget interface [.NET Framework debugging]
ms.assetid: bd9936a6-cc24-4869-8761-0988664464e6
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fcfdab2857745dee7c40823ad25592de5dc833ea
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugremotetarget-interface"></a>ICorDebugRemoteTarget, interface
Fournit des méthodes qui permettent aux développeurs de déboguer les applications Silverlight dans l’environnement du common language runtime (CLR).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
interface ICorDebugRemoteTarget  : IUnknown  
{  
    HRESULT GetHostName (  
        [in]  ULONG32                    cchHostName,  
        [out] ULONG32*                   pcchHostName,  
        [out, size_is(cchHostName),  
              length_is(*pcchHostName)]  
                  WCHAR szHostName[]  
        );  
};  
```  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[ICorDebugRemoteTarget::GetHostName, méthode](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-gethostname-method.md)|Retourne le nom d’hôte ou l’adresse IP d’un ordinateur distant.|  
  
## <a name="remarks"></a>Notes  
 Débogage en mode mixte (code managé et natif) n’est pas pris en charge sur Windows 95, Windows 98 ou Windows Millennium Edition ou sur les plateformes non-x86 (par exemple, ia64 et AMD64).  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl  
  
 **Bibliothèque :** : CorGuids.lib  
  
 **Versions du .NET framework :** 3.5 SP1  
  
## <a name="see-also"></a>Voir aussi  
 [ICorDebugRemote, interface](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)  
 [ICorDebug, interface](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
 [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
