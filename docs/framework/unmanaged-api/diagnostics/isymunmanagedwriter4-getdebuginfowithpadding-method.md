---
title: "ISymUnmanagedWriter4::GetDebugInfoWithPadding, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 881e20ca-8131-4bd0-ba41-c2d6391b0fe2
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f85486370d567ceb1506c41f6aa7c4f3a1929941
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriter4getdebuginfowithpadding-method"></a>ISymUnmanagedWriter4::GetDebugInfoWithPadding, méthode
Fonctionne comme [GetDebugInfo, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md) , sauf que la chaîne de chemin d’accès est complétée avec des zéros qui suivent le caractère null de fin pour rendre les données de chaîne de taille fixe de `MAX_PATH`. Marge intérieure ne reçoit que si la longueur de chaîne de chemin d’accès lui-même est inférieure à `MAX_PATH`.  
  
 Cela rend plus facile d’écrire des outils que les fichiers PE de différence.  
  
## <a name="syntax"></a>Syntaxe  
  
```idl  
HRESULT GetDebugInfoWithPadding(    [in, out] IMAGE_DEBUG_DIRECTORY *pIDD,    [in] DWORD cData,    [out] DWORD *pcData,    [out, size_is(cData), length_is(*pcData)] BYTE data[]);  
```  
  
#### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`pIDD`||  
|`cData`||  
|`pcData`||  
|`data`||  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne `HRESULT`.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Voir aussi  
 [ISymUnmanagedWriter4, interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-interface.md)
