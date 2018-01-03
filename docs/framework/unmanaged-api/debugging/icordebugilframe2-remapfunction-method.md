---
title: "ICorDebugILFrame2::RemapFunction, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugILFrame2.RemapFunction
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugILFrame2::RemapFunction
helpviewer_keywords:
- ICorDebugILFrame2::RemapFunction method [.NET Framework debugging]
- RemapFunction method [.NET Framework debugging]
ms.assetid: dd639ba0-f77b-426d-9ff6-f92706840348
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a9fed4759576d1b6d2fec1a5e9c1e36019e5944c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilframe2remapfunction-method"></a>ICorDebugILFrame2::RemapFunction, méthode
Remappe une fonction modifiée en spécifiant l’offset du nouveau Microsoft intermediate language (MSIL)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT RemapFunction (  
    [in] ULONG32      newILOffset  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `newILOffset`  
 [in] Nouvel offset MSIL du frame de pile à laquelle le pointeur d’instruction doit être placé. Cette valeur doit être un point de séquence.  
  
 Il est responsable de l’appelant pour garantir la validité de cette valeur. Par exemple, l’offset MSIL n’est pas valide s’il est en dehors des limites de la fonction.  
  
## <a name="remarks"></a>Notes  
 Lors de la fonction d’un frame a été modifiée, le débogueur peut appeler le `RemapFunction` méthode pour passer à la dernière version de la fonction du frame afin de pouvoir être exécuté. L’exécution du code commence à l’offset MSIL donné.  
  
> [!NOTE]
>  Appel de `RemapFunction`, comme l’appel [ICorDebugILFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md), invalidera immédiatement toutes les interfaces de débogage qui sont liées à la génération d’une trace de pile du thread. Ces interfaces incluent [ICorDebugChain](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-interface.md), ICorDebugILFrame ICorDebugInternalFrame et ICorDebugNativeFrame.  
  
 Le `RemapFunction` méthode peut être appelée uniquement dans le contexte de l’image actuelle et uniquement dans un des cas suivants :  
  
-   Après réception d’un [ICorDebugManagedCallback2::FunctionRemapOpportunity](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-functionremapopportunity-method.md) rappel qui n’a pas encore repris.  
  
-   Pendant l’exécution du code est arrêtée en raison d’une [ICorDebugManagedCallback::EditAndContinueRemap](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-editandcontinueremap-method.md) événement pour ce frame.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
