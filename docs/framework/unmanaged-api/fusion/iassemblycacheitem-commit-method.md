---
title: "IAssemblyCacheItem::Commit, méthode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IAssemblyCacheItem.Commit
api_location: fusion.dll
api_type: COM
f1_keywords: IAssemblyCacheItem::Commit
helpviewer_keywords:
- IAssemblyCacheItem::Commit method [.NET Framework fusion]
- Commit method, IAssemblyCacheItem interface [.NET Framework fusion]
ms.assetid: c2321f17-f46f-4815-ae41-b28678753613
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3e1907fa3be4992573f84b4810f7504f3af78397
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="iassemblycacheitemcommit-method"></a>IAssemblyCacheItem::Commit, méthode
Valide la référence d’assembly mis en cache dans la mémoire.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Commit (  
    [in] DWORD dwFlags,   
    [out, optional] ULONG *pulDisposition  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `dwFlags`  
 [in] Indicateurs définis dans Fusion.idl.  
  
 `pulDisposition`  
 [out, facultatif] Une valeur qui indique le résultat de l’opération.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** consultez [requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Fusion.h  
  
 **Versions du .NET framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [IAssemblyCacheItem, interface](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md)
