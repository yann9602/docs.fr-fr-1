---
title: "ICorDebugChain::EnumerateFrames, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugChain.EnumerateFrames
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugChain::EnumerateFrames method
helpviewer_keywords:
- EnumerateFrames method [.NET Framework debugging]
- ICorDebugChain::EnumerateFrames method [.NET Framework debugging]
ms.assetid: 9fcefa98-750d-4168-8915-8173a43accf2
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 87e2fbc0a4ca9d97ac7e57234383ebd8cee56211
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugchainenumerateframes-method"></a>ICorDebugChain::EnumerateFrames, méthode
Obtient un énumérateur qui contient tous les frames de pile managés dans la chaîne, en commençant par le frame le plus récent.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT EnumerateFrames (  
    [out] ICorDebugFrameEnum **ppFrames  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `ppFrames`  
 [out] Pointeur vers l’adresse d’un objet ICorDebugFrameEnum qui est l’énumérateur pour les frames de pile.  
  
## <a name="remarks"></a>Remarques  
 La chaîne représente la pile des appels physique pour le thread.  
  
 Le `EnumerateFrames` méthode doit être appelée uniquement pour les chaînes managées. L’API de débogage ne fournit pas de méthodes pour obtenir des images contenues dans les chaînes non managées. Le débogueur doit utiliser d’autres moyens d’obtenir ces informations.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
