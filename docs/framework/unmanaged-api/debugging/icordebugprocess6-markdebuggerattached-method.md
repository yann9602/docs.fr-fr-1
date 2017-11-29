---
title: "ICorDebugProcess6::MarkDebuggerAttached, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: bf94f090-5265-4112-8e57-5b4e20e070d0
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f6d219e298e04157ea0670681c7550bd920bd284
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugprocess6markdebuggerattached-method"></a>ICorDebugProcess6::MarkDebuggerAttached, méthode
Change l'état interne du programme débogué pour que la méthode <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> de la bibliothèque de classes du .NET Framework retourne `true`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT MarkDebuggerAttached(  
    BOOL fIsAttached  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `fIsAttached`  
 `true` si la méthode <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> doit indiquer qu'un débogueur est attaché ; sinon, `false`.  
  
## <a name="return-value"></a>Valeur de retour  
 La méthode peut retourner les valeurs répertoriées dans le tableau suivant.  
  
|Valeur de retour|Description|  
|------------------|-----------------|  
|`S_OK`|Le programme débogué a été mis à jour.|  
|`CORDBG_E_MODULE_NOT_LOADED`|L'assembly contenant la méthode <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> n'est pas chargé ou il n'a pas pu être reconnu à cause d'une autre erreur (par exemple, métadonnées manquantes).<br /><br /> Cette erreur courante est sans gravité. Rappelez la méthode lors du chargement des assemblys supplémentaires.|  
|Autres valeurs `HRESULT` indiquant un échec.|Autres valeurs susceptibles d'indiquer un dysfonctionnement des composants du débogueur ou du compilateur.|  
  
## <a name="remarks"></a>Remarques  
  
> [!NOTE]
>  Cette méthode est uniquement disponible avec .NET Native.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorDebug.idl, CorDebug.h  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Icordebugprocess6, Interface](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)  
 [Interfaces de débogage](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
