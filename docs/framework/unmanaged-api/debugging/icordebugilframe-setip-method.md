---
title: "ICorDebugILFrame::SetIP, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugILFrame.SetIP
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugILFrame::SetIP
helpviewer_keywords:
- SetIP method, ICorDebugILFrame interface [.NET Framework debugging]
- ICorDebugILFrame::SetIP method [.NET Framework debugging]
ms.assetid: 23f38dc1-85e4-4263-9235-2d05bbb6a833
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: daffbbd9e961f4fdc7ff2e3c9be57e41e8fa3f78
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilframesetip-method"></a>ICorDebugILFrame::SetIP, méthode
Définit le pointeur d’instruction à l’emplacement de décalage spécifié dans le code MSIL (intermediate language) de Microsoft.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetIP (  
    [in] ULONG32 nOffset  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `nOffset`  
 L’emplacement de décalage dans le code MSIL.  
  
## <a name="remarks"></a>Notes  
 Les appels à `SetIP` invalident immédiatement tous les frames et des chaînes pour le thread actuel. Si le débogueur a besoin d’informations de frames après un appel à `SetIP`, il doit effectuer une nouvelle trace de pile.  
  
 [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) essaiera de conserver le frame de pile dans un état valide. Toutefois, même si le frame est dans un état valide, il reste peut-être des problèmes tels que des variables locales non initialisées. L’appelant est responsable de la cohérence du programme en cours d’exécution.  
  
 Sur les plateformes 64 bits, le pointeur d’instruction ne peut pas être déplacé hors d’un `catch` ou `finally` bloc. Si `SetIP` est appelée pour effectuer ce déplacement sur une plateforme 64 bits, il retourne un HRESULT indiquant un échec.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
