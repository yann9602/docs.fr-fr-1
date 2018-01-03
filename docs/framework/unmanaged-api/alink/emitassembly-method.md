---
title: "EmitAssembly, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IALink2.EmitAssembly
- EmitAssembly
api_location: alink.dll
api_type: COM
f1_keywords: EmitAssembly
helpviewer_keywords: EmitAssembly method
ms.assetid: 605ff39e-e5cc-4bff-8196-e8d68a9715b9
topic_type: apiref
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f012ea89fec0e64bc1639e6c47fb79249c25411a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="emitassembly-method"></a>EmitAssembly, méthode
Crée l’assembly. Appelez cette méthode après la fermeture de tous les autres fichiers à l’exception du fichier d’assembly. N’appelez pas cette méthode lors de la production de modules indépendants.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT EmitAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a>Paramètres  
 `AssemblyID`  
 ID de l’assembly.  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne S_OK si la méthode réussit.  
  
## <a name="requirements"></a>Configuration requise  
 Requiert alink.h  
  
## <a name="see-also"></a>Voir aussi  
 [IALink, interface](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [IALink2, interface](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [API ALink](../../../../docs/framework/unmanaged-api/alink/index.md)
