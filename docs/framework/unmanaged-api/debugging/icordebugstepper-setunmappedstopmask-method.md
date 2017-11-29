---
title: "ICorDebugStepper::SetUnmappedStopMask, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStepper.SetUnmappedStopMask
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStepper::SetUnmappedStopMask
helpviewer_keywords:
- ICorDebugStepper::SetUnmappedStopMask method [.NET Framework debugging]
- SetUnmappedStopMask method [.NET Framework debugging]
ms.assetid: b1211981-e90c-4e05-8def-fa18d85ad9ab
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 163a26ff38d0a4bbae5710d6d841ea29682a8984
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugsteppersetunmappedstopmask-method"></a>ICorDebugStepper::SetUnmappedStopMask, méthode
Définit une valeur qui spécifie le type de code non mappé dans lequel l’exécution s’arrêtera.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetUnmappedStopMask (  
    [in] CorDebugUnmappedStop   mask  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `mask`  
 [in] Valeur de l’énumération CorDebugUnmappedStop qui spécifie le type de code non mappé dans lequel le débogueur arrêtera l’exécution.  
  
 La valeur par défaut est STOP_OTHER_UNMAPPED. La valeur STOP_UNMANAGED est uniquement valide avec le débogage d’interopérabilité.  
  
## <a name="remarks"></a>Remarques  
 Lorsque le débogueur trouve une compilation juste-à-temps (JIT) qui n’a aucun mappage correspondant à Microsoft intermediate language (MSIL), il arrête l’exécution si l’indicateur qui spécifie ce type de code non mappé a été défini ; dans le cas contraire, de pas à pas de façon transparente continue.  
  
 Si le débogueur n’utilise pas une exécution pas à pas pour entrer une méthode, il ne sera pas nécessairement étape code non mappé.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
