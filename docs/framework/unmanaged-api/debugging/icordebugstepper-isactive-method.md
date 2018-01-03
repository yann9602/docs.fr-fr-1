---
title: "ICorDebugStepper::IsActive, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStepper.IsActive
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStepper::IsActive
helpviewer_keywords:
- IsActive method, ICorDebugStepper interface [.NET Framework debugging]
- ICorDebugStepper::IsActive method [.NET Framework debugging]
ms.assetid: 8b35e7a9-b40e-40a9-8d8e-b82e823fc575
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dd919852d3e7c187dff7fc4304d0a1b42f5294e0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugstepperisactive-method"></a>ICorDebugStepper::IsActive, méthode
Obtient une valeur qui indique si cet ICorDebugStepper exécute actuellement une étape.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT IsActive (  
    [out] BOOL   *pbActive  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `pbActive`  
 [out] Retourne `true` si l’exécution pas à pas exécute actuellement une étape ; sinon, retourne `false`.  
  
## <a name="remarks"></a>Notes  
 Toute étape reste active jusqu'à ce que le débogueur reçoive un [ICorDebugManagedCallback::StepComplete](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-stepcomplete-method.md) appeler, ce qui désactive automatiquement l’exécution pas à pas. Une exécution pas à pas peut également être désactivée prématurément en appelant [ICorDebugStepper::Deactivate](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-deactivate-method.md) avant le rappel condition est atteinte.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
