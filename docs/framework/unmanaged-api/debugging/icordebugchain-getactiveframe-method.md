---
title: "ICorDebugChain::GetActiveFrame, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugChain.GetActiveFrame
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugChain::GetActiveFrame
helpviewer_keywords:
- ICorDebugChain::GetActiveFrame method [.NET Framework debugging]
- GetActiveFrame method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 36887017-670b-4f21-b406-8fab956f84a3
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7498e031b74bd904b908342b663e4421432e6d95
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugchaingetactiveframe-method"></a>ICorDebugChain::GetActiveFrame, méthode
Obtient l’active (autrement dit, la plus récente) frame sur la chaîne.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetActiveFrame (  
    [out] ICorDebugFrame   **ppFrame  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppFrame`  
 [out] Un pointeur vers l’adresse d’un objet ICorDebugFrame qui représente l’actif (autrement dit, la plus récente) frame sur la chaîne.  
  
## <a name="remarks"></a>Notes  
 Si aucun frame de pile managé n’est disponible, `ppFrame` a la valeur null.  
  
 Si le frame actif n’est pas disponible, l’appel réussi et `ppFrame` sera null. Cadres active ne sera pas disponibles pour les chaînes initiées en raison de CHAIN_ENTER_UNMANAGED et pour certaines chaînes initiées en raison de CHAIN_CLASS_INIT. Consultez l’énumération CorDebugChainReason.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
