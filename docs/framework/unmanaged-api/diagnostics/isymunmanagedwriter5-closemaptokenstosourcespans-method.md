---
title: "ISymUnmanagedWriter5::CloseMapTokensToSourceSpans, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: f8a0c0a2-a11d-436c-aa85-bc110215cfd6
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2f8a89532999f599c8ec595fa709044b7d13a53a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriter5closemaptokenstosourcespans-method"></a>ISymUnmanagedWriter5::CloseMapTokensToSourceSpans, méthode
Fermez la section des données personnalisées spécifiques pour l’étendue de jeton vers la source des informations de mappage. Après sa fermeture, aucun plus d’informations de mappage ne peut être ajouté.  
  
## <a name="syntax"></a>Syntaxe  
  
```idl  
HRESULT CloseMapTokensToSourceSpans();  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne `HRESULT`.  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Voir aussi  
 [ISymUnmanagedWriter5, interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)
