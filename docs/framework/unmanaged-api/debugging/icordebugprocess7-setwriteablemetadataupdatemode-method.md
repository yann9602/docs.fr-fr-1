---
title: "ICorDebugProcess7::SetWriteableMetadataUpdateMode, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: ICorDebugProcess7.SetWriteableMetadataUpdateMode
api_location: mscordbi.dll
api_type: COM
ms.assetid: 8589bba7-7304-45ba-9e31-7bf43dfd5c19
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 635792962e259f181a1ff3e0c46438951e4223db
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugprocess7setwriteablemetadataupdatemode-method"></a>ICorDebugProcess7::SetWriteableMetadataUpdateMode, méthode
[Pris en charge dans .NET Framework 4.5.2 et ultérieur]  
  
 Configure la façon dont le débogueur gère les mises à jour en mémoire des métadonnées dans le processus cible.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT SetWriteableMetadataUpdateMode(  
   WriteableMetadataUpdateMode flags  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `flags`  
 A [WriteableMetadataUpdateMode](../../../../docs/framework/unmanaged-api/debugging/writeablemetadataupdatemode-enumeration.md) valeur d’énumération qui spécifie si les mises à jour en mémoire des métadonnées dans le processus cible sont visibles (`WriteableMetadataUpdateMode::AlwaysShowUpdates`) ou n’est pas visible (`WriteableMetadataUpdateMode::LegacyCompatPolicy`) pour le débogueur.  
  
## <a name="remarks"></a>Remarques  
 Les mises à jour apportées aux métadonnées du processus cible peuvent provenir de Modifier et continuer, d'un profileur ou de <xref:System.Reflection.Emit?displayProperty=nameWithType>.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Icordebugprocess7, Interface](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess7-interface.md)  
 [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
